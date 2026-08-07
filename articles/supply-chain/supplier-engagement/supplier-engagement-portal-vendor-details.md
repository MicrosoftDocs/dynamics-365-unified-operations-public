---
title: Vendor details in the supplier portal (preview)
description: Learn how vendors can manage their organizational profile, contacts, certificates, capabilities, and user access through the supplier portal.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 08/07/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Manage vendor details, local vendors, and users in the supplier portal (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

After completing onboarding, vendors can manage their organization's data and user access directly in the supplier portal.

- The **Global vendor setup** page provides a centralized interface for updating company details, contacts, certificates, and capabilities.
- The **Local vendor setup** page allows vendors to manage their records at the legal entity level, including ownership profiles, contact information, approved categories, and bank details.
- The **User management** page allows vendor administrators to control who has access to the portal, what roles they hold, and which vendors they can work with.

## Global vendor setup

Use the **Global vendor setup** page to manage your organization's profile, contacts, certificates, and capabilities. The page provides a structured interface for maintaining accurate and up-to-date information that's essential for supplier engagement and compliance. To open the page, complete one of the following steps:

- From the home page, select **Global vendor setup** from the **Vendor details** tile.
- From the navigation menu, go to **Setup** \> **Global vendor setup**.

The following table summarizes the settings available in the **Global vendor setup** page.

| Section | Description |
|---|---|
| General information | Maintain and update your core company profile, including the key organizational details required for supplier registration and business identification. |
| Ownership profile | Provide and manage your company ownership and business classification information for supplier diversity and business categorization purposes. |
| Contact information | Manage the primary company contact details used for communication and supplier-related correspondence. |
| Contact methods | Maintain the different communication channels associated with your company, including adding, updating, or removing contact methods as required. |
| Addresses | Manage your company address information by adding new addresses, updating existing address details, or removing outdated address records. |
| Contacts | Manage the contact persons associated with your organization, including maintaining active contact details and updating company representatives when needed. |
| Certificates | Manage compliance and certification records by maintaining certificate information, uploading supporting documents, and updating certification details as part of supplier compliance management. |
| Capabilities | Maintain and update your business capabilities, including areas of expertise, product categories, quality standards, and other capabilities that define your scope of supply. Make selections by using a tree-structured control that the buyer configures. |

## View and manage local vendors

Use the **Local vendor setup** page to view and manage your records at the legal entity level. The page provides a structured interface for maintaining accurate and up-to-date information that's essential for supplier engagement and compliance. To open the page, follow these steps:

1. Do one of the following steps:
    - From the home page, select **Local Vendor Setup** from the **Vendor details** panel.
    - From the navigation menu, go to **Setup** \> **For buyer's legal entities**.

1. Select the local vendor you want to work with.

The following table summarizes the key sections available in the **Local vendor setup** page.

| Section | Description |
|---|---|
| General information | Maintain and update the local vendor profile, including the key organizational details required for supplier registration and business identification. |
| Ownership profile | Provide and manage company ownership and business classification information for supplier diversity and business categorization purposes. |
| Vendor contacts | Manage the local vendor contact details and add or remove contact persons as needed. |
| Approved categories | View the product categories that the local vendor is approved by the buyer to supply. These categories are defined by the buyer and used for procurement classification and sourcing purposes. |
| Category requests | Submit requests to become an approved supplier for additional product categories. These requests are subject to buyer approval and used for procurement classification and sourcing purposes. |
| Certificates | Manage compliance and certification records by maintaining certificate information, uploading supporting documents, and updating certification details as part of supplier compliance management. |
| Capabilities | Maintain and update your business capabilities, including areas of expertise, product categories, quality standards, and other capabilities that define your scope of supply. Make selections by using a tree-structured control that the buyer configures. |
| Bank details | View and manage the bank account information associated with the local vendor for payment processing and financial transactions. |

## Localization

Some global and local vendor fields and sections are relevant only for specific countries or regions. The system automatically shows or hides these fields and tabs based on the vendor's legal entity. This feature ensures that vendors see only the information required for their local regulatory and business requirements. Country/region-specific sections include:

- **Ownership profile**
- **Business information**
- **State tax IDs**

## Manage portal users

The supplier portal provides user management capabilities that vendor administrators can use to control who has access to the portal, what roles they hold, and which vendors they can work with. The **User management** page in the supplier portal provides:

- A list of all current portal users.
- The ability to create new portal user requests.
- A list of submitted access requests with their status.

To open the **User management** page, sign in to the supplier portal and complete one of the following steps:
    - From the home page, select **Users** from the **Vendor details** panel.
    - From the navigation menu, go to **Setup** \> **Users**.

### Request to add a new user

Vendors can request to add new users by submitting an access request. This process ensures that requests are reviewed and approved before the user receives access. You can grant global or local access, depending on the scope of work.

To create a new user request, follow these steps:

1. Open the **User management** page.
1. In the **Access requests** section, select **Request access**. <!-- KFM: We should describe how the contacts get added to **Choose contact** list. The form is generally confusing, so it might help to give field-by-field descriptions here. -->
1. Fill out the request form and select **Submit**.

Personnel from the purchaser company use the Supplier Engagement app review and approve the portal user access request.

### Manage existing users

After you provision a user, you can update their access and roles. The supplier portal supports role changes, vendor assignments, and deactivation to maintain proper access control.

Changes you make in the Supplier Engagement app automatically synchronize with Supply Chain Management, updating user access rights accordingly.

#### Assign or remove roles or local vendor access

Roles define what a portal user can do. A user can act as an administrator or a standard user. Vendor access controls which vendor records a user can view or manage. This access is useful when a supplier operates across multiple entities but users only need access to certain vendors. Global Vendor Administrators can change roles as needed.

To manage roles and local vendor access, follow these steps:

1. Open the **User management** page.
1. In the **Portal users** section, select a portal user's name to open their details.
1. Manage roles and local vendor access as follows:
    - To add a role, select **Add web role**. Then choose a role and select **Add**.
    - To remove a role, select the role to open a menu, and then select **Remove**.
    - To add the users to a local vendor, select **Add vendor access**. Then choose the local vendors to assign and select **Submit**.
    - To remove local vendor access, select the local vendor to remove to open a menu, and then select **Remove**.

1. Select **Submit** to save your changes and close the dialog.

#### Deactivate a user

When a user no longer requires access, administrators can deactivate the user. This action immediately prevents the user from signing in to the supplier portal.

To deactivate a user, follow these steps:

1. Open the **User management** page.
1. In the **Portal users** section, find the portal user you want to deactivate. At the right side of their row, open the **Options** (ellipsis) menu and select **Deactivate**.
1. Confirm the action. The system immediately revokes the user's portal access.

## Related information

- [Supplier portal overview](supplier-engagement-portal-overview.md)
- [Manage global vendor information](supplier-engagement-global-vendor-info.md)
- [Manage global vendor capabilities](supplier-engagement-global-vendor-capabilities.md)
- [Manage certificates](supplier-engagement-manage-certificates.md)
- [Manage supplier portal users](supplier-engagement-portal-users.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
