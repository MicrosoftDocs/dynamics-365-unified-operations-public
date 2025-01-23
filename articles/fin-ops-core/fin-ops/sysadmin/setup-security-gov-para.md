--- 
title: Set up security governance parameters
description: Learn how to set up various parameters for the security governance module.
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
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

This article explains how to set up various parameters that are related to the security governance feature. These parameters are useful for licensing reports and user aging reports.

## Basic license cost

1. Go to **System administration** \> **Security governance setup** \> **Parameters**.
1. Expand the **Basic license cost** section.
1. Select **New**.
1. In the **Basic user license** field, select the user license.
1. In the **Price** field, enter the manual price of the license.
1. Repeat steps 3 through 5 to set up the manual price for other user licenses.
1. To exclude user accounts from the license price calculation on the **Licenses usage summary** report, in the **Exclude** section, select **Group**.
1. To exclude all system administrators from the license price calculation on the **Licenses usage summary** report, set the **System administrator** option to **Yes**.

## General

1. Go to **System administration** \> **Security governance setup** \> **Parameters**.
1. Expand the **General** section.
1. In the **Check similarity** field, select **Yes** to turn on the similarity check for duties in the **Segregation of duties validation** feature. Select **No** to turn off the similarity check.
1. In the **Level for similarity validation** field, enter the level of similarity validation that is done for the **Segregation of duties validation** feature. This field defines the amount of similarity that can exist between duties before a conflict is detected.
1. In the **Allow unpublished objects** field, select **Yes** to allow unpublished objects in **Security configuration** (**System administration** \> **Security** \> **Security configuration**). Select **No** to disallow unpublished objects.

## User aging periods

1. Go to **System administration** \> **Security governance setup** \> **Parameters**.
1. Expand the **User aging periods** section.
1. In the **Period 1** field, enter the number of days to use for the **User activity aging** report.
1. Repeat step 3 to set up the number of days for the other four periods.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
