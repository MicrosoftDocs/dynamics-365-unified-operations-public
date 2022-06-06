---
# required metadata

title: Generate a traceable goods operation report (Russia)
description: This article provides information about how set up and generate a report about operations with traceable goods.
author: v-oskinaolga
ms.date: 06/06/2022
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

# Report about operations with traceable goods

[!include [banner](../includes/banner.md)]

Goods traceability is a system for recording and storing information about goods imported from other countries. The goal is to control imported goods from the importer to the buyer and reduce the share of illegally imported goods. 
The action of this system begins the moment imported goods enter into the territory of the Russian Federation, and ends with the disposal of such goods either by sale to an individual, recycling, transfer to production, or export.

## Set up and generate Report about operations with traceable goods
These tasks guide you through setting up your Microsoft Dynamics 365 Finance environment to generate the electronic file for the Report about operations with traceable goods for Russia.

- [Import ER configurations](#import-er).
- [Set up application-specific parameters for VAT declaration fields](#set-up).
- [Download and import the data package for electronic messages](#import-em). 
- [Set up category hierarchy, financinal reasons, and fixed asset for traceable goods](#cat-hier-fin-reason-fa)
- [Generate a Traceable goods operation report in electronic format](#gen-report)

### <a name="import-er"></a>Import ER configurations

Open the Electronic reporting workspace, and import the latest versions of these ER formats under Products turnover model:

- Traceable goods operations 5.02 XML (RU)
- Traceable goods operations 5.02 Excel (RU)
- Traceable goods operations model mapping (RU)

For more information, see [Download ER configurations from the Global repository of Configuration service](../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

### <a name="set-up"></a>Set up application-specific parameters for Report about operations with traceable goods

> [!NOTE]
> We recommend that you enable the **Use application specific parameters from previous versions of ER formats** feature in the **Feature management** workspace. When this feature is enabled, parameters that are configured for an earlier version of an ER format automatically become applicable for a later version of the same format. If this feature isn't enabled, you must explicitly configure application-specific parameters for each format version. This feature is available in the **Feature management** workspace as of Finance version 10.0.23. For more information about how to set up the parameters of an ER format for each legal entity, see [Set up the parameters of an ER format per legal entity](../../fin-ops-core/dev-itpro/analytics/er-app-specific-parameters-set-up.md).

Complete the following steps to define which operations are related with vendor accounts/vendor posting profiles/vendor groups, customer accounts/customer posting profiles/customers, inventory journal names, and fixed asset reason codes to generate the **Traceable goods operation** report.

1. Go to **Workspaces** > **Electronic reporting**, and select **Reporting configurations**.
2. Select the **Traceable goods operations 5.02 XML (RU)** configuration, and then, on the Action Pane, select **Configuration** > **Application specific parameters setup**.
3. On the **Application specific parameters** page, on the **Lookups** FastTab, select **$VendorsLookup**/ **$VendPostingProfilesLookup**/ **$VendGroupsLookup** or **$CustomersLookup**/ **$CustGroupsLookup**/ **$CustPostingProfilesLookup** or **$InventoryJournalNamesLookup** or **$FixedAssetReasonCodeLookup**.
4. On the **Conditions** FastTab, set the following fields to associate the **Vendor accounts**/ **Vendor posting profile**/ **Vendor groups**, **Customer accounts**/ **Customer posting profile**/ **Customer groups**, **Inventory journal names**, **Fixed asset reason codes** and report operations.

    | Field | Description |
    |---|---|
    | Lookup result | Select the operation value for each Lookup (Vendor accounts/Vendor posting profile/Vendor groups, Customer accounts/Customer posting profile/ Customer, Inventory journal names, Fixed asset reason codes) if needed.|
    | Name | Select Vendor accounts/Vendor posting profile/Vendor groups, Customer accounts/Customer posting profile/Customer, Inventory journal names, or Fixed asset reason codes. |

    
  5. Create two new lines with **00** as the operation and in the **Name** field, enter **Blank** on one line and **Not blank** on the other. These lines prevent potential errors when generating the report. 
  6. In the **State** field, change the value to **Completed**.
  7. On the Action Pane, select **Export** to export the settings of the application-specific parameters.

### <a name="import-em"></a>Download and import the data package for electronic messages
Electronic messaging (EM) functionality is provided to maintain the different processes that are used in electronic reporting for different document types. For more information about electronic messages, see [Electronic messaging](../general-ledger/electronic-messaging.md).

> [!NOTE]
> Some of the data entity records in the package include a link to ER configurations. Before you start to import the data entities package, [import ER configurations into Finance](#import-er).

1. In [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/v2), in the Shared asset library, select **Data package** as the asset type, and then download, **Traceable goods operations 5.02**. The downloaded file is named **Traceable goods operations 5.02.zip**.
2. In Finance, in the **Data management** workspace, select **Import**.
3. On the **Import** FastTab, in the **Group name** field, enter a name for the job.
4. On the **Selected entities** FastTab, select **Add file**.
5. In the **Add file** dialog box, verify that the **Source data format** field is set to **Package**, select **Upload and add**, and then select the zip file that you downloaded earlier.
6. Select **Close**.
7. After the data entities are uploaded, on the Action Pane, select **Import**.
8. Go to **Tax** > **Inquiries and reports** > **Electronic messages** > **Electronic messages**, and validate the electronic message processing that you imported.

For more information about how to use the data management framework, see [Data management](../../fin-ops-core/dev-itpro/data-entities/data-entities-data-packages.md).

## <a name="cat-hier-fin-reason-fa"></a>Set up category hierarchy, financinal reasons, and fixed asset for traceable goods

- If not already set up, run a category hierarchy setup. Create a new category hierarchy and relate this category with the **Traceability hierarchy category** hierarchy type. For more information, see [Create a hierarchy of product classification](../../supply-chain/pim/tasks/create-hierarchy-product-classification.md).   Next, classify traceable products with this category. For more information, see [Classify a product using category hierarchies](../../supply-chain/pim/tasks/classify-product-category-hierarchies.md). 

- Set up financial reasons for fixed asset write-off transactions and then use these reasons in the fixed asset journal lines and also in free text invoices when selling a fixed asset.

- For traceable fixed assets, the **Traceable number** field on the **Purchase** or **Sale** FastTab should be filled out. This field is populated automatically if the GTD dimension is set when purchasing a fixed asset by using the purchase order. The item in the purchase order line is associated with a category hierarchy that has the **Traceability hierarchy category** hierarchy type. You can manually set a value in the **Traceable number** field.  

## <a name="gen-report"></a>Generate a Traceable goods operation report in electronic format

Most operation codes are filled out in the report based on setting application-specific parameters. Operations codes '09' and '10' are filled out based on inventory transactions with **Counting** value in the **Reference** field and operation codes '01' and '12'  are filled out based on inventory transactions with **Production line** value in the **Reference** field.

> [!NOTE]
> You should only sell a fixed asset by using a free text invoice. Use different Invent journal names for the receipt and write off of items.

1. To generate the **Traceable goods operation report** file, go to **Tax** > **Inquiries and reports** > **Electronic messages** > **Electronic messages**.
2. In the left pane, select the **ОтчетОперПрТов 5.02 report** format to generate.
3. On the **Messages** FastTab, select **New**.
4. Select the message line that is created, enter a description, and then specify the start date and end date for the report. The end date is treated as the base date for financial reports.
5. On the **Messages** FastTab, select **Update status** and in the **Run processing** dialog box, select **OK**.
6. Validate that the message status is changed to **Ready to generate**.
7. On the **Messages** FastTab, select **Generate report**.
8. In the **Electronic reporting parameters** dialog box, enter the following information and then select **OK**.

    | Field | Description |
    |---|---|
    |Signatory type | Specify who signs the profit tax declaration. Select either **Taxpayer** or **Representative**|
    |First name, Middle name, Last name | Enter the full name of the signatory |
    |Representative document | If you selected Representative as the signatory type, enter the document that confirms the representative's authority.|
    |Correction number|Enter the number of the correction|
    |Date from, Date to|Enter the reporting date, if you didn't specify it in step 6|


    > [!NOTE] 
    > If you select **Preview Traceable Goods operations 5.02** in the **Action** field, the system generates a MIcrosoft Excel file but the status isn't updated.
    >
    > When the report is generated, the status of the message changes to **Generated**. If an error occurs while the report is generated, the status of the message changes to **Technical error**.

9. On the **Action log** FastTab, review all the user actions for the current message.
10.	To review the report that is generated, select **Attachments** in the upper-right corner of the page, and then select **Open** to open the file.

[!INCLUDEfooter-include]



    





