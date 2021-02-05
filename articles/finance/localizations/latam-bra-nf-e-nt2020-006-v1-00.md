---
# required metadata

title: NT2020.006 – Intermediary sales digital platform for NF-e
description: This topic explains how to tag intermediary digital sales for NF-e.
author: gionoder
manager: AnnBe
ms.date: 02/05/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Brazil
# ms.search.industry: 
ms.author: sndray
ms.search.validFrom: 2021-02-05
ms.dyn365.ops.version: 8.0

---

# NT2020.006 – Intermediary sales digital platform for NF-e

[!include [banner](../includes/banner.md)]

In the scenarios where a sale was accomplished without the physical presence of the consumer, and the transaction was intermediated by a digital platform or marketplace, the XML of the electronic fiscal document model 55 (NF-e) issued from this sale must contain a new tag to indicate the participation of such intermediary in the operation.

## Enable the technical note in Dynamics 365 Finance and Dynamics 365 Supply Chain Management

1. Log in to your Finance or Supply Chain Management instance.
2. Go to **Organization administration** > **Organizations** > **Fiscal establishments** > **Fiscal establishments**.
3. Select the fiscal establishment and then select **Edit**.
4. On the **NF-e and NFC-e federal** FastTab, in the **NF-e technical notes** field group, select **Enable NF-e technical note**.
5. In the **NF-e technical notes** field, select **2020.006 v1.00 technical note**.

## Enable the technical note in Microsoft Dynamics AX2012 R3

To enable the technical note in Dynamics AX2012 R3, apply KB 4598546.

## Sale intermediated by own sales digital platform

When the sale is intermediated by a digital platform owned by the tax payer, if one of the following options is selected as the presence type in the header of the sales order created for this sale, the tag **&lt;indintermed&gt;** is added to the XML of the NF-e with a value of zero (0).

- Internet
- Telesales
- Others

## Out of scope of the feature

- The NF-e issued from free text invoices generated from a sale without the presence of the consumer and intermediated by a sale digital platform is not in the scope of this feature.
- The NF-e issued from returns, transfer orders, complementary and tax credit scenarios are not in scope for this feature.
