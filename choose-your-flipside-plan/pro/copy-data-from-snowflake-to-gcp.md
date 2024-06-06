# Copy Data from Snowflake to GCP

To copy data from Snowflake into Google Cloud Storage (GCS) without creating a storage integration, you can create an external stage with GCP credentials. Here's how you can do it:

1. **Create the external stage**
2. **Copy data into the GCS bucket**

Here’s the process step-by-step:

1. **Create the external stage:**

Replace `your-bucket-name`, `your-path`, and `your-gcp-keyfile-json-string` with your actual GCS bucket name, path, and the contents of your GCP key file (in JSON format), respectively.

```sql
CREATE OR REPLACE STAGE my_gcs_stage
URL = 'gcs://your-bucket-name/your-path/'
CREDENTIALS = (
  GCP_KEYFILE = 'your-gcp-keyfile-json-string'
);
```

2. **Copy data into the GCS bucket:**

Replace `your-file-name` with the desired file name in the GCS bucket and `your_table` with the name of the table you want to export.

```sql
COPY INTO @my_gcs_stage/your-file-name
FROM your_table
FILE_FORMAT = (TYPE = CSV);
```
