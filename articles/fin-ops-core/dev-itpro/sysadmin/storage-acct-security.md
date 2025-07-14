---
title: Finance and operations storage account security updates
description: This article describes the latest security enhancements in the finance and operations storage account.
author: mansijainms
ms.author: mansijain 
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/10/2025
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

The finance and operations environment doesn't share details about the managed identity that is used to connect to the storage account. Additionally, the platform runtime doesn't have access to the managed identity information.

### How does the platform code use managed identity to connect to the storage account when the identity isn't available?

An implementation of the **TokenCredential** object and token is regularly refreshed by using a service that runs behind the scenes.

### Previously, a connection string allowed unrestricted access to perform almost any operation on a storage account. After the introduction of role-based access control (RBAC) and managed identities, which permissions are now restricted or disabled?

We grant almost all the permissions that are required to perform operations in the data plane. Additionally, permissions that are related to containers, queues, and tables in the control plane are provided. However, storage account–level permissions and some network-related permissions are restricted.

### Does CloudInfrastructure.GetCsuStorageConnectionString() throw an error if the EnableSharingOfValidStorageConnectionString flight isn't enabled?

Yes. We're deprecating the **GetCsuStorageConnectionString()** API. We recommend that you use the **CloudStorageAccount**, **BlobServiceClient**, or **TableServiceClient** object that **SharedServiceUnitStorage** returns for interaction with the storage account.

The following APIs are available in **SharedServiceUnitStorage**:

- `public CloudStorageAccount GetSharedServiceUnitStorageAccount()`
- `public TableServiceClient GetSharedServiceTableServiceClient()`
- `public BlobServiceClient GetSharedServiceBlobServiceClient()`

### How can I get access to the connection string of the finance and operations managed storage account?

We plan to retire all APIs that provide access to the connection string, such as **CloudInfrastructure.GetCsuStorageConnectionString()**. Although there might be alternative ways to obtain a handle to the connection string, other restrictions are put in place to render those methods ineffective.

When the managed identity–based integration is enabled, it won't be possible to connect to the storage account by using connection strings shared through APIs outside the finance and operations process, such as interactive AOS, Batch AOS, or the Data Import/Export Framework (DIXF) service.

Because we're disabling the account access key at the storage account level, any access that uses the account access key won't work.

### What happens when I invoke CloudInfrastructure.GetCsuStorageConnectionString() in environments when the managed identity–based integration is also enabled?

When the managed identity–based integration is enabled, an invalid connection string is returned in this situation.

If you use the invalid connection string, all the existing constructs continue to work, if they're accessed within the AOS process space. The exceptions are those constructs that are tightly coupled with the access key, such as **GetSharedAccessSignature**.

For example, the following code continues to work as it is.

```
String connectionString = CloudInfrastructure.GetCsuStorageConnectionString();
CloudStorageAccount storageAccount = CloudStorageAccount.Parse(connectionString);
CloudBlobClient blobClient = cloudStorageAccount.CreateCloudBlobClient();
CloudBlobContainer blobContainer = blobClient.GetContainerReference(containerName);
```

### How does the code continue to work with invalid connection strings that are used within the AOS process space?

We intercept the outbound HTTPS requests that the storage software development kit (SDK) makes, to ensure that Azure Blob Storage treats the requests as if a client used a valid connection string to make them. This interception enables the operations to be processed as expected, even if you use the invalid connection string that is returned because of the managed identity-based integration.

### Can you provide more details about why GetSharedAccessSignature() fails, whereas other constructs continue to work?

When you invoke **GetSharedAccessSignature()** on a blob, container, queue, or other storage resources, the shared access signature (SAS) URL or token is generated within the SDK by using the account key that is stored in the **SharedAccessCredential** to sign the URL.

If **CloudStorageAccount** and other related objects are constructed by using an invalid account key, that invalid key is used to sign the SAS URL. Although the token/URL can be successfully generated, any attempt to use it to connect to the storage account fails and throws a "403 (Forbidden)" error, because the signature is invalid.

### Why does the SAS URL pattern that is generated by GetFileLink and other APIs in SharedServiceUnitStorage differ between the sandbox and production environments, or across different environments?

The SAS URL patterns might differ because the managed identity–based integration is enabled in one environment but not the other. When you connect to the storage account by using managed identity, a user-delegated SAS URL is generated instead of the SAS token or URL that is generated by using a connection string.

### Can I generate a user-delegated SAS URL by using WindowsAzure.Storage v9.3.3?

No, you can't generate a user-delegated SAS URL by using **WindowsAzure.Storage v9.3.3**, because it doesn't support this functionality.

### Can a user-delegated SAS URL that is generated by using WindowsAzure.Storage v12 or later work with a codebase that is written by using WindowsAzure.Storage v9.3.3?

Yes, a user-delegated SAS URL that is generated by using **Azure.Storage v12** works with **WindowsAzure.Storage v9.3.3** constructs. It's validated in the same way by using internal workflows and various test codes.

> [!NOTE]
> If you don't manually parse the SAS URL or token (by searching for various tokens, such as **se** and **st**, which might cause you to bump into a new token), you're OK, because the URL patterns are different.

### What known issues exist if the managed identity that is used is incompatible with previous libraries?

- You can't generate an SAS URL by using **GetSharedAccessSignature()**, regardless of the library that you use with managed identity.
- To generate a user-delegated SAS URL, you must use the **Azure.Storage.Blobs** SDK (v12 or later).
- Currently, user-delegated SAS URLs can't be generated for tables and queues. The Azure Storage team rolls out support for those resources. The tentative general availability (GA) date is March 2025. To use this feature, the SDK must be upgraded.
- User-delegated SAS URLs can't be generated for a period that is longer than seven days. This limit is a hard limit, and there are no plans to extend it.
- You can't generate a user-delegated SAS at the container level to modify a container-level attribute or check for container existence.

### Does this change affect connections to a customer-managed storage account from finance and operations apps (AOS/Interactive AOS, and so on)?

No, there's no impact. Additionally, no request that is made from those libraries is intercepted.

### Do you have any guidance about the use of code or libraries that are available in the platform code?

Refrain from using any classes or methods that are exposed in the **Microsoft.Dynamics.Clx.ServicesWrapper.Infrastructure.Interceptor** namespace, because they're intended for internal use only and are subject to change.

### Are there any logs to verify that only authorized access has occurred? Are those logs able available after deprecating the connection string? 

Once anonymous access and admin key-based authentication (for example, connection string) are disabled, access is only possible using [user delegated] SAS URLs or OAuth (via Managed Identity). Metrics, not logs, are available to track the type of authentication being used. These metrics are currently for internal use only and they're no plans to share them or expose them.

### Is the new method more secure than the connection string? If so, how? How could this become more secure? 

Yes, this is a more secure method for connecting to the storage account compared to using a connection string. Security needs should be addressed through a multi-pronged approach, including: 
- Disable anonymous access to the storage account. 
- Prevent the sharing of connection strings via public APIs. 
- Turn off access to the storage account via connection strings. 
- Upgrade the storage SDK in the platform repository to only support newer, supported versions (implemented in platform code). 
- These changes are at different stages of development, rollout, or discussion.

### Can the access string or replacement be rotated regularly? 

We're moving away from connection string, also known as account access key, and rotation of an account access key isn't needed.

### We have a process for LBD customers migrating from Dynamics 365 Finance on-premises (LBD) to cloud. Currently for the finance and operations attachments we provide customers with a SAS token. Is this affected by the changes? If so, do we need to have a way to help out customers migrate their attachments.

It works. If Managed Identity is enabled, a user-delegated SAS URL can be used to generate a SAS URL that can be shared with customers. However, a user-delegated SAS URL is valid for a maximum of seven days. Azure Storage doesn't support generating SAS URLs with a longer validity period. 

### Will a SAS URL that was created previously stop working once the storage account access key is disabled?

 Yes, previously created SAS URLs stop working when the account access key is disabled, because seven days are the maximum TimeToLive value (Validity of the URL). Therefore, the SAS URL expires and won't work after seven days.

### Resolving the Error: "The remote server returned an error: (409) Conflict" When Using File.UseFileFromURL for any file operations (Import/export/upload/downlaod)

This error may occur when the user-delegated SAS URL provided to the File.UseFileFromURL method is being truncated due to insufficient string length in the variable used.

**Cause:**
The user-delegated SAS URL, which is often long, may be cut off if the variable holding it isn't large enough to store the full value. This truncation results in an invalid or incomplete URL, triggering a 409 Conflict error from the remote server.

**Resolution**:
1. Check the Variable Type and Length:
- Ensure the variable used to store the SAS URL is of type string.
- Confirm that it has a minimum length capacity of 500 characters.
2. If You're Using an Extended Data Type (EDT):
- Replace the current EDT with one that supports longer strings.
- We recommend using the EDT SharedServiceUnitURL, which has a string length of 1,000 characters, sufficient to accommodate most SAS URLs.

By ensuring the variable can store the entire URL without truncation, the error should be resolved.

### UserDelegatedSASURL Length Consideration

UserDelegatedSASURL can be up to or slightly below 500 characters in length. To ensure reliability, it's recommended you treat the 500 characters as the minimum expected size. Always use a variable type that can safely accommodate the full URL as described in the resolution above.

> [!IMPORTANT]
> If the URL is truncated due to insufficient variable length, users may encounter errors such as (403) Forbidden, (404) Not Found, (409) Conflict, or PublicAccessNotPermitted-especially when the access key is disabled.

### Error: "403 (Forbidden): Server failed to authenticate the request."
This error may occur if you're using an old or cached connection string on finance and operations managed storage accounts. This is often due to secrets rotation following planned maintenance.

**What to check first:**
Review [What are the planned maintenance windows?
](/dynamics365/fin-ops-core/dev-itpro/deployment/plannedmaintenance-selfservice#windows). If the issue occurs after the scheduled maintenance window, proceed with the following resolution.

**Resolution**
If you're using or caching a connection string for the storage account, it may no longer be valid.
Retrieve a new connection string after the environment restarts to restore access. 
 

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
