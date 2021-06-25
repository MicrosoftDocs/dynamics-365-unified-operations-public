---
title: Upgrade to the party and global address book model
description: This topic describes how to upgrade dual-write data to the party and global address book model.
author: RamaKrishnamoorthy
ms.date: 03/31/2021
ms.topic: article
audience: Application User, IT Pro
ms.reviewer: rhaertle
ms.search.region: global
ms.author: ramasri
ms.search.validFrom: 2021-03-31
---

# Upgrade to the party and global address book model

[!include [banner](../../includes/banner.md)]

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

The [Microsoft Azure Data Factory template](https://aka.ms/dual-write-gab-adf) helps you upgrade existing **Account**, **Contact**, and **Vendor** table data in dual-write to the party and global address book model. The template reconciles the data from both finance and operations apps and customer engagement applications. At the end of the process, **Party** and **Contact** fields for **Party** records will be created and associated with **Account**, **Contact**, and **Vendor** records in customer engagement applications. A .csv file (`FONewParty.csv`) is generated to create new **Party** records inside the finance and operations app. This topic provides instructions about how to use the Data Factory template and upgrade your data.

If you don’t have any customizations, you can use the template as is. If you have customizations for **Account**, **Contact**, and **Vendor** then you must modify the template using the following instructions.

> [!NOTE]
> The template only upgrades the **Party** data. In a future release, postal and electronic addresses will be included.

## Prerequisites

The following prerequisites are required to upgrade to the party and global address book model:

+ [Azure subscription](https://portal.azure.com/)
+ [Access to the template](https://aka.ms/dual-write-gab-adf)
+ You must be an existing dual-write customer.

## Prepare for the upgrade
The following activities are needed to prepare for the upgrade:

+ **Fully synced**: Both environments are in a fully synced state for **Account (Customer)**, **Contact**, and **Vendor**.
+ **Integration keys**: **Account (Customer)**, **Contact**, and **Vendor** tables in customer engagement apps are using the integration keys that shipped out-of-the-box. If you customized the integration keys, you must customize the template.
+ **Party number**: All **Account (Customer)**, **Contact**, and **Vendor** records that will be upgraded have a **Party** number. Records without a **Party** number will be ignored. If you want to upgrade those records, add a **Party** number to them before you start the upgrade process.
+ **System outage**: During the upgrade process, you will have to take both the finance and operations and customer engagement environments offline.
+ **Snapshot**: Take snapshots of both the finance and operations apps and customer engagement apps. Use the snapshots to restore the previous state if you need to.

## Deployment

1. Download the template from [Dynamics-365-FastTrack-Implementation-Assets](https://aka.ms/dual-write-gab-adf).

2. Sign in to [Microsoft Azure](https://portal.azure.com/).

3. Create a [resource group](/azure/azure-resource-manager/management/manage-resource-groups-portal).

4. Create a [storage account](/azure/storage/common/storage-account-create?tabs=azure-portal) in the resource group that you created.

5. Create a [data factory](/azure/data-factory/quickstart-create-data-factory-portal) in above resource group that you created.

6. Open the data factory and select the **Author & Monitor** tile.

7. On the **Manage** tab, select **ARM template**.

8. Select the **Import ARM template** to import the **Party** template.

9. Import the template into the data factory. Enter the following values for **Project details** and **Instance details**.

    Field | Value
    ---|---
    Subscription | Azure subscription
    Resource group | Provide same resource under which storage account is created.
    Region | Specify region.
    Factory Name | Specify factory name.
    FO Linked Service_service Principal Key | Specify the application's key.
    Azure Blob Storage_connection String | Azure Blob storage connection string.
    Dynamics Crm Linked Service_password | The password for the user account you specified as the username.
    FO Linked Service_properties_type Properties_url  | `https://sampledynamics.sandbox-operationsdynamics.com/data`
    FO Linked Service_properties_type Properties_tenant | Specify the tenant information (domain name or tenant ID) under which your application resides.
    FO Linked Service_properties_type Properties_aad Resource Id | `https://sampledynamics.sandboxoperationsdynamics.com`
    FO Linked Service_properties_type Properties_service Principal Id | Specify the application's client ID.
    Dynamics Crm Linked Service_properties_type Properties_username | The username to connect to Dynamics 365.

    For additional information, refer to the following topics: 
    
    - [Manually promote a Resource Manager template for each environment](/azure/data-factory/continuous-integration-deployment#manually-promote-a-resource-manager-template-for-each-environment)
    - [Linked service properties](/azure/data-factory/connector-dynamics-ax#linked-service-properties)
    - [Copy data using Azure Data Factory](/azure/data-factory/connector-dynamics-crm-office-365#dynamics-365-and-dynamics-crm-online)

10. After deployment, validate the datasets, data flow, and linked service of the data factory.

   ![Datasets, data flow, and linked service](media/data-factory-validate.png)

11. Navigate to **Manage**. Under **Connections**, select **Linked Service**. Select **DynamicsCrmLinkedService**. In the **Edit linked service (Dynamics CRM)** form, enter the following values.

    Field | Value
    ---|---
    Name | DynamicsCrmLinkedService
    Description | Linked services to connect with CRM instance to fetch entities data
    Connect via integration runtime | AutoResolvelntegrationRuntime
    Deployment type | Online
    Service Uri | `https://<organization-name>.crm[x].dynamics.com`
    Authentication type | Office365
    User name |
    Password or Azure Key Vault | Password
    Password |

## Run the template

1. Stop the following **Account**, **Contact**, and **Vendor** dual-write maps using the Finance and Operations app.

    + Customers V3(accounts)
    + Customers V3(contacts)
    + CDS Contacts V2(contacts)
    + CDS Contacts V2(contacts)
    + Vendor V2 (msdyn_vendor)

2. Make sure the maps are removed from the `msdy_dualwriteruntimeconfig` table in Dataverse.

3. Install [Dual-write Party and Global Address Book Solutions](https://aka.ms/dual-write-gab) from AppSource.

4. In the finance and operations app, if the following tables contain data, then run **Initial Sync** for them.

    + Salutations
    + Personal character types
    + Complimentary closing
    + Contact person titles
    + Decision making roles
    + Loyalty levels

5. In the customer engagement app, disable the following plug-in steps.

    + Account Update
         + Microsoft.Dynamics.GABExtended.Plugins.UpdatePartyAttributesFromAccountEntity: Update of account
         + Microsoft.Dynamics.FinanceExtended.Plugins.TriggerNotesForCustomerTypeCodes: Update of account
    + Contact Update
         + Microsoft.Dynamics.GABExtended.Plugins.UpdatePartyAttributesFromContactEntity: Update of contact
         + Microsoft.Dynamics.FinanceExtended.Plugins.TriggerNotesForSellableContact: Update of contact
    + msdyn_party Update
         + Microsoft.Dynamics.GABExtended.Plugins.UpdatePartyAttributesFromPartyEntity: Update of msdyn_party
    + msdyn_vendor Update
         + Microsoft.Dynamics.GABExtended.Plugins.UpdatePartyAttributesFromVendorEntity: Update of msdyn_vendor

6. In the customer engagement app, disable the following workflows:

    + Create Vendors in Accounts Table
    + Create Vendors in Accounts Table
    + Create Vendors of type person in Contacts Table
    + Create Vendors of type Person in Vendors Table
    + Update Vendors in Accounts Table
    + Update Vendors in Vendors Table
    + Update Vendors of type Person in Contacts Table
    + Update Vendors of type Person in Vendors Table

7. In the data factory, run the template by selecting **Trigger now** as shown in the following image. This process might take a few hours to complete based on the data volume.

    ![Trigger run](media/data-factory-trigger.png)

    > [!NOTE]
    > If you have customizations for **Account**, **Contact**, and **Vendor**, then you need to modify the template.

8. Import the new **Party** records in the Finance and Operations app.

    + Download the `FONewParty.csv` file from Azure blob storage. The path is `partybootstrapping/output/FONewParty.csv`.
    + Convert the `FONewParty.csv` file into an Excel file and import the Excel file into the finance and operations app. If the csv import works for you, you can import the csv file directly. The import could take a few hours to run, depending on the data volume. For more information, see [Data import and export jobs overview](../data-import-export-job.md).

    ![Import the Datavers party records](media/data-factory-import-party.png)

9. In the customer engagement apps, enable the following plug-in steps:

    + Account Update
         + Microsoft.Dynamics.GABExtended.Plugins.UpdatePartyAttributesFromAccountEntity: Update of account
         + Microsoft.Dynamics.FinanceExtended.Plugins.TriggerNotesForCustomerTypeCodes: Update of account
    + Contact Update
         + Microsoft.Dynamics.GABExtended.Plugins.UpdatePartyAttributesFromContactEntity: Update of contact
         + Microsoft.Dynamics.FinanceExtended.Plugins.TriggerNotesForSellableContact: Update of contact
    + msdyn_party Update
         + Microsoft.Dynamics.GABExtended.Plugins.UpdatePartyAttributesFromPartyEntity: Update of msdyn_party
    + msdyn_vendor Update
         + Microsoft.Dynamics.GABExtended.Plugins.UpdatePartyAttributesFromVendorEntity: Update of msdyn_vendor

10. In the customer engagement apps, activate the following workflows if you deactivated them in previous steps:

    + Create Vendors in Accounts Table
    + Create Vendors in Accounts Table
    + Create Vendors of type person in Contacts Table
    + Create Vendors of type Person in Vendors Table
    + Update Vendors in Accounts Table
    + Update Vendors in Vendors Table
    + Update Vendors of type Person in Contacts Table
    + Update Vendors of type Person in Vendors Table

11. Run the **Party**-related maps as instructed in [Party and global address book](party-gab.md).

## Troubleshooting

1. If the process fails, rerun the data factory starting from the failed activity.
2. Some files are generated by the data factory that you can use for data validation purpose.
3. The data factory runs based on csv files that are comma-delimited. If there is a field value that has a comma, it may interfere with the results. You need to remove the commas.
4. The **Monitoring** tab provides information about all steps and data processed. Select a specific step to debug it.

    ![Monitoring tab](media/data-factory-monitor.png)

## Learn more about the template

You can find additional information about the template in [Comments for Azure Data Factory template readme](https://github.com/microsoft/Dynamics-365-FastTrack-Implementation-Assets/blob/master/Dual-write/Upgrade%20data%20to%20dual-write%20Party-GAB%20schema/readme.md).
