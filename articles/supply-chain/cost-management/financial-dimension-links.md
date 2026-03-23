---
title: Configure and manage financial dimension links to sites
description: Learn how to link a financial dimension to the site inventory dimension so that profit and loss figures can be calculated per site in Dynamics 365 Supply Chain Management.
author: AndersEvenGirke
ms.author: aevengir
ms.reviewer: kamaybac
ms.search.form: InventSiteDimensionLink
ms.topic: how-to
ms.date: 03/23/2026
ms.custom:
  - bap-template
---

# Configure and manage financial dimension links to sites

[!include [banner](../includes/banner.md)]

To enable the system to calculate profit and loss figures for each site for your legal entity, link a financial dimension to the site inventory dimension and assign a financial dimension value to each site.

## Set up a financial dimension link to a site

Setting up a financial dimension link to a site has the following effects:

- A financial dimension is associated with the site inventory dimension.
- A financial dimension value is associated with each site.

To set up a financial dimension link to a site, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Posting** \> **Dimension link**.
1. On the Action Pane, select **Edit**.
1. In the **Select the dimension to be linked to the storage dimension, Site** field, select the financial dimension to link to the site inventory dimension.
1. On the Action Pane, select **Sites** to open the **Sites** page.
1. On the list pane, select the site you want to link the financial dimension to.
1. Expand the **Financial dimensions** FastTab. The financial dimension that you selected in the previous page is shown here under the **Default financial dimensions** heading.
1. From the drop-down list under the **Default financial dimensions** heading, select the financial dimension value that you want to associate with the selected site.
1. Repeat steps 5 to 7 for each site.
1. When you're done, select **Save**.

## Activate a financial dimension link

Activating a financial dimension link has the following effects:

- When you create new transactions that use both inventory dimensions and financial dimensions, the system uses the dimension value that you specify for the site as the dimension value for the linked financial dimension.
- You can post transactions that use both inventory dimensions and financial dimensions, even if the dimension value for the linked financial dimension doesn't match the value that you specified for the site.
- You can change the dimension value for the linked financial dimension on open transactions that use both inventory dimensions and financial dimensions.

> [!NOTE]
> You must assign a financial dimension value to each site before you can complete this procedure.

To activate a financial dimension link, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Posting** \> **Dimension link**.
1. On the Action Pane, select **Activate link**.
1. The **Linked dimension update** dialog opens. Select **OK** to activate the link.
1. The **Current status** field updates to show that the *Dimension link is active* and the **Select the dimension to be linked to the storage dimension, Site** field becomes inactive.

## Lock a financial dimension link

Locking a financial dimension link has the following effects:

- New inventory transactions that use both inventory dimensions and financial dimensions get a financial dimension value based on the value specified for the site.
- You can post transactions that use both inventory dimensions and financial dimensions only when the dimension value of the linked financial dimension matches the value specified for the site.
- You can't change the dimension value of the linked financial dimension on transactions that use both inventory dimensions and financial dimensions.
- You can't modify the financial dimension value that's associated with a site.

You must set up a financial dimension link before you can lock it.

To lock a financial dimension link, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Posting** \> **Dimension link**.
1. On the Action Pane, select **Lock link**.
1. The **Linked dimension update** dialog opens. Select **OK** to lock the link. The system updates all open transactions accordingly.
1. The **Current status** field updates to show that the *Dimension link is locked*.

## Unlock a financial dimension link

You can unlock locked financial dimension links. Unlocking a link allows you to complete these tasks:

- Post transactions that use both inventory dimensions and financial dimensions, even if the dimension value of the linked financial dimension doesn't match the value that is specified for the site.
- Modify the dimension value of the linked financial dimension on open transactions that use both financial dimensions and inventory dimensions.
- Modify the financial dimension values on the **Sites** page.

1. Go to **Inventory management** \> **Setup** \> **Posting** \> **Dimension link**.
1. On the Action Pane, select **Unlock link**.
1. The **Current status** field updates to show that the *Dimension link is active*.

## Deactivate a financial dimension link

When you deactivate a financial dimension link, the following changes occur:

- The link between the site inventory dimension and the financial dimension is removed.
- The linked financial dimension isn't assigned the dimension value specified for each site.

- You can choose a different financial dimension to link to the site inventory dimension.

To deactivate a financial dimension link, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Posting** \> **Dimension link**.
1. On the Action Pane, select **Deactivate link**.
1. The **Current status** field updates to show that the *Dimension link is inactive*.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
