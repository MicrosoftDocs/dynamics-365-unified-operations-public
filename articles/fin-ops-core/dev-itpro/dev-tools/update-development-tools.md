---
title: Update the Visual Studio development tools
description: Learn about how to update Visual Studio development tools to new versions, including how to uninstall your existing Visual Studio development tools.
author: josaw1
ms.author: josaw
ms.topic: how-to
ms.date: 03/30/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: bd24d864-6915-4d17-9ebb-d1619b7d4311
---

# Update the Visual Studio development tools

[!include [banner](../includes/banner.md)]

This article explains how to update the development tools.

Use this tutorial to update your Visual Studio development tools to a new version. It explains how to uninstall your existing Visual Studio development tools and install the new extension. The new extension comes as an installable VSIX file. This file is part of the binary hotfix available on the Dynamics 365 Lifecycle Services site. The VSIX file is located in the **DevToolsService\\Scripts** folder of the binary hotfix package.

While working in Visual Studio, you might receive recurring feedback requests about new features.

To prevent the feedback requests from appearing in Visual Studio, run the following PowerShell command from a developer’s machine:

```powershell
Set-ItemProperty HKCU:\Software\Microsoft\Dynamics\AX7\Development\Configurations  -Name ProvideFeedback  -Value "No"
```

> [!NOTE]
> You don't need to follow the instructions in this article if you're upgrading your finance and operations platform to Platform update 4 or newer. It's an automatic step that's part of the platform upgrade process.

## Prerequisites

To use the finance and operations apps development tools, install the **Visual Studio extension development** workload in your Visual Studio, and include the **Modeling SDK** option.

If you don't have the workload installed, follow these steps to add it.

1. Open your Visual Studio Installer app and select **Modify** on your Visual Studio installed app.

   :::image type="content" source="media/vs-installer-modify.png" alt-text="Screenshot that shows the location of the Modify button in the Visual Studio Installer app.":::

   A new window opens and you see the **Workloads** tab.
1. From the **Other Toolsets** section, check **Visual Studio extension development**.
1. Under **Installation details**, check **Modeling SDK** under **Visual Studio extension development** > **Optional**.

   :::image type="content" source="media/vs-ext-dev-workload.png" alt-text="Screenshot that shows the location of the Visual Studio extension development toolset and the Modeling SDK checkbox.":::

1. Select **Modify** to add the workload.

## Uninstall the existing Visual Studio extension

To install a new version of the development tools, you need to uninstall the existing version first. Verify the version of the development tools that you have installed. If you don't have it installed, you can skip this section.

### Verify your current version of the Visual Studio extension

1. Open the Visual Studio **Help &gt; About Microsoft Visual Studio** dialog and find **finance and operations Developer Tools**.
1. Select it and click **OK**.

### Uninstall the extension

1. Open the Visual Studio **Tools &gt; Extensions and Updates** dialog.
1. Select **finance and operations Visual Studio Tools** and click **Uninstall**.
1. When the extension is uninstalled, exit Visual Studio.

## Install a new version of the extension

1. Make sure Visual Studio isn't running.
1. Double-click (or right-click and **Open**) the VSIX file of the new version.
1. Follow the installation instructions.
1. When installation is complete, start Visual Studio and start developing your application.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
