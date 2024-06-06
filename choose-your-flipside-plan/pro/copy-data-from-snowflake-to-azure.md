# Copy Data from Snowflake to Azure

o copy data from Snowflake into Azure Blob Storage without creating a storage integration, you can create an external stage with Azure credentials. Here's how you can do it:

1. **Create the external stage**
2. **Copy data into the Azure Blob Storage**

Here’s the process step-by-step:

1. **Create the external stage:**

Replace `your-account-name`, `your-container-name`, `your-path`, and `your-azure-sas-token` with your actual Azure account name, container name, path, and the SAS token, respectively.

```sql
CREATE OR REPLACE STAGE my_azure_stage
URL = 'azure://your-account-name.blob.core.windows.net/your-container-name/your-path/'
CREDENTIALS = (
  AZURE_SAS_TOKEN = 'your-azure-sas-token'
);
```

2. **Copy data into the Azure Blob Storage:**

Replace `your-file-name` with the desired file name in the Azure Blob Storage and `your_table` with the name of the table you want to export.

```sql
COPY INTO @my_azure_stage/your-file-name
FROM your_table
FILE_FORMAT = (TYPE = CSV);
```

This approach for both GCP and Azure allows you to copy data from Snowflake to your cloud storage without creating a storage integration.
