---
# required metadata

title: Customize App Suite reports using extensions
description: This topic discusses a series of scenarios for customizing App Suite reports.
author: sericks007
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 2051
ms.search.scope: Operations, Platform
# ms.tgt_pltfrm: 
ms.custom: 266614
ms.assetid: acf73781-08bb-4f59-9956-8f9f295ddd02
ms.search.region: Global
# ms.search.industry: 
ms.author: tjvass
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Platform update 3

---

# Customize App Suite reports using extensions

[!include[banner](../includes/banner.md)]


This topic discusses a series of scenarios for customizing App Suite reports.

Microsoft Dynamics 365 for Finance and Operations offers an expanded set of tools to support custom solutions. Customizations to reporting solutions in the standard application are fully supported using a pure extension model. This topic contains guidance about how to add the most common customizations to standard application reports without overlayering Application Suite artifacts. Here are some of the key benefits of using an extension-based approach when customizing the application:

-   It reduces the footprint of your application solutions by minimizing code duplication.
-   Custom reports benefit from enhancements made to standard solutions including updates to business logic in Report Data Provider (RDP), data contracts, and UI Builder classes.
-   Standard application solutions are unaffected and continue to be available in concert with custom reports.

Report extensions do not break or prevent access to standard application reports. Instead, the platform supports run-time selection of the target report allowing you to choose the appropriate report design based on the context of the user session. For more information about customizations using extensions, see [Customization: Overlayering and extensions](..\extensibility\customization-overlayering-extensions.md)

## Scenarios
There are four key scenarios which demonstrate the flexibility available. The first two scenarios involve extending existing RDP classes for custom reporting solutions.

-   [Expand existing datasets](expand-app-suite-report-data-sets.md) - Use table extensions and integrate custom business logic to add custom columns to an existing dataset.
-   Composing custom datasets – Add more data to application reports by extending an existing RDP class to return a custom dataset.

The other two scenarios offer insights on how to use extensions to redirect application navigations to your custom solutions.

-   [Extend report menu items](extend-report-menu-items.md) – Customize application menu items to redirect references to a custom report design.
-   [Custom designs for business documents](custom-designs-business-docs.md) – Delegate handlers allow you to add custom report designs to an existing Print Management document instance.




