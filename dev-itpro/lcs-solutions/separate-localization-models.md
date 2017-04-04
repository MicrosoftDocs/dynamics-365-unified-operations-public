---
# required metadata

title: Separate localization models
description: As part of the requirements for LCS solutions for localization &amp; translation, if a localization solution for previous versions of Microsoft Dynamics 365 for Operations or Microsoft Dynamics 365 for Operations contains both regulatory and competitive features, localization ISV solution providers must split the solution into separate models for each feature type. This article provides information about this requirement.
author: ShylaThompson
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: ShylaThompson
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 27561
ms.assetid: 49b634ab-d7f7-4e34-a7e9-7350548bf1a0
ms.search.region: Global
# ms.search.industry: 
ms.author: filatovm
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Separate localization models

As part of the requirements for LCS solutions for localization &amp; translation, if a localization solution for previous versions of Microsoft Dynamics 365 for Operations contains both regulatory and competitive features, localization ISV solution providers must split the solution into separate models for each feature type. This article provides information about this requirement.

Multinational customers must comply with regulatory requirements in all countries/regions where they deploy Microsoft Dynamics 365 for Operations. At the same time, these customers want to minimize the cost of code maintenance. Therefore, if a localization solution for previous versions of Dynamics 365 for Operations 365 for Operations contains both regulatory and competitive features, the solution must be split into separate models, so that customers can adopt and deploy the features that they require. An effort has been made to split the Application foundation and Application suite of the Dynamics 365 for Operations stack into multiple models. 
The number of models is expected to grow over time. Splitting a monolithic code base provides many benefits, such as better scalability, manageability, and serviceability. The localization requirement to split a localization solution into more granular models builds on this effort. The goal is to provide the same benefits to multinational customers of Dynamics 365 for Operations. 
After you've classified features as either regulatory or competitive, as described in [Classify localization features](classify-localization-features.md), split the code for these features into at least two models, one model for the regulatory features and at least one model for the competitive features. If the competitive features can be split further (for example, into features that are related to Retail and features that are related to Fixed assets), it's a good idea to split them. However, further splitting isn't mandatory. For more information about how to split the Dynamics 365 for Operations stack into multiple models, see [Understanding the model split](../dev-tools/model-split.md).

