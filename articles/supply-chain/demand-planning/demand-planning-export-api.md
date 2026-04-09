---
title: Export data using custom APIs
description: Learn how to use Dataverse custom APIs to programmatically export demand planning data from Dynamics 365 Supply Chain Management.
author: AndersEvenGirke
ms.author: aevengir
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 04/09/2026
ms.custom:
  - bap-template
---

# Export data using custom APIs

[!include [banner](../includes/banner.md)]

## Overview

You can programmatically export demand planning data (forecasts and time series) from Dynamics 365 Supply Chain Management to external systems using Dataverse custom API actions. This approach enables you to automate export workflows without needing to manually interact with the Demand Planning interface. The custom APIs support retrieving exported data as comma-separated values (CSV) files via secure shared access signature (SAS) URLs.

Dataverse custom API actions provide the public interface for export operations and can be called using:

- **Dataverse Web API** - OData HTTP requests for external applications and services
- **Power Platform tools** - Native integration with Power Automate, custom connectors, and Dataverse plugins

> [!NOTE]
> This article describes programmatic export using Dataverse custom APIs. To export data using the Demand Planning interface, see [Export and download data](export-data.md).

## Prerequisites

Before you use the export custom APIs, you must have:

- An export profile configured in Demand Planning. To create export profiles, see [Export and download data](export-data.md).
- Access to the Dataverse environment for your Demand Planning instance.

> [!TIP]
> To find your export profile ID, open the export profile in the Demand Planning interface and copy the GUID from the browser URL. Alternatively, query the `msdyn_scpexportdataprofile` entity using the Dataverse Web API to retrieve profile IDs programmatically.

## Export data programmatically

The following diagram shows the workflow for exporting data using Dataverse custom APIs:

:::image type="content" source="media/demand-planning-export-api/demand-planning-export-job-sequence-diagram.png" alt-text="Diagram of Dataverse export workflow showing job creation, status polling, export completion, and CSV download steps." lightbox="media/demand-planning-export-api/demand-planning-export-job-sequence-diagram.png":::

To export demand planning data using Dataverse custom APIs, follow these steps:

1. **Create an export job** - Create an export job using the Demand Planning interface. You can create jobs manually or configure scheduled jobs within the Demand Planning application. The job creation process runs asynchronously, so the export job is created immediately and then processes in the background.

2. **Monitor job status** - Poll the Dataverse **Export Job Run** entity (`msdyn_scpexportdatajobruns`) to track job progress. Query the entity using Dataverse Web API OData queries to check the `msdyn_jobrunstatus` field. For details, see [Monitor job status](#monitor-job-status).

3. **Retrieve the file URL** - When the job status shows as completed (status value 192350002), call the `msdyn_scpgetexportoutputfileurl` custom API action to retrieve a SAS URL for downloading the exported file. The URL is valid for 120 minutes. For details, see [Power Platform integration](#power-platform-integration).

4. **Download the file** - Use the returned SAS URL to download the CSV file. The file contains your exported demand planning data in the format described in the [Export file format](#export-file-format) section.

## Monitor job status

After scheduling an export job, monitor its progress by querying the Dataverse **Export Job Run** entity. Export jobs run asynchronously, so you need to poll for status updates until the job completes.

### Entity details

Query the following Dataverse entity to check export job status:

| Property | Value |
|----------|-------|
| Entity name | `msdyn_scpexportdatajobrun` |
| Display name | Export Job Run |

**Key fields:**

| Field name | Description |
|------------|-------------|
| `msdyn_jobrunstatus` | Current job status (see status values below) |
| `msdyn_name` | Job name provided when scheduling |
| `msdyn_starttime` | Job start timestamp |
| `msdyn_endtime` | Job completion timestamp |
| `msdyn_errormessage` | Error details if the job failed |
| `_msdyn_profile_value` | Associated export profile ID (lookup field) |

### Job status values

The `msdyn_jobrunstatus` field uses the following integer values:

| Status | Value | Description |
|--------|-------|-------------|
| Created | 192350000 | Job has been created but not yet started |
| Executing | 192350001 | Job is currently running |
| Completed | 192350002 | Job finished successfully |
| Failed | 192350003 | Job encountered an error |
| Canceling | 192350004 | Job cancellation in progress |
| Canceled | 192350005 | Job was cancelled |

### Query examples

Use Dataverse Web API OData queries to retrieve job status. The base query pattern is:

```odata
GET [Organization URI]/api/data/v9.2/msdyn_scpexportdatajobruns?$filter={filter expression}&$select={columns}
```

**Common query patterns:**

Filter by completed status:

```odata
GET [Organization URI]/api/data/v9.2/msdyn_scpexportdatajobruns?$filter=msdyn_jobrunstatus eq 192350002&$select=msdyn_name,msdyn_endtime
```

Filter by export profile:

```odata
GET [Organization URI]/api/data/v9.2/msdyn_scpexportdatajobruns?$filter=_msdyn_profile_value eq 11111111-1111-1111-1111-111111111111&$select=msdyn_name,msdyn_jobrunstatus
```

Combine multiple filters:

```odata
GET [Organization URI]/api/data/v9.2/msdyn_scpexportdatajobruns?$filter=msdyn_jobrunstatus eq 192350002 and _msdyn_profile_value eq 11111111-1111-1111-1111-111111111111
```

> [!NOTE]
> **Authentication**: When calling Dataverse Web API endpoints, you need to authenticate using one of the supported methods. Options include OAuth tokens, Azure managed identities, Azure DefaultAzureCredential, or service principal authentication. For detailed guidance on authentication options and implementation, see [Authenticate with Microsoft Dataverse web services](/power-apps/developer/data-platform/authentication).

> [!TIP]
> For Dataverse-native integrations, you can also use the `msdyn_scpgetexportoutputfileurl` custom API action to retrieve the output file URL directly from Dataverse.

For more information about Dataverse Web API queries, see [Query data using the Web API](/power-apps/developer/data-platform/webapi/query/overview).

## Power Platform integration

For Power Platform scenarios such as Power Automate flows, custom connectors, or Dataverse plugins, use Dataverse custom API actions. These actions provide native integration with the Power Platform ecosystem.

### Available custom API actions

The following custom API actions are available for export operations:

| Action name | Description | Use case |
|-------------|-------------|----------|
| `msdyn_scpgetexportoutputfileurl` | Retrieves the SAS URL for a completed export file | Downloading exported data in Power Automate flows or custom code |

### Use the custom API action

The `msdyn_scpgetexportoutputfileurl` action retrieves a SAS URL for downloading the exported CSV file from a completed export job.

**Input parameters:**

| Parameter name | Type | Required | Description |
|----------------|------|----------|-------------|
| `msdyn_exportprofileid` | String (GUID) | Yes | The ID of the export profile |

**Output:**

| Property name | Type | Description |
|---------------|------|-------------|
| `output` | String | The SAS URL for downloading the exported CSV file (valid for 120 minutes) |

**When to use:**

- **Power Automate flows** - Use the **Perform an unbound action** step to call the custom API action natively
- **Custom connectors** - Invoke the custom API action through Dataverse connectors
- **External applications** - Call the custom API action via Dataverse Web API (OData HTTP requests)
- **Dataverse plugins** - Execute the custom API action from within plugin code

### Example: Power Automate flow

To retrieve an export file URL in Power Automate:

1. Add the **Perform an unbound action** step
2. Select action name: `msdyn_scpgetexportoutputfileurl`
3. Provide the export profile ID as `msdyn_exportprofileid`
4. Use the `output` property to download the file or pass the URL to subsequent steps

> [!NOTE]
> The custom API action requires Dataverse authentication and appropriate permissions. Make sure your application or Power Platform connection has access to the Dataverse organization where Demand Planning is deployed.

For more information about using custom API actions in Power Platform, see [Use custom APIs](/power-apps/developer/data-platform/custom-api).

### Walkthrough: Automatically download exports to SharePoint

This walkthrough shows how to create a Power Automate flow that automatically downloads completed export files to a SharePoint folder. The flow monitors export job completions and retrieves the CSV file using the custom API action.

**Scenario:**

When an export job completes in Demand Planning, the flow automatically:

1. Detects the completed job
2. Retrieves the export file URL using the custom API action
3. Downloads the CSV file
4. Saves it to a designated SharePoint folder

**Prerequisites:**

- Access to Power Automate with a Dataverse connection
- SharePoint site and folder for storing export files
- Export profile configured in Demand Planning

**Create the flow:**

1. **Add trigger** - Use the **When a row is added, modified or deleted** trigger
   - Set **Change type**: Added or Modified or Deleted
   - Set **Table name**: Export Data Job Runs (`msdyn_scpexportdatajobruns`)
   - Set **Filter rows**: `msdyn_jobrunstatus eq 192350002` (filters for completed jobs only)
   - Optional: Add `_msdyn_profile_value eq {your-profile-guid}` to filter for specific export profiles

2. **Get export file URL** - Add **Perform an unbound action in selected environment** step
   - Set **Environment**: Your Dataverse environment
   - Set **Action name**: `msdyn_scpgetexportoutputfileurl`
   - Set **msdyn_exportprofileid**: The known export profile ID, or use the profile ID from the trigger output

3. **Download file** - Add **HTTP 2** action
   - Set **Method**: GET
   - Set **URI**: Use the `output` from the previous step (the SAS URL)

4. **Save to SharePoint** - Add **Create file** action (SharePoint)
   - Set **Site address**: Your SharePoint site
   - Set **Folder path**: Your target folder
   - Set **File name**: Use the job name from trigger or create a naming pattern
   - Set **File content**: Use the body output from the HTTP download step

:::image type="content" source="media/export-api-powerautomate-export-flow.png" alt-text="Power Automate flow for automatic export downloads" lightbox="media/export-api-powerautomate-export-flow.png":::

:::image type="content" source="media/export-api-export-profile-configuration.png" alt-text="Export profile configuration in Demand Planning" lightbox="media/export-api-export-profile-configuration.png":::

:::image type="content" source="media/export-api-sharepoint-exported-file.png" alt-text="Exported CSV file in SharePoint folder" lightbox="media/export-api-sharepoint-exported-file.png":::

> [!TIP]
> To download exports from multiple profiles, remove the profile filter from the trigger. The flow will process all completed export jobs. You can add condition logic to route files to different SharePoint folders based on the profile ID.

## Export file format

The exported files use a standard CSV format with configurable columns.

### CSV structure

Exported files have the following structure:

**Standard columns:**

- **Time** - Timestamp of the data point (format configurable via organization settings)
- **Value** - The numeric value (forecast, demand, and so on)
- **Dimension columns** - Additional columns based on the time series dimensions (such as Product, Location, Customer)

**Example CSV:**

```csv
Time,Value,Product,Location
2024-01-01,1500.50,PROD001,WH-EAST
2024-01-02,1623.75,PROD001,WH-EAST
2024-01-01,892.25,PROD002,WH-WEST
2024-01-02,945.00,PROD002,WH-WEST
```

### File storage

- **Location**: Azure Data Lake Storage Gen2
- **Path**: `ExportFiles/{exportProfileId}.csv`
- **Format**: UTF-8 encoded CSV
- **Access**: SAS URL valid for 120 minutes (2 hours)

## Best practices

Follow these best practices to ensure successful exports:

- **SAS URL expiration** - The SAS URL expires after 120 minutes. Download the file promptly or request a new URL if needed.
- **Job naming** - Use descriptive job names that include context (such as date range and purpose) for easier tracking and auditing.
- **Export profile management** - Configure export profiles in advance with appropriate filters, date ranges, and dimension selections.
- **Error handling** - Implement retry logic for transient failures and proper error handling for authentication and authorization issues when calling Dataverse custom APIs.
- **File size** - Be mindful of large exports. Consider filtering data by date range or dimensions to manage file sizes.

### Error responses

When an error occurs calling Dataverse custom APIs, standard Dataverse error responses are returned. For details on error handling, see [Web API error handling](/power-apps/developer/data-platform/webapi/compose-http-requests-handle-errors#handle-errors).

**Common error scenarios:**

- **401 Unauthorized**: Authentication token is missing, expired, or invalid
- **403 Forbidden**: The authenticated user lacks permissions to access the Dataverse organization or execute custom API actions
- **404 Not Found**: The specified export profile or export file doesn't exist
- **400 Bad Request**: Invalid request parameters such as malformed GUIDs or missing required fields

## Data classification

> [!IMPORTANT]
> Exported data may contain customer content and system metadata. The `msdyn_scpgetexportoutputfileurl` custom API action returns SAS URLs to access customer content. Make sure you follow appropriate data handling and storage practices according to your organization's security policies.

## See also

- [Export and download data](export-data.md)
- [Rolling forecasts](rolling-forecasts.md)
