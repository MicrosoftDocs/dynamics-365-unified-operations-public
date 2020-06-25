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

The below is an example theme style definition file created as part of the 'add-theme' [CLI command](cli-command-reference.md).

![Style presets definition file](media/style-presets.png)

## Style preset definition schema

* "**$type**" - The definition file type.  This must be "styleDefinition"
* "**name**" – The name of the theme. This property must match the theme name found in the theme definition file.
* "**friendlyName**" – The friendly name of the style preset. This name is shown in the site builder tool when configuring style presets. The minimum length is three characters.
* "**description**" – The description of the style preset. The description provides a friendly string that is shown in the site builder tool when configuring the style presets.
* "**global**" – The global section is used to add style presets that are globally scoped across the theme.
* "**module**" – The module section is used to add style presets that are scoped only to specific modules.  Module names are used as children of this node to define module specific style presets.

### Style schema
The below schema is used for each style property defined in the global and module style section.
* "**friendlyName**" – The friendly name of the individual style preset property. This name is shown in the site builder tool when configuring style presets. The minimum length is three characters.
* "**description**" – The description of the style preset property. The description provides a friendly string that is shown in the site builder tool when configuring the style presets.

## Style preset instances

