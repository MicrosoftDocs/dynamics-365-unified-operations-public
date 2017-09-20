---
# required metadata

title: Data management package integration API
description: This topic describes the data management framework's package REST API for integrating with Microsoft Dynamics 365 for Finance and Operations, Enterprise edition using data packages.
author: Sunil-Garg
manager: 09/11/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: margoc
ms.search.scope: AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sunilg
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Data management package API 

[!include[banner](../includes/banner.md)]

This topic describes the data management framework's package REST API for integrating with Microsoft Dynamics 365 for Finance and Operations, Enterprise edition, using data packages.

## Choosing an integration API
There are two APIs in Finance and Operations that support file-based integration scenarios: the data management platform's package API and the recurring integrations API. Both APIs support both data import and data export scenarios. The following table describes key decision points to use when deciding which API to use. 

| Decision point             |    Recurring integrations API                               |    Data management package API                                    |
|----------------------------|-------------------------------------------------------------|-------------------------------------------------------------------|
| Scheduling                 | Scheduling within Finance and Operations                    | Scheduling external to Finance and Operations                     |
| Format                     | Files and data packages                                     | Only data packages                                                |
| Transformation             | Supports XSLT transformation if the data file format is XML | Transformations are external to the system                        |
| Supported protocols        | SOAP and REST                                               | REST                                                              |
| Service Type               | Custom Service                                              | OData action                                                      |
| Availabiity                | RTW+                                                        | Platform Update 5 and above                                       |

If the recurring integrations API better meets your needs, see [Recurring integrations](recurring-integrations.md).

## Authorization
The data management platform's package API uses OAuth 2.0 for authorizing access. The API must be called with a valid OAuth access token. You can find more details about OAuth 2.0 and AAD [here](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-protocols-oauth-code). 

> Note: When using Client Credentials Grant flow, Dynamics 365 for Finance and Operations maintains an Access Control List which can be found under **System administration** > **Setup** > **Azure Active Directory Applications**. This form captures the approved client Ids and the user security mapping that should be enforced when the APIs is called using this flow.

## Import APIs
The following APIs are used for performing file (data package) imports.

### GetAzureWritableUrl

This API is used to get a writable blob URL. Using this method, which has shared access token embedded in the URL, a data package can be uploaded to the Finance and Operations Azure Blob Storage container.

```CSharp
POST /data/DataManagementDefinitionGroups/Microsoft.Dynamics.DataEntities.GetAzureWriteUrl

BODY
{  
   "uniqueFileName":"<string>",      
}
```
A successful sample response would look as follows

```json
HTTP/1.1 200 OK

{  
   "@odata.context":"https://<baseurl>/data/$metadata#Edm.String",
   "value":{  
      "BlobId":"{<GUID>}",
      "BlobUrl":"https://<baseurl_id>.blob.core.windows.net/dmf/<uniqueFileName>?<SAS Token>"
   }
}
```

Input parameters: 

| **Parameter**                | **Description**                         |
|------------------------------|-----------------------------------------|
| **string packageUrl**        | A unique file name to track blob IDs. You can include a GUID to ensure a unique file name. |

Output parameters: 

| **Parameter**                | **Description**                         |
|------------------------------|-----------------------------------------|
| **string BlobId**            | The blob ID of the allocated blob conainer. |
| **string BlobUrl**           | A writable blob URL shared access signature to write to blob storage. |

> Note: The shared access signature is only valid within the expiry time stamped. Any request isssued after the time expiry will result in error. You can read more about this [here](https://docs.microsoft.com/en-us/azure/storage/common/storage-dotnet-shared-access-signature-part-1)


### ImportFromPackage

This API is used to initiate an import from the data package that is uploaded to the Finance and Operations's azure blob storage.

```CSharp
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

A successful sample response would look as follows

```json
HTTP/1.1 200 OK

{  
   "@odata.context":"https://<baseurl>/data/$metadata#Edm.String",
   "value":{  
      "value":"<executionId>"
   }
}
```

Input parameters: 

| **Parameter**                | **Description**                |
|--------------------------|--------------------------------------------------------------------------------------------------|
| **string packageUrl**        | The URL of the data package within the Azure Blob Storage associated with Finance and Operations |
| **string definitionGroupId** | The name of the data project for import                                                          |
| **string executionId**       | The ID to use for the job. If an empty ID is assigned, a new execution ID will be created.       |
| **bool execute**             | Set to True to run the target step, otherwise False.                                             |
| **bool overwrite**           | Set to True if data should be overwritten, otherwise False.                                      |
| **string legalEntityId**     | The legal entity for the data import.                                                            |                                                         |

Output parameters:
| **Parameter**                | **Description**                         |
|------------------------------|-----------------------------------------|
| **string executionId**       | The execution ID of the data import. |

## Export APIs
The following APIs are used for performing file (data package) exports.

### ExportToPackage
This API is used to initiate an export of a data package.

```
DataManagementDefinitionGroups.ExportToPackage(string definitionGroupId, 
      string packageName,
      string executionId, 
      bool reExecute, 
      string legalEntityId)
```

Input parameters: 

| **Parameter**                | **Description**                                                                                |
|--------------------------|--------------------------------------------------------------------------------------------|
| **string definitionGroupId** | The name of the data project for export.                                                    |
| **string packageName**       | The name of the exported data package.                                                     |
| **string executionId**       | The ID to use for the job. If an empty ID is assigned, a new execution ID will be created. |
| **bool reExecute**           | Set to True to run the target step, otherwise False.                                       |
| **string legalEntityId**     | The legal entity for the data import.                                                      |
	
Output parameters:
**string executionId**	The execution ID of the data export.


### GetExportedPackageUrl

This API is used to get the URL of the exported data package that was exported by called ExportToPackage.

```
DataManagementDefinitionGroups.GetExportedPackageUrl(string executionId)
```

Return object: 
**string BlobUrl**

Input parameters:
**string executionId**	The execution ID of the export data project.

Output parameters:
**string BlobUrl**	A blob URL with an embedded shared access token to download the exported data package.

## Status check APIs	
The following APIs are used to check status.

### GetExecutionSummaryStatus

This API is used for both import and export jobs to check the status of a data project execution.

```CSharp
POST /data/DataManagementDefinitionGroups/Microsoft.Dynamics.DataEntities.GetExecutionSummaryStatus

BODY
{"executionId":"<executionId>"}
```
A successful sample response would look as follows

```json
HTTP/1.1 200 OK

{  
   "@odata.context":"https://<baseurl>/data/$metadata#Edm.String",
   "value":{  
      "value":"<executionStatus>"
   }
}
```

Input parameters: 

| **Parameter**                | **Description**                         |
|------------------------------|-----------------------------------------|
| **string executionId**       | The execution ID of the data project run.      |


Output parameters:
| **Parameter**                | **Description**                         |
|------------------------------|-----------------------------------------|
| **DMFExecutionSummaryStatus executionStatus**       | The execution status. |

Possible values for execution status :
- Unknown
- NotRun
- Executing
- Succeeded
- PartiallySucceeded
- Failed
- Canceled 


## Import and export processes 
The following diagram shows how the data management package methods can be used to import data packages.

![Data package file import using the data management package methods](./media/data-package-import.png)
 
The following diagram shows how the data management package methods can be used to export data packages.

![Data package file export using the management package methods](./media/data-package-export.png)
 
A sample console application is available on GitHub to showcase the data import and data export methods.

For more information, see: 
https://github.com/Microsoft/Dynamics-AX-Integration/tree/master/FileBasedIntegrationSamples/ConsoleAppSamples



