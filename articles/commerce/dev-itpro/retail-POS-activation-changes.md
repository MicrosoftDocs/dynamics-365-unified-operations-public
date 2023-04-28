---
title: Device activation of a customized Modern POS
description: This article explains how to configure Microsoft Dynamics 365 Commerce Headquarters when a customized application is used.
author: jashanno
ms.date: 04/28/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: jashanno
ms.search.validFrom: 2017-09-30
ms.dyn365.ops.version: Application update 3
---

# Device activation of a customized Modern POS

[!INCLUDE [banner](../includes/banner.md)]
[!include [banner](../includes/mpos-hybrid-apps-deprecation-banner.md)]


This article explains how to configure Microsoft Dynamics 365 Commerce Headquarters so that device activation works correctly when a customized Modern POS application is used. It describes the steps that are required in order to obtain the customized reply address and enter that value in Headquarters.

Modern POS is a client-side component for Microsoft Dynamics 365 Commerce. To use the POS, you must perform device activation. Device activation uses Microsoft Azure Active Directory (Azure AD) to authenticate users. Enhanced functionality in this area has modified the device activation flow to take better advantage of the Web Account Manager service. As part of this enhancement, there is now enhanced security for the authentication approval process. This enhanced security requires additional configuration in Headquarters when the POS is customized, because a specific, unique value is now required for the callback URI. (The callback URI is also known as the redirect URI.)

By default, Modern POS is already registered for this callback URI. However, when customized, the callback URI is changed. Therefore, it must be correctly configured so that it works again. This article describes the steps that you must follow to complete this configuration. If this configuration isn't completed, you receive an error message when you try to perform device activation in the customized POS application. This error message resembles the following example:

> AADSTS50011: The reply address 'ms-appx-web://Microsoft.AAD.BrokerPlugin/[...]' does not match the reply addresses configured for the application.

The reply address is dependent on the Modern POS package SID that is shown at the end of the above error message. This is a function of the Package Family Name (PFN), so it is dependent on a name and public key. This means that when you customize Modern POS and sign it with your company certificate, the SID will change. The change is based on the certificate and not the package version, so as long as the entire package is not different and the certificate remains the same (which can be renewed to keep the same signature), then the SID will remain the same.

> [!NOTE]
> We recommend that you try to use the customized Modern POS application one time before you configure Dynamics 365 headquarters. In this way, you can see what the error message looks like and more easily obtain the customized reply address.

## Setup

The following steps are required so that device activation works correctly when the customized Modern POS application is used. You will create two Azure AD applications: one for Modern POS and one for Commerce Scale Unit. The Commerce Scale Unit Azure AD application is required because the POS uses resources through Commerce Scale Unit. Therefore, both Azure AD applications are used when the POS is used. In this scenario, Commerce Scale Unit serves as the endpoint for protected resources that the POS requests.

### Create the Commerce Scale Unit Azure AD application

1. In a web browser, go to <https://portal.azure.com/>.
2. Sign in by using Azure AD credentials that have enough permission to create Azure AD applications.
3. Select **Azure Active Directory** from the list of Azure services, then select **App registrations** from the leftmost menu that appears.
4. Create the Commerce Scale Unit Azure AD application by selecting **New registration** and entering the following values:

    - **Name:** Enter **Customized Commerce Scale Unit**. You can enter any other unique value, but be sure to make a note of the name entered.
    - **Supported account types:** Select the value **Accounts in this organization directory only** unless this application registration will be used across multiple tenants, which would require the next value **Accounts in any organizational directory**. Note that this selection is not typical.
    - **Redirect URI:** This value can be left blank but you need to verify that the initial drop-down selection is set to **Web**.

5. Select **Register** at the bottom of the page. The page will change to the newly created Azure AD application.
6. Select **Application ID URI** where it has a link stating **Add an Application ID URI**. This page can also be reached from the left menu by selecting **Expose an API**.
7. On the tile that opens, select the **Application ID URI** value that states **Set**. Copy the value shown before selecting the **Save** button. You will paste this value into the DLLHost.exe.config file for POS in the next section.
8. Select **Save** to set this URI.
9. Select the **Add a scope** button.
10. In the slider that appears, enter the following values:

    - **Scope name:** Enter **AccessRetailServer**. You can enter any other unique value, but be sure to make a note of the name entered.
    - **Who can consent**: Select the **Admins and users** option.
    - **Admin consent display name:** Enter **AccessRetailServer**. For simplicity, make this value match the **Scope name** above.
    - **Admin consent description:** Enter **AccessRetailServer**. You can enter any value here. This is used noting the reason for the scope.
    - The fields **User consent display name** and **User consent description** will not be used.
    - **State:** Verify that **Enabled** is selected.

11. Select the **Add scope** button.
12. Select the **Overview** tab on the leftmost menu. Verify that the **Application ID URI** value matches what was copied back in step seven.

> [!NOTE]
> Do not close the web browser window because you will use it again later in this article.

### Update the Modern POS configuration

1. In File Explorer, go to **C:\\Program Files (x86)\\Microsoft Dynamics 365\\70\\Retail Modern POS\\ClientBroker**. (This path assumes that the Microsoft Windows operating system on the computer is based on the x64 architecture.)
2. In File Explorer, select **File** \> **Open Windows PowerShell** \> **Open Windows PowerShell as administrator**.
3. In the Microsoft Windows PowerShell window that appears, enter **notepad DLLHost.exe.config**, and then press the Enter key. (The Windows PowerShell window will already be pointed to the current file directory.)
4. In the Notepad window that appears, find the value that corresponds to the **AADRetailServerResourceId** key. (By default, this value is `https://commerce.dynamics.com`.) Then paste the App ID URI value that you copied in step 7 in the previous section.
5. Select **File** \> **Save**.

> [!NOTE]
> Don't close the Notepad window, because you will use it again in the next section.
> Another way to perform the above steps would be to use a script or a post-step installation customization.

### Create the customized Modern POS Azure AD application

1. Return to the web browser window where <https://portal.azure.com/> is open, and create the Retail Modern POS Azure AD application by repeating steps 3-5 in the "Create the Commerce Scale Unit Azure AD application" section. However, enter the following values this time:

    - **Name:** Enter **Customized Retail Modern POS**. (You can enter any other unique value, but be sure to make a note of the name entered.)
    - **Supported account types:** Select the value **Accounts in this organization directory only** unless this application registration will be used across multiple tenants, which would require the next value **Accounts in any organizational directory**. Note that this selection is not typical.
    - **Redirect URI:** The initial drop-down value should be changed to **Public client/native (mobile & desktop)**. The value to enter for this type of Redirect URI is the value shown at the beginning of this article in the Modern POS error message received. Enter the reply address (redirect URI) that corresponds to that error message. The value will start with **ms-appx-web://Microsoft.AAD.BrokerPlugin/[...]**.

        > [!NOTE]
        > - You can also see the reply address (redirect URI) in Event Viewer in Windows, under **Microsoft-Dynamics-Commerce-ModernPos/Operational**. The event ID is 40619. The error message will start with the following text: "This UWP application was assigned the following callback URI to be used while interacting with Azure AD: ms-appx-web://Microsoft.AAD.BrokerPlugIn/S-1-15-2-[...]"
        > - After the Azure AD application is created, you can specify additional redirect URIs as you require. If multiple packages that have different callback URIs have been generated for any reason, keep this single Azure AD application, and maintain all redirect URIs in it.

2. It is important to validate this value in the **Redirect URI** field. Then select **Create**, and wait until the operation is successfully completed. (If an error occurs, address it, and then try again.)

    A tile appears that shows the details of the new customized Retail Modern POS Azure AD application.

3. Select **Register** at the bottom of the page. The page will change to the newly created Azure AD application.
4. Find the **Application (client) ID** field, and copy the value. Switch to the notepad you opened in the previous section (or follow the above section **Update the Modern POS configuration** to open the **DLLHost.exe.config** file) to navigate to the value corresponding to **AADClientId**. Paste in the value for this field that was copied at the beginning of this step and then save the file (as shown in step 5 of the same section).
5. Returning to the web browser, in the leftmost menu, select the **API permissions** option.
6. On the **API permissions** tile, select **+ Add a permission**.
7. On the slider that appears, first select the **My APIs** heading. Then select the API titled **Customized Commerce Scale Unit** or whatever value was entered as the name in step 4 at the beginning of this document.
8. Under the **Select permissions** sub-heading, select **AccessRetailServer** or whatever value was entered as the scope name in step 10 at the beginning of this document.
9. Select **Add permissions** at the bottom of the slider.
10. Select **Grant admin consent for \<your AAD name\>**. Select **Yes**. This grants consent and can be verified with the **Granted** displaying in the **Status** column in the **AccessRetailServer** row.

    > [!NOTE]
    > Granting consent is not required, but simplifies the process by consenting in advance for all users in your tenant (and you as the Admin). If this step is not completed, then each user will be asked for consent the first time that they try to activate Modern POS.

### Configure Dynamics 365 Headquarters

The previous steps were required so that the Modern POS application can be authenticated. You must now follow these steps to add the new Azure AD applications to the list of safe programs in Headquarters, so that the requests are authorized. (A list of safe programs is sometimes also referred to as a safe list.)

1. In a web browser, go to the Headquarters URL, and sign in by using Azure AD credentials.
2. Go to **Retail and Commerce** &gt; **Headquarters setup** &gt; **Parameters** &gt; **Commerce shared parameters**.
3. On the **Identity Providers** tab, in the **Identity providers** section, select the provider that begins with `HTTPS://sts.windows.net/`. The values in the **Relying parties** section are updated, based on the provider that you selected.
4. In the **Relying parties** section, select **+ Add**, and enter the following values:

    - **ClientId:** Enter the value that you copied in step 3 in the previous section and then pasted into the DLLHost.exe.config file in step 13.
    - **Type:** Select **Public**.
    - **UserType:** Select **Worker**.
    - **Name:** Enter a description to help users understand what this entry references.

5. On the Action Pane, select **Save**. The relying party that you just created should remain selected.
6. In the **Server resource IDs** section, select **+ Add**, and enter the following values:

    - **Server Resource Id:** Enter the URL that you copied in step 4 in the "Update the Modern POS configuration" section. (You originally created this value in step 4 in the "Create the Commerce Scale Unit Azure AD application" section.)
    - **Name:** Enter a description to help users understand what this entry references.

7. On the Action Pane, select **Save**.
8. Go to **Retail and Commerce** &gt; **Retail and CommerceIT** \> **Distribution schedule**.
9. Select job **1110** (**Global configuration**), and then, on the Action Pane, select **Run now**. This job synchronizes the new data. However, there is a cache in Commerce Scale Unit that won't be updated for several minutes. Therefore, if you require an immediate update, the Commerce Scale Unit application pool must be recycled.

    > [!NOTE]
    > For best results, verify that Modern POS is closed, and that no instances of DLLHost.exe exist in Task Manager.

### Perform Modern POS device activation

Try to activate the Modern POS device. If you still experience issues, open Event Viewer in Windows, and view the logs that correspond to Modern POS. Look for warnings and errors that might help you determine which steps you missed in the previous sections.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
