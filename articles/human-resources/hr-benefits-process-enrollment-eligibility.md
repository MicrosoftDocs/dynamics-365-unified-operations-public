---
# required metadata

title: Process enrollment eligibility
description: This article explains how to run the enrollment eligibility process.
author: andreabichsel
manager: AnnBe
ms.date: 02/03/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-human-resources
ms.technology: 

# optional metadata

ms.search.form: BenefitWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Process enrollment eligibility

[!include [banner](includes/preview-feature.md)]

This article explains how to run the enrollment eligibility process.

1. In the **Benefits management** workspace, under **Processing**, select **Enrollment eligibility processing**.

2. In the **Run benefit enrollment eligibility process** dialog box, specify values for the following fields:

   | Field | Description |
   | --- | --- |
   | Enrollment period | The enrollment period to process enrollment eligibility for. |
   | Legal entity | The legal entity to process enrollment eligibility for. |
   | Worker | The worker to process enrollment eligibility for. If you leave this field blank, enrollment eligibility will be processed for all workers. |
   | Benefit plan | The benefit plan to process enrollment eligibility for.

3. If you want to run the process in the background, select **Run in the background** and do the following tasks:

   1. Enter information for the process.

   2. To set up a recurring job, select **Recurrence**, enter the recurrence information, and the select **OK**.

   3. To set up a job alert, select **Alerts**, select the alerts to receive, and then select **OK**.

   4. Select **OK**. The process will run with the parameters you set.

4. Select **OK**.
