---
title: B2B multioutlet capabilities
description: Learn about the key features and benefits of native business-to-business (B2B) multioutlet capabilities in Microsoft Dynamics 365 Commerce.
author: Jcava-Evenica
ms.date: 03/13/2026
ms.topic: overview
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: v-jcavataio
ms.search.validFrom: 2021-01-31
ms.search.form: RetailOperations
ms.custom:
  - bap-template
---
 
# B2B multioutlet capabilities
 
[!INCLUDE [banner](../../includes/banner.md)]

This article explains the key features and benefits of native business-to-business (B2B) multioutlet capabilities in Microsoft Dynamics 365 Commerce.

Native business-to-business (B2B) multioutlet capabilities in Dynamics 365 Commerce let one signed-in user place orders for multiple associated organizations or outlets. This approach reduces duplicate setup and aligns the online buying experience with common B2B operating models where buyers purchase on behalf of more than one branch or purchasing entity.
 
## B2B multioutlet support
 
B2B multioutlet support lets a single business user contact access and place orders for multiple organizations or outlets in the same B2B online channel.
 
Key characteristics include:
 
- **Single sign-in identity**: A user signs in once by using one storefront identity.
- **Organization-based purchasing context**: Pricing, catalogs, addresses, credit limits, and fulfillment rules are defined per organization or outlet.
- **Contact-based access model**: A contact is associated with one or more organizations through **Customer hierarchies**.
- **Context-aware ordering**: The active organization or outlet determines pricing, inventory, and checkout behavior.
 
When a contact has access to more than one organization, the storefront can prompt the user to select the organization or outlet to shop for. Users can switch between available organizations during a session.
 
## Why B2B multioutlet support matters
 
Many B2B organizations operate through multiple purchasing locations (for example, branches, stores, or outlets). Often, the same group of buyers places orders for more than one location, while commercial rules such as pricing, catalogs, credit limits, and fulfillment options vary by purchasing entity.
 
B2B multioutlet support helps by separating *user identity* from *purchasing context*, which supports:
 
- *Scalability* as organizations add outlets and buyers.
- *Operational efficiency* by reducing duplicate records and configuration.
- *A streamlined buyer experience* by removing the need for multiple sign-ins.
 
## Differences from traditional B2B commerce models
 
Traditional implementations often enforce a one-to-one relationship between a buyer's online identity and a purchasing account. As organizations grow, one-to-one relationships can lead to:
 
- *Multiple user accounts for the same person*, one per outlet or purchasing account.
- *Duplicate pricing and catalog configuration* across many buyer records.
- *Fragmented order history*, where purchasing activity is spread across multiple buyer accounts instead of being consolidated at the organization level.
 
B2B multioutlet support addresses these issues by using a contact identity model and an organization-centric transaction model.
 
## What changes with B2B multioutlet support?
 
B2B multioutlet support introduces a model shift:
 
- **Who places the order**: The *contact* (user identity).
- **Which entity is purchasing**: The *organization or outlet* (purchasing context).
 
This shift affects user management, sales order creation, storefront behavior, and call center experiences.

> [!NOTE]
> Credit limits continue to be evaluated at the organization (customer hierarchy) level, not at the individual contact level.
 
### Users are managed as contacts
 
With B2B multioutlet support:
 
- Each signed-in user is represented as a contact (not a person-type customer account).
- A single contact can be associated with one or more organizations or outlets through customer hierarchies.
- Contacts inherit purchasing rules such as pricing, catalogs, credit limits, fulfillment, and channel access from the active organization or outlet context.
 
This approach reduces identity duplication and simplifies administration as organizations add outlets or change staffing.
 
### Organization-based sales order creation (with contact recorded)
 
With B2B multioutlet support enabled:
 
- Sales orders are created against the organization account, represented by the customer hierarchy.
- The contact is recorded on the sales order for auditing and tracking, but the contact doesn't own the purchasing account.
 
This approach consolidates purchasing activity under the organization regardless of which contact placed the order.
 
## Experiences enabled by B2B multioutlet support
 
### Business partner prospect approval flow updates

The B2B multioutlet feature updates the standard business partner prospect flow to automatically create a contact associated with the new organization instead of a person-type customer account. The system links the contact to a customer hierarchy with no additional configuration changes required.
 
### Management of user access through customer hierarchies
 
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
 
### Storefront experiences for multioutlet users
 
For users who can act on behalf of multiple organizations or outlets, the following storefront experiences apply:
 
- After sign-in, the storefront determines which organizations or outlets the contact can access.
- If multiple organizations or outlets are available, the user can select the active outlet purchasing context.
- Pricing, catalogs, inventory availability, and checkout behavior update based on the selected organization or outlet.
- The storefront indicates the active purchasing context based on the selected outlet.
- Each organization or outlet has its own shopping cart, which helps keep purchasing context consistent.
 
#### Prospect workflow and sign-in for contact-based users
 
When the B2B multioutlet feature is enabled, the business partner sign-up process allows for new B2B prospects to be submitted and processed with approval. The new contact-based user can then use the storefront sign-up process to gain access to the storefront.
 
#### Organization-level orders and order templates
 
Order history visibility and order templates are available at the organization level so that users associated with the same organization can access shared purchasing history and templates.
 
> [!NOTE]
> Currently, order templates and order history are only scoped at the organization level. User-level templates and order history are planned for a future release.
 
### Contact-aware call center experiences
 
B2B multioutlet support extends to assisted selling in Commerce by improving how customer service users identify and work with individual buyers.
 
With B2B multioutlet support enabled:
 
- The organization account remains the customer for the sales order.
- A contact field can be used to associate the individual who placed or requested the order.
- For storefront-originated orders, the system can populate the contact reference automatically.

#### Updated contact-based customer search option

Updated options within the customer service form are available to search for a specific contact in the system through various identifying information. Once a contact is found, their related organizations are available to select from to create a new order, or review previously placed orders that are connected with that contact. The existing option to search by organization is available as well, with updates to the user interface for related contact information.
 
#### Behavior for inactive contacts
 
- Only active contacts associated with the selected organization or outlet can be used on new sales orders.
- If a contact becomes inactive after placing an order, the existing order remains unchanged and retains the contact reference.
- If all contacts are inactive, customer service users can still create sales orders by using the organization account, without associating a contact.
 
## Enable the B2B multioutlet feature
 
The **B2B Multi-Outlet Ordering with Contact-Based Access** feature is available for preview starting with Commerce version 10.0.47.
 
To enable the feature, follow these steps:
 
1. In Commerce headquarters, go to **Feature management** (**System administration > Workspaces > Feature management**).
1. Search for and enable the **B2B Multi-Outlet Ordering with Contact-Based Access** feature.
1. Run the Commerce Data Exchange (CDX) **1010 (Customers)** job.
 
> [!NOTE]
> - The preview feature is only recommended for new B2B channel implementations without existing B2B users in the system.
> - Once enabled, this feature can't be disabled.

## Additional resources

[B2B multioutlet configuration](b2b-multi-outlet-configuration.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
