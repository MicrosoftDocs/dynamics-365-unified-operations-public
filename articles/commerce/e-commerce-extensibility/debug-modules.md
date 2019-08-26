---
# required metadata

title: Debug modules
description: This topic describes the various options available to help debug modules during development.
author: samjarawan
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
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
# Debug modules

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes the various options available to help debug modules during development.

## Overview

The e-Commerce functionality in Dynamics 365 Commerce uses React and Node, which supports client-side debugging. Although you can also use standard React and Node debugging patterns, they aren't covered in this topic.

## Debug using a query string parameter

When you test your modules in a local developer environment, you can add the **&debug=true** query parameter to the query string. This parameter provides extended trace output in the **Command Prompt** window that is running Yarn.

## Debug using a browser

During the development of modules, you can take advantage of the standard debugging tools available in your web browser. For more information, see the browser documentation.
