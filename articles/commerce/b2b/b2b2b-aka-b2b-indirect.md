---
title: B2B indirect workflows
description: Learn about the key features and benefits of native B2B indirect workflows in Microsoft Dynamics 365 Commerce.  
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

# B2B indirect workflows

[!include [banner](../../includes/banner.md)]

This article provides an overview of the key features and benefits of native business-to-business (B2B) Indirect workflows in Microsoft Dynamics 365 Commerce.

The Dynamics 365 Commerce B2B indirect feature can help your business grow by powering dynamic, multitiered supply chains that enable products to flow seamlessly from manufacturers through trusted distributors to business customers. This strategy amplifies market reach, maximizes distribution channels, and accelerates sales by connecting consumer packaged goods (CPG) brands with retailers and other businesses via a robust network of intermediaries. The B2B indirect feature can help improve your B2B distribution process because each business intermediary becomes a catalyst for growth, ensuring that your products reach the right customers.

![B2B2B Overview Conceptual Model](../media/B2B2B-Overview-Conceptual-Model.png)

## Dynamics 365 Commerce support for B2B indirect workflows

The Dynamics 365 Commerce cloud-based platform provides a comprehensive set of capabilities to enable B2B commerce scenarios. The platform supports both direct and indirect B2B workflows with a headless, composable architecture that allows merchants to manage multiple types of business relationships and transactions. 

B2B indirect workflow capabilities enable you to:

- Create and manage multiple B2B seller and B2B buyer accounts that each have their own pricing, catalog, and inventory management.
- Configure and apply complex pricing and discount rules based on criteria such as account type, order quantity, and product category.
- Create and manage multiple catalogs and assortments for different B2B seller and B2B buyer accounts. You can choose to inherit, override, or extend product information from the primary catalog.
- Allow B2B buyers to purchase from an authorized and approved list of B2B sellers, or directly from the manufacturer.
- Allow customer service agents (also known as field sellers) from the manufacturer's organization to order on behalf of (OBO) B2B buyers (outlet-buyer) from specific B2B sellers (distributors/wholesalers).
- Use a rich and responsive user interface for B2B seller and B2B buyer portals with features that include product search, browsing, filtering, sorting, comparison, reviews, ratings, wish lists, cart, checkout, and order history.
- Integrate with various external systems and services, such as enterprise resource planning (ERP), customer relationship management (CRM), payment, tax, and shipping using the platform's APIs and connectors.

## Benefits of choosing Dynamics 365 Commerce for B2B indirect workflows

Dynamics 365 Commerce is designed to support high-volume merchants and provides a suite of advanced features to cater to the specific requirements of B2B transactions. 

Some of the benefits of choosing Dynamics 365 Commerce for B2B indirect workflows are:

- B2B indirect workflows build on the existing B2B workflows and use the same platform features and data model, so users get a consistent and smooth experience.
- B2B indirect workflows are available in a headless mode so that merchants can use the platform's APIs and SDKs to build custom extensions and integrations that fit their existing business processes.
- B2B indirect workflows are scalable, secure, and reliable because they're built on the Microsoft Azure cloud platform, which offers high availability, performance, and compliance.
- B2B indirect workflows are flexible and customizable. Merchants can configure many parts of the platform such as business rules, workflows, and the user interface to fit their specific needs.

![Evolution of Dynamics 365 Commerce to support B2B2B natively](../media/EvolutionB2BtoB2B2B.png)

## B2B seller prospect sign-up and approval process

The following steps provide an overview of how tp become a B2B seller on the platform:

- **Submit a B2B seller prospect application**: Prospective B2B sellers submit an application expressing their interest in becoming a seller on the platform. The application includes relevant business information and contact details.
- **Sync prospect application**: The submitted application is synced to Commerce headquarters and made available for review. <!--Run or schedule a P-001 sync job from the Distribution Schedule and run **Sync Customer requests**.-->
- **Review prospect application**: The platform team evaluates the prospect's suitability based on predefined criteria. Criteria may include business size, industry, product offerings, and compliance with platform policies. The review process aims to identify genuine businesses and filter out potential fraud or unwanted applicants.
- **Approve or reject B2B seller prospect**: Based on the platform team review, the prospect application is either approved or rejected. Approved prospects receive confirmation and further instructions on the next steps. Rejected applicants are informed of the decision and the reasons behind it.

Once approved, the system sets up the following elements in headquarters and associates them with the B2B seller:

- **Creates a copy of existing online B2B channel**: The platform creates a new B2B channel specifically for the approved seller. This channel has a unique site and warehouse, allowing the seller to manage their inventory separately.
- **Creates an employee record**: An employee record is set up automatically for the B2B seller. This record enables the seller to carry out inventory management, order management, and other operational tasks.
- **Maps the customer hierarchy**: The B2B seller (channel) is mapped to a specific customer hierarchy. This hierarchy defines the relationships between the seller and their customers, such as pricing, discounts, and payment terms.
- **Maps the manufacturer channel**: The B2B seller's channel is mapped to the manufacturer channel, which ensures that the seller can purchase products directly from the manufacturer to maintain supply chain efficiency and quality control.

By following these steps, the B2B seller can become a part of the platform and can start selling to their retail outlets.

![B2B Seller (aka B2B Distributor) approval process visualized in simplest manner](../media/B2BSeller-Approval-Process.png)

## B2B indirect feature capabilities

As part of the B2B indirect feature, you're able to take advantage of the following capabilities:

- Onboard a B2B seller as a new B2B prospect type for distributors or wholesalers.
- Convert existing B2B buyers to become B2B sellers and buyers.
- Map B2B buyers to select B2B sellers and decide if they can also buy directly from the manufacturer. 
- Create B2B catalog-aware Commerce orders in headquarters and call center, along with the ability to choose the fulfilling channel (B2B seller or distributor) in the order header.
- Map individual B2B buyer organizations to B2B sellers and/or manufacturers, giving you control over who can buy from whom. You can configure this functionality directly from the B2B buyer's customer hierarchy by mapping the associated B2B channels they can buy from.
- Allow B2B buyers to choose to purchase from multiple B2B sellers and/or the manufacturer.
- B2B buyers can at any time buy directly from a single B2B seller (distributor) or manufacturer, but can also have multiple active carts at the same time with individual B2B sellers or the manufacturer.
- Enable customers to bulk-add items from multiple catalogs with catalog-aware order templates.
- Allow customers to quickly rebuy catalog-specific items directly from their catalog-aware order history using "Buy Again" functionality.
- Filter order history using various options, including the channel (B2B seller or manufacturer) where the order originated.
- Allow manufacturer customer service agents to use order-on-behalf-of functionality to place orders directly with the manufacturer or a B2B seller on behalf of their B2B partners.
- Use available headless APIs to allow representatives from the B2B seller (distributor) organization to manage their inventory on hand and accept or reject orders.

![Glimpse into end-user experience using native experiences of B2B indirect (aka B2B2B)](../media/B2B-Indirect-Experience-Glimpse.png)
