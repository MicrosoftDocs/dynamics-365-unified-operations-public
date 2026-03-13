---
title: B2B multioutlet configuration (preview)
description: Learn how to configure business-to-business (B2B) multioutlet capabilities in Microsoft Dynamics 365 Commerce.
author: Jcava-Evenica
ms.date: 03/13/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: v-jcavataio
ms.search.validFrom: 2021-01-31
ms.search.form: RetailOperations
ms.custom:
  - bap-template
---
# B2B multioutlet configuration (preview)

[!include [banner](../../includes/banner.md)]
[!include [banner](../../includes/preview-banner.md)]

This article explains how to configure business-to-business (B2B) multioutlet capabilities in Microsoft Dynamics 365 Commerce.

## B2B organization account setup

B2B organization onboarding begins when a B2B buyer prospect is approved. You then complete the following steps to establish entities and relationships:

1. **Create organization account**: Create an organization account and assign it to the attached online channel's address book.
1. **Create contact under organization account**: Create a contact under the organization account. This contact replaces the traditional person-type customer account model and represents the initial user for the organization. You also add the contact to the attached online channels address book.
1. **Create customer hierarchy and link to organization account**: Create a customer hierarchy and link it to the organization account.
    - The hierarchy is configured as a B2B buyer hierarchy.
    - The organization name is used as the hierarchy name.
1. **Link initial contact to customer hierarchy as the administrator**: Link the initial contact to the customer hierarchy and designate the contact as the hierarchy administrator. This configuration enables access to other functions on the storefront.

After you create the organization account and customer hierarchy, complete the following steps to make the organization account and its users available on one or more B2B channels.

### Assign a catalog (if applicable)

Catalog assignment controls the products that are available to users of the B2B partner organization in the storefront.

To assign a catalog, follow these steps:

1. In Commerce headquarters, go to **Retail and Commerce > Customers > Customer hierarchies**.
1. Under **Customer hierarchy ID**, select the relevant hierarchy ID.
1. On the **Catalogs** FastTab, select **Add line**.
1. Select the appropriate catalog.

> [!NOTE]
> Catalog assignment is optional and depends on how assortments are managed in your Commerce environment.

### Link contacts to the customer hierarchy

Contacts represent individual B2B users who can access the B2B e-commerce storefront for their associated organization.

To link contacts to the customer hierarchy, follow these steps:

1. In headquarters, go to **Retail and Commerce > Customers > Customer hierarchies**.
1. Under **Customer hierarchy ID**, select the hierarchy ID.
1. On the **Hierarchy** FastTab, select **Add**.
1. From the dropdown list, select the contact to link.
1. In the dialog that appears, select **Select**.

> [!NOTE]
> - The list shows all contacts that are available to be linked to the organization account or organization's customer hierarchy.
> - In prospect-based onboarding flows, the initial contact is already linked to the organization account and is assigned the **Admin** role.
> - If a selected contact doesn't exist under the linked organization account, a new contact is created under that organization account that reflects updates made to any instance of that contact.

### Enable the contact for storefront access

You enable a contact before the associated user can sign in to the B2B storefront.

To enable the contact for storefront access, follow these steps:

1. In headquarters, go to **Retail and Commerce > Customers > Customer hierarchies**.
1. Under **Customer hierarchy ID**, select the hierarchy ID.
1. On the **Hierarchy** FastTab, select the contact.
1. Select **Enable**.

> [!IMPORTANT]
> Only enabled contacts can sign in and access the storefront. Contacts that are linked but not enabled can't place orders or view organization data.

### Assign or update the contact role (if applicable)

Roles determine the permissions that a contact has within the organization.

To assign or update the contact role, follow these steps:

1. In headquarters, go to **Retail and Commerce > Customers > Customer hierarchies**.
1. Under **Customer hierarchy ID**, select the hierarchy ID.
1. On the **Hierarchy** FastTab, select the contact.
1. Select **Change role**.
1. Under **Role**, select one of the following roles:
    - **Admin**
    - **User**
1. Select **OK**.

> [!NOTE]
> At least one contact must be assigned the **Admin** role for each customer hierarchy.

### Complete organization account configuration (if applicable)

Depending on business requirements, more configuration may be required at the organization account level to ensure the correct purchasing experience in the storefront. Examples include:

- Pricing configuration.
- Discount assignment.
- Credit limits.
- Other organization-specific purchasing settings.

### Synchronize data to Commerce

After you complete the configuration steps, you must synchronize data so that changes are available in the storefront.

To synchronize data to Commerce, run the Commerce Data Exchange (CDX) **1010 (Customers)** job. Once the data is synchronized, the organization account and its enabled contacts can sign in to the B2B storefront.

The **1010 (Customers)** job synchronizes:

- Organization account data
- Contact records
- Customer hierarchy relationships

> [!NOTE]
> Currently, B2B seller/buyer organizations aren't available to use with this feature. Functionality to include B2B seller/buyer organizations will be included in a future release.

## Manual onboarding setup

Manual onboarding is used to enable online access for an existing B2B organization account by creating and linking a customer hierarchy to that organization. This process is performed primarily on the customer hierarchies page in headquarters.

A key requirement of this process is that at least one contact must be selected and assigned as an administrator for the customer hierarchy. The contact can exist under the linked organization account or under another organization account.

Before you start manual onboarding, ensure that:
- The organization account already exists.
- At least one contact exists for that organization account with a valid email address.

### Create a contact (if necessary)

An organization account must have at least one contact available to establish an initial administrator for the customer hierarchy. 

To create a contact, follow these steps:

1. In headquarters, go to **Retail and Commerce > Customers > Customer hierarchies**.
1. Under **Customer hierarchy ID**, select the hierarchy ID.
1. On the **Hierarchy** FastTab, select **Add** to add the contact as an administrator. The contact must have a valid email address to support storefront access.

> [!NOTE]
> The selected contact becomes the initial administrator for the customer hierarchy.

### Create a customer hierarchy

Customer hierarchies define how organizations and users are structured for B2B commerce.

To create a customer hierarchy and link it to an organization account, follow these steps:

1. In headquarters, go to **Retail and Commerce > Customers > Customer hierarchies**.
1. Select **New**.
1. Enter a name for the customer hierarchy.
1. In the **Organization** field, select the appropriate organization account from the dropdown list.

### Select the initial administrator contact (required)

When you link an organization account during manual hierarchy creation, the system requires selection of an initial administrator.

- A prompt appears to select the initial administrator contact.
- The selection list includes active contacts from the selected organization that have email addresses.

> [!IMPORTANT]
> - Selecting an initial administrator contact is required to save the customer hierarchy.
> - If the prompt is canceled, the organization isn't linked and the hierarchy can't be saved.

### Automatically link other contacts as users

After the initial administrator contact is selected:

- Any remaining eligible contacts associated with the organization are automatically linked to the customer hierarchy.
- These contacts are assigned the **User** role by default.
     
This automatic process reduces the need for manual user linking during initial setup.

### Enable contacts for storefront access (required)

Contacts must be enabled to access the B2B storefront.

1. In headquarters, go to **Retail and Commerce > Customers > Customer hierarchies**.
1. Under **Customer hierarchy ID**, select the hierarchy ID.
1. On the **Hierarchy** FastTab, select the contact.
1. Select **Enable**.

> [!IMPORTANT]
> - Only enabled contacts can sign in to the storefront.
> - The enable and disable controls take effect through the **1010 (Customers)** job and are used to control site access.

### Assign catalogs (if applicable)

Catalog assignment determines which products are available to users in the storefront.

1. In headquarters, go to **Retail and Commerce > Customers > Customer hierarchies**.
1. Under **Customer hierarchy ID**, select the relevant hierarchy ID.
1. On the **Catalogs** FastTab, select **Add line**.
1. Select the appropriate catalog.

> [!NOTE]
> Catalog assignment is optional and depends on how assortments are managed in your environment.

### Assign or update contact roles (if applicable)

Roles control what users can see and manage in the storefront.

1. In headquarters, go to **Retail and Commerce > Customers > Customer hierarchies**.
1. Under **Customer hierarchy ID**, select the hierarchy ID.
1. On the **Hierarchy** FastTab, select the contact.
1. Select **Change role**.
1. Under **Role**, select one of the following roles:
    - **Admin**
    - **User**
1. Select **OK**.

> [!NOTE]
> Each customer hierarchy must have at least one contact assigned the **Admin** role.

### Other organization account configuration (optional)

Depending on business requirements, other configuration may be required at the organization account level to ensure correct storefront behavior.

Examples include:

  - Pricing configuration.
  - Discount assignment.
  - Other organization-specific purchasing settings.

### Synchronize data to Commerce

After completing setup, synchronize data so that changes are available in the storefront.

Run the Commerce Data Exchange (CDX) **1010 (Customers)** job.

The **1010 (Customers)** job synchronizes:
- Organization account data.
- Contact records.
- Customer hierarchy relationships.

Once the data is synchronized, the organization and its enabled contacts can sign in to the B2B storefront.

## Configure other user management functions

### Link a contact to another customer hierarchy

Contacts can be associated with more than one organization by linking them to other customer hierarchies.

To link a contact to another hierarchy, follow these steps:

1. In headquarters, go to **Retail and Commerce > Customers > Customer hierarchies**.
1. Under **Customer hierarchy ID**, select the hierarchy ID.
1. On the **Hierarchy** FastTab, select **Add**.
1. Select the appropriate contact from the list. The selection list displays all contacts available for linking.
1. In the dialog that appears, select **Select**.

> [!NOTE]
> If the selected contact doesn't exist under the linked organization account, a new contact is created under that organization using the same party ID as the original contact.

### Remove a contact link from a customer hierarchy

When you remove a contact, you delete the relationship between the contact and the customer hierarchy.

To remove a contact from a hierarchy, follow these steps:

1. In headquarters, go to **Retail and Commerce > Customers > Customer hierarchies**.
1. Under **Customer hierarchy ID**, select the hierarchy ID.
1. On the **Hierarchy** FastTab, select the contact.
1. Select **Delete**.

> [!IMPORTANT]
> Contacts that place one or more orders can't be removed from the hierarchy. In these cases, disable the contact instead to remove storefront access while preserving audit history.

### Disable a contact for an organization

Disabling a contact removes storefront access for the organization while keeping the contact and hierarchy relationship intact.

To disable a contact, follow these steps:

1. In headquarters, go to **Retail and Commerce > Customers > Customer hierarchies**.
1. Under **Customer hierarchy ID**, select the hierarchy ID.
1. On the **Hierarchy** FastTab, select the contact.
1. Select **Disable**.
1. When prompted, enter a reason for disabling the contact.

> [!NOTE]
> - Disabled contacts can't sign in to the storefront for that organization.
> - The **Enable** and **Disable** actions on the contact form also update the contacts status in the customer hierarchy.

### Synchronize changes to the storefront

After completing any user management changes, run the **1010 (Customers)** job.

The **1010 (Customers)** job synchronizes:
- Contact updates.
- Role changes.
- Enable/disable status.
- Customer hierarchy relationships.

After synchronization is complete, the updated user access, roles, and organization associations are reflected in the B2B storefront and customer service experiences.

## Storefront experience functions

### Storefront sign up

The sign-up process allows a contact to create credentials and access the B2B storefront.

> [!NOTE]
> This process assumes that the contact already exists in a synchronized organization account and customer hierarchy. The sign-up process applies to B2B buyer organizations.

To sign up from the storefront, follow these steps:

1. On the storefront header, select **Sign in**.
1. Select **Sign up now**.
1. Enter the required registration details.
1. After registration is complete, you're automatically signed in and connected to the associated organization account.

The sign-in process allows existing contacts to access the storefront.

To sign in, follow these steps:

1. On the storefront header, select **Sign in**.
1. Enter your credentials.
    - If necessary, complete the forgot password flow to reset credentials.
    - After your password reset, you're automatically signed in.

### Select an organization (multioutlet access)

Contacts who are configured with access to multiple organization accounts can select which organization they want to work with.

> [!NOTE]
> The organization selection module is displayed only for contacts that have access to more than one organization.

To select an organization, follow these steps:

1. Sign in to the B2B storefront.
1. In the header, use **Select** to select the preferred organization account. The selected organization is then marked as **Selected**, and the organization name appears in the **My account** menu.

After you select an organization, storefront functions that depend on organization or customer hierarchy context such as pricing, catalogs, and checkout behavior are updated accordingly.

### Switch organizations during a session

The storefront supports switching between organizations without signing out.

To switch organizations, follow these steps:

1. Open the **My account** menu.
1. Select **Switch organization**.
1. Select a different organization from the list.

When you switch organizations, the storefront displays a confirmation dialog explaining that:
- Pricing, discounts, and inventory may change.
- The current shopping cart is preserved.
- Cart items can be restored when you switch back to the previous organization.

The confirmation dialog ensures that users understand the impact of changing organizational context.

### Catalog visibility using My catalogs

Catalog visibility in the storefront is evaluated based on the active organization account and its customer hierarchy configuration.

To review available catalogs, follow these steps:

1. Open the **My account** menu.
1. Select **My catalogs**.
1. Review the catalogs available for the currently selected organization.

When the active organization changes, the available catalogs may also change, depending on customer hierarchy and channel configuration.

## Call center experience functions

### Review contact information on placed orders

Orders placed through the storefront include contact-level tracking. The contact field appears in the **General** section of the sales order header.

### Search orders by contact

Call center provides a contact search experience for locating orders associated with a specific contact.

To search orders by contact, follow these steps:

1. Select the **Contact search** tab.
1. Select one of the following search options:
    - **Contact name**
    - **Contact phone number**
    - **Contact email address**

### Create orders for a contact in call center

The order creation experience depends on the organization account selection made during contact search.

The main options for searching and their details for order creation are:
  - **Search contact, select all organizations**:
    - The call center user is prompted to select a single organization before creating the order.
    - Only organizations where the contact is active are available for selection.
  - **Search contact, select a subset of organizations**:
    - The call center user is prompted to select a single organization.
    - Only organizations where the contact is active are available for selection.
  - **Search contact, select a single organization**:
    - The flow proceeds directly to sales order creation for the call center user.

Creating a sales order for the contact at a given organization adheres to the specific configurations for the selected organization account. Some example areas include:
  - Product eligibility through catalogs (based on the organization account's customer hierarchy).
  - Pricing and discounts.
  - The organization account's credit limits for on-account payments.

> [!NOTE] 
> An inactive contact can't be assigned to an order.

## Additional resources

[B2B multioutlet capabilities](b2b-multi-outlet.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
