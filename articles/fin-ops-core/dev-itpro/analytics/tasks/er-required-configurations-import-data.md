---
title: ER Create required configurations to import data from an external file
description: This article describes how to design Electronic reporting configurations to import data in to the Microsoft Dynamics 365 Finance app from an external file.
author: kfend
ms.date: 04/09/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: DefaultDashboard, ERWorkspace, ERSolutionTable, ERDataModelDesigner, ERSolutionCreateDropDialog, EROperationDesigner, ERModelMappingTable, ERModelMappingDesigner, ERExpressionDesignerFormula, Tax1099Summary, VendSettlementTax1099
---

# ER Create required configurations to import data from an external file

[!include [banner](../../includes/banner.md)]

The following steps explain how a user in the System administrator or Electronic reporting developer role can design Electronic reporting (ER) configurations to import data into the application from an external file. In this example, you create the required ER configurations for the sample company, Litware, Inc. To complete these steps, you must first complete the steps in the task guide, "ER Create a configuration provider and mark it as active." You can complete these steps by using the USMF data set. You must also download and save the following files locally:

| Content description                       | File name                                     |
|-------------------------------------------|-----------------------------------------------|
| ER data model configuration - 1099 | [1099model.xml](https://download.microsoft.com/download/b/d/9/bd9e8373-d558-4ab8-aa9b-31981adc97ea/1099model.xml)                  |
| ER format configuration - 1099    | [1099format.xml](https://download.microsoft.com/download/e/8/7/e87154b0-b53f-431f-8e1e-0b7f7c9805a9/1099format.xml)                  |
| Sample of the incoming document in XML format                          | [1099entries.xml](https://download.microsoft.com/download/4/0/3/403a4958-df24-476a-b8b0-6843a9fa7f89/1099entries.xml)        |
| Sample of the workbook to manage data of incoming document                          | [1099entries.xlsx](https://download.microsoft.com/download/6/0/0/6001abab-a331-48db-a939-41851fb0f5d0/1099entries.xlsx) |

ER offers business users the ability to configure the process of importing external data files to tables in either .XML or .TXT format. First, you must design an abstract data model and an ER data model configuration to represent the data that you're importing. Next, you need to define the structure of the file that you're importing and the method that you use to port the data from the file to the abstract data model. You must create the ER format configuration that maps to the designed data model for that abstract data model. Then, you must extend the data model configuration with a mapping that describes how the imported data is persisted as abstract data model data and how it is used to update tables. You must append the ER data model configuration with a new model mapping that describes the binding of the data model to the application's destinations.  

The following scenario shows the ER data import capabilities. This scenario includes vendor transactions that are tracked externally and then imported to be reported later in Vendor's settlement for 1099's.

## Add a new ER model configuration

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.

    Verify that the configuration provider for sample company **Litware, Inc.** is available and marked as active. If you don't see this configuration provider, first complete the steps in the procedure, "Create a configuration provider and mark it as active."

1. Select **Reporting configurations**.

    Instead of creating a new model to support data import, load the file, `1099model.xml`, that you previously downloaded. This file contains the custom data model of vendors' transactions. You map this data model to the data components that are in the AOT data entity.

1. Select **Exchange**.
1. Select **Load from XML file**.

    Select **Browse** and go to the `1099model.xml` file that you previously downloaded.  

1. Select **OK**.
1. In the tree, select **1099 Payments model**.

## Review data model settings

1. Select **Designer**.

    This model represents vendors' transactions from the business standpoint. It's separate from the implementation.

1. In the tree, expand **1099-MISC**.
1. In the tree, select **1099-MISC\Transactions**.
1. In the tree, expand **1099-MISC\Transactions**.

    The **Transactions** element of this model represents individual transactions. Use the child elements to specify required details, such as vendor account and transaction date, for each transaction.

1. Close the page.

## Add a new ER format configuration that supports data import

The steps in this subtask show you how to create a new format configuration to manage data import from external files.

1. Select **Create configuration** to open the drop dialog.
1. In the **New** field, enter *Format based on data model 1099 Payments model*.
1. Select **Yes** in the **Supports data import** field.
1. Press **ESC** key to close this page.

    Instead of creating a new format to support data import, load the 1099format.xml file that you previously downloaded. This file contains the defined structure of the file you are importing and the mapping of the structure to the custom data model of vendors' transactions.
1. Select **Exchange**.
1. Select **Load from XML file**.
    Select **Browse** and go to the 1099format.xml file that you previously downloaded.  
1. Select **OK**.
1. In the tree, expand *1099 Payments model*.
1. In the tree, select *1099 Payments model\Format for importing vendors' transactions*.

## Review format settings

1. Select **Designer**.
1. Toggle **Show details** on.
1. Select **Expand/collapse**.
1. Select **Expand/collapse**.

    The designed format represents the expected structure of the external file. This file must be in XML format and have the settlement root element. Each vendor's transaction is represented by the transaction element that is defined as having zero-to-many multiplicity. This definition means that the incoming file can contain zero to multiple transactions. Nested elements of the *transaction* element represent a single transaction's attributes. All attributes, except country/region, are mandatory, so the importing file must include them.

## Review the settings of the format mapping to the data model

1. Select **Map format to model**.

    The mapping **For importing vendors' transactions** contains the data transfer rules from the incoming XML file to the selected part of the custom data model, which you define by selecting the 1099-MISC definition.  

1. Select **Designer**.
1. Toggle **Show details** on.
1. In the tree, expand **format: Record**.
1. In the tree, select **format: Record**.

    You see the designed format as a data source component.  

1. In the tree, expand `format: Record*settlement: XML Element 1..1 (settlement): Record`.
1. In the tree, expand `format: Record*settlement: XML Element 1..1 (settlement): Record\transaction: XML Element 0..* (transaction): Record list`.
1. In the tree, expand `format: Record*settlement: XML Element 1..1 (settlement): Record\transaction: XML Element 0..* (transaction): Record list*vendor: XML Element 1..1 (vendor): Record`.
1. In the tree, expand `format: Record*settlement: XML Element 1..1 (settlement): Record\transaction: XML Element 0..1 (country): Record`.
1. In the tree, select `format: Record*settlement: XML Element 1..1 (settlement): Record\transaction: XML Element 0..* (transaction): Record list*vendor: XML Element 1..1 (vendor): Record`.

    The predefined **format** data source component presents mandatory and optional format elements differently.  
1. In the tree, expand **Transactions: Record list= format.settlement.'$enumerated'**.

    The elements of the format that defines the structure of the imported file are bound to the elements of the custom data model. Based on these bindings, the content of the imported XML file is stored at run-time in the existing data model. Pay attention to the binding of the country element. For any transaction element in the incoming file that has no such element, the default country code **USA** is populated in the data model.  

1. Select the **Validations** tab.

    This format mapping can contain user-defined logic to validate the accuracy of the imported data from a business standpoint. For example, based on the setting, for any transaction in the importing file without a defined country code, a warning message is generated in the Infolog that informs the user about the case and indicates the transaction's sequence number.  

1. Close the page.

## Run the format mapping to the data model

Run this format mapping for testing purposes. Use the `1099entries.xml` file that you previously downloaded. You can export this file from the `1099entries.xlsx` workbook that you use to manage vendor transactions. The generated output imports from the selected XML file and populates the custom data model at real import.  

1. Select **Run**.

    Select **Browse** and go to the `1099entries.xml` file that you previously downloaded.  

1. Select **OK**.

    Note the warning message about a missing country code for a transaction in the imported file.  

    Review the output in XML format, which represents the data that you imported from the selected file and ported to the data model.

1. Close the page.
1. Close the page.

## Review the settings for the model mapping to the destinations

1. In the tree, select **1099 Payments model**.
1. Select **Designer**.
1. Select **Map model to datasource**.

    The mapping **For 1099 manual transactions import** is defined with the **To destination** direction type. This mapping supports data import and contains the setting of rules that define how the imported external file and persisted abstract data model data are used to update tables in the application.  

1. Select **Designer**.
1. In the tree, expand **model: Data model 1099 Payments model**.
1. In the tree, expand **model: Data model 1099 Payments model\Transactions: Record list**.

    The designed model appears as a data source element. At runtime, it contains the data that you import from the external file. Add several tables as data source elements to ensure that the imported data is compliant with the data of the current application, including whether the importing transaction vendor account is available in the system, whether the combination of the importing country/region and state codes exists, and other checks.  

1. In the tree, select `model: Data model 1099 Payments model\Transactions: Record list\$failed: Calculated field = IF(OR(ISEMPTY(model.Transactions.'$refs'.vendor), ISEMPTY(model.Transactions.'$refs'.vendor1099), ISEMPTY(model.Transactions.'$refs'.box1099), ISEMPTY(model.Transactions.'$refs'.country), ISEMPTY(model.Transactions.'$refs'.state), ISEMPTY(model.Transactions.'$refs'.location)), true, false): Boolean`.
1. Select **Edit**.
1. Select **Edit formula**.

    When at least one validation fails for a single imported transaction, the data source attribute `$failed` marks this transaction as failed.  

1. Close the page.
1. Select **Cancel**.
1. In the tree, select `tax1099trans: Table 'VendSettlementTax1099' records= model.Validated`.
1. Select **Edit destination**.

    Add this ER destination to specify how the imported data updates the application tables. In this case, select the data table `VendSettlementTax1099`. Because the record action `Insert` is selected, the imported transactions are inserted in the table `VendSettlementTax1099`. A single model mapping can contain several destinations. This design means that the imported data can update multiple application's tables at once. You can use tables, views, and data entities as ER destinations.

    If you call the mapping from a point in the application (such as button or menu item) that you specifically designed for this action, mark the ER destination as the integration point. In this example, this point is `ERTableDestination#VendSettlementTax1099`.  

1. Select **Cancel**.
1. Select **Show all**.
1. Select **Show mapped only**.
1. In the tree, expand `tax1099trans: Table 'VendSettlementTax1099' records= model.Validated`.

    The data source element that contains only validated transactions is bound to the created destination. You can filter the imported transactions to skip the ones that are incompatible with the applications' data.  

1. In the tree, select `failed: Table 'VendSettlementTax1099Entity' records= model.Failed`.
1. Select the **Validations** tab.

    This model mapping can contain user-defined logic to validate the correctness of the imported data from the existing application data. For example, based on the present setting, for any transaction in the imported file with a vendor account that isn't in the system, a warning message is generated that informs the user and indicates the incorrect vendor account code.  

    Use the **Post validation action** option for each validation to specify whether the import process must continue or stop, and if the already performed inserts or updates can be kept or rolled back.  

1. Select **Show mapped only**.
1. Select **Show all**.
1. Close the page.

    Execute this model mapping to test the designed format and model mappings. Use the file `1099entries.xml`. The data from the selected file is imported into the system.  

1. Select **Run**.

    The dialog box contains no additional questions about the format mapping that must be used to parse the imported file and then port the data to the data model. This condition exists because there's currently only one format that uses this model, which is marked as designed to support data import.  

    Define the voucher ID to differentiate the imported transactions from other transactions that you might already entered manually or imported.  

1. In the **Enter voucher id** field, type `IMPORT-001`.

    Browse to get the `1099entries.xml` file.  

1. Select **OK**.

    The list of generated warnings provides information about incorrect vendor accounts, an incorrect tax 1099 box code, missing country codes, and other issues. Compare this list of warnings to the content that the execution XML file includes.  

1. Close the page.
1. Close the page.
1. Close the page.
1. Close the page.
1. Go to **Accounts payable** > **Periodic tasks** > **Tax 1099** > **Vendor settlement for 1099s**.

    This form shows the cumulative transactions in the **Tax1099Summary** table that the system created based on imported transactions.  

1. In the **From date** field, set the date to 2000-01-01.
1. Select **Manual 1099 transactions**.

    This form contains the list of transactions that you added manually and those that you just imported.  

1. Open **Voucher** column filter.
1. Enter a filter value of `IMPORT-001` on the **Voucher** field by using the **begins with** filter operator.

## Review the relationship between model and format mappings

1. Close the page.
1. Close the page.
1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
1. Select **Reporting configurations**.
1. In the tree, select **1099 Payments model**.

    Assume that you want to support importing the same data but from a .TXT file format.

1. Select **Create configuration** to open the dialog box.
1. In the **New** field, enter *Format based on data model 1099 Payments model*.
1. In the **Name** field, type *Import data from TXT file*.
1. Select **Yes** in the **Supports data import** field.
1. Select **Create configuration**.
1. Select **Designer**.
1. Select **Map format to model**.
1. Select **New**.
1. In the **Definition** field, enter or select a value.

    Select **1099-MISC** option.  

1. In the **Name** field, type *Import data from TXT file*.
1. In the **Description** field, type *Import data from TXT file*.
1. Select **Save**.
1. Close the page.
1. Close the page.
1. Select **Edit**.

    If you installed the hotfix "KB 4012871 Support of GER model mappings in separated configurations with an ability to specify different kinds of prerequisites for deploying them on different versions of Dynamics 365 Finance" ([KB 4012871](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4012871)), execute the next step **Turn the flag 'Default for model mapping' on** for the entered format configuration. Skip the next step otherwise.  

1. Select **Yes** in the **Default for model-mapping** field.
1. In the tree, select **1099 Payments model**.
1. Select **Designer**.
1. Select **Map model to datasource**.
1. Select **Run**.

    If you installed the hotfix, KB 4012871 Support of GER model mappings in separated configurations with an ability to specify different kinds of prerequisites for deploying them on different versions ([KB 4012871](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4012871)), select the preferred model mapping in the lookup field. If you didn't install the hotfix, skip to the next step as the mapping is already selected by the definition of the default format configuration.  

    If you didn't install the hotfix, KB 4012871, the dialog box contains an additional model-mapping question that is used to parse the file that you're importing. The data is then ported from the dialog box to the data model. Currently, you can choose which format mapping to use depending on the type of file that you plan to import.  

    If you plan to call this model mapping from a point in the application that is specifically designed for the action, the ER destination and the format mapping must be marked as part of the integration.  

1. Select **Cancel**.
1. Close the page.
1. Close the page.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
