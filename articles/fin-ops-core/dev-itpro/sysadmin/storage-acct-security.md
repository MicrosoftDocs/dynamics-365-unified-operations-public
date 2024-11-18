---
title: Finance and operations storage account security updates
description: This article describes the latest security enhancements in the finance and operations storage account.
author: mansijainms
ms.author: mansijain 
ms.topic: conceptual
ms.custom: 
  - bap-template
ms.date: 11/18/2024
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

The **Microsoft.Dynamics.Clx.ServicesWrapper.CloudInfrastructure::GetCsuStorageConnectionString()** public method is being deprecated. Learn more in [End of support for sharing storage account connection strings via public API GetCsuStorageConnectionString](../../fin-ops/get-started/removed-deprecated-features-platform-updates.md#end-of-support-for-sharing-storage-account-connection-strings-via-public-api-getcsustorageconnectionstring).

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
1. In the CHE, restart Application Object Server (AOS) and the Batch service.

### Which managed identity is used to connect to the storage account?

The finance and operations environment doesn't share the details about the managed identity used to connect to the storage account. Also, the platform runtime doesn't have access to the managed identity information.

### How does the platform code connect to the storage account using managed identity when the identity isn't available?

An implementation of the TokenCredential object and token is refreshed regularly by a service behind the scenes.

### Previously, a connection string allowed unrestricted access to perform almost any operation on a storage account. With the introduction of RBAC and managed identities, which permissions are now restricted or disabled?

We have granted almost all the necessary permissions to perform operations in the data plane. Permissions related to containers, queues, and tables in the control plane are usually provided also. However, storage account-level permissions and certain network-related permissions are restricted.

### CloudInfrastructure.GetCsuStorageConnectionString() throws error, if flight EnableSharingOfValidStorageConnectionString isn't enabled?

Yes, we're deprecating the **GetCsuStorageConnectionString()** API. We recommend using the **CloudStorageAccount**, **BlobServiceClient**, or **TableServiceClient** objects returned by the **SharedServiceUnitStorage** for interacting with the storage account.

The following APIs are available in SharedServiceUnitStorage: 

```
public CloudStorageAccount GetSharedServiceUnitStorageAccount() 
public TableServiceClient GetSharedServiceTableServiceClient() 
public BlobServiceClient GetSharedServiceBlobServiceClient()
```

### How can I get access to the connection string of the finance and operations managed storage account?

We plan to retire all APIs that provide access to the connection string, such as **CloudInfrastructure.GetCsuStorageConnectionString()**. While there may be alternative ways to obtain a handle to the connection string, other restrictions will be put in place to render those methods ineffective.

In the future, when the managed identity-based integration is enabled, it won't be possible to connect to the storage account using connection strings shared through APIs outside the finance and operations process, such as through interactive AOS, Batch AOS, or the DIXF service.

We're disabling the account access key at the storage account level, meaning that any access using the account access key won't work.

### What happens when I invoke CloudInfrastructure.GetCsuStorageConnectionString() in environments when managed identity-based integration is also enabled?

An invalid connection string is returned when the managed identity-based integration is enabled.

When you use the invalid connection string, all the existing constructs work as long as they're accessed within AOS process space except for those that are tightly coupled with access key like GetSharedAccessSignature.

For example, the following code would continue to work as it is.

```
String connectionString = CloudInfrastructure.GetCsuStorageConnectionString();
CloudStorageAccount storageAccount = CloudStorageAccount.Parse(connectionString);
CloudBlobClient blobClient = cloudStorageAccount.CreateCloudBlobClient();
CloudBlobContainer blobContainer = blobClient.GetContainerReference(containerName);
```

### How will the code continue to work with invalid connection strings used within AOS process space?

We intercept the outbound HTTPs requests made by the storage SDK to ensure that Azure Blob Storage treats the requests as if they were made by a client using a valid connection string. This intercept allows the operations to be processed as expected, even when using the invalid connection string returned due to the managed identity-based integration.

### Can you provide more details on why the GetSharedAccessSignature() fails while other constructs continue to work?

When you invoke GetSharedAccessSignature() on a blob, container, queue, or other storage resources, the SAS URL ortoken generates within the SDK by signing the URL using the account key that's stored in the SharedAccessCredential.

When we construct the CloudStorageAccount and other related objects using an invalid account key, the SAS URL is signed with this invalid key. Although the token/URL can be generated successfully, any attempt to use it to connect to the storage account fails with a **403 (Forbidden) error**, since the signature is invalid.

### Why does the SAS URL pattern generated by GetFileLink and other APIs in SharedServiceUnitStorage differ between the sandbox environment and production, or across different environments?

They may differ because managed identity-based integration is enabled in one and not the other. When we connect to storage account using managed identity, we generate user delegated SAS url instead of the shared access signature token or URL generated using connection string.

### Can you generate a User Delegated SAS (UDS) URL using WindowsAzure.Storage v9.3.3?

No, you can't generate a User Delegated SAS URL using **WindowsAzure.Storage v9.3.3** because it doesn't support this functionality.

### Can a user delegated SAS URL generate using Azure.Storage v12 or later work with a codebase written using WindowsAzure.Storage v9.3.3?

Yes, the user delegated SAS url generated using Azure.Storage v12 works with **WindowsAzureStorage v9.3.3** constructs. It's validated the same with internal workflows and various test code.

> [!NOTE]
> As long you aren’t manually parsing the SAS URL or token [searching for various tokens, like se and st, as u might bump into new token], we're good, because the URL patterns are different.

### What known issues exists using a managed identity that's incompatible with previous libraries?

1. You can't generate a SAS URL using **GetSharedAccessSignature()** regardless of the library you use with managed identity.
1. To generate a User Delegated SAS URL, you must use the Azure.Storage.Blobs SDK (v12 and later).
1. User Delegated SAS URLs can't be generated for Tables and Queues at this time. Support for these resources will be rolled out by the Azure Storage team, with a tentative general availability (GA) date of March 2025. To use this feature, the SDK needs to be upgraded.
1. User Delegated SAS URLs can't be generated for a period longer than seven days. This limit is a hard limit, and there aren't plans to extend it.
1. You can’t generate user delegated SAS at container level to modify container level attribute or use for check for container existence.

### Is connecting to a customer-managed storage account from finance and operations apps (AOS/Interactive AOS, etc.) impacted by this change?

No, there isn't any impact, nor would any request made from those libraries be intercepted.

### Do you have any guidance on the usage of code or libraries available in platform code?

Refrain from using any classes or methods exposed in the **Microsoft.Dynamics.Clx.ServicesWrapper.Infrastructure.Interceptor** namespace becasue they're intended for internal use only and are subject to change.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
