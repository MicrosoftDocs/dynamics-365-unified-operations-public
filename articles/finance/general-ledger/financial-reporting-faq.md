---
# required metadata

title: Financial reporting FAQ
description: This topic provides answers to some frequently asked questions about Financial reporting.
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

This topic provides answers to frequently asked questions about Financial reporting.

## How do I restrict access to a report by using tree security?

The following example shows how to restrict access to a report by using tree security.

The USMF demo company has a **Balance sheet** report that not all Financial reporting users should have access to. You can use tree security to restrict access to a single report so that only specific users can access it.

1. Sign in to Financial Reporter Report Designer.
2. Select **File \> New \> Tree Definition** to create a new tree definition.
3. Double-tap (or double-click) the **Summary** line in the **Unit Security** column.
4. Select **Users and Groups**.
5. Select the users or groups that require access to the report.
6. Select **Save**.
7. In the report definition, add your new tree definition.
8. In the tree definition, select **Setting**. Then, under **Reporting unit selection**, select **Include all units**.

## How do I identify which accounts don't match my balances?

If you have a report that doesn't have matching balances, use the following procedures to identify each account and variance.

### In Financial Reporter Report Designer

1. Create a new row definition.
2. Select **Edit \> Insert Rows from Dimensions**.
3. Select **MainAccount**.
4. Select **OK**.
5. Save the row definition.
6. Create a new column definition.
7. Create a new report definition.
8. Select **Settings** and unmark this option.
9. Generate the report. 
10. Export the report to Microsoft Excel.

### In Dynamics 365 Finance

1. Go to **General ledger \> Inquiries and reports \> Trial balance**.
2. Set the following fields:

    - **From Date** – Enter the start date of the fiscal year.
    - **To Date** – Enter the date that you're generating the report for.
    - **Financial Dimension** – Set this field to **Main Account set**.

3. Select **Calculate**.
4. Export the report to Excel.

You should now be able to copy the data from the Financial Reporter Excel report to the **Trial Balance** report, so that you can compare the **Closing Balance** columns.

## When I design a report in Report Designer, or when I generate a financial report, I received the following message: "The operation could not be completed due to a problem in the data provider framework." How should I respond?

The message indicates that an issue occurred when the system tried to retrieve financial metadata from the data mart while you were using Financial reporting. There are two ways to respond to this issue:

- Review the integration status of the data by going to **Tools \> Integration status** in Report Designer. If the integration is incomplete, wait for it to be completed. Then retry what you were doing when you received the message.
- Contact Support to identify and work through the issue. There might be inconsistent data in the system. Support engineers can help you identify that issue on the server and find the specific data that might require an update.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
