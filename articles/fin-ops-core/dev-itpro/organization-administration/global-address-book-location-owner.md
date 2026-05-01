---
title: Global address book and location owners
description: Learn about location owners and explains how to change the owner in the global address book, including an overview on assigning location ownership.
author: jaredha
ms.author: anisagrawal
ms.topic: article
ms.date: 03/17/2026
ms.reviewer: twheeloc
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2021-08-16
ms.search.form: DirPartyTable, DirPartyTableRoles
ms.dyn365.ops.version: AX 7.0.0
---

# Global address book and location owners

[!include [banner](../../../finance/includes/banner.md)]

Each address in the global address book has a location owner. The location owner determines whether you can edit the address on the party record. If the party is the location owner of the address, you can use the party to edit the address from either the global address book or the associated master record page (such as the customer, vendor, or worker). If the party isn't the location owner of the address, you can't edit the record.

## Specify a location owner

System administrators can use the **Specify location owner** feature to specify the owner of a location (address). Typically, a party owns the locations that are associated with it. If a location doesn't have an owner, or if the owner is incorrectly set, you can't edit the address.

Previously, there wasn't a way to specify a location owner. However, the **Specify location owner** feature enables you to specify a location owner through the **Advanced** option on the party address and on a new list page. After you set the location owner, you can edit the address. By default, only system administrators have access to this feature.

## Assigning location ownership

You determine the location owner when you create an address. When you create the address, you assign the party that the address is for as the location owner.

If you create locations through data entities, set the location owner property (**IsLocationOwner**) to **Yes** for the party that is the intended owner of the location. Otherwise, you can't edit the address in the application.

## Updating location owners

If the location owner isn't correct, you can't use the associated party to edit the address. In this case, update the location owner by either changing or confirming the location owner.

> [!NOTE]
> In Feature management, select **Check for updates** to update the **Enabled by default** status for the **Specify location owner** feature.

### Change the location owner

You can update the location owner for a single address record in the global address book.

1. Go to **Global address book**.
1. Open a party record from the address book list.
1. On the **Addresses** FastTab, select the address to change the location owner for.
1. Select **Edit**.
1. On **Edit address**, select the **Change location owner** action.

Alternatively, you can update the location owner on **Manage addresses**.

1. Go to **Global address book**.
1. Open a party record from the address book list.
1. On the **Addresses** FastTab, select the address to change the location owner for.
1. Select **More options** \> **Advanced**.
1. On **Manage addresses**, select **Change location owner**.

In both cases, you assign location ownership of the address to the current party.

> [!NOTE]
> The **Change location owner** option is available only if the current party isn't already the owner of the selected location.

### Confirm the location owner

On **Confirm location owners**, you can confirm location owners for one or more locations. This page contains a list of locations that are associated with a single party where the associated party isn't the location owner.

1. Go to **Global address book** > **Locations** > **Confirm location owners**.
1. Select the location to confirm the owner for.
1. On the Action Pane, select **Confirm owner**.

The location owner for the selected location is set to the party that appears in the **Proposed owning party name** field.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
