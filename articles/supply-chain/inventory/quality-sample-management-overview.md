---
title: Sample management overview (preview)
description: Learn how sample management enables manufacturers to systematically handle, track, and test product samples throughout their lifecycle.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 10/24/2025
ms.custom: 
  - bap-template
---

<!-- KFM: 

Johan: This is raw Copilot generated text. You should review carefully for inspiration, but probably start over on most it. 

-->

# Sample management overview (preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until 10.0.45 GA -->

Sample management enables manufacturers to systematically handle, track, and test product samples throughout their lifecycle. This functionality supports industries such as pharmaceuticals, food and beverage, chemicals, and life sciences, where quality assurance and regulatory compliance are critical.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

Sample management provides tools to:

- Define and register samples.
- Execute sampling and testing plans.
- Track sample lifecycle states.
- Analyze test results.
- Control inventory disposition based on quality outcomes.

## Why sample management matters

In regulated and quality-sensitive industries, manufacturers must ensure that products meet strict specifications before release. Sampling is a key part of this process—it allows organizations to test small quantities of product at various stages of production to detect issues early and ensure consistency.

Sample management helps organizations:

- Maintain traceability and auditability of samples.
- Automate sample registration and testing.
- Integrate quality control with production workflows.
- Comply with standards like GMP, GLP, ISO, FDA, and EMA.

## Types of Sampling Supported

Dynamics 365 supports two primary sampling methods:

1. Inline sampling

Samples are collected during production, before the item is reported as finished. This allows for early detection of quality issues.

    - **When used** – During production, before inventory is reported as finished.
    - **Purpose** – To detect and correct quality issues early (e.g., pH imbalance, viscosity).
    - **How it works** – Samples are manually registered on a production or batch order. Each sample  generates a quality order. Quality test results are tracked over time to monitor trends.
    - **Inventory impact** – No inventory transactions are associated with inline samples.

2. Continuous sampling

Samples are taken at regular intervals throughout batch production to monitor quality trends and maintain consistency.

    - **When used** – During batch production, triggered automatically at Report as finished.
    - **Purpose** – To monitor quality trends and control inventory release.
    - **How it works** – Samples are registered at defined intervals, such as every two license plates. A subset of samples is tested. Based on results, inventory is either released or blocked using batch disposition codes.
    - **Inventory impact** – Inventory transactions are associated with continuous samples.

Each sample type is configured with its own lifecycle states, label layouts, and procedures. These configurations ensure that samples are handled consistently and according to business rules.

## Related quality management tools

Sample management both leverages and enhances existing quality management entities and capabilities within Supply Chain Management, while also introducing new tools and features to support advanced quality processes.


### Existing entities and capabilities

- **Quality Orders** – Automatically or manually created for each sample to record test results.
- **Item Sampling** – Enhanced to support sample registration and testing plans.
- **Test groups** - Test groups define which tests are performed during quality orders and control how inventory is updated for samples, based on whether tests pass or fail.
- **Quality Associations** – Link sampling logic to the report as finished production event.
- **Batch Disposition Codes** – Used to block or release produced inventory batches based on test outcomes.
- **Inventory status** - Used to block or release produced license plates based on test outcomes. 

### New entities and capabilities

- **Sample label layouts** - Enable flexible design of sample labels content to accommodate specific business requirements.
- **Sample procedures** - Defines the specific steps or actions required for handling samples.
- **Sample life cycle states** - Represent the various stages a sample goes through during its lifecycle.
- **Sample types** - Defines the classification and processing methods for samples. 
- **Sample associations** - Defines how and when quality samples are taken for a specific item. 
- **Sample procedures and sample procedure types** - Sample procedure define the specific steps or actions required for handling samples. Sample procedure types define the categories and groups for organizing procedures.
- **Sample Management Workbench** – A new centralized interface for managing samples, viewing audit trails, and performing lifecycle actions.
- **Audit Trail** – Tracks all sample-related events including registration, testing, and inventory updates.

