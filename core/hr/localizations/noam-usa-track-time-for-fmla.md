---
# required metadata

title: Comply with the Americans with Disabilities Act
description: This article describes features that can assist your organization in complying with the Americans with Disabilities Act (ADA). This information applies only to legal entities doing business in the United States.
author: shielas
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: rschloma
ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 2741
ms.assetid: 42504e87-7cb1-42e0-8a8b-9bc91fb54095
ms.search.region: USA
# ms.search.industry: 
ms.author: shielas
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Track time off for FMLA

[!include[banner](../../includes/banner.md)]


This topic describes how to track Family and Medical Leave Act (FMLA)
eligibility and hours worked to meet federal requirements.

## Prerequisites

The following prerequisites must be in place before you start.

| Category                                  | Prerequisite                                                                                                   |
|-------------------------------------------|----------------------------------------------------------------------------------------------------------------|
                     |
| Task                                      | Verify that the settings are accurate on the Human resources parameters and Case category type security pages. |
| Knowledge and experience   | Be familiar with cases and how they work. |                                                               | Planning       | Determine whether you will integrate FMLA with Payroll.         |

| Country/region  | (USA) The primary address for the legal entity must be in the following countries/regions: United States.      |

## 1. Determine work eligibility

When a worker submits a leave request or inquiries about their FMLA
eligibility, you can easily determine how many hours they have a available.
To determine worker eligibility, complete the following steps.

1. Open the **Workers** page.

2. Select the worker to determine eligibility for, and then select **Employment** \> **FMLA**> **eligibility**.

3. In the **Eligibility date** field, enter the date you expect eligibility to begin.

4. Click **Calculate**. The number of estimated available hours for both standard FMLA and military FMLA is displayed. This number is determined by the number of hours the employee has worked, their length of employment, and whether the worker has taken any leave that reduces their remaining hours.

## 2 Create an FMLA case

FMLA uses cases to track eligibility and hours taken.

> [!NOTE]
> Before you create an FMLA case, create the employment leave, if you haven’t already done so.

This is required for all leaves of absence, regardless of whether the leave qualifies for FMLA.

To create an FMLA case, follow these steps:

> 1. Open the **FMLA cases** page.

> 2. On the **Action Pane**, in the **New** group, click **Case**.

> 3. Optional: If the case has already been approved, select the **Approved**
> check box on the **General** tab. You can also select the approver, if applicable.

>  4. Enter the following information.

| Field                    | Description                                                                                                                       |
|--------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| Reason                   | Select the reason for the leave.                                                                                                  |
| Leave request date       | Select the deate when the leave was requested. This is often today’s date.                                                        |
| Leave start date         | Select the first day of the leave. If this changes, you can return to this page and update the date.                              |
| Estimated leave end date | Select the last day that the worker intends to remain on leave. If this changes, you can return to this form and update the date. |
| Approved hours           | Enter the approved hours for the leave. The Eligibility section of the page should help you determine this number.                |
| Leave schedule           | Select the leave schedule.                 |


5. Optional: On the **Certifications** FastTab, enter any certification information to track.

6. On the **Associated leave** FastTab, click **Add**. Select the employment leave that corresponds to this FMLA case.

7. Optional: On the **Case log** FastTab, enter any notes about the case that you want to store for reference purposes.

 ## 3. If required: Recalculate FMLA eligibility

After you create an FMLA case for a worker, you can recalculate the worker’s eligibility at any time. To recalculate a worker’s eligibility, follow these steps.

1. Open the **FMLA cases** page.

2. Open the case to log hours for.

3. On the **Action Pane**, in the Maintain group, click FMLA hours.

4. Click **Add line** and enter the earning date, hours taken, and any applicable notes.

## 4. If required: Enter FMLA hours taken

>   After an FMLA clase is approved, you can change and track the number of hours workers apply toward their FMLA leave. To enter FMLA hours that have been taken, follow these steps:

1. Open the FMLA cases page.

2. Open the case to log hours for.

3. On the **Action Pane**, in the **Maintain** group, click **FMLA hours**.

4. Click **Add line** and enter the earning date, hours taken, and any applicable notes.

> [!NOTE]
>   The source column is always set to **Manual** unless FMLA is integrated with Microsoft Dynamics AX and the line was created by the system.

## 5. If required: Set up Payroll to integrate with FMLA

If you use Payroll, you can use earning codes to automatically track the hours worked that count toward FMLA. When earning lines that contain these codes are released during the approved leav period for a worker, the time counts toward **FMLA** and is added to the FMLA hours form for the FMLA case.

> [!TIP]
> If you use this method of tracking FMLA hours, you can still change the hours manually after they are created.

To integrate Payroll with FMLA, complete the following steps.

1. Open the **Earning codes** page.

2. Open an earning code that, when hours are logged for a worker, reduces the number of FMLA hours available for the worker.

3. On the **General** tab, select a value in the **Reduce remaining FMLA** time field.

> [!NOTE]
> You can select this check box only if the **Productive** check box isn’t selected and the **Unit of measure** is set to **Hours**.

## Optional: Generate the FMLA hours taken report

You can create a report of all workers who have FMLA cases and the hours that have been applied toward each case. To generate the FMLA leave taken report, follow these steps:

1. Open the **FMLA leave taken** page.

2. Enter the first and last day of the leave period that you want to view.

3. Click **OK**.
