---
# required metadata

title: Device activation of a customized Retail Modern POS
description: This topic explains how to configure headquarters to allow device activation to function properly when a customized Retail Modern POS application is used. 
author: jashanno
manager: AnnBe
ms.date: 04/25/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations, Retail 
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global 
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: jashanno
ms.search.validFrom: 2017-09-31
ms.dyn365.ops.version: Application update 3
---

# Device activation of a customized Retail Modern POS

[!INCLUDE [banner](../includes/banner.md)]

This topic explains how to configure headquarters to allow device activation to function properly when a customized Retail Modern POS application is used. It details the steps necessary to pull the customized reply address and enter this value into headquarters.

> [!NOTE]
> This security and functionality enhancement was introduced in the July 2017 (7.2) release and has since been ported to the previous 1611 (7.1) release.

The Retail Modern POS application is a client-side component for Microsoft Dynamics 365 for Finance and Operations and Microsoft Dynamics 365 for Retail.  To utilize Retail Modern POS, it is mandatory to perform device activation.  Device activation leverages Azure Active Directory (AAD) to authenticate users.  Enhanced functionality in this area has modified the device activation flow to better leverage the Windows Web Account Manager.  As a function of this enhancement, there is now enhanced security around the authentication approval process that requires additional configuration in headquarters when Retail Modern POS has been customized.  Specifically, the Callback (also known as the Reply) URI now requires a very specific and unique value.  By default, the Retail Modern POS application is already registered for this Callback URI.  When customized, this URI is altered and must be configured correctly to function again.  This topic provides the steps required to perform this configuration.  When this configuration is not followed, an error message occurs when device activation is attempted in the customized Retail Modern POS application.  The error will be similar to the following:

```
AADSTS50011: The reply address 'ms-appx-web://Microsoft.AAD.BrokerPlugin/[...]' does not match the reply addresses configured for the application
```

> [!NOTE]
> - It is recommended to attempt to use the customized Retail Modern POS application without configuring headquarters once to see what the error looks like and to more easily pull the custom reply address.
> - Take note that the error showcases the reply address used for the Application ID, which corresponds to the Retail Modern POS application.

## Setup
The steps that follow are required to allow device activation to function correctly when the customized Retail Modern POS application is used.  There will be two Azure Active Directory (AAD) applications generated, one for Retail Modern POS and one for Retail Server.  The Retail Server AAD application is required because Retail Modern POS utilizes resources through Retail Server, so both AAD applications are utilized through Retail Modern POS usage.  Retail Server, in this scenario, functions as the endpoint for protected resources that get requested by the Retail Modern POS application.

### Create the Retail Server AAD application
1. Open a web browser and navigate to https://portal.azure.com/.
2. Sign in using AAD credentials that have enough permission to create AAD applications.
3. Go to **Azure Active Directory** > **App registrations**.
4. Create the AAD Retail Server application by repeating steps 3-4, provide the following values:
  - **Name** should specify "Customized Retail Server". (Any unique value desired can be put here, but keep note of it.)
  - **Application type** should specify "Web app / API" from the drop-down.
  - **Sign-on URL** can be any unique URL that does not point to a real, physical location. As an example, enter `https://MyNotRealURL`.
5. Press the **Tab** button on the keyboard to allow Azure to verify the field, then select the **Create** button and wait until the operation completes successfully. (If and error occurs, address the error and try again.)
6. The page will now show the details of the newly created Retail Server AAD application created.
7. Select the application's **Settings** page on the action bar at the top of the tile, then go to **Properties** and copy the value shown in the field titled **App ID URI**.  This value needs to be copied into the DLLHost.exe.config file for Retail Modern POS (Which is explained in the next set of steps).

    > [!NOTE]
    > Do not close this web browser as it will be used again later in this topic.

### Update the Retail Modern POS configuration
8. Open **File Explorer** and navigate to **C:\Program Files (x86)\Microsoft Dynamics 365\70\Retail Modern POS\ClientBroker** (assuming the computer Windows operating system is based on the x64 architecture). 
9. In the **File Explorer** window, select **File** > **Open Windows PowerShell** > **Open Windows PowerShell as administrator**.
10. In the **Windows PowerShell** window that opens (the window will already be pointed to the current file directory) enter the text **notepad DLLHost.exe.config** and press the **Enter** key on the keyboard.
11. In the **Notepad** that opens, find the value corresponding to the key **AADRetailServerResourceId** (by default, this value will state `https://commerce.dynamics.com`), and then enter the value that was copied in step seven of the previous procedure.
12. Select **File** > **Save**.

    > [!NOTE]
    > Do not close this Notepad as it will be used again in the next sub-heading.

### Create the customized Retail Modern POS AAD application
13. Return to the web browser with the https://portal.azure.com/ page open and create the AAD MPOS application by repeating steps 3-5 above except provide the following values this time:
  - **Name** should specify "Customized Retail Modern POS". (Any unique value desired can be put here, but keep note of it.)
  - **Application type** should specify "Native" from the drop-down.
  - **Redirect URI** should specify the reply address corresponding to the error seen in Retail Modern POS (or the **Event Viewer**) as described in the previous procedure.  The reply address value will start with **ms-appx-web://Microsoft.AAD.BrokerPlugin/[...]**

    > [!NOTE]
    > - The reply address (redirect URI) can be seen in the **Event Viewer** under **Microsoft-Dynamics-Commerce-ModernPos/Operational**.  The event ID is 40619.
    > - The error text will begin with *This UWP application was assigned the following callback Uri to be used while interacting with AAD: ms-appx-web://Microsoft.AAD.BrokerPlugIn/S-1-15-2-[...]*.
    > - It is important to note that once the AAD application is created, additional **Redirect URIs** can be specified as needed. If, for any reason, multiple packages with different callback URLs have been generated, keep this single AAD application and maintain all redirect URIs in this single AAD application.

14. Press the **Tab** button on the keyboard to allow Azure to verify the field, then select the **Create** button and wait until the operation completes successfully. (If an error occurs, address the error and try again.)
15. The page will now show the details of the newly created customized Retail Modern POS AAD application created.
16. Find the field **Application ID** and copy it. (This value will be pasted into the attribute value corresponding to the key **AADClientId** in the file DLLHost.exe.config.)
17. Select the application's **Settings** page on the action bar at the top of the tile, then go to **Required permissions**.
18. In the new tile, select **+Add**.
19. In the new tile, select **1 Select an API**.
20. In the new tile, type the name of the Retail Server AAD application generated at the beginning of this topic (titled in this topic as "Customized Retail Server"), select the listing that appears that corresponds to the application previous created, then select the **Select** button at the bottom of the tile.
21. The previous tile will now automatically select the **2 Select permission** value and a new tile will appear titled **Enable Access**.
22. In the new tile, mouse over the line showing **Access Customized Retail Server** (again, this will list the name entered previously) and select the checkbox on the left side. (This will highlight the line, check the box, and light up the **Select** button at the bottom of the tile.)
23. Click the **Select** button at the bottom of the tile to return to the previous tile (the tile titled **Add API access**).
24. Click the **Done** button at the bottom of the tile to return to the previous tile (the tile titled **Add API access**).
25. Now back to the tile titled **Required permissions**, select the **Grant Permissions** action, then select **Yes** on the pop-up that appears to verify that permissions will be granted.
18. Switch to the **Notepad** that should be still open (showing the DLLHost.exe.config file contents), find the value corresponding to the key **AADClientId** (by default, this value will a GUID value corresponding to the headquarters environment) and enter the value that was copied in step 16 above.
19. Select **File** > **Save**.

### Configure Dynamics 365 headquarters
The previous steps are required to allow for authentication of the Retail Modern POS application.  The final steps that are shown here are necessary to properly whitelist the new created AAD applications in Dynamics 365 headquarters to authorize the requets.

20. Open a web browser and navigate to the Dynamics 365 headquarters URL and sign in using AAD credentials.
21. Got to **Retail** &gt; **Headquarters setup** &gt; **Parameters** &gt; **Retail shared parameters**.
22. Select the **Identity providers** FastTab.
23. On the **Identity providers** FastTab, select the provider that begins with `HTTPS://sts.windows.net/` (The values on the **Relying parties** sub-heading are listed, based on this selection.)
24. On the **Relying parties** sub-heading, select **+Add** button and enter the following details:
  - **ClientId** should specify the value used in step 18 above (also now shown in the **DLLHost.exe.config** notepad).
  - **Type** should specify the value **Public** from the drop-down menu.
  - **UserType** should specify the value **Worker** from the drop-down menu.
  - **Name** is a description field to help understand what this entry is referencing.
25. On the Action Pane, select **Save**. (The newly created **Relying parties** should maintain selection.)
26. At the bottom of this page, under the **Server resource IDs** sub-heading, select **+Add** and enter the following details:
  - **Server Resource Id** should specify the URL copied in step 11 above. (Originally created in step four above.)
  - **Name** is a description field to help understand what this entry is referencing.
27. On the Action Pane, select **Save**.
28. Navigate to **Retail** &gt; **Retail IT** > **Distribution schedule**.
29. Select the job **1110** from the left-hand list and then select **Run now** from the Action pane. This will synchronize the new data, however there is a cache in Retail Server that will not update for several minutes, so if immediate update is required then the Retail Server application pool will require recycling.

    > [!NOTE]
    > Verify that Retail Modern POS is closed and no instances of DLLHost.exe exist in **Task Manager** for best results.

### Perform Retail Modern POS device activation
Attempt to activate the Retail Modern POS device. If issues are still experienced, open the Windows **Event Viewer** and see the logs corresponding to Retail Modern POS for warnings and errors which would assist in the investigation of the steps above that were missed.
