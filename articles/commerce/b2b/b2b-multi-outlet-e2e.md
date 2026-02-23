---
title: B2B multioutlet capabilities (preview)
description: Learn about the key features and benefits of native business-to-business (B2B) multioutlet capabilities in Microsoft Dynamics 365 Commerce.
author: Jcava-Evenica
ms.date: 02/06/2026
ms.topic: overview
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: v-jcavataio
ms.search.validFrom: 2021-01-31
ms.search.form: RetailOperations
ms.custom: 
  - bap-template
---
#  End to End experiences/Configuration Steps
## User Management
### B2B Organization Account Set Up  Prospect flows
B2B organization onboarding begins when a B2B Buyer prospect is approved. 
#### B2B Buyer prospect approval flow
When a B2B buyer prospect is approved, the following entities and relationships are established:
-	**Create Customer record of the Organization type**
 An organization account is created to represent the B2B organization and assigned to the attached online channel’s address book.
- **Create contact under Customer record** 
A contact is created under the Customer record. This contact replaces the traditional person-type Customer record model and represents the initial user for the organization. The contact is also added to the attached online channels address book.
- **Create customer hierarchy and link to Customer record** 
A customer hierarchy is created and linked to the Customer record.
1. The hierarchy is configured as a B2B buyer hierarchy.
1. The organization name is used as the hierarchy name.
-	**Link initial contact to customer hierarchy as admin**
 The initial contact is linked to the customer hierarchy and designated as the hierarchy administrator, enabling access to additional functions on the storefront.
 #### Subsequent Commerce configuration context
After the automated onboarding flow completes, additional Commerce configurations may be applied, including:
- Assignment of product catalogs
- Configuration of user roles
-	Maintenance of channel assignments at the customer hierarchy level
- Synchronization of data using Commerce Data Exchange (CDX) jobs
These steps support the organizations readiness for B2B eCommerce operations across channels.

- #### Complete the setup for B2B channel availability
After the organization account and customer hierarchy are created, complete the following steps to make the organization and its users available on one or more B2B channels.

#### Assign a catalog (if applicable)
Catalog assignment controls the products that are available to users of the B2B organization in the storefront.
1.	Open the relevant customer hierarchy.
2.	In the Catalogs section, select Add line.
3.	Select the appropriate catalog.

- ***Note***
Catalog assignment is optional and depends on how assortments are managed in your Dynamics 365 Commerce environment.

- #### Link contacts to the customer hierarchy
Contacts represent individual users who can access the storefront on behalf of the organization.
1.	In the Hierarchy section, select Add.
2.	From the list, select the contact to link.
3.	Select Select.

- ***Behavior***
-	The list shows all contacts that are available to be linked to the customer hierarchy.
-	In prospect-based onboarding flows, the initial contact is already linked and assigned the Admin role.
-	If a selected contact does not exist under the linked organization account, a new contact is created under that organization and will reflect any updates made to any instance of that contact.


- #### Enable the contact for storefront access
A contact must be enabled before the user can sign in to the B2B storefront.
1.	Select the contact in the Hierarchy grid.
2.	Select Enable.

- ***Important***
Only enabled contacts can sign in and access the storefront. Contacts that are linked but not enabled cannot place orders or view organization data.

- #### Assign or update the contact role (if applicable)
Roles determine the permissions that a contact has within the organization.
1.	Select the contact in the Hierarchy grid.
2.	Select Change role.
3.	Assign one of the following roles:
- Admin
- User

- ***Note***
At least one contact must be assigned the Admin role for each customer hierarchy.

- #### Assign retail channels (if applicable)
Retail channel assignment determines if only specific B2B channels are available to the organization.
1.	In the Retail channels section, select Add.
2.	Select the channels that should be available to the customer hierarchy.

- ***Note***
If no retail channels are assigned, the customer hierarchy can operate with any available channel in the same legal entity.

- #### Complete organization account configuration (if applicable)
Depending on business requirements, additional configuration may be required at the organization account level to ensure the correct purchasing experience in the storefront.
Examples include:
-	Pricing configuration
- Discount assignment
- Other organization-specific purchasing settings

- #### Synchronize data to Commerce
After configuration is complete, synchronize data so that changes are available in the storefront.
1.	Run Commerce Data Exchange (CDX) job 1010 Customers.
The 1010  Customers job synchronizes:
- Organization account data
- Contact records
- Customer hierarchy relationships

- ***Note***
If a B2B Seller/Buyer organization was approved through the prospect flow, additional configuration and synchronization may be required to enable access to the B2B seller channel. Those steps are outside the scope of this article.

- **Result**
After these steps are completed and data synchronization finishes, the organization and its enabled contacts can sign in to the B2B storefront and access the assigned channels, catalogs, and purchasing configuration.

- # B2B Organization Account Set Up Manual 
Manual onboarding is used to enable online access for an existing B2B organization by creating and linking a customer hierarchy to that organization. This process is performed primarily on the Customer hierarchies page in Finance and Operations.

A key requirement of this process is that at least one contact must be selected and assigned as an administrator for the customer hierarchy. The contact can exist under the linked organization account or under another organization account.

- **Before you begin**
Before starting manual onboarding, ensure that:
- The organization account already exists.
- At least one contact exists with a valid email address.
- You understand whether the hierarchy should be created as a B2B buyer or B2B seller hierarchy.

- ## Step 1: Create a contact (if required)
An organization must have at least one contact available to establish an initial administrator for the customer hierarchy.
-	If no contact exists, create a contact under the organization account.
-	The contact must have a valid email address to support storefront access.

- ***Note***
The selected contact will become the initial Admin for the customer hierarchy.

- ## Step 2: Create a customer hierarchy
Customer hierarchies define how organizations and users are structured for B2B commerce.
1.	Go to Retail and Commerce > Customers > Customer hierarchies.
2.	Select New.

- ***Note***
The hierarchy type determines additional system behavior. For B2B seller hierarchies, contacts may also have employee records created, and additional seller-specific steps apply.
If a B2B Seller customer hierarchy is required, the Promote to seller button can be selected on the customer hierarchy form. Additional seller setup steps are required, for more information, please see the B2B Indirect Workflows article.

- ## Step 3: Link the customer hierarchy to an organization account
After selecting the hierarchy type:
1.	Enter a name for the customer hierarchy.
2.	In the Organization field, select the appropriate organization account from the dropdown list.
Linking the organization establishes the commercial context that will be used by all users associated with the hierarchy.

- ## Step 4: Select the initial admin contact (required)
When linking an organization during manual hierarchy creation, the system requires selection of an initial administrator.
- A prompt appears to select the initial admin contact.
- The selection list includes active contacts from the selected organization that have email addresses.


- ***Important***
Selecting an initial admin contact is required to save the customer hierarchy.
If the prompt is canceled, the organization is not linked and the hierarchy cannot be saved.

- ## Step 5: Automatically link additional contacts as users
After the initial admin contact is selected:
- Any remaining eligible contacts associated with the organization are automatically linked to the customer hierarchy.
- These contacts are assigned the User role by default.
This reduces the need for manual user linking during initial setup.

- ## Step 6: Enable contacts for storefront access (required)
Contacts must be enabled to access the B2B storefront.
1.	In the Hierarchy grid, select the contact.
2.	Select Enable.

- ***Important***
Only enabled contacts can sign in to the storefront.
The enable and disable controls take effect after the data has been synchronized through Commerce Data Exchange (CDX) job 1010 – Customers  and are used to control site access.

- ## Step 7: Assign catalogs (if applicable)
Catalog assignment determines which products are available to users in the storefront.
1.	In the Catalogs section of the customer hierarchy, select Add line.
2.	Select the appropriate catalog.

- ***Note***
Catalog assignment is optional and depends on how assortments are managed in your environment.

- ## Step 8: Assign or update contact roles (if applicable)
Roles control what users can see and manage in the storefront.
1.	Select a contact in the Hierarchy grid.
2.	Select Change role.
3.	Assign one of the following roles:
- Admin
- User

- ***Note***
At least one contact must remain assigned the Admin role for each customer hierarchy.

- ## Step 9: Assign retail channels (if applicable)
Retail channel assignment controls which B2B channels are available to the organization.
1.	In the Retail channels section, select Add.
2.	Select the appropriate retail channels.

- ***Note***
If no retail channels are assigned, the customer hierarchy can operate with any available channel within the same legal entity.

- ## Step 10: Perform additional organization account configuration (if applicable)
Depending on business requirements, additional configuration may be required at the organization account level to ensure correct storefront behavior.
Examples include:
- Pricing configuration
- Discount assignment
- Other organization-specific purchasing settings

- ## Step 11: Synchronize data to Commerce
After completing setup, synchronize data so that changes are available in the storefront.
1.	Run Commerce Data Exchange (CDX) job 1010 Customers.
The 1010 Customers job synchronizes:
- Organization account data
- Contact records
- Customer hierarchy relationships

- ***Note***
If a B2B Seller/Buyer organization was approved through the prospect flow, additional configuration and synchronization is required to enable access to the B2B seller channel. Please refer to the B2B indirect Workflows article for more information.

- **Result**
After these steps are completed and data synchronization finishes, the existing organization and its enabled contacts can sign in to the B2B storefront and access the assigned channels, catalogs, and purchasing configurations.

- ### User Management D365 F&O

This section describes how contacts are managed for B2B online access in Dynamics 365 Commerce using Finance and Operations. 
All user-related changes are synchronized to the Commerce storefront by running Commerce Data Exchange (CDX) job 1010 Customers.


- **Update role assignment for a contact**
Roles control the level of access a contact has for a specific organization.
To update a contact role
1.	Go to Retail and Commerce > Customers > Customer hierarchies.
2.	Open the relevant customer hierarchy.
3.	In the Hierarchy grid, select the contact.
4.	Select Change role.
5.	Assign one of the following roles:
- Admin
- User

- ***Note***
Each customer hierarchy must have at least one contact assigned the Admin role.

- **Link a contact to another customer hierarchy**
Contacts can be associated with more than one organization by linking them to additional customer hierarchies.

To link a contact to another hierarchy
1.	Go to Retail and Commerce > Customers > Customer hierarchies.
2.	Open the target customer hierarchy.
3.	In the Hierarchy section, select Add.
4.	Select the appropriate contact from the list.
5.	Select Select to confirm.

- **Behavior**
-The selection list displays all contacts available for linking.
-If the selected contact does not exist under the linked organization account, a new contact is created under that organization using the same party ID as the original contact.

- **Remove (delete) a contact link from a customer hierarchy** 
Removing a contact deletes the relationship between the contact and the customer hierarchy.
To remove a contact from a hierarchy
1.	Go to Retail and Commerce > Customers > Customer hierarchies.
2.	Open the relevant customer hierarchy.
3.	In the Hierarchy grid, select the contact.
4.	Select Delete.

- ***Important***
Contacts that have placed one or more orders cannot be removed from the hierarchy.
In these cases, use the Disable contact procedure instead to remove storefront access while preserving audit history.

- **Disable a contact for a specific organization**
Disabling a contact removes storefront access for the organization while keeping the contact and hierarchy relationship intact.
To disable a contact
1.	Go to Retail and Commerce > Customers > Customer hierarchies.
2.	Open the relevant customer hierarchy.
3.	In the Hierarchy grid, select the contact.
4.	Select Disable.
5.	When prompted, enter a reason for disabling the contact.

- ***Note***
- Disabled contacts cannot sign in to the storefront for that organization.
- The Enable/Disable actions on the contact form also update the contacts status in the customer hierarchy.

- **Synchronize changes to the storefront**
After completing any user management changes:
1.	Run CDX job 1010 Customers.
This job synchronizes:
- Contact updates
- Role changes
- Enable/disable status
- Customer hierarchy relationships

- **Result**
After synchronization completes, the updated user access, roles, and organization associations are reflected in the B2B storefront and Customer Service experiences.

## Storefront Experiences
### Storefront Sign Up

The sign-up process allows a contact to create credentials and access the B2B storefront.

- ***Note***
This process assumes that the contact already exists in a synchronized organization account and customer hierarchy. The sign-up process applies to B2B buyer organizations.

- **To sign up from the storefront**
1.	In the storefront header, select Sign in.
2.	Select Sign up now.
3.	Enter the required registration details.
4.	After registration is complete, the user is automatically signed in and connected to the associated organization account.

- **MVP v1- Sign in**
The sign-in process allows existing contacts to access the storefront.
To sign in
1.	In the storefront header, select Sign in.
2.	Enter credentials.
- If required, complete the Forgot password flow to reset credentials.
- After password reset, the user is signed in automatically.


### Select an organization (multi-outlet access)
Contacts who are configured with access to multiple organization accounts can select which organization they want to work with.

- ***Note***
The organization selection module is displayed only for contacts that have access to more than one organization.
To select an organization
1.	Sign in to the B2B storefront.
2.	In the header, use the Select button to choose the preferred organization account.
3.	The selected organization is marked as Selected.
4.	The organization name appears in the My account menu.

Once selected, all storefront elements that depend on organization or customer hierarchy contextsuch as pricing, catalogs, and checkout behavior are updated accordingly.

### Switch organizations during a session
The storefront supports switching between organizations without signing out.
To switch organizations
1.	Open the My account menu.
2.	Select Switch organization.
3.	Choose a different organization from the list.

### Confirmation dialog when changing organizations (MVP1)
When switching organizations, the storefront displays a confirmation dialog.
The dialog explains:
1. That pricing, discounts, and inventory may change
2. That the current shopping cart is preserved
3. That cart items can be restored when switching back to the previous organization

This confirmation ensures that users understand the impact of changing organizational context.

### Catalog visibility and My catalogs
Catalog visibility in the storefront is evaluated based on the active organization and its customer hierarchy configuration.
To review available catalogs
1.	Open the My account menu.
2.	Select My catalogs.
3.	Review the catalogs available for the currently selected organization.

- **Expected outcome**
- When the active organization changes, the available catalogs may also change, depending on hierarchy and channel configuration.

### Call Center (Customer Service) experiences 
### Review contact information on placed orders (MVP1)
Orders placed through the storefront include contact-level tracking.
-	The Contact field appears in the General section of the sales order header.

### Search orders by contact (Contact search) (MVP1)
Customer Service provides a Contact search experience for locating orders associated with a specific contact.
- **Contact search experience** 
1.	Select the Contact search tab.
2.	Choose a search option:
- Contact name
- Contact phone number
- Contact email address

- **Behavior**
- Switching between search tabs resets the search fields and clears the sales order list.
- The Contact Information fast tab displays contact details when the feature is enabled.
- The fast tab appears on other search tabs but is populated only when a sales order with an assigned contact is selected.

- **Organization selection during contact search**
After a contact is selected, an organization selection column is displayed.
1. Multiple organizations selected
- Orders placed by the contact across all selected organizations are shown.
2. Single organization selected
- Customer information is displayed.
3. No single organization selected
- Customer information remains hidden.
The Sales Order fast tab updates dynamically based on the selected contact and organization scope.

### Create orders for a contact in Customer Service (MVP1)
The order creation experience depends on the organization selection made during contact search.
1. Search contact, select all organizations
- The user is prompted to select a single organization before creating the order.
- Only organizations where the contact is active are available for selection.
2. Search contact, select a subset of organizations
- The user is prompted to select a single organization.
- Only organizations where the contact is active are available.
3. Search contact, select a single organization
- The flow proceeds directly to sales order creation.

- ***Note***
If a single organization is selected but the contact is inactive for that organization, the sales order is created with the organization account assigned, but the contact is not associated with the order.


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
 
When each B2B user is treated as a separate customer account, pricing rules and discounts often have to be duplicated across records. The contact model removes this additional configuration step and instead allows any number of contact users at a given organization to be updated at once through the organization's pricing configurations.
 
This duplication increased:
 
- Configuration and maintenance effort.
- Difficulty of managing pricing changes consistently.
- Risk of configuration drift between users attached to the same organization.
 
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
- **Updating contact details (name and status)**: Contact detail updates flow through to hierarchy-based access evaluation and storefront authentication.
 
This alignment helps ensure that user status remains consistent across organization accounts, customer hierarchies, and Commerce channels.
 
### Why hierarchy-based user management matters
 
Managing users from the customer hierarchy provides several benefits:
 
- **Centralized control**: Administrators manage access from a single, authoritative structure.
- **Immediate effect**: Enable and disable actions take effect without more configuration.
- **Audit-friendly**: Reasons for access changes are captured and preserved.
- **Scalable administration**: Organizations can manage many users and outlets without duplicating effort.
 
## Contact‑Aware Call Center Experiences
 
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
 
## Contact-aware eCommerce Storefront experiences
 
### Prospect workflow and standard log in support for contact based users

When the B2B multi-outlet feature is enabled, the business partner sign up feature will instead create a contact for the first B2B user when a prospect is approved. Once the prospect is approved and their contact is created, the new B2B user can sign up using the existing authentication process through the storefront and start shopping immediately. In addition, the standard configuration for logging in and authenticating will operate in a similar manner using contacts as well. 

> [!NOTE]
> This process assumes that the contact already exists in Dynamics 365 Finance and Operations and is associated with an organization through a synchronized customer hierarchy. Registration and Sign-up applies only to B2B buyer organizations for this release.


### Intuitive controls and consistent organization display for multi-outlet B2B users

A B2B user who is associated with more than one organization will be prompted to select which account they would like to shop with upon logging in, and can change between their organizations freely. B2B users who are attached to a single organization have these elements hidden as part of their shopping experience to reduce any confusion when shopping or navigating the different links throughout the storefront. The currently active organization, along with the name of the user is displayed in the header at all times to provide a quick point of reference for the currently selected organization.

### Seamless access to organization based configurations

All pricing, catalog and shopping cart/checkout configurations which would impact an organization's options when searching, filtering or purchasing products is available for contact based users. These elements can change immediately and accurately to reflect the currently active organization for multi-outlet users as well within a single logged in session.  

### Persistent shopping carts when switching organizations

Multi-outlet users are given the freedom to switch between their organizations with their cart in any state, and can pick up where they left off after any number of organization selections.

### Organization level orders and order templates available in the storefront

Organization based order history visibility and order templates are available and allow for all users at a given organization to view orders and use order templates. 
 
> [!NOTE]
> For the current state of this feature, order templates and order history are only scoped at the organization level. User-level templates and order history are planned for a future release.
  
### Uses existing data exchange and batch jobs to operate

Enabling the feature will update all of the impacted download and upload data exhanges appropriately, requiring no additional job scheduling for day to day operations or configuration changes to take effect on the storefront.


## Enable the B2B multioutlet feature
 
The **B2B Multi-Outlet Ordering with Contact-Based Access** feature is available for preview starting with Commerce version 10.0.47.

To configure multioutlet and contact-based B2B customer hierarchies, follow these steps:
 
1. In Commerce headquarters, go to the **Feature management** workspace (**System administration > Workspaces > Feature management**).
1. Enable the **B2B Multi-Outlet Ordering with Contact-Based Access** feature.
1. Run the **1110 CDX job**.
 
> [!NOTE]
> This preview feature is recommended for new B2B channel implementations only, without existing B2B users in the system. This feature cannot be disabled after enabling as well. A future release includes migration options for existing B2B organization and user configurations.
 
## Configure multioutlet organizations
 
At a high level, administrators set up multioutlet organizations by:
 
- Creating or onboarding organization accounts.
- Creating contacts to represent **B2B** users for **organization accounts**.
- Linking contacts to **one or more** organizations by using customer hierarchies.
- Assigning roles, catalogs, and channels.
- Enabling contacts for storefront access.
- Synchronizing data to Commerce by using CDX jobs.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
