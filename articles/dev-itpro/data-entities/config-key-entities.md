
---
# required metadata

title: Configuration keys and data entities
description: This topic describes the relationship between configuration keys and data entities. 
author: Sunil-Garg
manager: AnnBe
ms.date: 01/01/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: margoc
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 25341
ms.assetid: 8e214c95-616b-4ee1-b5a4-fa5ce5147f2c
ms.search.region: Global
# ms.search.industry: 
ms.author: sunilg
ms.search.validFrom: 2018-01-01
ms.dyn365.ops.version: Platform update 13

---

# Configuration keys and data entities
When using data entities for imports and/or exports, it is recommended to first understand what impact if any, would configuration keys will have on the data entities that you are planning to use. It is recommended that you follow the below defined process for determining this prior to using data entities. 

To learn more about configuration keys in D365FO, refer to this topic.

### Configuration key assignments
Configuration keys can be assigned to one or all the following artifacts.
-   Data entity

    -   Table(s) (which are added as data sources)

        -   Field(s)

    -   Fields (data entity fields)

Following table provides a summary of what the expected behavior should be under various scenarios while dealing with configuration keys.
| **Config key setting on data entity** | **Config key setting on table** | **Config key setting on table field** | **Config key on data entity field** | **Expected behavior**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|---------------------------------------|---------------------------------|---------------------------------------|-------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Disabled                              | Doesn’t matter                  | Doesn’t matter                        | Doesn’t matter                      | If the configuration key on the data entity is disabled, the data entity will not be functional. It will not matter in this case if the configuration keys in the underlying table(s) and field(s) were enabled or disabled.                                                                                                                                                                                                                                                                                                              |
| Enabled                               | Disabled                        | Doesn’t matter                        | Doesn’t matter                      | If the configuration key on the data entity is enabled, data management will then check the configuration key on each of the underlying tables. If the configuration key of a table is disabled, that table will not be available in the data entity for functional use. The field level configuration key nor the entity field from that table will not matter in this case. Note that, if the primary table in the entity has its configuration key disabled, then this will behave as if the entity’s configuration key were disabled. |
| Enabled                               | Enabled                         | Disabled                              | Doesn’t matter                      | If the configuration key on the data entity and the underlying table(s) are enabled, data management will check the configuration key on each one of the fields in the table(s). If the configuration key of a field is disabled, that field will not be available in the data entity for functional use even if the corresponding entity field had the configuration key enabled.                                                                                                                                                        |
| Enabled                               | Enabled                         | Enabled                               | Disabled                            | If the configuration key is enabled at all levels but the entity field, then the field will not be available for use in the data entity.                                                                                                                                                                                                                                                                                                                                                                                                  |

[!include[banner](../includes/banner.md)]
