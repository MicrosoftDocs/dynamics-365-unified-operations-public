--- 
title: Configure financial cross-company data sharing
description: Learn about how to configure, enable, validate, and resolve conflicts when sharing data between companies, including a step-by-step process. 
author: aprilolson
ms.author: aolson
ms.topic: how-to
ms.date: 03/10/2026
ms.custom:
ms.reviewer: johnmichalak 
audience: Application User 
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: DataManagementWorkspace, DMFQuickImportExportRnr, DMFExecutionHistoryWorkspace, DMFExecutionHistorySummary, DMFExecutionHistoryEntities,  SysDataSharingConfiguration, SysDataSharingDiscrepencies  
ms.dyn365.ops.version: Version 7.0.0 
---

# Configure financial cross-company data sharing

[!include [banner](../../../finance/includes/banner.md)]

This procedure shows how to configure, enable, validate, and resolve conflicts when sharing data between companies. It uses the USMF company and the Financial data sharing template.

This task guide requires Dynamics AX platform 7.1 or later.

1. Go to **Navigation pane > Modules > System administration > Workspaces > Data management**.
1. Select **Import**.
1. In the **Name** field, enter a value.
1. In the **Source data format** field, select the **Package** type. Select **Upload**. Go to the location of the Financial data sharing template package file and select that file.
1. Select **Save**.
1. In the list, select the row. Select the data sharing policy that you created.  
1. Select **Import**.
1. Select **Close**.
1. Refresh the page.
1. Close the page.
1. Close the page.
1. Close the page.
1. Go to **Navigation pane > Modules > System administration > Setup > Configure cross-company data sharing**.
1. In the list, find and select **Payment days**.
1. Select **Add**.
1. In the list, select the row.
1. In the **Company** field, enter **USSI**.
1. Select **Add**.
1. In the **Company** field, enter **USMF**.
1. Select **Save**.
1. Select **Enable**.
1. Select **Yes**.
1. Select **Find sharing issues**.
1. Select **Yes**.
1. Select **Update field value**.
1. Select **Use value from company 1**.
1. Refresh the page.
1. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]