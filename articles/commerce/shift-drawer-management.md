---
title: Shift and cash drawer management
description: This article explains how to set up and use shifts in Commerce point of sale (POS).
author: josaw1
ms.date: 02/03/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: josaw
ms.search.region: global
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update
ms.custom: 105011
ms.assetid: 49a0fcc9-d4db-45ad-8c4b-213ccaced82b
ms.search.industry: Retail
ms.search.form: RetailHardwareProfile, RetailTerminalTable
---

# Shift and cash drawer management

[!include [banner](includes/banner.md)]

This article explains how to set up and use shifts in Commerce point of sale (POS).

In Dynamics 365 Commerce, the term *shift* describes the collection of POS transactional data and activities between two points in time. For each shift, the amount of money that is expected is compared against the amount that was counted and declared.

Typically, shifts are opened at the start of the business day. At that point, a user declares the starting amount that the cash drawer contains. Sales transactions are then performed throughout the day. Finally, at the end of the day, the drawer is counted, and the closing amounts are declared. The shift is closed, and a Z report is generated. The Z report indicates whether there is an overage or shortage.

## Typical shift scenarios

Commerce provides several configuration options and POS operations to support a wide range of end-of-day business processes for the POS. This section describes some typical shift scenarios.

### Fixed till

Traditionally, this scenario has been used most often. It's still extensively used. In a "fixed till" shift, the shift and till are associated with a specific register. They aren't moved from one register to another. A "fixed till" shift can be used by a single user or shared among multiple users. "Fixed till" shifts don't require any special configuration.

### Floating till

In a "floating till" shift, the shift and cash drawer can be moved from one register to another. Although a register can have only one active shift per cash drawer, shifts can be suspended and then resumed later or on a different register.

For example, a store has two registers. Each register is opened at the start of the day when the cashier opens a new shift and provides the starting amount. When one cashier is ready to take a break, that cashier suspends their shift and removes the till from the cash drawer. That register then becomes available to other cashiers. Another cashier can sign in to and open their own shift on the register. After the first cashier's break has ended, that cashier can resume their shift when one of the other registers becomes available. "Floating till" shifts don't require any special configuration or permission.

### Single user

Many retailers prefer to allow only one user per shift, to help guarantee the highest level of accountability for the cash in the cash drawer. If only one user is allowed to use the till that is associated with a shift, that user can be held solely responsible for any discrepancies. If more than one user uses a shift, it's difficult to determine who made an error, or who might be trying to steal from the till.

### Multiple users

Some retailers are willing to sacrifice the level of accountability that single-user shifts provide and to allow more than one user per shift. This approach is typical when there are more users than available registers, and the need for flexibility and speed outweighs the potential for loss. It's also typical when store managers don't have their own shifts but can, as required, use the shifts of any of their cashiers. To sign in to and use a shift that was opened by another user, a user must have the **Allow multiple shift logon** POS permission.

### Shared shift

A "shared shift" configuration lets retailers have a single shift across multiple registers, cash drawers, and users. A shared shift has a single starting amount and a single closing amount that are summarized across all cash drawers. Shared shifts are most typical when mobile devices are used. In this scenario, a separate cash drawer isn't reserved for each register. Instead, all registers can share one cash drawer.

For shared shifts to be used in a store, the cash drawer must be configured as a "shared shift drawer" at **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Hardware profiles \> Drawer**. Additionally, users must have one or both of the shared shift permissions (Allow manage shared shift and Allow use shared shift).

> [!NOTE]
> Only one shared shift can be open at a time in each store. Shared shifts and stand-alone shifts can be used in the same store.

## Shift and drawer operations

Various operations can be performed to change the state of a shift, or to increase or decrease the amount of money in the cash drawer. This section describes these shift operations for Store Commerce.

### Open shift

The POS requires that users have an active, open shift in order to perform any operations that will produce a financial transaction, such as a sale, return, or customer order.

When a user signs in to the POS, the system first verifies whether an active shift is available for that user on the current register. If an active shift isn't available, the user can open a new shift, resume an existing shift, or sign in in "non-drawer" mode, depending on the system configuration and the user's permissions.

### Declare start amount

This operation is often the first operation that is performed for a newly opened shift. For this operation, users specify the starting cash amount in the cash drawer for the shift. This operation is important because the overage/shortage calculation that occurs when a shift is closed considers the start amount.

### Float entry

*Float entries* are non-sales transactions that are performed in an active shift to increase the amount of cash in the cash drawer. A typical example of a float entry is a transaction to add additional change to the drawer when it's running low.

### Tender removal

*Tender removals* are non-sales transactions that are performed in an active shift to reduce the amount of cash in the cash drawer. This operation is most often used in conjunction with a Float entry operation on a different shift. For example, because register 1 is running low on change, the user on register 2 does a tender removal to reduce the amount in their cash drawer. The user on register 1 then does a float entry to increase the amount in their cash drawer.

### Suspend shift

Users can suspend their active shift to free up the current register for another user, or to move their shift to a different register (in this case, the shift is often referred to as a "floating till" shift).

Suspension of a shift prevents any new transactions or changes to the shift until it's resumed.

### Resume shift

This operation lets users resume a previously suspended shift on any register that doesn't already have an active shift.

### Tender declaration

This operation is performed to specify the total amount of money that is currently in the cash drawer. Users most often perform this operation before they close a shift. The specified amount is compared against the expected shift amount to calculate the overage/shortage amount.

### Safe drop

Safe drops can be done on an active shift at any time. This operation removes money from the cash drawer so that it can be transferred to a more secure location, such as a safe in the back room. The total amount that is recorded for safe drops is included in shift totals, but it doesn't have to be counted as part of the tender declaration.

### Bank drop

Like safe drops, bank drops are done on active shifts. This operation removes money from the shift to prepare for the bank deposit.

### Blind close shift

*Blind-closed shifts* are no longer active but haven't been fully closed. Unlike suspended shifts, blind-closed shifts can't be resumed. However, operations such as Declare start amount and Tender declaration can be performed on them later or from a different register.

Blind-closed shifts are often used to free up a register for a new user or shift without first having to fully count, reconcile, and close the shift.

### Close shift

This operation calculates shift totals and overage/shortage amounts, and then finalizes an active or blind-closed shift. Depending on the user's permissions, a Z report is also printed for the shift. Closed shifts can't be resumed or modified.

### Print X

This operation generates and prints an X report for the current active shift.

### Reprint Z

This operation reprints the last Z report that the system generated when a shift was closed.

### Manage shifts

This operation lets users view all active, suspended, and blind-closed shifts for the store. Depending on their permissions, users can perform their final closing procedures, such as Tender declaration and Close shift operations for blind-closed shifts. This operation also lets users view and delete invalid shifts, in the rare event that shifts are left in a bad state after a switch between offline and online modes. These invalid shifts don't contain any financial information or transactional data that is required for reconciliation.

## Shift and drawer permissions

The following POS permissions affect what a user can and can't do in various scenarios:

- **Allow blind close**
- **Allow X-report printing**
- **Allow Z-report printing**
- **Allow tender declaration**
- **Allow floating declaration**
- **Open drawer without sale**
- **Allow multiple shift logon** – This permission allows the user to sign in to and use a shift that a different user opened. Users who don't have this permission can sign in to and use only shifts that they have opened.
- **Allow manage shared shift** – Users must have this permission to open or close a shared shift.
- **Allow use shared shift** – Users must have this permission to sign in to and use a shared shift.

## Back-office end-of-day considerations

The way that shifts and cash drawer reconciliation are used in the POS differs from the way that transaction data is summarized during statement calculation. It's important that you understand this difference. Depending on your configuration and your business processes, the shift data in the POS (the Z report) and a calculated statement in the back office can give you different results. This difference doesn't necessarily mean that either the shift data or the calculated statement is incorrect, or that there is a problem with the data. It just means that the parameters that are provided might be including additional transaction or fewer transactions, or that the transactions have been summarized differently.

Although every retailer has different business requirements, we recommend that you set up your system in the following way to avoid situations where differences of this type occur:

Go to **Retail and Commerce \> Channels \> Stores \> All stores \> Statement/closing**, and for each store, set both the **Statement method** field and the **Closing method** field to **Shift**.

This setup helps guarantee that back-office statements include the same transactions as shifts in the POS, and that the data is summarized by that shift.

For more information about statement and closing methods, see [Store configurations for Retail statement](/dynamics365/unified-operations/retail/tasks/store-configurations-retail-statements).


[!INCLUDE[footer-include](../includes/footer-banner.md)]
