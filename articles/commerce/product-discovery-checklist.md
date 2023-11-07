---
title: Product discovery checklist
description: This article provides a product discovery checklist to follow to ensure that products are discoverable in Microsoft Dynamics 365 Commerce channels for various scenarios.
author: rickwyang
ms.date: 11/07/2023
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
- Ensure that you run the distribution schedule **1040 (Products)** and **1150 (Catalog)** jobs. In case any key table is deleted from the jobs, to add the table(s) back to the job(s), run the **Initialize Commerce scheduler** (**Retail and Commerce \> Headquarters setup \> Commerce scheduler \> Initialize Commerce scheduler**) in Commerce headquarters.

## Additional configurations to check if you are using cloud-powered search

- When [Cloud-powered search overview](cloud-powered-search-overview.md) is used, products are published to search indexes. Since price information is required to be accurate in the search indexes, to ensure that products can be published successfully, you must ensure that prices can be calculated.
- Ensure that the sales unit of measure is configured for the product.
- If the channel is an online store, it's mandatory to enable cloud-powered search.
- If the channel is an online store, ensure that the e-commerce site language is included in the channel's languages.
- If the channel is associated with a new site or new warehouse, make sure the distribution schedule jobs are run, 1040 (Products) for site data, 1120 (Mode of delivery) or 1070 (Channel configuration) for warehouse data.
- Ensure that the currency exchange rate works for the channel currency and the accounting currency.

If the channel and accounting currencies are different, follow these steps.

1. Configure the channel currency on the channel setting (**Retail and Commerce \> Channels \> Stores \> All stores** for a brick-and-mortar store, or **Retail and Commerce \> Channels \> Online stores** for an online store).
1. Configure the accounting currency at **General ledger \> Ledger Setup \> Ledger**.
1. Configure the currency exchange rate at **General ledger \> Currencies \> Currency exchange rates**.
1. Assign the exchange rate as the **Exchange rate type** at **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**.
  
## Product discovery under the channel's navigation hierarchy

- Ensure that the navigation hierarchy is associated with the channel. For more information, see [Configure a channel to use a channel navigation hierarchy](configure-channel-hierarchy.md).
- Ensure that the product is added to a category of the channel's navigation hierarchy.

## Workarounds on the Store Commerce app when there is a product discovery issue

If you encounter a product discovery issue on Store Commerce app, there is a quick workaround to sell the product without engaging Microsoft's support.

1. When you see a message like "We didn't find anything to display here" on the search screen, it means the product can't be discovered in the channel. Select **Search other stores** below the message.
1. Select **Search all stores and catalogs**. The selected store then changes to **All stores and catalogs**.
1. Select the **All store products** tile. A real-time service call is then performed to search the product.
1. If you still can't find the product, it probably isn't correctly released to the legal entity. Check the product's configuration.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
