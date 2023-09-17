---
# required metadata

title: TDS calculation on payments and promissory notes
description: This article provides reference information about the different payment transactions that Tax Deducted at Source (TDS) is calculated on.
author: kailiang
ms.date: 02/12/2021
ms.topic: article
ms.prod: 

ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# 
# ms.tgt_pltfrm: 
ms.assetid: b4b406fa-b772-44ec-8dd8-8eb818a921ef
ms.search.region: Global
# ms.search.industry: 
ms.author: kailiang
ms.search.validFrom: 2021-02-12
ms.dyn365.ops.version: AX 10.0.17

---

# TDS calculation on payments and promissory notes

[!include [banner](../includes/banner.md)]

This article provides reference information about the different payment transactions that Tax Deducted at Source (TDS) is calculated on.

| Serial number | Transaction type | Transaction amount | Page name and path | Account type and offset account type |
|---------------|------------------|--------------------|--------------------|--------------------------------------|
| 1             | Advance payment/Payment against invoice (TDS payable) | Debit or Credit | <ul><li>General journal (**General ledger \> Journal entries \> General journals**)</li><li>Invoice journal (**Accounts payable \> Invoices \> Invoice journal**)</li><li>Payment journal (**Accounts payable \> Payments \> Vendor payment journal**)</li></ul> | Vendor (Dr.), Bank (Cr.) |
| 2             | Advance payment/Payment against invoice (Purchase made from customer – TDS payable) | Debit or Credit | <ul><li>General journal (**General ledger \> Journal entries \> General journals**)</li><li>Invoice journal (**Accounts payable \> Invoices \> Invoice journal**)</li><li>Payment journal (**Accounts payable \> Payments \> Vendor payment journal**)</li></ul> | Customer (Dr.), Bank (Cr.) |
| 3             | Promissory notes | Debit | Draw promissory note journal (**Accounts payable \> Payments \> Promissory notes \> Draw promissory note journal**) | Vendor (Dr.), Ledger (Cr.) |
| 4             | Miscellaneous income (TDS receivable) | Debit or Credit | General journal (**General ledger \> Journal entries \> General journals**) | Bank (Dr.), Ledger (Cr.) |
| 5             | Other expenses (TDS payable) | Debit or Credit | General journal (**General ledger \> Journal entries \> General journals**) | Bank (Dr.), Ledger (Cr.) |

Follow these steps to calculate TDS on payments and promissory notes.

1. On the journal pages, create journal lines. Select the account type and offset account type.
2. Select **Functions \> Settlement** to open the **Open transaction editing** page. Then select a specific invoice that must be settled. If TDS has already been calculated at the invoice level, the **Amount origin** field shows the base amount that the TDS was calculated on. The **TDS amount** field shows the TDS amount that was calculated for the transaction. The **Amount** field shows the net payment amount (that is, the payment amount after TDS is deducted).

    > [!NOTE]
    > For a payment that was made against an invoice, the following conditions apply:
    >
    > - If the payment amount and the invoice amount are the same, TDS isn't calculated if it has already been calculated at the invoice level.
    > - If the invoice amount after the TDS amount is deducted is more than the payment amount, TDS isn't calculated.
    > - If the invoice amount after the TDS amount is deducted is less than the payment amount, TDS is calculated on the amount that exceeds the invoice amount.

3. On the **Journal voucher** page, on the **Overview** tab, in the **TDS groups** field, review or change the default TDS group that is defined for the vendor or customer. TDS that is calculated on journal lines is based on the formula that is defined for the TDS tax codes in the TDS group.

    > [!NOTE]
    > TDS is calculated only if the **Calculate withholding tax** option is set to **Yes** for the vendor on the **Vendors** page.

4. On the **Tax information** tab, in the **Company information** section, in the **Name** field, you can select a company name for alternate addresses that are set up for the company.

    In the **Withholding tax** section, the **Nature of assessee** field shows the nature of assessee category of the vendor or customer. The **Tax account number (TAN)** field shows the tax account number (TAN) of the selected company.

5. Select **Withholding tax button \> withholding tax** to open the **Temporary withholding tax transactions** page. The upper part of this page has the following fields:

    - **Withholding tax amount in total** – The total TDS that was calculated for the transaction for the TDS group.
    - **Value** – The total percentage that was used to calculate TDS for the transaction. The total percentage is based on the formula that is defined for the TDS tax codes and attached to the TDS group.
    - **Adjusted withholding tax amount in total** – The total adjusted TDS amount for all tax codes in the TDS group.
    - **TDS** – A selected checkbox indicates that a TDS group is attached to the transaction.

    The fields on the **Overview**, **General**, and **Adjustment** tabs show the calculated TDS amount and details of the adjusted TDS amount for each TDS tax code that is attached to the TDS group.

6. Select **Threshold** to open the **Threshold** page, where you can review the threshold limit that is defined for the TDS tax component that is attached to a specific TDS tax code.
7. Select **Formula designer** to open the **Formula designer** page, where you can review the formula that is defined for a specific TDS tax code.
8. Close the **Formula designer** and **Temporary withholding tax transactions** pages to return to the **Journal voucher** page.
9. Validate and post the journal. The TDS amount that was calculated is posted to the payable account that is defined for each TDS tax code in the TDS group. The receivable accounts for TDS tax codes are defined on the **Withholding tax codes** page.
10. Select **Posted withholding tax** to open the **Withholding tax transactions** page. The **Value** field shows the total percentage that was used to calculate TDS for the transaction.

    The fields on the **Overview**, **General**, and **Amount** tabs show the TDS amounts that were calculated for the TDS group that is attached to the transaction.

11. Review the TDS calculation information for each TDS tax code that is attached to the TDS group.

## Generate payments

To generate payments, follow these steps.

1. Follow one of these steps:

    - Go to **Accounts payable \> Payments \> Vendor payment journal**.
    - Go to **Accounts receivable \> Payments \> Customer payment journal**.
    - Go to **Accounts payable \> Payments \> Promissory notes \> Draw promissory note journal**.
    - Go to **Accounts receivable \> Payments \> Bill of exchange \> Draw bill of exchange journal**.
    - Go to **Accounts receivable \> Payments \> Bill of exchange \> Redraw bill of exchange journal**.

2. Select **Lines**.
3. Select **Functions \> Generate payments**.
