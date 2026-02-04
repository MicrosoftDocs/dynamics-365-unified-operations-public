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


Many B2B organizations operate through multiple purchasing locations, branches, or outlets that are managed by the same group of buyers. These buyers are often responsible for placing orders for one or more outlets, while commercial rules such as pricing, credit limits, catalogs, and fulfillment settings are defined centrally at the organization or outlet level.
**B2B Multi-Outlet support in Dynamics 365 Commerce** introduces a scalable, modern model that allows a single user identity to place orders across multiple associated outlets without duplicating configuration or fragmenting order visibility.
This capability represents a significant evolution in how B2B users and organizations are modeled in Commerce. It moves away from a **person-based customer account model** toward a **contact-based identity model**, tightly integrated with **customer hierarchies**.
 
## What is B2B Multi-Outlet support?

B2B Multi-Outlet support enables a single business user—represented as a contact—to access, select, and place orders for multiple organizations or outlets within the same Commerce environment.

Key characteristics include:

- Single sign-in identity for users who manage multiple outlets
- Organization-based purchasing context, where pricing, catalogs, addresses, and credit limits are defined
- Contact-based access, where users are associated with one or more organizations through customer hierarchies
- Context-aware ordering, where the selected outlet determines pricing, inventory, and checkout behavior
 
This model closely reflects real-world B2B operations and removes the need to create duplicate users or customer records for each outlet.
 
## Why B2B Multi-Outlet support matters

B2B organizations rarely operate as a single purchasing entity. Instead, they often consist of multiple branches, outlets, cost centers, or locations that place orders independently while still belonging to the same legal or commercial organization.

Supporting this operating model effectively is critical for:

- Scalability as organizations grow
- Operational efficiency for administrators
- A streamlined buying experience for users

B2B Multi-Outlet support addresses this need by clearly separating **user identity** from **purchasing context**, while maintaining centralized control over commercial configuration.

## Challenges with traditional B2B commerce models

In traditional B2B Commerce implementations, systems often enforced a one-to-one relationship between a user and a purchasing account. As organizations expanded, this model introduced several challenges.

**Separate user accounts for each outlet**

Organizations frequently had to create multiple user accounts for the same individual—one per outlet or purchasing account. For example, a regional buyer responsible for five stores might need five separate logins.

This increased:

- User frustration due to managing multiple credentials
- Administrative effort for onboarding, role changes, and offboarding
- Risk of inconsistent access and security gaps
 
**Duplicate pricing configuration**

When each outlet was treated as a separate customer account, pricing rules, discounts, often had to be duplicated across records.

This duplication:

- Increased configuration and maintenance effort
- Made pricing changes harder to manage consistently
- Increased the risk of configuration drift between outlets
 
**Fragmented order history**

Sales orders were created against individual customer accounts rather than a unified organizational entity. As a result:

- Order history was spread across multiple customer accounts
- Headquarters lacked a consolidated view of organizational purchasing
- Customer Service had limited visibility into total organizational spend


## The shift enabled by B2B Multi-Outlet support

B2B Multi-Outlet support introduces a fundamental shift by clearly separating two core concepts:

- **Who places the order** — the contact
- **Which entity is purchasing** — the organization or outlet

This separation aligns the system with real-world B2B business practices.

**Centralized commercial control**

Organizations define pricing, discounts, catalogs, credit limits, and fulfillment rules once at the organization or outlet level. These settings are reused consistently across all associated users.

**Flexible user access**

Users are represented as contacts and can be associated with one or more outlets through customer hierarchies. A single user can act on behalf of multiple outlets without duplicating identity or configuration.

## What changes with B2B Multi-Outlet support

B2B Multi-Outlet support enables a set of core capabilities that modernize user management, transaction ownership, eCommerce storefront behavior, and Customer Service workflows for Call center.

**Users managed using contacts**

With B2B Multi-Outlet support, users are modeled as contacts rather than person-type customer accounts.

- Each contact represents an individual user who signs in to the storefront.
- A single contact can be associated with one or more organizations or outlets, and is granted online access through association with an organization’s customer hierarchy.
- Contacts inherit purchasing rules such as pricing, catalogs, credit limits, and fulfillment settings from the organization context.

This approach simplifies identity management and aligns with enterprise authentication models.
 
 
**Single sign-in for managing orders across multiple outlets**

With B2B Multi-Outlet support, users sign in to the Dynamics 365 Commerce storefront once and can access all authorized outlets without maintaining separate credentials for each location.

In this model, a user is represented as a contact and authenticated through a single identity. That contact can be associated with one or more organizations or outlets through customer hierarchies. After signing in, the user can select the outlet they want to operate under and place orders within that context.

**How it works**

- The user signs in using a single storefront identity.
- After sign-in, the storefront evaluates which organizations or outlets the contact is authorized to access.
- If multiple outlets are available, the storefront presents an organization selection experience.
- The selected outlet determines pricing, catalogs, inventory availability, and checkout behavior.

Users can switch between outlets during the same session without signing out or reauthenticating.
 
**Business value**

Single sign-in across outlets provides several benefits:

- **Simplified user experience**
 Users manage one set of credentials instead of multiple logins for different outlets.
- **Reduced identity duplication**
 Organizations avoid creating multiple user accounts for the same individual.
- **Improved security and governance**
 Access is managed centrally through customer hierarchies rather than distributed across multiple accounts.
- **Operational efficiency**
 Onboarding and offboarding users is faster because access changes are applied once at the contact level.
 
**Impact on storefront behavior**

When a user switches outlets during a session:

- Pricing, catalogs, and inventory availability are refreshed based on the selected outlet.
- The active purchasing context is clearly indicated in the storefront.
- The shopping cart is unique for each outlet, allowing for a clean and consistent user experience.

This ensures that users always place orders using the correct organizational context while benefiting from a seamless sign-in experience.
 
## Sales order creation: from individual customer accounts to organization-based ordering

**Current behavior in traditional B2B eCommerce**

In existing Dynamics 365 Commerce B2B standard implementations, sales orders are created against **individual customer accounts** that represent buyers. Even when users belong to the same organization, each user owns their own transactional customer account.

As a result:

- Orders for the same organization are distributed across multiple customer accounts
- Order ownership does not align with how businesses manage purchasing
- Credit limit evaluation is already performed at the customer hierarchy (organization) level, not at the individual contact or outlet level

Although organization-level credit evaluation exists today, the user-centric order creation model introduces reporting and operational complexity.
 
**Challenges with the current order creation model**

- Fragmented order history across multiple buyer accounts
- Higher maintenance effort for managing many customer records
- Misalignment between business ownership and transactional ownership, where the organization is the true purchaser but does not own the orders in the system
 
**Organization-based sales order creation with B2B Multi-Outlet support**

With B2B Multi-Outlet support enabled, Dynamics 365 Commerce introduces an organization-centric transaction model.

**New behavior**

- Sales orders are created against the organization account, represented by the customer hierarchy
- Contacts represent the users who place orders but do not own the customer account
- Each sales order retains a contact reference for audit and tracking purposes

This ensures that all purchasing activity is consolidated under the organization, regardless of which user places the order.
 
## Business impact of organization-based ordering

**Consolidated organizational purchasing view**

Organizations gain:

- A single, unified view of all orders
- Improved reporting and analytics
- Simplified Customer Service support for multi-user organizations
 
**Credit controls remain organization-driven**

Credit limit evaluation continues to be performed at the **customer hierarchy (organization) level**. This ensures that:
- Credit exposure reflects total organizational purchasing
- No credit limits need to be defined per user
- Credit control aligns with standard B2B credit practices

**Key point**
Credit limits are evaluated at the organization (customer hierarchy) level, not at the individual contact level.

**Clear accountability without data fragmentation**

Although orders are owned by the organization, the system records which contact placed each order. This preserves:

- Auditability
- User-level accountability
- Clear investigation paths for Customer Service
 
**Reduced administrative overhead**

Organizations can:

- Add or remove users without creating or deleting customer accounts
- Scale buyers and outlets without duplicating configuration
- Maintain cleaner, more maintainable customer data
 

## Managing user access through customer hierarchies
Customer hierarchies serve as the primary control point for managing user access in B2B Multi-Outlet support. Administrators can associate, update, and manage contacts directly from the customer hierarchy view, ensuring that access rules are applied consistently across Commerce, the storefront, and Customer Service experiences.

This centralized approach simplifies user lifecycle management while preserving auditability and historical integrity.

**Associating contacts directly from the customer hierarchy**

Administrators can associate contacts to an organization by adding them directly to the customer hierarchy.

When a contact is added through the customer hierarchy:

- The contact becomes authorized to act on behalf of the linked organization.
- The contact inherits organization-level purchasing context, including pricing, catalogs, credit limits, and channel access.
- A role (Admin or User) can be assigned at the hierarchy level to control visibility and permissions.

Associating contacts through the customer hierarchy has the same functional effect as associating them through the organization account, ensuring consistent access behavior regardless of entry point.

**Making users inactive from the customer hierarchy**

Customer hierarchies provide controls to disable user access without removing historical associations.

When an administrator disables a contact from the customer hierarchy:

- The contact  loses storefront access for the selected organization.
- The contact remains associated with the organization for audit and reporting purposes.
- Existing orders and historical transactions remain unchanged.

Contacts who have placed orders cannot be fully removed from the hierarchy. Disabling the contact ensures security while preserving transaction history.

**Providing a reason when disabling a contact**

When disabling a contact, administrators are prompted to enter a reason for the action.

Some example reasons include:
- User left the organization
- Temporary suspension
- Role change
- Access no longer required

This is done by D365 Commerce administrator entering text as part of the process, so it is open ended and user defined. This reason is stored and visible in the customer hierarchy for audit and operational visibility.

Capturing a reason helps organizations maintain clarity around access decisions and supports compliance and audit scenarios.

**Impact of organization-level updates on customer hierarchy association**

Changes made to a contact at the organization account level are reflected in the customer hierarchy.
Examples include:

- **Disabling a contact at the organization level**
 The contact is also treated as inactive in the customer hierarchy and loses storefront access.
- **Re-enabling a contact**
 Access can be restored without reconfiguring hierarchy associations.
- **Updating contact details (such as email or status)**
 These updates flow through to hierarchy-based access evaluation and storefront authentication.

This alignment ensures that user status remains consistent across organization accounts, customer hierarchies, and Commerce channels.

**Why hierarchy-based user management matters**

Managing users directly from the customer hierarchy provides several benefits:

- Centralized control – Access is managed from a single, authoritative structure.
- Immediate effect – Enable and disable actions take effect without additional configuration.
- Audit-friendly – Reasons for access changes are captured and preserved.
- Scalable administration – Organizations can manage large numbers of users and outlets without duplicating effort.
 
## Call center scenarios

B2B Multi-Outlet support extends call center and assisted selling capabilities in Dynamics 365 Commerce by enhancing how Customer Service users identify and work with individual buyers who place orders on behalf of an organization.

These enhancements improve auditability, accountability, and operational clarity without changing the organization-centric transaction model.

**Enhancements to the Customer Service form**

With B2B Multi-Outlet support enabled, the Customer Service form includes support for associating a **contact** with a sales order.

- The **organization account** remains the customer for the order.
- The **contact** represents the individual who is responsible for placing or requesting the order.
- The contact association is optional and is used for identification, audit, and support purposes.

This enhancement allows Customer Service users to clearly distinguish between _who the organization is and who acted on behalf of that organization_.

**Associating a contact with a sales order**

When creating or reviewing a sales order in Customer Service:

- A **Contact** field is available on the sales order.
- Customer Service users can select a contact who is associated with the organization through the customer hierarchy.
- The selected contact is stored on the order as a reference to indicate who placed or requested the order.

For orders originating from the storefront:
- The contact reference is populated automatically.


**Call Center behavior for disabled or inactive contacts**

Contact association is governed by the contact’s active status within the organization and customer hierarchy.

**Creating new sales orders**

- Only active contacts associated with the selected organization can be associated with new sales orders.
- If a contact is disabled or inactive for the organization:
-- The contact does not appear as a selectable option.
-- The contact cannot be associated with the order.

This ensures that only authorized and currently active users are linked to new transactions.

**Existing orders and historical data**

- If a contact becomes inactive after placing an order:
-- The existing sales order remains unchanged.
-- The contact reference is retained for audit and reporting purposes.
- Historical orders continue to show the original contact, even if that contact is no longer active.

This behavior preserves transaction history while enforcing current access rules.

**Creating orders when contacts are inactive**

If all contacts for an organization are inactive:

- Customer Service users can still create sales orders using the organization account.
- No contact is associated with the order unless an active contact is available.
- This allows business continuity while maintaining access controls.

**Why this behavior matters**
This design provides a balance between flexibility and governance:
- **Security** – Prevents inactive or unauthorized users from being linked to new transactions.
- **Auditability** – Maintains a clear record of who placed historical orders.
- **Operational clarity** – Separates organizational ownership of orders from individual responsibility.
- **Consistency** – Applies the same access rules across storefront and call center scenarios.


## Storefront experiences

For the current state of this feature the storefront supports:

- Organization selection at sign-in and available to change afterward for users with multi-outlet access
- Pricing, catalogs, and checkout behavior based on the selected outlet
- Persistent shopping carts when switching organizations
- Role-based order history visibility

> [!NOTE]
> For the current state of this feature order templates are scoped at the contact level. Organization-level templates are planned for a future release.
 
Call center and Customer Service experiences
B2B Multi-Outlet support enhances assisted selling scenarios by enabling Customer Service users to:
·	Identify which contact placed an order
·	Search orders by contact across one or more outlets
·	Create orders on behalf of a contact while respecting outlet access rules
Only active contacts associated with the selected organization can be assigned to new orders. If a contact is inactive, the organization account can still be used, but the contact cannot be associated with the order.

## Enabling the B2B Multi-Outlet Feature
The **B2B Multi-Outlet Ordering with Contact-Based Access** feature is available for preview starting with the Commerce version 10.0.47 release. To configure multi-outlet and contact based B2B customer hierarchies, go to the **Feature management** workspace (**System administration > Workspaces > Feature management**), enable the **B2B Multi-Outlet Ordering with Contact-Based Access feature**, and then run the **1110 CDX job**.
>[!NOTE] 
>This preview feature is recommended for new B2B channel implementations only, with no existing B2B users in the system. A future release will include migration options from B2B organization and user configurations as part of enabling the feature.

Configuring multi-outlet organizations
At a high level, organizations can see multi-outlet support by:
1.	Creating or onboarding organization accounts
2.	Creating contacts to represent users
3.	Linking contacts to organizations using customer hierarchies
4.	Assigning roles, catalogs, and channels
5.	Enabling contacts for storefront access
6.	Synchronizing data to Commerce using CDX jobs


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
