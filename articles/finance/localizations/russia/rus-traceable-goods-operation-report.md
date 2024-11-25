---
title: Generate a Traceable goods operation report (Russia)
description: Learn how set up and generate a report about operations that involve traceable goods, including an outline on generating Traceable goods operation reports.
author: evgenypopov
ms.author: evgenypopov
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/11/2024
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2022-06-04
ms.search.form: InventTrans, RAssettrans
ms.dyn365.ops.version: 10.0.27
---

# Generate a Traceable goods operation report (Russia)

[!include [banner](../../includes/banner.md)]

Goods traceability is a system for recording and storing information about goods that are imported from other countries or regions. The goal is to control imported goods from the importer to the buyer, and to reduce the share of illegally imported goods.

The action of this system begins the moment that imported goods enter the territory of the Russian Federation. It ends when those goods are disposed of through sale to an individual, recycling, transfer to production, or export.

This topic guides you through the process of setting up your Microsoft Dynamics 365 Finance environment to generate the electronic file for the report for Russia about operations that involve traceable goods (the **Traceable goods operation** report).

## Set up and generate a Traceable goods operation report

To set up and generate a **Traceable goods operation** report for Russia, complete the following tasks:

1. [Import Electronic reporting (ER) configurations](#import-er).
2. [Set up application-specific parameters for the Traceable goods operation report](#set-up).
3. [Download and import the data package for electronic messages](#import-em). 
4. [Set up a category hierarchy, financial reasons, and fixed assets for traceable goods](#cat-hier-fin-reason-fa).
5. [Generate a Traceable goods operation report in electronic format](#gen-report)

### <a name="import-er"></a>Import ER configurations

- Go to **Workspaces** \> **Electronic reporting**, and import the latest versions of the following ER formats under **Products turnover model**:

    - Traceable goods operations 5.02 XML (RU)
    - Traceable goods operations 5.02 Excel (RU)
    - Traceable goods operations model mapping (RU)

For more information, see [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

### <a name="set-up"></a>Set up application-specific parameters for the Traceable goods operation report

> [!NOTE]
> We recommend that you enable the **Use application specific parameters from previous versions of ER formats** feature in the **Feature management** workspace. When this feature is enabled, parameters that are configured for an earlier version of an ER format automatically become applicable for a later version of the same format. If this feature isn't enabled, you must explicitly configure application-specific parameters for each format version. This feature is available in the **Feature management** workspace as of Finance version 10.0.23. For more information about how to set up the parameters of an ER format for each legal entity, see [Set up the parameters of an ER format per legal entity](../../../fin-ops-core/dev-itpro/analytics/er-app-specific-parameters-set-up.md).

Follow these steps to define which operations are related to vendor accounts/vendor posting profiles/vendor groups, customer accounts/customer posting profiles/customers, inventory journal names, and fixed asset reason codes so that you can generate the **Traceable goods operation** report.

1. In the **Electronic reporting** workspace, select **Reporting configurations**.
2. Select the **Traceable goods operations 5.02 XML (RU)** configuration, and then, on the Action Pane, select **Configuration** \> **Application specific parameters setup**.
3. On the **Application specific parameters** page, on the **Lookups** FastTab, select **$VendorsLookup**/**$VendPostingProfilesLookup**/**$VendGroupsLookup**, **$CustomersLookup**/**$CustGroupsLookup**/**$CustPostingProfilesLookup**, **$InventoryJournalNamesLookup**, or **$FixedAssetReasonCodeLookup**.
4. On the **Conditions** FastTab, set the following fields to associate the **Vendor accounts**/**Vendor posting profile**/**Vendor groups**, **Customer accounts**/**Customer posting profile**/**Customer groups**, **Inventory journal names**, or **Fixed asset reason codes** lookup and report operations.

    | Field | Description |
    |---|---|
    | Lookup result | Select the operation value for each lookup (**Vendor accounts**/**Vendor posting profile**/**Vendor groups**, **Customer accounts**/**Customer posting profile**/**Customer**, **Inventory journal names**, or **Fixed asset reason codes**) as required. |
    | Name | Select **Vendor accounts**/**Vendor posting profile**/**Vendor groups**, **Customer accounts**/**Customer posting profile**/**Customer**, **Inventory journal names**, or **Fixed asset reason codes**. |

5. Create two new lines where the operation is **00**. On one line, enter **Blank** in the **Name** field. On the other line, enter **Not blank** in the **Name** field. These lines help prevent errors when the report is generated.
6. In the **State** field, select **Completed**.
7. On the Action Pane, select **Export** to export the settings of the application-specific parameters.

### <a name="import-em"></a>Download and import the data package for electronic messages

Electronic messaging (EM) functionality is provided to maintain the different processes that are used in electronic reporting for different document types. For more information about electronic messages, see [Electronic messaging](../../general-ledger/electronic-messaging.md).

> [!NOTE]
> Some of the data entity records in the package include a link to ER configurations. Before you start to import the data entities package, [import ER configurations into Finance](#import-er).

1. In [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/v2), in the Shared asset library, select **Data package** as the asset type, and then download **Traceable goods operations 5.02**. The downloaded file is named **Traceable goods operations 5.02.zip**.
2. In Finance, in the **Data management** workspace, select **Import**.
3. On the **Import** FastTab, in the **Group name** field, enter a name for the job.
4. On the **Selected entities** FastTab, select **Add file**.
5. In the **Add file** dialog box, verify that the **Source data format** field is set to **Package**, select **Upload and add**, and then select the zip file that you downloaded earlier.
6. Select **Close**.
7. After the data entities are uploaded, on the Action Pane, select **Import**.
8. Go to **Tax** \> **Inquiries and reports** \> **Electronic messages** \> **Electronic messages**, and validate the electronic message processing that you imported.

For more information about how to use the Data management framework, see [Data management](../../../fin-ops-core/dev-itpro/data-entities/data-entities-data-packages.md).

## <a name="cat-hier-fin-reason-fa"></a>Set up a category hierarchy, financial reasons, and fixed assets for traceable goods

- If a category hierarchy isn't already set up, create one, and relate it to the **Traceability hierarchy category** hierarchy type. For more information, see [Create a hierarchy of product classification](../../../supply-chain/pim/tasks/create-hierarchy-product-classification.md). Then use this category hierarchy to classify traceable products (traceable goods). For more information, see [Classify a product using category hierarchies](../../../supply-chain/pim/tasks/classify-product-category-hierarchies.md).
- Set up financial reasons for fixed asset write-off transactions. Then use these reasons on the fixed asset journal lines and also in free text invoices when you sell a fixed asset.
- For traceable fixed assets, the **Traceable number** field should be set on the **Purchase** or **Sale** FastTab. This field is automatically set if the GTD dimension is set when a fixed asset is purchased by using a purchase order. The item on the purchase order line is associated with a category hierarchy that has the **Traceability hierarchy category** hierarchy type. You can manually set the **Traceable number** field.

## <a name="gen-report"></a>Generate a Traceable goods operation report in electronic format

Most operation codes on the **Traceable goods operation** report are entered based on the setting of application-specific parameters. Operations codes **09** and **10** are entered based on inventory transactions where the **Reference** field is set to **Counting**. Operation codes **01** and **12** are entered based on inventory transactions where the **Reference** field is set to **Production line**.

> [!NOTE]
> You should sell a fixed asset only by using a free text invoice. Use different inventory journal names for the receipt and write-off of items.

Follow these steps to generate a **Traceable goods operation report** file.

1. Go to **Tax** \> **Inquiries and reports** \> **Electronic messages** \> **Electronic messages**.
2. In the left pane, select the **ОтчетОперПрТов 5.02 report** format.
3. On the **Messages** FastTab, select **New**.
4. Select the message line that is created, enter a description, and then specify the start date and end date for the report. The end date is treated as the base date for financial reports.
5. On the **Messages** FastTab, select **Update status**.
6. In the **Run processing** dialog box, select **OK**.
7. Validate that the message status is changed to **Ready to generate**.
8. On the **Messages** FastTab, select **Generate report**.
9. In the **Electronic reporting parameters** dialog box, enter the following information.

    | Field | Description |
    |---|---|
    | Signatory type | Specify who signs the profit tax declaration. Select either **Taxpayer** or **Representative**. |
    | First name, Middle name, Last name | Enter the full name of the signatory. |
    | Representative document | If you selected **Representative** as the signatory type, enter the document that confirms the representative's authority. |
    | Correction number | Enter the number of the correction. |
    | Date from, Date to | Enter the reporting date, if you didn't specify it in step 4. |

    > [!NOTE]
    > If you select **Preview Traceable Goods operations 5.02** in the **Action** field, the system generates an Excel file, but the status isn't updated.
    >
    > When the report is generated, the status of the message is changed to **Generated**. If an error occurs while the report is being generated, the status of the message is changed to **Technical error**.

10. Select **OK**.
11. On the **Action log** FastTab, review all the user actions for the current message.
12.	To review the report that is generated, select **Attachments** in the upper-right corner of the page, and then select **Open** to open the file.

[!INCLUDEfooter-include]
