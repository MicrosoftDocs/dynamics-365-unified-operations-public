---
# required metadata

title: Style presets
description: This topic describes how to add authorable style variables to a custom theme which are exposed inside the site builder tool.
author: samjarawan
manager: annbe
ms.date: 05/28/2020
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
ms.dyn365.ops.version: Release 10.0.5
---

# Configure theme settings

[!include [banner](../includes/banner.md)]

This topic describes how to add authorable style variables to a custom theme which are exposed inside the site builder tool.

## Overview

A style preset is a stored set of all authorable style values across a site's theme. It can be used to immediately change the look of a site from site builder. Style presets let Commerce site builder authors quickly change, preview, and activate a set of style values across their site, without having to use Cascading Style Sheets (CSS) or deploy themes. Font styles, button styles, and site colors are typical examples of style variables that can be managed through style presets.


For more details on how the features works from the site builder tool see the [Work with style presets](../style-presets.md) documentation.

## Style preset definition files
Each theme contains a style presets definition file, which provides the metadata for the site builder tool including the friendly name and description.  This file then includes the global and module specific styles that will be exposed to the authoring tool to be customized as desired.

When using the CLI command 'add-theme' to create a theme, the style preset definition file is automatically created and can be found under the theme "styles" directory.  The file name uses the pattern THEME_NAME.definition.scss.json file.

The below is an example theme style definition file created as part of the 'add-theme' CLI command.

![Style presets definition file](media/style-presets.png)



The below example shows a theme called "spring" with two style presets defined, one called 

