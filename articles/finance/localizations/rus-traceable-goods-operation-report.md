---
# required metadata

title: Report about operations with traceable goods (Russia)
description: This article provides information about how set up and generate a report about operations with traceable goods.
author: v-oskinaolga
ms.date: 06/04/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: InventTrans, RAssettrans
audience: Application User
# ms.devlang: 
ms.reviewer: 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: 
ms.search.validFrom: 2022-06-04
ms.dyn365.ops.version: 10.0.27

---

# Report about operations with traceble goods

[!include [banner](../includes/banner.md)]

The traceability system has been operational since July 8. 
Its action begins from the moment of importation of imported goods into the territory of the Russian Federation, and ends with the disposal of such goods: sale to an individual, recycling, transfer to production, export.

# Set up Report about operations with traceble goods
These tasks will guide you through setting Microsoft Dynamics 365 Finance environment to generate the electronic file for the Report about operations with traceble goods for Russian.
- [Import ER configurations](#import-er).
- [Set up application-specific parameters for VAT declaration fields](#set-up).
- [Download and import the data package for electronic messages](#import-em). 

## <a name="import-er"></a>Import ER configurations

Open the Electronic reporting workspace, and import the latest versions of these ER formats under Products turnover model:

-	Traceable goods operations 5.02 XML (RU)
-	Traceable goods operations 5.02 Excel (RU)
-	Traceable goods operations model mapping (RU)

For more information, see [Download ER configurations from the Global repository of Configuration service](../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

## <a name="set-up"></a>Set up application-specific parameters for Report about operations with traceble goods

> [!NOTE]
> We recommend that you enable the **Use application specific parameters from previous versions of ER formats** feature in the **Feature management** workspace. When this feature is enabled, parameters that are configured for an earlier version of an ER format automatically become applicable for a later version of the same format. If this feature isn't enabled, you must explicitly configure application-specific parameters for each format version. This feature is available in the **Feature management** workspace as of Finance version 10.0.23. For more information about how to set up the parameters of an ER format for each legal entity, see [Set up the parameters of an ER format per legal entity](../../fin-ops-core/dev-itpro/analytics/er-app-specific-parameters-set-up.md).

Follow these steps to define which operations are related with Vendor accounts/Vendor posting profile/Vendor groups, Customer accounts/ Customer posting profile/ Customer, Inventory journal names, Fixed asset reason codes for generation Traceable goods operation report.

1.	Go to **Workspaces** \> **Electronic reporting**, and select **Reporting configurations**.
2.	Select the **Traceable goods operations 5.02 XML (RU) configuration**, and then, on the Action Pane, select **Configurations \> Application specific parameters setup**.
3.	On the **Application specific parameters** page, on the **Lookups** FastTab, select **$VendorsLookup**/ **$VendPostingProfilesLookup**/ **$VendGroupsLookup** or **$CustomersLookup**/ **$CustGroupsLookup**/ **$CustPostingProfilesLookup** or **$InventoryJournalNamesLookup** or **$FixedAssetReasonCodeLookup**.
4.	On the **Conditions** FastTab, set the following fields to associate the **Vendor accounts**/ **Vendor posting profile**/ **Vendor groups**, **Customer accounts**/ **Customer posting profile**/ **Customer groups**, **Inventory journal names**, **Fixed asset reason codes** and report operations.

    | Field | Description |
    |---|---|
    | Lookup result | Select the value of operation for every Lookup (Vendor accounts/Vendor posting profile/Vendor groups, Customer accounts/ Customer posting profile/ Customer, Inventory journal names, Fixed asset reason codes) if needed.|
    | Name | Select Vendor accounts/Vendor posting profile/Vendor groups, Customer accounts/ Customer posting profile/ Customer, Inventory journal names, Fixed asset reason codes|
    |---|---|
    
  5. Create additional two lines with ‘00’ operation for *Blank* and *Not blank* name value. This prevents potential errors when generating the report. 
  6. In the **State** field, change the value to **Completed**.
  7. On the Action Pane, select **Export** to export the settings of the application-specific parameters

## <a name="import-em"></a>Download and import the data package for electronic messages
Electronic messaging (EM) functionality is provided to maintain the different processes that are used in electronic reporting for different document types. For more information about electronic messages, see [Electronic messaging](../general-ledger/electronic-messaging.md).

> [!NOTE]
> Some records in the data entities in the package include a link to ER configurations. Before you start to import the data entities package, [import ER configurations into Finance](#import-er).

1. In [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/v2), in the Shared asset library, select **Data package** as the asset type, and then download **Traceable goods operations 5.02**. The downloaded file is named **Traceable goods operations 5.02.zip**.
2. In Finance, in the **Data management** workspace, select **Import**.
3. On the **Import** FastTab, in the **Group name** field, enter a name for the job.
4. On the **Selected entities** FastTab, select **Add file**.
5. In the **Add file** dialog box, verify that the **Source data format** field is set to **Package**, select **Upload and add**, and then select the zip file that you downloaded earlier.
6. Select **Close**.
7. After the data entities are uploaded, on the Action Pane, select **Import**.
8. Go to **Tax** \> **Inquiries and reports** \> **Electronic messages** \> **Electronic messages**, and validate the electronic message processing that you imported (**Traceable goods operations 5.02**).

For more information about how you can use the data management framework, see [Data management](../../fin-ops-core/dev-itpro/data-entities/data-entities-data-packages.md).

    





