---
# required metadata

title: Regulatory Configuration Service - Delete RCS Environment
description: This topic explains how the RCS System Administrator can delete their RCS environment and related data.
author: JaneA07
ms.date: 06/09/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: RCS, Regulatory Configuration Services, Localization, Global
# ROBOTS: 
audience: Application User, System Admin
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 97423
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: janeaug
ms.search.validFrom: 2021-01-01
ms.dyn365.ops.version: AX 10.0.15

---
# Regulatory Configuration Service (RCS) - Delete environment & related data

[!include [banner](../includes/banner.md)]

The following procedure explains how the RCS System Administrator can delete their RCS environment and related data. 
Before you can complete those procedures, you must complete the following prerequisites:
-	To be able to delete the RCS environment the user needs to be the **System Admin** for that RCS environment.
-	**System Admin** needs to have the **‘RCSDeleteEnvironmentDuty’** role assigned.

# Delete RCS environment
-	Go to **RCS homepage**
-	Click on **Electronic reporting** workspace tile.
-	Under **Related links** click on **Delete RCS environment** link: 

  ![Delete RCS environment in related links](media/01_RCS-Delete-Environ-Related-Link.PNG)  
  
-	Opens right hand panel **Delete RCS environment**
-	Review the associated deletion messages regarding scope of deletion:
  
  ![Delete RCS environment message](media/01_RCS-Delete-Environ-Msg_noGUID.PNG)
  
> [!NOTE]
> Deleting your RCS Environment is irreversible.
> This will delete the selected RCS environment, and related data including features and configurations stored in Global repository. Features and configuration shared with other organizations will be unshared and deleted if they have no dependencies. Feature and configurations with dependencies will be marked are discontinued.

-	To confirm delete type the RCS environment `GUID` for your environment in the field provided. (Note - The environment `GUID` is included in the body of the deletion message.)
-	After you enter the `GUID` the **Delete environment** button becomes active:

![Delete options](media/01_RCS-Delete-Environ-Msg-Options.PNG)

-	Click **Delete environment**.
	
Your RCS Environment & related data is now deleted.

> [!NOTE]
> After RCS environment deletion there is no ability to recover data. A new RCS environment can be created in any available RCS region.


