---
title: End to End Experiences/Configuration Steps (preview)
description: Learn about End to End Experiences/Configuration steps for native business-to-business (B2B) multioutlet capabilities in Microsoft Dynamics 365 Commerce.
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
# End to End Experiences/Configuration Steps (preview)
[!include [banner](../../includes/banner.md)]
## User management within Dynamics 365 Finance and Operations
### B2B Organization Account Setup - Prospect flow
B2B organization onboarding begins when a B2B Buyer prospect is approved. The following entities and relationships are established:

**Create Customer record of the Organization type** —
 An organization account is created to represent the B2B organization and assigned to the attached online channel’s address book.
 
**Create contact under Customer record** —
A contact is created under the Customer record. This contact replaces the traditional person-type Customer record model and represents the initial user for the organization. The contact is also added to the attached online channels address book.


**Create customer hierarchy and link to Customer record**—A customer hierarchy is created and linked to the Customer record.
- The hierarchy is configured as a B2B buyer hierarchy.
- The organization name is used as the hierarchy name.
        
**Link initial contact to customer hierarchy as admin** —
 The initial contact is linked to the customer hierarchy and designated as the hierarchy administrator, enabling access to extra functions on the storefront.
 

#### Complete the setup for B2B channel availability
After the organization account and customer hierarchy are created, complete the following steps to make the organization and its users available on one or more B2B channels.

#### Assign a catalog (if applicable)
Catalog assignment controls the products that are available to users of the B2B organization in the storefront.
1.	Open the relevant customer hierarchy.
1.	In the Catalogs section, select Add line.
1.	Select the appropriate catalog.

> [!NOTE]
> Catalog assignment is optional and depends on how assortments are managed in your Dynamics 365 Commerce environment.

#### Link contacts to the customer hierarchy
Contacts represent individual users who can access the storefront on behalf of the organization.
1.	In the Hierarchy section, select Add.
1.	From the list, select the contact to link.
1.	Select Select.

 **Behavior**
-	The list shows all contacts that are available to be linked to the customer hierarchy.
-	In prospect-based onboarding flows, the initial contact is already linked and assigned the Admin role.
-	If a selected contact does not exist under the linked organization account, a new contact is created under that organization, reflecting updates made to any instance of that contact.


#### Enable the contact for storefront access
A contact must be enabled before the user can sign in to the B2B storefront.
1.	Select the contact in the Hierarchy grid.
1.	Select Enable.

> [!IMPORTANT]
> Only enabled contacts can sign in and access the storefront. Contacts that are linked but not enabled cannot place orders or view organization data.

#### Assign or update the contact role (if applicable)
Roles determine the permissions that a contact has within the organization.
1.	Select the contact in the Hierarchy grid.
1.	Select Change role.
1.	Assign one of the following roles:
  - Admin
  - User

> [!NOTE]
> At least one contact must be assigned the Admin role for each customer hierarchy.


#### Complete organization account configuration (if applicable)
Depending on business requirements, more configuration may be required at the organization account level to ensure the correct purchasing experience in the storefront.
Examples include:
-	Pricing configuration
- Discount assignment
- Other organization-specific purchasing settings

#### Synchronize data to Commerce
After configuration is complete, synchronize data so that changes are available in the storefront.
Run Commerce Data Exchange (CDX) job 1010 Customers.
The 1010  Customers job synchronizes:

- Organization account data
- Contact records
- Customer hierarchy relationships

> [!NOTE]
> B2B Seller/Buyer organizations are not available to use with this feature and will be included in a future release.

**Result**

Once the data is synchronized, the organization and its enabled contacts can sign in to the B2B storefront.

### Manual B2B Organization Account Setup
Manual onboarding is used to enable online access for an existing B2B organization by creating and linking a customer hierarchy to that organization. This process is performed primarily on the Customer hierarchies page in Finance and Operations.

A key requirement of this process is that at least one contact must be selected and assigned as an administrator for the customer hierarchy. The contact can exist under the linked organization account or under another organization account.

**Before you begin**
Before starting manual onboarding, ensure that:

  1. The organization account already exists.
  1. At least one contact exists with a valid email address.

#### Create a contact (if necessary)
An organization must have at least one contact available to establish an initial administrator for the customer hierarchy. 

  1. If no contact exists, create a contact under the organization account.
  1. The contact must have a valid email address to support storefront access.

> [!NOTE]
> The selected contact becomes the initial Administrator for the customer hierarchy.

#### Create a customer hierarchy
Customer hierarchies define how organizations and users are structured for B2B commerce.
  1.	Go to Retail and Commerce > Customers > Customer hierarchies.
  1.	Select New.


#### Link the customer hierarchy to an organization account
After selecting the hierarchy type:

  1.	Enter a name for the customer hierarchy.
  1.	In the Organization field, select the appropriate organization account from the dropdown list.

#### Select the initial admin contact (required)
When linking an organization during manual hierarchy creation, the system requires selection of an initial administrator.
  1. A prompt appears to select the initial admin contact.
  1. The selection list includes active contacts from the selected organization that have email addresses.


***Important***

Selecting an initial admin contact is required to save the customer hierarchy.
If the prompt is canceled, the organization is not linked and the hierarchy cannot be saved.

#### Automatically link other contacts as users
After the initial admin contact is selected:

  1. Any remaining eligible contacts associated with the organization are automatically linked to the customer hierarchy.
  1. These contacts are assigned the User role by default.
     
This automatic process reduces the need for manual user linking during initial setup.

#### Enable contacts for storefront access (required)
Contacts must be enabled to access the B2B storefront.

  1.	In the Hierarchy grid, select the contact.
  1.	Select Enable.

***Important***

Only enabled contacts can sign in to the storefront.
The enable and disable controls take effect through the Commerce Data Exchange (CDX) job 1010 – Customers and are used to control site access.

#### Assign catalogs (if applicable)
Catalog assignment determines which products are available to users in the storefront.

  1.	In the Catalogs section of the customer hierarchy, select Add line.
  1.	Select the appropriate catalog.

> [!NOTE]
> Catalog assignment is optional and depends on how assortments are managed in your environment.

#### Assign or update contact roles (if applicable)
Roles control what users can see and manage in the storefront.

  1.	Select a contact in the Hierarchy grid.
  1.	Select Change role.
  1.	Assign one of the following roles:
    - Admin
    - User

> [!NOTE]
> At least one contact must remain assigned the Admin role for each customer hierarchy.


#### Perform other organization account configuration (if necessary)
Depending on business requirements, other configuration may be required at the organization account level to ensure correct storefront behavior.

Examples include:

  - Pricing configuration
  - Discount assignment
  - Other organization-specific purchasing settings

#### Synchronize data to Commerce
After completing setup, synchronize data so that changes are available in the storefront.
Run Commerce Data Exchange (CDX) job 1010 Customers.
The 1010 Customers job synchronizes:
  1. Organization account data
  1. Contact records
  1. Customer hierarchy relationships

**Result**

Once the data is synchronized, the organization and its enabled contacts can sign in to the B2B storefront.

### Other user management functions

#### Update role assignment for a contact
Roles control the level of access a contact has for a specific organization.
To update a contact role:

  1.	Go to Retail and Commerce > Customers > Customer hierarchies.
  1.	Open the relevant customer hierarchy.
  1.	In the Hierarchy grid, select the contact.
  1.	Select Change role.
  1.	Assign one of the following roles:
             - Admin
             - User

> [!NOTE]
> Each customer hierarchy must have at least one contact assigned the Admin role.

#### Link a contact to another customer hierarchy
Contacts can be associated with more than one organization by linking them to other customer hierarchies.

To link a contact to another hierarchy

  1.	Go to Retail and Commerce > Customers > Customer hierarchies.
  1.	Open the target customer hierarchy.
  1.	In the Hierarchy section, select Add.
  1.	Select the appropriate contact from the list.
  1.	Select Select to confirm.

**Behavior**
  - The selection list displays all contacts available for linking.
  - If the selected contact does not exist under the linked organization account, a new contact is created under that organization using the same party ID as the original contact.

#### Remove (delete) a contact link from a customer hierarchy 
Removing a contact deletes the relationship between the contact and the customer hierarchy.
To remove a contact from a hierarchy

  1.	Go to Retail and Commerce > Customers > Customer hierarchies.
  1.	Open the relevant customer hierarchy.
  1.	In the Hierarchy grid, select the contact.
  1.	Select Delete.

**Important**

Only contacts with no orders can be removed.
In these cases, use the Disable contact procedure instead to remove storefront access while preserving audit history.

#### Disable a contact for a specific organization

Disabling a contact removes storefront access for the organization while keeping the contact and hierarchy relationship intact.
To disable a contact

  1.	Go to Retail and Commerce > Customers > Customer hierarchies.
  1.	Open the relevant customer hierarchy.
  1.	In the Hierarchy grid, select the contact.
  1.	Select Disable.
  1.	When prompted, enter a reason for disabling the contact.

> [!NOTE]
> - Disabled contacts cannot sign in to the storefront for that organization.
> - The Enable/Disable actions on the contact form also update the contacts status in the customer hierarchy.

#### Synchronize changes to the storefront
After completing any user management changes:
Run CDX job 1010 Customers.
This job synchronizes:
  1. Contact updates
  1. Role changes
  1. Enable/disable status
  1. Customer hierarchy relationships

**Result**

After synchronization completes, the updated user access, roles, and organization associations are reflected in the B2B storefront and Customer Service experiences.

## Storefront Experiences
### Storefront Sign Up

The sign-up process allows a contact to create credentials and access the B2B storefront.

> [!NOTE]
> This process assumes that the contact already exists in a synchronized organization account and customer hierarchy. The sign-up process applies to B2B buyer organizations.

**To sign up from the storefront**
  1.	In the storefront header, select Sign in.
  1.	Select Sign up now.
  1.	Enter the required registration details.
  1.	After registration is complete, the user is automatically signed in and connected to the associated organization account.

**Sign in**
The sign-in process allows existing contacts to access the storefront.
To sign in
  1.	In the storefront header, select Sign in.
  1.	Enter credentials.
         - If necessary, complete the Forgot password flow to reset credentials.
         - After password reset, the user is signed in automatically.


### Select an organization (multi-outlet access)
Contacts who are configured with access to multiple organization accounts can select which organization they want to work with.

> [!NOTE]
>The organization selection module is displayed only for contacts that have access to more than one organization.

**To select an organization**
  1.	Sign in to the B2B storefront.
  1.	In the header, use the Select button to choose the preferred organization account.
  1.	The selected organization is marked as Selected.
  1.	The organization name appears in the My account menu.

Once selected, all storefront elements that depend on organization or customer hierarchy context such as pricing, catalogs, and checkout behavior are updated accordingly.

### Switch organizations during a session
The storefront supports switching between organizations without signing out.
To switch organizations
  1.	Open the My account menu.
  1.	Select Switch organization.
  1.	Choose a different organization from the list.

### Confirmation dialog when changing organizations
When switching organizations, the storefront displays a confirmation dialog.
The dialog explains:
  1. That pricing, discounts, and inventory may change
  1. That the current shopping cart is preserved
  1. That cart items can be restored when switching back to the previous organization

This confirmation ensures that users understand the impact of changing organizational context.

### Catalog visibility and My catalogs
Catalog visibility in the storefront is evaluated based on the active organization and its customer hierarchy configuration.
To review available catalogs
  1.	Open the My account menu.
  1.	Select My catalogs.
  1.	Review the catalogs available for the currently selected organization.

**Expected outcome**
When the active organization changes, the available catalogs may also change, depending on hierarchy and channel configuration.

## Call Center (Customer Service) experiences 
### Review contact information on placed orders
Orders placed through the storefront include contact-level tracking.
  -	The Contact field appears in the General section of the sales order header.

### Search orders by contact
Customer Service provides a Contact search experience for locating orders associated with a specific contact.
**Contact search experience** 
  1.	Select the Contact search tab.
  1.	Choose a search option:
          - Contact name
          - Contact phone number
          - Contact email address

### Create orders for a contact in Customer Service
The order creation experience depends on the organization selection made during contact search.
  1. Search contact, select all organizations 
        - The user is prompted to select a single organization before creating the order.
        - Only organizations where the contact is active are available for selection.
  1. Search contact, select a subset of organizations
        - The user is prompted to select a single organization.
        - Only organizations where the contact is active are available.
  1. Search contact, select a single organization
        - The flow proceeds directly to sales order creation.

> [!NOTE] 
> An inactive contact cannot be assigned to an order.


## Related information

For an overview of native B2B multioutlet capabilities in Microsoft Dynamics 365 Commerce, see [B2B multioutlet capabilities (preview)](b2b-multi-outlet.md).
- Organization-based purchasing context, where pricing, catalogs, addresses, and credit limits are defined.
- Contact-based access, where users are associated with one or more organizations through customer hierarchies.
- Context-aware ordering, where the selected outlet determines pricing, inventory, and checkout behavior.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
