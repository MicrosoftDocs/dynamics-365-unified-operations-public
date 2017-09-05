---
# required metadata

title: File-based integration APIs
description: This topic describes the integration APIs for working with files in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition.
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

# File-based integration APIs 

[!include[banner](../includes/banner.md)]

There are two primary sets of APIs that support file-based integration scenarios in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition: the recurring integration API and the data management platform package API. Both APIs support both data import and data export. This topic describes the differences between the APIs, and when we recommend using them.



| Decision point |    Recurring integration API                                         |    Data management package API                                                               |
|----------------------------|-------------------------------------------------------------|-------------------------------------------------------------------|
| Scheduling                 | Scheduling within Finance and Operations   | Scheduling external to Finance and Operations |
| Format                     | Files and data packages                                     | Only data packages                                                |
| Transformation             | Supports XSLT transformation if the data file format is XML | Transformations are external to the system                  |

Authentication and authorization
All the DMF APIs uses OAuth flow for authentication. All of the below APIs, unless noted, needs to be called with a valid OAuth authentication token in order to successfully call these APIs. 

Furthermore, the context of the user in which the APIs needs to be made should be established so that the proper security and user access rights can be established. 

For Client authentication flow, the client ID is assigned a specific user in System administration > Setup> Azure Active Directory Applications 

For native clients, user context is embedded in the authentication flow. 

Data Management Framework Package APIs 
Let’s look at the APIs available for importing DIXF packages into Dynamics 365 for Finance and Operations. 

Import APIs

1.	Get Azure Writable Url API

This API is used to get a writable blob url. Using this Url which has shared access token embedded in the url, a data package can be uploaded to the Dynamics 365 Finance and Operations Azure Blob Storage container.

       DataManagementDefinitionGroups.GetAzureWriteUrl(string uniqueFileName)
	Return object: 
{
	string BlobId,
	String BlobUrl,
}
	Input parameters:
	string uniqueFileName – A unique file name to track different blob Id.
       Note: You could use GUID to ensure a unique file name.

	Output parameters:
	string BlobId –  A blob Id of the allocated blob conainer.
 	string BlobUrl – A writable blob url with embedded shared access token to write to 
   the blob storage.		
     	
2.	Import from package API

The API is used to initiate an import from the data package that is uploaded to Dynamics Blob storage

DataManagementDefinitionGroups.ImportFromPackage(string packageUrl, 
                                              string definitionGroupId, 
                                              string executionId, 
                                              bool execute, 
                                              bool overwrite, 
                                              string legalEntityId)
Return object: string executionId

	Input parameters:
string packageUrl	The url of the data package within Dynamics 365 Finance and Operations Azure Blob Storage
string definitionGroupId	The name of the data project for import
string executionId	The execution Id to use for the execution.
Note: If assigned an empty Id, a new execution Id will be created.
bool execute	True, if execute target step, False otherwise.
bool overwrite	True, if data should be over written, False otherwise.
string legalEntityId	The legal entity for the data import.

	Output parameters:
string executionId	The execution id of the data import execution.

Export APIs
3.	Export to package API

The API is used to initiate an export of a data package.
DataManagementDefinitionGroups.ExportToPackage(string definitionGroupId, 
      string packageName,
      string executionId, 
      bool reExecute, 
      string legalEntityId)
Return object: string executionId
	
Input parameters:
string definitionGroupId	The name of the data project to export data.
string packageName	The name to provide for the exported data package.
string executionId	The execution Id to use for the execution.
Note: If assigned an empty Id, a new execution Id will be created.
bool reExecute	True, if it is an re-execution, False otherwise.
string legalEntityId	The legal entity for the data export.
	
Output parameters:
string executionId	The execution id of the data export execution.


4.	Get exported package Url API

The API is used to get the url of the exported data package that was exported by called ExportToPackage.

DataManagementDefinitionGroups.GetExportedPackageUrl(string executionId)

Return object: string BlobUrl

Input parameters:
string executionId	The execution Id of the export data project.

Output parameters:
string BlobUrl	A blob url with embedded shared access token to download the exported data package.

Check Status API	

5.	Get execution summary status Url

DataManagementDefinitionGroups.GetExecutionSummaryStatus(string executionId)

Output Object: DMFExecutionSummaryStatus executionStatus

Input parameters:
string executionId	The execution Id of the data project.

Output parameters:
DMFExecutionSummaryStatus executionStatus
	The status of the execution.
Possible values:
   Unknown
   NotRun
   Executing
   Succeeded
   PartiallySucceeded
   Failed
   Canceled

	


The following diagrams showcase, how the above APIs can be used to import and export the data packages
Data package file import using the DMF Package APIs
 
Data package file import using the DMF Package APIs
 
The following sample console application showcases the data import and data export APIs
https://github.com/Microsoft/Dynamics-AX-Integration/tree/master/FileBasedIntegrationSamples/ConsoleAppSamples

The following lab explains how to setup file based import and export using the data package APIs using the above sample code



For more information:
[Recurring integrations](recurring-integrations.md)

