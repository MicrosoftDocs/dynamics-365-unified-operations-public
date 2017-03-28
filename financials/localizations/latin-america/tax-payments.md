---
# required metadata

title: Tax payments in Brazil
description: This topic provides information about tax payments in Brazil. In Brazil, users can register and post tax payments together with related fiscal information that must be reported to the tax authorities.
author: ShylaThompson
manager: AnnBe
ms.date: 2017-02-09 20 - 32 - 36
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: FBTaxAssessmentPayment_BR, FBTaxAssessmentPaymentOtherDebits_BR
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 81
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 270254
ms.assetid: 92223189-69a8-4a40-b867-ef9b4f14c23d
ms.search.region: Brazil
# ms.search.industry: 
ms.author: sndray
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Tax payments in Brazil

This topic provides information about tax payments in Brazil. In Brazil, users can register and post tax payments together with related fiscal information that must be reported to the tax authorities.

Overview
--------

Every type of tax in Brazil has its own process, due date, and additional tax statement information that is required by the tax authorities. The **Fiscal books** module generates the Sistema Publico de Escrituração Digital (SPED) statements that are required for taxes. The tax payment process is separated by tax types: ICMS, ICMS-ST, ICMS-DIF, IPI, ISS, and PIS-COFINS.

-   ICMS, ICMS-ST, and ICMS-DIF are state taxes that are related to merchandise movement.
-   ISS is a city tax that is charged by the city.
-   IPI is a production tax that is charged by the federal government. The federal government is also responsible for the PIS and COFINS taxes that are applied to products.

The difference between the tax amount that is collected on sales of goods and the ICMS tax amount that is paid on purchases of goods is calculated. If the net amount is a tax liability, a vendor invoice journal entry can be created. Then the amount of tax that is owed to the tax authority is paid. To pay the taxes, a related tax assessment is created. The tax assessment collects information from the transactions for the correct time frame, as required by the tax. On the **Tax assessment** page, you select the tax to work with. On the **Tax payment** page, you generate the related tax payment. Depending on the collection requirement, there are two ways to create the tax payment:

-   **Create from assessment** – Collect and pay tax monthly, in accordance with the rules that are established by the tax authority.
-   **Other debits** – Collect and pay a specific tax amount outside the regular process when the tax authority requires the payment.

![Creating tax payments](./media/taxpaymentsbra.jpg) 


### Overview

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Payment type</td>
<td>Select one of the following options:
<ul>
<li><strong>Periodic</strong> – Create a monthly periodic payment (regular). All tax transactions that are generated from fiscal documents, and all transaction adjustments (general or by fiscal document) where the special debit configuration of adjustment isn't marked, are summarized to generate the periodic payment.</li>
<li><strong>Other debits</strong> – Make a specific payment of ICMS outside the regular process, because the payment is required by law. Examples include differential of % ICMS and Import goods. All adjustment transactions that are marked as <strong>Other debit payment</strong> in the configuration are summarized to generate a payment.</li>
</ul></td>
</tr>
<tr class="even">
<td>Date</td>
<td>The payment date.</td>
</tr>
<tr class="odd">
<td>ICMS to pay code</td>
<td>The ICMS to pay code that the tax authorities require. This field is available only for ICMS, ICMS-ST, and ICMS-DIF taxes. The following options are available:
<ul>
<li>000: ICMS to collect</li>
<li>003: Anticipation of Aliquot differential</li>
<li>004: Anticipation of Import goods</li>
<li>005: Anticipate tax</li>
<li>006: Anticipation of additional ICMS</li>
<li>090: Other obligations</li>
</ul></td>
</tr>
<tr class="even">
<td>Receita code</td>
<td>The classification of the payment, as defined by the state tax authorities. The program must offer the latest receita code that is used in the previous transactions. Receita codes vary, depending on the payment type. If you select <strong>Other debits</strong> as the payment type, the receita code is entered automatically from the adjustment transactions, provided that the adjustment transactions have a default receita code.</td>
</tr>
<tr class="odd">
<td>Due date</td>
<td>The due date of the payment. If the <strong>Terms of payment</strong> field is blank, you must enter a value in this field. Otherwise, the value is set to the due date that is generated based on terms of payment. After ledger integration is activated, the due date in the ledger transaction will be entered.</td>
</tr>
<tr class="even">
<td>Sales tax amount</td>
<td>The total amount of ICMS to pay. The amount is calculated based on the payment type.</td>
</tr>
<tr class="odd">
<td>Interest amount</td>
<td>The amount of interest in the event of late payments.</td>
</tr>
<tr class="even">
<td>Fine amount</td>
<td>The amount of fines in the event of late payments.</td>
</tr>
<tr class="odd">
<td>Amount</td>
<td>The sum of the sales tax amount, interest amount, and fine amount.</td>
</tr>
<tr class="even">
<td>Reference month</td>
<td>The reference month for this ICMS tax payment, such as <strong>012017</strong>.</td>
</tr>
<tr class="odd">
<td>Voucher</td>
<td>The voucher number. This number is automatically assigned when the payment is posted and the ledger integration is activated.</td>
</tr>
</tbody>
</table>

#### General

| Field                     | Description                                                                                                                                                                                             |
|---------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Description               | Enter a description for the sales tax payments.                                                                                                                                                         |
| Authority                 | Select the tax authority where the tax assessment is created. The sales tax authority defines a vendor account number that is used to transfer sales tax payments to the vendor that makes the payment. |
| Terms of payment          | The terms of payment that are used to determine the due date of a sales tax payment. The terms of payment that you select here will be used for the vendor invoice.                                     |
| Company                   | The legal entity where the tax payment transaction will be posted if ledger integration is activated.                                                                                                   |
| Reversed                  | A selected option indicates that the tax payment was reversed.                                                                                                                                          |
| Trace number              | The trace number for the reversed payment.                                                                                                                                                              |
| Referenced process number | The referenced process number.                                                                                                                                                                          |
| Agency                    | The agency that the referenced process belongs to.                                                                                                                                                      |
| Description               | The description of the referenced process.                                                                                                                                                              |

#### Tax payments

The following tax payments can be made on the **Tax payment** page (**Fiscal books** &gt; **Common** &gt; **Booking period** &gt; **Assessment**):

-   ICMS or ICMS-ST tax assessment
-   IPI tax payment
-   ICMS-DIF tax payment
-   ISS tax payment
-   PIS and COFINS tax payment – One payment is made for PIS tax, and another payment is made for COFINS tax. The type of PIS and COFINS regime is shown in the **Overview** section of the tax payment. A payment can be related to the cumulative regime, the non-cumulative regime, or both regimes.

## Reversing tax payments
You can reverse the transaction for a tax payment that has been posted by selecting the tax payment and clicking **Transaction**. The transaction reversal process reverses the original transaction and all related transactions that were created when the original transaction was posted. The number sequence for the transaction reversal and trace number references in the number sequences must be configured to allow for the registration of reversals. Existing tax payments can be reversed under the following conditions:

-   Ledger integration with Fiscal books is activated on the **Ledger integration** page.
-   The liability that is generated when the tax payment was posted is still in open. Additionally, the current balance in the vendor account of the tax authority must be greater than or less than 0.00

When a tax payment is reversed, the status of the original transaction is set to **Reverse**, and the related sequence number is entered in the **Trace number** field.

## Deleting tax payments
You can delete tax payments if the voucher number wasn't blank when the payment transaction was posted.

