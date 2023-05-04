---
# required metadata

title: Vendor aging report
description: This article provides information about the Vendor aging report that's available in Microsoft Dynamics 365 Finance.
author: sunfzam
ms.date: 02/13/2023
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

# Vendor aging report

The **Vendor aging** report shows the balances that are due to vendors. Balances on the report are sorted either by date interval or by aging period definition.

## How to filter the data on this report

When you generate the **Vendor aging** report, the following default fields are shown. You can use them to filter the data that will appear on the report. 


| Field | Description |
|-------|-------------| 
| Start date | Enter a date in the first period interval or aging period to include on the report. |
| Balance as of | Enter the date to view the vendor balances for. |
| Criteria | <p>Select the type of date to base the report on:</p><ul><li>**Transaction date** – Use the posting date of the transactions (for example, an invoice date that's the basis for the calculation of the due date).</li><li>**Due date** – Use the due date of the transactions, based on the terms of payment.</li><li>**Document date** – Use a user-defined document date that's the basis for the calculation of the due date.</li></ul> |
| Aging period definition | <p>Select an aging period definition. If you select an aging period definition in this field, the **Interval** field isn't used. Aging period definitions that have more than six aging periods (columns) can't be used on the printed report.</p><p>**Note:** You can set up aging periods on the **Aging period definitions** page.<p> |
| Print aging period description | Select **Yes** to include aging period descriptions at the top of each aging period column on the report. Select **No** to print the report without column headers. |
| Interval | <p>Define the period to use by entering the number of day or month units in each period. For example, to show aging information at intervals of 15 days on the report, enter **15** in this field, and select **Day** in the **Day/Mth** field. To show aging information by month, enter **1** in this field, and select **Month** in the **Day/Mth** field.</p><p>**Note:** The value that you enter in this field is used only if you don't select an aging period definition in the **Aging period definition** field.<p> |
| Day/Mth | Select the unit that defines the period in the **Interval** field. You can select either **Day** or **Month**. |
| Printing direction | Select how you want to calculate balances and print the aging report for past or future periods, relative to the date that's selected in the **Balance as on** field. Select **Backward** to show information for past periods. Select **Forward** to show information for future periods. |
| Details | Select this checkbox to list the transactions that are included in the balances that are shown on the report. |
| Include amounts in transaction currency | Select this checkbox to include the amounts in the transaction currency. |
| Negative balance | Select this checkbox to include negative balances. |
| Exclude zero balance accounts | Select this checkbox to exclude vendors who have a zero balance. |
| Payment positioning | Select this checkbox to include payments that haven't been settled. These payments are shown in the first column of the report. |
| Vendors | The information in this section depends on the query that's created. |
| Current print destination | The information in this section depends on the printing options. | 
