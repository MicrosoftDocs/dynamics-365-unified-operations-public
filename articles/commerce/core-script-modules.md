---
# required metadata

title: External and inline script modules
description: This topic covers the external and inline script modules and describes how to add one to a template in Microsoft Dynamics 365 Commerce.
author: samjarawan
manager: annbe
ms.date: 02/11/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---

# External and inline script modules

[!include [banner](includes/banner.md)]

This topic covers the external and inline script modules and describes how to add one to a template in Microsoft Dynamics 365 Commerce.

External and inline scripts can be added to a template's **HTML Head**, **Body Begin** or **Body End** slots.  An example below shows external and inline scripts added to various slots in a template.

![Script modules](media/script-modules-1.png)

## External script module properties

| Property name     | Values | Description |
|-------------------|--------|-------------|
| Script source | Text | The URL of the script file location. |
| execute script asynchronously | **True** or **False** | If true, the script will execute asynchronously. |
| defer script execution | **True** or **False** | If set to true, the script will execute when the page has finished executing. |

## Inline script module properties

| Property name     | Values | Description |
|-------------------|--------|-------------|
| Inline script | Text | The collection of scripting statements that will be inserted inline into script tags on the HTML page. |

## Adding a script module to a template

From within a site builder template select the **Add Module** option within the **...** of the slot you intend to add the script module to. Select the script module followed by the **OK** button as shown below.  Ensure you add the appropriate page summary module based on the page types the template will be used for.

![Add new module](media/script-modules-2.png)

Once the summary module is added it should look similar to the below image.  The module can now be configured and the template can be saved and published.

![Inline script module added](script-modules-3.png)


## Additional resources

[Module library overview](starter-kit-overview.md)

[Default page module](core-page-summary-modules.md)

[Default page module](core-default-page-module.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
