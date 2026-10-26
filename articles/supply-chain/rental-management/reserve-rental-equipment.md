---
title: Reserve fleet items (preview)
description: Learn how to use reservation requests and reservations to manage fleet item availability for planned rental contracts.
author: jodahlMSFT
ms.author: jodahl
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 10/23/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Reserve fleet items (preview)

[!INCLUDE [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Reservations help ensure that fleet items are available when a customer needs them. A rental reservation holds a fleet item for a customer over a date range in rental management. Rental management supports two types: *reservation requests*, which can refer to a rental class, model, or individual fleet item without locking a specific fleet item, and *reservations*, which lock a specific fleet item.

## Understand reservation types

The following table describes the differences between reservation requests and reservations.

| Feature | Reservation request | Reservation |
|---|---|---|
| Level | Individual fleet item, model, or rental class | Specific fleet item |
| Locks a specific fleet item | No | Yes |
| Visible to other coordinators | Yes (as demand) | Yes (as committed) |
| Blocks other rentals | No, never | Depends on the reservation configuration |

## Create a reservation request

A reservation request captures demand for a rental class, model, or individual fleet item over a specific date range. It earmarks one or more fleet items to signal that demand to other rental coordinators, but the earmark is soft: it doesn't lock those fleet items, so they stay available to others, and you can even rent or sell them.

To create a reservation request, follow these steps:

1. Open a rental quotation, and select the quotation line that you want to reserve.
1. On the Action Pane, on the **Quotation** tab, in the **Reservation** group, select **Create reservation request**.
1. Set the reservation dates to match the expected rental period. If the line has no fleet item, select a **Rental class** or a **Model** to describe what the customer needs. The reservation type must have **Class allowed** or **Model allowed** turned on.
1. Select **OK** to create the reservation request.

Reservation requests are useful in the following situations:

- The customer has confirmed they need a specific type of fleet item but hasn't specified a preferred fleet item.
- You want to signal demand.
- The ship date is far enough out that you don't need to commit a specific fleet item yet.

## Create a reservation

A reservation locks a specific serialized fleet item for a customer. Depending on the reservation configuration, it can block other users from putting the fleet item on a quotation, contract, or sales order for a different customer or a different responsible worker.

To create a reservation, follow these steps:

1. Open a rental quotation, and select the quotation line that you want to reserve. The line must have a fleet item assigned. For a line without one, use **Create reservation request** instead.
1. On the Action Pane, on the **Quotation** tab, in the **Reservation** group, select **Create reservation**.
1. In the **Reservation** dialog, check **Reservation type**, which defaults from your row in the **Rental user setups** grid. Also check **Customer account** or **Prospect**, **Opportunity ID**, **Start date**, and **End date**, which default from the quotation. **Opportunity ID** is mandatory when **Opportunity required** is turned on for the reservation type, and **End date** isn't available when the type has **Open end date** turned on.
1. Select **OK**. The **Fleet item reservations** page opens with the new reservation, which holds the fleet item on the line together with the attachments that are attached to it.

You can also reserve fleet items from the **Fleet item availability** page: select the **Marked** check box for each fleet item, and then, in the **Reservation** group, select **Create reservation**.

You can reserve a fleet item only while it isn't committed to another customer, which means it's on an active contract line for a different customer over dates that overlap the reservation.

Each contract and each reservation records a responsible worker, so you can contact the coordinator who holds the fleet item. A fleet item also can't be on two active reservations whose dates overlap. The same check runs when you change the dates of a reservation and when you convert a reservation request into a reservation. The check doesn't apply to reservation requests, because they don't lock a fleet item.

> [!TIP]
> Start with reservation requests during the quoting phase to signal demand. Convert to reservations as the ship date approaches.

## Reservation statuses

Both reservation requests and reservations move through statuses during their lifecycle.

| Status | Description |
|---|---|
| *Active* | The reservation is in effect and hasn't expired or been superseded. |
| *Expired* | The reservation passed its expiry date without being converted or canceled. |
| *Converted* | The reservation was fulfilled—for example, when you converted its quotation to a contract, when you converted it to a rental contract or sales order, or when you added its fleet item to a contract. |
| *Canceled* | You canceled the reservation manually before it expired or converted. |

## Review, convert, and cancel reservations

The **Fleet item reservations** page lists reservation requests and reservations together. To open it, go to **Rental management (Preview)** > **Common** > **Reservations** > **All reservations**. You can also select **View reservations** on the **Fleet item availability** page or on a rental quotation.

The list opens with **Only mine** selected, so it shows only the records that you created. Use the **Status** and **Period** filters to widen it. **Type** and **Status** are separate columns: **Type** says how strongly the record holds a fleet item, *Request* or *Reservation*, and **Status** says what happened to it. Converting a request changes **Type** and leaves **Status** at *Active*.

The **Fleet item on reservation** tab lists the fleet items that the record holds, each with a **Convert** check box that decides which of them a conversion includes. The **Reference** tab shows the documents and the opportunity that the record is linked to, and the **Administration** tab shows the responsible worker.

You can edit, cancel, or convert a record only while its status is *Active*, and only if you created it. To let a worker act on records that other workers created, an administrator selects **Manage all reservations** for that worker in the **Rental user setups** grid.

To convert a reservation request, select it, and then select **Convert to reservation**. The request must hold at least one fleet item, must not have expired, and must be free of a conflict with another customer's contract or with an overlapping active reservation. Its start date, length, and fleet type must also fall inside the limits of its reservation type.

From then on, the validation rules and stop rules of the reservation type apply.

To create a document from a reservation, select it, and then, in the **Conversion** group, select **Convert to rental quotation**, **Convert to rental contract**, **Convert to sales quotation**, or **Convert to sales order**. A command is available only while the reservation isn't already linked to a rental or sales quotation, and only for the document types that its reservation type allows. **Convert to rental contract** and **Convert to sales order** mark the reservation *Converted*.

To cancel a record, select it, and then select **Cancel**. Its status changes to *Canceled*.

## Reservations, quotations, and contracts

A reservation request or reservation links to the quotation or contract that you created it from, and it follows that document through its lifecycle:

- **Created from a quotation** – the reservation request stays *Active* and links to the quotation.
- **Reserved fleet item added to a contract** – when the reservation's validation rules pass, the reservation links to the contract and is marked *Converted*.
- **Quotation converted to a contract** – the linked reservations move to the new contract and are marked *Converted*.
- **Quotation canceled or marked lost** – the linked active reservations are canceled, depending on **Cancel reservation behind rental quotation** on the **Rental parameters** page: *Never*, *Prompt*, or *Always*.
- **Reservation reaches its expiry date** – the **Reservation expiry** periodic job marks the record *Expired*. The expiry date is the start date plus the configured **Expiry time**, and you can scope a run so that it covers only part of the fleet. Learn more in [Run rental management periodic jobs](run-rental-periodic-jobs.md).
- **Reservation canceled manually** – it's marked *Canceled*.

Because a reservation request is soft, it's converting or canceling the source document that drives the request's status—not whether an individual earmarked fleet item was rented or sold in the meantime.

## Configure reservation controls

Reservation controls define the rules and limits for how reservations work in your system. Separate controls exist for reservation requests and reservations.

### Reservation request controls

To configure reservation request controls, go to **Rental management (Preview)** > **Setup** > **Reservations** > **Reservation requests**.

Key settings include:

- **Maximum requests per fleet item** – Limits overlapping active requests that reference the same individual fleet item. It doesn't apply to requests that specify only a model or rental class.
- **Maximum requests per model or class** – Limits how many reservation requests can exist for a specific model or rental class.
- **Expiry time** – The number of days that the system adds to the start date to calculate the expiry date. The system recalculates the expiry date whenever the start date or the reservation type changes.
- **Fleet types** – On the **Fleet types** tab, the fleet types that reservation requests of this type can include.
- **Model allowed** and **Class allowed** – Control whether you can select a model and a rental class on the reservation request.

### Reservation (fleet item-level) controls

To configure reservation controls, go to **Rental management (Preview)** > **Setup** > **Reservations** > **Reservations**.

Key settings include:

- **Time window** – Maximum number of days from today to the start date of a reservation. A value of *0* allows any start date.
- **Fleet types** – On the **Fleet types** tab, the fleet types that you can reserve with this reservation type. You can't reserve a fleet item whose fleet type isn't listed.
- **Opportunity required** – Whether you must enter an **Opportunity ID** when you create a reservation of this type. Reservation requests don't require one.
- **Maximum length** – The longest reservation allowed, in days.
- **Expiry time** – The number of days after the start date when a reservation expires. The system recalculates the expiry date whenever the start date or the reservation type changes.
- **Open end date** – Whether reservations of this type have no end date.
- **Validation rules** – **Customer validation** and **User validation** decide whether a conflict exists. With **Customer validation** turned on, a conflict is raised when the reservation belongs to a different customer than the document being created. With **User validation** turned on, a conflict is raised when the responsible worker on the reservation isn't the responsible worker on the document, such as the **Sales taker** on a rental quotation or contract.
- **Stop rules** – **Stop rental quotation**, **Stop rental contract**, **Stop sales quotation**, and **Stop sales order** decide what a conflict blocks. A stop rule prevents a coordinator from putting an already reserved fleet item on that document type. Stop rules take effect only after a validation rule finds a conflict. If both **Customer validation** and **User validation** are turned off, no stop rule ever fires, and the reservation is a visible hold that blocks nothing.
- **Convert to rental quotation**, **Convert to rental contract**, **Convert to sales quotation**, and **Convert to sales order** – Control which document types you can convert the reservation into. Each command creates the document from the reservation for the fleet items that you mark with the **Convert** check box, and each command is available only on a reservation, never on a reservation request. **Convert to rental contract** and **Convert to sales order** require a customer account on the reservation; the two quotation commands accept either a customer account or a prospect.
- **Copy start date** and **Copy end date** – Whether the start and end dates from the reservation carry over to the new document.

## Related information

- [Rental management overview](rental-management-overview.md)
- [Check fleet item availability and select fleet items](check-equipment-availability.md)
- [Create rental quotations and contracts by using the rental cart](create-rental-quotations-contracts.md)
- [Ship and receive fleet items using fleet item movements](ship-receive-rental-equipment.md)
- [Run rental management periodic jobs](run-rental-periodic-jobs.md)
