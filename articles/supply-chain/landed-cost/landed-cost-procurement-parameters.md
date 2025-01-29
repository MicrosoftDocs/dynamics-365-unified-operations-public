---
title: Procurement and sourcing parameters for Landed cost
description: Learn how to set up the relevant Procurement and sourcing parameters when you use the Landed cost module, including a step-by-step process.
author: lisascholz91
ms.author: lisascholz
ms.topic: article
ms.date: 12/09/2020
ms.custom:
ms.reviewer: kamaybac
ms.search.form: SrmParameters
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
