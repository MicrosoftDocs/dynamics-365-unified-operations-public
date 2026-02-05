---
title: B2B multioutlet capabilities (preview)
description: Learn about the key features and benefits of native business-to-business (B2B) multioutlet capabilities in Microsoft Dynamics 365 Commerce.
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

# B2B multioutlet capabilities (preview)

[!INCLUDE [banner](../../includes/banner.md)]
[!INCLUDE [banner](../../includes/preview-banner.md)]

This article describes the key features and benefits of native business-to-business (B2B) multioutlet capabilities in Microsoft Dynamics 365 Commerce.

Many B2B organizations operate through multiple purchasing locations, branches, or outlets. The same group of buyers often places orders for one or more outlets. Commercial rules such as pricing, credit limits, catalogs, and fulfillment settings are defined centrally at the organization or outlet level.
 
B2B multioutlet support in Dynamics 365 Commerce is a scalable model that allows one user identity to place orders across multiple associated outlets. This model reduces duplicate configuration and improves visibility across orders.
 
This capability changes how Commerce models B2B users and organizations. It moves from a *person-based customer account model* to a *contact-based identity model* that integrates with *customer hierarchies*.
 
## What is B2B multioutlet support?
 
B2B multioutlet support allows a single business user, represented as a contact, to access and place orders for multiple organizations or outlets in the same Commerce environment.
 
Key characteristics include:
 
- Single sign-in identity for users who manage multiple outlets.
- Organization-based purchasing context, where pricing, catalogs, addresses, and credit limits are defined.
- Contact-based access, where users are associated with one or more organizations through customer hierarchies.
- Context-aware ordering, where the selected outlet determines pricing, inventory, and checkout behavior.
 
This model reflects common B2B operations. It also removes the need to create duplicate users or customer records for each outlet.
 
## Why B2B multioutlet support matters
 
B2B organizations rarely operate as a single purchasing entity. Instead, they often include multiple branches, outlets, cost centers, or locations that place orders independently. These entities still belong to the same legal or commercial organization.
 
Supporting this operating model is critical for:
 
- Scalability as organizations grow.
- Operational efficiency for administrators.
- A streamlined buying experience for users.
 
B2B multioutlet support addresses this need by separating *user identity* from *purchasing context*. At the same time, it keeps centralized control over commercial configuration.
 
## Challenges with traditional B2B commerce models
 
Traditional B2B Commerce implementations often enforce a one-to-one relationship between a user and a purchasing account. As organizations expand, that model creates several problems.
 
### Separate user accounts for each outlet
 
Organizations frequently create multiple user accounts for the same individual, one per outlet or purchasing account. For example, a regional buyer who manages five stores might need five separate sign-ins.
 
This pattern increases:
 
- User frustration from managing multiple credentials.
- Administrative effort for onboarding, role changes, and offboarding.
- Risk of inconsistent access and security gaps.
 
### Duplicate pricing configuration
 
When each outlet is treated as a separate customer account, pricing rules and discounts often have to be duplicated across records.
 
This duplication increases:
 
- Configuration and maintenance effort.
- Difficulty of managing pricing changes consistently.
- Risk of configuration drift between outlets.
 
### Fragmented order history
 
Sales orders are created against individual customer accounts instead of a single organizational entity. As a result:
 
- Order history is spread across multiple customer accounts.
- Headquarters lacks a consolidated view of organizational purchasing.
- Customer service has limited visibility into the total organizational spend.
 
## The shift enabled by B2B multioutlet support
 
B2B multioutlet support separates two core concepts:
 
- **Who places the order**: The contact
- **Which entity is purchasing**: The organization or outlet
 
This separation aligns Commerce with common B2B business practices.
 
### Centralized commercial control
 
Organizations define pricing, discounts, catalogs, credit limits, and fulfillment rules once at the organization or outlet level. Commerce reuses these settings across all associated users.
 
### Flexible user access
 
Commerce represents users as contacts. Administrators can associate each contact with one or more outlets through customer hierarchies. A single user can act on behalf of multiple outlets without duplicating identity or configuration.
 
## What changes with B2B multioutlet support?
 
B2B multioutlet support adds capabilities that modernize user management, transaction ownership, storefront behavior, and call center workflows.
 
### Users are managed as contacts
 
With B2B multioutlet support, users are modeled as contacts instead of person-type customer accounts.
 
- Each contact represents an individual user who signs in to the storefront.
- A single contact can be associated with one or more organizations or outlets. The contact is granted online access through association with an organization’s customer hierarchy.
- Contacts inherit purchasing rules such as pricing, catalogs, credit limits, and fulfillment settings from the organization context.
 
This approach simplifies identity management and aligns with enterprise authentication models.
 
### Single sign-in for orders across multiple outlets
 
With B2B multioutlet support, users sign in to the Commerce storefront once. They can access all authorized outlets without maintaining separate credentials for each location.
 
In this model, a user is represented as a contact and authenticated through a single identity. The contact can be associated with one or more organizations or outlets through customer hierarchies. After the user signs in, the storefront lets the user select the outlet to use for ordering.
 
#### How single sign-in works

Single sign-in works in the following ways:

- The user signs in by using a single storefront identity.
- After the user signs in, the storefront determines which organizations or outlets the contact can access.
- If multiple outlets are available, the storefront shows an organization selection experience.
- The selected outlet determines pricing, catalogs, inventory availability, and checkout behavior.
 
Users can switch between outlets during the same session without signing out.
 
#### Business value
 
Single sign-in across outlets provides several benefits:
 
- **Simplified user experience**: Users manage one set of credentials instead of multiple sign-ins for different outlets.
- **Reduced identity duplication**: Organizations avoid creating multiple user accounts for the same individual.
- **Improved security and governance**: Administrators manage access centrally through customer hierarchies instead of distributing access across multiple accounts.
- **Operational efficiency**: Onboarding and offboarding users is faster because administrators apply access changes once at the contact level.
 
#### Impact on storefront behavior
 
When a user switches outlets during a session, the following things happen:
 
- Pricing, catalogs, and inventory availability are refreshed based on the selected outlet.
- The storefront indicates the active purchasing context.
- Each outlet has its own shopping cart, which supports a clean and consistent user experience.
 
This behavior helps users place orders in the correct organizational context while using a single sign-in.
 
## Sales order creation: From individual customer accounts to organization-based ordering
 
### Current behavior in traditional B2B e-commerce
 
In many existing Dynamics 365 Commerce B2B implementations, sales orders are created against *individual customer accounts* that represent buyers. Even when users belong to the same organization, each user owns a separate transactional customer account.
 
As a result:
 
- Orders for the same organization are distributed across multiple customer accounts.
- Order ownership doesn't align with how organizations manage purchasing.
- Credit limit evaluation is already performed at the customer hierarchy (organization) level, not at the individual contact or outlet level.
 
Although organization-level credit evaluation already exists, user-centric order creation adds reporting and operational complexity.
 
### Challenges with the current order creation model

Challenges with the current order creation model include:
 
- Fragmented order history across multiple buyer accounts.
- Higher maintenance effort for managing many customer records.
- Misalignment between business ownership and transaction ownership.
 
### Organization-based sales order creation with B2B multioutlet support
 
With B2B multioutlet support enabled, Commerce uses an organization-centric transaction model.
 
New behavior includes:
 
- Sales orders are created against the organization account, represented by the customer hierarchy.
- Contacts represent the users who place orders but don't own the customer account.
- Each sales order retains a contact reference for auditing and tracking.
 
This approach consolidates purchasing activity under the organization, regardless of which user places the order.
 
## Business impact of organization-based ordering
 
### Consolidated organizational purchasing view
 
Benefits of a consolidated organizational purchasing view include:
 
- A single, unified view of all orders.
- Improved reporting and analytics.
- Simplified customer service support for multiuser organizations.
 
### Credit controls remain organization-driven
 
Credit limit evaluation continues to be performed at the *customer hierarchy (organization) level*. This approach ensures that:
 
- Credit exposure reflects total organizational purchasing.
- Credit limits aren't defined per user.
- Credit control aligns with standard B2B credit practices.
 
> [!NOTE]
> Credit limits are evaluated at the organization (customer hierarchy) level, not at the individual contact level.
 
### Clear accountability without data fragmentation
 
Although the organization owns the orders, the system records which contact placed each order. This record supports:
 
- Auditability.
- User-level accountability.
- Investigation by customer service.
 
### Reduce administrative overhead
 
Organizations reduce administrative overhead in the following ways:
 
- Adding or removing users without creating or deleting customer accounts.
- Scaling buyers and outlets without duplicating configuration.
- Maintaining cleaner customer data.
 
## Manage user access through customer hierarchies
 
Customer hierarchies are the primary control point for managing user access in B2B multioutlet support. Administrators can associate, update, and manage contacts from the customer hierarchy view. This approach helps ensure that access rules are applied consistently across Commerce, the storefront, and customer service experiences.
 
This centralized approach simplifies user lifecycle management while preserving auditability and historical integrity.
 
### Associate contacts from the customer hierarchy
 
Administrators can associate contacts with an organization by adding the contacts directly to the customer hierarchy.
 
When an administrator adds a contact through the customer hierarchy:
 
- The contact is authorized to act on behalf of the linked organization.
- The contact inherits organization-level purchasing context, including pricing, catalogs, credit limits, and channel access.
- The administrator can assign a role (administrator or user) at the hierarchy level to control permissions.
 
Associating contacts using the customer hierarchy has the same effect as associating them through the organization account. It provides consistent access behavior, regardless of where an administrator makes the change.
 
### Make users inactive in the customer hierarchy
 
Customer hierarchies provide controls to disable user access without removing historical associations.
 
When an administrator disables a contact in the customer hierarchy:
 
- The contact loses storefront access for the selected organization.
- The contact remains associated with the organization for auditing and reporting.
- Existing orders and historical transactions remain unchanged.
 
Contacts who placed orders can't be fully removed from the hierarchy. Disabling access helps maintain security while preserving transaction history.
 
### Provide a reason when disabling a contact
 
When an administrator disables a contact, they're prompted to enter a reason.
 
Examples include:
 
- The user left the organization.
- Temporary suspension.
- Role change.
- Access is no longer required.
 
The Commerce administrator enters the disable reason during the process. The reason is stored in the customer hierarchy for auditing and operational visibility.
 
Capturing a reason helps organizations understand access decisions and supports compliance and audit scenarios.
 
### Impact of organization updates on customer hierarchy associations
 
Changes made to a contact at the organization account level are reflected in the customer hierarchy. Examples include:
 
- **Disabling a contact at the organization level**: The contact is treated as inactive in the customer hierarchy and loses storefront access.
- **Re-enabling a contact**: Access can be restored without reconfiguring hierarchy associations.
- **Updating contact details (such as email or status)**: Contact detail updates flow through to hierarchy-based access evaluation and storefront authentication.
 
This alignment helps ensure that user status remains consistent across organization accounts, customer hierarchies, and Commerce channels.
 
### Why hierarchy-based user management matters
 
Managing users from the customer hierarchy provides several benefits:
 
- **Centralized control**: Administrators manage access from a single, authoritative structure.
- **Immediate effect**: Enable and disable actions take effect without more configuration.
- **Audit-friendly**: Reasons for access changes are captured and preserved.
- **Scalable administration**: Organizations can manage many users and outlets without duplicating effort.
 
## Call center scenarios
 
B2B multioutlet support extends to assisted selling capabilities in Commerce. It improves how customer service users identify and work with individual buyers who place orders on behalf of an organization.
 
These enhancements improve auditability and operational clarity, without changing the organization-centric transaction model.
 
### Enhancements to the Customer Service form
 
With B2B multioutlet support enabled, the **Customer Service** form supports associating a *contact* with a sales order.
 
- The *organization account* remains the customer for the order.
- The *contact* represents the individual who places or requests the order.
- Contact association is optional and is used for identification, auditing, and support.
 
This enhancement helps customer service users distinguish between the organization and the contact who acted on behalf of the organization.
 
### Associate a contact with a sales order
 
When creating or reviewing a sales order in customer service:
 
- A **Contact** field is available on the sales order.
- Customer service users can select a contact who is associated with the organization through the customer hierarchy.
- The selected contact is stored on the order as a reference that indicates who placed or requested the order.
 
For orders that originate from the storefront, the system populates the contact reference automatically.
 
### Call center behavior for disabled or inactive contacts
 
Contact association is governed by the contact’s active status in the organization and customer hierarchy.
 
#### Only active contacts can create new sales orders
 
- Only active contacts that are associated with the selected organization can be associated with new sales orders.
- If a contact is disabled or inactive for the organization:
  - The contact doesn't appear as a selectable option.
  - The contact can't be associated with the order.
 
This behavior helps ensure that only authorized and active users are linked to new transactions.
 
#### Existing orders and historical data remain unchanged
 
- If a contact becomes inactive after placing an order:
  - The existing sales order remains unchanged.
  - The contact reference is retained for auditing and reporting.
- Historical orders continue to show the original contact, even if the contact is no longer active.
 
This behavior preserves transaction history while enforcing current access rules.
 
#### Customer service users can create orders when contacts are inactive
 
If all contacts for an organization are inactive:
 
- Customer service users can still create sales orders by using the organization account.
- No contact is associated with the order unless an active contact is available.
 
This approach supports business continuity while maintaining access controls.
 
#### Design benefits
 
This design balances flexibility and governance:
 
- **Security**: Prevents inactive or unauthorized users from being linked to new transactions.
- **Auditability**: Maintains a clear record of who placed historical orders.
- **Operational clarity**: Separates organizational ownership of orders from individual responsibility.
- **Consistency**: Applies the same access rules across storefront and call center scenarios.
 
## Storefront experiences
 
For the current state of this feature, the storefront supports:
 
- Organization selection at sign-in, with the option to change the selected organization after sign-in for users with multioutlet access.
- Pricing, catalogs, and checkout behavior based on the selected outlet.
- Persistent shopping carts when switching organizations.
- Role-based order history visibility.
 
> [!NOTE]
> For the current state of this feature, order templates are scoped at the contact level. Organization-level templates are planned for a future release.
 
## Call center and customer service experiences
 
B2B multioutlet support enhances assisted selling scenarios, which helps customer service users:
 
- Identify which contact placed an order.
- Search for orders by contact across one or more outlets.
- Create orders on behalf of a contact while respecting outlet access rules.
 
Only active contacts associated with the selected organization can be assigned to new orders. If a contact is inactive, customer service can still create the order by using the organization account. However, the contact can't be associated with the order.
 
## Enable the B2B multioutlet feature
 
The **B2B Multi-Outlet Ordering with Contact-Based Access** feature is available for preview starting with Commerce version 10.0.47.

To configure multioutlet and contact-based B2B customer hierarchies, follow these steps:
 
1. In Commerce headquarters, go to the **Feature management** workspace (**System administration > Workspaces > Feature management**).
1. Enable the **B2B Multi-Outlet Ordering with Contact-Based Access** feature.
1. Run the **1110 CDX job**.
 
> [!NOTE]
> This preview feature is recommended for new B2B channel implementations only, without existing B2B users in the system. A future release includes migration options for existing B2B organization and user configurations.
 
## Configure multioutlet organizations
 
At a high level, administrators set up multioutlet organizations by:
 
- Creating or onboarding organization accounts.
- Creating contacts to represent users.
- Linking contacts to organizations by using customer hierarchies.
- Assigning roles, catalogs, and channels.
- Enabling contacts for storefront access.
- Synchronizing data to Commerce by using CDX jobs.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
