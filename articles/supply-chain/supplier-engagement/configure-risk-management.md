---
title: Configure risk management elements (preview)
description: Configure risk scenarios and corrective action types so purchasers can assess and manage vendor risk consistently.
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

# Configure risk management elements (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Risk configuration helps purchasers identify, assess, and monitor issues that might affect vendors or supply chain operations. When you define risk scenarios and corrective action types ahead of time, teams can evaluate risks consistently and track mitigation work more effectively. Historical analysis and reporting also become easier because the same structures are used across the supplier network.

## Risk scenarios

Risk scenarios define the types of issues that can affect vendors or supply chain operations, such as financial instability, regulatory noncompliance, quality failures, or delivery delays. Configuring these scenarios helps purchasers classify and evaluate risks consistently across vendors.

## Corrective action types

Corrective action types define the measures that purchasers take to reduce or eliminate identified risks. Each action type represents a mitigation approach that you can associate with one or more risk scenarios.

## Risk hierarchies

Both risk scenarios and corrective action types support parent-child relationships. This structure lets you group related risks and mitigation strategies into multilevel hierarchies that are easier to analyze and manage.

For example, a parent risk scenario such as *Dependence* can include child scenarios, while a corrective action type such as *Mitigation* can include more specific actions beneath it. These relationships use self-referential one-to-many relationships, where each record can link to a parent record of the same type.

## Create, delete, and edit risk management elements

Use the following procedure to manage risk scenarios and corrective action types.

1. Open the Supplier Engagement app, and at the bottom of the navigation pane, select the **Configuration** area.
1. On the navigation pane, under the **Risks** heading, select the risk entity that you want to set up: **Risk scenarios** or **Corrective action types**.
1. Either open an existing record to edit it or, on the command bar, select **New** to create a record. You can also select **Delete** to remove a selected record.
1. Enter the following information for the new or selected record:
    - **Name** – Enter a descriptive name.
    - **Parent** – If the record belongs under another record of the same type, select the parent record to place it in the hierarchy.
1. Select **Save**.

## Related information

- [Configure the Supplier Engagement app overview](configure-app-overview.md)
- [Configure certificate types and organizations](configure-certificate-types.md)
- [Configure capabilities](configure-capabilities.md)
- [Configure self-assessment questions](configure-self-assessment.md)
- [Configure Supplier Engagement app settings](configure-settings.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
