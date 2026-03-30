---
title: Data management package REST API
description: Learn about the data management framework's package REST API, including a table that outlines recurring integration APIs for various decision points.
author: pnghub
ms.author: johnmichalak
ms.topic: article
ms.date: 01/20/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2017-03-31
ms.dyn365.ops.version: Platform update 5
---

# Data management package REST API

[!include [banner](../includes/banner.md)]

This article describes the Data management framework's package representational state transfer (REST) application programming interface (API). The package API lets you integrate by using data packages. You can use the REST API with both cloud deployments and on-premises deployments.

Although on-premises support is added, API names aren't changed. Therefore, Microsoft keeps a single API set for both cloud deployments and on-premises deployments.

## Choosing an integration API

Two APIs support file-based integration scenarios: the Data management framework's package API and the recurring integrations API. Both APIs support both data import scenarios and data export scenarios. The following table describes the main decision points that you consider when you're trying to decide which API to use.

| Decision point      | Recurring integrations API | Data management framework's package API |
|---------------------|--------------------------------------|-----------------------------|
| Scheduling          | Scheduling in finance and operations apps | Scheduling outside finance and operations apps |
| Format              | Files and data packages | Only data packages |
| Transformation      | Support for Extensible Stylesheet Language Transformations (XSLT) if the data file is in XML format | Transformations that are external to the system |
| Supported protocols | SOAP and REST | REST |
| Service type        | Custom service | Open Data Protocol (OData) action |

If you decide that the recurring integrations API meets your requirement better than the Data management framework's package API, see [Recurring integrations](recurring-integrations.md). The rest of this article discusses the Data management framework's package API.

## Authorization

The Data management framework's package API uses OAuth 2.0 to authorize access. You must call the API by using a valid OAuth access token. For more information about OAuth 2.0 and Microsoft Entra ID, see [Authorize access to web applications using OAuth 2.0 and Microsoft Entra ID](/azure/active-directory/develop/active-directory-protocols-oauth-code). For on-premises deployments, use Active Directory Federation Services (AD FS) for authorization.

> [!NOTE]
> When you use the Client Credentials Grant flow, the application maintains an access control list. You can find the access control list at **System administration** \> **Setup** \> **Microsoft Entra applications**. The **Microsoft Entra applications** page shows the approved client IDs and the user security mapping that the API enforces when it's called by using the Client Credentials Grant flow.
>
> For on-premises deployments, this list must have a valid client ID from AD FS. Additionally, for on-premises use, **\<baseurl\>** in the following examples must append **/namespaces/AXSF** when a connection is made.

## Import APIs

Use the following APIs to import files (data packages).

### GetImportStagingErrorFileUrl

The GetImportStagingErrorFileUrl API is used to get the URL of the error file containing the input records that failed at the source to the staging step of import for a single entity. An empty string is returned if no error file is generated.

POST /data/DataManagementDefinitionGroups/Microsoft.Dynamics.DataEntities.GetImportStagingErrorFileUrl

```json
Body
{
 "executionId":"<string>",
 "entityName":"<string>"
}

Successful Response:

HTTP/1.1 200 OK
{
 "@odata.context":"https://<baseurl>/data/$metadata#Edm.String",
 "value":"<errorfileurl>"
}
```

**Input parameters**

| Parameter     | Description |
|---------------------|--------------------------------------|
| string executionId          | Execution ID of import. The UI calls this ID the Job ID. |
| string entityName        | Name of the entity for which to get the error file. |

**Output parameters**

| Parameter         | Description |
|-------------------|-------------|
| string errorkeysfileurl | The URL of the error file. The return value is empty if an error file wasn't generated. |

### GenerateImportTargetErrorKeysFile

Use the GenerateImportTargetErrorKeysFile API to create an error file that contains the keys of the import records that failed during the staging to target step of import for a single entity.  

If this API returns `true`, use the GetImportTargetErrorKeysFileUrl API to get the URL of the generated error keys file.

POST /data/DataManagementDefinitionGroups/Microsoft.Dynamics.DataEntities.GenerateImportTargetErrorKeysFile

```json
Body

{
 "executionId":"<string>",
 "entityName":"<string>"
}

Successful Response:

HTTP/1.1 200 OK
{
 "@odata.context":"https://<baseurl>/data/$metadata#Edm.Boolean",
 "value": <errorsExist>
}
```

**Input parameters**

| Parameter     | Description |
|---------------------|--------------------------------------|
| string executionId          | Execution ID of import |
| string entityName        | Name of the entity for which to get the error file |

**Output parameters**

| Parameter     | Description |
|---------------------|--------------------------------------|
| Boolean errorsExist     | `true` if there are import errors; `false` if there are no errors |

### GetImportTargetErrorKeysFileUrl

Use the **GetImportTargetErrorKeysFileUrl** API to get the URL of the error file that contains the keys of the import records that failed at the staging-to-target step of import for a single entity.

If the error file is available, this API returns the URL. If the error file is still being generated, or if there isn't an error file, the API returns an empty string.

> [!IMPORTANT]
> Before you call this API, call the **GenerateImportTargetErrorKeysFile** API to generate the error file. If the **GenerateImportTargetErrorKeysFile** API returns **true**, call this API in a loop until it returns a non-empty string. If the **GenerateImportTargetErrorKeysFile** API returns **false**, this API always returns an empty string, because there are no errors.

**Pseudocode example**

```csharp
errorsExist = GenerateImportTargetErrorKeysFile(executionId, entityName)

if (errorsExist)
{
    errorFileUrl = null

    while (errorFileUrl is not a non-empty string)
    {
        errorFileUrl = GetImportTargetErrorKeysFileUrl(executionId, entityName)
        if (errorFileUrl is not a non-empty string)
        {
            wait for some time before retrying
        }
    }
}
```

```csharp
POST
/data/DataManagementDefinitionGroups/Microsoft.Dynamics.DataEntities.GetImportTargetErrorKeysFileUrl

Body
{
    "executionId":"<string>",
    "entityName":"<string>"
}
```

Here's an example of a successful response.

```json
HTTP/1.1 200 OK
{
    "@odata.context":"https://<baseurl>/data/$metadata#Edm.String",
    "value":"<errorkeysfileurl>"
}
```

**Input parameters**

| Parameter         | Description |
|-------------------|-------------|
| string executionId | The execution ID of the import. The UI calls this ID the Job ID.|
| string entityName | The name of the entity to get the error file for. |

**Output parameters**

| Parameter         | Description |
|-------------------|-------------|
| string errorkeysfileurl | The URL of the error keys file, if the file is available. If the error file is still being generated, or if no errors exist, the method returns an empty string. |

### GetAzureWriteUrl

Use the **GetAzureWriteUrl** API to get a writable blob URL. The method includes a shared access signature (SAS) token that is embedded in the URL. Use this method to upload a data package to the Azure Blob storage container. For on-premises deployments, this API still returns the URL that is abstracted to local storage.

> [!NOTE]
> An SAS is valid only during an expiry time window. Any request that is made after the window returns an error. For more information, see [Using shared access signatures (SAS)](/azure/storage/common/storage-dotnet-shared-access-signature-part-1).

```csharp
POST /data/DataManagementDefinitionGroups/Microsoft.Dynamics.DataEntities.GetAzureWriteUrl
BODY
{
    "uniqueFileName":"<string>"
}
```

Here's an example of a successful response.

```json
HTTP/1.1 200 OK
{
    "@odata.context":"https://<baseurl>/data/$metadata#Edm.String",
    "value": "{\"BlobId\":\"{<GUID>}\",\"BlobUrl\":\"https://<baseurl_id>.blob.core.windows.net/dmf/<uniqueFileName>?<SAS Token>\"}"
    }
}
```

**Input parameters**

| Parameter         | Description |
|-------------------|-------------|
| string uniqueFileName | A unique file name that tracks blob IDs. You can include a globally unique identifier (GUID) to help guarantee a unique file name. |

**Output parameters**

| Parameter      | Description |
|----------------|-------------|
| string BlobId  | The blob ID of the allocated blob container. |
| string BlobUrl | A URL that has an embedded SAS token. Use the URL to write to Blob storage. |

### ImportFromPackage

Use the **ImportFromPackage** API to start an import from the data package you upload to the Blob storage associated with your implementation. For on-premises deployments, the import starts from the local storage where you previously uploaded the file.

An async version of this API, **ImportFromPackageAsync**, is also available. It has the same specifications. You must capture the execution ID it returns and later call the **GetExecutionSummaryStatus** API to check when the execution finishes.

> [!NOTE]
> The **ImportFromPackage** API supports composite entities. However, the limitation is that package that consists of a composite data entity must only have that one composite data entity.
>
> The XMLField tags must be mapped to entities in manifest file for mapping to load correctly.

```csharp
POST /data/DataManagementDefinitionGroups/Microsoft.Dynamics.DataEntities.ImportFromPackage
BODY
{
    "packageUrl":"<string>",
    "definitionGroupId":"<string>",
    "executionId":"<string>",
    "execute":<bool>,
    "overwrite":<bool>,
    "legalEntityId":"<string>"
}
```

Here's an example of a successful response.

```json
HTTP/1.1 200 OK
{
    "@odata.context":"https://<baseurl>/data/$metadata#Edm.String",
    "value":"<executionId>"
}
```

**Input parameters**

| Parameter                | Description |
|--------------------------|-------------|
| string packageUrl        | The URL of the data package in the Blob storage that is associated with a finance and operations app. |
| string definitionGroupId | The name of the data project for import. |
| string executionId       | The ID to use for the job. This ID appears as the Job ID in the UI. If you assign an empty ID, a new execution ID is created. |
| bool execute             | Set this parameter to **True** to run the target step. Otherwise, set it to **False**. |
| bool overwrite           | Always set this parameter to **False** when a composite entity is used in a package. Otherwise, set it to **True**. |
| string legalEntityId     | The legal entity for the data import. |

**Output parameters**

| Parameter          | Description |
|--------------------|-------------|
| string executionId | The execution ID of the data import. This ID appears as the Job ID in the UI. |

> [!NOTE]
> **ImportFromPackage()** uses a batch to perform the import. Therefore, parallel processing rules must be used in Data management to perform parallel imports. Don't call **ImportFromPackage()** in parallel threads. Otherwise, it fails.

## Export APIs

Use the following APIs to export files (data packages).

### ExportToPackagePreview

Use the **ExportToPackagePreview** API to preview an export of a data package with a large number of records. This API applies to both cloud deployments and on-premises deployments.

An async version of this API, **ImportFromPackagePreviewAsync**, is available. The specifications are the same. You must capture the execution ID that's returned and then call the **GetExecutionSummaryStatus** API to determine when the execution finishes.  

- You must create the export data project before you call this API. If the project doesn't exist, a call to the API returns an error.
- If you turn on change tracking, the API exports only records that are created or updated since the last run. (In other words, the API returns only the delta.)
- Use the **count** parameter to limit the number of records returned.

```csharp
POST /data/DataManagementDefinitionGroups/Microsoft.Dynamics.DataEntities.ExportToPackagePreview
BODY
{
    "definitionGroupId":"<Data project name>",
    "packageName":"<Name to use for downloaded file.>",
    "executionId":"<Execution Id if it is a rerun>",
    "reExecute":<bool>,
    "legalEntityId":"<Legal entity Id>",
    "count":"<Legal entity Id>"
}
```

Here's an example of a successful response.

```json
HTTP/1.1 200 OK
{
    "@odata.context":"https://<baseurl>/data/$metadata#Edm.String",
    "value":{
        "value":"<executionId>"
    }
}
```

**Input parameters**

| Parameter                | Description |
|--------------------------|-------------|
| string definitionGroupId | The name of the data project for export. |
| string packageName       | The name of the exported data package. |
| string executionId       | The ID to use for the job. This ID appears as the Job ID in the UI. If you assign an empty ID, the API creates a new execution ID. |
| bool reExecute           | Set this parameter to **True** to run the target step. Otherwise, set it to **False**. |
| string legalEntityId     | The legal entity for the data import. |
| count                    | The number of records to return. No top count condition is applied if set to zero. |
 
**Output parameters**

| Parameter          | Description |
|--------------------|-------------|
| string executionId | The execution ID of the data export. This ID appears as the Job ID in the UI. |

### ExportToPackage

Use the **ExportToPackage** API to start exporting a data package. This API works for both cloud and on-premises deployments.

An async version of this API, **ExportToPackageAsync**, is also available. It has the same specifications. You must capture the execution ID it returns and then call the **GetExecutionSummaryStatus** API to check when the execution finishes.

- You must create the export data project before you call this API. If the project doesn't exist, a call to the API returns an error.
- If you turn on change tracking, the API exports only records that are created or updated since the last run. (In other words, the API returns only the delta.)

```csharp
POST /data/DataManagementDefinitionGroups/Microsoft.Dynamics.DataEntities.ExportToPackage
BODY
{
    "definitionGroupId":"<Data project name>",
    "packageName":"<Name to use for downloaded file.>",
    "executionId":"<Execution Id if it is a rerun>",
    "reExecute":<bool>,
    "legalEntityId":"<Legal entity Id>"
}
```

Here's an example of a successful response.

```json
HTTP/1.1 200 OK
{
    "@odata.context":"https://<baseurl>/data/$metadata#Edm.String",
    "value":{
        "value":"<executionId>"
    }
}
```

**Input parameters**

| Parameter                | Description |
|--------------------------|-------------|
| string definitionGroupId | The name of the data project for export. |
| string packageName       | The name of the exported data package. |
| string executionId       | The ID to use for the job. This ID appears as the Job ID in the UI. If you assign an empty ID, the API creates a new execution ID. |
| bool reExecute           | Set this parameter to **True** to run the target step. Otherwise, set it to **False**. |
| string legalEntityId     | The legal entity for the data import. |
 
**Output parameters**

| Parameter          | Description |
|--------------------|-------------|
| string executionId | The execution ID of the data export. This ID appears as the Job ID in the UI. |

### GetExportedPackageUrl

Use the **GetExportedPackageUrl** API to get the URL of the data package that a call to **ExportToPackage** exports. This API works for both cloud deployments and on-premises deployments.

```csharp
POST /data/DataManagementDefinitionGroups/Microsoft.Dynamics.DataEntities.GetExportedPackageUrl
BODY
{"executionId":"<Execution Id>"}
```

Here's an example of a successful response.

```json
HTTP/1.1 200 OK
{
    "@odata.context":"https://<baseurl>/data/$metadata#Edm.String",
    "value":{
        "value":"https://<baseurl_id>.blob.core.windows.net/dmf/<uniqueFileName>?<SAS Token>"
    }
}
```

**Input parameters**

| Parameter          | Description |
|--------------------|-------------|
| string executionId | The execution ID of the data project run. The UI calls this ID the Job ID. |

**Output parameters**

| Parameter      | Description |
|----------------|-------------|
| string BlobUrl | A blob URL that has an embedded SAS token. Use the URL to download the exported data package. |

## Status check API 

Use the following APIs to check status. Use them during both import flows and export flows.

### GetExecutionSummaryStatus

Use the **GetExecutionSummaryStatus** API for both import jobs and export jobs. Use it to check the status of a data project execution job. This API works for both cloud deployments and on-premises deployments.

> [!NOTE]
> To get the final execution status, such as *Succeeded*, you need to create the package.

```csharp
POST /data/DataManagementDefinitionGroups/Microsoft.Dynamics.DataEntities.GetExecutionSummaryStatus
BODY
{"executionId":"<executionId>"}
```

Here's an example of a successful response.

```json
HTTP/1.1 200 OK
{
    "@odata.context":"https://<baseurl>/data/$metadata#Edm.String",
    "value":"<executionStatus>"
}
```

**Input parameters**

| Parameter          | Description |
|--------------------|-------------|
| string executionId | The execution ID of the data project run. The UI calls this ID the Job ID. |

**Output parameters**

| Parameter | Description |
|-----------|-------------|
| DMFExecutionSummaryStatus executionStatus | The execution status. Possible values include: Unknown, NotRun, Executing, Succeeded, PartiallySucceeded, Failed, Canceled. |

> [!NOTE]
> The file in Blob storage stays for seven days. After that period, it's automatically deleted.

## Get the list of errors

Use `GetExecutionErrors` to get the list of errors in a job execution. The API takes the execution ID as the parameter, and returns a set of error messages in a JSON list.

```json
POST /data/DataManagementDefinitionGroups/Microsoft.Dynamics.DataEntities.GetExecutionErrors
BODY
{"executionId":"<executionId>"}
```

## Import and export processes

The following illustration shows how the Data management package methods can be used to import data packages.

:::image type="content" source="./media/data-package-import.png" alt-text="Screenshot of data package file import that uses the Data management package methods.":::

The following illustration shows how the Data management package methods can be used to export data packages.

:::image type="content" source="./media/data-package-export.png" alt-text="Screenshot of data package file export that uses the Data management package methods.":::

A sample console application that showcases the data import and data export methods is available on GitHub. For more information, see <https://github.com/Microsoft/Dynamics-AX-Integration/tree/master/FileBasedIntegrationSamples/ConsoleAppSamples>.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
