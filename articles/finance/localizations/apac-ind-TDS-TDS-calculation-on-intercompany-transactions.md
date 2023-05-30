---
# required metadata

title: TDS calculation on intercompany transactions
description: This article describes the process that is used to calculate Tax Deducted at Source (TDS) on intercompany transactions in phases.
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

# TDS calculation on intercompany transactions

[!include [banner](../includes/banner.md)]

This article describes the process that is used to calculate Tax Deducted at Source (TDS) on intercompany transactions in phases.

When an intercompany purchase order or sales order is created, the default TDS group that is defined for the customer or vendor is used to calculate the TDS amount. The TDS amount is posted to the recoverable or payable accounts after the invoice is posted.

An intercompany sales order or purchase order is automatically created for the original purchase order or sales order. The default TDS group is shown on the intercompany order, so that TDS can be calculated. You can change the TDS group. The invoice can be posted only if the net invoice amount on the intercompany order that is automatically created matches the net invoice amount on the original order. (The net amount is the invoice amount after TDS is deducted.)

For example, a sales invoice is created for 50,000, and the **10%** TDS group is attached to it. The posted invoice amount is 45,000, and the posted TDS amount for the sales invoice is 5,000. A purchase order is automatically created for the intercompany sales order, and the  **10%** TDS group is attached to it. If you change the TDS group to **15%**, you can't post the invoice, because the net invoice amount of the intercompany sales order that was automatically created doesn't match the net invoice amount of the original sales order.

A payment journal that is created for an intercompany invoice is automatically posted. That payment journal can be posted only if the net payment amount on it matches the net payment amount on the original payment journal.
