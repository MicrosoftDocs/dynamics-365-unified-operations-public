---
# required metadata

title: Invoice management on B2B e-commerce website
description: This topic describes the capabilities around requesting and paying invoices directly from the B2B e-commerce website.
author: shajain
ms.date: 02/05/2022
ms.topic: article
ms.prod: 
ms.technology: 
# optional metadata
ms.search.form: RetailOperations
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: v-chgri
#ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: retail
ms.author: shajain
ms.search.validFrom: 2021-01-31
ms.dyn365.ops.version: 10.0.14

---

# Invoice management on B2B e-ecommerce website

[!include [banner](../../includes/banner.md)]

This topic describes the capabilities around requesting and paying invoices directly from the B2B e-commerce website.
It is a common practice for companies dealing with B2B operations to accept the orders on customer credit and after fulfilling the order, send an invoice to the customers. There are payment terms defined for the customers such as Net10, Net30 etc. along with some discounts to motivate the customers to pay on or before time. To increase the probability of receiving the payment on time, the B2B e-commerce website enables the customers to view all their invoices. They can easily filter the invoices to view paid, unpaid, and partially paid invoices along with the due date of the invoice.

![View invoices](/articles/commerce/media/ViewInvoices.png "View invoices on the B2B website")

> [!NOTE]
> The logged in user can only view and pay for their invoice. If the organization account is set on the “Invoice account” of the customer record, then the user will view and pay for the organization account.

The user can select an unpaid or partially paid invoice and press the “Pay invoice” button to add the invoice to the cart and then proceed with the payment. The user can decide to either pay the full amount or pay the partial amount for the invoice. As expected, the user cannot use the on account payment to pay for invoices. 

> [!NOTE]
> An invoice can be added to the cart only if there are no items in the cart and vice versa. This restriction would be removed in future.

![Pay invoices](/articles/commerce/media/PayInvoice.png "Pay invoices from the B2B website")

The user can also request to send the invoice details on the registered email. To do so, the user can press the “Request invoice” button.

![Request an invoice on email](/articles/commerce/media/RequestInvoice.png "Request invoices from the B2B website")

> [!NOTE]
> After requesting the invoice, this request is moved to the “B2B Requests” section of the “My account" page. Once the P-0001 job and Synchronize orders and channel requests job are run, then the invoice email gets triggered and the status of the B2B request is marked as completed

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
