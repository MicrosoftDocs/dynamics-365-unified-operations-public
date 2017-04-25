---
# required metadata

title: Withholding tax in Thailand
description: This topic provides information about withholding tax and how to set it up for Thailand. The withholding tax functionality has been enhanced for both vendor and customer transactions, so that withholding tax is calculated and withholding tax reports are generated.
author: ShylaThompson
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 81
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 265904
ms.assetid: d530961f-98af-475a-9556-88169e20fb71
ms.search.region: Thailand
# ms.search.industry: 
ms.author: leguo
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Withholding tax in Thailand

[!include[banner](../includes/banner.md)]


This topic provides information about withholding tax and how to set it up for Thailand. The withholding tax functionality has been enhanced for both vendor and customer transactions, so that withholding tax is calculated and withholding tax reports are generated.

Set up Thailand withholding tax
-------------------------------

You must complete the following tasks before you can calculate withholding tax for transactions for a legal entity in Thailand:

1.  Set up tax registration numbers on the **Legal entities** page.
2.  Set up withholding settlement periods on the **Withholding tax settlement periods** page.
3.  Set up withholding tax authorities on the **Withholding tax authorities** page.
4.  Set up withholding tax codes on the **Withholding tax codes** page.
5.  Set up withholding tax groups on the **Withholding tax groups** page.
6.  Set up withholding tax revenue types on the **Withholding tax revenue** **types** page.
7.  Set up withholding tax groups on the **Item withholding tax groups** page for an item or service.
8.  Select the **Calculate withholding tax** check box on the **Vendors** page.
9.  Select the **Calculate withholding tax** check box on the **Customers** page.
10. Select the **Calculate withholding tax** check box on the **Released products** page.

## Payments that include withholding taxes
Any payment that is made to a vendor is taxable, and the legal entity pays tax on the withholding tax. The tax that the legal entity pays on the withholding tax is also taxable. This additional tax amount is paid by the vendor. You can use either the single iteration method or the perpetual gross-up method to gross up vendor payments. For example, for a purchase order amount of THB 4,000 and a withholding tax (WHT) rate of 15 percent, here is how the tax amount, the tax on the tax amount, and the total payment amount are calculated:

-   **Single iteration method** – In this method, part of the withholding tax is paid by the legal entity, and the other part is paid by the vendor.
    -   Tax on tax amount = Tax amount × WHT rate = 600 × 0.15 = THB 90
    -   Total payment amount = Purchase order amount + (Purchase order amount × WHT rate) – (Purchase order amount × WHT rate) – (Purchase order amount × WHT rate) × WHT rate = 4,000 + 600 – 600 – 90 = THB 3,910
    -   Tax amount = Purchase order amount × WHT rate = 4,000 × 0.15 = THB 600
-   **Perpetual gross-up method** – If the number of iterations to calculate the tax on the tax amount increases, the amount that is grossed up (the purchase order amount) decreases in value. In the perpetual gross-up method, a perpetual gross-up rate percentage is calculated by using the WHT rate. The perpetual gross-up rate percentage is then rounded to two decimal places to calculate the grossed-up amount.
    -   Total payment amount = Purchase order amount × Perpetual gross-up rate percentage = 4,000 × 117.65% = THB 4,706
    -   The withholding tax at 15 percent is deducted from the total payment amount of THB 4,706. In other words, (4,706 – \[4,706 × 0.15\]) = THB 4,000. In this manner, the vendor receives the original payment amount after withholding tax is deducted.
    -   Perpetual gross-up rate percentage = 100 ÷ (1 – WHT rate) = 100 ÷ (1 – 15%) = 100 ÷ 0.85 = 117.65%

### Withholding tax for item or service purchases

Use the **Journal voucher** page to enter and post payments that you make to a vendor for the purchase of items or services. When you post a vendor payment journal, the withholding tax group that is set up for the vendor is used to calculate the withholding tax on the transaction.

### Withholding tax for item or service sales

Use the **Journal voucher** page to enter and post payments that you receive from customers. You must post a customer payment journal or general journal for withholding tax transactions that include the tax branch code.

### Making a withholding tax payment on behalf of a vendor

Performance awards that are given to vendors are taxable and can be withheld by a legal entity. You can make withholding tax payments on behalf of the vendor. In this case, the tax that you pay is treated as an expense for the company. This process is referred to as payment gross-up. You can generate the withholding tax reports after you post a payment journal for a vendor.

## Generate withholding tax reports
You must generate the **Withholding tax certificate** report after you've settled payments and before you post a vendor payment journal. On the **Withholding tax slip** page, select to generate the **Withholding tax certificate** report. You can also generate the **Withholding tax (Por Ngor Dor 53)**, **Withholding tax (Por Ngor Dor 3)**, **Withholding tax special**, **Withholding tax accounts receivable journal**, and **Withholding tax accounts payable journal** reports after you post a payment journal. You can mark transactions that should be excluded from withholding tax reports.

### Generate the Withholding tax special report

When you submit the **Withholding tax (Por Ngor Dor 53)** or **Withholding tax (Por Ngor Dor 3)** report, and you pay the withheld tax to the Revenue Department of Thailand, the department issues a receipt number. You must enter this receipt number in the **Receipt number** field on the **Posted withholding tax** page. Then, at the end of the month, you must generate the **Withholding tax special** report and submit it to the Revenue Department of Thailand. This report is generated in a format that is specified by the Revenue Department of Thailand.



