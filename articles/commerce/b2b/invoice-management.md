---
# required metadata

title: Invoice management for B2B e-commerce websites
description: This topic describes invoice management capabilities for B2B e-commerce websites using Microsoft Dynamics 365 Commerce.
author: shajain
ms.date: 02/09/2022
ms.topic: article
ms.prod: 
ms.technology: 
# optional metadata
ms.search.form: RetailOperations
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: v-chgriffin
#ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: retail
ms.author: shajain
ms.search.validFrom: 2021-01-31
ms.dyn365.ops.version: 10.0.14

---

# Invoice management for B2B e-ecommerce website

[!include [banner](../../includes/banner.md)]

This topic describes invoice management capabilities for business-to-business (B2B) e-commerce websites using Microsoft Dynamics 365 Commerce.

It is a common practice for companies handling B2B transactions to accept orders on customer credit and then send an invoice to customers after fulfilling the order. Payment terms are defined for customers and there may be some discounts to motivate customers to pay on or before time. To increase the probability of receiving payments on time, B2B e-commerce websites enable customers to view all of their invoices. Invoices can easily be filtered to view paid, unpaid, and partially paid invoices along with the due dates of the invoices.

![Invoices page on a B2B website](/articles/commerce/media/ViewInvoices.png)

> [!NOTE]
> A signed-in user can only view and pay the user's invoice. If an organization account is configured on the **Invoice account** drop-down menu under the **Invoice and delivery** FastTab of the customer record in Commerce headquarters, then the user will be able to view and pay for the organization account.

On the **Invoices** page of a B2B website, a user can select an unpaid or partially paid invoice and then select **PAY INVOICE** to add the invoice to the cart and proceed with payment. The user can then decide to either pay the full amount of the invoice or pay a partial amount. The user cannot use the on-account payment method to pay for invoices. 

> [!NOTE]
> Currently an invoice can only be added to the cart if there are no items in the cart. Conversely, items can only be added to the cart if there are no invoices in the cart. There are plans to remove this restriction in future Commerce releases.

![Cart page on a B2B website](/articles/commerce/media/PayInvoice.png)

A user can also request to send the details of an invoice to the user's registered email address by selecting **REQUEST INVOICE** next to the invoice on the **Invoices** page of the B2B website.

![Request invoice dialog box](/articles/commerce/media/RequestInvoice2.png)

After requesting the invoice, the request is moved to the **B2B Requests** section of the **My account** page. Once the **P-0001** and **Synchronize orders and channel requests** jobs are run in headquarters, the invoice email is triggered and the status of the B2B request is marked as completed.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
