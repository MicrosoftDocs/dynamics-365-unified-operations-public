---
title: Debug MPOS (sealed) and CPOS extensions
description: Learn how to debug sealed Modern Point of Sale (MPOS) and Cloud POS (CPOS) extensions.
author: josaw1
ms.date: 02/25/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2020-04-13
ms.custom: 
  - bap-template
---

# Debug MPOS (sealed) and CPOS extensions

[!include [banner](../../includes/banner.md)]

This article explains how to debug sealed Modern Point of Sale (MPOS) and Cloud POS (CPOS) extensions. It applies to version 10.0.18 and later of the Retail software development kit (SDK).

 > [!NOTE]
 > To debug the Store Commerce app, see [Debug Store Commerce extensions using Visual Studio Code](../sc-debug.md).

## Debug sealed Modern POS by using Visual Studio 2017

Follow these steps to debug your extension.

1. Install sealed Modern POS (MPOS) on the development machine by using the sealed MPOS installer. You can download the **Modern POS (SEALED)** installer from [https://lcs.dynamics.com/V2/SharedAssetLibrary](https://lcs.dynamics.com/V2/SharedAssetLibrary) in the Retail Self-service package section.
1. After you install the **Modern POS (SEALED)** installer, a desktop shortcut icon is created to **Install or Update POS Universal Windows Platform (UWP) app**. Double-click the **Install or update Retail Modern POS** icon on the desktop to install the UWP app. This previous step deploys the required backend components and installs the UWP app.
1. In Microsoft Visual Studio, build your MPOS extension package project (the JavaScript project file [.jsproj file]).
1. Deploy your MPOS extension package. In Solution Explorer, select and hold (or right-click) the MPOS .jsproj file, and then select **Deploy**.
1. Open POS so that the debugger is attached:

    1. On the **Debug** menu, select **Other Debug Targets &gt; Debug Installed App Package**.
    1. Search for and select **Commerce Modern POS**.
    1. Select **Start** to open the app.

## Run and debug Cloud POS

### <a name="configure-cloud-pos"></a>Configure the Cloud POS extension development environment

Follow these steps the first time you develop an extension package on the machine or if you delete the link. In the Cloud POS (CPOS) **Extensions** directory, create a directory symbolic link to the root directory of the extension package.

1. Make sure that CPOS is deployed on the machine. If it isn't deployed, use the Commerce Scale Unit (self-hosted) installer to deploy it.
1. Open Internet Information Services (IIS). Select **Windows logo key+R** to open the **Run** dialog box, enter **inetmgr**, and then select **OK**.
1. Expand **Sites**, select and hold (or right-click) **RetailCloudPos**, and then select **Explore**.
1. Select **File**, and then select **Open Windows PowerShell as administrator**.
1. In the **Windows PowerShell** window, run the following command to open a Windows command prompt.

    ```powershell
    cmd .
    ```

1. Run the following command to change the current directory to the **Extensions** root directory.

   ```powershell
   cd Extensions
   ```

1. Run the following command to create a session variable that has the name of your extension package.

    ```powershell
    set ExtensionPackageName=Contoso.Pos.Developer.Samples
    ```

    > [!NOTE]
    > Replace **Contoso.Pos.Developer.Samples** with the name of your POS extension package. The name of the extension package must match the name that you specify in **ExtensionPackageDefinition** in the Commerce runtime (CRT) trigger extension that configures the POS extension package.

1. Run the following command to create a session variable that has the absolute path of the directory for your POS extension package project.

    ```powershell
    set AbsolutePathToExtensionPackageProject=%FullPathToPOSExtensionProjectRootDirectory%
    ```

    > [!NOTE]
    > Replace **%FullPathToPOSExtensionProjectRootDirectory%** with the absolute path of your POS extension package project. Here's an example.
    >
    > ```powershell
    > set AbsolutePathToExtensionPackageProject=K:\RetailCloudPos\WebRoot\Extensions\ Contoso.Pos.Developer.Samples
    > ```

1. Run the following command to create a link from the **Extensions** directory to the root directory of the extension package project.

    ```powershell
    mklink /D %ExtensionPackageName% %AbsolutePathToExtensionPackageProject%
    ```

1. Verify that the linked folder for your extension package is created in the directory for the CPOS extension package.

## Debug CPOS by using the Microsoft Edge developer tools

1. Follow the steps in the [Configure the Cloud POS extension development environment](#configure-cloud-pos) section earlier in this article.
1. Build your CPOS extension project.
1. In Microsoft Edge, open the CPOS website.
1. Select the **F12** key to open the Microsoft Edge developer tools.
1. Set up a workspace that points to the root directory of your CPOS extension package. You only need to set up the workspace the first time you complete this procedure.
1. Make sure that **JavaScript Source Mapping** is enabled.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
