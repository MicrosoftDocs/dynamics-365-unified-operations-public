---
# required metadata

title: Model management lifecycle (preview)
description: This topic describes ways to maintain your organization's machine learning models to optimize the predictions that they generate.
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

This topic describes ways to maintain your organization's machine learning models to optimize the predictions that they generate.

We recommend training the AI model in a sandbox environment, and then deploying it to a production environment using managed solutions. This will help ensure proper controls are in place for managing the model lifecycle.

Since the AI model is based on the available invoice and customer data, it is important that the sandbox environment has a recent copy of the production data. You can begin training your model by following the steps in the [Use Customer payment predictions](use-customer-payment-predictions.md) topic. Once the model has been re-trained, evaluate the results as described in the [Evaluate the initial customer payment prediction model](evaluate-payment-prediction.md) topic, and use [Improve the prediction model](improve-model.md) topic to experiment with feature and filter combinations that can improve the model.  

When you're satisfied with the training results, follow the steps in the [Distribute your AI model](https://docs.microsoft.com/ai-builder/distribute-model) topic to transition the model to your production environment.
 
