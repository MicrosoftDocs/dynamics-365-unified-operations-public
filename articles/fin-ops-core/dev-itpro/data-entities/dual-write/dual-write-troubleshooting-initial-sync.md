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

## Self-reference or circular-reference failures during initial synchronization

You might receive an error messages if any of your mappings have self-references or circular references. The errors fall into these categories:

- [Vendors V2 to msdyn_vendors entity mapping](#error-vendor-map)
- [Customers V3 to Accounts entity mapping](#error-customer-map)

## <a id="error-vendor-map"></a>Resolve an error in Vendors V2 to msdyn_vendors entity mapping

You might run into the following initial sync errors on the **Vendors V2** to **msdyn_vendors** mapping if the entities have existing records with values in the **PrimaryContactPersonId** and **InvoiceVendorAccountNumber** fields. This because **InvoiceVendorAccountNumber** is a self-referencing field, and **PrimaryContactPersonId** is a circular reference in the vendor mapping.

*Couldn't resolve the guid for the field: <field>. The lookup was not found: <value>. Try this URL(s) to check if the reference data exists: https://focdsdevtest2.crm.dynamics.com/api/data/v9.0/<entity>?$select=<field>&$filter=<field> eq <value>*

Here are a couple of examples:

- *Couldn't resolve the guid for the field: msdyn_vendorprimarycontactperson.msdyn_contactpersonid. The lookup was not found: 000056. Try this URL(s) to check if the reference data exists: https://focdsdevtest2.crm.dynamics.com/api/data/v9.0/contacts?$select=msdyn_contactpersonid.contactid&$filter=msdyn_contactpersonid eq '000056'*
- *Couldn't resolve the guid for the field: msdyn_invoicevendoraccountnumber.msdyn_vendoraccountnumber. The lookup was not found: V24-1. Try this URL(s) to check if the reference data exists: https://focdsdevtest2.crm.dynamics.com/api/data/v9.0/msdn_vendors?$select=msdyn_vendoraccountnumber,msdyn_vendorid&$filter=msdyn_vendoraccountnumber eq 'V24-1'*

If you have records with values in these fields in the vendor entity follow the steps in the below section to complete initial sync successfully.

1. In the Finance and Operations app, delete the **PrimaryContactPersonId** and **InvoiceVendorAccountNumber** fields from the mapping and save the changes.

    1. Navigate to the dual-write mapping page for **Vendors V2 (msdyn_vendors)**, and select the **Entity mappings** tab. In the left filter, select **Finance and Operations apps.Vendors V2**. In the right filter, select **Sales.Vendor**.

    2. Search for **primarycontactperson** to find the source field **PrimaryContactPersonId**.
    
    3. Click the **Actions** button, and select **Delete**.
    
        ![self or circular reference 3](media/vend_selfref3.png)
    
    4. Repeat to delete the **InvoiceVendorAccountNumber** field.
    
        ![self or circular reference 3](media/vend_selfref4.png)
    
    5. Save the mapping changes.

2. Disable the change tracking for the **Vendors V2** entity.

    1. Navigate to **Data management \> Data Entities**.
    
    2. Select the **Vendors V2** entity.
    
    3. Click **Options** from the menu bar, and then **Change tracking**.
    
        ![self or circular reference 5](media/selfref_options.png)
    
    4. Click **Disable Change Tracking**.
    
        ![self or circular reference 6](media/selfref_tracking.png)

3. Run the initial sync of **Vendors V2 (msdyn_vendors)** mapping. The initial sync should run successfully without any errors.

4. Run the initial sync for the **CDS Contacts V2 (contacts)** mapping. You must sync this mapping if you want to sync primary contact field on vendors entity as the contacts records also need to be initial synced.

5. Add the fields **PrimaryContactPersonId** and **InvoiceVendorAccountNumber** back to the **Vendors V2 (msdyn_vendors)** mapping and save the mapping.

6. Run the initial sync again for the **Vendors V2 (msdyn_vendors)** mapping. All the records will be synced, because change tracking is disabled.

7. Enable change tracking for the **Vendors V2** entity.

## <a id="error-customer-map"></a>Resolve an error in Customers V3 to Accounts entity mapping

You might run into the following initial sync errors on the **Customers V3** to **Accounts** mapping if the entities have existing records with values in the **Primary Contact** and **InvoiceAccount** fields. This because **InvoiceAccount** is a self-referencing field, and **Primary Contact** is a circular reference in the vendor mapping.

*Couldn't resolve the guid for the field: <field>. The lookup was not found: <value>. Try this URL(s) to check if the reference data exists: https://focdsdevtest2.crm.dynamics.com/api/data/v9.0/<entity>?$select=<field>&$filter=<field> eq <value>*

- *Couldn't resolve the guid for the field: primarycontactid.msdyn_contactpersonid. The lookup was not found: 000056. Try this URL(s) to check if the reference data exists: https://focdsdevtest2.crm.dynamics.com/api/data/v9.0/contacts?$select=msdyn_contactpersonid.contactid&$filter=msdyn_contactpersonid eq '000056'*
- *Couldn't resolve the guid for the field: msdyn_billingaccount.accountnumber. The lookup was not found: 1206-1. Try this URL(s) to check if the reference data exists: https://focdsdevtest2.crm.dynamics.com/api/data/v9.0/accounts?$select=accountnumber.account&$filter=accountnumber eq '1206-1'*

If you have records with values in these fields in the customer entity follow the steps in the below section to complete initial sync successfully. You can use this approach for any out-of-the-box entities such Accounts and Contacts.

1. In the Finance and Operations app, delete the fields **ContactPersonID** and **InvoiceAccount** from the **Customers V3 (accounts)** mapping and save the mapping.

    1. Navigate to the dual-write mapping page for **Customers V3 (accounts)**, select the **Entity mappings** tab. In the left filter, select **Finance and Operations app.Customers V3**. In the right filter, select **Common Data Service.Account**.

    2. Search for **contactperson** to find the source field **ContactPersonID**.
    
    3. Click the **Actions** button, and select **Delete**.
    
        ![self or circular reference 3](media/cust_selfref3.png)
    
    4. Repeat to delete the **InvoiceAccount** field.
    
        ![self or circular reference](media/cust_selfref4.png)
    
    5. Save the mapping changes.

2. Disable the change tracking for the **Customers V3** entity.

    1. Navigate to **Data management \> Data Entities**.
    
    2. Select the **Customers V3** entity.
    
    3. Click **Options** from the menu bar, and then **Change tracking**.
    
        ![self or circular reference 5](media/selfref_options.png)
    
    4. Click **Disable Change Tracking**.
    
        ![self or circular reference 6](media/selfref_tracking.png)

3. Run the initial sync for the **Customers V3 (Accounts)** mapping. The initial sync should run successfully without any errors.

4. Run the initial sync for the **CDS Contacts V2 (contacts)** mapping. There are 2 maps with the same name. Select the one with the description **Dual-write template for sync between FO.CDS Vendor Contacts V2 to CDS.Contacts. Requires new package \[Dynamics365SupplyChainExtended\].** on the **Details** tab of the map.

5. Add the fields **InvoiceAccount** and **ContactPersonId** back to the **Customers V3 (Accounts)** mapping and save the mapping. Now, both the **InvoiceAccount** field and the **ContactPersonId** field are again part of live sync mode. In the next step, you complete the initial sync for these fields.

6. Run the initial sync again for the **Customers V3 (Accounts)** mapping. Because change tracking is disabled, running the sync will sync the data for **InvoiceAccount** and **ContactPersonId** from the Finance and Operations app to Common Data Service.

7. To sync the data for **InvoiceAccount** and **ContactPersonId** from Common Data Service to the Finance and Operations, you use a data integration project.

    1. In Power Apps, create a data integration project between the **Sales.Account** and **Finance and Operations apps.Customers V3** entities. The data direction must be from Common Data Service to the Finance and Operations app.  Because **InvoiceAccount** is a new attribute in dual-write, you may want to skip initial sync for this attribute. For more information, see [Integrate data into Common Data Service](https://docs.microsoft.com/power-platform/admin/data-integrator).

        The following image shows a project that updates **InvoiceAccount** and **ContactPersonId**.

        ![self or circular reference](media/cust_selfref6.png)

    2. Add the company criteria in the filter on Common Data Service side, because only the records that match filter criteria will be updated in the Finance and Operations app. To add a filter, click the filter icon. In the **Edit query** dialog, you can add a filter query like **_msdyn_company_value eq '\<guid\>'**. If the filter icon is not present, create a support ticket to ask the data integration team to enable the filter capability on your tenant. If you do not enter a filter query for **_msdyn_company_value**, then all the records are synced.

        ![self or circular reference](media/cust_selfref7.png)

        This completes the initial sync of the records.

8. Enable change tracking for the **Customers V3** entity in the Finance and Operations app.

