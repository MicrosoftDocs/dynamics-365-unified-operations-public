--- 
title: Setup security governance parameters
description: Learn about how to setup various parameters which can be utilized for security governance module.
author: saurabhgupta
ms.author: saurabhgupta
ms.topic: how-to
ms.date: 01/13/2025
ms.custom:
ms.reviewer: twheeloc     
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: SysSecRolesEditUsers, SysSecAssignmentQueryLookup, SysQueryForm, SysSecRoleExcludeUsers
ms.dyn365.ops.version: Version 7.0.0 
---

# Setup security governance parameters

[!include [banner](../../includes/banner.md)]

This article explains how to set up multiple parameters related to security governance module. These parameters are useful for utilizing licensing reports and user aging reports. 


## Basic license cost
1. Go to **System administration** > **Security governance setup** > **Parameters**.
2. Expand the **Basic license cost** section.
3. Click **New**.
4. In the **Basic user license** field, select the user license.
5. In the **Price** field, enter the manual price of the license.
    
Using the same steps, setup the manual price for all desired user licenses.

6. Select **Group** under **EXCLUDE** section to exclude user accounts from the license price calculation on the **Licenses usage summary** report.
7. Select **Yes** or **No** for the **System administrator** option to exclude all system administrators from the license price calculation on the **Licenses usage summary** report.


## General
1. Go to **System administration** > **Security governance setup** > **Parameters**.
2. Expand the **General** section.
3. Select **Yes** or **No** for the **Check similarity** option to enable or disable the similarity check of duties under the **Segregation of duties validation** feature.
4. In the **Level for similarity validation** field, enter the level of similarity validation for the **Segregation of duties validation** feature. It will determine how much similarity is allowed between duties before a conflict is detected.
5. Select **Yes** or **No** for the **Allow unpublished objects** field to allow or disallow the unpublished objects in **Security configuration**.  
 
## User aging periods
1. Go to **System administration** > **Security governance setup** > **Parameters**
2. Expand the **User aging periods** section.
3. In the **Period 1** field, enter the number of days you want to use for **User activity aging** report.
 
Using the same steps, setup the number of days you want to set for other four periods.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
