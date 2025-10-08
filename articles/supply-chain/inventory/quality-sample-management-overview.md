---
title: Sample management overview (preview)
description: Learn how sample management enables manufacturers to systematically handle, track, and test product samples throughout their lifecycle.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: overview
ms.date: 10/24/2025
ms.custom: 
  - bap-template
---

# Sample management overview (preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Sample management enables manufacturers to systematically handle, track, and test product samples throughout their lifecycle. This functionality supports industries such as pharmaceuticals, food and beverage, chemicals, and life sciences, where quality assurance and regulatory compliance are critical.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

Sample management provides tools to:

- Define and register samples.
- Execute sampling and testing plans.
- Track sample lifecycle states.
- Analyze test results.
- Control inventory disposition based on quality outcomes.

## Why sample management matters

In regulated and quality-sensitive industries, manufacturers must ensure that products meet strict specifications before release. Sampling is a key part of this process. It allows organizations to test small quantities of product at various stages of production to detect issues early and ensure consistency.

Sample management helps organizations:

- Maintain traceability and auditability of samples.
- Automate sample registration and testing.
- Integrate quality control with production workflows.
- Comply with standards like GMP, GLP, ISO, FDA, and EMA.

## Types of sampling supported

Sample management supports two primary sampling methods:

- **Inline sampling** – Manually collect samples during production, before the item is reported as finished. This method detects quality issues early and ensures stable quality before the finished product. Here are the main characteristics for inline sampling:

    - *When used* – During production, before inventory is reported as finished.
    - *Purpose* – Detect and correct quality issues early (such as pH imbalance or viscosity).
    - *How it works* – Manually register samples on a production or batch order. Each sample generates a quality order. Track quality test results over time to monitor trends.
    - *Inventory impact* – No inventory transactions are associated with inline samples.

- **Continuous sampling** – Automatically take samples at regular intervals throughout batch production to monitor quality trends and maintain consistency in product quality during a production run. Here are the main characteristics for continuous sampling:

    - *When used* – During batch production, triggered automatically when items are reported as finished.
    - *Purpose* – Monitor quality trends and control inventory release.
    - *How it works* – Register samples at defined intervals, such as every two license plates. Test a subset of samples. Based on the test results, release or block the inventory by using batch disposition codes.
    - *Inventory impact* – Inventory transactions are associated with continuous samples.

Each sample type is configured with its own lifecycle states, label layouts, and procedures. These configurations ensure that you handle samples consistently and according to business rules.

## Related quality management tools

Sample management both leverages and enhances existing quality management entities and capabilities within Supply Chain Management, while also introducing new tools and features to support advanced quality processes.

### Existing entities and capabilities

Sample management builds on the following existing quality management entities and capabilities:

- **Quality orders** – Automatically or manually created for each sample to record test results.
- **Item sampling** – Enhanced to support sample registration and testing plans.
- **Test groups** – Define which tests are performed during quality orders and control how inventory is updated for samples, based on whether tests pass or fail.
- **Quality associations** – Link sampling logic to the report-as-finished production event.
- **Batch disposition codes** – Used to block or release produced inventory batches based on test outcomes.
- **Inventory status** – Used to block or release produced license plates based on test outcomes.

### New entities and capabilities

Sample management introduces the following new entities and capabilities:

- **Sample label layouts** – Enable flexible design of sample label content to accommodate specific business requirements.
- **Sample procedures** – Define the specific steps or actions required for handling samples.
- **Sample life cycle states** – Represent the various stages a sample goes through during its lifecycle.
- **Sample types** – Define the classification and processing methods for samples.
- **Sample associations** – Define how and when quality samples are taken for a specific item.
- **Sample procedures** – Define the specific steps or actions required for handling samples.
- **Sample procedure types** – Define categories and groups for organizing sample procedures.
- **Sample management workbench** – A centralized interface for managing samples, viewing audit trails, and performing lifecycle actions.
- **Audit trail** – Tracks all sample-related events including registration, testing, and inventory updates.
