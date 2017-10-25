---
# required metadata

title: Data entities - Fixed assets
description: This article provides a list of the data entities that are available for Fixed assets.
author: kfend
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 96073
ms.assetid: 1e224c6b-d4ad-4a8f-b620-99087f3a329f
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Data entities - Fixed assets

[!include[banner](../includes/banner.md)]


This article provides a list of the data entities that are available for Fixed assets.

Available data entities
-----------------------

**16.1.001 FA – Fixed assets attributes**

| Suggested sequence | Entity name                    | Area         | Entity type | Dependency | Comments                                                                                                                                                                                                               |
|--------------------|--------------------------------|--------------|-------------|------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1                  | Fixed asset major type         | Fixed assets | Setup       | None       | Use to identify high-level asset groups.                                                                                                                                                                               |
| 2                  | Fixed asset activity codes     | Fixed assets | Setup       | None       | Use to set up asset activity codes that can be assigned to fixed assets, so that you can track fixed assets according to the activity categories that they are used for.                                               |
| 3                  | Fixed asset property groups    | Fixed assets | Setup       | None       | Use to set up property groups that can be assigned to fixed assets, so that you can track fixed assets according to the categories that they belong to.                                                                |
| 4                  | Fixed asset condition          | Fixed assets | Setup       | None       | Use to identify conditions of fixed assets, such as good or excellent.                                                                                                                                                 |
| 5                  | Fixed asset properties         | Fixed assets | Setup       | None       |                                                                                                                                                                                                                        |
| 6                  | Fixed asset acquisition method | Fixed assets | Setup       | None       | Use to define the ways that you can acquire assets.                                                                                                                                                                    |
| 7                  | Fixed asset provision types    | Fixed assets | Setup       | None       | Use to set up controls for posting profits from the sale of a fixed asset, or for posting the reserve value of an asset if a revenue recognition of reserves proposal has been created for a fixed asset journal line. |

**16.1.002 FA – Fixed assets setup**

| Suggested sequence | Entity name                                 | Area         | Entity type | Dependency                                  | Comments                                                                                                                                          |
|--------------------|---------------------------------------------|--------------|-------------|---------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| 8                  | Fixed asset groups                          | Fixed assets | Setup       | None                                        | Use to set up the fixed asset groups that define asset characteristics, such as type, number sequence, and default value models.                  |
| 9                  | Fixed asset depreciation profiles           | Fixed assets | Setup       | None                                        | Use to create and modify depreciation profiles, which contain the calculations that are used to reduce the value of depreciable assets over time. |
| 10                 | Fixed asset depreciation book setup         | Fixed assets | Setup       | Fixed asset depreciation profiles           | Use to create, update, or delete depreciation books.                                                                                              |
| 11                 | Fixed asset value model setup               | Fixed assets | Setup       | Fixed asset depreciation profiles           | Use to create and manage value models for fixed assets.                                                                                           |
| 12                 | Fixed asset group value model setup         | Fixed assets | Setup       | Fixed asset groups, Fixed asset value model | Use to create fixed asset groups that use the selected value model.                                                                               |
| 13                 | Fixed asset posting profile                 | Fixed assets | Setup       | None                                        | Use to specify the ledger accounts that fixed asset transactions are posted to.                                                                   |
| 14                 | Fixed asset posting profile disposal        | Fixed assets | Setup       | Fixed asset posting profile                 | Use to set up the posting accounts that should be used when a fixed asset is sold or scrapped.                                                    |
| 15                 | Fixed asset depreciation book journal names | Fixed assets | Setup       | None                                        | Use to set up depreciation book journal names.                                                                                                    |
| 16                 | Fixed asset parameters                      | Fixed assets | Setup       | Fixed asset value models                    | Use to set up parameters for Fixed assets.                                                                                                        |

**16.1.003 FA – Fixed assets**

| Suggested sequence | Entity name                         | Area         | Entity type | Dependency   | Comments                                                                               |
|--------------------|-------------------------------------|--------------|-------------|--------------|----------------------------------------------------------------------------------------|
| 17                 | Fixed assets                        | Fixed assets | Master      | None         | Use to create fixed assets.                                                            |
| 18                 | Fixed asset group value model setup | Fixed assets | Setup       | Fixed assets | Use to create fixed asset groups that use the selected value model.                    |
| 19                 | Fixed asset depreciation book       | Fixed assets | Master      | Fixed assets | Use to create fixed asset information that is related to a specific depreciation book. |
| 20                 | Fixed asset value model             | Fixed assets | Master      | Fixed assets | Use to create fixed asset information that is related to a specific value model.       |

See also
--------

[Data entities and packages framework](data-entities-data-packages.md)

[Data entities](data-entities.md)



