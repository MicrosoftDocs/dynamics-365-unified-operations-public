---
# required metadata

title: Procurement and sourcing parameters for Landed cost
description: This topic describes how to set up the relevant Procurement and sourcing parameters when you use the Landed cost module.
author: Weijiesa
ms.date: 12/09/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SrmParameters
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: weijiesa
ms.search.validFrom: 2020-12-09
ms.dyn365.ops.version: 10.0.17
---

# Procurement and sourcing parameters for Landed cost

[!include [banner](../../includes/banner.md)]

The **Procurement and sourcing parameters** page has a few settings that are especially relevant when you use the **Landed cost** module. Use the **Update order lines** dialog box that is opened from the **Procurement and sourcing parameters** page to specify whether purchase order lines should automatically be updated when changes are made on the purchase order header.

To complete this setup, follow these steps.

1. Go to **Procurement and sourcing \> Setup \> Procurement and sourcing parameters**.
1. On the **General** tab, select the **Update order lines** link.
1. The **Update order lines** dialog box lists the fields on the order header that can also apply automatic updates to related fields on the order lines. Set each field in the list to one of the following values:

    - **Always** – The order lines should automatically be updated when the order header is updated.
    - **Never** – The order lines should never be updated when the order header is updated.
    - **Prompt** – The user will be prompted to select whether the order lines should be updated.
