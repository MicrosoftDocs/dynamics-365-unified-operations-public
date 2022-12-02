---
# required metadata

title: Year-end activities FAQ 
description: This article lists questions that can arise when closing a year, and the answers that can assist with year-end closing activities.
author: moaamer
ms.date: 12/01/2022
ms.topic: index-page
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global 
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2020-12-14
ms.dyn365.ops.version: 10.0.14

---

# Year-end activities FAQ 

[!include [banner](../includes/banner.md)]

This article lists questions that can arise when closing a year, and the answers that can assist with year-end closing activities. The information in this article primarily focuses on questions concerning year-end closing activities for General ledger and Accounts payable.

## General ledger year-end enhancements 
Version 10.0.20 introduced a year-end close enhancement, which is enabled by default starting with version 10.0.25, and is mandatory starting with version 10.0.29. If your organization uses a version earlier than 10.0.25, we recommend enabling this feature before beginning the year-end close process. Before you can use this feature, it must be turned on in your system. Admins can use the Feature management workspace to check the status of the feature and turn it on if it's required. There, the feature is listed in the following way:

 - Module: General ledger
 - Feature name: General ledger year-end enhancements

The setup of the year-end closing templates has moved to a new setup page, **Year-end close template setup**. The existing year-end close page will change in a manner similar to the General ledger foreign currency revaluation, where a list displays each time the year-end close is run or reversed. Historical year-end close information performed prior to enabling the feature won't be displayed. An accounting manager can initiate the year-end close from the new page. 

To reverse the year-end close, select the most recent fiscal year for the appropriate legal entity and choose the **Reverse year-end close** button. The reversal will delete the accounting entries for the previous year-end close and will not rerun the year-end close automatically. If you have enabled the **General ledger year-end enhancements** feature after completing a year-end close, and you want to reverse the historical year, you can reverse the historical year-end results by running the historical year-end close again with the General ledger parameter **Delete existing year-end close entries when re-closing the year** enabled. 

You can rerun the year-end close by restarting the process for the fiscal year and legal entity. The process will continue to use the General ledger parameter setting to determine whether the year-end close rerun will account for only the new or changed transactions, or completely reverse the previous close, rerunning the process for all transactions.

## General ledger: The year-end close process is failing because of an error “The year-end close can’t be run because one or more ledger transactions posted into the fiscal year that you are closing were settled to a ledger transaction in a different fiscal year.” What does this mean? 
Because the feature **Awareness between ledger settlement and year-end close** is enabled, only settled ledger transaction from the fiscal year being closed are excluded from the opening balance. This causes debits and credit to be out of balance. For more information, see the [Awareness between ledger settlement and year-end close](awareness-between-ledger-settlement-year-end-close.md) article.

## General ledger: The reversal of the year-end close process is failing because of an error “The year-end close for 1/1/2022 can’t be reversed because beginning balance transaction have been ledger settled in fiscal year 1/1/2023.” What does this mean? 
Because the feature **Awareness between ledger settlement and year-end close** is enabled, reversals of the year-end processing aren't allowed if the opening transactions have been settled in the new fiscal year. Either reverse the ledger settlement in the new fiscal year 2023 before reversing the 1/1/2022 year or close 1/1/2022 year again, but only for new adjusting entries. Reclosing the year for adjustments only is accomplished by disabling the General ledger parameter **Delete existing year-end entries when re-closing the year**. 

## General ledger: Why isn’t the ledger settlement automation processing December’s ledger settlement transactions? 
The **Automate ledger settlements** feature will run the automation for transactions dated from the first day of the fiscal year to the current date that the occurrence executes. You may need to adjust the execution date of your occurrence to ensure that it is run in December, for fiscal years that end on December 31. For example, assume that you have an automation set up to run monthly on the first day of the month. It will be executed on December 1st, 2022 and is scheduled to run on January 1st, 2023. It is recommended to alter the January 1st, 2023 occurrence to run instead on December 31, 2022. This will ensure that the transactions dated December 2-31 will be considered for automatic settlement. 

## General ledger: What is the difference between Reverse year-end close action and Delete existing year-end entries when re-closing the year parameter for year-end close? 
Confusion might exist over the difference between the **Reverse year-end close** action, and the **Delete existing year-end entries when re-closing** parameter in General ledger (**General ledger > Ledger setup > General ledger parameters**). 
 
Select the **Reverse year-end close** action  when running the year-end close process to delete all closing balance and opening balance entries, as if the year-end close had never been run. The vouchers will be deleted. The year-end close will not run again automatically. To run the year-end close, select the **Run year-end close** action. 

The **Delete existing year-end entries when re-closing the year** parameter in General ledger is used only when running (not reversing) the year-end close. If that parameter is set to **Yes**, all closing balance and opening balance entries will be deleted and the year-end close will run again. This process is used when the organization wants all transactions, including adjustments since the last year-end close, to be posted in a single accounting entry for the closing balance and opening balance entries. 

If this option is set to **No**, all closing balance and opening balance entries remain. They are not deleted. Instead, a new closing balance and opening balance entry will be created for only the delta or new transactions posted since the last year-end close for that fiscal year.  

> [!NOTE]
> The closing balance entry is created in the year being closed. This only occurs if the **Create closing transactions during transfer** parameter in General ledger is set to **Yes**. The opening balance entry is always created, because this is the beginning balance for the next year. 

## General ledger: What can be changed to enhance performance of year-end processing? 
You can make a number of changes to improve performance of the year-end close. We recommend that you evaluate these suggested changes to consider whether the change is appropriate for your organization.

### Optimize year-end close service
**Optimize year-end close** empowers **Dynamics 365 Finance** customers to accelerate their year-end close by moving heavy processing of year-end to a microservice. With an efficient year-end close, the saved time enables each Finance team to react in a timely manner to necessary adjustments, ending in the generation of the financial reports. By processing the year-end close on a microservice, valuable resources are freed up.  The processing elevation minimizes the load on SQL and gives an opportunity to customers to accelerate the year-end close processing.  
  
**Optimize year-end close** is available on APP 10.0.31 and to allow more customers to utilize the new service for the 2022 year-end season. Additionally, **Optimize year-end close** has been backported to 10.0.30 and 10.0.29 versions. For more information, see the [Optimize year-end close](optimize-year-end-close.md) article.

### Dimension sets
When running the year end close, each dimension set balance is rebuilt, having a direct impact on the performance. Some organizations create dimension sets unnecessarily because they were used at one point or might be used at some point.  These unnecessary dimension sets are still rebuilt during the year end close, which adds time to the process. Take time to evaluate your dimension sets and delete any unnecessary dimension sets.

The unnecessary dimension sets also impact the batch job **BudgetDimensionFocusInitializeBalance** (**General ledger > Chart of accounts > Dimensions > Financial dimension sets**).

[![Financial dimension sets.](./media/faq-2020-yr-end-04.png)](./media/faq-2020-yr-end-04.png)

### Year-end close template configuration
The year-end close template lets organizations select the financial dimension level to maintain when transferring profit and loss balances to retained earnings. The settings allow an organization to maintain the detailed financial dimensions (**Close all**) when moving the balances to retained earnings or choose to summarize the amounts to a single dimension value (**Close single**). This can be defined for each financial dimension. For more information on these settings, see the [Year-end close](year-end-close.md) article.

We recommend that you evaluate your organization's requirements and if possible, close as many dimensions as possible using the **Close single** year-end option to improve performance. By closing to a single dimension value (which can also be a blank value), the system calculates less detail when determining the balances for retained earnings account entries.

### Degenerate dimensions

A degenerate dimension provides little to no reuse by itself and in combination with other dimensions. There are two types of degenerate dimensions. The first type is a dimension that is individually degenerate. Typically this type of degenerate dimension will appear on only a single transaction, or on small sets of transactions. The second type is a dimension that becomes degenerate in combination with one or more additional dimensions that exhibit the same potential based on the possible permutations that can be generated. A degenerate dimension can have a significant impact on the performance of the year-end close process. To minimize performance issues, define all degenerate dimensions as **Close single** in the year-end close setup as described in the preceding section.

## Accounts payable: What changes have been made to support 1099 year-end reporting for 2022?

#### Update to all 1099 forms
The following changes have been made to all 1099 forms for the 2022 tax year:

  - In 2021, the year was fixed on 1099 forms. Starting in 2022, the year is filled in by the report. 

#### 1099-MISC
The following updates have been made on Form 1099-MISC for the 2022 tax year:

 - Box 13: Now indicates the Foreign Account Tax Compliance Act (FATCA) filing requirement. 
 - Box 14: Now used to report the excess golden parachute payments. 
 - Box 15: Now used to report the payment under nonqualified deferred compensation (NQDC) plans. 
 - Box 16: Now used to report state withheld taxes.
 - Box 17: Now used to report the payer's state number.
 - Box 18: Now used to report the state income. 

## Accounts payable: 1099 – How do I change the 1099 box and values for a vendor that wasn’t tracking 1099 information throughout the year?
Use the Update 1099 functionality (**Accounts payable > Vendors>All vendors > Select a vendor > Vendor tab in ribbon > Update 1099**) to go through previously paid invoice transactions to reassign the 1099 data appropriately according to the settings on the **Tax 1099** tab on the **Vendor** page.

## Can I run the Update 1099 for all my vendors at once?
You can use the **Update 1099 information for multiple vendors** page to update the 1099 box on a vendor record, and to update transactions with the 1099 box information. You can open this page by going to **Accounts payable > Periodic task > Tax 1099**. You must be assigned to the **Update 1099 box and transactions for multiple vendors** security privilege to access the page. 

## Accounts payable: 1099 – Recalculate existing 1099 amounts versus Update all in the Update 1099 utility
The **Recalculate existing 1099 amounts** check box will reset the 1099 amount to the total paid values, when used in conjunction with the **Update all** check box. 

[![Tax 1099 transactions: Before running the update routine.](./media/faq-2020-yr-end-07.png)](./media/faq-2020-yr-end-07.png)

The **Recalculate existing 1099 amounts** check box only comes into play when there are partial 1099 values on the invoice or if it was modified on the Tax 1099 form. For example, assume you have an invoice valued at $1000.00, but the user manually types in a 1099 amount on the invoice of $500.00.

[![Tax 1099 transactions: Marking both Update all and Recalculate existing 1099 amounts.](./media/faq-2020-yr-end-08.png)](./media/faq-2020-yr-end-08.png)

When this is paid, $500.00 will be the 1099 amount paid. If you perform the recalculation routine, the system will change the 1099 amount to be $1000.00, which is the total that was paid.

[![Tax 1099 transactions: After running the 1099 routine.](./media/faq-2020-yr-end-09.png)](./media/faq-2020-yr-end-09.png)

## Accounts payable: 1099 – Manually create 1099 transactions
An organization might need to manually create 1099 transactions that aren't associated with an invoice. You can add manual 1099 transactions by going to **Accounts payable > Periodic tasks > Tax 1099 > Vendor settlement for 1099s**. Select the **Manual 1099 transactions** button. 

Manually created 1099 transactions are not updated with the **Update all** process or the **Recalculate existing 1099 amounts** process in the **Update 1099** utility.

## Accounts payable: 1099 – Does Dynamics 365 Finance support the 1096 form? 

Dynamics 365 Finance doesn’t print the 1096 Annual Summary and Transmittal of US Information Returns form.

## Accounts payable: 1099 – Are there any new features that support 1099 reporting for Public sector? 
A new Public sector feature, **Update 1099 information by main account**, has been added, which you can enable in the **Feature management** workspace. This feature lets you associate the 1099 values for a vendor by the main account in the accounting distribution, rather than the default account on the vendor record.

For more information, see [Set up vendors for 1099 reporting](../localizations/noam-usa-set-up-vndrs-1099-rprtg.md).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
