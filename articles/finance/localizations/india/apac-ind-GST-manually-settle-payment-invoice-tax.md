---
title: Manual settlement of an advance payment and invoice that include tax
description: Learn about the tax entries that are generated in various scenarios when an invoice and a payment that include tax are settled.
author: epodkolzina
ms.author: epodkolzina
ms.topic: conceptual
ms.custom: 
  - bap-template
ms.date: 07/01/2024
ms.reviewer: johnmichalak 
ms.search.region: India
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.4
---

# Manual settlement of an advance payment and invoice that include tax

[!include [banner](../../includes/banner.md)]

Tax is posted on both the advance payment and the sales invoice. When these transactions are settled on the **Open transaction editing** page, the double tax entry is reversed.

The following table shows the tax entries that are generated in various scenarios when an invoice and a payment that have tax are settled.

<table>
<thead>
<tr>
<th>Transaction details</th>
<th>Example</th>
<th>Tax entries that are generated during settlement</th>
</tr>
</thead>
<tbody>
<tr>
<td>Invoice = Payment</td>
<td>
<p>Invoice amount: 12,000.00</p>
<p>Payment amount: 12,000.00</p>
</td>
<td>
<ul>
<li>Tax on the payment is reversed.</li>
<li>IGST interim payable account Cr. 2,000.00.</li>
<li>IGST payable account Dr. 2,000.00.</li>
</ul>
<td>
</tr>
<tr>
<td>Invoice &lt; Payment</td>
<td>
<p>Invoice amount: 6,000.00</p>
<p>Payment amount: 12,000.00</p>
</td>
<td>
<ul>
<li>Tax on the payment is reversed to the extent of the invoice amount.</li>
<li>IGST interim payable account Cr. 1,000.00.</li>
<li>IGST payable account Dr. 1,000.00.</li>
</ul>
</td>
</tr>
<tr>
<td>Invoice &gt; Payment</td>
<td>
<p>Invoice amount: 24,000.00</p>
<p>Payment amount: 12,000.00</p>
</td>
<td>
<ul>
<li>Tax on the payment is reversed.</li>
<li>IGST interim payable account Cr. 2,000.00.</li>
<li>IGST payable account Dr. 2,000.00.</li>
</ul>
</td>
</tr>
</tbody>
</table>


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
