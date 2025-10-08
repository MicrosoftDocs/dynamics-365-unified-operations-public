---
title: Use asset management to maintain calibration of test instruments
description: Learn about how to schedule maintenance plans in Asset Management, for test instruments used in quality management.
author: johanhoMSFT
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 10/08/2025
ms.custom: 
  - bap-template
---

# Use asset management to maintain calibration of test instruments

[!include [banner](../../includes/banner.md)]

Calibration ensures that test instruments provide accurate and reliable measurements, which is critical for maintaining product quality, meeting regulatory requirements, and avoiding costly errors. Asset Management in Dynamics 365 Supply Chain Management provides tools to schedule, track, and document calibration activities for all your test instruments.

## Key concepts

Maintaining accurate and reliable test instruments is essential for ensuring product quality, meeting regulatory requirements, and reducing operational risks. Dynamics 365 Supply Chain Management provides a connected framework that brings together quality control and asset management to achieve these goals.

- **Standardized instrument management** - Define test instrument types to guide quality teams in selecting the right tools for inspections and calibration. This ensures consistency, reduces errors, and supports compliance across all quality processes.
- **Full Traceability and Digital Records** - Use test instrument tags as digital twins of physical instruments. These tags store calibration history, specifications, and usage data, enabling complete traceability and simplifying audits.
- **Automated Quality Tracking** - Quality orders not only capture inspection results but can also track instrument usage automatically. This usage data drives usage-based calibration schedules, ensuring instruments remain accurate without manual intervention.
- **Lifecycle Control Through Asset Management** - Model each test instrument as an asset, giving you full visibility into its lifecycle—from acquisition to calibration and retirement—while aligning with maintenance best practices.
- **Proactive Calibration Scheduling** - Implement maintenance plans to automate calibration scheduling. Plans can be time-based or usage-based, reducing the risk of missed calibrations and ensuring compliance with industry standards.
- **Efficient Execution and Documentation** - Generate maintenance work orders to perform and document calibration events. These work orders include all necessary details—tasks, resources, and compliance notes—streamlining execution and record-keeping.

## Set up calibration in asset management

1. **Assets for test instruments** - Create assets for the test instruments that require scheduled calibration in asset management. When defining an asset, you must assign an **Asset type**, which categorizes the asset and helps standardize its management and maintenance processes. Learn more about defining assets in: [Create an asset](../objects/create-an-object.md).
1. **Test instrument type** - Create or update test instrument types, which serve as categories for grouping similar test instruments. Each test instrument type should be linked to an **Asset type** to ensure consistency between quality management and asset management processes. Learn more about test instrument types in: [Use asset management to maintain calibration of test instruments](test-instrument-calibration.md).
1. **Test instrument tags** - Create a test instrument tag. The tag represents the physical test instrument and links to the test instrument asset in asset management. Learn more in: TO-DO.
1. **Maintenance plan** - Create or edit a maintenance plan for the test instrument asset. A maintenance plan is a predefined schedule that automatically creates work orders for recurring maintenance tasks such as calibrating test instruments based on time intervals or usage thresholds. Learn more in: [Maintenance plans](maintenance-plans.md).
