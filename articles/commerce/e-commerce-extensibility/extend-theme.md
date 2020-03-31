---
# required metadata

title: Extend a theme
description: This topic describes how to create a theme based off of another theme for a Microsoft Dynamics 365 Commerce online site. 
author: samjarawan
manager: annbe
ms.date: 03/31/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.11

---
# Extend a theme

[!include [banner](../includes/banner.md)]

This topic describes how to create a theme based off of another theme for a Microsoft Dynamics 365 Commerce online site.

## Overview

Themes can be created and modified using the Dynamics 365 Commerce online store extensibility sdk. Themes can be stand alone themes or extended from a base theme. For example, you can have a default base theme that defines module CSS styles, module view extensions and module definition extensions then have a different theme (or set of themes) that add additional changes on top of the base theme. This is helpful when a single Dynamics 365 environments has multiple online sites with different theme branding.

## Setting a base theme

To specify a base theme on a theme, edit the theme definition file and add a '$ref' section.

In the below example, notice the "$ref" that's been addded to reference the fabrikam theme

```json
{
    "$ref": "@msdyn365-commerce-modules/fabrikam-design-kit/dist/lib/modules/fabrikam/fabrikam.definition.json",
    "$type": "themeModule",
    "description": "This is SDK template theme module",
    "friendlyName": "adventureworks",
    "name": "adventureworks"
}
```

The below example shows a base theme definition file and another theme file that derives from the base theme

**basetheme.definition.json**
```json
{
    "$type": "themeModule",
    "description": "This is SDK template theme module",
    "friendlyName": "base",
    "name": "base"
}
```

**contoso.definition.json**
```json
{
    "$ref": "@msdyn365-commerce-modules/fabrikam-design-kit/dist/lib/modules/fabrikam/fabrikam.definition.json",
    "$type": "themeModule",
    "description": "This is SDK template theme module",
    "friendlyName": "adventureworks",
    "name": "adventureworks"
}
```
