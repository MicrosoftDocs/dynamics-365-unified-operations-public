---
# required metadata

title: Landed cost procurement and sourcing parameters
description: This topic describes how to set up the relevant procurement and sourcing parameters when you use Landed cost.
author: mkirknel
manager: tfehr
ms.date: 12/09/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mkirknel
ms.search.validFrom: 2020-12-09
ms.dyn365.ops.version: Release 10.0.17
---

# Landed cost procurement and sourcing parameters

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

The **Procurement and sourcing parameters** page has a few settings that are especially relevant when you are using the Landed cost module. Use the **Update order lines** dialog box (accessible from the **Procurement and sourcing parameters** page) to specify whether you want to update purchase order lines automatically when making modifications in the purchase order header. To set this option, do the following steps:

1. Go to **Procurement and sourcing > Setup > Procurement and sourcing parameters**.
1. On the **General** tab, select the **Update order lines** link.
1. The **Update order lines** dialog box opens. It lists the fields in the order header that can also apply automatic updates to related fields in the order lines. Set each listed field to one of the following values:
    - **Always** - The order lines are updated automatically when the order header is updated.
    - **Never** - The order lines are never updated when the order header is updated.
    - **Prompt** - The user is prompted to choose whether to update the order lines.
