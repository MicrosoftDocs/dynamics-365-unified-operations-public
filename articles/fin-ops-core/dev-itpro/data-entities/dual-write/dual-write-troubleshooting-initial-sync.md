---
# required metadata

title: Troubleshoot issues during initial synchronization
description: This topic provides troubleshooting information that can help you fix issues that might occur during initial synchronization.
author: RamaKrishnamoorthy 
manager: AnnBe
ms.date: 03/16/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: ramasri
ms.dyn365.ops.version: 
ms.search.validFrom: 2020-03-16

---

# Troubleshoot issues during initial synchronization

[!include [banner](../../includes/banner.md)]

[!include [preview-banner](../../includes/preview-banner.md)]

This topic provides troubleshooting information for dual-write integration between Finance and Operations apps and Common Data Service. Specifically, it provides information that can help you fix issues that might occur during initial synchronization. 

> [!IMPORTANT]
> Some of the issues that this topic addresses might require either the system admin role or Microsoft Azure Active Directory (Azure AD) tenant admin credentials. The section for each issue explains whether a specific role or credentials are required.

## Check for initial synchronization errors in a Finance and Operations app

After you enable the mapping templates, the status of the maps should be **Running**. If the status is **Not running**, errors occurred during initial synchronization. To view the errors, select the **Initial sync details** tab on the **Dual-write** page.

![Initial sync details tab](media/initial_sync_status.png)

## You can't complete initial synchronization: 400 Bad Request

**Required role to fix the issue:** System admin

You might receive the following error message when you try to run the mapping and initial synchronization:

*The remote server returned an error: (400) Bad Request.), AX export encountered an error*

Here is an example of the full error message.

```console
Dual write Initial Sync completed with status: Error. Following are the details:
Executed leg: From AX Financial dimensions to CRM msdyn_dimensionattributes
with exported records count: 0, ImportRecordsErrorCount: 0,
ImportRecordsInsertedCount: 0 and ImportRecordsUpdatedCount: 0
ErrorsDetails:
Dual write Initial sync failed
Message: ([Bad Request], The remote server returned an error: (400) Bad Request.), AX export encountered an error
Stacktrace: at
Microsoft.Dynamics.Integrator.QueryGenerator.AxClient.\<ExportAxPackage\>d__16.MoveNext()
in X:\\bt\\1024532\\repo\\src\\Core\\QueryGenerator\\AxClient.cs:line 265
\--- End of stack trace from previous location where exception was thrown ---
at System.Runtime.ExceptionServices.ExceptionDispatchInfo.Throw()
at System.Runtime.CompilerServices.TaskAwaiter.HandleNonSuccessAndDebuggerNotification(Task task)
at Microsoft.D365.ServicePlatform.Context.ServiceContext.Activity.\<ExecuteAsync\>d__11\`2.MoveNext()
\--- End of stack trace from previous location where exception was thrown ---
```

If this error occurs consistently, and you can't complete the initial synchronization, follow these steps to fix the issue.

1. Sign in to the virtual machine (VM) for the Finance and Operations app.
2. Open Microsoft Management Console. 
3. In the **Services** pane, make sure that the Microsoft Dynamics 365 Data import export framework service is running. Restart it if it has been stopped, because the initial synchronization requires it.

## Initial synchronization error: 403 Forbidden

You might receive the following error message during initial synchronization:

*(\[Forbidden\], The remote server
returned an error: (403) Forbidden.), AX export encountered an error*

To fix the issue, follow these steps.

1. Sign in to the Finance and Operations app.
2. On the **Azure Active Directory applications** page, delete the **DtAppID** client, and then add it again.

![List of Azure AD applications](media/aad_applications.png)

## Self-reference failures during initial synchronization

You might receive an error message that resembles the following example if any of your mappings have self-references:

*On the Vendors V2, the following error: Record Id: new record, ErrorMessage:
Couldn't resolve the guid for the field:
msdyn\_invoicevendoraccountnumber.msdyn\_vendoraccountnumber. The lookup value was
not found: CN-001. Try this URL(s) to check if the reference data exists:
`https://sampleorg.crm.dynamics.com/api/data/v9.0/msdyn_vendors?$select=msdyn_vendoraccountnumber,msdyn_vendorid&$filter=msdyn_vendoraccountnumber`
eq 'CN-001'*

This type of error occurs during initial synchronization of mappings that have self-references. In the preceding example, the field invoice account references the vendor entity.

To fix the issue, you might have to run the mapping two times before the initial synchronization is successful.

