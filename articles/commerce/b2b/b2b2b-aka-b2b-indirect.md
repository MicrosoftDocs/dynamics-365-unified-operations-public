---
title: B2B Indirect workflows
description: Learn about the key features and benefits of native B2B Indirect workflows in Microsoft Dynamics 365 Commerce.  
author: ashishmsft  
ms.date: 06/10/2025  
ms.topic: overview
ms.reviewer: johnmichalak
ms.search.region: Global  
ms.author: asharchw  
ms.search.validFrom: 2021-01-31  
ms.search.form: RetailOperations  
ms.custom: 
  - bap-template
---

# B2B Indirect workflows

[!include [banner](../../includes/banner.md)]

This article provides an overview of the key features and benefits of native business-to-business (B2B) Indirect workflows in Microsoft Dynamics 365 Commerce.

## What is B2B Indirect?

The Dynamics 365 Commerce B2B Indirect feature can help your business grow by powering dynamic, multitiered supply chains that enable products to flow seamlessly from manufacturers through trusted distributors to business customers. This strategy amplifies market reach, maximizes distribution channels, and accelerates sales by connecting consumer packaged goods (CPG) brands with retailers and other businesses via a robust network of intermediaries. B2B Indirect can help improve your B2B distribution process because each business intermediary becomes a catalyst for growth, ensuring that your products reach the right customers.

![B2B2B Overview Conceptual Model](../media/B2B2B-Overview-Conceptual-Model.png)

## How does Dynamics 365 Commerce support B2B Indirect workflows?

Dynamics 365 Commerce is a cloud-based platform that provides a comprehensive set of capabilities to enable B2B commerce scenarios. The platform supports both direct and indirect B2B workflows in a headless, composable manner, allowing merchants to manage multiple types of business relationships and transactions. Some of the key features of Dynamics 365 Commerce for B2B Indirect workflows are:

- Ability to create and manage multiple B2B Seller and B2B Buyer accounts, each with their own pricing, catalog, and inventory management.
- Ability to configure and apply complex pricing and discount rules based on various criteria such as account type, order quantity, product category, and more.
- Ability to create and manage multiple catalogs and assortments for different B2B Seller and B2B Buyer accounts. You can choose to inherit, override, or extend product information from the primary catalog.
- Ability to allow B2B Buyers to buy from a select authorized and approved list of B2B Sellers or from the Manufacturer directly.
- Ability to allow Customer service agents (aka field sellers) from the Manufacturer’s organization to order on behalf of (OBO) a B2B Buyer (outlet-buyer) with a specific B2B Seller (Distributor/Wholesaler).
- Ability to provide a rich and responsive user interface for B2B Seller and B2B Buyer portals. Features include product search, browsing, filtering, sorting, comparison, reviews, ratings, wish lists, cart, checkout, order history, and more.
- Ability to integrate with various external systems and services, such as ERP, CRM, payment, tax, shipping, and more, using the platform's APIs and connectors.

## Why choose Dynamics 365 Commerce for B2B Indirect workflows?

Dynamics 365 Commerce is designed to support high-volume merchants and provides a suite of advanced features to cater to the specific needs of B2B transactions. Some of the benefits of choosing Dynamics 365 Commerce for B2B Indirect workflows are:

![Evolution of Dynamics 365 Commerce to support B2B2B natively](../media/EvolutionB2BtoB2B2B.png)

- B2B Indirect workflows build on the existing B2B workflows. They use the same platform features and data model, so users get a consistent and smooth experience.
- B2B Indirect workflows are available in a headless manner. This means merchants can use the platform's APIs and SDKs to build custom extensions and integrations that fit their existing business processes.
- B2B Indirect workflows are scalable, secure, and reliable, as they're built on the Microsoft Azure cloud platform, which offers high availability, performance, and compliance.
- B2B Indirect workflows are flexible and customizable. Merchants can configure many parts of the platform—such as business rules, the user interface, and workflows—to fit their specific needs.

## B2B Seller Prospect Sign-up and Approval Process

![B2B Seller (aka B2B Distributor) approval process visualized in simplest manner](../media/B2BSeller-Approval-Process.png)

The following is a brief overview of the steps involved in becoming a B2B seller on the platform:

- Submit B2B Seller Prospect Application: Prospective B2B sellers submit an application expressing their interest in becoming a seller on the platform. The application includes relevant business information, contact details, etc.
- Sync Prospect Application: The submitted application is synced to HQ and made available for review. Run or schedule a P-001 sync job from the Distribution Schedule and run `Sync Customer requests`.
- Review Prospect Application: The platform team evaluates the prospect’s suitability based on predefined criteria. Criteria may include business size, industry, product offerings, and compliance with platform policies. The review process aims to identify genuine businesses and filter out potential fraud or unwanted applicants.
- Approve/Reject B2B Seller Prospect: Based on the review, the prospect application is either approved or rejected. Approved prospects receive confirmation and further instructions on the next steps. Rejected applicants are informed of the decision and the reasons behind it.

Once approved, the system sets up the following elements in the back office and associates them with the B2B seller through these steps:

- Creates a Copy of Existing Online B2B Channel: The platform creates a new B2B channel specifically for the approved seller. This channel has a unique site and warehouse, allowing the seller to manage their inventory separately.
- Employee Record Creation: An employee record is set up automatically for the B2B seller. This record enables the seller to carry out inventory management, order management, and other operational tasks.
- Customer Hierarchy Mapping: The B2B seller (channel) is mapped to a specific customer hierarchy. This hierarchy defines the relationships between the seller and their customers, such as pricing, discounts, payment terms, etc.
- Manufacturer Channel Mapping: The B2B seller’s channel is linked to the manufacturer channel. This ensures that the seller can purchase products directly from the manufacturer, maintaining supply chain efficiency and quality control.

By following these steps, the B2B seller can become a part of the platform and can start selling to their retail outlets.

## B2B Indirect capabilities

As part of this feature, you'll be able to natively leverage the following capabilities, in addition to all existing B2B capabilities that are already available:

- Onboard _B2B Seller_ as a new B2B Prospect type for _Distributors or Wholesalers_.
- Convert existing _B2B Buyers_ to become _B2B Seller and Buyer_.
- Map _B2B Buyers_ to select _B2B Sellers_ and choose if they can also buy from _Manufacturer_ directly. 
- Create _B2B catalog-aware_ Commerce orders in HQ and Call Center, along with the ability to choose the fulfilling channel _(B2B Seller or distributor)_ in the order header.
- Map individual _B2B Buyer_ organizations to _B2B Sellers and/or Manufacturers_, giving you control over who can buy from whom. You can configure this directly from the _B2B Buyer’s customer hierarchy_, by mapping associated _B2B channels_ they can buy from.
- Allow _B2B Buyers_ to choose to purchase from _multiple B2B Sellers and/or the Manufacturer_.
- At any point in time, B2B buyers can buy from a single _B2B Seller (aka distributor) or Manufacturer directly_, but they can have multiple active carts at the same time with individual B2B Sellers or the Manufacturer.
- Order templates are now catalog-aware, enabling customers to bulk-add items from multiple catalogs.
- Order history is catalog-aware, allowing customers to quickly rebuy catalog-specific items directly from order history using "Buy Again."
- Order history allows you to filter by various options, including the channel (B2B Seller or Manufacturer) where the order originated.
- Order-on-behalf-of allows customer service agents (C1 employees) from the Manufacturer (not B2B Sellers) to place an order on behalf of their B2B partners (C2 - B2B Buyers) directly with the Manufacturer or a B2B Seller.
- Additionally, there are headless APIs available to allow C1 from the B2B Seller (Distributor's) organization to manage their inventory on hand and accept or reject orders.

![Glimpse into end-user experience using native experiences of B2B Indirect (aka B2B2B)](../media/B2B-Indirect-Experience-Glimpse.png)
