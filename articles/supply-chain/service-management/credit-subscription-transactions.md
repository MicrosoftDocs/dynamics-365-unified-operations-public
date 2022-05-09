---
# required metadata

title: Credit subscription transactions  
description: This topic shows how to credit subscription transactions.
author: sorenva
ms.date: 05/01/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SMASubscriptionTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sorenand
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Credit subscription transactions 

[!include [banner](../includes/banner.md)]


## Credit subscription transactions

1.  Click **Service management** \> **Common** \> **Service subscriptions** \> **All service subscriptions**.

2.  Select the subscription attached to the subscription transaction for which you want to create a credit note.

3.  Select the **Analyze** tab, and then click the **Fee transactions** button on the Action Pane.

4.  From the **Fee transactions** form, select the transaction for which you want to create a credit note.

5.  Click **Functions** \> **Select for credit note**.

6.  From the **Select for credit note** form, select the transaction that you want to credit and then click **OK**.


> [!NOTE]
> <P>When you create the credit note, make sure that you select <STRONG>Credit notes</STRONG>. This is found in the <STRONG>Invoicing method</STRONG> list in the <STRONG>Create invoice</STRONG> dialog box.</P>

If the **Reverse accruals on crediting** field in the **Service management parameters** form is set to **Manual**, you have to reverse each accrued revenue transaction individually before you create a credit note proposal for the transaction.

## See also

[Invoice subscription transactions](invoice-subscription-transactions.md)


 


[!INCLUDE[footer-include](../../includes/footer-banner.md)]