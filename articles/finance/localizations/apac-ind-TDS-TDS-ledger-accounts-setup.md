---
# required metadata

title: Set up TDS ledger accounts
description: This article explains how to set up ledger accounts for the Tax Deducted at Source (TDS) feature.
author: kailiang
ms.date: 02/12/2021
ms.topic: article
ms.prod: 

ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# 
# ms.tgt_pltfrm: 
ms.assetid: b4b406fa-b772-44ec-8dd8-8eb818a921ef
ms.search.region: Global
# ms.search.industry: 
ms.author: kailiang
ms.search.validFrom: 2021-02-12
ms.dyn365.ops.version: AX 10.0.17

---

# Set up TDS ledger accounts

[!include [banner](../includes/banner.md)]

This article explains how to set up ledger accounts for the Tax Deducted at Source (TDS) feature. You use the **Chart of accounts** page to set up ledger accounts for TDS.

1. Go to **General ledger \> Chart of accounts \> Accounts \> Main accounts**.
2. On the **Overview** tab, select **Alt+N** to create a TDS ledger account, and enter the required details.
3. On the **Setup** tab, in the **Posting type** field, select **Withholding tax**.		

    > [!NOTE]
    > Ledger accounts that have a posting type of **Withholding tax** can be defined only as receivable accounts that are used to post the TDS receivable amount for a TDS tax code.

4. Close the page.
