---
# required metadata

title: Discontinue configurations in RCS/Global repository
description: This topic describes how to discontinue configurations in the RCS Global repository.
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
# Discontinue configurations in RCS/Global repository

[!include [banner](../includes/banner.md)]

This topic describes how to discontinue configuration in the RCS Global repository. Previously is was possible only to delete configurations that were no longer required. However now, you can mark a released configuration as **Discontinued** in the RCS Global repository and:
 
 - Provide upfront notifications when a configuration is planned to be discontinued.
 - Include applicable details about the replacement configuration.
 - Set a **Supported until** date for the specific configuration to inform the user when it will be discontinued.

When you discontinue a configuration version, you have the option to specify the following information:

  - **Replacement configuration**
  - **Replacement configuration version**
  - **Free text note**: Use this field to provide documentation links or references
  - **Supported until**: This field provides the proposed date up to which the current configuration/version will be supported. This date must be udpated manually.
  
To discontinue the configuration,complete the following steps. 

1. Select whether you want to discontinue a single version or all versions with the same settings in one operation by setting **All versions** to **Yes**. 
2. Slide the **Discontinue** parameter to **Yes**.
3. Select **OK** to discontinue the configurations. The **Discontinued date** field will be populated when you save the changes.
  
You can revert configuration back to **Shared** or adjust discontinuation information at any time. If you share a configuration, specify the **Supported until** date and all other information related to the discontinuation to indicate your plans for future discontinuation.

> [!NOTE]
> Discontinuation doesn't limit operations with configurations. You can continue to import, run, or derive the configurations, it's just informational fields.

## Finance supports displaying this information starting in version 10.0.14

On the **Global repository** page you can view up-to-date information related to discontinuation. By default, configurations that are discontinued are filtered out.
  
The **Imported configurations** (ERSolutionTable) page, shows configurations that were already discontinued when there were imported. For those configurations that were discontinued after import, the discontinuation information can be synchronized by running the **Import configurations updates** job.


