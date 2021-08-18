---
# required metadata

title: Managing location owners
description: Understand location owners in the global address book, and how to change the owner when needed.
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

# Managing location owners

[!include [banner](../includes/banner.md)]

Each address in the global address book has a location owner, which determines whether the address is editable on the party record. If the party is the owner of the address, the address can be edited when accessed using the party in either the global address book or from the associated master record form (such as customer, vendor, or worker). If the party is not the owner of the address, the record cannot be edited from those forms for that party record.

## Assigning location ownership

The location owner is determined when a new address is created. When the address is created, the party for which the address is created is assigned as the location owner. 

If locations are created through data entities, the location owner property (**IsLocationOwner**) should be set to **Yes** for the party for the intended owner of the location. If this is not set to Yes for the owner of the location, the address will not be editable in the application.

## Changing location owners

If the location owner is not set correctly the address will not be editable using the associated party. In this situation, the location owner can be updated. This can be done by either changing or confirming the location owner.

> [!NOTE]
> The **Specify location owner** feature must be enabled in **Feature management** and users must be assigned to a role containing the **Set location owner** privilege to have access to actions that enable change in location ownership.

### Change location owner

You can update the location owner for a single address record from the address record in the global address book.

1. Navigate to the global address book.
2. Open a party record from the address book list.
3. In the **Addresses** fast tab on the party record, select the address for which you want to change the owner. 
4. Select the **Edit** action on the action ribbon of the **Addresses** fast tab.
5. On the **Edit address** page, select the **Change location owner** action.

Optionally, you can use the action on the **Manage addresses** page for the address.

1. Navigate to the global address book.
2. Open a party record from the address book list.
3. In the **Addresses** fast tab on the party record, select teh address for which you want to change the owner.
4. Select the **More options > Advanced** action on the action ribbon of the **Addresses** fast tab.
5. On the action ribbon of the **Manage addresses** page, select the **Change location owner** action.

The action assigns location ownership for the address to the current party.

> [!NOTE]
> The **Change location owner** action is available only if the party is not the owner of the selected location.

### Confirm location owner
You can confirm location owners for one or more locations on the **Confirm location owners** page. This page contains a lost of locations that are associated to a single party for which the associated party is not the location owner.

1. Navigate to the **Confirm location owners** page (Global Address Book > Locations > Confirm location owners).
2. Select the location for which you want to confirm the location owner.
3. On the action ribbon of the page, select the **Confirm owner** action.

This action sets the location owner for the location to the party displayed in the **Proposed owning party name** field of the list.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
