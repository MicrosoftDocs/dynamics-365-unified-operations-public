---
# required metadata

title: Advance payments that are settled during invoice posting
description: This topic provides information about the tax that is posted on a customer advance payment when the payment is settled and the customer invoice is posted.
author: EricWangChen
ms.date: 06/03/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: wangchen
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.4

---

# Advance payments that are settled during invoice posting

[!include [banner](../includes/banner.md)]

The following tables shows the tax entries that are generated for the invoice when an advance payment is settled in various scenarios.

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
<li>Tax on the invoice is posted.</li>
<li>Tax on the payment is reversed to prevent a double entry in the related voucher.</li>
<li>IGST payable account Cr. 2,000.00.</li>
</ul>
<p><strong>Related voucher:</strong></p>
<p>IGST interim payable account Cr. 2,000.00</p>
<p>IGST payable account Dr. 2,000.00</p>
</td>
</tr>
<tr>
<td>Invoice &lt; Payment</td>
<td>
<p>Invoice amount: 6,000.00</p>
<p>Payment amount: 12,000.00</p>
</td>
<td>
<ul>
<li>Tax on the invoice is posted.</li>
<li>Tax on the payment is reversed to the extent of the invoice amount in the related voucher.</li>
<li>IGST payable account Cr. 1,000.00.</li>
</ul>
<p><strong>Related voucher:</strong></p>
<p>IGST interim payable account Cr. 1,000.00</p>
<p>IGST payable account Dr. 1,000.00</p>
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
<li>Tax on the invoice is posted.</li>
<li>Tax on the payment is reversed to the extent of the payment amount in the related voucher.</li>
<li>IGST payable account Cr. 4,000.00</li>
</ul>
<p><strong>Related voucher:</strong></p>
<p>IGST interim payable account Cr. 2,000.00</p>
<p>IGST payable account Dr. 2,000.00</p>
</td>
</tr>
</tbody>
</table>


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
