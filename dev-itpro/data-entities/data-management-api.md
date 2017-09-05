---
# required metadata

title: Data management package integration API
description: This topic describes the data management package API for working with files in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition.
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

This topic describes the data management package API in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition, and when to use it.

## Choose an integration API
There are two sets of APIs that support file-based integration scenarios i: the data management package API and the recurring integration API. Both APIs support both data import and data export. The following table describes key decision points to use when deciding which API to use. 

| Decision point |    Recurring integration API                                         |    Data management package API                                                               |
|----------------------------|-------------------------------------------------------------|-------------------------------------------------------------------|
| Scheduling                 | Scheduling within Finance and Operations   | Scheduling external to Finance and Operations |
| Format                     | Files and data packages                                     | Only data packages                                                |
| Transformation             | Supports XSLT transformation if the data file format is XML | Transformations are external to the system                  |

If the recurring integrations API better meets your needs, see [Recurring integrations](recurring-integrations.md).

## Authentication and authorization
The data management API uses OAuth for authentication. The API must be called with a valid OAuth authentication token. The user context in which the API is called should also be established so that the proper security and user access rights can be established. 

When authenticating from the web client, a client ID is assigned to a specific user in **System administration** > **Setup** > **Azure Active Directory Applications**.

When authenticating from native clients, the user context is embedded in the authentication flow. 

## Import APIs

### Get Azure Writable Url API

This API is used to get a writable blob URL. Using this URL which has shared access token embedded in the URL, a data package can be uploaded to the Finance and Operations Azure Blob Storage container.

```
       DataManagementDefinitionGroups.GetAzureWriteUrl(string uniqueFileName)
	Return object: 
{
	string BlobId,
	String BlobUrl,
}

```

Input parameters:
**string uniqueFileName** A unique file name to track blob IDs. You can include a GUID to ensure a unique file name.

Output parameters:
**string BlobId**  The blob ID of the allocated blob conainer.
**string BlobUrl** A writable blob URL with an embedded shared access token to write to blob storage.		
     	
### Import from package API

The API is used to initiate an import from the data package that is uploaded to the Finance and Operations blob storage

```
DataManagementDefinitionGroups.ImportFromPackage(string packageUrl, 
                                              string definitionGroupId, 
                                              string executionId, 
                                              bool execute, 
                                              bool overwrite, 
                                              string legalEntityId)
```
Return object: 
**string executionId**

Input parameters:
| string packageUrl                                                  | The URL of the data package in Finance and Operations Azure Blob Storage |
|--------------------------------------------------------------------|-------------------------------------------------------------------------------------------|
| string definitionGroupId                                           | The name of the data project to import.                                                   |
| string executionId                                                 | The execution ID to use for the execution. If an empty ID is assigned, a new execution ID will be created.                                               |
                                                                                   |
| bool execute                                                       | True, if the target step should be executed, otherwise False.                                            |
| bool overwrite                                                     | True, if data should be overwritten, otherwise False.                                    |
| string legalEntityId                                               | The legal entity for the data import.                                                     |

Output parameters:
**string executionId**	The execution ID of the data import.

## Export APIs

### Export to package API
This API is used to initiate an export of a data package.

```
DataManagementDefinitionGroups.ExportToPackage(string definitionGroupId, 
      string packageName,
      string executionId, 
      bool reExecute, 
      string legalEntityId)
```

Return object: 
**string executionId**
	
Input parameters:
| string definitionGroupId                                           | The name of the data project to export data.       |
|--------------------------------------------------------------------|----------------------------------------------------|
| string packageName                                                 | The name to provide for the exported data package. |
| string executionId                                                 | The execution Id to use for the execution.   If an empty ID is assigned, a new execution ID will be created.       |
| bool reExecute                                                     | True, if it is an re-execution, otherwise False.   |
| string legalEntityId                                               | The legal entity for the data export.              |
	
#### Output parameters
**string executionId**	The execution ID of the data export.


### Get exported package Url API

This API is used to get the URL of the exported data package that was exported by called ExportToPackage.

```
DataManagementDefinitionGroups.GetExportedPackageUrl(string executionId)
```

Return object: 
**string BlobUrl**

Input parameters:
**string executionId**	The execution Id of the export data project.

Output parameters:
**string BlobUrl**	A blob URL with an embedded shared access token to download the exported data package.

## Check status API	

### Get execution summary status Url

```
DataManagementDefinitionGroups.GetExecutionSummaryStatus(string executionId)
```

Output Object: 
**DMFExecutionSummaryStatus executionStatus**

Input parameters:
**string executionId**	The execution Id of the data project.

Output parameters:
**DMFExecutionSummaryStatus executionStatus** 

Possible values:
- Unknown
- NotRun
- Executing
- Succeeded
- PartiallySucceeded
- Failed
- Canceled

The following diagram shows how the data management package APIs can be used to import data packages.

[!Data package file import using the data management package APIs](./media/data-package-import.png)
 
The following diagram shows how the data management package APIs can be used to export data packages.

[!Data package file export using the management package APIs](./media/data-package-export.png)
 
A sample console application is available on GitHub to showcase the data import and data export APIs.

For more information, see: 
https://github.com/Microsoft/Dynamics-AX-Integration/tree/master/FileBasedIntegrationSamples/ConsoleAppSamples

The following example demonstrates how to set up file-based import and export using the data package APIs.




