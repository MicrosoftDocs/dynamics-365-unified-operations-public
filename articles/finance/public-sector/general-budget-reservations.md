---
title: General budget reservations
description: Learn about general budget reservations for Public sector. General budget reservations are only available in the outlined conditions.
author: brpotter
ms.author: twheeloc
ms.topic: article
ms.date: 08/29/2021
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2018-10-31
ms.search.form: BudgetReservation_PSN
ms.dyn365.ops.version: 8.1
---

# General budget reservations

[!include [banner](../includes/banner.md)]

A *general budget reservation* is a document that is sometimes also referred to as a *commitment*. Public sector entities often use this document to set aside or earmark budgeted funds so that they aren't available for other purposes. Typically, these reservations are made before any vendors have been selected for the purchase. By using general budget reservations, an organization can explicitly track planned expenditures for management and reporting purposes. Each purchase requisition, purchase order, or vendor invoice that is generated can be associated with at least one general budget reservation.

General budget reservations are available only if the following conditions are met:

- You have version 8.1 or later.
- The **Public sector**, **Encumbrance process**, and **Pre-encumbrance process** configuration keys are turned on.
- You're using posting definitions. (However, you don't have to use posting definitions if you don't activate commitment accounting.)
- The Budget control configuration is activated and configured, and budget control is turned on.

General budget reservations contain lines that provide details about the purpose of the reservation and the planned reserved funds. These details include the start and end dates for the reservation. You can add, change, and delete lines. You can also specify various details, such as the item that is requested, the currency, the unit price and quantity, and the total amount. General budget reservations are intended to be used by public sector entities.

Private sector entities use the term *budget reservation* to talk about encumbrances or pre-encumbrances. However, unlike general budget reservations, those budgets reservations aren't documents.

You can create different types of general budget reservation to specify various characteristics and requirements, based on your purchasing needs. The characteristics include the workflow that is used for the reservation, and default values. For example, you create three reservation types. You use one type for purchase requisitions, another type for purchase orders, and another type for vendor invoices.

In the general budget reservation, you can also view accounting distributions and subledger journal lines for the transaction.

> [!NOTE]
> Ledger accounts used on general budget reservations must be included in budget control. If those accounts aren't included in budget control, the following will occur. 
>- General budget reservation and their consuming documents won't be encumbered or pre-encumbered. 
>- Carry-forward transactions won't create budget register entries. 
>- Canceling and finalizing general budget reservations won't reduce carry-forward budget.
>- Ledger accounts won't be included on the budget analysis and budget control statistics inquiries.

If you use project accounting, you can turn on tracking of committed costs for general budget reservations.

You can carry over general budget reservations from one fiscal year to the next. You can also close or finalize a completed or expired general budget reservation at the end of the year.

A general budget reservation is relieved differently, depending on the document that references it:

- If the document is a purchase order, the reservation is relieved when the purchase order is *confirmed*.
- If the document is an invoice, and it doesn't reference a purchase order or purchase agreement, the general budget reservation is relieved when the invoice is *posted*.
- If the document is a purchase requisition, the reservation is relieved when the purchase requisition is *approved*.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
