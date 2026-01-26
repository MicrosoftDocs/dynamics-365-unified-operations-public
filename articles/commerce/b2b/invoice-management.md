---
title: Invoice management for B2B e-commerce websites
description: Learn about the invoice management capabilities of Microsoft Dynamics 365 Commerce business-to-business (B2B) e-commerce websites.
author: ShalabhjainMSFT
ms.date: 01/16/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2021-01-31
ms.search.industry: retail
ms.search.form: RetailOperations
---

# Invoice management for B2B e-commerce websites

[!include [banner](../../includes/banner.md)]

This article describes the invoice management capabilities of Microsoft Dynamics 365 Commerce business-to-business (B2B) e-commerce websites.

It's a common practice for companies that handle B2B transactions to accept orders on customer credit and then send an invoice to customers after they fulfill the order. You define payment terms for customers, and you might include some discounts to motivate customers to pay on time or early. To help increase the probability that payments are received on time, B2B e-commerce websites let customers view all their invoices. Customers can easily filter the invoices to view paid, unpaid, and partially paid invoices together with the due dates.

:::image type="content" source="../media/ViewInvoices.png" alt-text="Screenshot of the Invoices page on a B2B website showing invoice list with filtering options.":::

> [!NOTE]
> A signed-in user can view and pay only their own invoices. If you configure an organization account on the **Invoice account** drop-down menu on the **Invoice and delivery** FastTab of the customer record in Commerce headquarters, signed-in users can view and pay invoices for the organization account.

On the **Invoices** page of a B2B website, a user can select an unpaid or partially paid invoice and then select **Pay invoice**. The selected invoice is added to the cart, and the user can proceed with payment. The user can then decide whether to pay the full amount of the invoice or a partial amount. The user can't use the on-account payment method to pay for invoices.

:::image type="content" source="../media/PayInvoice.png" alt-text="Screenshot of the Cart page on a B2B website displaying an invoice ready for payment.":::

On the **Invoices** page, a user can also select **Request invoice** next to an invoice. In this way, the user can request to have the details of the invoice sent to their registered email address.

:::image type="content" source="../media/RequestInvoice2.png" alt-text="Screenshot of the Request invoice dialog box for sending invoice details via email.":::

After a user requests an invoice, the request is moved to the **B2B Requests** section of the **My account** page. Then, after the **P-0001** and **Synchronize orders and channel requests** jobs run in Commerce headquarters, the invoice email is triggered, and the status of the B2B request is marked as completed.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
