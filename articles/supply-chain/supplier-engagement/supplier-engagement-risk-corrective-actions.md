---
title: Risk management and corrective actions (preview)
description: Identify vendor risks, calculate risk levels, and track corrective actions in the Supplier Engagement app.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 07/27/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Risk management and corrective actions (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Supplier risk management helps organizations identify, assess, and mitigate risks that are associated with global vendors. The feature supports proactive monitoring by combining structured risk evaluations with corrective action tracking. It also preserves historical records so teams can review how risks were handled over time.

## Key capabilities

The Supplier Engagement app supports the following risk management capabilities:

- **Risk identification** – Select predefined risk scenarios.
- **Risk evaluation** – Assess likelihood and impact on a 1-to-5 scale.
- **Risk level calculation** – Automatically determine the overall risk level.
- **Corrective action tracking** – Define and monitor mitigation steps.
- **Historical risk records** – Keep prior evaluations and actions for reference.

## Prerequisites

Before you can create risk evaluations or corrective actions, complete the following configuration steps:

- **Risk scenarios** – Create and activate risk scenarios in **Configuration** > **Risks** > **Risk Scenarios**.
- **Corrective action types** – Configure corrective action types in **Configuration** > **Risks** > **Corrective Action Types**.

Learn more in [Configure risk management elements (preview)](configure-risk-management.md).

## Identify and evaluate risks

Create a risk evaluation when you need to document a vendor risk, score its severity, and capture the required mitigation details.

1. [Open the relevant global vendor record](supplier-engagement-global-vendor-info.md#open-a-global-vendor-record) and open the **Risks** tab.
1. On the command bar, select **Risk Evaluation**.
1. Fill out the dialog with the details of the risk and a possible corrective action.
1. Select **Save and close**.
1. The risk is now added to the **Active global vendor risks** list, where you and other users can review, open, and eventually delete it if appropriate.

The system calculates the **Risk number** by multiplying **Likelihood** by **Impact**, which produces a value from *1* to *25*. It then assigns a **Risk level** of *Low*, *Medium*, or *High* based on the most recent risk evaluation.

## Create corrective actions

Create a corrective action when a risk requires mitigation activities, ownership, and due date tracking.

1. [Open the relevant global vendor record](supplier-engagement-global-vendor-info.md#open-a-global-vendor-record) and open the **Risks** tab.
1. In the **Active corrective actions** section toolbar, select **New global vendor corrective action**.
1. Fill out the dialog with the details of the corrective action.
1. Select **Save and close**.

Corrective actions link to the related vendor and risk record so you can monitor mitigation work in context.

## Close or cancel corrective actions

Close a corrective action when the mitigation work is finished. Cancel it when the action is no longer required.

1. [Open the relevant global vendor record](supplier-engagement-global-vendor-info.md#open-a-global-vendor-record) and open the **Risks** tab.
1. In the **Active corrective actions** section, locate the corrective action row and select the **Go to record** button at the right side of the row.
1. In the **Measures Implemented** field, enter the actions that were taken to mitigate the risk.
1. On the command bar, select **Deactivate**.
1. In the **Confirm deactivation** dialog, select one of the following options from the **Status reason** drop-down list:
    - **Closed** – The corrective action was successfully implemented
    - **Cancelled** – The corrective action is no longer required

1. Select **Deactivate** to confirm the status change.

> [!NOTE]
> After a corrective action is closed or cancelled, the record becomes read-only. You can view deactivated corrective actions using the drop-down list at the top of this section (change the section name from **Active corrective actions** section to **Inactive corrective actions**).

## Related information

- [Global vendor management overview](supplier-engagement-global-vendors-overview.md)
- [Global vendor onboarding lifecycle](supplier-engagement-global-vendor-lifecycle.md)
- [Global vendor feedback](supplier-engagement-global-vendor-feedback.md)
- [Manage activities](supplier-engagement-activities.md)
- [Work with the Supplier Engagement app](supplier-engagement-app-overview.md)
