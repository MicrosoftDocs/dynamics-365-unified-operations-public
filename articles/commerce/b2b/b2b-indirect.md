---
title: B2B indirect workflows
description: Learn about the key features and benefits of native business-to-business (B2B) indirect workflows in Microsoft Dynamics 365 Commerce.
author: ashishmsft
ms.date: 06/13/2025
ms.topic: overview
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2021-01-31
ms.search.form: RetailOperations
ms.custom: 
  - bap-template
---

# B2B indirect workflows

[!include [banner](../../includes/banner.md)]

This article provides an overview of the key features and benefits of native business-to-business (B2B) indirect workflows in Microsoft Dynamics 365 Commerce. B2B indirect is also known as business-to-business-to-business (B2B2B). 

The Dynamics 365 Commerce B2B indirect feature can help your business grow by powering dynamic, multitiered supply chains that enable products to flow seamlessly from manufacturers through trusted distributors to business customers. This strategy amplifies market reach, maximizes distribution channels, and accelerates sales by connecting consumer packaged goods (CPG) brands with retailers and other businesses via a robust network of intermediaries. The B2B indirect feature can help improve your B2B distribution process, because each business intermediary becomes a catalyst for growth by ensuring that your products reach the right customers.

## Dynamics 365 Commerce support for B2B indirect workflows

The Dynamics 365 Commerce cloud-based platform provides a comprehensive set of capabilities to enable B2B commerce scenarios. The platform supports both direct and indirect B2B workflows through a headless, composable architecture that enables merchants to manage multiple types of business relationships and transactions.

B2B indirect workflow capabilities enable you to:

- Create and manage multiple B2B seller and B2B buyer accounts, each of which has its own pricing, catalog, and inventory management.
- Configure and apply complex pricing and discount rules based on criteria such as account type, order quantity, and product category.
- Create and manage multiple catalogs and assortments for different B2B seller and B2B buyer accounts. You can choose to inherit, override, or extend product information from the primary catalog.
- Allow B2B buyers to purchase either from an authorized and approved list of B2B sellers or directly from the manufacturer.
- Allow customer service representatives (also known as field sellers) from the manufacturer's organization to order from specific B2B sellers (distributors/wholesalers) on behalf of B2B buyers.
- Use a rich and responsive user interface (UI) for B2B seller and B2B buyer portals. Features include product search, browsing, filtering, sorting, comparison, reviews, ratings, wish lists, cart, checkout, and order history.
- Integrate with various external systems and services, such as enterprise resource planning (ERP), customer relationship management (CRM), payment, tax, and shipping, through the platform's application programming interfaces (APIs) and connectors.

## Benefits of choosing Dynamics 365 Commerce for B2B indirect workflows

Dynamics 365 Commerce is designed to support high-volume merchants. It provides a suite of advanced features to cater to the specific requirements of B2B transactions.

The benefits of choosing Dynamics 365 Commerce for B2B indirect workflows include:

- B2B indirect workflows build on the existing B2B workflows and use the same platform features and data model. Therefore, users get a consistent and smooth experience.
- B2B indirect workflows are available in a headless mode. Therefore, merchants can use the platform's APIs and software development kits (SDKs) to build custom extensions and integrations that fit their existing business processes.
- B2B indirect workflows are scalable, secure, and reliable because they are built on the Microsoft Azure cloud platform. This platform offers high availability, performance, and compliance.
- B2B indirect workflows are flexible and customizable. Merchants can configure many parts of the platform, such as business rules, workflows, and the UI, to fit their specific needs.

## B2B seller prospect sign-up and approval process

The following steps provide an overview of the process for becoming a B2B seller on the platform:

1. **Submit a B2B seller prospect application.** A prospective B2B seller submits an application to express their interest in becoming a seller on the platform. The application includes relevant business information and contact details.
1. **Sync the prospect application.** The submitted application is synced to Commerce headquarters and made available for review. <!--Run or schedule a P-001 sync job from the Distribution Schedule and run **Sync Customer requests**.-->
1. **Review the prospect application.** The platform team evaluates the prospect's suitability, based on predefined criteria. Criteria might include business size, industry, product offerings, and compliance with platform policies. The review process aims to identify genuine businesses and filter out potential fraud or unwanted applicants.
1. **Approve or reject the B2B seller prospect.** Based on the platform team's review, the prospect application is either approved or rejected. Approved prospects receive confirmation and instructions for the next steps. Rejected applicants are informed of the decision and the reasons behind it.

After a B2B seller is approved, the system completes the following setup in headquarters:

1. **Create a copy of an existing online B2B channel.** The platform creates a new B2B channel specifically for the approved seller. This channel has a unique site and warehouse, so that the seller can manage their inventory separately.
1. **Create an employee record.** An employee record is automatically set up for the B2B seller. This record enables the seller to perform inventory management, order management, and other operational tasks.
1. **Map the customer hierarchy**: The B2B seller's channel is mapped to a specific customer hierarchy. This hierarchy defines the relationships between the seller and their customers, such as pricing, discounts, and payment terms.
1. **Map the manufacturer channel**: The B2B seller's channel is mapped to the manufacturer channel. This mapping ensures that the seller can purchase products directly from the manufacturer to maintain supply chain efficiency and quality control.

Through these steps, the B2B seller can become a part of the platform and start to sell to their retail outlets.

## B2B indirect feature capabilities

As part of the B2B indirect feature, you can take advantage of the following capabilities:

- Onboard a B2B seller as a new B2B prospect type for distributors or wholesalers.
- Convert existing B2B buyers to B2B sellers and buyers.
- Map B2B buyers to selected B2B sellers, and decide whether they can also buy directly from the manufacturer.
- Create B2B catalog-aware Commerce orders in headquarters and call center, and enable selection of the fulfilling channel (B2B seller or distributor) on the order header.
- Map individual B2B buyer organizations to B2B sellers and/or manufacturers, so that you have control over who can buy from whom. You can configure this functionality directly from the B2B buyer's customer hierarchy, by mapping the associated B2B channels that the B2B buyer can buy from.
- Allow B2B buyers to choose to purchase from multiple B2B sellers and/or the manufacturer.
- Allow B2B buyers to buy directly from a single B2B seller or manufacturer at any time. However, also allow multiple carts with individual B2B sellers or the manufacturer to be active simultaneously.
- Enable customers to bulk-add items from multiple catalogs by using catalog-aware order templates.
- Allow customers to quickly rebuy catalog-specific items directly from their catalog-aware order history by using "Buy Again" functionality.
- Filter order history through various options, including the channel (B2B seller or manufacturer) that the order originated from.
- Allow a manufacturer's customer service representatives to use on behalf of (OBO) functionality to place orders directly with the manufacturer or a B2B seller on behalf of their B2B partners.
- Use available headless APIs to allow representatives from the B2B seller (distributor) organization to manage their on-hand inventory and accept or reject orders.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
