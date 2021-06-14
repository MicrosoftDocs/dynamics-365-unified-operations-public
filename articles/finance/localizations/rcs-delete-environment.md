---
# required metadata

title: Regulatory Configuration Service - Delete an RCS Environment
description: This topic explains how an RCS System administrator can delete the RCS environment and related data.
author: JaneA07
ms.date: 06/14/2021
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
# Regulatory Configuration Service (RCS) - Delete an RCS environment 

[!include [banner](../includes/banner.md)]

This topic explains how a RCS System administrator can delete the RCS environment and any related data. 

Before you can complete those procedures, the following prerequisites must be met:

   - You must be the **System Admin** for the RCS environment.
   - The **System Admin** role must have the **‘RCSDeleteEnvironmentDuty’** role assigned.

## Delete an RCS environment

1. Go to RCS and select the **Electronic reporting** workspace tile.
2. Under **Related links**, select **Delete RCS environment**.

  ![Delete RCS environment in related links](media/01_RCS-Delete-Environ-Related-Link.PNG)  
  
3. In the panel that opens, review the messages regarding scope of deleting the environment.
  
  ![Delete RCS environment message](media/01_RCS-Delete-Environ-Msg_noGUID.PNG)
  
> [!IMPORTANT]
> Deleting your RCS Environment can't be reversed. 
> This will delete the selected RCS environment, and any related data including features and configurations stored in the Global repository. Features and configuration shared with other organizations will be unshared and deleted if they have no dependencies. Features and configurations with dependencies will be marked as discontinued.

4. Type the RCS environment GUID in the field provided to confirm that you want to delete your environment. The environment GUID is included in the deletion message. 
5. Select **Delete environment**.
	
Your RCS environment and any related data is now deleted.

> [!IMPORTANT]
> After you delete the RCS environment, there is no way to recover the data. A new RCS environment can be created in any available RCS region.


