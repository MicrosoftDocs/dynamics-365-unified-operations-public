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

Tax Deducted at Source (TDS) is calculated on intercompany transactions. This topic describes the process whereby TDS is calculated in phases in intercompany transactions.

When an intercompany purchase order or sales order is created, the default TDS group defined for the customer or vendor is used to calculate TDS. TDS amount is posted to the recoverable or payable accounts after the invoice is posted.

1. A sales order or purchase order is created automatically in the intercompany for the original purchase order or sales order. The default TDS group is also displayed in the automatically created order to calculate TDS and can be modified. If the net invoice amount after deducting the TDS amount of the automatically created order does not match the net invoice amount of the original order, the invoice cannot be posted.

   For example, a sales invoice is created for 50000. A TDS group-10% is attached to the invoice. The posted invoice amount is 45000 and the posted TDS amount is 5000 for the sales invoice. A purchase order is automatically created for the sales order in the intercompany with the TDS group-10%. If you change the TDS group to 15%, you cannot post the invoice because the net invoice amount of the automatically created order does not match the net invoice amount of the original order.

2. When a payment journal is created for an intercompany invoice, a payment journal is posted automatically in the intercompany. If the net payment amount of the automatically created payment journal does not match the net payment amount of the original payment journal, the automatically created payment journal cannot be posted.
