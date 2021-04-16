---
# required metadata

title: Financial reporting FAQ 
description: This topic provides answers to frequently asked questions about financial reporting. 
author: jiwo
ms.date: 01/13/2021
ms.topic: index-page
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global 
# ms.search.industry: 
ms.author: jiwo
ms.search.validFrom: 2021-01-13
ms.dyn365.ops.version: 10.0.14

---

# Financial reporting FAQ 

This topic provides answers to frequently asked questions about financial reporting. 

## How do I restrict access to a report using Tree security?

The following examples shows how to restrict access to a report using Tree security.

The USMF demo company has a Balance sheet report that not all Financial reporting users should have access to. To restrict acces, you can use Tree security to restrict access to a single report so that only certain users can access the report. Follow these steps to do this: 

1.	Sign in to Financial Reporter Report Designer.

2.	Ceate a new tree definition. Go to **File > New > Tree Definition**.
3.	Double-click the **Summary** line in the **Unit Security** column.
4.	Select **Users and Groups**.  
5.	Select the users or groups that need access to this report. 
          
[![user screen](./media/FR-FAQ_users.png)](./media/FR-FAQ_users.png)

[![security screen](./media/FR-FAQ_security.jpg)](./media/FR-FAQ_security.jpg)

6. Select **Save**.
  
[![save button](./media/FR-FAQ_save.png)](./media/FR-FAQ_save.png)

7.	In the report definition, add your new tree definition.

[![tree definition form](./media/FR-FAQ_tree-definition.jpg)](./media/FR-FAQ_tree-definition.jpg)

A.	In the tree definition, select **Setting**. Under **Reporting unit selection**, select **Include all units**.

[![reporting unit selection form](./media/FR-FAQ_reporting-unit-selection.jpg)](./media/FR-FAQ_reporting-unit-selection.jpg)

**Before:**
          [![before screenshot](./media/FR-FAQ_before.png)](./media/FR-FAQ_before.png)

**After:**
          [![after screenshot](./media/FR-FAQ_after.png)](./media/FR-FAQ_after.png)

> [!NOTE]
> Reason for the above message is my user does not have access to that report after applying Unit Security

## How do I determine which accounts do not match my balances?

When you have a report that doesn't match the balances, here are some steps you can take to identify each of the accounts and variances. 

**Financial Reporter Report Designer**
1. In Financial Reporter Report Designer, create a new row definition. 
2. Select **Edit > Insert Rows from Dimensions**.
3. Select **MainAccount**.
        [![Select Main screen_](./media/FR-FAQ_selectmain_.png)](./media/FR-FAQ_selectmain_.png)
    
4. Select **OK**.
5. Save the row definition.
6. Create a new column definition
        [![Create a new column definition](./media/FR-FAQ_column.png)](./media/FR-FAQ_column.png)

7.	Create a new report definition.
8.	Select **Settings** and unmark this option.  
      [![Settings form](./media/FR-FAQ_settings.png)](./media/FR-FAQ_settings.png)
   
9.	Generate the report. 
10.	Export the report to Microsoft Excel.

**Dynamics 365 Finance** 
1. In Dynamics 365 Finance, go to **General Ledger > Inquiries and Reports > Trial Balance**.
2. Set the following parameters:
  - From Date: Start of Fiscal Year
  - To Date: Date you generated the report for
  - Financial Dimension Set “Main Account set”
       [![Main Account Form](./media/FR-FAQ_mainacct.png)](./media/FR-FAQ_mainacct.png)
      
 3. Select **Calculate**.
 4. Export the report to Microsoft Excel.

You should now be able to copy the data from the Financial Reporter Excel report and to the Trial Balance report and compare the **Closing Balance** columns.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
