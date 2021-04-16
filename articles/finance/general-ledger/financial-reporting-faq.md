---
# required metadata

title: Financial reporting FAQ 
description: This topic provides answers to frequently asked questions about financial reporting. 
author: jiwo
ms.date: 01/13/2021
ms.topic: article
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

## How do I restrict access to a report using tree security?

The following example shows how to restrict access to a report using tree security.

The USMF demo company has a Balance sheet report that not all Financial reporting users should have access to. To restrict access, you can use tree security to restrict access to a single report so that only certain users can access the report. Follow these steps to do restrict access: 

1. Sign in to Financial Reporter Report Designer.

2. Create a new tree definition. Go to **File > New > Tree Definition**.
3. Double-click the **Summary** line in the **Unit Security** column.
4. Select **Users and Groups**.  
5. Select the users or groups that need access to this report. 
6. Select **Save**.
7. In the report definition, add your new tree definition.
8. In the tree definition, select **Setting**. Under **Reporting unit selection**, select **Include all units**.

## How do I determine which accounts do not match my balances?

If you have a report that doesn't have matching balances, here are some steps you can take to identify each of the accounts and variances. 

**Financial Reporter Report Designer**
1. In Financial Reporter Report Designer, create a new row definition. 
2. Select **Edit > Insert Rows from Dimensions**.
3. Select **MainAccount**.  
4. Select **OK**.
5. Save the row definition.
6. Create a new column definition
7. Create a new report definition.
8. Select **Settings** and unmark this option.  
9. Generate the report. 
10. Export the report to Microsoft Excel.

**Dynamics 365 Finance** 
1. In Dynamics 365 Finance, go to **General Ledger > Inquiries and Reports > Trial Balance**.
2. Set the following parameters:
   - **From Date**- Enter the start of the fiscal year.
   - **To Date** - Enter the date you are generating the report for.
   - **Financial Dimension** - Set this field to **Main Account set**.
 3. Select **Calculate**.
 4. Export the report to Microsoft Excel.

You should now be able to copy the data from the Financial Reporter Excel report and to the Trial Balance report and compare the **Closing Balance** columns.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
