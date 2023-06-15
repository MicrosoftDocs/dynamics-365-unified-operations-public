---
# required metadata

title: Invoice capture solution mapping rules
description: This article provides information about the setup of mapping rules in the Invoice capture solution.
author: sunfzam
ms.date: 09/25/2022
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: VendorInvoiceWorkspace, VendInvoiceInfoListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: 0ec4dbc0-2eeb-423b-8592-4b5d37e559d3
ms.search.region: Global
# ms.search.industry: 
ms.author: zezhangzhao
ms.search.validFrom: 2022-09-28
ms.dyn365.ops.version: 

---

# Invoice capture solution mapping rules

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

Mapping rules bring basic master data from Microsoft Dynamics 365 Finance or the enterprise resource planning (ERP) system. After mapping rules are set up, the information that is required to create vendor invoices in Finance is derived. When mapping rules are used, the Accounts payable (AP) clerk will check the status instead of manually filling in all the missing field values.

There are four types of mapping rules:

- Legal entity
- Vendor account
- Item
- Expense type

## Manage mapping rules by using the app

To manage mapping rules using the app, select **Setup**. The **Mapping rule setup** tab provides four options:

- Legal entity 
- Vendor account 
- Item mapping 
- Expense type

For example, you select the **Legal entity mapping rules** option. The legal entity code will be identified by using the company name, address, and tax registration number. For a rule that is named **LE-USPM**, if the company name contains the text "Contoso Robotics USA," the legal entity code will be **USPM**.

The page shows all the active mapping rules. If you want to view the inactive mapping rules, select **Active mapping legal entity rules**, and then select **Inactive mapping legal entity rules**.

The following actions are available for mapping rules.

### Create a mapping rule

You can use two methods to create a mapping rule:

- Select **New** to create a new mapping rule. Then enter the information for the mapping rule. The **Rule Name** value should be unique for each type of mapping rule.
- If you select an existing mapping rule, the **Copy** button becomes available. Select it, and then select **OK** in the dialog box that appears. A mapping rule is created by duplicating the selected rule.

### Edit a mapping rule

To edit a mapping rule, select a field, and change the value.

### Activate/deactivate mapping rules

To deactivate one or more mapping rules, select them on the **Active mapping rules** page, and then select **Deactivate**. The rules are moved from the **Active mapping rules** page to the **Inactive mapping rules** page.

Likewise, to activate mapping rules, select them on the **Inactive mapping rules** page, and then select **Activate**.

### Remove mapping rules

To remove mapping rules, select them, and then select **Delete**.

### Check for conflicts

If two mapping rules have the same **Legal Entity** and **Vendor Account** values, but different **Item Name** values, a conflict will be detected, and the mapping rule won't be created or updated.

## Import/export mapping rules from Excel

An Excel add-in can be used to manage rules in a batch. The following options are available:

- Download an Excel template.
- Export to Excel.
- Import from Excel.

### Download an Excel template

To download an Excel template, select **Download template**. Then select the fields to include in the template.

### Export to Excel

You can export in two ways:

- Select **Open in Excel Online** to open the file in Excel. You can then edit the file online. When you've finished, select **Save**. All your changes will be saved on the **Mapping rule** page.
- Select **Download worksheet** to download an Excel file that contains mapping rules. You can then edit the file. When you've finished, select **Import from Excel** to upload the updated worksheet.

### Import from Excel

1. Select **Import from Excel** to import data from an XLSX file. You can also import from comma-separated values (CSV) or XML files. Before you import, you should decide whether duplicates are allowed.
2. Select **Review Mapping** to review the attributes mapping and determine whether it's correct. You can modify the mapping relationship.
3. When you've finished, select **Finish Import** to start the import.
4. You can select **Track Process** to track the progress of the import process.

    The import status is updated from **Finish** to **Parsing**, then to **Transforming**, and finally to **Completed**.

When the import process is completed, statistics for successes, partial failures, errors, and total processed are shown.
