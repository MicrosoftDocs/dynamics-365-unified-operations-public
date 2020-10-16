---
# required metadata

title: Eliminate a project estimate
description: This topic provides information about eliminating a project estimate after it is complete. 
author: kfend
manager: AnnBe
ms.date: 05/26/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Service industries
ms.author: roschlom
ms.dyn365.ops.version: 7.0
ms.search.validFrom: 2019-01-15
---
# Eliminate a project estimate

[!include [banner](../includes/banner.md)]

Project estimates provide the financial view for work that is estimated and scheduled for a project. To work with estimates for a project, you must attach the project to an estimate project. An estimate project is always based on an existing project, however multiple projects can refer to a single estimate project. Only fixed-price and investment projects can be attached to estimate projects, and those projects must belong to the same project group as the estimate project.

To eliminate an estimate project, it must be complete. The following steps explain how to eliminate an estimate.

1. Go to **Project management and accounting** > **All Projects** and open the project. 
2. On the **Manage** tab, select **Estimates**, and on the **Estimate** page select **Eliminate**.
3. On the **Eliminate estimate** page on the **General** tab, set the following options:

   - **Period code**: Select the period code to choose the appropriate estimate projects. 
   - **Estimate date**: Select the appropriate estimate date for elimination.
   - **Eliminate with WIP warnings**: Enable this option to provide notification when an estimate that is associated with a work in progress (WIP) will be eliminated. When this option is not enabled, elimination can’t continue if any non-estimated transactions exist. 
   > [!NOTE]
   > This option is available only when elimination is applied to an estimate project. It is not available if you are using periodic postings. This setting works with the settings on the **Estimate** tab on the **Project parameters** page, in the **Allow elimination when non-estimated transactions exist** field group.
   - **Set stage to Finished**: Enable this option to set the estimate project’s stage to **Finished** after you run the elimination.
   - **Print estimate list**: Select the information to be included when the estimate list is printed.
   - **Show Infolog**: Enable this option to display the Infolog.
   - **Posting date**: Choose the ledger posting date of the estimate.

4.  Select **OK**.
5. After the elimination process is complete, the eliminated estimate project is displayed with a negative value. 

If you did not intend to eliminate an estimate, you can select the eliminated estimate and select **Reverse elimination**.   
