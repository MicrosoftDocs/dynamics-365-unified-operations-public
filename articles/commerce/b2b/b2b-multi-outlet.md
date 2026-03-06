---
title: B2B multioutlet capabilities (preview)
description: Learn about the key features and benefits of native business-to-business (B2B) multioutlet capabilities in Microsoft Dynamics 365 Commerce.
author: Jcava-Evenica
ms.date: 02/11/2026
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
 
Native business-to-business (B2B) multioutlet capabilities in Microsoft Dynamics 365 Commerce let one signed-in user place orders for multiple associated Organizations or outlets. This approach reduces duplicate setup and aligns the online buying experience with common B2B operating models where buyers purchase on behalf of more than one branch or purchasing entity.
 
## What is B2B multioutlet support?
 
B2B multioutlet support lets a single business user—represented as a **contact**—access and place orders for multiple Organizations/outlets in the same B2B online channel.
 
Key characteristics include:
 
- **Single sign-in identity**: A user signs in once by using one storefront identity.
- **Organization-based purchasing context**: Pricing, catalogs, addresses, credit limits, and fulfillment rules are defined per Organization/outlet.
- **Contact-based access model**: A contact is associated with one or more Organizations through **Customer hierarchies**.
- **Context-aware ordering**: The active Organization/outlet determines pricing, inventory, and checkout behavior.
 
When a contact has access to more than one Organization, the storefront can prompt the user to choose the Organization/outlet to shop for. Users can switch between available Organizations during a session.
 
## Why B2B multioutlet support matters
 
Many B2B Organizations operate through multiple purchasing locations (for example, branches, stores, or outlets). Often, the same group of buyers places orders for more than one location, while commercial rules such as pricing, catalogs, credit limits, and fulfillment options vary by purchasing entity.
 
B2B multioutlet support helps by separating **user identity** from **purchasing context**, which supports:
 
- **Scalability** as Organizations add outlets and buyers.
- **Operational efficiency** by reducing duplicate records and configuration.
- **A streamlined buyer experience** by removing the need for multiple sign-ins.
 
## How this differs from traditional B2B commerce models
 
Traditional implementations often enforce a one-to-one relationship between a buyer’s online identity and a purchasing account. As Organizations grow, this can lead to:
 
- **Multiple user accounts for the same person**, one per outlet or purchasing account.
- **Duplicate pricing and catalog configuration** across many buyer records.
- **Fragmented order history**, where purchasing activity is spread across multiple buyer accounts instead of being consolidated at the Organization level.
 
B2B multioutlet support addresses these issues by using a contact identity model and an Organization-centric transaction model.
 
## What changes with B2B multioutlet support?
 
B2B multioutlet support introduces a model shift:
 
- **Who places the order**: the **contact** (user identity)
- **Which entity is purchasing**: the **Organization/outlet** (purchasing context)
 
This shift affects user management, sales order creation, storefront behavior, and call center experiences.
 
### Users are managed as contacts (not person-type Customer accounts)
 
With B2B multioutlet support:
 
- Each signed-in user is represented as a **contact**.
- A single contact can be associated with one or more Organizations/outlets through **Customer hierarchies**.
- Contacts inherit purchasing rules (pricing, catalogs, credit limits, fulfillment, and channel access) from the active Organization/outlet context.
 
This approach reduces identity duplication and simplifies administration as Organizations add outlets or change staffing.
 
### Organization-based sales order creation (with contact recorded)
 
With B2B multioutlet support enabled:
 
- **Sales orders are created against the Organization account**, represented by the Customer hierarchy.
- The **contact is recorded on the sales order** for auditing and tracking, but the contact doesn’t own the purchasing account.
 
This approach consolidates purchasing activity under the Organization regardless of which contact placed the order.
 
#### Credit controls remain Organization-driven
 
Credit limit evaluation continues to be performed at the **Organization (Customer hierarchy) level**, reflecting total organizational exposure.
 
> [!NOTE]
> Credit limits are evaluated at the Organization (Customer hierarchy) level, not at the individual contact level.
 
## Experiences enabled by B2B multioutlet support
 
### Business partner prospect approval flow updates

The B2B multioutlet feature updates the standard business partner prospect flow to automatically create a Contact associated with the new Organization instead of a "person" type Customer account and link it to a Customer Hierarchy with no additional configuration changes required.
 
### Manage user access through Customer hierarchies in D365 Finance and Operations
 
Customer hierarchies are the primary control point for managing B2B multioutlet access. Administrators use Customer hierarchies to associate contacts with Organizations/outlets and manage their access.
 
Common administration actions include:
 
- **Associate contacts** to an Organization/outlet by adding them to the Customer hierarchy.
- **Assign roles** (Administrator or User) at the hierarchy level to control permissions.
- **Enable/Disable access** for a contact (without removing historical associations).
 
Associating Contacts using the Customer hierarchy has the same effect as associating them through the Organization account. It provides consistent access behavior, regardless of where an administrator makes the change. This alignment helps ensure that user status remains consistent across Organization accounts, Customer hierarchies, and Commerce channels.
 
#### Disable contacts while preserving audit history
 
When an administrator disables a contact in the Customer hierarchy:
 
- The contact loses B2B e-commerce storefront access for the selected Organization/outlet.
- Call center customer service agents can no longer create sales orders or place orders on behalf of the disabled contact via the B2B e-commerce storefront.
- The association remains for auditing and reporting.
- Existing orders and historical transactions remain unchanged.
 
 
Contacts who placed orders can’t be fully removed from the hierarchy; disabling access helps maintain governance while preserving transaction history.
 
#### Capture a reason when disabling access
 
When a contact is disabled, administrators are prompted to enter a reason (for example, role change, temporary suspension, or the user left the Organization). This reason is stored for auditing and operational visibility.
 
### Storefront experiences for multioutlet users
 
For users who can act on behalf of multiple Organizations/outlets:
 
- After sign-in, the storefront determines which Organizations/outlets the contact can access.
- If multiple Organizations/outlets are available, the user can select the active Outlet purchasing context.
- Pricing, catalogs, inventory availability, and checkout behavior update based on the selected Organization/outlet.
- The storefront indicates the active purchasing context based on the selected Outlet.
- Each Organization/outlet has its own shopping cart, which helps keep purchasing context consistent.
 
#### Prospect workflow and sign-in for contact-based users
 
When the B2B multioutlet feature is enabled, the business partner sign-up process allows for new B2B prospects to be submitted and processed with approval. The new contact-based user can then use the storefront sign-up process to gain access to the storefront.
 
#### Organization-level orders and order templates
 
Order history visibility and order templates are available at the **Organization** level so that users associated with the same organization can access shared purchasing history and templates.
 
> [!NOTE]
> For the current state of this feature, order templates and order history are only scoped at the Organization level. User-level templates and order history are planned for a future release.
 
### Contact-aware call center experiences
 
B2B multioutlet support extends to assisted selling in Commerce by improving how customer service users identify and work with individual buyers.
 
With B2B multioutlet support enabled:
 
- The **Organization account** remains the customer for the sales order.
- A **Contact** field can be used to associate the individual who placed or requested the order.
- For storefront-originated orders, the system can populate the contact reference automatically.

#### Updated contact-based customer search option

Updated options within the customer service form are available to search for a specific contact in the system through various identifying information. Once a contact is found, their related Organization(s) are available to select from to create a new order, or review previously placed orders that are connected with that contact. The existing option to search by Organization is available as well, with updates to the user interface for related contact information.
 
#### Behavior for inactive contacts
 
- Only **active** contacts associated with the selected Organization/outlet can be used on new sales orders.
- If a contact becomes inactive after placing an order, the existing order remains unchanged and retains the contact reference.
- If all contacts are inactive, customer service users can still create sales orders by using the Organization account, without associating a contact.
 
## Enable the B2B multioutlet feature
 
The **B2B Multi-Outlet Ordering with Contact-Based Access** feature is available for preview starting with Commerce version 10.0.47.
 
To enable it:
 
1. In Commerce headquarters, go to **Feature management** (**System administration > Workspaces > Feature management**).
1. Enable **B2B Multi-Outlet Ordering with Contact-Based Access**.
1. Run the **1110 CDX job**.
 
> [!NOTE]
> This preview feature is recommended for new B2B channel implementations only, without existing B2B users in the system. Once enabled, this feature can't be disabled.
 
## Configure multioutlet Organizations (high level)
 
At a high level, administrators set up multioutlet Organizations by:
 
- Creating or onboarding Organization accounts.
- Creating contacts to represent B2B users.
- Linking contacts to one or more Organizations by using Customer hierarchies.
- Assigning roles, catalogs, and channels.
- Enabling contacts for storefront access.
- Synchronizing data to Commerce by using CDX jobs.
 
[!INCLUDE[footer-include](../../includes/footer-banner.md)]
