---
title: B2B multioutlet configuration (preview)
description: Learn how to configure business-to-business (B2B) multioutlet capabilities in Microsoft Dynamics 365 Commerce.
author: Jcava-Evenica
ms.date: 09/10/2026
ms.topic: how-to
ms.reviewer: mirao
ms.search.region: Global
ms.author: v-jcavataio
ms.search.validFrom: 2021-01-31
ms.search.form: RetailOperations
ms.custom:
  - bap-template
---
# B2B multioutlet configuration (preview)

[!INCLUDE [banner](../../includes/banner.md)]
[!INCLUDE [banner](../../includes/preview-banner.md)]

This article explains how to configure business-to-business (B2B) multioutlet capabilities in Microsoft Dynamics 365 Commerce.

## B2B organization account setup

B2B organization onboarding begins when a B2B buyer prospect is approved. Then, complete the following steps to establish entities and relationships:

1. **Create organization account**: Create an organization account and assign it to the attached online channel's address book.
1. **Create contact under organization account**: Create a contact under the organization account. This contact replaces the traditional person-type customer account model and represents the initial user for the organization. Also, add the contact to the attached online channel's address book.
1. **Create customer hierarchy and link to organization account**: Create a customer hierarchy and link it to the organization account.
    - Configure the hierarchy as a B2B buyer hierarchy.
    - Use the organization name as the hierarchy name.
1. **Link initial contact to customer hierarchy as the administrator**: Link the initial contact to the customer hierarchy and designate the contact as the hierarchy administrator. This configuration enables access to other functions on the storefront.

After you create the organization account and customer hierarchy, complete the following steps to make the organization account and its users available on one or more B2B channels.

### Assign a catalog

> [!NOTE]
> Catalog assignment is optional and depends on how assortments are managed in your Commerce environment.

Catalog assignment controls the products that are available to users of the B2B partner organization in the storefront.

To assign a catalog, follow these steps:

1. In Commerce headquarters, go to **Retail and Commerce** > **Customers** > **Customer hierarchies**.
1. Under **Customer hierarchy ID**, select the relevant hierarchy ID.
1. On the **Catalogs** FastTab, select **Add line**.
1. Select the appropriate catalog.

### Link contacts to the customer hierarchy

Contacts represent individual B2B users who can access the B2B e-commerce storefront for their associated organization.

To link contacts to the customer hierarchy, follow these steps:

1. In headquarters, go to **Retail and Commerce** > **Customers** > **Customer hierarchies**.
1. Under **Customer hierarchy ID**, select the hierarchy ID.
1. On the **Hierarchy** FastTab, select **Add**.
1. From the dropdown list, select the contact to link.
1. In the dialog that appears, select **Select**.

> [!NOTE]
>
> - The list shows all contacts that are available to be linked to the organization account or organization's customer hierarchy.
> - In prospect-based onboarding flows, the initial contact is already linked to the organization account and is assigned the **Admin** role.
> - If a selected contact doesn't exist under the linked organization account, a new contact is created under that organization account that reflects updates made to any instance of that contact.

### Enable the contact for storefront access

You need to enable a contact before the associated user can sign in to the B2B storefront.

To enable the contact for storefront access, follow these steps:

1. In headquarters, go to **Retail and Commerce** > **Customers** > **Customer hierarchies**.
1. Under **Customer hierarchy ID**, select the hierarchy ID.
1. On the **Hierarchy** FastTab, select the contact.
1. Select **Enable**.

> [!IMPORTANT]
> Only enabled contacts can sign in and access the storefront. Contacts that are linked but not enabled can't place orders or view organization data.

### Assign or update the contact role (if applicable)

Roles determine the permissions that a contact has within the organization.

To assign or update the contact role, follow these steps:

1. In headquarters, go to **Retail and Commerce** > **Customers** > **Customer hierarchies**.
1. Under **Customer hierarchy ID**, select the hierarchy ID.
1. On the **Hierarchy** FastTab, select the contact.
1. Select **Change role**.
1. Under **Role**, select one of the following roles:
    - **Admin**
    - **User**
1. Select **OK**.

> [!NOTE]
> You must assign at least one contact to the **Admin** role for each customer hierarchy.

### Complete organization account configuration (if applicable)

Depending on your business requirements, you might need to configure more settings at the organization account level to ensure the correct purchasing experience in the storefront. Examples include:

- Pricing configuration.
- Discount assignment.
- Credit limits.
- Other organization-specific purchasing settings.

### Synchronize data to Commerce

After you complete the configuration steps, synchronize data so that changes are available in the storefront.

To synchronize data to Commerce, run the Commerce Data Exchange (CDX) **1010 (Customers)** job. When the data is synchronized, the organization account and its enabled contacts can sign in to the B2B storefront.

The **1010 (Customers)** job synchronizes:

- Organization account data
- Contact records
- Customer hierarchy relationships

> [!NOTE]
> Currently, you can't use B2B seller or buyer organizations with this feature. Functionality to include B2B seller or buyer organizations will be included in a future release.

## Manual onboarding setup

Use manual onboarding to enable online access for an existing B2B organization account by creating and linking a customer hierarchy to that organization. Perform this process primarily on the customer hierarchies page in headquarters.

A key requirement of this process is that you select and assign at least one contact as an administrator for the customer hierarchy. The contact can exist under the linked organization account or under another organization account.

Before you start manual onboarding, ensure that:

- The organization account already exists.
- At least one contact exists for that organization account with a valid email address.

### Create a contact (if necessary)

An organization account must have at least one contact available to establish an initial administrator for the customer hierarchy.

To create a contact, follow these steps:

1. In headquarters, go to **Retail and Commerce** > **Customers** > **Customer hierarchies**.
1. Under **Customer hierarchy ID**, select the hierarchy ID.
1. On the **Hierarchy** FastTab, select **Add** to add the contact as an administrator. The contact must have a valid email address to support storefront access.

> [!NOTE]
> The selected contact becomes the initial administrator for the customer hierarchy.

### Create a customer hierarchy

Customer hierarchies define how organizations and users are structured for B2B commerce.

To create a customer hierarchy and link it to an organization account, follow these steps:

1. In headquarters, go to **Retail and Commerce** > **Customers** > **Customer hierarchies**.
1. Select **New**.
1. Enter a name for the customer hierarchy.
1. In the **Organization** field, select the appropriate organization account from the dropdown list.

### Select the initial administrator contact (required)

When you link an organization account during manual hierarchy creation, you must select an initial administrator.

- A prompt appears to select the initial administrator contact.
- The selection list includes active contacts from the selected organization that have email addresses.

> [!IMPORTANT]
>
> - You must select an initial administrator contact to save the customer hierarchy.
> - If you cancel the prompt, the organization isn't linked and you can't save the hierarchy.

### Automatically link other contacts as users

After you select the initial administrator contact:

- The system automatically links any remaining eligible contacts associated with the organization to the customer hierarchy.
- The system assigns the **User** role to these contacts by default.

This automatic process reduces the need for manual user linking during initial setup.

### Enable contacts for storefront access (required)

Contacts must be enabled to access the B2B storefront.

1. In headquarters, go to **Retail and Commerce** > **Customers** > **Customer hierarchies**.
1. Under **Customer hierarchy ID**, select the hierarchy ID.
1. On the **Hierarchy** FastTab, select the contact.
1. Select **Enable**.

> [!IMPORTANT]
>
> - Only enabled contacts can sign in to the storefront.
> - The **Enable** and **Disable** controls take effect through the **1010 (Customers)** job and control site access.

### Assign catalogs (if applicable)

Catalog assignment determines which products are available to users in the storefront.

1. In headquarters, go to **Retail and Commerce** > **Customers** > **Customer hierarchies**.
1. Under **Customer hierarchy ID**, select the relevant hierarchy ID.
1. On the **Catalogs** FastTab, select **Add line**.
1. Select the appropriate catalog.

> [!NOTE]
> Catalog assignment is optional and depends on how assortments are managed in your environment.

### Assign or update contact roles (if applicable)

Roles control what users can see and manage in the storefront.

1. In headquarters, go to **Retail and Commerce** > **Customers** > **Customer hierarchies**.
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

After you complete setup, synchronize data so that changes are available in the storefront.

Run the Commerce Data Exchange (CDX) **1010 (Customers)** job.

The **1010 (Customers)** job synchronizes:

- Organization account data.
- Contact records.
- Customer hierarchy relationships.

When you synchronize the data, the organization and its enabled contacts can sign in to the B2B storefront.

## Configure other user management functions

### Link a contact to another customer hierarchy

Contacts can be associated with more than one organization when you link them to other customer hierarchies.

To link a contact to another hierarchy, follow these steps:

1. In headquarters, go to **Retail and Commerce** > **Customers** > **Customer hierarchies**.
1. Under **Customer hierarchy ID**, select the hierarchy ID.
1. On the **Hierarchy** FastTab, select **Add**.
1. Select the appropriate contact from the list. The selection list displays all contacts available for linking.
1. In the dialog that appears, select **Select**.

> [!NOTE]
> If the selected contact doesn't exist under the linked organization account, a new contact is created under that organization using the same party ID as the original contact.

### Remove a contact link from a customer hierarchy

When you remove a contact, you delete the relationship between the contact and the customer hierarchy.

To remove a contact from a hierarchy, follow these steps:

1. In headquarters, go to **Retail and Commerce** > **Customers** > **Customer hierarchies**.
1. Under **Customer hierarchy ID**, select the hierarchy ID.
1. On the **Hierarchy** FastTab, select the contact.
1. Select **Delete**.

> [!IMPORTANT]
> You can't remove contacts that place one or more orders from the hierarchy. In these cases, disable the contact instead to remove storefront access while preserving audit history.

### Disable a contact for an organization

Disabling a contact removes storefront access for the organization while keeping the contact and hierarchy relationship intact.

To disable a contact, follow these steps:

1. In headquarters, go to **Retail and Commerce** > **Customers** > **Customer hierarchies**.
1. Under **Customer hierarchy ID**, select the hierarchy ID.
1. On the **Hierarchy** FastTab, select the contact.
1. Select **Disable**.
1. When prompted, enter a reason for disabling the contact.

> [!NOTE]
>
> - Disabled contacts can't sign in to the storefront for that organization.
> - The **Enable** and **Disable** actions on the contact form also update the contact's status in the customer hierarchy.

### Synchronize changes to the storefront

After you complete any user management changes, run the **1010 (Customers)** job.

The **1010 (Customers)** job synchronizes:

- Contact updates.
- Role changes.
- Enable and disable status.
- Customer hierarchy relationships.

When synchronization finishes, the B2B storefront and customer service experiences reflect the updated user access, roles, and organization associations.

## Storefront experience functions

### Storefront registration

The registration process lets a contact create credentials and access the B2B storefront.

> [!NOTE]
> This process assumes that the contact already exists in a synchronized organization account and customer hierarchy. The registration process applies to B2B buyer organizations.

To register from the storefront, follow these steps:

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

Contacts who have access to multiple organization accounts can select the organization they want to work with. For setup guidance, see [Organization selection](../organization-selection.md).

To select an organization, follow these steps:

1. Sign in to the B2B storefront.
1. In the header, use **Select** to choose the preferred organization account. The selected organization is marked as **Selected**, and the organization name appears in the **My account** menu.

After you select an organization, the storefront updates functions that depend on organization or customer hierarchy context, such as pricing, catalogs, and checkout behavior.

### Switch organizations during a session

The storefront supports switching between organizations without signing out.

To switch organizations, follow these steps:

1. Open the **My account** menu.
1. Select **Switch organization**.
1. Select a different organization from the list.

When you switch organizations, the storefront displays a confirmation dialog that explains:

- Pricing, discounts, and inventory might change.
- The current shopping cart is preserved.
- You can restore cart items when you switch back to the previous organization.

The confirmation dialog ensures that users understand the impact of changing organizational context.

### Catalog visibility using My catalogs

The storefront evaluates catalog visibility based on the active organization account and its customer hierarchy configuration.

To review available catalogs, follow these steps:

1. Open the **My account** menu.
1. Select **My catalogs**.
1. Review the catalogs available for the currently selected organization.

When you change the active organization, the available catalogs might change, depending on customer hierarchy and channel configuration.

## Call center experience functions

### Review contact information on placed orders

Orders you place through the storefront include contact-level tracking. The contact field appears in the **General** section of the sales order header.

### Search orders by contact

Call center provides a contact search experience for locating orders associated with a specific contact.

To search orders by contact, follow these steps:

1. Select the **Contact search** tab.
1. Select one of the following search options:
    - **Contact name**
    - **Contact phone number**
    - **Contact email address**

### Create orders for a contact in call center

The order creation experience depends on the organization account selection you make during contact search.

The main options for searching and their details for order creation are:

- **Search contact, select all organizations**:
  - The call center user is prompted to select a single organization before creating the order.
  - Only organizations where the contact is active are available for selection.
- **Search contact, select a subset of organizations**:
  - The call center user is prompted to select a single organization.
  - Only organizations where the contact is active are available for selection.
- **Search contact, select a single organization**:
  - The flow proceeds directly to sales order creation for the call center user.

When you create a sales order for the contact at a given organization, you follow the specific configurations for the selected organization account. Some example areas include:

- Product eligibility through catalogs (based on the organization account's customer hierarchy).
- Pricing and discounts.
- The organization account's credit limits for on-account payments.

> [!NOTE]
> You can't assign an inactive contact to an order.

## More resources

[B2B multioutlet capabilities](b2b-multi-outlet.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
