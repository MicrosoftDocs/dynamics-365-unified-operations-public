---
# required metadata

title: Create a deployable package
description: This topic describes the workflow for creating and applying a deployable package.
author: RobinARH
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 61
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 24211
ms.assetid: 6d44cedb-9e2b-447b-abe5-8967ce6fd280
ms.search.region: Global
# ms.search.industry: 
ms.author: shailesn
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Create and apply a deployable package

This topic describes the workflow for creating and applying a deployable package.

Overview of the packaging and deployment process
------------------------------------------------

The following diagram shows the workflow for creating and applying a deployable package. [](./media/generate-deployable-package.png)[![generate-deployable-package](./media/generate-deployable-package.png)](./media/generate-deployable-package.png) **Note:** The manual steps that are described in this article will be automated as part of the servicing features that are being developed.

## Create a deployable package
After you have completed the development of the modules, follow these steps to create and upload a deployable package.

1.  In Microsoft Visual Studio, select **Dynamics 365** &gt; **Deploy** &gt; **Create Deployable Package**.
2.  Select the package that contains your model, and then select a location in which to create the deployable package. [![Selecting a package](./media/pack3.png)](./media/pack3.png) [![Selecting a location](./media/pack4.png)](./media/pack4.png)
3.  After a deployable package is created, sign in to Microsoft Dynamics Lifecycle Services (LCS), and then, in your LCS project, click the **Asset Library** tile.
4.  Upload the deployable package that you created earlier. [![Uploading a deployable package](./media/pack6-1024x325.png)](./media/pack6.png)

## Apply a deployable package
For information about how to apply a deployable package in an environment, see [Installing a deployable package](install-deployable-package.md).

