---
# required metadata

title: Process enrollment eligibility
description: This article explains how to run the enrollment eligibility process.
author: ramagadu 
ms.date: 04/25/2025
ms.topic: how-to
# optional metadata

ms.search.form: BenefitWorkspace, HcmBenefitSummaryPart
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anisagrawal
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Process enrollment eligibility

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article explains how to run the enrollment eligibility process.

1. In the **Benefits management** workspace, under **Processing**, select **Enrollment eligibility processing**.
2. In the **Run benefit enrollment eligibility process** dialog, specify values for the following fields:

   | Field | Description |
   | --- | --- |
   | **Enrollment period** | The enrollment period to process enrollment eligibility for. |
   | **Legal entity** | The legal entity to process enrollment eligibility for. |
   | **Worker** | The worker to process enrollment eligibility for. If you leave this field blank, enrollment eligibility is processed for all workers. |
   | **Benefit plan** | The benefit plan to process enrollment eligibility for. |
   | **From** | The date from which records are included in the processing. This date is based on the employee's start date. |
   | **To** | The date until which records are included in the processing. This date is based on the employee's start date. |

3. If you want to run the process in the background, select **Run in the background** and do the following tasks:

   1. Enter information for the process.
   2. To set up a recurring job, select **Recurrence**, enter the recurrence information, and the select **OK**.
   3. To set up a job alert, select **Alerts**, select the alerts to receive, and then select **OK**.
   4. Select **OK**. The process runs with the parameters you set.

4. Select **OK**.

## View Process Results

This article explains how to view eligibility process results.

1. In the **Benefits management** workspace, under **Processing**, select **Process results**.
2. In the **Process results** page, the following fields are specified:

   | Field | Description |
   | --- | --- |
   | **Process ID** | The unique ID for the combination of Worker, Legal entity, and process run. |
   | **Process type** | This field identifies the process that was run. For example: Enrollment. |
   | **Time stamp** | The time that the eligibility process was run. |
   | **Legal entity** | The legal entity specified during the enrollment process. |
   | **Worker** | The worker who was processed. |
   | **Plan** | The Benefit plan that enrollment was attempted for. |
   | **Eligibility rule** | The eligibility rule that was processed. If an error was encountered before eligibility was run, this field is blank. For example: If compensation wasn't defined for a worker, the eligibility process doesn't run, and this field remains blank. |
   | **Result status** | The possible values are **Eligible** and **Ineligible**. The result status is **Ineligible** if the worker didn't meet the eligibility rule criteria, if the worker is missing required information such as a pay frequency or fixed compensation, or if there is information missing on the benefit plan that prevents workers from being enrolled. |
   | **Result message** | Indicates why a worker is ineligible for a benefit plan or if the eligibility rule passed. |

## Clean up benefits eligibility process results (preview)

> [!NOTE]
> This feature is currently in preview. The functionality and behavior that are described might change before general availability (GA).
>
> [This is prerelease documentation and is subject to change.]

In Dynamics 365 Human Resources, you can now clean up old benefits eligibility process results to help maintain system performance.

Over time, the benefits eligibility process result table can become large and cause database time-outs. HR administrators can use this new feature to delete old records, based on a specified retention period.

Before you can use this feature, the **Benefits management** feature must be enabled.

You can access the **Clean up benefits eligibility process results** feature from the following places:

- **Human Resources** \> **Benefits management** \> **Processing** \> **Clean up benefits eligibility process results**
- **Benefits management** \> **Processing** \> **Clean up benefits eligibility process results**
- **Workspaces** \> **Benefits management** \> **Links** \> **Processing**

When you run the cleanup, consider the following information:

- Enter the maximum age (in days). Records that are older than the maximum age are deleted.
- You can run the cleanup immediately or schedule it as a batch job.

The cleanup is specific to the legal entity.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
