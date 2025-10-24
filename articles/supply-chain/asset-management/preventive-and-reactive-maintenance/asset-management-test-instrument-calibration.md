---
title: Manage test instrument calibration with Asset Management (preview)
description: Learn about how to use Asset Management to schedule maintenance plans for test instruments used in quality management.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 10/24/2025
ms.custom: 
  - bap-template
---

# Manage test instrument calibration with Asset Management (preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Calibration ensures that test instruments provide accurate and reliable measurements. This accuracy is critical for maintaining product quality, meeting regulatory requirements, and avoiding costly errors. Asset Management in Dynamics 365 Supply Chain Management provides tools to schedule, track, and document calibration activities for all your test instruments.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

Maintaining accurate and reliable test instruments is essential for ensuring product quality, meeting regulatory requirements, and reducing operational risks. Supply Chain Management provides a connected framework that brings together quality control and asset management to achieve these goals.

- **Standardized instrument management** - Define test instrument types to guide quality teams in selecting the right tools for inspections and calibration. This approach ensures consistency, reduces errors, and supports compliance across all quality processes.
- **Full traceability and digital records** - Use test instrument tags as digital twins of physical instruments. These tags store calibration history, specifications, and usage data, enabling complete traceability and simplifying audits.
- **Automated quality tracking** - Quality orders not only capture inspection results but can also track instrument usage automatically. This usage data drives usage-based calibration schedules, ensuring instruments remain accurate without manual intervention.
- **Lifecycle control through asset management** - Model each test instrument as an asset, giving you full visibility into its lifecycle, from acquisition to calibration and retirement, while aligning with maintenance best practices.
- **Proactive calibration scheduling** - Implement maintenance plans to automate calibration scheduling. Plans can be time-based or usage-based, reducing the risk of missed calibrations and ensuring compliance with industry standards.
- **Efficient execution and documentation** - Generate maintenance work orders to perform and document calibration events. These work orders include all necessary details—tasks, resources, and compliance notes. These features help streamline execution and record keeping.

## Prerequisites

To use Asset Management to maintain calibration of test instruments, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.46 or later.
- The following features must be turned on in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md):
    - *Advanced quality management*
    - *(Preview) Optional linking of test instruments to maintainable assets*

## Set up calibration in Asset Management

To set up your system to manage test instrument calibration with Asset Management, complete the following steps. Follow the links to learn more about each step.

1. **Create assets for your test instruments** – Create assets for the test instruments that require scheduled calibration in Asset Management. When defining an asset, you must assign an **Asset type**, which categorizes the asset and helps standardize its management and maintenance processes. Learn more about defining assets in [Create an asset](../objects/create-an-object.md).
1. **Set up test instrument types** – Test instrument types serve as categories for grouping similar test instruments. Each test instrument type must be linked to an **Asset type** to ensure consistency between quality management and asset management processes. Learn more about test instrument types in [Quality management test instruments](../../inventory/quality-test-instruments.md).
1. **Create test instrument tags** – Each tag represents a physical test instrument and links to the test instrument asset in Asset Management. For instructions, see the next section.
1. **Create a maintenance plan** – Create or edit a maintenance plan for the test instrument asset. A maintenance plan is a predefined schedule that automatically creates work orders for recurring maintenance tasks such as calibrating test instruments based on time intervals or usage thresholds. Learn more in [Maintenance plans](maintenance-plans.md).

## Set up test instrument tags for test instruments managed with Asset Management

Each test instrument tag represents a physical test instrument and also links to the test instrument asset in Asset Management. Follow these steps to create a test instrument tag with an asset assigned:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Test instruments** to open the test instruments page.
1. Select or create a test instrument type record where an **Asset type** is assigned, as described in [Quality management test instruments](../../inventory/quality-test-instruments.md).
1. On the Action Pane, select **Test instrument tags**.
1. On the Action Pane, select **New** to add a new tag. Then make the following settings in the header for the new tag:
    - **Tag number** – Enter a unique name, number, or code for the instrument.
    - **Test instrument type** – Specify the test instrument type that this tag belongs to. This field is prefilled to show test instrument type that was selected when you opened the **Test instrument tags** page.
    - **Instrument usage status** – The current usage status of the test instrument. Although the field is read-only, you can manually change the status to *Out of service* or *Available* by using the buttons on the **Update usage status** tab of the Action Pane. The following status values are used:

        - *Available* – The test instrument is ready to be assigned to a new quality order.
        - *Calibration* – The test instrument is currently being calibrated. This status is automatically set when an open (in-progress) calibration record exists for this test instrument tag.
        - *Out of service* – The test instrument is out of service and can't be used for quality order tests. This status is automatically set when the lifetime usage maximum is reached.

1. On the **General** FastTab, make the following settings:
    - **Asset** – Select the asset that represents the test instrument that requires scheduled calibration in Asset Management.
    - **Usage increment** – If the field Fixed increment counter type is set on the related instrument type record, then this field is incremented each time a quality order is validated with the increment specified in the field Usage increment, on the related instrument type record.
    - **Skip check for test instrument on open quality order** – Set this option to *No* to prevent test instrument tags that are already assigned to open quality orders from being assigned to new quality orders. Set it to *Yes* to skip this check (in this case, a test instrument tag might be assigned to more than one open quality order at a time).
    - **Check if test instrument is being calibrated** – Select the action that is taken on a quality order when the **Instrument usage status** value of the instrument is *Calibration*. The default value for new tags is defined in [Inventory and warehouse management parameters](../../inventory/quality-instrument-calibration.md#parameters), but you can change it for individual test instrument tags. The following values are available:
        - *No check* – Skip this check.
        - *Warning only* – If the instrument is being calibrated, show a warning message, but allow the instrument to be used.
        - *Not allowed* – If the instrument is being calibrated, show an error message that states that the instrument can't be used.

1. On the Action Pane, select **Save** to save the new test instrument tag.
