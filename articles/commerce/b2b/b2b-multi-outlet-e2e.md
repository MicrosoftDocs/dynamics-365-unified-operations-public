---
title: B2B multioutlet end-to-end Experiences and Configuration Steps (preview)
description: Learn about the end-to-end experiences and configuration steps for native business-to-business (B2B) multioutlet capabilities in Microsoft Dynamics 365 Commerce.
author: Jcava-Evenica
ms.date: 02/06/2026
ms.topic: how-to
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: v-jcavataio
ms.search.validFrom: 2021-01-31
ms.search.form: RetailOperations
ms.custom:
  - bap-template
---
# B2B multioutlet end-to-end experiences and configuration steps (preview)
[!include [banner](../../includes/banner.md)]
## User management within Dynamics 365 Finance and Operations
### B2B Organization account setup - prospect flow
B2B Organization onboarding begins when a B2B Buyer prospect is approved. The following entities and relationships are established:

**Create Organization account** —
 An Organization account is created and assigned to the attached online channel’s address book.
 
**Create Contact under Organization account** —
A Contact is created under the Organization account. This Contact replaces the traditional person-type Customer account model and represents the initial user for the Organization. The Contact is also added to the attached online channels address book.


**Create Customer hierarchy and link to Organization account**—A Customer hierarchy is created and linked to the Organization account.
- The hierarchy is configured as a B2B buyer hierarchy.
- The Organization name is used as the hierarchy name.
        
**Link initial Contact to Customer hierarchy as Admin** —
 The initial Contact is linked to the Customer hierarchy and designated as the hierarchy administrator, enabling access to extra functions on the storefront.
 

#### Complete the setup for B2B channel availability
After the Organization account and Customer hierarchy are created, complete the following steps to make the Organization account and its users available on one or more B2B channels.

#### Assign a catalog (if applicable)
Catalog assignment controls the products that are available to users of the B2B Partner Organization in the storefront.
1. Open the relevant Customer hierarchy.
1. In the Catalogs section, select Add line.
1. Select the appropriate catalog.

> [!NOTE]
> Catalog assignment is optional and depends on how assortments are managed in your Dynamics 365 Commerce environment.

#### Link Contacts to the Customer hierarchy
Contacts represent individual B2B users who can access the B2B eCommerce storefront for their associated Organization.
1. In the Hierarchy section, select Add.
1. From the list, select the Contact to link.
1. Select Select.

 **Behavior**
- The list shows all Contacts that are available to be linked to the Organization account or Organization's Customer hierarchy.
- In prospect-based onboarding flows, the initial Contact is already linked to the Organization account and assigned the Admin role.
- If a selected Contact does not exist under the linked Organization account, a new Contact is created under that Organization account, reflecting updates made to any instance of that Contact.


#### Enable the Contact for storefront access
A Contact must be enabled before the user can sign in to the B2B storefront.
1. Select the Contact in the Hierarchy fast-tab.
1. Select Enable.

> [!IMPORTANT]
> Only enabled Contacts can sign in and access the storefront. Contacts that are linked but not enabled cannot place orders or view Organization data.

#### Assign or update the Contact role (if applicable)
Roles determine the permissions that a Contact has within the Organization.
1.	Select the Contact in the Hierarchy grid.
1.	Select Change role.
1.	Assign one of the following roles:
    - Admin
    - User

> [!NOTE]
> At least one Contact must be assigned the Admin role for each Customer hierarchy.


#### Complete Organization account configuration (if applicable)
Depending on business requirements, more configuration may be required at the Organization account level to ensure the correct purchasing experience in the storefront. Examples include:

-	Pricing configuration
- Discount assignment
- Credit limits
- Other Organization-specific purchasing settings

#### Synchronize data to Commerce
After configuration is complete, synchronize data so that changes are available in the storefront.
Run Commerce Data Exchange (CDX) job 1010 Customers.
The 1010  Customers job synchronizes:

- Organization account data
- Contact records
- Customer hierarchy relationships

> [!NOTE]
> B2B Seller/Buyer Organizations are not available to use with this feature and will be included in a future release.

**Result**

Once the data is synchronized, the Organization account and its enabled Contacts can sign in to the B2B storefront.

### Manual B2B Organization Account Setup
Manual onboarding is used to enable online access for an existing B2B Organization account by creating and linking a Customer hierarchy to that Organization. This process is performed primarily on the Customer hierarchies page in Finance and Operations.

A key requirement of this process is that at least one Contact must be selected and assigned as an administrator for the Customer hierarchy. The Contact can exist under the linked Organization account or under another Organization account.

**Before you begin**
Before starting manual onboarding, ensure that:

  1. The Organization account already exists.
  1. At least one Contact exists for that Organization account with a valid email address.

#### Create a Contact (if necessary)
An Organization account must have at least one Contact available to establish an initial administrator for the Customer hierarchy. 

  1. If no Contact exists, create a Contact under the Organization account.
  1. The Contact must have a valid email address to support storefront access.

> [!NOTE]
> The selected Contact becomes the initial Administrator for the Customer hierarchy.

#### Create a Customer hierarchy
Customer hierarchies define how Organizations and users are structured for B2B commerce.
  1.	Go to Retail and Commerce > Customers > Customer hierarchies.
  1.	Select New.


#### Link the Customer hierarchy to an Organization account
After selecting the hierarchy type:

  1.	Enter a name for the Customer hierarchy.
  1.	In the Organization field, select the appropriate Organization account from the dropdown list.

#### Select the initial admin Contact (required)
When linking an Organization account during manual hierarchy creation, the system requires selection of an initial administrator.
  1. A prompt appears to select the initial admin Contact.
  1. The selection list includes active Contacts from the selected Organization that have email addresses.


> [!IMPORTANT]
> Selecting an initial admin Contact is required to save the Customer hierarchy.
> If the prompt is canceled, the Organization is not linked and the hierarchy cannot be saved.

#### Automatically link other Contacts as users
After the initial admin Contact is selected:

  1. Any remaining eligible Contacts associated with the Organization are automatically linked to the Customer hierarchy.
  1. These Contacts are assigned the User role by default.
     
This automatic process reduces the need for manual user linking during initial setup.

#### Enable Contacts for storefront access (required)
Contacts must be enabled to access the B2B storefront.

  1.	In the Hierarchy grid, select the Contact.
  1.	Select Enable.

> [!IMPORTANT]
> Only enabled Contacts can sign in to the storefront.
> The enable and disable controls take effect through the Commerce Data Exchange (CDX) job 1010 – Customers and are used to control site access.

#### Assign catalogs (if applicable)
Catalog assignment determines which products are available to users in the storefront.

  1.	In the Catalogs section of the Customer hierarchy, select Add line.
  1.	Select the appropriate catalog.

> [!NOTE]
> Catalog assignment is optional and depends on how assortments are managed in your environment.

#### Assign or update Contact roles (if applicable)
Roles control what users can see and manage in the storefront.

  1.	Select a Contact in the Hierarchy grid.
  1.	Select Change role.
  1.	Assign one of the following roles:
    - Admin
    - User

> [!NOTE]
> At least one Contact must remain assigned the Admin role for each Customer hierarchy.


#### Perform other Organization account configuration (if necessary)
Depending on business requirements, other configuration may be required at the Organization account level to ensure correct storefront behavior.

Examples include:

  - Pricing configuration
  - Discount assignment
  - Other Organization-specific purchasing settings

#### Synchronize data to Commerce
After completing setup, synchronize data so that changes are available in the storefront.
Run Commerce Data Exchange (CDX) job 1010 Customers.
The 1010 Customers job synchronizes:
  1. Organization account data
  1. Contact records
  1. Customer hierarchy relationships

**Result**

Once the data is synchronized, the Organization and its enabled Contacts can sign in to the B2B storefront.

### Other user management functions

#### Update role assignment for a Contact
Roles control the level of access a Contact has for a specific Organization.
To update a Contact role:

  1.	Go to Retail and Commerce > Customers > Customer hierarchies.
  1.	Open the relevant Customer hierarchy.
  1.	In the Hierarchy grid, select the Contact.
  1.	Select Change role.
  1.	Assign one of the following roles:
             - Admin
             - User

> [!NOTE]
> Each Customer hierarchy must have at least one Contact assigned the Admin role.

#### Link a Contact to another Customer hierarchy
Contacts can be associated with more than one Organization by linking them to other Customer hierarchies.

To link a Contact to another hierarchy

  1.	Go to Retail and Commerce > Customers > Customer hierarchies.
  1.	Open the target Customer hierarchy.
  1.	In the Hierarchy section, select Add.
  1.	Select the appropriate Contact from the list.
  1.	Select Select to confirm.

**Behavior**
  - The selection list displays all Contacts available for linking.
  - If the selected Contact does not exist under the linked Organization account, a new Contact is created under that Organization using the same party ID as the original Contact.

#### Remove (delete) a Contact link from a Customer hierarchy 
Removing a Contact deletes the relationship between the Contact and the Customer hierarchy.
To remove a Contact from a hierarchy

  1.	Go to Retail and Commerce > Customers > Customer hierarchies.
  1.	Open the relevant Customer hierarchy.
  1.	In the Hierarchy grid, select the Contact.
  1.	Select Delete.

> [!IMPORTANT]
> Contacts that have placed one or more orders cannot be removed from the hierarchy.
> In these cases, use the Disable Contact procedure instead to remove storefront access while preserving audit history.
#### Disable a Contact for a specific Organization

Disabling a Contact removes storefront access for the Organization while keeping the Contact and hierarchy relationship intact.
To disable a Contact

  1.	Go to Retail and Commerce > Customers > Customer hierarchies.
  1.	Open the relevant Customer hierarchy.
  1.	In the Hierarchy grid, select the Contact.
  1.	Select Disable.
  1.	When prompted, enter a reason for disabling the Contact.

> [!NOTE]
> - Disabled Contacts cannot sign in to the storefront for that Organization.
> - The Enable/Disable actions on the Contact form also update the Contacts status in the Customer hierarchy.

#### Synchronize changes to the storefront
After completing any user management changes:
Run CDX job 1010 Customers.
This job synchronizes:
  1. Contact updates
  1. Role changes
  1. Enable/disable status
  1. Customer hierarchy relationships

**Result**

After synchronization completes, the updated user access, roles, and Organization associations are reflected in the B2B storefront and Customer Service experiences.

## Storefront experiences
### Storefront sign up

The sign-up process allows a Contact to create credentials and access the B2B storefront.

> [!NOTE]
> This process assumes that the Contact already exists in a synchronized Organization account and Customer hierarchy. The sign-up process applies to B2B buyer Organizations.

**To sign up from the storefront**
  1.	In the storefront header, select Sign in.
  1.	Select Sign up now.
  1.	Enter the required registration details.
  1.	After registration is complete, the user is automatically signed in and connected to the associated Organization account.

**Sign in**
The sign-in process allows existing Contacts to access the storefront.
To sign in
  1.	In the storefront header, select Sign in.
  1.	Enter credentials.
         - If necessary, complete the Forgot password flow to reset credentials.
         - After password reset, the user is signed in automatically.


### Select an Organization (multioutlet access)
Contacts who are configured with access to multiple Organization accounts can select which Organization they want to work with.

> [!NOTE]
> The Organization selection module is displayed only for Contacts that have access to more than one Organization.

**To select an Organization**
  1.	Sign in to the B2B storefront.
  1.	In the header, use the Select button to choose the preferred Organization account.
  1.	The selected Organization is marked as Selected.
  1.	The Organization name appears in the My account menu.

Once selected, all storefront elements that depend on Organization or Customer hierarchy context such as pricing, catalogs, and checkout behavior are updated accordingly.

### Switch Organizations during a session
The storefront supports switching between Organizations without signing out.
To switch Organizations
  1.	Open the My account menu.
  1.	Select Switch Organization.
  1.	Choose a different Organization from the list.

### Confirmation dialog when changing Organizations
When switching Organizations, the storefront displays a confirmation dialog.
The dialog explains:
  1. That pricing, discounts, and inventory may change
  1. That the current shopping cart is preserved
  1. That cart items can be restored when switching back to the previous Organization

This confirmation ensures that users understand the impact of changing Organizational context.

### Catalog visibility and My catalogs
Catalog visibility in the storefront is evaluated based on the active Organization account and its Customer hierarchy configuration.
To review available catalogs
  1.	Open the My account menu.
  1.	Select My catalogs.
  1.	Review the catalogs available for the currently selected Organization.

**Expected outcome**
When the active Organization changes, the available catalogs may also change, depending on Customer hierarchy and channel configuration.

## Call center (customer service) experiences
### Review Contact information on placed orders
Orders placed through the storefront include Contact-level tracking.
  -	The Contact field appears in the General section of the sales order header.

### Search orders by Contact
Customer Service provides a Contact search experience for locating orders associated with a specific Contact.
**Contact search experience** 
  1.	Select the Contact search tab.
  1.	Choose a search option:
          - Contact name
          - Contact phone number
          - Contact email address

### Create orders for a Contact in Customer Service
The order creation experience depends on the Organization account selection made during Contact search. The main options for searching and their details for order creation are below:
  - **Search Contact, select all Organizations** 
        - The Call center user is prompted to select a single Organization before creating the order.
        - Only Organizations where the Contact is active are available for selection.
  - **Search Contact, select a subset of Organizations**
        - The Call center user is prompted to select a single Organization.
        - Only Organizations where the Contact is active are available.
  - **Search Contact, select a single Organization**
        - The flow proceeds directly to sales order creation for the Call center user.

Creating a sales order for the Contact at a given Organization will adhere to the specific configurations for the selected Organization account. Some example areas include:
- Product eligibility through catalogs (based on Organization account's Customer hierarchy)
- Pricing and discounts
- Credit limits for on-account payments


> [!NOTE] 
> An inactive Contact cannot be assigned to an order.

## Related information

For an overview of native B2B multioutlet capabilities in Microsoft Dynamics 365 Commerce, see [B2B multioutlet capabilities (preview)](b2b-multi-outlet.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
