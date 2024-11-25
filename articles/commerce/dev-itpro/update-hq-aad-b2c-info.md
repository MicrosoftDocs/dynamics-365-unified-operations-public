---
title: Update Commerce headquarters with the new Microsoft Entra B2C information
description: This article describes how to update Microsoft Dynamics 365 Commerce headquarters with new Microsoft Entra business-to-consumer (B2C) information.
author: BrianShook
ms.date: 08/02/2024
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2020-02-13
ms.custom: 
  - bap-template
---

# Update Commerce headquarters with the new Microsoft Entra B2C information

[!include [banner](../includes/banner.md)]

This article describes how to update Microsoft Dynamics 365 Commerce headquarters with new Microsoft Entra business-to-consumer (B2C) information.

Once the Microsoft Entra B2C provisioning steps above are completed, the Microsoft Entra B2C application must be registered in your Dynamics 365 Commerce environment.

To update headquarters with the new Microsoft Entra B2C information, follow these steps.

1. In Commerce, go to **Commerce Shared Parameters** and select **Identity Providers** in the left menu.
1. Under **Identity Providers**, do the following:
    1. In the **Issuer** box, enter the identity provider issuer string. To find your issuer string, see [Obtain issuer string for headquarters setup](#obtain-issuer-string-for-headquarters-setup) below.
    1. In the **Name** box, enter a name for your issuer record.
    1. In the **Type** box, enter **Microsoft Entra ID B2C (id_token)**.
1. Under **Relying Parties**, with the above B2C identity provider item selected, do the following:
    1. In the **ClientID** box, enter your B2C application ID, which you can find in the **Application ID** box of your B2C application's properties page.
    1. In the **Type** box, enter **Public**.
    1. In the **User Type** box, enter **Customer**.
1. On the action pane, select **Save**.
1. In the Commerce search box, search for **Distribution schedule**
1. In the left navigation menu of the **Distribution schedules** page, select job **1110 Global configuration**.
1. On the action pane, select **Run Now**.

### Obtain issuer string for headquarters setup

To obtain your identity provider issuer string, follow these steps.

1. On the Microsoft Entra B2C page of the Azure portal, navigate to your **Sign up and sign in** user flow.
1. Select **Page layouts** in the left navigation menu, under **Layout name** select **Unified sign up or sign in page**, and then select **Run user flow**.
1. Ensure that your application is set to your intended Microsoft Entra B2C application created above, and then select the user flow link that appears under the **Run user flow** header that includes ``.../.well-known/openid-configuration?p=<B2CSIGN-INPOLICY>``. (Don't select **Run user flow**.) A new tab will open displaying metadata for the policy to collect the issuer string.
1. On the metadata page displayed in your browser tab, copy the identity provider issuer string (the value for **issuer** starting with "https://" and ending with "/v2.0/") that looks similar to the following example.
   - ``https://login.fabrikam.com/011115c3-0113-4f43-b5e2-df01266e24ae/v2.0/``.
 
**OR**: To construct the same metadata URL manually, do the following steps.

1. Create a metadata address URL in the following format using your B2C tenant and policy: ``https://<B2CTENANTNAME>.b2clogin.com/<B2CTENANTNAME>.onmicrosoft.com/v2.0/.well-known/openid-configuration?p=<B2CSIGN-INPOLICY>``
    - Example: ``https://d365plc.b2clogin.com/d365plc.onmicrosoft.com/v2.0/.well-known/openid-configuration?p=B2C_1_signinup``.
1. Enter the metadata address URL into a browser address bar.
1. In the metadata, copy the identity provider issuer URL (the value for **"issuer"**).
    - Example: ``https://login.fabrikam.com/011115c3-0113-4f43-b5e2-df01266e24ae/v2.0/``.

## Next steps

To continue the process of setting up a B2C tenant in Commerce, proceed to [Configure your B2C tenant in Commerce site builder](config-b2c-tenant-site-builder.md).

## Additional resources

[Set up a B2C tenant in Commerce](set-up-B2C-tenant.md)

[Create or link to an existing Microsoft Entra B2C tenant in the Azure portal](create-link-aad-b2c-tenant.md)

[Create the B2C application](create-b2c-app.md)

[Create user flow policies](create-user-flow-policies.md)

[Add social identity providers (Optional)](add-social-identity-providers.md)

[Configure your B2C tenant in Commerce site builder](config-b2c-tenant-site-builder.md)

[Additional B2C information](additional-b2c-info.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
