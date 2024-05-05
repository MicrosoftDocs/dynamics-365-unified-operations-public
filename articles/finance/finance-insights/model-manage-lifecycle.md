---
title: Model management lifecycle
description: Learn about ways to maintain your organization's machine learning models to optimize the predictions that they generate.
author: ShivamPandeyMSFT
ms.author: shpandey
ms.topic: article
ms.date: 07/16/2021
ms.reviewer: kfend
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2020-05-28
ms.search.form: 
ms.dyn365.ops.version: AX 10.0.8
ms.assetid: 3d43ba40-780c-459a-a66f-9a01d556e674
---

# Model management lifecycle

[!include [banner](../includes/banner.md)]

This article describes ways to maintain your organization's machine learning models to optimize the predictions that they generate.

We recommend that you train the AI model in a sandbox environment and then use managed solutions to deploy it to a production environment. This approach helps ensure that the correct controls are in place for managing the model lifecycle.

Because the AI model is based on the available invoice and customer data, it's important that the sandbox environment have a recent copy of the production data. You can begin to train your model by following the steps in [Use Customer payment predictions](use-customer-payment-predictions.md). After the model has been retrained, evaluate the results as described in [Evaluate the initial customer payment prediction model](evaluate-payment-prediction.md). Use the information in [Improve the prediction model](improve-model.md) to experiment with feature and filter combinations that can help improve the model.

When you're satisfied with the training results, follow the steps in [Distribute your AI model](/ai-builder/distribute-model) to transition the model to your production environment.
