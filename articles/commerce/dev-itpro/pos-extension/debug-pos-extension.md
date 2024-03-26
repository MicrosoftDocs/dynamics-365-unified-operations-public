---
title: Debug MPOS (sealed) and CPOS extensions
description: This article explains how to debug Modern Point of Sale (Sealed) and Cloud POS extensions.
author: josaw1
ms.date: 05/05/2022
ms.topic: article
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2020-04-13
ms.dyn365.ops.version: AX 10.0.18
---

# Debug MPOS (sealed) and CPOS extensions

[!include [banner](../../includes/banner.md)]

This article explains how to debug **sealed** Modern Point of Sale (MPOS) and Cloud POS extensions. It applies to version 10.0.18 and later of the Retail software development kit (SDK). 

 > [!NOTE]
 > To debug the Store Commerce app, see [Debug Store Commerce extensions using Visual Studio Code](../sc-debug.md)

## Debug Sealed Modern POS by using Visual Studio 2017

Follow these steps to debug your extension.

1. Install Sealed Modern POS (MPOS) on the development machine by using the Sealed MPOS installer. The **Modern POS (SEALED)** installer can be downloaded from  https://lcs.dynamics.com/V2/SharedAssetLibrary > Retail Self-service package section.
2. After installing the **Modern POS (SEALED)** installer, a desktop shortcut icon will be created to Install or Update POS Universal Windows Platform (UWP) app. Double click the **Install or update Retail Modern POS** icon on the desktop to install the UWP app. This previous deploys the required backend components and installs the UWP app.
3. In Microsoft Visual Studio, build your MPOS extension package project (the JavaScript project file \[.jsproj file\]).
4. Deploy your MPOS extension package. In Solution Explorer, select and hold (or right-click) the MPOS .jsproj file, and then select **Deploy**.
5. Open POS so that the debugger is attached:

    1. On the **Debug** menu, select **Other Debug Targets &gt; Debug Installed App Package**.
    2. Search for and select **Commerce Modern POS**.
    3. Select **Start** to open the app.

## Run and debug Cloud POS

### <a name="configure-cloud-pos"></a>Configure the Cloud POS extension development environment

Follow these steps the first time that an extension package is developed on the machine or if the link is deleted. In the Cloud POS (CPOS) **Extensions** directory, create a directory symbolic link to the root directory of the extension package.

1. Make sure that CPOS is deployed on the machine. If it isn't deployed, use the Commerce Scale Unit (self-hosted) installer to deploy it.
2. Open Internet Information Services (IIS). Select **Windows logo key+R** to open the **Run** dialog box, enter **inetmgr**, and then select **OK**.
3. Expand **Sites**, select and hold (or right-click) **RetailCloudPos**, and then select **Explore**.
4. Select **File**, and then select **Open Windows PowerShell as administrator**.
5. In the **Windows PowerShell** window, run the following command to open a Windows command prompt.

    ```powershell
    cmd .
    ```

6. Run the following command to change the current directory to the **Extensions** root directory.

   ```powershell
   cd Extensions
   ```

7. Run the following command to create a session variable that has the name of your extension package.

    ```powershell
    set ExtensionPackageName=Contoso.Pos.Developer.Samples
    ```

    > [!NOTE]
    > Replace **Contoso.Pos.Developer.Samples** with the name of your POS extension package. The name of the extension package must match the name that is specified in **ExtensionPackageDefinition** in the Commerce runtime (CRT) trigger extension that configures the POS extension package.

8. Run the following command to create a session variable that has the absolute path of the directory for your POS extension package project.

    ```powershell
    set AbsolutePathToExtensionPackageProject=%FullPathToPOSExtensionProjectRootDirectory%
    ```

    > [!NOTE]
    > Replace **%FullPathToPOSExtensionProjectRootDirectory%** with the absolute path of your POS extension package project. Here is an example.
    >
    > ```powershell
    > set AbsolutePathToExtensionPackageProject=K:\RetailCloudPos\WebRoot\Extensions\ Contoso.Pos.Developer.Samples
    > ```

9. Run the following command to create a link from the **Extensions** directory to the root directory of the extension package project.

    ```powershell
    mklink /D %ExtensionPackageName% %AbsolutePathToExtensionPackageProject%
    ```

10. Verify that the linked folder for your extension package is created in the directory for the CPOS extension package.

## Debug CPOS by using the Microsoft Edge developer tools

1. Follow the steps in the [Configure the Cloud POS extension development environment](#configure-cloud-pos) section earlier in this article.
2. Build your CPOS extension project.
3. In Microsoft Edge, open the CPOS website.
4. Select the **F12** key to open the Microsoft Edge developer tools.
5. Set up a workspace that points to the root directory of your CPOS extension package. You have to set up the workspace only the first time that you complete this procedure.
6. Make sure that **JavaScript Source Mapping** is enabled.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
