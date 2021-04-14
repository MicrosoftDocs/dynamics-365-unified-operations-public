---
# required metadata

title: Setoff rule error The transactions on voucher do not balance as per…
description:
author: yungu
manager: beya
ms.date: 02/04/2021
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



# Setoff rule error The transactions on voucher do not balance as per…

[!include [banner](https://github.com/MicrosoftDocs/dynamics-365-unified-operations-public/blob/live/articles/finance/includes/banner.md)]

## **Symptom**

- Error message "The transactions on voucher do not balance as per…" shows when running sales tax settlement.

 

## **Trouble shooting guide**

- **Step 1: Find the setoff rule version currently used**

- 1. Go to "*Modules -> Tax -> Setup ->Sales tax -> Maintain setoff hierarchy profiles*".

  2. Find the setoff rule version currently used according to the effective date.

     For example, customers want to settle transactions in 2/19/2020. As shown in the figure below, the version 1 setoff rule is used according to the effective date. 

     [![Direct taxes (tab)](./media/setoff-rule-error-Picture01.png)](./media/setoff-rule-error-Picture01.png)

- **Step 2: Check setoff rule settings**

  1. Go to "*Modules -> Tax -> Setup -> Sales tax -> Sales tax hierarchies*", mark the setoff rule currently used.

  2. Click "View" to check the sales tax hierarchies under usage.

     [![Direct taxes (tab)](./media/setoff-rule-error-Picture1.png)](./media/setoff-rule-error-Picture1.png)

  3. Click "Setoff rules for sales tax hierarchies"

     [![Direct taxes (tab)](./media/setoff-rule-error-Picture2.png)](./media/setoff-rule-error-Picture2.png)

  4. According to the setoff, check if both *Recoverable* and *Payable* nodes are well set; If yes, it maybe posting issue, please go to Microsoft; otherwise, please edit the setoff rule.

     [![Direct taxes (tab)](./media/setoff-rule-error-Picture3.png)](./media/setoff-rule-error-Picture3.png)

- **Step 3: If no issue is found in above steps, check whether customization exists. If not, create a service request to Microsoft for further support.**


[!INCLUDE[footer-include](https://github.com/MicrosoftDocs/dynamics-365-unified-operations-public/blob/live/articles/includes/footer-banner.md)]
