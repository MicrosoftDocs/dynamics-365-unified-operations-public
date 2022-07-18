---
# required metadata

title: Configure Cloud POS to use custom Azure AD application
description: This article explains how to configure Cloud POS to use custom AAD application.
author: boycez
ms.date: 07/18/2022
ms.topic: article
ms.prod:
ms.technology: 
# optional metadata
# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
# ms.custom:
ms.search.region: global
# ms.search.industry:
ms.author: boycez
ms.search.validFrom:
ms.dyn365.ops.version: 10.0.21
---

# Configure Cloud POS to use custom Azure AD application

[!include [banner](includes/banner.md)]

The out-of-the-box Cloud POS is pointing to the pre-registered Microsoft first party application in Azure Active Directory (AAD). This way anyone can just start using it without making any changes in AAD which is convenient. However, there could be circumstances which you might want to point your instance of CPOS to the custom AAD application you control. This article describes the required configuration steps to archive that.

## Set up custom Retail Server application in AAD

To create and configure a custom Retail Server application in AAD, follow these steps.

1.	Login into Azure Active Directory admin center with any AAD user account. The user doesn't have to be an administrator of any kind.
1.	Click **Azure Active Directory** on the navigation pane.
1.	Click **App registrations**, then click **New registration” to open the **Register an application** dialog. Provide values for the following fields.
a.	**Name** – Enter a custom name for the application. For instance, “Customized Retail Server”.
b.	**Support account types** – Select the default option **(Accounts in this organizational directory only (Microsoft only - Single tenant)**.
c.	**Redirect URI** - Optional field, leave it as blank.
d.	**Service Tree ID** - Optional field, leave it as blank.
1.	Click the **Register** button, which opens the configuration page for the newly registered application.
1.	Under **Overview \> Essentials** section, click the **Add an Application ID URI** link, then click **Set** besides the “Application ID URI”, take a note of the suggested value which is needed later while registering the AAD application within Commerce headquarters, and then click **Save** to accept the value. 
1.	Click **Add a scope** and provide values for the scope
e.	**Scope name** – Enter a custom name for the scope. For instance, “Legacy.Access.Full”.
f.	**Who can consent** – Based on your organization’s security policies, decide if both Admins and Users can accept or only Admins, and then make proper selection.
g.	**Admin consent display name** – Enter the consent’s display name. For instance, “Access Retail Server”.
h.	**Admin consent description** – Enter the description to be displayed to the end users. For instance, “Gives an access to Retail Server APIs”.
1.	Click the **Add scope** button.

## Set up custom CPOS application in AAD

To create and configure a custom CPOS application in AAD, follow these steps.

1.	Login into Azure Active Directory admin center with any AAD user account. The user doesn't have to be an administrator of any kind.
1.	Click **Azure Active Directory** on the navigation pane.
1.	Click **App registrations**, then click **New registration” to open the **Register an application** dialog. Provide values for the following fields.
i.	**Name** – Enter a custom name for the application. For instance, “Customized Cloud POS”.
j.	**Support account types** – Select the default option **(Accounts in this organizational directory only (Microsoft only - Single tenant)**.
k.	**Redirect URI** - Select **Single-page application (SPA)** in the dropdown and enter your CPOS URI in the input box.
l.	**Service Tree ID** - Optional field, leave it as blank.
1.	Click the **Register** button, which opens the configuration page for the newly registered application.
1.	Under **Manifest** section, set **oauth2AllowIdTokenImplicitFlow** and **oauth2AllowImplicitFlow** parameters to **true** , and then click **Save** to save the changes. 
1.	Under **Token configuration** section, add two claims:
a.	Click **Add optional claim**. In the prompt dialog, set **Token type** to **ID**, and then select the **sid** claim. Click **Add** button.
b.	Click **Add optional claim**. In the prompt dialog, set **Token type** to **Access**, and then select the **sid** claim. Click **Add** button.
1.	Under **API permissions** section, click **Add a permission**. In the prompt dialog, select **APIs my organization uses** tab, then type and search the Retail Server application you created in the above procedure (“Customized Retail Server”), and click **Add permissions**.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
