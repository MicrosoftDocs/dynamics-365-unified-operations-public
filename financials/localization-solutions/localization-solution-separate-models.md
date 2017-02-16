---
# required metadata

title: Separate localization models
description: As part of the requirements for LCS solutions for localization &amp; translation, if a localization solution for previous versions of Microsoft Dynamics AX contains both regulatory and competitive features, localization ISV solution providers must split the solution into separate models for each feature type. This article provides information about this requirement.
author: ShylaThompson
manager: AnnBe
ms.date: 2015-12-14 15 - 53 - 58
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
ms.assetid: ab7c2efb-65e9-41fd-bab2-7a6aca5989ea
ms.search.region: Global
# ms.search.industry: 
ms.author: filatovm
ms.dyn365.ops.intro: Feb-16
ms.dyn365.ops.version: AX 7.0.0

---

# Separate localization models

As part of the requirements for LCS solutions for localization &amp; translation, if a localization solution for previous versions of Microsoft Dynamics AX contains both regulatory and competitive features, localization ISV solution providers must split the solution into separate models for each feature type. This article provides information about this requirement.

Multinational customers must comply with regulatory requirements in all countries/regions where they deploy Microsoft Dynamics AX. At the same time, these customers want to minimize the cost of code maintenance. Therefore, if a localization solution for previous versions of Dynamics AX contains both regulatory and competitive features, the solution must be split into separate models, so that customers can adopt and deploy the features that they require. An effort has been made to split the Application foundation and Application suite of the Dynamics AX stack into multiple models. The number of models is expected to grow over time. Splitting a monolithic code base provides many benefits, such as better scalability, manageability, and serviceability. The localization requirement to split a localization solution into more granular models builds on this effort. The goal is to provide the same benefits to multinational customers of Dynamics AX. After you've classified features as either regulatory or competitive, as described in [Localization requirements – Classify localization features](localization-solution-classify-localization-features.md), split the code for these features into at least two models, one model for the regulatory features and at least one model for the competitive features. If the competitive features can be split further (for example, into features that are related to Retail and features that are related to Fixed assets), it's a good idea to split them. However, further splitting isn't mandatory. For more information about how to split the Dynamics AX stack into multiple models, see [Understanding the model split](model-split.md).

