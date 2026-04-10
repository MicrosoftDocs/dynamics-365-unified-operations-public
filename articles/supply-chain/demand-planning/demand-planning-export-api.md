---
title: Export data using custom APIs
description: Learn how to use Dataverse custom APIs to programmatically export Demand planning data.
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

You can programmatically export Demand planning data (forecasts and time series) to external systems using Dataverse custom API actions. This approach enables you to automate export workflows without needing to manually interact with the Demand planning interface. The custom APIs support retrieving exported data as comma-separated values (CSV) files through secure shared access signature (SAS) URLs.

Dataverse custom API actions provide the public interface for export operations. You can call them using:

- **Dataverse Web API** – OData HTTP requests for external applications and services
- **Power Platform tools** – Native integration with Power Automate, custom connectors, and Dataverse plugins

> [!NOTE]
> This article describes programmatic export using Dataverse custom APIs. Learn how to export data using the Demand planning interface in [Export and download data](export-data.md).

## Prerequisites

Before you use the export custom APIs, make sure you have:

- An export profile configured in Demand planning. Learn how to create export profiles in [Export and download data](export-data.md).
- Access to the Dataverse environment for your Demand planning instance.

> [!TIP]
> To find your export profile ID, open the export profile in the Demand planning interface and copy the GUID from the browser URL. Alternatively, query the `msdyn_scpexportdataprofile` entity using the Dataverse Web API to retrieve profile IDs programmatically.

## Export data programmatically

The following diagram shows the workflow for exporting data using Dataverse custom APIs:

:::image type="content" source="media/demand-planning-export-api/demand-planning-export-job-sequence-diagram.png" alt-text="Diagram of Dataverse export workflow showing job creation, status polling, export completion, and CSV download steps." lightbox="media/demand-planning-export-api/demand-planning-export-job-sequence-diagram.png":::

To export Demand planning data using Dataverse custom APIs, follow these steps:

1. **Create an export job** – Create an export job using the Demand planning interface. You can create jobs manually or configure scheduled jobs within the Demand planning application. The job creation process runs asynchronously, so the export job is created immediately and then processes in the background.

1. **Monitor job status** – Poll the Dataverse **Export Job Run** entity (`msdyn_scpexportdatajobruns`) to track job progress. Query the entity using Dataverse Web API OData queries to check the `msdyn_jobrunstatus` field. Learn more in [Monitor job status](#monitor-job-status).

1. **Retrieve the file URL** – When the job status shows as completed (status value 192350002), call the `msdyn_scpgetexportoutputfileurl` custom API action to retrieve a SAS URL for downloading the exported file. The URL is valid for 120 minutes. Learn more in [Power Platform integration](#power-platform-integration).

1. **Download the file** – Use the returned SAS URL to download the CSV file. The file contains your exported Demand planning data in the format described in the [Export file format](#export-file-format) section.

## Monitor job status

After scheduling an export job, monitor its progress by querying the Dataverse **Export Job Run** entity. Export jobs run asynchronously, so you need to poll for status updates until the job completes.

### Entity details

Query the following Dataverse entity to check export job status:

| Property | Value |
|----------|-------|
| Entity name | `msdyn_scpexportdatajobrun` |
| Display name | Export Job Run |

The following table lists the key fields in the `msdyn_scpexportdatajobrun` entity that are relevant for monitoring export jobs:

| Field name | Description |
|------------|-------------|
| `msdyn_jobrunstatus` | Current job status (see status values in the next section) |
| `msdyn_name` | Job name provided when scheduling |
| `msdyn_starttime` | Job start timestamp |
| `msdyn_endtime` | Job completion timestamp |
| `msdyn_errormessage` | Error details if the job failed |
| `_msdyn_profile_value` | Associated export profile ID (lookup field) |

### Job status values

The `msdyn_jobrunstatus` field uses the following integer values:

| Status | Value | Description |
|--------|-------|-------------|
| Created | 192350000 | Job is created but not started yet |
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

The following examples show common query patterns for monitoring export jobs.

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
> When calling Dataverse Web API endpoints, authenticate by using one of the supported methods. Options include OAuth tokens, Azure managed identities, Azure DefaultAzureCredential, or service principal authentication. For detailed guidance on authentication options and implementation, see [Authenticate with Microsoft Dataverse web services](/power-apps/developer/data-platform/authentication).

> [!TIP]
> For Dataverse-native integrations, you can also use the `msdyn_scpgetexportoutputfileurl` custom API action to retrieve the output file URL directly from Dataverse.

For more information about Dataverse Web API queries, see [Query data using the Web API](/power-apps/developer/data-platform/webapi/query/overview).

## Power Platform integration

For Power Platform scenarios such as Power Automate flows, custom connectors, or Dataverse plugins, use Dataverse custom API actions. These actions provide native integration with the Power Platform ecosystem.

### Available custom API actions

The following custom API action is available for export operations:

| Action name | Description | Use case |
|-------------|-------------|----------|
| `msdyn_scpgetexportoutputfileurl` | Retrieves the SAS URL for a completed export file | Downloading exported data in Power Automate flows or custom code |

### Use the custom API action

The `msdyn_scpgetexportoutputfileurl` action retrieves a SAS URL for downloading the exported CSV file from a completed export job.

The following table lists the input parameters required to call the `msdyn_scpgetexportoutputfileurl` custom API action:

| Parameter name | Type | Required | Description |
|----------------|------|----------|-------------|
| `msdyn_exportprofileid` | String (GUID) | Yes | The ID of the export profile |

The following table describes the output returned by the `msdyn_scpgetexportoutputfileurl` custom API action:

| Property name | Type | Description |
|---------------|------|-------------|
| `output` | String | The SAS URL for downloading the exported CSV file (valid for 120 minutes) |

Use the `msdyn_scpgetexportoutputfileurl` custom API action in the following scenarios:

- **Power Automate flows** – Use the *Perform an unbound action* step to call the custom API action natively.
- **Custom connectors** – Invoke the custom API action through Dataverse connectors.
- **External applications** – Call the custom API action via Dataverse Web API (OData HTTP requests).
- **Dataverse plugins** – Execute the custom API action from within plugin code.

### Example: Power Automate flow

To retrieve an export file URL in Power Automate:

1. Add the *Perform an unbound action* step.
1. Select the action name `msdyn_scpgetexportoutputfileurl`.
1. Enter the export profile ID as `msdyn_exportprofileid`.
1. Use the `output` property to download the file or pass the URL to subsequent steps.

> [!NOTE]
> The custom API action requires Dataverse authentication and appropriate permissions. Make sure your application or Power Platform connection has access to the Dataverse organization where Demand planning is deployed.

For more information about using custom API actions in Power Platform, see [Use custom APIs](/power-apps/developer/data-platform/custom-api).

### Walkthrough: Automatically download exports to SharePoint

This walkthrough shows how to create a Power Automate flow that automatically downloads completed export files to a SharePoint folder. The flow monitors export job completions and retrieves the CSV file by using the custom API action.

#### Scenario

When an export job completes in Demand planning, the flow automatically:

1. Detects the completed job
1. Retrieves the export file URL by using the custom API action
1. Downloads the CSV file
1. Saves it to a designated SharePoint folder

#### Scenario prerequisites

To implement this scenario, you need the following prerequisites:

- Access to Power Automate with a Dataverse connection
- SharePoint site and folder for storing export files
- Export profile configured in Demand planning

#### Create the flow

To create the flow, follow these steps:

1. **Add trigger** – Use the *When a row is added, modified or deleted* trigger
   - Set **Change type** – Added, Modified, or Deleted
   - Set **Table name** – Export Data Job Runs (`msdyn_scpexportdatajobruns`)
   - Set **Filter rows** – `msdyn_jobrunstatus eq 192350002` (filters for completed jobs only)
   - Optional: Add `_msdyn_profile_value eq {your-profile-guid}` to filter for specific export profiles

1. **Get export file URL** – Add the *Perform an unbound action in selected environment* step
   - Set **Environment** – Your Dataverse environment
   - Set **Action name** – `msdyn_scpgetexportoutputfileurl`
   - Set **msdyn_exportprofileid** – The known export profile ID, or use the profile ID from the trigger output

1. **Download file** – Add the *HTTP 2* action
   - Set **Method** – GET
   - Set **URI** – Use the `output` from the previous step (the SAS URL)

1. **Save to SharePoint** – Add the *Create file* action (SharePoint)
   - Set **Site address** – Your SharePoint site
   - Set **Folder path** – Your target folder
   - Set **File name** – Use the job name from trigger or create a naming pattern
   - Set **File content** – Use the body output from the HTTP download step

The following image shows the full created flow:

:::image type="content" source="media/export-api-power-automate-export-flow.png" alt-text="Power Automate flow for automatic export downloads" lightbox="media/export-api-power-automate-export-flow.png":::

> [!TIP]
> To download exports from multiple profiles, remove the profile filter from the trigger. The flow processes all completed export jobs. You can add condition logic to route files to different SharePoint folders based on the profile ID.

## Export file format

The exported files use a standard comma-separated values (CSV) format with configurable columns.

### CSV structure

Exported files have the following standard columns:

- **Time** – Timestamp of the data point (format configurable via organization settings)
- **Value** – The numeric value (forecast, demand, and so on)
- **Dimension columns** – Additional columns based on the time series dimensions (such as Product, Location, Customer)

Here's an example of CSV file content:

```csv
Time,Value,Product,Location
2024-01-01,1500.50,PROD001,WH-EAST
2024-01-02,1623.75,PROD001,WH-EAST
2024-01-01,892.25,PROD002,WH-WEST
2024-01-02,945.00,PROD002,WH-WEST
```

### File storage

Files are stored as follows:

- **Location** – Azure Data Lake Storage Gen2
- **Path** – `ExportFiles/{exportProfileId}.csv`
- **Format** – UTF-8 encoded CSV
- **Access** – SAS URL valid for 120 minutes (2 hours)

## Best practices

Follow these best practices to ensure successful exports:

- **SAS URL expiration** – The SAS URL expires after 120 minutes. Download the file promptly or request a new URL if needed.
- **Job naming** – Use descriptive job names that include context (such as date range and purpose) for easier tracking and auditing.
- **Export profile management** – Configure export profiles in advance with appropriate filters, date ranges, and dimension selections.
- **Error handling** – Implement retry logic for transient failures and proper error handling for authentication and authorization issues when calling Dataverse custom APIs.
- **File size** – Be mindful of large exports. Consider filtering data by date range or dimensions to manage file sizes.

### Error responses

When an error occurs calling Dataverse custom APIs, the API returns standard Dataverse error responses. For details on error handling, see [Web API error handling](/power-apps/developer/data-platform/webapi/compose-http-requests-handle-errors#handle-errors).

Here are some common error scenarios you might encounter when calling the export custom API action:

- **401 Unauthorized** – Authentication token is missing, expired, or invalid.
- **403 Forbidden** – The authenticated user lacks permissions to access the Dataverse organization or execute custom API actions.
- **404 Not Found** – The specified export profile or export file doesn't exist.
- **400 Bad Request** – Invalid request parameters exist, such as malformed GUIDs or missing required fields.

## Data classification

> [!IMPORTANT]
> Exported data might contain customer content and system metadata. The `msdyn_scpgetexportoutputfileurl` custom API action returns SAS URLs to access customer content. Make sure you follow appropriate data handling and storage practices according to your organization's security policies.

## Additional resources

- [Export and download data](export-data.md)
- [Rolling forecasts](rolling-forecasts.md)
