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

    - **When used** – During production, before inventory is reported as finished.
    - **Purpose** – To detect and correct quality issues early (e.g., pH imbalance, viscosity).
    - **How it works** – Samples are manually registered and tested. Each test generates a quality order. Results are tracked over time to monitor trends.
    - **Inventory impact** – No inventory transactions are associated with inline samples.

2. Continuous sampling

    - **When used** – During batch production, triggered automatically at Report as Finished (RAF).
    - **Purpose** – To monitor quality trends and control inventory release.
    - **How it works** – Samples are registered at defined intervals (e.g., every 2 license plates). A subset of samples is tested. Based on results, inventory is either released or blocked using batch disposition codes.
    - **Inventory impact** – Inventory transactions are associated with continuous samples.

Each sample type is configured with its own lifecycle states, label layouts, and procedures. These configurations ensure that samples are handled consistently and according to business rules.

## Related quality management tools

Sample management builds on and integrates with existing quality management capabilities in Supply Chain Management:

- **Quality Orders** – Automatically or manually created for each sample to record test results.
- **Item Sampling** – Enhanced to support sample registration and testing plans.
- **Quality Associations** – Link sampling logic to production events like RAF.
- **Batch Disposition Codes** – Used to block or release inventory based on test outcomes.
- **Sample Management Workbench** – A new centralized interface for managing samples, viewing audit trails, and performing lifecycle actions.
- **Audit Trail** – Tracks all sample-related events including registration, testing, and inventory updates.

