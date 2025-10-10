---
title: Manage and process samples (preview)
description: Learn how workers can use sample management features to collect and manage samples for quality testing.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 10/24/2025
ms.custom: 
  - bap-template
---

# Manage and process samples (preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Sample management is a component of quality control in manufacturing, ensuring that products meet regulatory and quality standards. The process described in this article serves as an example of how sample management can be implemented, but the specific details may vary depending on your company's branch, industry, and practices. By tailoring the sample management process to your organization's needs, you can maintain compliance, improve operational efficiency, and ensure product integrity. Use this guide as a framework to understand the key steps involved, and adapt them to align with your unique requirements and workflows. Proper implementation of sample management can significantly enhance traceability, accountability, and overall quality assurance.

## Understanding the lifecycle of a sample in sample management

In modern manufacturing and quality control environments, the ability to systematically manage product samples is essential for ensuring compliance, traceability, and consistent product quality. Sample management provides a structured framework for handling samples from their creation through to disposal, integrating seamlessly with production workflows and quality assurance protocols.
The lifecycle of a sample begins with its registration, triggered either manually or automatically based on predefined sampling plans. These plans are tailored to the production context—whether inline sampling, which occurs during active production before inventory is finalized, or continuous sampling, which monitors quality at regular intervals throughout batch production.

Once registered, each sample is assigned a unique identifier and categorized by sample type, which determines its handling procedure, retention policy, and applicable lifecycle states. These lifecycle states—such as Quality Order Created, Quality Order Validated, and Sample Scrapped—are system-defined and visually tracked to ensure clarity and accountability throughout the sample's journey.

Samples undergo testing via quality orders, which may be automatically generated or manually initiated. The outcome of these tests directly influences inventory control decisions: passing results may release blocked inventory, while failed tests can trigger automatic blocking of related batches or license plates. This dynamic interaction between sample status and inventory disposition ensures that only quality-approved goods proceed through the supply chain.

Throughout the lifecycle, samples are managed using tools like the sample management workbench, which offers capabilities such as label printing, audit trail review, lifecycle state changes, and manual overrides. These features empower quality teams to maintain control and visibility over sample data, enabling informed decision-making and regulatory compliance.

In essence, sample management transforms quality control from a reactive process into a proactive, data-driven discipline. By embedding sample lifecycle tracking into production and inventory systems, organizations can uphold high standards of product integrity while streamlining operations across departments.

The remaining sections of this article provide an overview of the activities connected to what could be typical life cycle states of a sample.

## Sample registration

Sample registration is the first step in the sample management process. It serves as the foundation for ensuring quality control in manufacturing. This step involves creating a unique identity for each sample, which allows for accurate tracking and management throughout its lifecycle. By registering samples, manufacturing managers can ensure that all quality-related data is systematically recorded and easily accessible. Samples can be registered in multiple ways, but usually they are registered manually by production personnel as [inline samples](quality-sample-management-inline.md), or periodically based on a [continuous sampling setup](quality-sample-management-continuous.md).

<!-- KFM: We have a **Create manual sample** item in the Action Pane of the workbench, but it's always disabled for me for some reason. We should maybe describe how to enable and use this. -->

## Collect and label the sample

<!-- KFM: I think we should have a section for this. Mention the related commands in the Action Pane of the workbench for choosing layout and printing labels. -->

## Receive and store samples

Proper storage is essential to maintain the integrity of samples until testing. This step prevents degradation or contamination, ensuring reliable test results.

To store a sample:

1. Go to **Inventory management** \> **Periodic tasks** \> **Quality management** \> **Sample Management Workbench**.
1. Find the sample by using its unique **Sample ID**.
1. Check storage conditions, for example: <!-- KFM: How do we know these? Are the linked or listed as part of the sample record somewhere? -->
   - Make sure the temperature and humidity levels are correct.
   - Make sure the containment and labeling are proper.
1. Update the lifecycle state to *Stored*. <!-- KFM: Tell how to do this. -->
1. Document the storage location and relevant observations. <!-- KFM: Tell how to do this. -->
1. Save the updates. <!-- KFM: Tell how to do this. -->

## Test samples

Testing is a critical step in the sample management process. In this step, you analyze samples to determine if they meet quality standards.

<!-- KFM: This should probably be rather longer. Include more details from [Set up continuous sampling (preview)](quality-sample-management-continuous.md), and maybe include them more here than there.  -->

To conduct testing:

1. Go to **Inventory management** \> **Periodic tasks** \> **Quality management** \> **Sample Management Workbench**.
1. Find the sample by using its unique **Sample ID**.
1. Verify the sample's readiness for testing.
1. Conduct tests as per the predefined plan, for example: <!-- KFM: Tell how to lookup the required tests. -->
   - Physical inspections
   - Chemical analyses
   - Microbiological testing
1. Record test results and flag deviations. <!-- KFM: Tell how to do this. -->
1. Save the updates. <!-- KFM: Tell how to do this. -->

## Handle sample failures

<!-- KFM: We should describe what to do when a sample fails, including the fallback to previous sample and releasing products in between. Maybe in a new section. -->

## Sample disposal

Disposal involves safely and compliantly disposing of samples that reached the end of their retention period or are no longer needed for testing or quality assurance. Proper disposal minimizes environmental impact, prevents contamination, and ensures compliance with regulatory requirements.

To dispose of a sample:

1. Go to **Inventory management** \> **Periodic tasks** \> **Quality management** \> **Sample Management Workbench**.
1. Find the sample by using its unique **Sample ID**. <!-- KFM: Maybe I should also (or instead) looks for samples in a particular status? -->
1. Verify the sample is in a disposed state and no longer needed for testing or quality assurance.
1. Update the sample's lifecycle state to *Disposed*. <!-- KFM: Tell how to do this. -->
1. Document the disposal date, method, and any relevant observations in the system. <!-- KFM: Tell how to do this. -->
1. Ensure that all disposal activities follow safety and environmental regulations.
1. Save the updates. <!-- KFM: Tell how to do this. -->
