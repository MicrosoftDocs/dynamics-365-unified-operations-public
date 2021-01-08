---
# required metadata

title: Global withholding tax overview
description: This topic provides information about global withholding tax functionality and how to set it up. Global withholding tax functionality is enhanced for vendor and customer transactions, so that withholding tax is calculated at the item level.
author: roschlom
manager: AnnBe
ms.date: 01/12/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 15721
ms.assetid: b4b406fa-b772-44ec-8dd8-8eb818a921ef
ms.search.region: Global
# ms.search.industry: 
ms.author: kailiang
ms.search.validFrom: 2020-01-12
ms.dyn365.ops.version: AX 10.0.16

---

# Global withholding tax overview

This topic provides information about global withholding tax functionality and how to set it up. Global withholding tax functionality is enhanced for vendor and customer transactions, so that withholding tax is calculated at the item level. The balance in withholding tax account from purchase transactions can be settled via withholding tax payment job procedure against withholding tax settlement account.

> [!Note]
>
> Global withholding tax is not supporting **Maintain charges** in Purchase order, Vendor invoice and Sales order forms.

## Enable global withholding tax

Tihs topic walks through the steps for enabling the new global withholding tax capability, which became available with the release of version 10.0.17. 

To enable global withholding tax functionality,complete the following steps.

1. Go to **Feature management**, Select **Global withholding tax**, click **Enable now**.
2. Go to **Navigation pane > Modules > Tax > Setup > Parameters > General ledger parameters**, In **Withholding tax** tab, switch on **Enable global withholding tax**.
3. Click **Save**.
4. Refresh your browser.

> [!NOTE] 
> Global withholding tax functionality cannot be enabled for following countries/regions where localized withholding tax solutions already exist: **India**, **Brazil**, **Thailand**, **Saudi Arabia**, **Ireland** and **Great Britain**.
