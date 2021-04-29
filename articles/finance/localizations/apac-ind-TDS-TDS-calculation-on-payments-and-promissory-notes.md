---
# required metadata

title: TDS calculation on payments and promissory notes
description: This topic provides reference information for different payment transactions that Tax Deducted at Source (TDS) is calculated on. 
author: kailiang
manager: AnnBe
ms.date: 02/12/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 15721
ms.assetid: b4b406fa-b772-44ec-8dd8-8eb818a921ef
ms.search.region: Global
# ms.search.industry: 
ms.author: kailiang
ms.search.validFrom: 2021-02-12
ms.dyn365.ops.version: AX 10.0.17

---

# TDS calculation on payments and promissory notes

[!include [banner](../includes/banner.md)]

This topic provides reference information for different payment transactions that Tax Deducted at Source (TDS) is calculated on. 

| Serial number | Transaction type                                             | Transaction amount | Form name and locator                                        | Account type and offset account type |
| ------------- | ------------------------------------------------------------ | ------------------ | ------------------------------------------------------------ | ------------------------------------ |
| 1.            | Advance payment / Payment against invoice (TDS payable)      | Debit  Or  Credit  | General journal form  (General ledger >  Journal entries > General journals), Invoice journal form (Accounts payable >  Invoices > Invoice journal), Payment journal form (Accounts payable >  Payments > Vendor payment journal) | Vendor (Dr.)  Bank (Cr.)             |
| 2.            | Advance payment/ Payment against invoice (Purchase made  from customer –TDS payable) | Debit  Or  Credit  | General journal form  (General ledger >  Journal entries > General journals), Invoice journal form (Accounts payable >  Invoices > Invoice journal), Payment journal form (Accounts payable >  Payments > Vendor payment journal) | Customer (Dr.)  Bank (Cr.)           |
| 3.            | Promissory notes                                             | Debit              | Draw promissory note journal form (Accounts payable >  Payments > Promissory notes > Draw promissory note journal) | Vendor (Dr.)  Ledger (Cr.)           |
| 4.            | Miscellaneous income (TDS receivable)                        | Debit  Or  Credit  | General journal form (General ledger >  Journal entries > General journals) | Bank (Dr.)  Ledger (Cr.)             |
| 5.            | Other expenses  (TDS payable)                                | Debit  Or  Credit  | General journal form (General ledger >  Journal entries > General journals) | Bank (Dr.)  Ledger (Cr.)             |

Complete the following steps to calculate TDS on payments and promissory notes. 

1. Create journal lines using the journal forms, select the account type and offset account type.

2. Click the **Functions button > settlement** to open the **Open transaction editing** page and select a specific invoice that needs to be settled. If TDS is already calculated at the invoice-level, in the **Amount origin** field, the base amount that the TDS is calculated on is displayed. The TDS amount that's calculated for the transaction is displayed in the **TDS amount** field. View the net payment amount, which is the payment amount after deducting TDS, in the **Amount** field.

> [!Note]
> For a payment made against an invoice, the following conditions apply: <br>
   - TDS is not calculated if it is already calculated at the invoice-level if the payment amount and invoice amount are same.<br>
   - TDS is not calculated if the invoice amount after deducting the TDS amount is greater than the payment amount.<br>
   - TDS is calculated on the amount that exceeds the  invoice amount if the invoice amount after deducting the TDS amount is less than the payment amount.  

3. View or modify the default TDS group defined for the vendor or customer. This information is in the **TDS group** field, on the **Overview** tab on the **Journal** **voucher** page. The TDS calculated on journal lines is based on the formula defined for the TDS tax codes in the TDS group.

>   [!Note]
>   TDS is calculated only if the **Calculate withholding tax** check box is selected for the vendor in the **Vendors**  form.  

4. Click the **Tax information** tab. The company name is displayed in the **Name** field under the **Company information** field group. You can select a company name for alternate addresses that are set up for the company. 

5. View the nature of assessee category of the vendor or customer in the **Nature of assessee** field under the **Withholding tax** field group. View the tax account number of the selected company in the **Tax account number (TAN)** field. 

6. Click **Withholding tax button > withholding tax** to open the **Temporary withholding tax transactions** page. View the following fields on the upper pane of the **Temporary withholding tax transactions** page.

- **Withholding tax amount in total** field: The total TDS calculated for the transaction for the TDS group.
- **Value** field: The total percentage used to calculate TDS for the transaction. The total percentage is based on the formula that's defined for TDS tax codes and that's attached to the TDS group.
- **Adjusted withholding tax amount in total** field: The total adjusted TDS amount for all tax codes in the TDS group.
- **TDS** check box: This check box will be selected if a TDS group is attached to the transaction.

  The fields on the **Overview** tab, **General** tab, and **Adjustment** tab on the **Temporary withholding tax transactions** page display the calculated TDS amount and adjusted TDS amount details for each TDS tax code attached to the TDS group.

7. Click the **Threshold** button to open the **Threshold** page. View the threshold limit defined for the TDS tax component attached to a specific TDS tax code on this page.

8. Click the **Formula designer** button to open the **Formula designer** page. View the formula defined for a specific TDS tax code on this page.

9. Close the **Formula designer** and **Temporary withholding tax transactions** pages to return to **Journal voucher**.

10. Validate and post the journal. The TDS amount calculated is posted to the payable account that is defined for each TDS tax code in the TDS group. The receivable accounts for TDS tax codes are defined on the **Withholding tax codes** page.

11. Click **Posted withholding tax** button to open the **Withholding tax transactions** page. In the **Value** field, view the total percentage used to calculate TDS for the transaction.

The fields on the **Overview** tab, **General** tab, and **Amount** tab on the **Withholding tax transactions** page display the TDS amounts that are calculated for the TDS group that's attached to the transaction. View the TDS calculation information for each TDS tax code attached to the TDS group on this page.

### Generate payments

Generate payments using the **Generate payments** function in the following locations:

- **Accounts payable > Payments > Vendor payment journal > Lines button > Functions button > Generate payments**
- **Accounts receivable > Payments > Customer payment journal > Lines button > Functions button > Generate payments**
- **Accounts payable > Payments > Promissory notes > Draw promissory note journal > Lines button > Functions button > Generate payments**
- **Accounts receivable > Payments > Bill of exchange > Draw bill of exchange journal > Lines button > Functions button > Generate payments**
- **Accounts receivable > Payments > Bill of exchange > Redraw bill of exchange journal > Lines button > Functions button > Generate payments**
