---
title: Device activation of a customized Modern POS
description: Learn how to configure Microsoft Dynamics 365 Commerce headquarters when a customized application is used.
author: jashanno
ms.date: 02/19/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2017-09-30
ms.custom: 
  - bap-template
---

# Device activation of a customized Modern POS

[!INCLUDE [banner](../includes/banner.md)]
[!include [banner](../includes/mpos-hybrid-apps-deprecation-banner.md)]

This article explains how to configure Microsoft Dynamics 365 Commerce headquarters so that device activation works correctly when a customized Modern POS application is used. It describes the steps that are required to obtain the customized reply address and enter that value in headquarters.

Modern POS is a client-side component for Microsoft Dynamics 365 Commerce. To use the POS, you must perform device activation. Device activation uses Microsoft Entra to authenticate users. Enhanced functionality in this area modified the device activation flow to take better advantage of the Web Account Manager service. As part of this enhancement, there's now enhanced security for the authentication approval process. This enhanced security requires more configuration in headquarters when the POS is customized, because a specific, unique value is now required for the callback URI. (The callback URI is also known as the redirect URI.)

By default, Modern POS is already registered for this callback URI. However, when you customize Modern POS, you change the callback URI. You must correctly configure the callback URI so that it works. This article describes the steps that you must follow to complete this configuration. If you don't complete this configuration, you receive an error message when you try to perform device activation in the customized POS application. This error message resembles the following example:

> Microsoft EntraSTS50011: The reply address 'ms-appx-web://Microsoft.Microsoft Entra ID.BrokerPlugin/[...]' doesn't match the reply addresses configured for the application.

The reply address depends on the Modern POS package SID that appears at the end of the error message. It's a function of the Package Family Name (PFN), so it depends on a name and public key. This means that when you customize Modern POS and sign it with your company certificate, the SID changes. The change is based on the certificate and not the package version. As long as the entire package isn't different and the certificate remains the same (which can be renewed to keep the same signature), the SID remains the same.

> [!NOTE]
> Use the customized Modern POS application one time before you configure Dynamics 365 headquarters. By using this approach, you can see what the error message looks like and more easily obtain the customized reply address.

## Setup

The following steps are required so that device activation works correctly when the customized Modern POS application is used. You create two Microsoft Entra applications: one for Modern POS and one for Commerce Scale Unit. The Commerce Scale Unit Microsoft Entra application is required because the POS uses resources through Commerce Scale Unit. Therefore, you use both Microsoft Entra applications when you use the POS. In this scenario, Commerce Scale Unit serves as the endpoint for protected resources that the POS requests.

### Create the Commerce Scale Unit Microsoft Entra application

1. In a web browser, go to <https://portal.azure.com/>.
1. Sign in by using Microsoft Entra credentials that have enough permission to create Microsoft Entra applications.
1. Select **Microsoft Entra ID** from the list of Azure services, and then select **App registrations** from the leftmost menu that appears.
1. Create the Commerce Scale Unit Microsoft Entra application by selecting **New registration** and entering the following values:

    - **Name:** Enter **Customized Commerce Scale Unit**. You can enter any other unique value, but be sure to make a note of the name you enter.
    - **Supported account types:** Select the value **Accounts in this organization directory only** unless you plan to use this application registration across multiple tenants, which requires the next value **Accounts in any organizational directory**. This selection isn't typical.
    - **Redirect URI:** You can leave this value blank but you need to verify that the initial drop-down selection is set to **Web**.

1. Select **Register** at the bottom of the page. The page changes to the newly created Microsoft Entra application.
1. Select **Application ID URI** where it has a link stating **Add an Application ID URI**. You can also reach this page from the left menu by selecting **Expose an API**.
1. On the tile that opens, select the **Application ID URI** value that states **Set**. Copy the value shown before selecting the **Save** button. You paste this value into the DLLHost.exe.config file for POS in the next section.
1. Select **Save** to set this URI.
1. Select the **Add a scope** button.
1. In the slider that appears, enter the following values:

    - **Scope name:** Enter **AccessRetailServer**. You can enter any other unique value, but be sure to make a note of the name you enter.
    - **Who can consent**: Select the **Admins and users** option.
    - **Admin consent display name:** Enter **AccessRetailServer**. For simplicity, make this value match the **Scope name** value.
    - **Admin consent description:** Enter **AccessRetailServer**. You can enter any value here. This value notes the reason for the scope.
    - The fields **User consent display name** and **User consent description** aren't used.
    - **State:** Verify that **Enabled** is selected.

1. Select the **Add scope** button.
1. Select the **Overview** tab on the leftmost menu. Verify that the **Application ID URI** value matches the value you copied in step seven.

> [!NOTE]
> Don't close the web browser window because you use it again later in this article.

### Update the Modern POS configuration

1. In File Explorer, go to **C:\Program Files (x86)\Microsoft Dynamics 365\70\Retail Modern POS\ClientBroker**. (This path assumes that the Microsoft Windows operating system on the computer is based on the x64 architecture.)
1. In File Explorer, select **File** \> **Open Windows PowerShell** \> **Open Windows PowerShell as administrator**.
1. In the Microsoft Windows PowerShell window that appears, enter **notepad DLLHost.exe.config**, and then press the Enter key. (The Windows PowerShell window already points to the current file directory.)
1. In the Notepad window that appears, find the value that corresponds to the **Microsoft Entra IDRetailServerResourceId** key. (By default, this value is `https://commerce.dynamics.com`.) Then paste the App ID URI value that you copied in step 7 in the previous section.
1. Select **File** \> **Save**.

> [!NOTE]
> Don't close the Notepad window, because you use it again in the next section.
> Another way to perform the preceding steps is to use a script or a post-step installation customization.

### Create the customized Modern POS Microsoft Entra application

1. Return to the web browser window where <https://portal.azure.com/> is open, and create the Retail Modern POS Microsoft Entra application by repeating steps 3-5 in the "Create the Commerce Scale Unit Microsoft Entra application" section. However, enter the following values this time:

    - **Name:** Enter **Customized Retail Modern POS**. (You can enter any other unique value, but be sure to make a note of the name entered.)
    - **Supported account types:** Select the value **Accounts in this organization directory only** unless you plan to use this application registration across multiple tenants, which requires the next value **Accounts in any organizational directory**. This selection isn't typical.
    - **Redirect URI:** Change the initial drop-down value to **Public client/native (mobile & desktop)**. Enter the value for this type of Redirect URI that appears at the beginning of this article in the Modern POS error message received. Enter the reply address (redirect URI) that corresponds to that error message. The value starts with **ms-appx-web://Microsoft.Microsoft Entra ID.BrokerPlugin/[...]**.

        > [!NOTE]
        > - You can also see the reply address (redirect URI) in Event Viewer in Windows, under **Microsoft-Dynamics-Commerce-ModernPos/Operational**. The event ID is 40619. The error message starts with the following text: "This UWP application was assigned the following callback URI to be used while interacting with Microsoft Entra ID: ms-appx-web://Microsoft.Microsoft Entra ID.BrokerPlugIn/S-1-15-2-[...]"
        > - After you create the Microsoft Entra application, you can specify more redirect URIs as you require. If multiple packages that have different callback URIs are generated for any reason, keep this single Microsoft Entra application, and maintain all redirect URIs in it.

1. Validate the value in the **Redirect URI** field. Then select **Create**, and wait until the operation is successfully completed. (If an error occurs, address it, and then try again.)

    A tile appears that shows the details of the new customized Retail Modern POS Microsoft Entra application.

1. Select **Register** at the bottom of the page. The page changes to the newly created Microsoft Entra application.
1. Find the **Application (client) ID** field, and copy the value. Switch to the notepad you opened in the previous section (or follow the preceding section **Update the Modern POS configuration** to open the **DLLHost.exe.config** file) to navigate to the value corresponding to **Microsoft Entra IDClientId**. Paste in the value for this field that you copied at the beginning of this step and then save the file (as shown in step 5 of the same section).
1. Returning to the web browser, in the leftmost menu, select the **API permissions** option.
1. On the **API permissions** tile, select **+ Add a permission**.
1. On the slider that appears, first select the **My APIs** heading. Then select the API titled **Customized Commerce Scale Unit** or whatever value you entered as the name in step 4 at the beginning of this document.
1. Under the **Select permissions** subheading, select **AccessRetailServer** or whatever value you entered as the scope name in step 10 at the beginning of this document.
1. Select **Add permissions** at the bottom of the slider.
1. Select **Grant admin consent for \<your Microsoft Entra name\>**. Select **Yes**. This grants consent and you can verify it with the **Granted** displaying in the **Status** column in the **AccessRetailServer** row.

    > [!NOTE]
    > Granting consent isn't required, but it simplifies the process by consenting in advance for all users in your tenant (and you as the Admin). If you don't complete this step, each user is asked for consent the first time that they try to activate Modern POS.

### Configure Dynamics 365 headquarters

The previous steps are required so that the Modern POS application can authenticate. Now, follow these steps to add the new Microsoft Entra applications to the list of safe programs in headquarters, so that the requests are authorized. (A list of safe programs is sometimes also referred to as a safe list.)

1. In a web browser, go to the headquarters URL, and sign in by using Microsoft Entra credentials.
1. Go to **Retail and Commerce > Headquarters setup > Parameters > Commerce shared parameters**.
1. On the **Identity Providers** tab, in the **Identity providers** section, select the provider that begins with `HTTPS://sts.windows.net/`. The values in the **Relying parties** section are updated, based on the provider that you selected.
1. In the **Relying parties** section, select **+ Add**, and enter the following values:

    - **ClientId:** Enter the value that you copied in step 3 in the previous section and then pasted into the DLLHost.exe.config file in step 13.
    - **Type:** Select **Public**.
    - **UserType:** Select **Worker**.
    - **Name:** Enter a description to help users understand what this entry references.

1. On the Action Pane, select **Save**. The relying party that you created should remain selected.
1. In the **Server resource IDs** section, select **+ Add**, and enter the following values:

    - **Server Resource Id:** Enter the URL that you copied in step 4 in the "Update the Modern POS configuration" section. (You originally created this value in step 4 in the "Create the Commerce Scale Unit Microsoft Entra application" section.)
    - **Name:** Enter a description to help users understand what this entry references.

1. On the Action Pane, select **Save**.
1. Go to **Retail and Commerce > Retail and CommerceIT** > **Distribution schedule**.
1. Select job **1110** (**Global configuration**), and then, on the Action Pane, select **Run now**. This job synchronizes the new data. However, a cache in Commerce Scale Unit isn't updated for several minutes. Therefore, if you need an immediate update, you must recycle the Commerce Scale Unit application pool.

    > [!NOTE]
    > For best results, verify that Modern POS is closed, and that no instances of DLLHost.exe exist in Task Manager.

### Perform modern POS device activation

Activate the modern POS device. If you still experience problems, open Event Viewer in Windows, and view the logs that correspond to modern POS. Look for warnings and errors that might help you determine which steps you missed in the previous sections.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
