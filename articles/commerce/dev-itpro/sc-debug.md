---
title: Debug Store Commerce extensions using VS Code
description: This document explains how to debug the Store Commerce extensions using VSCode.
author: mugunthanm
ms.date: 03/30/2022
ms.topic: article
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: mumani
ms.search.validFrom: 03-30-2022
ms.dyn365.ops.version: AX 10.0.25
---

# Debug Store Commerce extensions using VS Code

[!include [banner](../includes/banner.md)]

This document explains how to debug the Store Commerce app extension code using VSCode. Follow the steps documented below to debug Store Commerce Extensions:

> [!NOTE]
> To debug offline Commerce runtime (CRT)/Hardware station (HWS) code in Store Commerce you need to use Visual Studio 2019 or later, VS Code only supports debugging 64-bit .NET Framework apps. Launch the Store Commence app and then open the CRT or HWS code in Visual studio and then from the  menu choose Debug > Attach to Process and select Microsoft.Dynamics.Commerce.StoreCommerce.exe. 

1.	Install [Visual Studio Code](https://code.visualstudio.com/)
2.	Launch the Visual Studio Code and install the [Microsoft Edge Tools for VS Code - Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-edgedevtools.vscode-edge-devtools)

 ![Commerce components.](../media/EdgeTool.png)

3.	Before deploying the extensions, [Install the Store Commerce app](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/store-commerce#device-installation), during install please enable the debug option by passing the parameter **--enablewebviewdevtools.**
```ps
Ex:  .\StoreCommerce.Installer.exe install --enablewebviewdevtools
```
4.	Download the Store Commerce extension sample code from the InStore GitHub Repo or use your own extension code.

> [!NOTE]
> Don’t run VS code in admin mode.

5.	Open VS developer command prompt and type **code .** to open VS code.
6.	Inside the VSCode, Click File > Open Folder and open your Extension Code root folder.
7.	In the VSCode, right click the root folder of your solution directory and create a new folder called **.vscode**. 
8.	Inside the .vscode folder, create a new file and name it as launch.json.

![Commerce components.](../media/Launch.png)

9.	Inside the launch.json file add the configurations to build and debug the Store Commerce extensions. 

**Debug Store Commerce** – This configuration will launch the Store Commerce app and attach the extension code to Store Commerce app for debugging.

**Build and Debug Store Commerce** - This configuration will build the extension code, deploy the extension, launch the Store Commerce app and attach the extension code to the Store Commerce app for debugging.
**Attach debugger to Store Commerce** - This configuration will attach the extension code to the Store Commerce app for debugging, this will not start the Store Commerce app.

Copy the below configurations code to the launch.json file and save it.
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

10.	Inside the .vscode folder, create a new file and name it as tasks.json to create the configurations to build and install the Store Commerce app.

Inside the tasks.json file, copy the below configurations:
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
11.	Click the Debug button in VS and choose the right option based on your scenario and start debugging by placing breakpoint in your extension code.

 ![Commerce components.](../media/Debug.png)

### Troubleshooting debug issues
**msbuild error**

If you get the this error: msbuild : The term 'msbuild' is not recognized as the name of a cmdlet, function, script file, or operable program
Close VS Code and Open Visual Studio Developer Command prompt and navigate to the solution directory and then type **Code .**.  This will open VS Code and set the right msbuild version.

**Json Comment extension**

If you get any error related to json file comment, then close the opened json file and try the debug command again or delete all the comments in the json.



