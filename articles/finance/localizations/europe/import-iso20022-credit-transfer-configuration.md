--- 
title: Import ISO20022 credit transfer configuration
description: Learn how to import a vendor payment electronic reporting configuration with Microsoft Dynamics 365 Finance.
author: kailiang
ms.author: kailiang
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/27/2025
ms.reviewer: johnmichalak   
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: ERWorkspace, ERVendorPart, ERSolutionRepositoryTable, ERSolutionImport 
---

# Import ISO20022 credit transfer configuration

[!include [banner](../../includes/banner.md)]

This article explains how to import a vendor payment electronic reporting configuration with Microsoft Dynamics 365 Finance.

Complete the steps in the following procedure to import a vendor payment electronic reporting configuration. The German ISO 20022 credit transfer format is used as an example. These steps can be used for other available electronic reporting formats. 

The procedure was created using the demo data company DEMF, but you can use any demo data company.

1. In Dynamics 365 Finance, go to **Organization administration \> Workspaces \> Electronic reporting**.
1. In the list of available configuration providers, select **Microsoft**.
1. Select **Set active**.
1. Select **Repositories \> Open**.
1. Select **Show filters**.
1. In the **Configuration name** field, using the **"begins with"** filter operator, enter a filter value of "ISO20022 Credit transfer (DE)". Alternatively, you can find the configuration in the list, select it, and then move it to the **Import** task.  
1. Select **Import**.

   > [!NOTE]
   > If the **Import** button isn't available, the configuration has already been imported.
   
1. Select **Yes**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
