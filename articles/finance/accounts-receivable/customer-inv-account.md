---
title: Customer and invoice accounts
description: Learn about customer and invoice accounts in Microsoft Dynamics 365 Finance, including an outline on sales order fields with examples.
author: JodiChristiansen
ms.author: jchrist
ms.topic: article
ms.date: 08/05/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: LedgerTransVoucher, LedgerJournalTable
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: b4b406fa-b772-44ec-8dd8-8eb818a921ef
---

# Customer and invoice accounts

[!include [banner](../includes/banner.md)]

In Microsoft Dynamics 365 finance and operations apps, invoices are an essential part of the sales process. The assumption is that the customer who places an order also receives the invoice. However, there might be situations where the customer who must be invoiced differs from the customer who places the order. This article explains the concept of customer accounts and invoice use.

## Sales order fields

When you create an order or sales order in Finance and Operations apps, the **Invoice and delivery** FastTab provides the fields that you need to manage the invoicing process.

In the **Invoice account** field, select the customer account to invoice. This customer account can differ from the one that's associated with the order. This capability is useful when parties such as resellers or distributors act as intermediaries between the order customer and the invoicing party.

### Examples

- **Same customer account**

    In most cases, the customer account that you select for invoicing is the same as the customer account that's associated with the order. This scenario applies when the order customer is also responsible for receiving the invoice directly. In these cases, update the **Invoice account** field with the order customer's account. Therefore, you don't need to make a manual selection.

- **Separate customer accounts**

    In some cases, the customer who places the order isn't responsible for receiving the invoice directly. An example is a sales scenario where a distributor places an order on behalf of a retailer. In these cases, select the distributor's account in the **Invoice account** field.

### Other fields to consider

- **Billing address** – When you invoice a different customer account, provide the correct billing address that's associated with the invoice recipient.
- **Financial agreement** – Align any financial agreements, such as payment terms or credit limits, with the selected invoice account.
- **Communication** – Clear communication and information exchange between involved parties, including the order customer and the invoice recipient, are critical to preventing misunderstandings or delays.
