---
# required metadata

title: Setoff rule activate take long time
description:
author: shaoling
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



# Setoff rule activate take long time

[!include [banner](https://github.com/MicrosoftDocs/dynamics-365-unified-operations-public/blob/live/articles/finance/includes/banner.md)]

## **Symptom**

- Activate the setoff hierarchy profile takes long time. This usually happens while activating profile for a long period, e.g. 1 year.

  [![Direct taxes (tab)](./media/setoff-rule-activation-takes-long-time-Picture1.png)](./media/setoff-rule-activation-takes-long-time-Picture1.png)

 

## **Mitigation steps:**

- **Step 1:** Enable feature "*Activate setoff hierarchy profile in batch*".

  [![Direct taxes (tab)](./media/setoff-rule-activation-takes-long-time-Picture2.png)](./media/setoff-rule-activation-takes-long-time-Picture2.png)

- **Step 2**: Activate setoff hierarchy profile in batch mode.

  [![Direct taxes (tab)](./media/setoff-rule-activation-takes-long-time-Picture3.png)](./media/setoff-rule-activation-takes-long-time-Picture3.png)

- **Step 3:** Check job status.

  [![Direct taxes (tab)](./media/setoff-rule-activation-takes-long-time-Picture4.png)](./media/setoff-rule-activation-takes-long-time-Picture4.png)

- **Step 4:** If cannot resolve issue with above steps, check whether customization exists. If not, create a service request to Microsoft for further support.



[!INCLUDE[footer-include](https://github.com/MicrosoftDocs/dynamics-365-unified-operations-public/blob/live/articles/includes/footer-banner.md)]