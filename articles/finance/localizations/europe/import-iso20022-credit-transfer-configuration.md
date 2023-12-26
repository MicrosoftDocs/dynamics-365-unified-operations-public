--- 
# required metadata 
 
title: Import ISO20022 credit transfer configuration
description: This article explains how to import a vendor payment electronic reporting configuration. 
author: mrolecki
ms.date: 08/01/2023
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: ERWorkspace, ERVendorPart, ERSolutionRepositoryTable, ERSolutionImport   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: mrolecki
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Import ISO20022 credit transfer configuration

[!include [banner](../../includes/banner.md)]

Complete the steps in this article to import a vendor payment electronic reporting configuration. The German ISO 20022 credit transfer format is used as an example. These steps can be used for other available electronic reporting formats. This article was created using the demo data company DEMF but you can use any demo data company to complete this task.

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
2. In the list of available configuration providers, select **Microsoft**.
3. Select **Set active**.
4. Select **Repositories** > **Open**.
5. Select **Show filters**.
6. Apply the following filters: In the **Configuration name** field, enter a filter value of **"ISO20022 Credit transfer (DE)"** using the **"begins with"** filter operator. Alternatively, you can find the configuration in the list, select it, and then move it to the **Import** task.  
7. Select **Import**.

   > [!NOTE]
   > If the **Import** button isn't available, the configuration has already been imported.
   
8. Select **Yes**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
