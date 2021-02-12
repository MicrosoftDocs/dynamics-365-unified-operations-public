---
# required metadata

title: RCS discontinuing configuration in RCS/Global repository
description: This topic describes how to discontinue configuration in the RCS Global repository.
author: JaneA07      
manager: AnnBe
ms.date: 02/04/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: ERSolutionTable, ERWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 97423
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: janeaug
ms.search.validFrom: 2021-02-02
ms.dyn365.ops.version: AX 10.0.14

---
# RCS discontinuing configuration in RCS/Global repository

[!include [banner](../includes/banner.md)]

This topic describes how to discontinue configuration in the RCS Global repository. Previously is was possible only to delete configurations that were no longer required. However now, you can mark a released configuration as **Discontinued** in the RCS Global repository and then:
 
 - Provide upfront notifications when a configuration is planned to be discontinued.
 - Include applicable details about the replacement configuration.
 - Set a **Supported until** date for the specific configuration to inform the user when it will be discontinued.
 
![image.png](media/Discontinue_version_1.png)

You can discontinue a configuration version and specify the following discontinuation information. Note that all fields are optional.
  - Replacement configuration
  - Replacement configuration version
  - Free text note - this field should be used to convey additional documentation links or references
  - 'Supported until' - provides the proposed date up to which the current configuration/version will be supported to. Note that this date is not updated automatically, so if used, will need to be maintained manually.
  
- To discontinue the configuration, you need to:
  - Select whether you want to discontinue a single version or if you want to discontinue all versions with the same settings in one operation slide 'All versions' parameter to 'Yes' 
  - Slide Discontinue' parameter to 'Yes'.
  - Click 'Ok' to discontinue the configuration(s). Note Discontinued date will be populated on save, when the discontinue parameter is 'Yes'.
  
- You can revert configuration back to Shared or adjust discontinuation info at anytime.
- You can keep configuration Shared, but specify 'Supported until' (and all other discontinuation info) to indicate your plans to discontinue the configuration in future.

> [!NOTE]
> Discontinuation does not limit any operations with configurations for customers, they still can import, run or derive them, it's just informational fields.

## Discontinuation details page

![image.png](articles/finance/localizations/media/Discontinue_details_2.png)

## F&O supports displaying this information starting from 10.0.14

- On the Global repository form:
  - User will see the up to date information related to discontinuation.
  - By default, configurations that are discontinued will be filtered out.
  
- On imported Configurations form (ERSolutionTable)
  - For the configurations that were already discontinued when there were imported.
  - For configurations that were discontinued after they were imported - discontinuation info can be synchronized by running "Import configurations updates" job.


