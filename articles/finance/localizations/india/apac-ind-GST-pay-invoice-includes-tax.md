---
title: Payment of invoices that include tax
description: Learn about payment of an invoice that includes tax, including a step-by-step process and outline on validating financial entries.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/03/2019
ms.reviewer: johnmichalak 
ms.search.region: India
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.4
---

# Payment of invoices that include tax

[!include [banner](../../includes/banner.md)]

Follow these steps to post an invoice that includes sales tax.

1. Go to **Accounts receivable \> Payments \> Payment journal**.
2. Create a record.
3. In the **Name** field, select a value.
4. On the **Setup** tab, select the **Amounts include sales tax** check box.
5. Select **Lines**.
6. Create a customer advance payment journal.
7. Select **Functions \> Settlement**.
8. In the **Invoice** field, select a value.
9. Close the page.
10. Save the record.
11. Select **Post \> Post**.
12. Close the message that you receive.

### Validate financial entries

Validate the financial entries by selecting **Inquiries \> Voucher**.

The following table shows the tax entries that are generated when an invoice payment is made in various scenarios.

<table>
<thead>
<tr>
<th>Transaction details</th>
<th>Example</th>
<th>Tax entries that are generated during settlement</th>
</tr>
</thead>
</tbody>
<tr>
<td>Invoice = Payment</td>
<td>
<p>Invoice amount: 12,000.00</p>
<p>Payment amount: 12,000.00</p>
</td>
<td>No tax entries are generated.</td>
</tr>
<tr>
<td>Invoice &lt; Payment</td>
<td>
<p>Invoice amount: 6,000.00</p>
<p>Payment amount: 12,000.00</p>
<p>Note that if either a Harmonized System of Nomenclature (HSN) code or a Services Accounting Code (SAC) is defined for the journal, tax is calculated and posted on the journal amount.</p>
</td>
<td>
<ul>
<li>Tax is calculated and posted on the payment amount.</li>
<li>Tax on the payment is reversed to the extent of the invoice amount in the related voucher.</li>
<li>IGST interim payable account Dr. 2,000.00.</li>
<li>IGST payable account Cr. 2,000.00.</li>
</ul>
<p><strong>Related voucher</strong></p>
<p>IGST interim payable account Cr. 1,000.00</p>
<p>IGST payable account Dr. 1,000.00</p>
</td>
</tr>
<tr>
<td>Invoice &gt; Payment</td>
<td>
<p>Invoice amount: 24,000.00</p>
<p>Payment amount: 12,000.00 without tax</p>
</td>
<td>No tax entries are generated.</td>
</tr>
</tbody>
</table>


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
