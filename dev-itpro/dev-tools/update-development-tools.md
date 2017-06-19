---
# required metadata

title: Update Visual Studio development tools
description: This topic explains how to update the development tools.
author: RobinARH
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 61
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 33571
ms.assetid: bd24d864-6915-4d17-9ebb-d1619b7d4311
ms.search.region: Global
# ms.search.industry: 
ms.author: robadawy
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Update Visual Studio development tools

[!include[banner](../includes/banner.md)]


This topic explains how to update the development tools.

Use this tutorial to update your Visual Studio development tools with a new version. It explains how to uninstall your existing Visual Studio development tools and install the new extension. The new extension is in the form of an installable VSIX file. This file is a part of the binary hotfix available on the Dynamics Lifecycle Services (LCS) site. The VSIX file is located in the **DevToolsService\\Scripts** folder of the binary hotfix package. Whenever you update a developer machine with an AOS binary hotfix, it is also recommended to install the development tools that are packaged within the same binary hotfix.

## Uninstall the existing Visual Studio extension
In order to install a new version of the development tools, you'll need to uninstall the existing version first. Verify the version of the development tools that you have installed. If you don't have it installed, you can skip this section.

### Verify your current version of the Visual Studio extension

1.  Open the Visual Studio **Help &gt; About Microsoft Visual Studio** dialog and find **Finance and Operations Developer Tools**.
2.  Select it and click **OK**.

### Uninstall the extension

1.  Open the Visual Studio **Tools &gt; Extensions and Updates** dialog.
2.  Select **Finance and Operations Visual Studio Tools** and click **Uninstall**.
3.  When the extension is uninstalled, exit Visual Studio.

## Install a new version of the extension
1.  Make sure Visual Studio is not running.
2.  Double-click (or right-click and **Open**) the VSIX file of the new version.
3.  Follow the installation instructions.
4.  When installation is complete, you can start Visual Studio and start developing your application.




