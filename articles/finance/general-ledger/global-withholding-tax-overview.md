---
# required metadata

title: Global withholding tax
description: This article provides information about global withholding tax functionality and how to set it up. Global withholding tax functionality is enhanced for vendor and customer transactions, so that withholding tax is calculated at the item level.
author: kailiang
ms.date: 01/12/2021
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LedgerParameters
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# 
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: b4b406fa-b772-44ec-8dd8-8eb818a921ef
ms.search.region: Global
# ms.search.industry: 
ms.author: kailiang
ms.search.validFrom: 2020-01-12
ms.dyn365.ops.version: AX 10.0.16

---

# Global withholding tax

[!include [banner](../includes/banner.md)]

This article provides information about global withholding tax functionality and explains how to set it up. The new functionality is available in version 10.0.17 and later.

Global withholding tax functionality is enhanced for vendor and customer transactions, so that withholding tax is calculated at the item level. The balance in the withholding tax account from purchase transactions can be settled by running the withholding tax payment job against the withholding tax settlement account.

> [!NOTE]
> Global withholding tax doesn't support the **Maintain charges** function on the purchase order, vendor invoice, and sales order pages.

## Turn on global withholding tax

1. In the **Feature management** workspace, select **Global withholding tax**, and then select **Enable now**.
2. Go to **Tax \> Setup \> Parameters \> General ledger parameters**, and then, on the **Withholding tax** tab, set the **Enable global withholding tax** option to **Yes**.
3. Select **Save**.
4. Refresh the page in your web browser.

> [!NOTE]
> Global withholding tax functionality can’t be turned on for countries/regions where localized withholding tax solutions already exist. These areas include but are not restricted to India, Brazil, Thailand, Saudi Arabia, Ireland, Great Britain and the United States.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
