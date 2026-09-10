---
title: B2B multioutlet capabilities (preview)
description: Learn about the key features and benefits of native business-to-business (B2B) multioutlet capabilities in Microsoft Dynamics 365 Commerce.
author: Jcava-Evenica
ms.date: 09/10/2026
ms.topic: overview
ms.reviewer: mirao
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

This article explains the key features and benefits of native business-to-business (B2B) multioutlet capabilities in Microsoft Dynamics 365 Commerce.

Native business-to-business (B2B) multioutlet capabilities in Dynamics 365 Commerce let one signed-in user place orders for multiple associated organizations or outlets. This approach reduces duplicate setup and aligns the online buying experience with common B2B operating models where buyers purchase on behalf of more than one branch or purchasing entity.

When you use native business-to-business (B2B) multistore capabilities in Dynamics 365 Commerce, one signed-in user can place orders for multiple associated organizations or outlets. This approach reduces duplicate setup and aligns the online buying experience with common B2B operating models where buyers purchase on behalf of more than one branch or purchasing entity.

B2B multioutlet support lets a single business user contact access and place orders for multiple organizations or outlets in the same B2B online channel.

Key characteristics include:

- **Single sign-in identity**: A user signs in once by using one storefront identity.
- **Organization-based purchasing context**: Pricing, catalogs, addresses, credit limits, and fulfillment rules are defined per organization or outlet.
- **Contact-based access model**: A contact is associated with one or more organizations through **Customer hierarchies**.
- **Context-aware ordering**: The active organization or outlet determines pricing, inventory, and checkout behavior.

When a contact has access to more than one organization, the storefront can prompt the user to select the organization or outlet to shop for. Users can switch between available organizations during a session.

## Why B2B multioutlet support matters

Many B2B organizations operate through multiple purchasing locations, such as branches, stores, or outlets. Often, the same group of buyers places orders for more than one location, while commercial rules such as pricing, catalogs, credit limits, and fulfillment options vary by purchasing entity.

B2B multioutlet support separates *user identity* from *purchasing context*, which supports:

- *Scalability* as organizations add outlets and buyers.
- *Operational efficiency* by reducing duplicate records and configuration.
- *A streamlined buyer experience* by removing the need for multiple sign-ins.

## Differences from traditional B2B commerce models

Traditional implementations often enforce a one-to-one relationship between a buyer's online identity and a purchasing account. As organizations grow, one-to-one relationships can lead to:

- *Multiple user accounts for the same person*, one per outlet or purchasing account.
- *Duplicate pricing and catalog configuration* across many buyer records.
- *Fragmented order history*, where purchasing activity is spread across multiple buyer accounts instead of being consolidated at the organization level.

B2B multioutlet support addresses these problems by using a contact identity model and an organization-centric transaction model.

## What changes with B2B multioutlet support?

B2B multioutlet support introduces a model shift:

- **Who places the order**: The *contact* (user identity).
- **Which entity is purchasing**: The *organization or outlet* (purchasing context).

This shift affects user management, sales order creation, storefront behavior, and call center experiences.

> [!NOTE]
> Credit limits continue to be evaluated at the organization (customer hierarchy) level, not at the individual contact level.

### Manage users as contacts

With B2B multioutlet support:

- Each signed-in user is represented as a contact (not a person-type customer account).
- You can associate a single contact with one or more organizations or outlets through customer hierarchies.
- Contacts inherit purchasing rules such as pricing, catalogs, credit limits, fulfillment, and channel access from the active organization or outlet context.

This approach reduces identity duplication and simplifies administration as organizations add outlets or change staffing.

### Organization-based sales order creation (with contact recorded)

When you enable B2B multioutlet support:

- You create sales orders against the organization account, which the customer hierarchy represents.
- You record the contact on the sales order for auditing and tracking, but the contact doesn't own the purchasing account.

This approach consolidates purchasing activity under the organization regardless of which contact placed the order.

## Experiences enabled by B2B multioutlet support

### Business partner prospect approval flow updates

The B2B multioutlet feature updates the standard business partner prospect flow to automatically create a contact associated with the new organization instead of a person-type customer account. The system links the contact to a customer hierarchy with no extra configuration changes required.

### Manage user access through customer hierarchies

Customer hierarchies are the primary control point for managing B2B multioutlet access. Administrators use customer hierarchies to associate contacts with organizations or outlets and manage their access.

Common administration actions include:

- Associate contacts with an organization or outlet by adding them to the customer hierarchy.
- Assign roles (admin or user) at the hierarchy level to control permissions.
- Enable or disable access for contacts, without removing historical associations.

Associating contacts using the customer hierarchy has the same effect as associating them through the organization account. It provides consistent access behavior regardless of where an administrator makes the change. This alignment helps ensure that user status remains consistent across organization accounts, customer hierarchies, and Commerce channels.

#### Disable contacts while preserving audit history

When an administrator disables a contact in the customer hierarchy:

- The contact loses B2B e-commerce storefront access for the selected organization or outlet.
- Call center customer service agents can no longer create sales orders or place orders on behalf of the disabled contact via the B2B e-commerce storefront.
- The association remains for auditing and reporting.
- Existing orders and historical transactions remain unchanged.

Contacts who placed orders can't be fully removed from the hierarchy. Disabling access helps maintain governance while preserving transaction history.

#### Capture a reason when disabling access

When a contact is disabled, administrators are prompted to enter a reason (for example, role change, temporary suspension, or the user left the organization). This reason is stored for auditing and operational visibility.

### B2B permission groups

In B2B businesses, different individuals might handle the ordering process. Currently, B2B users have only two roles, which can limit customers and increase operational risk. So, define permission groups as sets of access configurations that you can maintain and assign through Commerce headquarters.

This functionality is part of the multioutlet feature and initially includes the default permission groups **Admin** and **User** for backward compatibility. You can edit these groups to fit your business needs, and create and assign more roles as needed. You can also assign a default permission group when you create users in the storefront to provide a controlled and consistent experience.

You can also extend the permission group model to accommodate unique and complex business needs for user access.

### Storefront experiences for multioutlet users

For users who can act on behalf of multiple organizations or outlets, the following storefront experiences apply:

- After sign-in, the storefront determines which organizations or outlets the contact can access.
- If multiple organizations or outlets are available, the user can select the active outlet purchasing context.
- Pricing, catalogs, inventory availability, and checkout behavior update based on the selected organization or outlet.
- The storefront indicates the active purchasing context based on the selected outlet.
- Each organization or outlet has its own shopping cart, which helps keep purchasing context consistent.

#### Prospect workflow and sign-in for contact-based users

When you enable the B2B multioutlet feature, the business partner sign-up process accepts new B2B prospects and processes their approval. The new contact-based user can then use the storefront sign-up process to gain access to the storefront.

#### Order history enhancements

Order history fully supports the display of contact-based orders through automatic filtering of a user's own orders on the page and user labeling on orders, so it's clear who is responsible for each order listed. Administrator-level users who have access to multiple organizations can see all the orders by selecting a new option on the order history page. When using this feature, the updated order history with search and filter options is also supported.

#### Order template enhancements

Order templates are contact aware with this feature and administrator-level users can share order templates across their organization. This feature lets other users use their work, while also protecting the original creator's template by not allowing edits to the shared order template by anyone other than the original order template creator. Clear user labeling on order templates is available to help distinguish who created each order template and if it's a shared order template or not. More filtering options are also available to help users see only their order templates, or include shared order templates too.

#### Invoice enhancements

Invoices have built-in filtering to support contact users, with users having the ability to see and pay invoices attached to their placed orders. Administrator-level users can see and pay any invoice for a given organization.

#### Wishlist enhancements

Wishlists are contact aware with this feature, letting each user maintain their own wishlist for an organization.

#### Expanded B2B indirect workflows to use contact-based users

Distributors can use a single set of credentials for multiple B2B buyer and seller organizations through the same process using customer hierarchies that B2B buyer organizations have access to. The channel assignment functionality through the customer hierarchy works with this feature, aligning organizations with the correct list of distributor (direct or indirect) options on the B2B website.

#### Account manager access to contact-based users through on behalf of (OBO) capabilities

OBO-enabled sales representatives or account managers can select contact-based users in their assigned organizations to act on behalf of those contacts and access the same controls. The OBO user can then switch between organizations and users within the same session, with the website dynamically updating products, distributor options, pricing, and more. Also, clear labeling on orders and order templates created through OBO includes the representative's or account manager's name and the selected contact's name. Adding or removing access to an organization is as simple as assigning the appropriate sales group to the organization account. OBO users can authenticate by using their Commerce headquarters credentials through a separate sign-in option on the B2B website.

#### Contact-based organization users module

The organization users module provides tools to help organizations manage employees who need storefront access without requiring customer service assistance. You can use it to create new contacts or disable existing contacts under the currently selected organization, along with their associated customer hierarchy.

After you create a new storefront-created user by using the **Organization Users** page, and after processing the **P-0001** and **Synchronize customers and channel requests** jobs, you can complete the same storefront registration steps that are needed for headquarters-created users. Contact users who are deactivated from the storefront require the same jobs to run before the change takes effect. A system-populated deactivation reason is also set to maintain consistency with the headquarters deactivation process.

A default permission group (initially, **User**) is automatically assigned to contact users created through the storefront. If you need additional permissions for a user, use the existing Commerce headquarters user creation and update steps.

#### Updates to requesting invoices and statements

Additional options are available to users to help with sending invoice and account balance information to other contacts configured in Headquarters. Email contacts assigned to the organization and current contact user (as well as the contact on an invoice, where applicable) are available from these areas in the account management suite of modules.

### Contact-aware call center experiences

B2B multioutlet support extends to assisted selling in Commerce by improving how customer service users identify and work with individual buyers.

When you enable B2B multioutlet support:

- The organization account remains the customer for the sales order.
- You can use a contact field to associate the individual who placed or requested the order.
- For storefront-originated orders, the system can populate the contact reference automatically.

#### Updated contact-based customer search option

Updated options within the customer service form are available to search for a specific contact in the system through various identifying information. When you find a contact, you can select from their related organizations to create a new order or review previously placed orders that are connected with that contact. The existing option to search by organization is available as well, with updates to the user interface for related contact information.

#### Behavior for inactive contacts

- You can use only active contacts associated with the selected organization or outlet on new sales orders.
- If a contact becomes inactive after placing an order, the existing order remains unchanged and retains the contact reference.
- If all contacts are inactive, customer service users can still create sales orders by using the organization account, without associating a contact.

## Enable the B2B multioutlet feature

The B2B multioutlet ordering with contact-based access feature is available starting with Commerce release version 10.0.48.

> [!NOTE]
> You can't reverse this migration or disable the feature after you enable it. So, test it in a nonproduction environment.

To enable the feature, follow these steps:

1. In Commerce headquarters, go to **Feature management** (**System administration** > **Workspaces** > **Feature management**).
1. Search for and enable the **B2B Multi-Outlet Ordering with Contact-Based Access** feature.
1. Run the **Migrate B2B Multi-Outlet Customers** batch job (**Retail and Commerce** > **Retail and Commerce IT**). This step is mandatory for environments with existing B2B customers.
1. Run the Commerce Data Exchange (CDX) **1010 (Customers)** job.

## Import customer hierarchies and contacts

After you enable this feature, use the following entities to import customer hierarchies and contacts from different data sources and file formats by using data management:

- **Customer hierarchies**: Use the **Customer Hierarchies (CustomerHierarchyEntity)** entity to import customer hierarchies that are associated with specific organization accounts. Populate the organization's party ID in the **ORGANIZATIONPARTYNUMBER** field, along with other required entity data.
- **Contacts**: Use the **Contacts V2 (smmContactPersonV2Entity)** entity to import users under specific organization accounts. Populate the organization's party ID in the **ASSOCIATEDPARTYNUMBER** field, along with other required entity data. These contacts are automatically associated with the customer hierarchy through the link between contacts under the organization account and those listed in the customer hierarchy.

## Existing B2B customer migration

To enable this feature, run a one-time batch job that migrates existing B2B customers, B2B2B channels (distributors), and OBO configurations and users. This batch job is part of the activation process. The batch job, **Migrate B2B Multi-Outlet Customers**, is located under **Retail and Commerce** > **Retail and Commerce IT**. This batch job performs the following steps:

1. Finds all organization-type customers attached to a customer hierarchy.
1. Creates a contact under the organization for each person-type customer attached to the customer hierarchy. This contact uses the same Party ID as the person-type account for traceability.
1. Attaches the existing authentication details as part of the pairing process to the new contacts.
1. Assigns the same role (Admin or User) to the new contacts.

After these steps are completed and the updated configurations and data are available to the website through the CDX **1010 (Customers)** job, existing users can sign in by using their existing credentials and use the website.

## More resources

- [B2B multioutlet configuration](b2b-multi-outlet-configuration.md)
- [B2B indirect workflows](b2b-indirect.md)
- [Enable on behalf of (OBO) functionality](../on-behalf-of.md)
- [Order history with search and filters module](../order-history-module.md)
- [Invoice management for B2B e-commerce websites](invoice-management.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
