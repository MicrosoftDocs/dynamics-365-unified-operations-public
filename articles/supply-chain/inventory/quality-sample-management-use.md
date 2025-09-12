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

<!-- KFM: 

Johan: This is raw Copilot generated text. You should review carefully for inspiration, but probably start over on most it. 

-->

# Manage and process samples (preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until 10.0.45 GA -->

Sample management is a vital component of quality control in manufacturing, ensuring that products meet regulatory and quality standards. The process described in this article serves as an example of how sample management can be implemented, but the specific details may vary depending on your company's branch, industry, and practices. By tailoring the sample management process to your organization's needs, you can maintain compliance, improve operational efficiency, and ensure product integrity. Use this guide as a framework to understand the key steps involved, and adapt them to align with your unique requirements and workflows. Proper implementation of sample management can significantly enhance traceability, accountability, and overall quality assurance.

## A typical sample management process

<!-- KFM: into needed -->

1. **Registration** – Register the sample in the system. The system generates a unique sample ID and records relevant details such as sample type and lifecycle state.
1. **Receipt in lab** – Receive the sample in the laboratory and verify its condition. Update the lifecycle state to reflect its arrival.
1. **Storage** – Securely store the sample under appropriate conditions to maintain its integrity. Document storage details, such as location and duration.
1. **Test** – Test the sample based on the predefined testing plan. Record results and flag any deviations from quality standards for review.
1. **Review** – Analyze test results to determine whether the sample meets quality standards. Make decisions regarding the next steps, such as releasing or blocking inventory.
1. **Retention** – Retain compliant samples for a specified period to meet regulatory or business requirements. Retention policies ensure traceability and accountability.
1. **Disposal** – After the retention period, dispose of samples in accordance with safety and regulatory guidelines. Update the lifecycle state to *Disposed* and maintain an audit trail.

:::image type="content" source="media/sample-management-process-diagram.png" alt-text="Diagram of a typical sample management process" lightbox="media/sample-management-process-diagram.png":::

## Sample registration

Sample registration is the first step in the sample management process. It serves as the foundation for ensuring quality control in manufacturing. This step involves creating a unique identity for each sample, which allows for accurate tracking and management throughout its lifecycle. By registering samples, manufacturing managers can ensure that all quality-related data is systematically recorded and easily accessible.

<!-- KFM: 

- Describe how sample records are created (with links to the topics for inline and continuous sampling). Maybe also describe how to manually create a sample from the workbench.
- Describe how the task of taking the sample is assigned and then discovered by the worker that needs to do it.
- How to print and apply the label.
- How the sample is transported to the lab (quality order generates pick and putaway work I suppose).

-->









## Receipt in lab

When a sample arrives in the lab, a worker verifies its condition. This step ensures that only valid samples proceed to testing, maintaining the integrity of the quality management process. This step offers several key benefits:

- **Quality assurance**: Ensures only valid samples are tested.
- **Traceability**: Provides a clear audit trail for sample receipt.
- **Efficiency**: Reduces delays by streamlining the receipt process.

When you receive a sample in the lab, follow these steps:

1. Go to the **Sample Management Workbench**.
1. Find the sample by using its unique ID.
1. Verify the sample’s condition:
   - Check for proper labeling and identification.
   - Inspect for any signs of damage or contamination.
1. Update the lifecycle state to **Received in Lab**.
1. Record observations about the sample’s condition.
1. Save the updates.

## Storage

Proper storage is essential to maintain the integrity of samples until testing. This step prevents degradation or contamination, ensuring reliable test results. This step offers several key benefits:

- **Integrity preservation**: Maintains sample quality for accurate testing.
- **Compliance**: Adheres to storage regulations and standards.
- **Operational efficiency**: Facilitates easy retrieval and reduces mismanagement.

To store a sample:

1. Go to the **Sample Management Workbench**.
1. Find the sample by using its unique ID.
1. Check storage conditions:
   - Make sure the temperature and humidity levels are correct.
   - Make sure the containment and labeling are proper.
1. Update the lifecycle state to **Stored**.
1. Document the storage location and relevant observations.
1. Save the updates.

## Test

Testing is a critical step in the sample management process. In this step, you analyze samples to determine if they meet quality standards. This step provides essential data that drive decision-making regarding product release, rework, or disposal. This step offers several key benefits:

- **Quality control**: Ensures that samples meet the required quality standards before proceeding in the production process.
- **Data-driven decisions**: Accurate test results provide the information needed to make informed decisions regarding product disposition.
- **Compliance assurance**: Systematic testing and documentation support compliance with regulatory and quality requirements.
- **Continuous improvement**: Analyzing test results helps identify trends or issues that may require corrective actions or process improvements.

To conduct testing:

1. Go to the **Sample Management Workbench**.
1. Find the sample by using its unique ID.
1. Verify the sample’s readiness for testing.
1. Conduct tests as per the predefined plan:
   - Physical inspections
   - Chemical analyses
   - Microbiological testing
1. Record test results and flag deviations.
1. Save the updates.

## Review

The review step involves analyzing test results and other relevant data to make informed decisions about the quality and disposition of samples. This step ensures that you release only products that meet the highest quality standards. The review step offers several key benefits:

- **Quality assurance**: The review process ensures that all samples meet the required quality standards before product release.
- **Informed decision-making**: Access to comprehensive data and test results enables objective and accurate decision-making.
- **Regulatory compliance**: Proper review and documentation support adherence to regulatory and quality standards.
- **Process optimization**: Identifying trends or recurring issues during the review can highlight areas for process improvement.

To review a sample:

1. Go to the **Sample Management Workbench**.
1. Find the sample by using its unique ID.
1. Review test results and flagged deviations.
1. Decide on a disposition:
   - **Release**: The sample meets quality standards and is approved for use or sale.
   - **Rework**: The sample requires additional processing to meet quality standards.
   - **Reject**: The sample doesn't meet quality standards and should be discarded or returned.
1. Document the decision and any relevant justifications or instructions in the system.
1. Save the updates.

## Retention

Retention involves keeping compliant samples for a specified period to meet regulatory, quality, or business requirements. This step ensures traceability and accountability, and provides evidence of compliance in case of audits or investigations. This step offers several key benefits:

- **Regulatory compliance**: Proper retention of samples ensures adherence to legal and regulatory requirements.
- **Traceability**: Retained samples provide a reliable reference for future audits, investigations, or quality assessments.
- **Risk management**: Effective retention practices help mitigate risks associated with product recalls, liability claims, or regulatory penalties.
- **Operational efficiency**: Systematic retention and disposal processes optimize storage use and reduce clutter.

To retain a sample:

1. Go to the **Sample Management Workbench**.
1. Find the sample by using its unique ID.
1. Verify the sample is in a compliant state and ready for retention.
1. Update the sample’s lifecycle state to **Retained**.
1. Document the retention start date, duration, and any relevant conditions in the system.
1. Monitor the retention period and receive alerts for samples approaching the end of their retention time.
1. Save the updates.

## Disposal

Disposal involves safely and compliantly disposing of samples that reached the end of their retention period or are no longer needed for testing or quality assurance. Proper disposal minimizes environmental impact, prevents contamination, and ensures compliance with regulatory requirements. This step offers several key benefits:

- **Regulatory compliance**: Proper disposal of samples ensures adherence to environmental and safety regulations.
- **Risk mitigation**: Effective disposal practices reduce the risk of contamination, environmental harm, or regulatory penalties.
- **Operational efficiency**: Systematic disposal processes free up storage space and reduce clutter in the laboratory or storage areas.
- **Data integrity**: Accurate documentation of disposal activities supports reliable tracking and management of samples.

To dispose of a sample:

1. Go to the **Sample Management Workbench**.
1. Find the sample by using its unique ID.
1. Verify the sample is in a disposed state and no longer needed for testing or quality assurance.
1. Update the sample’s lifecycle state to **Disposed**.
1. Document the disposal date, method, and any relevant observations in the system.
1. Ensure that all disposal activities follow safety and environmental regulations.
1. Save the updates.
