---
title: What's new in Dynamics Translation Service 
description: Learn about new or changed features in the Microsoft Dynamics Translation Service, including overviews on service degradation and incident updates.
author: joshsantana
ms.author: joshsantana
ms.topic: overview
ms.date: 03/07/2023
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 
ms.dyn365.ops.version: 2012
---

# What's new in Dynamics Translation Service

[!include[banner](../includes/banner.md)]

This article provides information about the new or changed features in Microsoft Dynamics Translation Service (DTS).

## DTS will not support Dynamics NAV after June 1, 2024  

Mainstream support for Dynamics NAV 2018 ended on Jan 10, 2023. DTS ends support for Dynamics NAV 2018 and prior versions by June 1, 2024.

## Dynamics 365 Translation Service Connector release

The Dynamics 365 Translation Service Connector is now available. Because this connector integrates with Microsoft Power Platform, you can access DTS directly from a flow or app. The connector calls the DTS API on the user's behalf, saving them a trip to the website.

The following functionality is supported:

- Translate user interface (UI) files.
- Regenerate translation requests.
- Create translation memory (TM) files.

To learn more, see [Dynamics Translation Service](/connectors/dynamicstranslations/).

## DTS API release

The DTS API is now available for DTS users. With the API, customers can perform Translation, Alignment, and Regeneration actions without the need to visit Lifecycle Services. This release allows developers to create custom translation solutions, using the capabilities of DTS. For more information, see [Dynamics 365 Translation Service API](dts-api-info.md).

## Incident update: DTS API failures impacting extension users

The Lifecycle Services team has identified the root cause of the problem. The necessary fixes will be rolled out in the next release, and we anticipate that the DTS API will be fully functional by April 15, 2023.

We understand the inconvenience that this issue has caused, and appreciate your patience and continuous support for the DTS.

If you require immediate support, contact the support team at dtssup@microsoft.com.

## Incident: DTS API failures impacting extension users

We're investigating an issue that causes intermittent API failures across DTS endpoints. This is an active incident that impacts the usability of the DTS extensions. Contact dtssup@microsoft.com if you require immediate support. 

## DTS will stop supporting Dynamics AX 2012 by March 31, 2023

Mainstream and extended support for Dynamics AX 2012 has ended. DTS will end support for Dynamics AX 2012 R3 by March 31, 2023. 

## Visual Studio Code extension

The Visual Studio Code extension was created for Dynamics 365 Business Central users who develop extensions in AL by using the AL language extension. The Visual Studio Code extension provides a DTS integration into the AL environment for Business Central developers.

The following features are included in the Visual Studio Code extension:

- **DTS Translation** – Create translation requests for resource files in a workspace.
- **Resource file explorer** – View and manage existing resource files.

To download the Visual Studio Code extension, go to [Dynamics 365 Translation Service Visual Studio Code extension on Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=dts-publisher.dts-vsc). For more information, see [Dynamics 365 Translation Service Visual Studio Code extension](dts-vscode-doc.md).

## Visual Studio extension release

The DTS extension for Visual Studio was created so that finance and operations developers can perform actions in DTS directly from their Visual Studio integrated development environment (IDE). To use the DTS Visual Studio extension, you must have access to Microsoft Dynamics Lifecycle Services. Additionally, the extension is intended primarily to support the development workflow for finance and operations apps in Visual Studio.

The following features are included in the Visual Studio extension release:

- **Translation** – Create translation requests for label resource files in the project.
- **Regenerate** – Post-edit the XLIFF outputs, and regenerate the label resource files.
- **Align** – Create XLIFF translation memories (TMs) from previously translated label resource files.

To download the Visual Studio extension, go to [Dynamics 365 Translation Service Visual Studio extension on Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=dts-publisher.dts-vs-ext&ssr=false#overview). For more information, see [Dynamics 365 Translation Service Visual Studio extension](dts-visual-studio.md).
