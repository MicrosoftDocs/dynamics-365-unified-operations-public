---
# required metadata

title: General budget reservations
description: This topic provides information about general budget reservations for public sector in Microsoft Dynamics 365 for Finance and Operations.
author: ShylaThompson
manager: AnnBe
ms.date: 02/20/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
ms.search.industry: Public sector
ms.author: brpotter
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# General budget reservations

[!include [banner](../includes/banner.md)]

A general budget reservation, sometimes referred to as a commitment, is a document often used by public sector entities to set aside or earmark budgeted funds so that they are not available for other purposes. Typically these reservations are made before any vendors have been selected for the purchase. Using general budget reservations, an organization can explicitly track planned expenditures for management and reporting. Each purchase requisition, purchase order, or vendor invoice that is generated can be associated with at least one general budget reservation.
General budget reservations are available only if the following conditions are met:

- You have Microsoft Dynamics 365 for Finance and Operations version 8.1 or newer
- The Public Sector, Encumbrance process, and Pre-encumbrance process configuration keys are selected.
- You are using posting definitions (not required if you do not activate commitment accounting).
- Budget control configuration is activated and configured, and budget control is turned on.

General budget reservations contain lines which detail the purpose of the reservation and specifics about the planned reserved funds, including the start and end dates for the reservation. You can add, change, and delete lines, and specify various details such as the item requested, currency, unit price and quantity, and total amount. General budget reservations are intended for use with public sector entities. Private sector entities use the term “budget reservation” with encumbrances or with pre-encumbrances, but such reservations, unlike general budget reservations, are not documents in their own right. 

You can create different types of general budget reservation in order to specify various characteristics and requirements, according to your purchasing needs. For example, you might create three reservation types for use with purchase requisitions, purchase orders, and vendor invoices. A reservation type defines characteristics, such as workflow, and default values for the budget reservation. 
In the general budget reservation, you can also view accounting distributions and subledger journal lines for the transaction. 
If you use project accounting, you can enable committed cost tracking for general budget reservations. 
You can carry over general budget reservations from one fiscal year to the next. You can also close or finalize a completed or expired general budget reservation at year-end.

A general budget reservation is relieved depending on which document references it. If the document is a purchase order, the reservation is relieved when the purchase order is confirmed. If the document is an invoice, and does not reference a purchase order or purchase agreement, the general budget reservation is relieved when the invoice is posted. If the document is a purchase requisition, the reservation is relieved when the requisition is approved.


