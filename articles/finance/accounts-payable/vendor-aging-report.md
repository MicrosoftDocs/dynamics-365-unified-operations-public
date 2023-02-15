---
# required metadata

title: Vendor aging report
description: This article provides information about the Vendor aging report available in Microsoft Dynamics 365 Finance.
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

The Vendor aging report displays the balances that are due to vendors, sorted by date interval or by aging period definition.

## How to filter the data on this report
When you generate this report, the following default parameters are displayed. You can use these parameters to filter the data that will be displayed on the report. 
For more information, see Filter the data on a report.

| Field              | Description  |
|--------------------|----------------|

|**Start date**	|Enter a date in the first period interval or aging period to include on the report.|
|**Balance as of**|	Enter the date to view the vendor balances for.|
|**Criteria**	| <p>Select the type of date to base the report on.</p><ul><li>
**Transaction date** – The posting date of the transactions. For example, an invoice date that is the basis for the calculation of the due date.</li><li>
**Due date** – The due date of the transactions, based on the terms of payment.</li><li>
**Document date** – A user-defined document date that is the basis for the calculation of the due date.</li></ul><p>|
|**Aging period definition**	|Select an aging period definition. The **Interval** field isn't used if an aging period definition is selected.|
Aging period definitions that have more than six aging periods (columns) can't be used on the printed report.
<ul><li>>[!Note]
>You can set up aging periods in the **Aging period definitions** page.</li></ul>|
|**Print aging period description**|	Select **Yes** to include aging period descriptions at the top of each aging period column on the report. Select **No** to print the report without column headers.|
|**Interval**|Define the period to use by entering the number of the day or month units in each period. For example, enter 15 and select **Day** in the **Day/Mth** field to show aging information at intervals of 15 days on the report. To show aging information by month, enter 1 in this field and select **Month** in the **Day/Mth** field.
<ul><li>>[!Note]
>The information that you enter in this field is used only if an aging period definition isn't selected.</li></ul>|

|**Day/Mth**|	Select the unit, either **Day** or **Month**, that is used to define the period in the **Interval** field.|
|**Printing direction**|	Select how to calculate balances and print the aging report for past or future periods, relative to the date that is selected in the **Balance as on** field. Select **Backward** to display information for past periods. Select **Forward** to display information for future periods.|
|**Details**	|Select this checkbox to list the transactions that are included in the balances that are shown on the report.|
|**Include amounts in transaction currency**	|Select this checkbox to include the amounts in transaction currency.|
|**Negative balance**	|Select this checkbox to include negative balances.|
|**Exclude zero balance accounts**	|Select this checkbox to exclude vendors who have a zero balance.|
|**Payment positioning**	|Select this checkbox to include payments that haven't been settled. These are displayed in the first column of the report.|
|**Vendors**|	The information displayed in this section is determined by the created query.|
|**Current print destination**|	The information displayed in this section is determined by the printing options.| 


