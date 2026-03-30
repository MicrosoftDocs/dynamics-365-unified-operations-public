---
title: Enable automatic linking of identity records to customer accounts
description: Learn how to enable automatic linking of identity records to customer accounts in Microsoft Dynamics 365 Commerce.
author: BrianShook
ms.date: 02/17/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2021-03-01
ms.custom: 
  - bap-template
---

# Enable automatic linking of identity records to customer accounts

[!include [banner](../includes/banner.md)]

This article describes how to enable automatic linking of identity records to customer accounts in Microsoft Dynamics 365 Commerce.

Use the Commerce automatic linking feature in business-to-business (B2B) and business-to-consumer (B2C) site flows to allow approved customers to sign up to a Microsoft Entra B2C tenant and be automatically linked to their existing customer record. You can also use the identity record automatic linking feature in B2C site flows to automatically link users who sign up to a Microsoft Entra tenant to their customer account record created earlier in Commerce through point of sale (POS), call center, or Commerce headquarters.

> [!WARNING]
> Use the identity record automatic linking feature with Microsoft Entra ID B2C as the identity provider. In the **sign up and sign in** user flow, keep the default setting for the local account sign-up page layout, which is the **Email Address** user attribute with the **Requires verification** option set to "Yes." This configuration ensures that the email verification functionality persists for the sign-up flow when using the automatic linking feature.

Commerce works with identity provider services such as Microsoft Entra B2C to store a user's authentication credentials such as username and password. A linking table in Commerce references the user's identity provider record to associate the authenticated user to a customer account in Commerce.

## Enable the automatic linking feature in Commerce headquarters

To enable the automatic linking feature for your environment in Commerce headquarters, follow these steps:

1. Go to **System administration \> Workspaces \> Feature management** and select the **All** tab.
1. Search for the feature named **Local Identity Record and Commerce Customer automatic linking**.
1. Select the feature, and then select **Enable now** in the properties pane.

> [!NOTE]
> For automatic linking to succeed, run the **1010 (Customers)** distribution schedule job before the customer signs in to the website. When you enable the automatic linking feature, you enable it for all channels in your environment. This feature is important to be aware of if you're hosting different types of sites within your environment.

## Automatic linking on B2B sites

A B2B site is a Commerce site connected to an online store with the **Customer type** property set to "B2B" during channel creation. For B2B sites, automatic linking of identity records to customer accounts is critical to the customer approval and sign-in process. You create customer records when you approve a B2B record or when a B2B administrator creates the user record. After the customer record exists, the user can navigate to the B2B site and sign in. When the user is directed to the Microsoft Entra B2C sign-in experience, they can proceed to sign up. When sign-up is complete, the user is redirected back to the B2B site. On this return call, Commerce reviews the automatic link options for the customer's initial sign-in.

The email address used as the user's Microsoft Entra B2C user ID is searched for across all of the B2B customer records within the legal entity. The Commerce automatic linking feature reviews customer records of type **person** where **isB2B** is set to "true" and then matches against the primary email address configured for the customer record.

For B2B sites, automatic linking performs the following checks:

- If only one customer record within the legal entity meets the matching condition, the user signing up is automatically linked to that record.
- If no customer records within the legal entity meet the matching conditions, Commerce generates a **CommerceIdentityNotFound** error with error code **Microsoft_Dynamics_CommerceIdentityNotFound**.
    - To send a user-facing message when the **CommerceIdentityNotFound** error occurs, in Commerce site builder, open your site's header module fragment, and then in the outline view, select the header module. In the properties pane on the right, for **Error message if customer not found**, enter a message (for example, "Your sign-up was successful, but your business user record hasn't yet been approved. Please try signing in at a later time or you may sign in once instructed your account has been approved."). Then save and publish the fragment.
- If more than one customer record within the legal entity is found to have matching conditions, Commerce generates a **CustomerServiceMultipleCustomerAccountsFoundErrorOccurredWhenAutoLinking** error with error code **Microsoft_Dynamics_Commerce_Runtime_MultipleCustomerAccountsFoundWithSameEmailAddress**.
    - To send a user-facing message when the **CommerceIdentityNotFound** error occurs, in Commerce site builder, open your site's header module fragment, and then in the outline view, select the header module. In the properties pane on the right, for **Multiple customers found error msg**, enter a message (for example, "Your sign-up was successful, but there's an issue associating to the business user account. Please try signing in at a later time."). Then save and publish the fragment.

## Automatic linking on B2C sites

A B2C site is a Commerce site connected to an online store with the **Customer type** property set to "B2C" during channel creation. For B2C sites, the automatic linking feature checks if a single customer account with the email address used for sign-up exists within the legal entity.

The automatic linking feature searches the email address used as the user's Microsoft Entra B2C user ID across all of the B2C customer records within the legal entity. It reviews customer records of type **person**.

For B2C sites, automatic linking performs the following checks:

- If only one customer record within the legal entity meets the matching condition, the user signing up is automatically linked to that record.
- If no customer records within the legal entity meet the matching condition, Commerce generates a new customer record that is linked to the identity provider record.
- If more than one customer record within the legal entity meets the matching conditions, Commerce generates a **CustomerServiceMultipleCustomerAccountsFoundErrorOccurredWhenAutoLinking** error with error code **Microsoft_Dynamics_Commerce_Runtime_MultipleCustomerAccountsFoundWithSameEmailAddress**.
    - To send a user-facing message when the **CommerceIdentityNotFound** error occurs, in Commerce site builder, open your site's header module fragment, and then in the outline view, select the header module. In the properties pane on the right, for **Multiple customers found error msg**, enter a message (for example, "Your sign-up was successful, but there's an issue associating to the business user account. Please try signing in at a later time."). Then save and publish the fragment.

> [!NOTE]
> - You can extend the Commerce notifications module to display error messages to users when error conditions are met.
> - If you set up social identity provider records in Microsoft Entra ID B2C, they automatically link to the same customer records with matching conditions if a single record is found. A Commerce customer account can link to both a local identity record and a social identity record simultaneously.

## Additional resources

[Configure your domain name](../configure-your-domain-name.md)

[Deploy a new e-commerce tenant](../deploy-ecommerce-site.md)

[Create an e-commerce site](../create-ecommerce-site.md)

[Associate a Dynamics 365 Commerce site with an online channel](../associate-site-online-store.md)

[Manage robots.txt files](../manage-robots-txt-files.md)

[Upload URL redirects in bulk](upload-bulk-redirects.md)

[Set up a B2C tenant in Commerce](set-up-B2C-tenant.md)

[Set up custom pages for user logins](../custom-pages-user-logins.md)

[Configure multiple B2C tenants in a Commerce environment](../configure-multi-B2C-tenants.md)

[Add support for a content delivery network (CDN)](../add-cdn-support.md)

[Enable location-based store detection](../enable-store-detection.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
