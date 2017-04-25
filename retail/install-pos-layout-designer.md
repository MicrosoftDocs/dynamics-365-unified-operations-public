---
# required metadata

title: Install the Retail POS Layout designer
description: You can use the one-click designer to design different Retail Modern POS (MPOS) and Cloud POS layouts, in either Landscape mode or Portrait mode, for stores, registers, cashiers, and managers.
author: MargoC
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: RetailTillLayout
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 11
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 219684
ms.assetid: 2e2c4eea-c6e2-4912-9832-a6b22416e39f
ms.search.region: Global
ms.search.industry: Retail
ms.author: athinesh
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Install the Retail POS Layout designer

[!include[banner](includes/banner.md)]


You can use the one-click designer to design different Retail Modern POS (MPOS) and Cloud POS layouts, in either Landscape mode or Portrait mode, for stores, registers, cashiers, and managers.

The graphical design interface for MPOS or Cloud POS is controlled by the till layout. A layout controls the position of various objects. Examples include the total layout, the item grid layout, the customer layout, the payment layout, and the layout of various menu buttons. Layouts also include the overall appearance of the sales interface that is presented to workers.

## Install the one-click designer
1.  In Microsoft Dynamics 365 for Operations, use the menu in the upper left to navigate to **Retail** **and commerce** &gt; **Channel setup** &gt; **POS setup** &gt; **POS** &gt; **Screen layouts**.
2.  Select any layout that has an application type of **Modern POS for Windows** or **Cloud POS**, and then click **Layout designer**.
3.  On the notification bar that appears at the bottom of the Internet Explorer window, click **Open** to install the one-click designer. (The notification bar might appear in a different place in other browsers.)
4.  In the **Application Run - Security Warning** message box that appears, click **Run** to install the Retail designer host. A progress indicator shows the progress of the installation.
5.  After the installation is completed, on the **Sign in** page, enter your Microsoft Dynamics 365 for Operations user name and password, and then click **Sign in** to start the designer.
6.  After your credentials are validated and the designer starts, you can design your own layout or modify the existing layout. [![Layout in the one-click designer](./media/screenlayoutdesign_mposdownload-1024x664.png)](./media/screenlayoutdesign_mposdownload.png)

## Troubleshoot the installation of the Layout designer
-   When you click **Designer**, the prompt to download (or run) the installer doesn't appear, or your current security settings don't allow you to download the file. **Solutions:**
    -   In Internet Explorer, make sure that the pop-up blocker is disabled for this site. Click **Settings** &gt; **Options** &gt; **Privacy** &gt; **Find Pop-up Blocker**, and change the setting, if a change is required.
    -   In Internet Explorer, add the Dynamics 365 for Operations URL to your trusted sites. Click **Settings** &gt; **Options** &gt; **Security** &gt; **Trusted sites** &gt; **Sites** &gt; **Add**.
-   The program doesn't start, and you're instructed to contact the vendor. **Solution:** In Internet Explorer, add the Dynamics 365 for Operations URL to your trusted sites. Click **Setting** &gt; **Options** &gt; **Security** &gt; **Trusted sites** &gt; **Sites** &gt; **Add**.

**Known issue:** The designer doesn't work correctly in the Google Chrome and Mozilla Firefox browsers. We are working to fix this issue.

See also
--------

[Configure, download, install, and activate Retail Modern POS](retail-modern-pos-device-activation.md)



