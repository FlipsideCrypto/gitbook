# Copy Data from Snowflake to AWS

To copy data from Snowflake into AWS S3 without creating storage integration, you can use a named external stage. This way, you define the credentials and S3 bucket details within the stage itself rather than creating a storage integration. Here's how you can do it:

1. **Create the external stage**
2. **Copy data into the S3 bucket**

Here’s the process step-by-step:

1. **Create the external stage:**

Replace `your-bucket-name`, `your-path`, `your-aws-access-key-id`, and `your-aws-secret-access-key` with your actual S3 bucket name, path, AWS access key ID, and secret access key, respectively.

```sql
CREATE OR REPLACE STAGE my_s3_stage
URL = 's3://your-bucket-name/your-path/'
CREDENTIALS = (
  AWS_KEY_ID = 'your-aws-access-key-id'
  AWS_SECRET_KEY = 'your-aws-secret-access-key'
);
```

2. **Copy data into the S3 bucket:**

Replace `your-file-name` with the desired file name in the S3 bucket and `your_table` with the name of the table you want to export.

```sql
COPY INTO @my_s3_stage/your-file-name
FROM your_table
FILE_FORMAT = (TYPE = CSV);
```

This way, you don’t need to create a storage integration, and you can still copy data from Snowflake to S3.
