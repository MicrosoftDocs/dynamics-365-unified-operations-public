---
title: Create a default customer
description: Learn how to create a default customer to use when creating a channel in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 01/21/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2020-01-20
ms.custom: 
  - bap-template
---
# Create a default customer

[!include [banner](includes/banner.md)]

This article describes how to create a default customer to use when creating a channel in Microsoft Dynamics 365 Commerce.

When you create a channel, you need to provide a default customer. You can easily create a default customer after you create the customer group and customer address book.

## Create a customer group

If no customer groups exist yet, create one. Examples of customer groups include wholesale, retail, Internet, employees, and more.

To create a customer group, follow these steps:

1. In the navigation pane, go to **Modules > Retail and commerce > Customers > Customer groups**.
1. On the action pane, select **New**.
1. In the **Customer group** box, enter a customer group ID.
1. In the **Description** box, enter an appropriate description.
1. In the **Terms of payment** box, enter an appropriate value.
1. In the **Time between invoice due date and payment date** box, enter an appropriate value.
1. In the **Default tax group** box, enter a tax group if applicable.
1. Select the **Prices include sales tax** check box if applicable.
1. In the **Default write-off reason** box, enter an appropriate value, if applicable.

The following image shows several configured customer groups.

:::image type="content" source="media/customer-groups.png" alt-text="Screenshot of configured customer groups.":::

## Create a customer address book

You need to associate each customer with an address book. If an address book doesn't exist, create one.

To create a customer address book, follow these steps:

1. In the navigation pane, go to **Modules \> Retail and commerce \> Channel setup \> Address Books**.
1. On the action pane, select **New**.
1. In the **Name** box, enter a name.
1. In the **Description** box, enter a description.
1. On the action pane, select **Save**.

The following image shows an example address book.

:::image type="content" source="media/address-book.png" alt-text="Screenshot of an example address book.":::

## Create a default customer

To create a default customer, follow these steps:

1. In the navigation pane, go to **Modules \> Retail and commerce \> Customers \> All customers**.
1. On the action pane, select **New**.
1. In the **Type** drop-down list, select **Person**.
1. In the **Customer account** drop-down list, select or enter an account number (for example, **100001**).
1. In the **First name** drop-down list, select or enter a name (for example, **Default**).
1. In the **Middle name** drop-down list, select or enter a name (for example, **Retail**).
1. In the **Last name** drop-down list, select or enter a name (for example, **Customer**).
1. In the **Currency** drop-down list, select or enter a currency (for example, **USD**).
1. In the **Customer group** drop-down list, select the customer group you created previously.
1. In the **Address books**  drop-down list, select an existing customer address book.
1. Select **Save** to save and return to customer details screen for the new customer.

> [!NOTE]
> You don't need to add an address for a default customer.

The following image shows an example of customer creation.

:::image type="content" source="media/default-customer-creation.png" alt-text="Screenshot of default customer creation.":::

The following image shows a default customer configuration.

:::image type="content" source="media/default-customer-configuration1.png" alt-text="Screenshot of sample customer configuration.":::

Most of the default values on the customer details screen can remain, but change two values.

1. On the customer details screen, expand **Sales order defaults**.
1. In the **Site** drop-down list, select or enter a preconfigured site.
1. In the **Warehouse** drop-down list, select or enter a preconfigured warehouse.

The following image shows an example customer configuration.

:::image type="content" source="media/default-customer-configuration2.png" alt-text="Screenshot of example customer configuration.":::

## Additional resources

[Channels overview](channels-overview.md)

[Channel setup prerequisites](channels-prerequisites.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
