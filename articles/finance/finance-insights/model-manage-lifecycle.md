---
# required metadata

title: Model management lifecycle (preview)
description: This topic describes ways to maintain your organizations machine learning models to optimize the predictions that they generate.
author: ShivamPandey-msft
ms.date: 06/03/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
ms.custom: 14151
ms.assetid: 3d43ba40-780c-459a-a66f-9a01d556e674
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2020-05-28
ms.dyn365.ops.version: AX 10.0.8

---

# Model management lifecycle (preview)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic describes ways to maintain your organizations machine learning models to optimize the predictions that they generate.

It is recommended that the AI model is trained in a sandbox environment and then deployed to a production environment using managed solutions.  This will help ensure proper controls are in place for managing the model lifecycle.

Since the AI model is based on the available invoice and customer data, it is important that the sandbox environment has a recent copy of the production data.  Training can be initiated as described in <link to training steps documentation> [Use Customer payment predictions](use-customer-payment-predictions.md).  Once the model has been re-trained, evaluate the results as described in [Evaluate the initial customer payment prediction model](evaluate-payment-prediction.md) and use <link to improve model documentation> [Improve the prediction model](improve-model.md) to experiment with feature and filter combinations that can improve the model.  

Once you are satisfied with the training results, follow [Distribute your AI model](https://docs.microsoft.com/en-us/ai-builder/distribute-model) to transition the model to the production environment.
 


