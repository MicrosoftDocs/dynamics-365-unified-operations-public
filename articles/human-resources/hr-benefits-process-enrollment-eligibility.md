---
# required metadata

title: Process enrollment eligibility
description: This topic explains how to run the enrollment eligibility process.
author: twheeloc
ms.date: 08/23/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: BenefitWorkspace, HcmBenefitSummaryPart
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Process enrollment eligibility


[!INCLUDE [PEAP](../includes/peap-2.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic explains how to run the enrollment eligibility process.

1. In the **Benefits management** workspace, under **Processing**, select **Enrollment eligibility processing**.

2. In the **Run benefit enrollment eligibility process** dialog box, specify values for the following fields:

   | Field | Description |
   | --- | --- |
   | **Enrollment period** | The enrollment period to process enrollment eligibility for. |
   | **Legal entity** | The legal entity to process enrollment eligibility for. |
   | **Worker** | The worker to process enrollment eligibility for. If you leave this field blank, enrollment eligibility will be processed for all workers. |
   | **Benefit plan** | The benefit plan to process enrollment eligibility for.

3. If you want to run the process in the background, select **Run in the background** and do the following tasks:

   1. Enter information for the process.

   2. To set up a recurring job, select **Recurrence**, enter the recurrence information, and the select **OK**.

   3. To set up a job alert, select **Alerts**, select the alerts to receive, and then select **OK**.

   4. Select **OK**. The process will run with the parameters you set.

4. Select **OK**.

## View Process Results

This topic explains how to view eligibility process results.

1.	In the **Benefits management** workspace, under **Processing**, select **Process results**.

2.	In the **Process results** page, the following fields are specified:

   | Field | Description |
   | --- | --- |
   | **Process ID** | The unique ID for the combination of Worker, Legal entity, and process run. |
   | **Process type** | This identifies the process that was run. For example:  Enrollment. |
   | **Time stamp** | The time that the eligibility process was run. |
   | **Legal entity** | The legal entity specified during the enrollment process. |
   | **Worker** | The worker who was processed. |
   | **Plan | The Benefit plan that enrollment was attempted for. |
   | **Eligibility rule** | The eligibility rule that was processed. If an error was encountered before eligibility was run, this will be blank. For example: If compensation hasn't been defined for a worker, the eligibility process won't run, and this field will be left blank. |
   | **Result status** | This will be Eligible or Ineligible. The result status will be Ineligible if the worker didn’t meet the eligibility rule criteria, if the worker is missing required information such as a pay frequency or fixed compensation, or if there is information missing on the benefit plan that prevents workers from being enrolled. |
   | **Result message** | Indicates why a worker is ineligible for a benefit plan or if the eligibility rule passed. |



[!INCLUDE[footer-include](../includes/footer-banner.md)]
