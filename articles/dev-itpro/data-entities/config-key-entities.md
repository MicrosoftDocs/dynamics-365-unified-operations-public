
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

Note, if an entity has another entity as a data source then, the above semantics are applied in a recursive manner.

### Entity list refresh
When the entity list is refreshed, data management builds the configuration key metadata for runtime use. This metadata is built using the above semantics. It is always recommended to wait for the entity refresh to complete before using jobs and entities in data management as the configuration key meta data may not be up to date and could result in an unexpected outcome. When the entity list is being refreshed, the following message is shown in the entity list page.

![Entity list refresh](.media/Entity refresh list.png)

### Data entity list page
The data entity list page in data management shows the configuration key settings for the entities. You must start from this page for each of the entities you plan to use to first understand the impact from configuration keys on the data entity.
This information is shown using the metadata that is built during entity refresh. The configuration key column shows the name of the configuration key that is associated with the data entity. If this is blank, it means, there is no configuration key associated. The configuration key status column shows the state of the configuration key. If it has a tick mark, it means the key is enabled. If it is blank, it means either the key is disabled or there is no key associated.

### Target fields
The next step is to drill into the internals of the data entity to view the impact of configuration keys on tables and fields. The target fields form for a data entity shows configuration key and the key status information for the related tables and the fields in the data entity. If the key column is blank, it means there is no key associated. If the key status column is blank, it means either there is no key is associated or the key is disabled. If the data entity itself has its configuration key disabled, a warning message is shown informing that the tables and fields in the target fields form for this entity will not be available at all regardless of their configuration key status.

### Child entities
Certain entities have another entity(s) as data sources. The child entities form in such cases or in the case of composite entities, shows the configuration key information. Use this form in the similar way to the entities list page described above. The target fields form for the child entity also behaves like what is described above.

### Using data entities
After understanding the full impact, if any, of configuration keys on the data entities that you would like to use, you can now proceed to using the entities by adding to the data projects. You will now know which fields are going to be available for use and hence can create the mappings accordingly.

### Run time validations for configuration keys
Using the configuration key metadata built during entity refresh list, run time validations are performed in the following use cases.
•	When a data entity is added to a job 
•	When user clicks ‘validate’ on the entity list 
•	When the user loads a data package into a data project
•	When the user loads a template into a data project
•	Before the export/import job is executed (batch, non-batch, recurring, Odata) 
•	When the user generates mapping 
•	When the user maps fields in the mapping UI 
•	When the user adds only 'importable fields'

### Guidance on managing configuration key changes in data management
Any time configuration keys are updated at the entity, table or field level, the entity list in data management must be refreshed. This process will ensure that, data management picks up the latest configuration key settings. Until the entity list is refreshed, the following warning will be shown in the entity list page. The updated configuration key changes will take effect immediately after the entity list is refreshed. It is recommended to validate existing data projects and jobs to make sure they will function as expected after the configuration keys changes were put in effect.



