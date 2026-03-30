---
title: Extend report menu items to redirect user navigation
description: Learn how to extend existing application menu items so that navigation are redirected to a custom reporting solution.
author: johnmichalak
ms.author: johnmichalak
ms.topic: how-to
ms.date: 10/22/2025
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Platform update 3
ms.assetid: 7bf76862-e320-4a81-81a4-5bda7288e573
---

# Extend report menu items to redirect user navigation

[!include [banner](../includes/banner.md)]

This article shows how to extend existing application menu items so that, with only minimal code changes, you can redirect navigation to a custom reporting solution.

This article focuses on the process of extending existing application menu items so that, with only minimal code changes, you can redirect navigation to a custom reporting solution. By using this technique, you avoid the inconvenience of tracking down and replacing all references to an existing application report. Just extend an existing application menu item to redirect application navigations to reports that you define in an extension model. The following illustration shows a typical application customization.

:::image type="content" source="./media/extendingmenuitem.png" alt-text="Screenshot of typical application customization workflow for extending menu items." lightbox="./media/extendingmenuitem.png":::

## What's important to know?

Before you apply this solution, be aware of the following basic assumptions.

- Extended menu items let you override both the display string and the target.
- You can use this technique for all types of reports, from simple query-based reports to complex report data provider (RDP)–based reports.
- Extended menu items are available for direct references to reports and solutions that orchestrate the reporting session by using a controller class.

## Extend report menu items

The following walkthrough shows how to use menu item extensions to redirect user navigations in the application to a custom solution. The solution includes a custom **Customer list** report for the Fleet Management application and defines all the application customizations in a pure extension model. The following illustration shows the menu item that you use to access the custom **Customer list** report.

:::image type="content" source="./media/fleet-workspace-customer-list.png" alt-text="Screenshot of Fleet workspace customer list menu item.":::

1. **Create a new model for your application customizations.** For more information about extension models, see [Customize through extension and overlayering](../extensibility/customization-overlayering-extensions.md).
1. **Create a new project in Microsoft Visual Studio,** **and add your custom report.** Additionally, add all the solution artifacts. These artifacts include the RDP class or source query, the controller class, and UI builders, if they're present.
1. **Create an extension of the menu item that is used to access the report.** In this example, the output menu item is named **FMCustomerListReport**. Use the menu item structure to find the menu item name that the application exposes. The following illustration shows the action in Application Explorer.

    :::image type="content" source="./media/fleet-extension-create-menu-extension.png" alt-text="Screenshot of creating an extension of the menu item that is used to access the report." lightbox="./media/fleet-extension-create-menu-extension.png":::

1. **Modify the properties of the menu item extension.** Update the report design or controller reference in the menu item to direct navigations to your custom solution.

    > [!NOTE]
    > The property changes that you can make on the object depend on the original application solution. If the application report manages the solution by using a controller, a controller class is required for the report.

1. **Rebuild the solution, and deploy the custom report.**

You finished extending the report menu item. Navigations to the standard menu item now redirect to your custom reporting solution.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
