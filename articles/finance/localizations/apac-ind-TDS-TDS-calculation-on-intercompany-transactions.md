---
# required metadata

title: TDS calculation on intercompany transactions
description: Tax Deducted at Source (TDS) is calculated on intercompany transactions. This topic describes the process whereby TDS is calculated in phases in intercompany transactions.
author: kailiang
manager: AnnBe
ms.date: 02/12/2021
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
ms.search.validFrom: 2021-02-12
ms.dyn365.ops.version: AX 10.0.17

---
# TDS calculation on intercompany transactions

[!include [banner](../includes/banner.md)]

Tax Deducted at Source (TDS) is calculated on intercompany transactions. This topic describes the process for calculcating TDS in phases in intercompany transactions.

When an intercompany purchase order or sales order is created, the default TDS group defined for the customer or vendor is used to calculate the TDS amount. The TDS amount is posted to the recoverable or payable accounts after the invoice is posted.

An intercompany sales order or purchase order is created automatically for the original purchase order or sales order. The default TDS group is also displayed on that order to calculate TDS, and it can be modified. If the net invoice amount on the order that was automatically doesn't match the net invoice amount of the original order, the invoice can't be posted. The net amount is the invoice amount after deducting TDS. 

   For example, suppose a sales invoice is created for 50,000, and that TDS group-10% is attached to the invoice. The posted invoice amount is 45,000 and the posted TDS amount is 5,000 for the sales invoice. A purchase order is automatically created for the intercompany sales order with the TDS group-10%. If you change the TDS group to 15%, you cannot post the invoice because the net invoice amount of the sales order that was created automatically doesn't match the net invoice amount of the original order.

When a payment journal is created for an intercompany invoice, that journal is posted automatically. If the net payment amount of the automatically created payment journal doesn't match the net payment amount of the original payment journal, the payment journal that was created automatically can't be posted.
