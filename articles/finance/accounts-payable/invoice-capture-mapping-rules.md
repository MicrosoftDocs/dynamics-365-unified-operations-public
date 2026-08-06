---
title: Invoice capture solution mapping rules
description: Learn about the setup of mapping rules in the Invoice capture solution, including an outline on managing mapping rules by using the app.
author: sunfzam
ms.author: zezhangzhao
ms.topic: overview
ms.date: 07/28/2026
ms.reviewer: twheeloc
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2022-09-28
ms.search.form: VendorInvoiceWorkspace, VendInvoiceInfoListPage
ms.dyn365.ops.version: 
ms.assetid: 0ec4dbc0-2eeb-423b-8592-4b5d37e559d3
---

# Invoice capture solution mapping rules

[!include [banner](../includes/banner.md)]

Mapping rules bring basic master data from Microsoft Dynamics 365 Finance or the enterprise resource planning (ERP) system. After you set up mapping rules, you can derive the information required to create vendor invoices in Finance. When you use mapping rules, the accounts payable (AP) clerk checks the status instead of manually filling in all the missing field values.

There are four types of mapping rules:

- Legal entity
- Vendor account
- Item
- Expense type

## Manage mapping rules by using the app

To manage mapping rules by using the app, select **Setup**. The **Mapping rule setup** tab provides four options:

- Legal entity
- Vendor account
- Item mapping
- Expense type

For example, you select the **Legal entity mapping rules** option. The legal entity code is identified by using the company name, address, and tax registration number. For a rule that is named **LE-USPM**, if the company name contains the text "Contoso Robotics USA," the legal entity code is **USPM**.

The page shows all the active mapping rules. If you want to view the inactive mapping rules, select **Active mapping legal entity rules**, and then select **Inactive mapping legal entity rules**.

The following actions are available for mapping rules.

### Create a mapping rule

Use the following methods to create a mapping rule:

- Select **New** to create a new mapping rule. Enter the information for the mapping rule. The **Rule Name** value should be unique for each type of mapping rule.
- Select an existing mapping rule to activate the **Copy** button. Select it, and then select **OK** in the dialog box that appears. You create a mapping rule by duplicating the selected rule.

### Edit a mapping rule

Select a field, and change the value to edit a mapping rule.

### Activate or deactivate mapping rules

To deactivate one or more mapping rules, select them on the **Active mapping rules** page, and then select **Deactivate**. The rules move from the **Active mapping rules** page to the **Inactive mapping rules** page.

To activate mapping rules, select them on the **Inactive mapping rules** page, and then select **Activate**.

### Remove mapping rules

Select the mapping rules, and then select **Delete**.

### Check for conflicts

If two mapping rules have the same **Legal Entity** and **Vendor Account** values, but different **Item Name** values, the system detects a conflict and doesn't create or update the mapping rule.

## Import and export mapping rules from Excel

Use an Excel add-in to manage rules in a batch. The following options are available:

- Download an Excel template.
- Export to Excel.
- Import from Excel.

### Download an Excel template

To download an Excel template, select **Download template**. Then select the fields to include in the template.

### Export to Excel

You can export in two ways:

- Select **Open in Excel Online** to open the file in Excel. You can then edit the file online. When you finish, select **Save**. All your changes are saved on the **Mapping rule** page.
- Select **Download worksheet** to download an Excel file that contains mapping rules. You can then edit the file. When you finish, select **Import from Excel** to upload the updated worksheet.

### Import from Excel

1. Select **Import from Excel** to import data from an XLSX file. You can also import from comma-separated values (CSV) or XML files. Before you import, decide whether to allow duplicates.
1. Select **Review Mapping** to review the attributes mapping and determine whether it's correct. You can modify the mapping relationship.
1. When you finish, select **Finish Import** to start the import.
1. Select **Track Process** to track the progress of the import process.

    The import status updates from **Finish** to **Parsing**, then to **Transforming**, and finally to **Completed**.

When the import process completes, statistics for successes, partial failures, errors, and total processed are shown.
