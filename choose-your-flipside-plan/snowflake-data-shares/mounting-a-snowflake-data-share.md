# Mounting a Snowflake Data Share

Onboarding the Flipside shares is a simple three or four step process.&#x20;

1. Get the listing
2. Mount the shared data&#x20;
3. Run the provided script that will finish the setup
4. OPTIONAL: Create an alert to notify if the task fails

Flipside data shares contain the underlying tables and [the script in step three](mounting-a-snowflake-data-share.md#sql-script) will ensure the final presentation layer is recreated within the consumer’s snowflake account.

{% embed url="https://www.loom.com/share/72b376e9ed1b4933b6da3ec0e4517586?sid=919df848-e828-41f4-be80-ae65e34ab3c" %}
Quick walkhrough of mounting a Data Share listing.
{% endembed %}

### Step 1: Get and mount the share

In the Snowflake account you shared with Flipside, navigate to: _Data > Data Products >_ then click on the tab _Shared With Me_. Find the listing titled _Flipside\_\[Chain Name]_ and click the blue button labeled 'Get' \


<figure><img src="https://lh7-us.googleusercontent.com/rS5hROQ8vFww2lUvTsdyKAuDIKkdQW8bquVKIYA5nKCDsJR3WD_8XAwWggqP38yeotlaPRbrSX0VN1jGqQu9-xiIFZvMM_bqw3_qZiQmbN2GHyavMXyK3PM-EMt0wdKnzKMwczZ1ytpRa8OxlSsVF4Y" alt=""><figcaption></figcaption></figure>

### Step 2: Mount the share

Mount the data and make sure the database is named Flipside\_\[Chain name] (if Trial remove \_Trial at the end)

* Example: Flipside\_Ethereum

<figure><img src="https://lh7-us.googleusercontent.com/Ec1eAqf_kA-Kzar1bvZJhqse_DorBSIa_sTmmiWUIGmyjXjaD0HnB0367cXvBB8KxUk0bsbn8_8M9ibXaBd60YJ2ONS_JUbp-CW91YJSl6JJYvx0IfcWNSWC8on0LSwCnRM-vQd3eGHfyNZbLLIp1V8" alt=""><figcaption></figcaption></figure>

### Step 3: Run the [SQL script](mounting-a-snowflake-data-share.md#sql-script) to recreate the presentation layer as ACCOUNTADMIN

Open a new worksheet in Snowflake and run the script [linked here](mounting-a-snowflake-data-share.md#sql-script).

<figure><img src="https://lh7-us.googleusercontent.com/kBZlzqG-LNAjwTgFdhhkNQ3cUvmArKpHQtfsdXLOOI2NwF5H1h5_88vncdupfIH1jFLLlM22PYggbDofY86oD92UHbXNZWAqCavOJ-zGzKtdveY5sDwc3OTNCKW093aU91yJSQmkcCUvnkJWynklO0M" alt=""><figcaption></figcaption></figure>

### (Optional) Step 4: Modify and execute the [sample code](mounting-a-snowflake-data-share.md#task-alerting) to set up email alerting



#### SQL Script

```sql
--Create utility db
create database if not exists _flipside;


-- create base proc that uses the db and updated_since
CREATE OR REPLACE PROCEDURE _flipside.public.sp_ddl_refresh(db string ,UPDATED_SINCE TIMESTAMP_NTZ(9))
RETURNS VARCHAR NOT NULL
LANGUAGE SQL
AS 
DECLARE 
    full_table varchar DEFAULT :db || '._datashare._create_gold';
    destination_db varchar default REPLACE(:db,'FLIPSIDE_');
    QUERY varchar default '';
DDL_HASH STRING;
BEGIN
select replace(
        replace(
            replace(ddl, '\\$\\$', '$$'),
            '__SOURCE__',
            UPPER(:db)
        ),
        '__NEW__',
         UPPER(:destination_db)
    ) ,
    ddl_hash into :QUERY,
    :DDL_HASH
from
     IDENTIFIER(:full_table)
     WHERE DDL_CREATED_AT >= :UPDATED_SINCE
order by
    ddl_created_at desc
limit
    1;
      IF (:QUERY is not null) then 
       EXECUTE IMMEDIATE  :QUERY;
  end if;
  
   RETURN:DDL_HASH;
END;


-- create  proc that uses just the db
CREATE OR REPLACE PROCEDURE _FLIPSIDE.PUBLIC.SP_DDL_REFRESH(DB string)
RETURNS TABLE (ddl_hash STRING)
LANGUAGE SQL
AS DECLARE 
  results resultset;
BEGIN
  results := (call _flipside.public.sp_ddl_refresh(:db, '2000-01-01'::TIMESTAMP_NTZ) );
  RETURN table(results);
END;


-- create proc that uses the updated since and will run for all flipside dbs
CREATE OR REPLACE PROCEDURE _flipside.public.sp_ddl_refresh("UPDATED_SINCE" TIMESTAMP_NTZ(9))
RETURNS TABLE (dbs string)
LANGUAGE SQL


-- EXECUTE AS OWNER
AS DECLARE
  cur CURSOR FOR  select 
       database_name
    from SNOWFLAKE.INFORMATION_SCHEMA.DATABASES 
    where database_name like 'FLIPSIDE_%';
BEGIN
    create or replace temporary table results as 
    select ''::string as db
    from dual 
    limit 0;
    FOR cur_row IN cur DO
        let db varchar:= cur_row.database_name;
        call _flipside.public.sp_ddl_refresh(:db, :updated_since);
            insert into results (db) values (:db);
    END FOR;
    let rs resultset := (select * from results order by db);
    RETURN TABLE(rs);
END;


-- create  proc that will recreated all dbs regardless of updated since date
CREATE OR REPLACE PROCEDURE _flipside.public.sp_ddl_refresh()
RETURNS TABLE (dbs string)
LANGUAGE SQL
AS 
DECLARE
  results resultset;
BEGIN
  results := (call _flipside.public.sp_ddl_refresh( '2000-01-01'::TIMESTAMP_NTZ) );
  RETURN table(results);
END;


-- create  task that runs every 10 minutes (procs only run  if there's a change -- in the last 10 mins)
create or replace task _flipside.public.TK_ddl_refresh
schedule='10 MINUTE'
as DECLARE
rs resultset;
output string;
BEGIN
    rs := (call _flipside.public.sp_ddl_refresh(sysdate() - interval '10 mins'));
    select listagg($1, ';') into :output from table(result_scan(last_query_id())) limit 1;
    call SYSTEM$SET_RETURN_VALUE( :output );
END;


--set task to resume. By default they are suspended
alter task _flipside.public.TK_ddl_refresh resume;


--Call the proc for the first time to created the new dbs manually
call _flipside.public.sp_ddl_refresh();



--query to see that the task is successfully created
select *
  from table(_flipside.information_schema.task_history())
  where name ='TK_DDL_REFRESH'
  order by scheduled_time desc;// Some code
```

### Task alerting

Alerting/Monitoring for failed tasks can be done in many ways. One option is to use the built in snowflake email alerting. Snowflake docs: [alerting documentation](https://docs.snowflake.com/en/user-guide/alerts#label-alerts-history) | [email notification](https://docs.snowflake.com/en/user-guide/email-stored-procedures#label-create-email-notification-integration)

Below is a sample example of how we can check the task history every 10 minutes to look for failures

```sql
--create email integrations
CREATE NOTIFICATION INTEGRATION my_email_int
    TYPE=EMAIL
    ENABLED=TRUE
    ALLOWED_RECIPIENTS=('user@flipsidecrypto.com');


--create alert
CREATE OR REPLACE ALERT myalert
  WAREHOUSE = [warehouse name]
  SCHEDULE = '10 MINUTE'
 IF (EXISTS (
      SELECT *
      from table(_flipside.information_schema.task_history())
       where name ='TK_DDL_REFRESH' and STATE ='FAILED'
       and COMPLETED_TIME BETWEEN SNOWFLAKE.ALERT.LAST_SUCCESSFUL_SCHEDULED_TIME()
       AND SNOWFLAKE.ALERT.SCHEDULED_TIME()
  ))
  THEN CALL SYSTEM$SEND_EMAIL(
    'my_email_int',
    'user@flipsidecrypto.com',
    'Email Alert: The data share ddl refresh failed',
    'Task A has ...'
);

--make sure to resume the alert. By default it's suspended
ALTER ALERT myalert RESUME;// Some code
```

### Granting permissions

If another role outside of accountadmin needs access to the data, the below scripts should allow for granting access to the current views and will also ensure any new schemas/views are accessible.&#x20;

```sql
GRANT usage on database [blockchain] to role [your_role];
```

```sql
GRANT usage on all schemas in database [blockchain] to role [your_role];
```

```sql
GRANT select on all views in database [blockchain] to role [your_role];
```

```sql
GRANT usage on future schemas in database [blockchain] to role [your_role];
```

```sql
GRANT select on future views in database [blockchain] to role [your_role];
```
