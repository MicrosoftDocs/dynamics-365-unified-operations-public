---
# required metadata

title: Enable automatic linking of identity records to customer accounts 
description: This topic describes how to enable automatic linking of identity records to customer accounts in Microsoft Dynamics 365 Commerce.
author: BrianShook
ms.date: 07/21/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: brshoo
ms.search.validFrom: 2021-03-01
ms.dyn365.ops.version: 

---

# Enable automatic linking of identity records to customer accounts 

[!include [banner](includes/banner.md)]

This topic describes how to enable automatic linking of identity records to customer accounts in Microsoft Dynamics 365 Commerce.

This topic covers the identity record automatic linking feature to enable authenticated users to be automatically linked to an existing customer account record. This feature is used in business-to-business (B2B) and business-to-consumer (B2C) site flows to allow approved customers to sign up to an Azure Active Directory (Azure AD) B2C tenant and be linked to their created customer record. The identity record automatic linking feature can also be used in B2C site flows to automatically link users who sign up to a Azure AD tenant to their customer account record created earlier in Commerce through point of sale (POS), call center, or Commerce headquarters.

> [!WARNING] 
> The identity record automatic linking feature should be used with Azure AD B2C as the identity provider. In the "sign up and sign in" user flow, the local account sign up page layout should retain the default setting of the **Email Address** user attribute with the **Requires verification** option set to "Yes." This configuration ensures that the email verification functionality persists for the sign-up flow when using the automatic linking feature.

Commerce works with identity provider services such as Azure AD B2C to store a user's authentication credentials such as username and password. The user's identity provider  record is referenced by a linking table in Commerce to associate the authenticated user to a customer account in Commerce. 

## Enable the automatic linking feature in Commerce headquarters 

To enable the automatic linking feature for your environment in Commerce headquarters, follow these steps. 

1. Go to **System administration \> Workspaces \> Feature management** and select the **All** tab. 
1. Search for the feature named **Local Identity Record and Commerce Customer automatic linking**.
1. Select the feature, and then select **Enable now** in the properties pane.

> [!NOTE]
> Once enabled, the automatic linking feature will be enabled for all channels in your environment. Keep this in mind if you are hosting different types of sites within your environment.

## Automatic linking on B2B sites 

A B2B site is a Commerce site connected to an online store with the **Customer type** property set to "B2B" during channel creation. For B2B sites, automatic linking of identity records to customer accounts is critical to the customer approval and sign-in process. Customer records are created when a B2B record is approved, or when a B2B administrator creates the user record. Once the customer record exists, the user will navigate to the B2B site and sign in. Once directed to the Azure AD B2C sign-in experience, the user can then proceed to sign up. When sign-up is complete, the user is redirected back to the B2B site. On this return call, Commerce will review the automatic link options for the customer's initial sign-in.

The email address used as the user's Azure AD B2C user ID will be searched for across all of the B2B customer records within the legal entity. The Commerce automatic linking feature  reviews customer records of type **person** where **isB2B** is set to "true" and then matches against the primary email address configured for the customer record.

For B2B sites, automatic linking will perform the following checks:

- If only one customer record within the legal entity meets the matching condition, the user signing up is automatically linked to that record.
- If no customer records within the legal entity meet the matching conditions, Commerce will generate a **CommerceIdentityNotFound** error with error code **Microsoft_Dynamics_CommerceIdentityNotFound**.
- If more than one customer record within the legal entity is found to have matching conditions, Commerce will generate a **CustomerServiceMultipleCustomerAccountsFoundErrorOccurredWhenAutoLinking** error with error code **Microsoft_Dynamics_Commerce_Runtime_MultipleCustomerAccountsFoundWithSameEmailAddress**.

## Automatic linking on B2C sites

A B2C site is a Commerce site connected to an online store with the **Customer type** property set to "B2C" during channel creation. For B2C sites, the automatic linking feature will review if a single customer account with the email address used for sign-up exists within the legal entity.

The email address used as the user's Azure AD B2C user ID will be searched for across all of the B2C customer records within the legal entity. The Commerce automatic linking feature reviews customer records of type **person**.

For B2C sites, automatic linking will perform the following checks:

- If only one customer record within the legal entity meets the matching condition, the user signing up is automatically linked to that record.
- If no customer records within the legal entity meet the matching condition, Commerce will generate a new customer record that is linked to the identity provider record. 
- If more than one customer record within the legal entity meets the matching conditions, Commerce will generate a **CustomerServiceMultipleCustomerAccountsFoundErrorOccurredWhenAutoLinking** error with error code **Microsoft_Dynamics_Commerce_Runtime_MultipleCustomerAccountsFoundWithSameEmailAddress**.

> [!NOTE]
> - The Commerce notifications module can be extended to display error messages to users when error conditions are met.
> - Social identity provider records set up in Azure AD B2C will also automatically link to the same customer records with matching conditions if a single record is found. A Commerce customer account can be linked to both a local identity record and a social identity record simultaneously.

## Additional resources

[Configure your domain name](configure-your-domain-name.md)

[Deploy a new e-commerce tenant](deploy-ecommerce-site.md)

[Create an e-commerce site](create-ecommerce-site.md)

[Associate a Dynamics 365 Commerce site with an online channel](associate-site-online-store.md)

[Manage robots.txt files](manage-robots-txt-files.md)

[Upload URL redirects in bulk](upload-bulk-redirects.md)

[Set up a B2C tenant in Commerce](set-up-B2C-tenant.md)

[Set up custom pages for user logins](custom-pages-user-logins.md)

[Configure multiple B2C tenants in a Commerce environment](configure-multi-B2C-tenants.md)

[Add support for a content delivery network (CDN)](add-cdn-support.md)

[Enable location-based store detection](enable-store-detection.md)
