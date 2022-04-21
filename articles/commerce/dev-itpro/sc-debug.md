---
title: Debug Store Commerce extensions using Visual Studio Code
description: This topic describes how to debug Microsoft Dynamics 365 Commerce Store Commerce extensions by using Visual Studio Code.
author: mugunthanm
ms.date: 04/21/2022
ms.topic: article
audience: Developer
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: mumani
ms.search.validFrom: 03-30-2022
ms.dyn365.ops.version: AX 10.0.25
---

# Debug Store Commerce extensions using Visual Studio Code

[!include [banner](../includes/banner.md)]

This topic describes how to debug Microsoft Dynamics 365 Commerce Store Commerce extensions by using Visual Studio Code.

> [!NOTE]
> You can use Visual Studio Code to debug only 64-bit .NET Framework apps. To debug offline Commerce runtime (CRT)/Hardware station (HWS) code in Store Commerce, you must use Visual Studio 2019 or later.
>
> 1. Open the Store Commerce app.
> 1. In Visual Studio, open the CRT or HWS code.
> 1. On the menu, select **Debug \> Attach to Process**, and then select **Microsoft.Dynamics.Commerce.StoreCommerce.exe**.

To debug Store Commerce extensions by Using Visual Studio Code, follow these steps.

1. Install [Visual Studio Code](https://code.visualstudio.com/).
1. Open Visual Studio Code, and install [Microsoft Edge Tools for VS Code](https://marketplace.visualstudio.com/items?itemName=ms-edgedevtools.vscode-edge-devtools) from the Visual Studio Marketplace.
1. Before you deploy the extensions, install the [Store Commerce app](store-commerce.md#device-installation). During the installation process, enable the debug option by passing the **--enablewebviewdevtools** parameter as shown in the following example.

    ```PowerShell
    .\StoreCommerce.Installer.exe install --enablewebviewdevtools
    ```

1. Download the Store Commerce extension sample code from the [InStore GitHub repository (repo)](https://github.com/microsoft/Dynamics365Commerce.InStore), or use your own extension code.

    > [!NOTE]
    > Don't run Visual Studio Code in administrator mode.

1. Open the Visual Studio developer command prompt, and enter **code** to open Visual Studio Code.
1. In Visual Studio Code, select **File \> Open Folder**, and then open your extension code root folder.
1. In Visual Studio Code, select and hold (or right-click) the root folder of your solution directory, and create a new folder that is named **.vscode**.
1. Inside the **.vscode** folder, create a new file that is named **launch.json**.
1. In the **launch.json** file, add the following configurations to build and debug the Store Commerce extensions:

    - **Debug Store Commerce** – This configuration will open the Store Commerce app and attach the extension code to it for debugging.
    - **Build and Debug Store Commerce** - This configuration will build the extension code, deploy the extension, open the Store Commerce app, and attach the extension code to it for debugging.
    - **Attach debugger to Store Commerce** - This configuration will attach the extension code to the Store Commerce app for debugging, but it won't open the Store Commerce app.

1. Copy the following configuration code, paste it into the **launch.json** file, and then save the file.

    ```json
    {
        "version": "0.2.0",
        "configurations": [
            {
                "type": "pwa-msedge",
                "request": "launch",
                "port": 9222,
                "name": "Debug Store Commerce",
                "useWebView": true,
                "runtimeExecutable": "${env:ProgramFiles}/Microsoft Dynamics 365/10.0/Store Commerce/Microsoft/contentFiles/Microsoft.Dynamics.Commerce.StoreCommerce.exe",
                "userDataDir": "${env:LocalAppData}/Microsoft Dynamics 365/10.0/Data/Store Commerce/Pos",
                "url": "file:///${env:ProgramFiles}/Microsoft Dynamics 365/10.0/Store Commerce/Microsoft/contentFiles/Pos/Pos.html"
            },
            {
                "type": "pwa-msedge",
                "request": "launch",
                "port": 9222,
                "name": "Build and Debug Store Commerce",
                "useWebView": true,
                "runtimeExecutable": "${env:ProgramFiles}/Microsoft Dynamics 365/10.0/Store Commerce/Microsoft/contentFiles/Microsoft.Dynamics.Commerce.StoreCommerce.exe",
                "userDataDir": "${env:LocalAppData}/Microsoft Dynamics 365/10.0/Data/Store Commerce/Pos",
                "url": "file:///${env:ProgramFiles}/Microsoft Dynamics 365/10.0/Store Commerce/Microsoft/contentFiles/Pos/Pos.html",
                "preLaunchTask": "${defaultBuildTask}"
            },
            {
                "name": "Attach debugger to Store Commerce",
                "type": "pwa-msedge",
                "port": 9222,
                "request": "attach",
                "useWebView": true,
                "runtimeExecutable": "${env:ProgramFiles}/Microsoft Dynamics 365/10.0/Store Commerce/Microsoft/contentFiles/Microsoft.Dynamics.Commerce.StoreCommerce.exe"
            }
        ]
    }
    ```

1. Inside the **.vscode** folder, create a new file that is named **tasks.json**. You will use this file to create the configurations to build and install the Store Commerce app.
1. Copy the following configuration code, and paste it into the **tasks.json** file.

    ```json
    {
        "version": "2.0.0",
        "tasks": [
            {
                "label": "Build & Install Store Commerce Extension",
                "type": "shell",
                "command": "msbuild",
                "args": [
                    "/p:Configuration=debug",
                    "/p:InstallStoreCommerceExtensionsAfterBuild=true",
                    "/t:build",
                    "/m",
                    "/consoleloggerparameters:NoSummary",
                    "${workspaceFolder}"
                ],
                "group": {
                    "kind": "build",
                    "isDefault": true
                },
            }
        ]
    }
    ```

1. In Visual Studio Code, select **Debug**, select the appropriate option for your scenario, and then start to debug by putting a breakpoint in your extension code.

## Troubleshoot debug issues

### msbuild error

You might receive the following error message: "msbuild : The term 'msbuild' is not recognized as the name of a cmdlet, function, script file, or operable program." In this case, close Visual Studio Code. Then open the Visual Studio developer command prompt, go to the solution directory, and enter **code** to reopen Visual Studio Code and set the correct msbuild version.

### JSON file comment extension

If you receive any error messages that are related to .json file comments, close the .json file, and then try the **Debug** command again. Alternatively, delete all the comments in the .json file.
