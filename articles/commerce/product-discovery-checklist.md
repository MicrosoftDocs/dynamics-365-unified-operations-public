---
title: Product discovery checklist
description: This article provides a product discovery checklist to follow to ensure that products are discoverable in Microsoft Dynamics 365 Commerce channels for various scenarios.
author: rickwyang
ms.date: 11/29/2023
ms.topic: article
audience: Application User
ms.reviewer: josaw
ms.search.region: Global
ms.author: wenxyang
ms.search.validFrom: 2023-11-04

---

# Product discovery checklist

[!include [banner](includes/banner.md)]

This article provides a product discovery checklist to follow to ensure that products are discoverable in Microsoft Dynamics 365 Commerce channels for various scenarios.

## Basic configurations

- Ensure that the product is released to the legal entity of the channel's warehouse. For more information, see [Release an engineering product to a local company](/dynamics365/supply-chain/engineering-change-management/engineering-scenarios#release).
- Ensure that the product is assorted to the channel. You can validate the product is assorted to the channel using the **Validate a channel's assortment** section. For more information, see [Set up assortments](set-up-assortments.md).
- Ensure that you run the distribution schedule **1040 (Products)** and **1150 (Catalog)** jobs. If any key tables are deleted from the jobs, to add the table(s) back to the jobs, run the **Initialize Commerce scheduler** (**Retail and Commerce \> Headquarters setup \> Commerce scheduler \> Initialize Commerce scheduler**) in Commerce headquarters.

## Configurations for cloud-powered search

- When [Cloud-powered search overview](cloud-powered-search-overview.md) is used, products are published to search indexes. Since price information is required to be accurate in the search indexes, to publish products successfully, you must ensure that prices can be calculated.
- Ensure that the sales unit of measure is configured for the product.
- If the channel is an online store, cloud-powered search must be enabled.
- If the channel is an online store, ensure that the e-commerce site language is included in the channel's languages.
- If the channel is associated with a new site or new warehouse, ensure that you run the following distribution schedule jobs: **1040 (Products)** for site data, and either **1120 (Mode of delivery)** or **1070 (Channel configuration)** for warehouse data.
- Ensure that the currency exchange rate functions for the channel currency and the accounting currency.

    If the channel and accounting currencies are different, follow these steps.

    1. Configure the channel currency at **Retail and Commerce \> Channels \> Stores \> All stores** for a brick-and-mortar store, or at **Retail and Commerce \> Channels \> Online stores** for an online store.
    1. Configure the accounting currency at **General ledger \> Ledger Setup \> Ledger**.
    1. Configure the currency exchange rate at **General ledger \> Currencies \> Currency exchange rates**.
    1. Assign the exchange rate as **Exchange rate type** at **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**.

## Configurations for product discovery under a channel's navigation hierarchy

- Ensure that the navigation hierarchy is associated with the channel. For more information, see [Configure a channel to use a channel navigation hierarchy](configure-channel-hierarchy.md).
- Ensure that the product is added to a category of the channel's navigation hierarchy.

## Configurations for B2B sites

- Ensure that **Enable use of multiple catalogs on retails channels** feature is enabled.
- Ensure that you have created a customer hierarchy and added both customers and catalogs in the customer hierarchy, so after login the customer can see products under the catalogs. See [Manage B2B business partners using customer hierarchies](./b2b/partners-customer-hierarchies.md) for more details.

## Workaround for product discovery issues on the Store Commerce app or POS

If you encounter a product discovery issue on the Store Commerce app or POS, follow these steps to sell the product without engaging Microsoft support.

1. When you see a message like "We didn't find anything to display here" on the search screen, it means the product can't be discovered in the channel. Select **Search other stores** below the message.
1. Select **Search all stores and catalogs**. The selected store then changes to **All stores and catalogs**.
1. Select the **All store products** tile. A real-time service call is then performed to search for the product.
1. If you still can't find the product, it probably isn't correctly released to the legal entity. Check that the product is configured correctly.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
