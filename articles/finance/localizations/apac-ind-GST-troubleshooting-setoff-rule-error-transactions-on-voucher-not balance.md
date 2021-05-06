---
# required metadata

title: Setoff rule error when running a tax settlement 
description: This topic provides troubleshooting information to resolve the setoff rule error the you receive when running a tax settlement.
author: yungu
manager: beya
ms.date: 05/04/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

#ms.search.form:
audience: Application user
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: wangchen
ms.search.validFrom: 2021-04-01
ms.dyn365.ops.version: 10.0.1
---

# Setoff rule error when running a tax settlement 

[!include [banner](../includes/banner.md)]

When you run a tax settlement, you might receive an error. Complete the sections in this topic to resolve the error.

## Find the setoff rule version currently in use

1. Go to **Tax** > **Setup** > **Sales tax** > **Maintain setoff hierarchy profiles**.
2. Find the setoff rule version currently in use based on the effective date. For example, customers want to settle transactions for 2/19/2020. As the following graphic shows, the version 1 setoff rule is used according to the effective date. 

     [![](./media/setoff-rule-error-Picture01.png)](./media/setoff-rule-error-Picture01.png)

## Check the settings of the setoff rule

1. Go to **Tax** > **Setup** > **Sales tax** > **Sales tax hierarchies**, and mark the setoff rule currently in use.
2. Select **View** to check which sales tax hierarchies are used.

     [![](./media/setoff-rule-error-Picture1.png)](./media/setoff-rule-error-Picture1.png)

3. Select **Setoff rules for sales tax hierarchies**.

     [![Direct taxes (tab)](./media/setoff-rule-error-Picture2.png)](./media/setoff-rule-error-Picture2.png)

4. According to the setoff, check if both *Recoverable* and *Payable* nodes are well set; If yes, it maybe posting issue, please go to Microsoft; otherwise, please edit the setoff rule.

     [![Direct taxes (tab)](./media/setoff-rule-error-Picture3.png)](./media/setoff-rule-error-Picture3.png)

## Determine whether customization exists

If you've completed the steps in the previous section but have found no issue, determine whether customization exists. If no customization exists, create a Microsoft service request for further support.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
