---
# required metadata

title: Postdated checks
description: This article provides information about support for postdated checks. Postdated checks are issued to make and receive payments on a future date.
author: angelad116
ms.date: 01/12/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: VendPostDatedChecks, CustPostDatedChecks
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.assetid: 4eb7c7da-1e6b-4d35-9f41-373b66103229
ms.search.region: Global
# ms.search.industry: 
ms.author: angelading
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Postdated checks

[!include [banner](../includes/banner.md)]

This article provides information about support for postdated checks. Postdated checks are checks that are issued to make and receive payments on a future date. Therefore, the check can't be cashed until the specified date.

Dynamics 365 Finance supports the full management cycle for postdated checks in both Accounts receivable and Accounts payable, as shown in the following table.
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Scenario</th>
<th>Details</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Set up postdated checks</td>
<td>You must set up a new payment method, and specify the payment routine for clearing accounts for issued checks, received checks, and withholding tax.</td>
</tr>
<tr class="even">
<td>Register and post a postdated check for a vendor</td>
<td>Register the details of a postdated check that you issue to a vendor. When the payment is posted, the vendor liability is recognized, but the bank account isn’t yet credit. Instead, a clearing account is used for this purpose. </td>
</tr>
<tr class="odd">
<td>Register and post a postdated check for a customer</td>
<td>Register the details of a postdated check that you receive from a customer. When the payment is posted, the customer receivable is credit, but the bank account isn’t yet debit. Instead, a clearing account is used for this purpose.</td>
</tr>
<tr class="even">
<td>Register and post a replacement postdated check for a customer or a vendor</td>
<td>
If your original check to a vendor or from a customer is lost or damaged, you can issue a replacement postdated check. When you register the check details, provide a reference to the original check, and indicate that the new check is a replacement for the original. You can also post the replacement check.</td>
</tr>
<tr class="odd">
<td>Transfer a customer postdated check to a vendor</td>
<td>When you receive a postdated check from a customer, you can transfer that check to a vendor as a payment.</td>
</tr>
<tr class="even">
<td>Settle a postdated check for a customer or a vendor</td>
<td>Settle a postdated check that is posted to a bridging account for a customer or a vendor when the check finally matures. When the check is settled, the bank is finally debit or credit against the clearing account that was used earlier.</td>
</tr>
<tr class="odd">
<td>Cancel a postdated check for a vendor</td>
<td>You can cancel a posted postdated check in these situations:
- The check is returned by the bank.
- The check is applied to an incorrect invoice.
- A cash payment is made against the check.
  </td>
  </tr>
  <tr class="even">
  <td>Stop payment for a postdated check</td>
  <td>You can stop payment on a postdated check that was issued to a vendor, for reasons such as not sufficient funds, changes in the terms of the agreement with the vendor, supply of defective goods by the vendor, or return of goods to the vendor. You can stop payment only on checks that haven’t cleared.</td>
  </tr>
  </tbody>
  </table>



For more information, see the following topics:

[Set up postdated checks](tasks/set-up-postdated-checks.md)

[Register and post a postdated check for a customer](tasks/register-post-postdated-check-customer.md)

[Settle a postdated check from a customer](tasks/settle-postdated-check-customer.md)

[Register and post a postdated check for a vendor](tasks/register-post-postdated-check-vendor.md) 

[Settle a postdated check for a vendor](tasks/settle-postdated-check-vendor.md)





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
