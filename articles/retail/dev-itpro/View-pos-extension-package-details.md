---
# required metadata

title: View POS extension package information
description: This article describes the steps for merging the build systems for both Dynamics 365 for Finance and Operations, and Dynamics 365 for Retail using Azure DevOps.  
author: mumani
manager: AnnBe
ms.date: 02/25/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: Tonya.Fehr
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 2019-02-25
ms.dyn365.ops.version: AX 10.0.1

---

# View POS extension package information:

We added a new section “Extension packages” in the POS settings view to show the list of POS extension packages included part of the core POS. Under each package you can find the status of the package whether the extension is loaded, failed or skipped.

**Extension package status:**

   **Loaded** – Extension package loaded successfully.

   **Failed** – Failed in loading the extension package.

   **Skipped** – Loading of the extension package is skipped. In the extension manifest we can specify to load the package only for particular locale and skip in all the other locales.

**Ex:** Load extension only in “*en-fr”* and must be skipped in all the other locale.

> [!NOTE]
> This topic applies to Dynamics 365 for Finance and Operations, and to Microsoft Dynamics 365 for Retail with application update 10.0.1 or later.

[![POS Extension package details](./media/ExtensionPackage.png)](./media/ExtensionPackage.png)

**Extension package details:**

Now you can also view the details of each extension package and troubleshoot which extension file is causing the issue in case of the extension loading is failed or skipped or if there is conflicting extension.

To view the details of each extension package, click the view details button under the package details tile. Once the View details button is clicked POS will navigate to a new view where you can see the details of all the individual extension within the package. If any of the extension is failed or skipped to load you can see the details in the right pane. The status column shows the status of the individual extension within that package, name column shows the name of the extension type and the path column shows the path of the implementation file within the package. You can also view the description of each extension item in the right details pane. Click on each line item to view the details of the extension item in the right pane.

Note: All the information like description, type, name etc. are shown based on the manifest file included in the extension package. The POS extension loader loads all the extension package and updates the status, log the error and shows it in the extension details view when POS fails to load the extension.

**Note:** If there is any conflicting extension between packages now you can identify it easily from this view.
