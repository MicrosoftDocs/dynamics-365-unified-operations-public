--- 
title: Set up security governance parameters
description: This article describes how to set up various parameters to be utilized for security governance module.
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

# Set up security governance parameters

[!include [banner](../includes/banner.md)]

This article explains how to set up multiple parameters related to security governance module. These parameters are useful for utilizing licensing reports and user aging reports. 


## Basic license cost
1. Go to **System administration** > **Security governance setup** > **Parameters**.
2. Expand the **Basic license cost** section.
3. Click **New**.
4. In the **Basic user license** field, select the user license.
5. In the **Price** field, enter the manual price of the license.
    
Using the same steps, set up the manual price for all desired user licenses.

6. To exclude user accounts from the license price calculation on the **Licenses usage summary** report, go to the **Exclude** section and select **Group**.
7. To exclude all system administrators from the license price calculation on the **Licenses usage summary** report, select **Yes** or **No** for the **System administrator** option.


## General
1. Go to **System administration** > **Security governance setup** > **Parameters**.
2. Expand the **General** section.
3. To enable or disable the similarity check of duties in the **Segregation of duties validation** feature, in the **Check similarity** field, select **Yes** or **No**.
4. In the **Level for similarity validation** field, enter the level Tf similarity validation for the **Segregation of duties validation** feature. This determines how much similarity is allowed between duties before a conflict is detected.
5. In the **Allow unpublished objects** field, select **Yes** or **No** to allow or disallow the unpublished objects in **Security configuration**.  
 
## User aging periods
1. Go to **System administration** > **Security governance setup** > **Parameters**.
2. Expand the **User aging periods** section.
3. In the **Period 1** field, enter the number of days to use for **User activity aging** report.
 
Using the same steps, set up the number of days for the other four periods.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
