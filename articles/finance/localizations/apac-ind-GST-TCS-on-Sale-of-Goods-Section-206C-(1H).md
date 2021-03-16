---
# required metadata

title: TCS on sales of goods 
description: This topic provides information about the functionality for Tax Collection at Source (TCS) on sales of goods.
author: prabhatb
manager: tfehr
ms.date: 03/15/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2020-09-01
ms.dyn365.ops.version: 10.0.13

---

# TCS on sales of goods

[!include [banner](../includes/banner.md)]

This topic provides information about the functionality for Tax Collection at Source (TCS) on sales of goods. For example, it describes how to do the basic setup for TCS deduction on sale of goods transactions, how to calculate TCS on transactions from customers or groups of customers, and how to calculate TCS on transactions when customers don't have a permanent account number (PAN).
Per section 206C (1H), TCS should be collected when payment is received from a customer against a sale consideration. When the seller receives the payment, the TCS amount is debited to the interim account and credited to the TCS payable account. When the invoice is posted, the TCS amount will be posted to the interim payable account and added to the invoice value.
One important aspect of this feature is that if multiple customers have the same PAN, the transaction amount will be accumulated and compared to a threshold to determine whether the transaction is eligible for TCS deduction.

The following illustration shows the process flow for this feature.

![Flow diagram](media/TCS-on-Sale-of-Goods-001.PNG)

## Base amount for TCS deduction

Central Board of Direct Taxes (CBDT) vide circular no. 17, dated September 30, 2020, clarified the base amount for TCS deduction. Because the collection is based on receipt of the amount of the sale consideration, no adjustment because of indirect taxes, including Goods and Services Tax (GST), is required for the collection of tax under this provision. Therefore, TCS that is collected on the sale consideration must include GST.

In the withholding tax group, you can include the GST tax component and charges in the base amount for TCS calculation.


## PAN-based accumulation of transactions for multiple customers

In the case of TCS on sales of goods, TCS will be deducted based on PANs. If multiple customers have the same PAN, all transactions by those customers will be accumulated and compared to the threshold that is prescribed by the government. You can also accumulate the purchase threshold based on the PANs of vendors. 

However, the accumulation is based on vendors or customers in one legal entity. Accumulation among multiple legal entities is out of scope.

## The point of collection of tax

Per the interpretation of TCS on sales of goods under section 206C (1H), tax should be collected "at the time of receipt." The law clarifies that TCS on sales of goods will be collected when actual payment is received by the seller.

However, to collect TCS on sales of goods, the seller must increase the amount of the sales invoice, including the amount of TCS. The seller must also account for the amount in the books as a TCS liability, even though it isn't actually payable. Although the TCS amount is debited to the buyer, the liability under section 206C (1H) doesn't arise until the amount is collected. To accommodate this requirement, a new **Tax liability on payment** option is added for the withholding tax group.

When this option is selected, the **Interim account** field for the withholding tax code becomes available. When a sale of goods is posted, the tax amount on the invoice is posted to the interim TCS payable account and debited to the customer account. When the user receives payment from the buyer, the system posts an invoice transaction to accrue the TCS liability on the payment.


## TCS on advance receipt of payment

Under section 206C(1H), sellers must deduct TCS every time that they receive payment against a sale consideration, or every time that they receive an advance payment. However, aa difficulty arises in the calculation when the amount of the payment that is received crosses the threshold that is set up in the system for transaction values. In this case, you must manually adjust the TCS amount that is calculated on customer payment transactions.

## Changes that have been incorporated based on the CBDT press release

Initially, experts interpreted the new TCS provision in the following way:

   - Tax must be collected when both the amount of the sale and the amount that was received as a sale consideration exceed 50 lakh rupees (INR 5,00,000) during the previous year.
   - Tax must be collected when the amount of the sale exceeds INR 50,00,000, regardless of the amount of the sale consideration that was received during the previous year.
   - Tax must be collected when the amount that was received as a sale consideration exceeds INR 50,00,000, regardless of the amount of the sale that was made during the previous year.
   
Based on this initial interpretation Finance and Operations apps provided functionality for the first option. However, some scenarios didn't comply with the intended law.

To clarify the applicability of the new TCS provisions, the CBDT issued circular no. 17, dated September 30, 2020. According to this circular, the third option is a more convenient, realistic, and reasonable way to get the expected result.

To make the solution comply with the new interpretation, the following changes have been incorporated into the existing feature:

   - **Initial achieved threshold value**: The CBDT clarification states, "It may be noted that this TCS shall be applicable only on the amount received on or after 1st October 2020. However the threshold is based on the yearly receipt, it may be noted that only for calculation of this threshold of Rs. 50 lakh, the receipt from the beginning of the financial year i.e. from 1st April 2020 shall be taken into account. For example, a seller who has received Rs. 1 crore before 1st October 2020 from a particular buyer and receives Rs. 5 lakh after 1st October 2020 would be required to collect tax on Rs. 5 lakh only and not on Rs. 55 lakh [i.e Rs.1.05 crore - Rs. 50 lakh (threshold)] but for threshold calculation amount received before 1st October will also be considered. To meet this change we introduced an initial threshold value concept."
   - **TCS when payment is collected from the customer against a sale consideration**: The CBDT clarification states, "It may be noted that this TCS applies only in cases where the receipt of sale consideration exceeds Rs. 50 lakh in a financial year. For example, a seller who has made sales of Rs. 1 crore before 1st October 2020 from a particular buyer and receives only Rs. 10 lakh after 1st October 2020 would not be required to collect tax on 10 lakh as the payment amount has not crossed the threshold value of Rs. 50."

   Based on this statement, you can use the **Feature management** workspace to enable TCS deduction when payment is collected from a customer against a sales consideration.

   - **Direct voucher posting of the TCS amount on payment and invoice transactions**: In the initial solution that was provided for TCS deduction, posting was done through related vouchers. The redesigned solution lets you post the TCS amount directly in the ledger. You don't have to post it through a related voucher.
   - **When TCS on sales is applied on Accounts payable transactions, the tax amount is posted to a recoverable account**: When you apply TCS on sales on a purchase transaction, the TCS amount is posted directly to the TCS recoverable account. You must then match the TCS ledger with Form 26AS to determine the TCS amount for a claim against the tax liability.
   - **The credit note reverses the TCS transaction without affecting the accumulated value for the threshold**: The tax must be calculated on the sale consideration that is received from the buyer. Therefore, when the credit note that is issued adjusts the buyer's ledger, the adjustment has no effect on the tax that must be collected. The posting will remain the same if the seller repays some of the sale consideration to the buyer after the tax is collected. In this situation, the amount of the sale consideration that the seller receives isn't reduced by the amount that is refunded for the calculation of TCS.
   - **TCS groups can automatically be entered from the invoice account**: In the **Feature management** workspace, you can enable the TCS group to automatically be entered on a sales transaction from the invoice account instead of the customer account. This functionality lets you address scenarios that involve third-party invoices.
   - **TCS groups can automatically be entered from the vendor account on a purchase transaction**: In the **Feature management** workspace, you can enable the TCS group to automatically be entered on a purchase transaction if the TCS withholding group is attached to the vendor account.

## Key scenarios covered

- Tax rates that have three decimal places
- Sales orders
- Free text invoices
- Customer payment journals
- Project invoices
- General journals
- Multi-line journals
- TCS through invoice accounts
- PAN-based accumulation of thresholds
- Credit notes

## Out-of-scope scenarios

- Intercompany transactions

## Feature support

The feature is supported in following versions of Microsoft Dynamics 365 Finance, or later versions:

- 10.0.14
- 10.0.15

## Set up TCS on sales of goods on a collection-of-payment basis

To enable TCS on sales of goods on a collection-of-payment basis, you must complete three tasks.

1. **Turn on the feature through Feature management**. Section 206C(1H) states that tax must be collected when the amount is received as consideration for the sale of goods. In other words, tax must be collected if the amount is received on or after October 1, 2020.

To turn on the feature, go to **Workspaces** > **Feature management**, select the **Enable TCS calculation on payment collection from customer basis** feature, and then select **Enable now**.
 
You can also turn on the following features if they are required for your:

   - Third- business party Invoice Scenario: Enable TDS/TCS information through invoice account
   - TCS on Purchase transactions: Enable "TDS/TCS withholding tax group" defaulting from the master form without differentiating the nature of the transaction

2. **Enable the threshold hierarchy**. To apply the TCS rate, based on whether a customer has a PAN, select the **Enable threshold hierarchy** check box in the **TCS on sales tax** code.
3. **Enable liability on payment**. To deduct TCS when payment is collected, select the **Liability on payment** check box.

    > [!NOTE]
    > If the **Liability on the payment** check box is cleared, the system creates TCS liability on the Invoice. If the **Enable TCS calculation on payment collection from customer basis** feature isn't turned on, the system considers both the invoice and the payment amount for threshold determination.

## Initial threshold achieved value
TCS is applicable from October 1, 2020. However, for threshold determination, transaction accumulation occurs from April 1 of every financial year.
The following example shows how the accumulated value is determined for TCS calculation:

   - The threshold value is INR 50,00,000.
   - TCS is applicable from October 1, 2020.
   - The transaction is run as shown in the following table.
   
   | Date      | Invoice | Amount    |
   |-----------|---------|-----------|
   | 1-Aug-20  | INV-001 | 20,00,000 |
   | 15-Aug-20 | INV-002 | 10,00,000 |
   | 28-Aug-20 | Payment | 15,00,000 |
   | 1-Sep-20  | Payment | 5,00,000  |
   | 15-Sep-20 | INV-003 | 50,00,000 |
   | 25-Sep-20 | Payment | 20,00,000 |
   | 10-Oct-20 | Payment | 12,00,000 |


## Create a new withholding tax code for sales of goods

1. Go to **Tax \> Setup \> Withholding tax code**.
2. In the left pane, select **Sale of Goods**.

    When you attach a withholding tax component of the **TCS** type, the new **Interim account** field on the **General** FastTab becomes available.

    > [!IMPORTANT]
    > Don't select an interim account yet. You will select it after you set the **Tax liability on payment** option to **Yes** for the withholding tax group in the next procedure.

3. Set the **Enable threshold hierarchy** option to **Yes**. The **PAN based accumulation** option become available.
4. If multiple customers have the same PAN, set the **PAN based accumulation** option to **Yes**.

![Withholding tax codes page](media/TCS-on-Sale-of-Goods-002.PNG)

## Create a new withholding tax group for sales of goods

1. Go to **Tax \> Setup \> Withholding tax group**.
2. In the left pane, select **Sale of Goods**.
3. Create a withholding tax group that has the **TCS** tax type, and set the **Tax liability on payment** option to **Yes**.
4. Go to **Tax \> Setup \> Withholding tax code**.
5. On the **Withholding tax codes** page, in the **Interim account** field, select **Interim TCS payable account**. This account was created in the chart of account and has the **India withholding tax (TCS)** posting type.
6. Return to the **Withholding tax groups** page.
7. In the **Include GST tax component for TDS or TCS calculation** field, include the GST tax component if it's part of the calculation of the TCS base amount.
8. If charges aren't part of the TCS calculation, in the **Exclude charges for TDS or TCS calculation** field, select **Yes**.
9. On the Action Pane, select **Designer**, and define the formula for TCS calculation.

![Withholding tax groups page](media/TCS-on-Sale-of-goods-003.PNG)

## Define threshold definitions

1. Go to **Tax \> Setup \> Threshold definitions**.
2. Define a threshold definition for sales of goods.
3. Define two threshold slabs:

    - 0-Max
    - Max-0

![Threshold designer page](media/TCS-on-Sale-of-Goods-004.PNG)

## Set up the TCS threshold for sales of goods

TCS on sales of goods applies to either a single customer or multiple customers that have the same PAN.

If the customer PAN isn't available, a higher tax rate will be applied after the exempted turnover amount is passed. If the customer PAN is available, the lower tax rate will be applied.

1. Define threshold references for customers.

    ![Threshold references page](media/TCS-on-Sale-of-goods-005.PNG)

2. Select **Threshold designer**.
3. Define two threshold slabs that have the following options:

    - With PAN number
    - Without PAN number

4. Define a separate TCS rate for each option.
5. Define the calculation basis for each slab:

    - For the exempted slab, set the following values:

        - **Calculate tax:** No

            Alternatively, set the **Calculate tax** option to **Yes**, and set the value to **0** (zero).

        - **Calculate previous non-tax transactions:** No
        - **Include in turnover base:** Yes

    - For the taxable slab, set the following values:

        - **Calculate tax:** Yes
        - **Calculate previous non-tax transactions:** No
        - **Include in turnover base:** Yes

![Threshold designer page](media/TCS-on-Sale-of-Goods-006.PNG)

## Activate the calculation of TCS for customers

- Go to **Accounts receivable \> Customers \> All customers**.

![All customer page](media/TCS-on-Sale-of-Goods-007.PNG)

## Invoice posting

When an invoice is posted, if the accumulated transaction passes the threshold limit, the following accounting entry is posted.

| Item | Qty | Unit price | Net amt. | Tax group | IGST     | Tax rate | Threshold value |
|------|-----|------------|----------|-----------|----------|----------|-----------------|
| A    | 6   | 10,000     | 60,000   | Cust1     | IGST @10 | 10       | 50,000          |

If the customer PAN is available, the TCS rate is 0.1 percent.

> [!NOTE]
> From October 1, 2019, through March 31, 2020, the TCS rate is 0.0750 percent.

The invoice is posted as shown here.

| Account                                       | Debit  | Credit |
|-----------------------------------------------|--------|--------|
| Customer A/C (Invoice amount)                 | 66,016 |        |
| Ledger A/C (Sales A/C)                        |        | 60,000 |
| GST Payable                                   |        | 6,000  |
| Interim TCS Payable A/C (0.1% on 66000-50000) |        | 16     |

## TCS liability that arises when payment is collected

When payment is received, and the invoice is attached to the payment transaction, the TCS amount is calculated based on the full payment amount and reversed through a related voucher. However, another related voucher is generated together with the invoice. This related vouched shows tax liability recognition in books for the eligible amount only.

| Account             | Debit  | Credit |
|---------------------|--------|--------|
| Bank                | 66,016 |        |
| Customer            |        | 66,016 |
| Interim TCS Payable | 65.95  |        |
| TCS Payable         |        | 65.95  |

The related voucher is generated as shown here.

| Account             | Debit | Credit |
|---------------------|-------|--------|
| Interim TCS payable |       | 65.95  |
| TCS Payable         | 65.95 |        |

> [!IMPORTANT]
> Another related voucher will be generated together with the posted sales invoice to book the actual TCS liability.

Go to the posted sales invoice voucher, and check the related voucher entry.

| Account             | Debit | Credit |
|---------------------|-------|--------|
| Interim TCS payable | 16.00 |        |
| TCS Payable         |       | 16.00  |

> [!NOTE]
> In the case of a purchase transaction where the vendor is deducting TCS, you must create a new TCS withholding group.

## TCS that vendors deduct on purchases of goods

If the selling vendor deducts TCS against the organization, you must create a separate **TCS on purchase of goods** withholding tax group. On the **Withholding tax group** page, in the **Apply threshold** section, set the **PAN based accumulation** option to **Yes**. You must define a threshold definition for the vendor and attach the withholding tax group to the vendor. When the purchase order is posted, the TCS amount that the vendor deducted will be posted to the TCS recoverable account.

Every organization will claim a credit for the TCS deduction after the deduction is reconciled by using Form 26AS.

1. Go to **Tax \> Inquiries and reports \> TDS/TCS inquiry**.
2. Select the required column fields to generate the report.

![Tax transaction inquiry page](media/TCS-on-Sale-of-Goods-008.PNG)
