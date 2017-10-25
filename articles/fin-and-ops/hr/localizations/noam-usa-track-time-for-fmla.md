---
# required metadata

title: Track time off for FMLA
description: This topic explains how to track Family and Medical Leave Act (FMLA) eligibility and hours that are worked to meet federal requirements.
author: ShielaSogge
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

This topic explains how to track Family and Medical Leave Act (FMLA) eligibility and hours that are worked to meet federal requirements.

## Prerequisites

The following table shows the prerequisites must be in place before you start.

> [!NOTE]
> The cases and payroll features are available only in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition.

| Category                  | Prerequisite |
|---------------------------|--------------|
| Task                      | Verify that the settings on the **Human resources parameters** and **Case category type security** pages are accurate. |
| Knowledge and experience  | Be familiar with cases and how they work. |
| Planning                  | Determine whether you will integrate FMLA with Payroll. |
| Country/region            | (USA) The primary address for the legal entity must be in the United States. |

## Determine work eligibility

When a worker submits a leave request, or inquires about his or her FMLA eligibility, you can easily determine how many available hours the worker has. To determine worker eligibility, follow these steps.

1. On the **Workers** page, select the worker to determine eligibility for, and then click **Employment** \> **FMLA** \> **FMLA eligibility**.
2. In the **Effective date** field, enter the date when you expect eligibility to begin.
3. Click **Calculate**. The estimated number of available hours for both standard FMLA and military FMLA is shown. This number is determined by the number of hours that the employee has worked, the length of his or her employment, and whether the employee has taken any leave that reduces his or her remaining hours.

## Create an FMLA case

FMLA uses cases to track eligibility and hours that have been taken.

> [!NOTE]
> Before you create an FMLA case, make sure that you have created the employment leave.

This step is required for all leaves of absence, regardless of whether the leave qualifies for FMLA.

To create an FMLA case, follow these steps.

1. On the **FMLA cases** page, on the **Action Pane**, in the **New** group, click **Case**.
2. Optional: If the case has already been approved, on the **General** tab, select the **Approved** check box. You can also select the approver.
3. Enter the following information.

    | Field                    | Description |
    |--------------------------|-------------|
    | Reason                   | Select the reason for the leave. |
    | Leave request date       | Select the date when the leave was requested. This date is often the current date. |
    | Leave start date         | Select the first day of the leave. If this information changes, you can return to this page and update the value. |
    | Estimated leave end date | Select the last day that the worker intends to remain on leave. If this information changes, you can return to this page and update the value. |
    | Approved hours           | Enter the number of hours that have been approved for the leave. The **Eligibility** section of the page should help you determine this value. |
    | Leave schedule           | Select the leave schedule. |

4. Optional: On the **Certifications** FastTab, enter any certification information to track.
5. On the **Associated leave** FastTab, click **Add**. Select the employment leave that corresponds to this FMLA case.
6. Optional: On the **Case log** FastTab, enter any notes about the case that you want to store for reference purposes.

## Recalculate FMLA eligibility (if required)

After you create an FMLA case for a worker, you can recalculate the worker’s eligibility at any time. To recalculate a worker’s eligibility, follow these steps.

1. On the **FMLA cases** page, open the case to log hours for.
3. On the **Action Pane**, in the **Maintain** group, click **Recalculate FMLA eligibility**.
4. Select the fields that should be updated based on the worker's current information. 
5. Click **Recalculate**.

## Enter FMLA hours that have been taken (if required)

After an FMLA case is approved, you can change and track the number of hours that the worker applies to his or her FMLA leave. To enter FMLA hours that have been taken, follow these steps.

1. On the **FMLA cases** page, open the case to log hours for.
2. On the **Action Pane**, in the **Maintain** group, click **FMLA hours**.
3. Click **Add line**, and enter the earning date, the number of hours that have been taken, and any applicable notes.

> [!NOTE]
> The **Source** column is always set to **Manual**. If you’re using Finance and Operations and Payroll, the **Source** column can be updated automatically, based on the earning code that is used on the employee’s pay statement.

## Set up Payroll for integration with FMLA (if required)

If you use Finance and Operations and Payroll, you can use earning codes to automatically track the hours that have been worked that count toward FMLA. When earning lines that contain these codes are released during the approved leave period for a worker, the time counts toward FMLA and is added to the **FMLA hours** page for the FMLA case.

> [!TIP]
> If you use this method to track FMLA hours, you can still change the hours manually after they are created.

To integrate Payroll with FMLA, follow these steps.

1. On the **Earning codes** page, open an earning code that reduces the number of FMLA hours that are available for a worker when hours are logged for that worker.
2. Select the **Reduce remaining FMLA time** check box.

    > [!NOTE]
    > You can select this check box only if the **Productive** check box is cleared and the **Unit of measure** field is set to **Hours**.

## Optional: Generate the FMLA hours taken report

You can create a report of all workers who have FMLA cases and the hours that have been applied toward each case. This report is available only in Finance and Operations. To generate the **FMLA leave taken** report, follow these steps.

1. On the **FMLA leave taken** page, enter the first and last day of the leave period to view.
2. Click **OK**.
