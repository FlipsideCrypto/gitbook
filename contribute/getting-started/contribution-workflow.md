# Contribution Workflow

\[ this workflow will be actively updated and enhanced as we receive feedback ]

**Create and contribute your first model**

1. Understand the modeling structure
   * Data models iterate through different “layers”. Generally speaking these are bronze, silver, and core. How these layers interact is defined in [Model Standards](../model-standards/).
2. Create model file within the proper layer and naming convention
   * Naming convention for file is `<layer name>__<table name>.sql`
   * Example for silver layer:  `./models/silver/silver__my_new_table.sql`
3. Create a corresponding .yml file
   * This should hold any model/column descriptions and tests for the model/columns
   * Example for silver layer:  `./models/silver/silver__my_new_table.yml`
4. Start writing SQL code
   * Write code in Snowflake Web UI (Snowsight):  [https://app.snowflake.com/us-east-1/vna27887](https://app.snowflake.com/us-east-1/vna27887)
   * Snowsight documentation:  [https://docs.snowflake.com/en/user-guide/ui-snowsight.html](https://docs.snowflake.com/en/user-guide/ui-snowsight.html)
5. Turn SQL code into DBT SQL
   * dbt combines sql with Jinja, see more:[ https://docs.getdbt.com/docs/building-a-dbt-project/jinja-macros](https://docs.getdbt.com/docs/building-a-dbt-project/jinja-macros)
   * Copy sql code into the file created earlier
   * Add config section
     * See existing models for examples
     * Dbt docs for available configurations [https://docs.getdbt.com/reference/resource-configs/snowflake-configs](https://docs.getdbt.com/reference/resource-configs/snowflake-configs)
   * Convert SQL elements into Jinja
     * Commonly this is changing table name to references and adding incremental loading logic
     * Ref: [https://docs.getdbt.com/reference/dbt-jinja-functions/ref](https://docs.getdbt.com/reference/dbt-jinja-functions/ref)
     * Incremental logic: [https://docs.getdbt.com/docs/building-a-dbt-project/building-models/configuring-incremental-models](https://docs.getdbt.com/docs/building-a-dbt-project/building-models/configuring-incremental-models)
       1. See existing curated models for examples on how to implement incremental logic. `ethereum-models/models/silver/silver__transactions.sql`
6. Run the dbt model to put it into the community dev database. You must run this command within the dbt-console. If you have exited the console run `make dbt-console` again
   * `dbt run -s <path to model>`
   * Run: [https://docs.getdbt.com/reference/commands/run](https://docs.getdbt.com/reference/commands/run)
   * If this is your 1st time using `dbt run` in this docker container, you may need to run `dbt deps` command
   * Models will be deployed to `<BLOCKCHAIN>_COMMUNITY_DEV` database within Snowflake.  This database refreshes daily at `04:00 AM UTC`, any non-production resources will be erased.
7. Run the test file
   * `dbt test -s <path to mode>`
   * Tests: [https://docs.getdbt.com/docs/building-a-dbt-project/tests](https://docs.getdbt.com/docs/building-a-dbt-project/tests)
8. Create GitHub Pull Request and write a summary on your updates/changes, as well as attaching passing test logs
9. Request Reviewer from one of the GitHub handles below
   * austinFlipside
   * juls858
   * James-Mission
   * desmond-hui
10. Fix Review Comments
11. Re-Request Reviewer after fixing review comments
12. If your PR has been approved, merge it to production
13. **Congratulations! You’ve successfully contributed a data model!**
