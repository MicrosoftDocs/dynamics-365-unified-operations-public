---
title: Finance and operations storage account security updates
description: This article describes the latest security enhancements in the finance and operations storage account.
author: mansijainms
ms.author: mansijain 
ms.topic: conceptual
ms.custom: 
  - bap-template
ms.date: 09/12/2024
ms.reviewer: twheeloc
ms.search.region: Global
ms.search.validFrom: 2024-09-12
ms.dyn365.ops.version: 
---

# Finance and operations storage account security updates

[!include [banner](../../../finance/includes/banner.md)]

This article describes the latest security enhancements in the finance and operations storage account.

## Frequently asked questions

### I receive the following error on my developer machine/customer-hosted environment: "Fetching a valid storage connection string is disabled." How can I fix this error?

The `Microsoft.Dynamics.Clx.ServicesWrapper.CloudInfrastructure::GetCsuStorageConnectionString()` public method is being deprecated. Learn more in [End of support for sharing storage account connection strings via public API GetCsuStorageConnectionString](../../fin-ops/get-started/removed-deprecated-features-platform-updates.md#end-of-support-for-sharing-storage-account-connection-strings-via-public-api-getcsustorageconnectionstring).

If the flight is set to *false* by default, an issue occurs when changes are deployed in developer environments or customer-hosted environments (CHEs). In this case, you receive the following error on your developer machine:

> EnableSharingOfValidStorageConnectionString is false. Fetching a valid storage connection string has been disabled.

If you receive the error, follow these steps.

1. In Microsoft SQL Server Management Studio (SSMS), run the following query.

    ```sql
    declare @flightName NVARCHAR(100) = 'EnableSharingOfValidStorageConnectionString';
    IF NOT EXISTS (SELECT TOP 1 1 FROM SysFlighting WHERE flightName = @flightName)
    INSERT INTO SYSFLIGHTING(FLIGHTNAME,ENABLED, FLIGHTSERVICEID,PARTITION)
    SELECT @flightName, 1, 12719367,RECID FROM DBO.[PARTITIONS];
    ELSE
    UPDATE SysFlighting SET enabled = 1, flightServiceId = 12719367 WHERE flightName = @flightName;
    select * from SysFlighting where flightName = 'EnableSharingOfValidStorageConnectionString';
    ```

2. In the CHE, restart Application Object Server (AOS) and the Batch service.

###What managed identity is used to connect to the storage account? 

The FinOps environment will not share the details of the managed identity used to connect to the storage account. In fact, the platform runtime also does not have access to the managed identity information. 

###How does the platform code connect to the storage account using managed identity, if the identity is available? 

We have our own implementation of TokenCredential object and token is refreshed by certain service regularly behind the scenes. 

###Previously, a connection string allowed unrestricted access to perform almost any operation on a storage account. With the introduction of RBAC and managed identities, which permissions are now restricted or disabled? 

We have granted almost all the necessary permissions to perform operations in the data plane, and for the most part, permissions related to containers, queues, and tables in the control plane are also provided. However, storage account-level permissions and certain network-related permissions have been restricted. 

###CloudInfrastructure.GetCsuStorageConnectionString() throws error, if flight EnableSharingOfValidStorageConnectionString is not enabled)? 

Yes, we are deprecating the GetCsuStorageConnectionString() API. 
We recommend using the CloudStorageAccount, BlobServiceClient, or TableServiceClient objects returned by the SharedServiceUnitStorage for interacting with the storage account. 

The following APIs are available in SharedServiceUnitStorage: 
public CloudStorageAccount GetSharedServiceUnitStorageAccount() 
public TableServiceClient GetSharedServiceTableServiceClient() 
public BlobServiceClient GetSharedServiceBlobServiceClient() 

###How can I get access to the connection string of the finops managed storage account? 

We plan to retire all APIs that provide access to the connection string, such as CloudInfrastructure.GetCsuStorageConnectionString(). While there may be alternative ways to obtain a handle to the connection string, additional restrictions will be put in place that will render those methods ineffective. 

In the future, when the managed identity-based integration is enabled, it will no longer be possible to connect to the storage account using connection strings shared through APIs outside the FinOps process, such as through interactive AOS, Batch AOS, or the DIXF service.  

We will be disabling the account access key at the storage account level, meaning that any access using the account access key will no longer work. 

###What happens when I invoke CloudInfrastructure.GetCsuStorageConnectionString() in environments when managed identity-based integration is also enabled? 

We would be returning a invalid connection string, as and when managed identity-based integration is enabled. 

Using the invalid connection string, all the existing constructs would work as long as they are accessed within AOS process space except for those that are tightly coupled with access key like GetSharedAccessSignature.  

Say for example the below code would continue to work as it is 

 String connectionString = CloudInfrastructure.GetCsuStorageConnectionString() 
 CloudStorageAccount storageAccount = CloudStorageAccount.Parse(connectionString); 
 CloudBlobClient blobClient = cloudStorageAccount.CreateCloudBlobClient(); 
 CloudBlobContainer blobContainer = blobClient.GetContainerReference(containerName) 

###How can will the code continue to work with invalid connection string be still used within AOS process space? 

We will intercept the outbound HTTPs requests made by the storage SDK to ensure that Azure Blob Storage treats the requests as if they were made by a client using a valid connection string. This will allow the operations to be processed as expected, even when using the invalid connection string returned due to the managed identity-based integration. 

###Can you provide more details on why the GetSharedAccessSignature() fails while other constructs continue to work? 

When you invoke GetSharedAccessSignature() on a blob, container, queue, or other storage resources, the SAS URL/token is generated within the SDK by signing the URL using the account key stored in the SharedAccessCredential. 

When we construct the CloudStorageAccount and other related objects using an invalid account key, the SAS URL will be signed with this invalid key. Although the token/URL can be generated successfully, any attempt to use it to connect to the storage account will fail with a 403 (Forbidden) error, since the signature is invalid. 

###Why does the SAS URL pattern generated by GetFileLink and other APIs in SharedServiceUnitStorage differ between the sandbox environment and production, or across different environments? 

It could be because managed identity-based integration is enabled in one v/s other. When we connect to storage account using managed identity, we generate user delegated SAS url v/s shared access signature token/URL generated using connection string. 

###No, you cannot generate a User Delegated SAS (UDS) URL using WindowsAzure.Storage v9.3.3? 

No, you cannot generate a User Delegated SAS URL using WindowsAzure.Storage v9.3.3, as it does not support this functionality. 

###Can a User Delegated SAS URL generate using Azure.Storage v12 or later work with a codebase written using WindowsAzure.Storage v9.3.3? 

Yes, the user delegated SAS url generated using Azure.Storage v12 can work with WindowsAzureStorage v9.3.3 constructs, we have validated the same with internal workflows and various test code.

Caveat: As long you aren’t manually parsing the SAS URL or token [searching for various token like se, st, as u might bump into new token], we are good, because the URL patterns are different.  

###What is the known issue that exist using managed identity that is incompatible to those in previous libraries /version? 

1. You cannot generate a SAS URL using GetSharedAccessSignature() regardless of the library you use using managed identity. 
2. To generate a User Delegated SAS URL, you must use the Azure.Storage.Blobs SDK (v12 and later). 
3. User Delegated SAS URLs cannot be generated for Tables and Queues at this time. Support for these resources will be rolled out by the Azure Storage team, with a tentative general availability (GA) date of March 2025. To use this feature, the SDK will need to be upgraded. 
4. User Delegated SAS URLs cannot be generated for a period longer than 7 days. This is a hard limit, and there are no plans to extend it. 
5. One can’t generate user delegated SAS at container level to modify container level attribute or use for check for container existence ..etc. 

###Will connecting to a customer-managed storage account from FinOps (AOS/Interactive AOS, etc.) be impacted by this change? 

No, there won’t be any impact, nor we would be intercepting* any request made from those libraries. 

###Any Guidance with respect to the usage of code or libraries available in platform code? 

Please refrain from using any classes or methods exposed in the Microsoft.Dynamics.Clx.ServicesWrapper.Infrastructure.Interceptor namespace, as they are intended for internal use only and are subject to change. 
