---
# required metadata

title: Enable automatic linking of identity records to customer accounts 
description: This topic reviews the ability to automatic link identity records to customer accounts in Microsoft Dynamics 365 Commerce.
author: BrianShook
manager: annbe
ms.date: 03/01/2021
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
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
[!include [banner](includes/preview-banner.md)]

This topic reviews the ability to automatic link identity records to customer accounts in Microsoft Dynamics 365 Commerce.

This topic covers the identity record automatic linking feature to enable authenticated users to be automatically linked to an existing customer account record. This feature is used in B2B site flows to allow approved customers to sign-up in an Azure Active Directory (AAD) B2C tenant and be linked to their created customer record. It can also be used in B2C site flows to automatically link a user signing up to a customer account record created earlier in Dynamics 365 Commerce through Point of Sale, Call Center, or Headquarters.

[!WARNING] Please note that this feature should be used with AAD B2C as the identity provider. In the 'Sign up and sign in' user flow, the "Local account sign up page" page layout should retain the default setting of the "Email Address" User attribute with the **Requires verification** option set to "Yes". Ensure the email verification remains for the sign-up flow if using the automatic linking feature.

Dynamics 365 Commerce works with an Identity Provider service such as Azure Active Directory B2C to store a user's authentication specific details such as username and password. The identity record for the user in the Identity Provider is referenced by a linking table in Commerce to link the authenticated user to a customer account in Commerce. 

## Enable the automatic linking feature in Commerce headquarters 

To enable automatic linking for your environment, in Headquarters navigate to the **Feature management** page. 

Under **All** features, search for the feature flag named **Local Identity Record and Commerce Customer automatic linking**. Select **Enable** to enable this feature.

[!NOTE] This feature will be enabled for all channels in the environment which it is enabled. Keep this in mind if you are hosting different types of sites within the environment.

## Automatic linking on B2B sites 

A B2B site is a Commerce site connected to an **Online store** with the **Customer type** property set to "B2B" upon the channel creation. For B2B Sites, automatic linking is crucial to the customer approval and login process. Customer records are created when a B2B prospect record is approved, or a B2B Admin creates the user record. Once the customer record exists, the user will navigate to the site and click sign-in. Once directed to the AAD B2C sign-in experience, the user can choose to **sign-up**. When the sign-up is complete, the user is re-directed back to the B2B Site. On this return call, Commerce will review the automatic link options for the customer's initial login.

The email used as the user's AAD B2C User ID will be searched across the B2B customer records within the legal entity. automatic linking is reviewing customer records of type **person** where **isB2B** is true, matching against the primary email address set for the customer record.

For B2B sites, automatic linking will perform the various checks:

- If only one customer record within the legal entity meets the matching condition, the signing in user is automatically linked to that record.
- If **no customer records** within the legal entity meet the matching condition, the Commerce service will throw a **CommerceIdentityNotFound** error (error code: *Microsoft_Dynamics_CommerceIdentityNotFound*).
- If **more than one** customer record is found within the legal entity with matching conditions, the Commerce service will throw a **CustomerServiceMultipleCustomerAccountsFoundErrorOccurredWhenAutoLinking** error (error code:  *Microsoft_Dynamics_Commerce_Runtime_MultipleCustomerAccountsFoundWithSameEmailAddress*).

## Automatic linking on B2C sites

A B2C site is a Commerce site connected to an **Online store** with the **Customer type** property set to "B2C" upon the channel creation. For B2C Sites, auto linking will review if a single customer account exists within the legal entity with the email utilized on sign up.

The email used as the user's AAD B2C User ID will be searched across the B2C customer records within the legal entity. Auto linking is reviewing customer records of type **person**.

For B2C sites, auto linking will perform the various checks:

- If only one customer record within the legal entity meets the matching condition, the signing up user is automatic linked to that record.
- If **no customer records** within the legal entity meet the matching condition, the Commerce service will create a new customer record (linked to the identity provider record). 
- If **more than one** customer record is found within the legal entity with matching conditions, the Commerce service will throw a **CustomerServiceMultipleCustomerAccountsFoundErrorOccurredWhenAutoLinking** error (error code:  *Microsoft_Dynamics_Commerce_Runtime_MultipleCustomerAccountsFoundWithSameEmailAddress*).

## Additional information

- The Notifications module can be extended to surface error messages to the user if error conditions are met.
- Social Identity Provider records set up in AAD B2C will also automatically link to the same customer record with matching conditions if a single record is found. A Commerce customer account can be linked to both a local identity record and Social Identity Records simultaneously.
