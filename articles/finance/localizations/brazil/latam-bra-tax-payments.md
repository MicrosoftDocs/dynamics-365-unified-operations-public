---
title: Tax payments in Brazil
description: Learn about tax payments in Brazil. Users register and post tax payments together with related fiscal information that must be reported to the tax authorities.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/05/2026
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2016-11-30
ms.search.form: FBTaxAssessmentPayment_BR, FBTaxAssessmentPaymentOtherDebits_BR
ms.assetid: 92223189-69a8-4a40-b867-ef9b4f14c23d
---

# Tax payments in Brazil

[!include [banner](../../includes/banner.md)]

This article provides information about tax payments in Brazil. In Brazil, users can register and post tax payments together with related fiscal information that must be reported to the tax authorities.

Every type of tax in Brazil has its own process, due date, and additional tax statement information that the tax authorities require. The **Fiscal books** module generates the Sistema Publico de Escrituração Digital (SPED) statements that are required for taxes. The tax payment process is separated by tax types: ICMS, ICMS-ST, ICMS-DIF, IPI, ISS, and PIS-COFINS.

- ICMS, ICMS-ST, and ICMS-DIF are state taxes that relate to merchandise movement.
- ISS is a city tax that the city charges.
- IPI is a production tax that the federal government charges. The federal government is also responsible for the PIS and COFINS taxes that apply to products.

The system calculates the difference between the tax amount collected on sales of goods and the ICMS tax amount paid on purchases of goods. If the net amount is a tax liability, you can create a vendor invoice journal entry. Then pay the amount of tax that you owe to the tax authority. To pay the taxes, create a related tax assessment. The tax assessment collects information from the transactions for the correct time frame, as required by the tax. On the **Tax assessment** page, select the tax to work with. On the **Tax payment** page, generate the related tax payment. Depending on the collection requirement, there are two ways to create the tax payment:

- **Create from assessment** – Collect and pay tax monthly, in accordance with the rules that the tax authority establishes.
- **Other debits** – Collect and pay a specific tax amount outside the regular process when the tax authority requires the payment.

:::image type="content" source="../media/taxpaymentsbra.jpg" alt-text="Screenshot of creating tax payments.":::

| Field | Description |
|---|---|
| Payment type | Select one of the following options: <br><br> **Periodic** – Create a monthly periodic payment (regular). Summarize all tax transactions that fiscal documents generate, and all transaction adjustments (general or by fiscal document) where the special debit configuration of adjustment isn't marked, to generate the periodic payment. <br><br> **Other debits** – Make a specific payment of ICMS outside the regular process, because the payment is required by law. Examples include differential of % ICMS and Import goods. Summarize all adjustment transactions that are marked as **Other debit payment** in the configuration to generate a payment. |
| Date | The payment date. |
| ICMS to pay code | The ICMS to pay code that the tax authorities require. This field is available only for ICMS, ICMS-ST, and ICMS-DIF taxes. The following options are available: <br><br> 000: ICMS to collect <br> 003: Anticipation of Aliquot differential <br> 004: Anticipation of Import goods <br> 005: Anticipate tax <br> 006: Anticipation of additional ICMS <br> 090: Other obligations |
| Receita code | The classification of the payment, as defined by the state tax authorities. The program must offer the latest receita code that is used in the previous transactions. Receita codes vary, depending on the payment type. If you select **Other debits** as the payment type, the receita code is entered automatically from the adjustment transactions, provided that the adjustment transactions have a default receita code. |
| Due date | The due date of the payment. If the **Terms of payment** field is blank, you must enter a value in this field. Otherwise, the value is set to the due date that is generated based on terms of payment. After ledger integration is activated, the due date in the ledger transaction is entered. |
| Sales tax amount | The total amount of ICMS to pay. The amount is calculated based on the payment type. |
| Interest amount | The amount of interest in the event of late payments. |
| Fine amount | The amount of fines in the event of late payments. |
| Amount | The sum of the sales tax amount, interest amount, and fine amount. |
| Reference month | The reference month for this ICMS tax payment, such as **012017**. |
| Voucher | The voucher number. This number is automatically assigned when you post the payment and activate the ledger integration. |

#### General

| Field                     | Description                                                                                                                                                                                             |
|---------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Description               | Enter a description for the sales tax payments.                                                                                                                                                         |
| Authority                 | Select the tax authority where you create the tax assessment. The sales tax authority defines a vendor account number that is used to transfer sales tax payments to the vendor that makes the payment. |
| Terms of payment          | The terms of payment that are used to determine the due date of a sales tax payment. The terms of payment that you select here are used for the vendor invoice.                                     |
| Company                   | The legal entity where the tax payment transaction is posted if ledger integration is activated.                                                                                                   |
| Reversed                  | A selected option indicates that the tax payment was reversed.                                                                                                                                          |
| Trace number              | The trace number for the reversed payment.                                                                                                                                                              |
| Referenced process number | The referenced process number.                                                                                                                                                                          |
| Agency                    | The agency that the referenced process belongs to.                                                                                                                                                      |
| Description               | The description of the referenced process.                                                                                                                                                              |

#### Tax payments

You can make the following tax payments on the **Tax payment** page (**Fiscal books** &gt; **Common** &gt; **Booking period** &gt; **Assessment**):

- ICMS or ICMS-ST tax assessment
- IPI tax payment
- ICMS-DIF tax payment
- ISS tax payment
- PIS and COFINS tax payment – One payment is made for PIS tax, and another payment is made for COFINS tax. The type of PIS and COFINS regime is shown in the **Overview** section of the tax payment. A payment can be related to the cumulative regime, the non-cumulative regime, or both regimes.

## Reversing tax payments

You can reverse the transaction for a tax payment that you posted by selecting the tax payment and clicking **Transaction**. The transaction reversal process reverses the original transaction and all related transactions that the process created when it posted the original transaction. You must configure the number sequence for the transaction reversal and trace number references in the number sequences to register reversals. You can reverse existing tax payments under the following conditions:

- You activate ledger integration with fiscal books on the **Ledger integration** page.
- The liability that the tax payment posting generates is still open. Additionally, the current balance in the vendor account of the tax authority must be greater than or less than 0.00.

When you reverse a tax payment, the status of the original transaction is set to **Reverse**, and the related sequence number is entered in the **Trace number** field.

## Deleting tax payments

You can delete tax payments if the voucher number isn't blank when you post the payment transaction.

## Additional resources

[Set up interest and fines for vendor payments](br-00065-1-set-up-interest-fines-vendor-payments.md)

[Calculate interest and fines on vendor payments](br-00065-2-calculate-interest-fines-vendor-payments.md)

[Set up interest and fines on customer payments](br-00066-1-set-up-interest-fines-customer-payments.md)

[Calculate interest and fines on customer payments](br-00066-2-calculate-interest-fines-customer-payments.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
