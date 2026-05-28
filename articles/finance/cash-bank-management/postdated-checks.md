---
title: Postdated checks
description: Learn about support for postdated checks. Postdated checks are issued to make and receive payments on a future date, including details for various scenarios.
author: twheeloc
ms.author: twheeloc
ms.topic: article
ms.date: 05/27/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: VendPostDatedChecks, CustPostDatedChecks
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 4eb7c7da-1e6b-4d35-9f41-373b66103229
---

# Postdated checks

[!include [banner](../includes/banner.md)]

This article provides information about support for postdated checks. Postdated checks are checks that you issue to make and receive payments on a future date. Therefore, the check can't be cashed until the specified date.

Dynamics 365 Finance supports the full management cycle for postdated checks in both Accounts receivable and Accounts payable, as shown in the following table.

| Scenario | Details |
|----------|---------|
| Set up postdated checks | Set up a new payment method, and specify the payment routine for clearing accounts for issued checks, received checks, and withholding tax. |
| Register and post a postdated check for a vendor | Register the details of a postdated check that you issue to a vendor. When you post the payment, the vendor liability is recognized, but the bank account isn't yet credited. Instead, a clearing account is used for this purpose. |
| Register and post a postdated check for a customer | Register the details of a postdated check that you receive from a customer. When you post the payment, the customer receivable is credited, but the bank account isn't yet debited. Instead, a clearing account is used for this purpose. |
| Register and post a replacement postdated check for a customer or a vendor | If your original check to a vendor or from a customer is lost or damaged, you can issue a replacement postdated check. When you register the check details, provide a reference to the original check, and indicate that the new check is a replacement for the original. You can also post the replacement check. |
| Transfer a customer postdated check to a vendor | When you receive a postdated check from a customer, you can transfer that check to a vendor as a payment. |
| Settle a postdated check for a customer or a vendor | Settle a postdated check that you post to a bridging account for a customer or a vendor when the check finally matures. When you settle the check, the bank is finally debited or credited against the clearing account that was used earlier. |
| Cancel a postdated check for a vendor | Cancel a posted postdated check in these situations:<br>- The check is returned by the bank.<br>- The check is applied to an incorrect invoice.<br>- A cash payment is made against the check. |
| Stop payment for a postdated check | Stop payment on a postdated check that you issued to a vendor, for reasons such as not sufficient funds, changes in the terms of the agreement with the vendor, supply of defective goods by the vendor, or return of goods to the vendor. You can stop payment only on checks that aren't cleared. |

For more information, see the following articles:

[Set up postdated checks](tasks/set-up-postdated-checks.md)

[Register and post a postdated check for a customer](tasks/register-post-postdated-check-customer.md)

[Settle a postdated check from a customer](tasks/settle-postdated-check-customer.md)

[Register and post a postdated check for a vendor](tasks/register-post-postdated-check-vendor.md)

[Settle a postdated check for a vendor](tasks/settle-postdated-check-vendor.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
