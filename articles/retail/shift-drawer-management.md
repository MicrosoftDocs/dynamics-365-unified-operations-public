---
# required metadata

title: Shift and cash drawer management
description: This article explains how to set up and use the two types of retail point of sale (POS) shifts -  shared and stand-alone. Shared shifts can be used by multiple users in multiple places, whereas stand-alone shifts can be used by only one worker at a time.
author: jeffblucher
manager: AnnBe
ms.date: 05/10/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form: RetailHardwareProfile, RetailTerminalTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 105011
ms.assetid: 49a0fcc9-d4db-45ad-8c4b-213ccaced82b
ms.search.region: global
ms.search.industry: Retail
ms.author: rubendel
ms.search.validFrom: 2016-02-28

ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update


---

# Shift and cash drawer management

[!include [banner](includes/banner.md)]

In Dynamics 365 for Retail a “shift” is a term used to describe a collection of POS transactional data and activities between two points in time, where the amount of money expected is compared against the amount counted and declared.

Typically, shifts are opened at the start of a business day and a user declares the starting amount contained in the cash drawer.  Sales transactions are performed throughout the day, and at the end of the day the drawer is counted and the closing amounts are declared.   The shift is closed, generating a Z report which indicates whether there is an overage or shortage. 

## Common shift scenarios
Dynamics 365 for Retail provides a number of configuration options and POS operations to support a wide variety of POS end of day business processes.  The section below describes some of the most common shift scenarios.

### Fixed till
Traditionally, this is the most common scenario and it is still used extensively today.  A “fixed till” shift simply means that the shift and till is associated with a particular register and does not move from one register to another.  A “fixed till” shift may be used by a single user or can be shared among multiple users.  “Fixed till” shifts do not require any special configuration.

### Floating till
A “floating till” refers to the ability to move a shift and cash drawer from one register to another.  While a register can only have one active shift per cash drawer, shifts can be suspended and resumed elsewhere or at a later time.
For example, a store has two registers.  Each register is opened at the start of the day when the cashier opens a new shift and provides their starting amount.  When one cashier is ready to take a break, they suspend their shift and remove the till from the cash drawer.  This frees the register up for cashiers to login and open their own new shift.  When the first cashier returns from their break, they can resume their shift once one of the other registers becomes available.  “Floating till” shifts do not require any special configuration or permission.

### Single user
Many retailers prefer to allow only one user per shift to ensure the highest level of accountability for the cash in the drawer.  If only one user is allowed to utilize the till associated with a shift, that user can solely be held responsible for any discrepancies.  If more than one user uses a shift it is difficult to determine who might have made an error or may be attempting to steal from the till.

### Multi-user
Some retailers are willing to sacrifice some of the accountability that a single user shift provides, by allowing more than one user.  This is common when there are more users than available registers and the need for flexibility and speed outweigh the potential for loss.  It is also common, when a store manager does not have their own shift, but are allowed to use any of their cashiers shifts when needed.  In order for a user to login and utilize a shift opened by another user they must have the “Allow multiple shift logon” POS permission. 

### Shared shift
A “shared shift” configuration allows retailers to have a single shift across multiple registers, cash drawers, and users.  A shared shift has a single starting amount and closing amount that is summarized across all cash drawers.  This is most common when using mobile devices.  Rather than having a cash drawer reserved for each register, they can all share one.  In order to use shared shifts within a store, the cash drawer must be configured as a “Shared shift drawer” (Retail > Channel setup > POS setup > POS profiles > Hardware profiles > Drawer) and users must have one or both of the shared shift permissions (Allow manage shared shift, Allow use shared shift).
 **Note:** Only one shared shift can be open at a time in each store. Shared shifts and stand-alone shifts can be used in the same store.

## Shift and drawer operations
Various actions can be taken to change the state of a shift or to increase or decrease the amount of money in the drawer. The section below describes these shift operations for Dynamics 365 for Retail Modern POS and Cloud POS.

### Open shift
POS requires that a user has an active, open shift to perform any operations that would result in a financial transaction such as a sale, return, or customer order.
When logging into the POS, the system first checks to see if the user has an active shift available on the current register. If not, the user can then choose to open a new shift, resume an existing shift, or continue to login in “non-drawer” mode, depending on the system configuration and their permissions.

### Declare start amount
This operation is often the first action that is taken a newly opened shift. Users specify the starting cash amount in the drawer for the shift. This is important because the over/short calculation that occurs when closing a shift accounts for this amount.

### Float entry
Float entries are non-sales transactions that are performed in an active shift and they increase the amount of the cash in the drawer. A common example of a float entry would be to add additional change to the drawer when it is running low.

### Tender removal
Tender removals are non-sales transactions that are performed in an active shift to reduce the amount of the cash in the drawer. This is most commonly used in conjunction with a float entry on a different shift. For example, Register 1 is running low on change, so the user on Register 2 performs a tender removal to reduce the drawer amount. The user on Register 1 would then perform a float entry to increase their amount.

### Suspend shift
Users can suspend their active shift to free up the current register for another user, or to move their shift to a different register (this is often referred to as a “floating till”).

Suspending the shift prevents any new transactions or changes to the shift until it resumed.

### Resume shift
This operation allows a user to resume a previously suspended shift on a register that does not already have an active shift.

### Tender declaration
The tender declaration is action the user takes to specify the amount of total money currently in the drawer, most often before closing the shift. This is the value that is compared against the expected shift to calculate the over/short amount.

### Safe drop
Safe drops can be performed at any time on an active shift. This operation removes money from the drawer, so it can be transferred to a more secure location such as a safe in the back room. The total amount recorded for safe drops is still included in the shift totals, but doesn't need to be counted as part of the tender declaration.

### Bank drop
Like safe drops, bank drops are also performed on active shifts. This operation removes money from the shift to prepare for the bank deposit.

### Blind close shift
A blind closed shift is a shift that is no longer active but has not been fully closed. Blind closed shifts can't be resumed like a suspended shift, but procedures such as declare staring amounts and tender declarations can be performed at a later time or from a different register.

Blind closed shifts are often used to free up a register for a new user or shift, without having to fully count, reconcile, and close this shift first.

### Close shift
This operation calculates shift totals, over/short amounts, and then finalizes an active or blind closed shift. Depending on the user’s permissions, a Z-report will also be printed for the shift.  Closed shifts cannot be resumed or modified.

### Print X
This operation generates and prints an X report for the current active shift

### Reprint Z
This operation will reprint the last Z report generated by the system when a shift was closed

### Manage shifts
This operation allows users to view all active, suspended, and blind closed shifts for the store. Depending on their permissions, users can perform their final closing procedures such as tender declaration and close shifts for blind closed shifts. This operation will also allow users to view and delete invalid shifts in the rare event that a shift is left in a bad state after switching between offline and online modes. These invalid shifts do not contain any financial information or transactional data needed for reconciliation.  

## Shift and drawer permissions
The following POS permissions affect what a user can and cannot do in various scenarios.
* **Allow blind close**
* **Allow X-report printing**
* **Allow Z-report printing**
* **Allow tender declaration**
* **Allow floating declaration**
* **Open drawer without sale**
* **Allow multiple shift logon**: Allows the user to login and utilize a shift opened by a different user.  Without this permission users can only login and use shifts that they have opened.
* **Allow manage shared shift**:  Users must have this permission to open or close a shared shift.
* **Allow use shared shift**:  Users must have this permission to login and use a shared shift.


## Back office “end of day” considerations
It is important to understand the difference between the usage of shifts and cash drawer reconciliation within POS and how transaction data is summarized during Statement calculation.   Depending on your configuration and your business processes, it is possible to get different results between the shift data in POS (Z-report) and a calculated statement in the back office.  This does not necessarily mean that either is incorrect, or that there is a problem with the data.  It simply means that the parameters provided could be including additional or fewer transactions, or that the transactions have been summarized differently.
While each retailer has different business requirements, it is recommended to configure your system as follows to avoid situations where there are differences:

**For each store (Retail > Channels > Retail stores > All retail stores > Statement/closing) set both the Statement method and the Closing method to “Shift”**

This setup will ensure that back office statements include the same transactions as the shift in POS and that the data is summarized by that shift.

For more information about statement and closing methods refer to : https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/tasks/store-configurations-retail-statements

