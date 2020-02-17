---
# required metadata

title: Device activation of a customized Modern POS
description: This topic explains how to configure Microsoft Dynamics 365 Commerce Headquarters so that device activation works correctly when a customized Modern POS application is used. 
author: jashanno
manager: AnnBe
ms.date: 08/24/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations, Retail 
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global 
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: jashanno
ms.search.validFrom: 2017-09-31
ms.dyn365.ops.version: Application update 3
---

# Device activation of a customized Modern POS

[!INCLUDE [banner](../includes/banner.md)]

This topic explains how to configure Microsoft Dynamics 365 Commerce Headquarters so that device activation works correctly when a customized Modern POS application is used. It describes the steps that are required in order to obtain the customized reply address and enter that value in Headquarters.

Modern POS is a client-side component for Microsoft Dynamics 365 Commerce. To use the POS, you must perform device activation. Device activation uses Microsoft Azure Active Directory (Azure AD) to authenticate users. Enhanced functionality in this area has modified the device activation flow to take better advantage of the Web Account Manager service. As part of this enhancement, there is now enhanced security for the authentication approval process. This enhanced security requires additional configuration in Headquarters when the POS is customized, because a specific, unique value is now required for the callback URI. (The callback URI is also known as the reply URI.)

By default, Modern POS is already registered for this callback URI. However, when customized, the callback URI is changed. Therefore, it must be correctly configured so that it works again. This topic describes the steps that you must follow to complete this configuration. If this configuration isn't completed, you receive an error message when you try to perform device activation in the customized POS application. This error message resembles the following example:

> AADSTS50011: The reply address 'ms-appx-web://Microsoft.AAD.BrokerPlugin/[...]' does not match the reply addresses configured for the application

> [!NOTE]
> - We recommend that you try to use the customized Modern POS application one time before you configure Dynamics 365 headquarters. In this way, you can see what the error message looks like and more easily obtain the customized reply address.
> - The error specifies the reply address that is used for the application ID that corresponds to the POS application.

## Setup
The following steps are required so that device activation works correctly when the customized Modern POS application is used. You will create two Azure AD applications: one for Modern POS and one for Commerce Scale Unit. The Commerce Scale Unit Azure AD application is required because the POS uses resources through Commerce Scale Unit. Therefore, both Azure AD applications are used when the POS is used. In this scenario, Commerce Scale Unit serves as the endpoint for protected resources that the POS requests.

### Create the Commerce Scale Unit Azure AD application
1. In a web browser, go to <https://portal.azure.com/>.
2. Sign in by using Azure AD credentials that have enough permission to create Azure AD applications.
3. Select **Azure Active Directory** \> **App registrations**.
4. Create the Commerce Scale Unit Azure AD application by selecting **New application registration** and entering the following values:

    - **Name:** Enter **Customized Commerce Scale Unit**. (You can enter any other unique value, but be sure to make a note of it.)
    - **Application type:** Select **Web app / API**.
    - **Sign-on URL:** Enter any unique URL that doesn't point to a real, physical location. For example, enter `https://MyNotRealURL`.

5. Press the Tab key so that Azure can validate the value in the **Sign-on URL** field. Then select **Create**, and wait until the operation is successfully completed. (If an error occurs, address it, and then try again.)

    A tile appears that shows the details of the new Azure AD application.

6. Select **Settings** at the top of the tile to open the **Settings** tile for the application. Then select **Properties**.
7. On the **Properties** tile, copy the value in the **App ID URI** field. You will paste this value into the DLLHost.exe.config file for POS in the next section.

> [!NOTE]
> Don't close the web browser window, because you will use it again later in this topic.

### Update the Modern POS configuration
1. In File Explorer, go to **C:\\Program Files (x86)\\Microsoft Dynamics 365\\70\\Retail Modern POS\\ClientBroker**. (This path assumes that the Microsoft Windows operating system on the computer is based on the x64 architecture.)
2. In File Explorer, select **File** \> **Open Windows PowerShell** \> **Open Windows PowerShell as administrator**.
3. In the Microsoft Windows PowerShell window that appears, enter **notepad DLLHost.exe.config**, and then press the Enter key. (The Windows PowerShell window will already be pointed to the current file directory.)
4. In the Notepad window that appears, find the value that corresponds to the **AADRetailServerResourceId** key. (By default, this value is `https://commerce.dynamics.com`.) Then paste the App ID URI value that you copied in step 7 in the previous section.
5. Select **File** \> **Save**.

> [!NOTE]
> Don't close the Notepad window, because you will use it again in the next section.

### Create the customized Modern POS Azure AD application
1. Return to the web browser window where <https://portal.azure.com/> is open, and create the Retail Modern POS Azure AD application by repeating steps 3 through 4 in the "Create the Commerce Scale Unit Azure AD application" section. However, enter the following values this time:

    - **Name:** Enter **Customized Retail Modern POS**. (You can enter any other unique value, but be sure to make a note of it.)
    - **Application type:** Select **Native**.
    - **Redirect URI:** If you tried to use the customized Modern POS application without configuring Dynamics 365 headquarters, as we recommended at the beginning of this topic, you received an error message. Enter the reply address (redirect URI) that corresponds to that error message. The value will start with **ms-appx-web://Microsoft.AAD.BrokerPlugin/[...]**.

        > [!NOTE]
        > - You can also see the reply address (redirect URI) in Event Viewer in Windows, under **Microsoft-Dynamics-Commerce-ModernPos/Operational**. The event ID is 40619. The error message will start with the following text: "This UWP application was assigned the following callback URI to be used while interacting with Azure AD: ms-appx-web://Microsoft.AAD.BrokerPlugIn/S-1-15-2-[...]"
        > - After the Azure AD application is created, you can specify additional redirect URIs as you require. If multiple packages that have different callback URIs have been generated for any reason, keep this single Azure AD application, and maintain all redirect URIs in it.

2. Press the Tab key so that Azure can validate the value in the **Redirect URI** field. Then select **Create**, and wait until the operation is successfully completed. (If an error occurs, address it, and then try again.)

    A tile appears that shows the details of the new customized Retail Modern POS Azure AD application.

3. Find the **Application ID** field, and copy the value. (You will paste this value into the DLLHost.exe.config file as the value that corresponds to the **AADClientId** key.)
4. Select **Settings** at the top of the tile to open the **Settings** tile for the application. Then select **Required permissions**.
5. On the **Required permissions** tile, select **+ Add**.
6. On the **Add API access** tile, select **1 Select an API**.
7. On the **Select an API** tile, in the search field, enter the name of the Commerce Scale Unit Azure AD application that you created in the "Create the Commerce Scale Unit Azure AD application" section. (In this topic, the application is named **Customized Commerce Server**.) Select the item that corresponds to that application, and then select **Select**.

    On the **Add API access** tile, **2 Select permission** is automatically selected, and a new tile appears that is named **Enable Access**.

8. On the **Enable Access** tile, hold the mouse pointer over the line for **Access Customized Commerce Scale Unit**, and then select the check box that appears on the left side. (If you entered a different name for the Commerce Scale Unit Azure AD application, that name is used on the line instead of **Customized Commerce Scale Unit**.) The **Select** button at the bottom of the tile becomes available.
9. Select **Select** to return to the **Add API access** tile.
10. Select **Done** to return to the **Required permissions** tile.
11. Select **Grant Permissions**. When a message prompts you to verify that you want to grant the permissions, select **Yes**.
12. Switch to the Notepad window that shows the contents of the DLLHost.exe.config file. (You left this window after you completed the steps in the previous section.)
13. Find the value that corresponds to the **AADClientId** key. (By default, this value is a globally unique identifier [GUID] that corresponds to the headquarters environment.) Paste the value that you copied in step 3.
14. Select **File** \> **Save**.

### Configure Dynamics 365 Headquarters
The previous steps were required so that the Modern POS application can be authenticated. You must now follow these steps to add the new Azure AD applications to the list of safe programs in Headquarters, so that the requests are authorized. (A list of safe programs is sometimes also referred to as a whitelist.)

1. In a web browser, go to the Headquarters URL, and sign in by using Azure AD credentials.
2. Go to **Retail and Commerce** &gt; **Headquarters setup** &gt; **Parameters** &gt; **Commerce shared parameters**.
3. On the **Identity Providers** tab, in the **Identity providers** section, select the provider that begins with `HTTPS://sts.windows.net/`. The values in the **Relying parties** section are updated, based on the provider that you selected.
5. In the **Relying parties** section, select **+ Add**, and enter the following values:

    - **ClientId:** Enter the value that you copied in step 3 in the previous section and then pasted into the DLLHost.exe.config file in step 13.
    - **Type:** Select **Public**.
    - **UserType:** Select **Worker**.
    - **Name:** Enter a description to help users understand what this entry references.

6. On the Action Pane, select **Save**. The relying party that you just created should remain selected.
7. In the **Server resource IDs** section, select **+ Add**, and enter the following values:

    - **Server Resource Id:** Enter the URL that you copied in step 4 in the "Update the Modern POS configuration" section. (You originally created this value in step 4 in the "Create the Commerce Scale Unit Azure AD application" section.)
    - **Name:** Enter a description to help users understand what this entry references.

8. On the Action Pane, select **Save**.
9. Go to **Retail and Commerce** &gt; **Retail and CommerceIT** \> **Distribution schedule**.
10. Select job **1110** (**Global configuration**), and then, on the Action Pane, select **Run now**. This job synchronizes the new data. However, there is a cache in Commerce Scale Unit that won't be updated for several minutes. Therefore, if you require an immediate update, the Commerce Scale Unit application pool must be recycled.

    > [!NOTE]
    > For best results, verify that Modern POS is closed, and that no instances of DLLHost.exe exist in Task Manager.

### Perform Modern POS device activation
Try to activate the Modern POS device. If you still experience issues, open Event Viewer in Windows, and view the logs that correspond to Modern POS. Look for warnings and errors that might help you determine which steps you missed in the previous sections.
