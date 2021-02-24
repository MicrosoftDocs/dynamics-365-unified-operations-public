---
# required metadata

title: TDS calculation on payments and promissory notes
description: This topic provides reference information for different payment transactions that the Tax Deducted at Source (TDS) is calculated on. 
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

This topic provides reference information for different payment transactions that the Tax Deducted at Source (TDS) is calculated on. 

| Serial number | Transaction type                                             | Transaction amount | Form name and locator                                        | Account type and offset account type |
| ------------- | ------------------------------------------------------------ | ------------------ | ------------------------------------------------------------ | ------------------------------------ |
| 1.            | Advance payment / Payment against invoice (TDS payable)      | Debit  Or  Credit  | General journal form  (General ledger >  Journal entries > General journals), Invoice journal form (Accounts payable >  Invoices > Invoice journal), Payment journal form (Accounts payable >  Payments > Vendor payment journal) | Vendor (Dr.)  Bank (Cr.)             |
| 2.            | Advance payment/ Payment against invoice (Purchase made  from customer –TDS payable) | Debit  Or  Credit  | General journal form  (General ledger >  Journal entries > General journals), Invoice journal form (Accounts payable >  Invoices > Invoice journal), Payment journal form (Accounts payable >  Payments > Vendor payment journal) | Customer (Dr.)  Bank (Cr.)           |
| 3.            | Promissory notes                                             | Debit              | Draw promissory note journal form (Accounts payable >  Payments > Promissory notes > Draw promissory note journal) | Vendor (Dr.)  Ledger (Cr.)           |
| 4.            | Miscellaneous income (TDS receivable)                        | Debit  Or  Credit  | General journal form (General ledger >  Journal entries > General journals) | Bank (Dr.)  Ledger (Cr.)             |
| 5.            | Other expenses  (TDS payable)                                | Debit  Or  Credit  | General journal form (General ledger >  Journal entries > General journals) | Bank (Dr.)  Ledger (Cr.)             |

Follow these steps to calculate TDS on payments and promissory notes. 

1. Create journal lines using the journal forms, select the account type and offset account type.

2. Click functions button > settlement to open the **Open** **transaction** **editing** form to select a specific invoice that needs to be settled. If TDS is already calculated at the invoice-level, in the **Amount** **origin** field, the base amount that the TDS is calculated on is displayed and in the **TDS** **amount** field, the TDS amount calculated for the transaction is displayed. In the **Amount** field, view the net payment amount after deducting the TDS amount.

>   [!Note]
>
>   For payment made against invoice, the  following conditions apply:  1. TDS is not calculated if it is already  calculated at the invoice-level if the payment amount and invoice amount are  same.  2. TDS is not calculated if the invoice amount  after deducting the TDS amount is greater than the payment amount.  3. TDS is calculated on the amount that exceeds the  invoice amount if the invoice amount after deducting the TDS amount is lesser  than the payment amount.  

3. On the **Overview** tab in the **Journal** **voucher** form, in the **TDS** **group** field, view or modify the default TDS group defined for the vendor or customer. The TDS calculated on journal lines is based on the formula defined for the TDS tax codes in the TDS group.

>   [!Note]
>
>   TDS is calculated only if the **Calculate**  **withholding** **tax** check box is selected for the vendor in the **Vendors**  form.  

4. Click the **Tax** **information** tab. Under the **Company** **information** field group, in the **Name** field, the company name is displayed. You can select a company name of alternate addresses that are set up for the company in this field. 

5. Under the **Withholding** **tax** field group, in the **Nature** **of** **assessee** field, view the nature of assessee category of the vendor or customer. In the **Tax** **Account** **Number** (**TAN**) field, view the TAN of the selected company. 

6. Click withholding tax button > withholding tax to open the **Temporary** **withholding** **tax** **transactions** form. View the following fields on the upper pane of the **Temporary** **withholding** **tax** **transactions** form.

- **Withholding** **tax** **amount** **in** **total** field: The total TDS calculated for the transaction for the TDS group.

- **Value** field: The total percentage used to calculate TDS for the transaction. The total percentage is based on the formula that is defined for TDS tax codes attached to the TDS group.

- **Adjusted** **withholding** **tax** **amount** **in** **total** field: The total adjusted TDS amount for all tax codes in the TDS group.

- **TDS** check box: This check box is displayed as selected if a TDS group is attached to the transaction.

  The fields on the **Overview** tab, **General** tab, and **Adjustment** tab in the **Temporary** **withholding** **tax** **transactions** form display the calculated TDS amount and adjusted TDS amount details for each TDS tax code attached to the TDS group.

7. Click the **Threshold** button to open the **Threshold** form. View the threshold limit defined for the TDS tax component attached to a specific TDS tax code in this form.

8. Click the **Formula** **designer** button to open the **Formula** **designer** form. View the formula defined for a specific TDS tax code in this form.

9. Close the Formula designer form and Temporary withholding tax transactions form to return to the Journal voucher form.

10. Validate and post the journal. The TDS amount calculated is posted to the payable account that is defined for each TDS tax code in the TDS group. The receivable accounts for TDS tax codes are defined in the **Withholding** **tax** **codes** form.

11. Click **Posted withholding tax** button to open the **Withholding** **tax** **transactions** form. In the **Value** field, view the total percentage used to calculate TDS for the transaction.

The fields on the **Overview** tab, **General** tab, and **Amount** tab in the **Withholding** **tax** **transactions** form display the information of TDS calculated for the TDS group attached to the transaction. View the TDS calculation information for each TDS tax code attached to the TDS group in this form.

### Generate payments

Generate payments using the **Generate** **payments** function in the following locations:

- **Accounts payable > Payments > Vendor payment journal > Lines button > Functions button > Generate payments**
- **Accounts receivable > Payments > Customer payment journal > Lines button > Functions button > Generate payments**

- **Accounts payable > Payments > Promissory notes > Draw promissory note journal > Lines button > Functions button > Generate payments**

- **Accounts receivable > Payments > Bill of exchange > Draw bill of exchange journal > Lines button > Functions button > Generate payments**

- **Accounts receivable > Payments > Bill of exchange > Redraw bill of exchange journal > Lines button > Functions button > Generate payments**
