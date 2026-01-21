---
title: B2B Multi-Outlet Feature Overview
description: Learn about the key features and benefits of native business-to-business (B2B) Multi-outlet capabilities in Microsoft Dynamics 365 Commerce.
author: Jcava-Evenica
ms.date: 01/21/2026
ms.topic: overview
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: v-jcavataio
ms.search.validFrom: 2021-01-31
ms.search.form: RetailOperations
ms.custom: 
  - bap-template
---

# B2B Multi-Outlet Feature Overview

[!include [banner](../../includes/banner.md)]

Business-to-Business (B2B) commerce often involves complex relationships between manufacturers, distributors, and downstream business partners. These relationships commonly include multiple organizations, multiple purchasing locations, and multiple users who place orders on behalf of those organizations.

Microsoft Dynamics 365 Commerce supports these scenarios by separating **purchasing context** (such as pricing, delivery addresses, and payment terms) from **user identity**, allowing organizations to scale their operations without duplicating configuration or losing visibility into ordering activity.

The following scenarios describe how this model is applied in real-world B2B commerce environments.


## Scenario 1: Manufacturer-to-distributor-to-outlet commerce model

**Business context**

In this scenario, a manufacturer sells products through one or more distributors. Distributors, in turn, sell to multiple business partners or outlets. Each participant plays a distinct role in the commerce process:
-	The **manufacturer** manages product availability and commercial agreements.
-	**Distributors** act as intermediaries and manage downstream pricing and relationships.
-	**Outlets** represent individual store locations or business units that place orders.
-	**Users** such as buyers, channel managers, and customer service representatives interact with the system to place or manage orders.
  
**How Dynamics 365 Commerce supports the scenario**

-	Each distributor and outlet is represented as a **separate purchasing entity** with its own pricing, delivery addresses, and financial terms.
-	Multiple users can place orders **on behalf of the same outlet**, without requiring individual purchasing configurations.
-	Orders are processed using the **outlet's purchasing context**, while retaining a reference to the user who submitted the order.
-	Customer service users can place orders **on behalf of outlets** using an order-on-behalf-of model, while preserving auditability.

**Business outcomes**
-	Centralized control of purchasing terms at the organization or outlet level
-	Flexible assignment of ordering responsibilities across users
-	Clear tracking of who placed each order
-	Reduced duplication of configuration across users

## Scenario 2: Multi-outlet purchasing with location-specific context

**Business context**

Organizations often operate multiple locations or business units that share a common parent organization but require separate purchasing contexts. Each location may have:
-	Different pricing or discount agreements
-	Different delivery addresses
-	Separate invoicing or financial reporting requirements
At the same time, buyers may be responsible for ordering for one or more locations.

**How Dynamics 365 Commerce supports the scenario**

-	Each location is represented as a **distinct organization or outlet** with its own purchasing configuration.
-	Buyers are represented as **contacts** and can be associated with one or more outlets.
-	A single user can switch between outlets and place orders in the correct purchasing context for each location.
-	Adding or removing buyers does not require changes to outlet-level configuration.

**Business outcomes**

-	Support for regional or location-based pricing models
-	Simplified buyer onboarding and maintenance
-	Accurate invoicing and fulfillment by location
-	Scalable model for growing organizations

**Key concepts illustrated by these scenarios**

These scenarios demonstrate the following core capabilities in Dynamics 365 Commerce:

-	**Organization-based purchasing**
Purchasing rules are defined at the organization or outlet level and reused across users.
-	**Contact-based user access**
Users are granted access to act on behalf of one or more organizations without duplicating setup.
-	**Context-aware ordering**
Orders automatically apply the correct pricing, addresses, and financial terms based on the selected organization.
-	**Auditability and accountability**
Orders retain visibility into both the organization and the individual user who placed them.

> [!NOTE]
>Some additional considerations before enabling this feature are below: 
>-	**Existing Contact Data** - If your accounts already use contacts, each contact must have a valid, unique email address to be used as an online user in the Commerce storefront. In addition, contact associations are maintained consistently between the organization and its linked customer hierarchy. As a result, removing a contact from the customer hierarchy also removes that contact from the organization.
>-	**Specific user level account settings (addresses, pricing)** - This model assumes that individual users use the same customer account settings as the linked organization.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
