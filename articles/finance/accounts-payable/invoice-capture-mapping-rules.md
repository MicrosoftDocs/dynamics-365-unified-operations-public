---
# required metadata

title: Invoice capture solution mapping rules overview
description: This article provides information about setting up mapping rules in the Invoice capture solution. 
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
ms.custom: ["13971", "intro-internal"]
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

Mapping rules bring basic master data from ERP system. Once mapping rules are set up, the information needed for vendor invoice creation in Dynamics 365 Finance is 
imported. With mapping rules, the AP clerk only needs to check the status, instead of filling out all the missing fields manually. 
There are three types of mapping rules: 
 - legal entity 
 - vendor account
 - item   

## Manage mapping rules via App 

To manage mapping rules using the app, select **Setup**. On the **Mapping rule setup** tab, there are three options: 
 - **Legal entity mapping rules** 
 - **Vendor account mapping rules** 
 - **Item mapping rules** 

### Legal entity mapping rule example

Let's use the **Legal entity mapping rules** as an example to see how the mapping rules work. The legal entity code will be identified using the company name, address and tax registration number. For a rule with rule name “LE-USPM”, if company name contains “Contoso Robotics USA”, the legal entity code would be USPM. 

The page displays all the active mapping rules. If you want to see all the inactive mapping rules, click **Active Mapping Legal Entity Rules** and select **Inactive 
Mapping Legal Entity Rules**. 


The following are available for mapping rules: 

### Create a mapping rule 

You can use two methods to create a mapping rule: **New** or **Duplicate**. 

### New 

Click **New** to create a new mapping rule. Enter the information of mapping rule, **Rule Name** should be unique for each type of mapping rules. 

### Duplicate 

After you select a mapping rule, **Duplicate** will display. Click **OK** when the dialog pops up and a duplicate mapping rule is created. 

### Edit a mapping rule 

To edit a mapping rule, click the field and modify it. The updated value will be saved when the field loses focus.  

### Activate / Deactivate mapping rules 

Choose one or several mapping rules on **Active Mapping Rules** page, click **Deactivate** to inactivate these rules. These rules will be moved from the **Active 
Mapping Rules** page to the **Inactive Mapping Rules** page. Similarly, click **Activate** on the **Inactive Mapping Rules** page to activate the selected rules. 

### Remove mapping rules 

Select several mapping rules and click **Delete** to remove the mapping rules. 

### Check conflict 

If two mapping rules have same values in the **Legal Entity**, **Vendor Account**, **Item Name** fields but a different value in the **Item Number** fields, 
a conflict will be detected and the mapping rule isn't created or updated due to duplication. 

## Import/Export mapping rules from Excel 

An Excel add-in can be used to manage rules in batch. Excel options include: 
**Excel Templates**
**Export to Excel** 
**Import from Excel** 

### Excel Templates 

Click **Download template** to download excel templates and select the fields to be included in the template. 
By default, the template includes the following fields:
 - **Description**
 - **Item number would be**
 - **Legal entity**
 - **Rule name**
 - **Status**
 - **Vendor account**


### Export to Excel 

You can export in two ways: **Open in Excel Online** or **Download worksheet**. 

#### Open in Excel Online 

Click **Open in Excel Online** to open excel and you can edit the file online. After the editing is completed, click **Save**, and the modification will be reflected 
on the mapping rule page. 

#### Download worksheet 

If you choose download a worksheet, an excel file containing mapping rules will be downloaded. After editing is done, click **Import from Excel** to upload the updated
spreadsheet. 

### Import from Excel 

Click **Import from Excel** to import data from an .xlsx file. You can also import from CSV or XML files. Before you import, you'll want to decide if duplicates are 
allowed or not.  

Click **Review Mapping** to review if the attributes mapping is correct. You can modify the mapping relationship. Click **Finish Import** to start importing. 

After the import process starts, click **Track Process** to track process of the import process.
The import status changes from **Finish** to **Parsing**, then to **Transforming** and finally **Completed**. 
Once the importing process completes, it will display the statistics of successes, partial failures, errors and total processed. 



