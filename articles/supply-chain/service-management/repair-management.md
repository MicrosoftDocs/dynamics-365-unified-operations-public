---
title: Repair management
description: Group problems systematically to help with the suggestion of solutions that have been successful in the past. Learn about repair management.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: SMAConditionTable, SMASymptomArea, SMADiagnosisArea, SMAResolutionTable, SMARepairStage
ms.topic: how-to
ms.date: 08/26/2024
ms.custom: 
  - bap-template
  - evergreen
---

# Repair management

[!include [banner](../includes/banner.md)]

For repair management you can group problems systematically. This is to help with the suggestion of solutions that have been successful in the past.

You set up symptoms, diagnosis, and resolution settings. All these can later be applied when you receive a similar item for repair. You can also set up repair stages that can follow the progress of a repair issue.

## Setting up repair management

Use the following setup pages to enter information that will be used to specify the symptoms, the diagnosis, and the resolution, of the repair.

- **Service management** \> **Setup** \> **Repair** \> **Conditions**.
- **Service management** \> **Setup** \> **Repair** \> **Symptom areas**.
- **Service management** \> **Setup** \> **Repair** \> **Diagnosis areas**.
- **Service management** \> **Setup** \> **Repair** \> **Resolutions**.
- **Service management** \> **Setup** \> **Repair** \> **Repair stages**.

## Symptoms and conditions

Symptoms are how the customer characterizes the problem. Symptoms include the customer observations that indicate the need for repair.

You can set up symptom areas, symptom codes, and conditions. The symptom area covers the area of malfunction, and the symptom code covers the malfunction symptom. The condition describes the situation or environment that is present when the problem occurs.

### Example

A computer is brought in for repair because the hard drive fails after an extended period of use. The hard drive failure causes a blue screen error. The technician who receives the computer enters the following symptoms and conditions:

- The symptom area is the hard drive.
- The symptom code is the blue screen error.
- The condition is that the hard drive fails after extended use.

## Diagnosis and resolutions

The diagnosis and resolution fields are statements from the repair perspective. These are the steps that a technician went through to investigate the problem.

The diagnosis area covers the operation that must occur to solve the issue. The diagnosis code is how the problem was handled, and the resolution could be that the item was repaired, replaced, or the order was canceled by the customer. For example, if the computer is repaired, the diagnosis area could be *defective part*, the diagnosis code could be *new video card installed*, and the resolution could be *replaced*.

## Repair stages

Repair stages state the progress of the repair process. The repair stage has a **Finished** sign-off parameter that indicates that the repair line has been completed, and the finishing date and time has been recorded.

## Applying repair management

To apply repair management to an item, the item must be set up with a service object relation on a service order. From the service order you can then create a repair line with information about the current issue. On the repair line you define the service object that is in repair and information about symptoms, diagnosis, and execution. You can also create a note for the repair line.

You can create repair lines for each step in the repair process.

## Create a repair line on a service order

1. Go to **Service management** \> **Service orders** \> **Service orders**.
1. Select the service order with the service object that needs repair.
1. Select **Repair** \> **Repair lines** to open the **Repair lines** page.
1. Select **New** to create a new line.
1. Select a service object. You can select any service object that has been set up with an object relation on the service order.
1. Select any of the preset symptoms, diagnosis, and execution values that are relevant in the repair line and then select the **Note** tab to create a note on the repair line, if needed.
1. Select **Save** to save the new repair line. The **Created date and time** field in the **General** tab of the **Repair lines** page is updated with the time of saving.

## Tracking progress and resolving a repair issue

You can set the repair stages of a repair line to track the progress of the repair.

When a repair issue is resolved, you can close the repair line. Set the repair stage to a stage with a **Finished** property enabled. The current date and time is registered as the finish time on the line.

## Close a repair line for a resolved issue

1. Open the **Repair lines** page. Follow the procedure earlier in this article to create a repair line.
1. Select the repair line with the repair issue that you want to close.
1. In the **Repair stage** field, select a stage with the **Finished** property enabled.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
