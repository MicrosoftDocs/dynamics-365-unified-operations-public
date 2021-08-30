---
# required metadata

title: Global address book and location owners
description: This topic describes location owners and explains how to change the owner in the global address book.
author: jaredha
ms.date: 08/16/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: DirPartyTable, DirPartyTableRoles
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: 
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jaredha
ms.search.validFrom: 2021-08-16
ms.dyn365.ops.version: AX 7.0.0

---

# Global address book and location owners

[!include [banner](../includes/banner.md)]

Each address in the global address book has a location owner. The location owner determines whether the address can be edited on the party record. If the party is the location owner of the address, the party can be used to edit the address from either the global address book or the associated master record page (such as the customer, vendor, or worker). If the party isn't the location owner of the address, the record can't be edited.

## Assigning location ownership

The location owner is determined when an address is created. When the address is created, the party that the address is created for is assigned as the location owner.

If locations are created through data entities, the location owner property (**IsLocationOwner**) should be set to **Yes** for the party that is the intended owner of the location. Otherwise, the address won't be editable in the application.

## Updating location owners

If the location owner isn't correct, the associated party can't be used to edit the address. In this case, you can update the location owner by either changing or confirming the location owner.

> [!NOTE]
> Before the location owner can be updated, the **Specify location owner** feature must be enabled in Feature management, and users must be assigned to a role that has the **Set location owner** privilege.

### Change the location owner

You can update the location owner for a single address record in the global address book.

1. Go to **Global address book**.
2. Open a party record from the address book list.
3. On the **Addresses** FastTab, select the address to change the location owner for.
4. Select **Edit**.
5. On the **Edit address** page, select the **Change location owner** action.

Alternatively, you can update the location owner on the **Manage addresses** page.

1. Go to **Global address book**.
2. Open a party record from the address book list.
3. On the **Addresses** FastTab, select the address to change the location owner for.
4. Select **More options** \> **Advanced**.
5. On the **Manage addresses** page, select **Change location owner**.

In both cases, location ownership of the address is assigned to the current party.

> [!NOTE]
> The **Change location owner** option is available only if the current party isn't already the owner of the selected location.

### Confirm the location owner

On the **Confirm location owners** page, you can confirm location owners for one or more locations. This page contains a list of locations that are associated with a single party where the associated party isn't the location owner.

1. Go to **Global address book** \> **Locations** \> **Confirm location owners**.
2. Select the location to confirm the owner for.
3. On the Action Pane, select **Confirm owner**.

The location owner for the selected location is set to the party that is shown in the **Proposed owning party name** field.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
