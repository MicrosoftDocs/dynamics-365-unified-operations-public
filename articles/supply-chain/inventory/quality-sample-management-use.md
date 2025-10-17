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

In sample management, samples can be created either manually or automatically, depending on the process requirements. 

- **Manual creation**

    1. **Inline sampling method** – This approach allows users to create samples directly during the production or inspection process. Learn more in: [Initiate an inline sample (preview)](quality-sample-management-inline.md)
    2. **Sample management workbench** – Users can manually create samples from the workbench interface, providing flexibility for ad-hoc or planned sampling activities. Only samples using the **Continuous sampling method** can be created manually from workbench. Follow these steps to manually create a sample for a license plate of batch number for a product that has been set up for the continuous sampling process:
        1. Create batch order for continuous sampling and report as finished four license plates to generate two samples. See description of scenario in [Initiate an inline sample (preview)](quality-sample-management-inline.md)
        1. Select the record for the production order in the the production order list page
        1. From the Action pane, select **Sample Management Workbench** and verify that two samples for the production order are listed.
        1. From the Action pane, select **Create manual sample**.
        1. Select one of the two license plates listed to which you want to associate a new sample.
        1. From the Action pane, select **Create sample**.
        1. Verify that a new record for the sample has been created in the sample management workbench. 
        1. From the Action pane, select **Create manual quality order** if you with to associate a quality order to the newly created sample.
- **Automatic creation**
    Samples are generated automatically when using the **Continuous** sampling method. Learn more in: [Set up continuous sampling (preview)](quality-sample-management-continuous.md)

## Collect, print label, and test the sample

Accurate sample collection and labeling are foundational to reliable testing and traceability. Proper collection ensures that the sample truly represents the intended material, while clear and consistent labeling safeguards identification throughout analysis and storage, preventing costly mix-ups. Learn more in: [Enable and configure sample management (preview)](quality-sample-management-admin.md)

### Collect samples

Collecting samples is the process of extracting a small fraction of the produced material to represent the entire batch or license plate. This step is essential for quality control and traceability, ensuring that subsequent testing reflects the actual production output. Workers typically perform this task using the sample management workbench, which provides visibility and filtering options for samples generated through either inline or continuous sampling methods.

### Print labels

 Printing the sample label is a crucial step to ensure proper identification and traceability throughout the testing process. A clear, accurate label links the sample to its batch or license plate, preventing mix-ups and supporting compliance. Once the sample is collected and recorded in the system, the label can be generated and printed directly from the sample management workbench, ready to be attached before storage or analysis. Use the following procedure to collect and print the labels for a set of samples associated a batch order.

1. Go to **Inventory management** \> **Periodic tasks** \> **Quality management** \> **Sample Management Workbench**.
1. Find the samples by filtering on the production or batch order number.
1. Select a specific sample or multi-select a range of samples you wish to print labels for.
1. In the Action pane, select **Print sample label** and confirm the printout.

## Testing samples 

Testing samples is a critical step in verifying product quality and compliance. Samples collected through both inline and continuous sampling methods can be tested to ensure they meet defined specifications. Within Sample Management, test results are configured to influence production control by updating the status of associated license plates or batch numbers based on the outcome. This integration helps maintain traceability and enforces quality standards throughout the manufacturing process.

### Testing inline samples

When an inline sample is created from the production order list page, it is automatically linked to a quality order, ensuring that every inline sample has a defined testing process from the start. Learn more about inline samples in: [Initiate an inline sample (preview)](quality-sample-management-inline.md).

Workers can identify inline samples ready for testing by using the sample management workbench and applying filters such as **Sample inspection method** = *Inline process* combined with the Life cycle state. For example, you might create a state named *Quality order generated* to indicate that the sample has an untested quality order. Once this state is part of the life cycle state model and the Quality order created property is enabled, any inline sample will automatically move to *Quality order generated* when its quality order is created. Learn more about configuring life cycle states in: [Configure lifecycle states](quality-sample-management-admin.md#configure-lifecycle-states).

To conduct testing of an inline sample (example):

1. Create a batch order for a product set for continuous sampling and report as finished four license plates to generate two samples. See description of the scenario in [Initiate an inline sample (preview)](quality-sample-management-inline.md)
1. Select the record for the production order in the the production order list page
1. From the Action pane, select **Sample Management Workbench** and verify that a sample with an associated quality order exists.
1. From the Action pane, select **Quality order**.
1. From the action pane, select **Quick result entry**.
1. In the **Result value** field, set a value that is within the accepted range for the test to pass.
1. Close the **Quick result entry** dialog, and select **Validate** from the Action pane.
1. Select **OK** to confirm the dialog and verify that the quality order is in status *Passed*.

### Testing continuous samples

Workers can identify continuous samples ready for testing by using the sample management workbench and applying filters such as **Sample inspection method** = *Continuous process* combined with the Life cycle state. For example, you might create a state named *Quality order generated* to indicate that the sample has an untested quality order. Once this state is part of the life cycle state model and the Quality order created property is enabled, any inline sample will automatically move to *Quality order generated* when its quality order is created. Learn more about configuring life cycle states in: [Configure lifecycle states](quality-sample-management-admin.md#configure-lifecycle-states).

When using continuous sampling, samples are generated automatically according to a predefined sampling plan set up on the item sampling configuration. Learn more about item sampling in: [Configure item sampling policies](quality-sample-management-admin.md#configure-item-sampling-policies). For example, if the item sampling plan specifies that a sample should be created for every second license plate produced, then as four license plates are manufactured, two samples will be created. However, only one quality order is generated to cover all four license plates. This means that the validation of that single quality order determines the inventory status for all four plates. If the quality order fails, the system updates the status of all four plates to blocked, ensuring that none of them can be used or shipped. If a worker wants to perform more detailed testing, they can manually create a quality order from the sample management workbench for a sample that does not yet have one associated. When this manual test passes, the system automatically updates the inventory status of the related plates, such as the first two, to indicate availability. This method reduces the number of quality orders required for routine checks while still allowing targeted testing when necessary, and it ensures that inventory status always reflects the outcome of quality validations across the linked items.

To conduct testing of continuous samples (example):

1. Create a batch order for a product set for continuous sampling and report as finished four license plates to generate two samples. See description of the scenario in: [Set up continuous sampling (preview)](quality-sample-management-continuous.md).
1. Select the record for the production order in the the production order list page
1. From the Action pane, select **Sample Management Workbench** and verify that two samples for the production order are listed.
1. From the Action pane, select **Sample relationships**
1. In the sample relationships page, verify that:
    - A record exist for each of the four license plates you reported
    - A sample has been created for every second license plate.
    - A quality order has been created for every second sample. Note the sample ID for the sample with the associated quality order.
1. Navigate back to the sample management workbench and select the record for the sample with the associated quality order.
1. From the action pane, select **Quality order**.
1. From the action pane, select **Quick result entry**.
1. In the **Result value** field, set a value that is within the accepted range for the test to pass.
1. Close the **Quick result entry** dialog, and select **Validate** from the Action pane.
1. In the **Sample management** section of the dialog, verify that:
    - The field **Update inventory status to** is set to *Available*. This status is defaulted from the definition of the status to use for passed tests on the test group. Learn more in: [Test groups](quality-sample-management-admin.md#test-groups). In case the quality order result falls outside the permitted range and the order is marked as failed, the system will propose to update the four license plate to a status of  *Failed*. A failed status typically prevents the license plate from being used in any warehouse or inventory transactions.
    - All the for license plates related to the test are listed in the grid section.
1. Select **OK** to confirm the dialog and verify that the quality order is in status *Passed*.
1. Navigate back to the sample management workbench and validate that:
    - The license plates for each sample has an inventory status that is *Available*. If you do not see the inventory status in the grid, you can enable it from the **Dimensions display** opened from the Action pane.
    - The sample with the associated quality order has automatically changed state to a state that indicates that the quality order is validated. This updates requires that the sample is configured with a sample life cycle state  with the property **Quality order validated** set to *Yes*. Learn more about the sample life cycle state in: [Configure lifecycle states](quality-sample-management-admin).

## Sample archiving

Once a sample has been collected, labeled, and successfully tested, it is typically archived for a defined period until it reaches its expiration date. The expiration date is determined when the sample is created and calculated based on the rules specified in the sample association. The system uses the sample life cycle state to indicate when a sample has been archived, marking its transition from active testing to storage. For details on how expiration periods are determined through sample associations, see: [Set up sample associations](quality-sample-management-admin.md#set-up-sample-associations). 

Use the following procedure to change the life cycle state from the sample management workbench:

1. Make sure you have defined a life cycle state that represents the archived state and that this state is selected on the sample type configured for the product. Learn more in [Configure lifecycle states](quality-sample-management-admin) and [Define sample types](quality-sample-management-admin.md#define-sample-types).
1. Create a batch order with continuous samples as described in: [Testing continuous samples](#testing-continuous-samples).
1. In the sample management workbench, select a sample for the production or batch order.
1. Select one sample or multi-select multiple samples.
1. On the Action pane, select **Change life cycle state** and select the *Achieved* state.

## Sample disposal

Disposal involves safely and compliantly disposing of samples that reached the end of their retention period or are no longer needed for testing or quality assurance. Proper disposal minimizes environmental impact, prevents contamination, and ensures compliance with regulatory requirements.

The system uses the sample life cycle state to indicate when a sample has been disposed, marking its transition from active testing to disposal. To identify samples that have expired in the sample management workbench, you can filter for those whose expiration date has passed.

To dispose of a sample follow these steps:

1. Make sure you have defined a life cycle state that represents the disposed state and that this state is selected on the sample type configured for the product. Learn more in [Configure lifecycle states](quality-sample-management-admin) and [Define sample types](quality-sample-management-admin.md#define-sample-types).
1. Create a batch order with continuous samples as described in: [Testing continuous samples](#testing-continuous-samples).
1. In the sample management workbench, select a sample for the production or batch order.
1. From the Action pane, select **Change expiration date** and select a date in the past in the dialog, to make this sample past it's expiration date.
1. On the Action pane, select **Change life cycle state** and select the *Disposed* state.

The *Disposed* state is typically the final stage in a sample’s life cycle. Samples can only be deleted from the Sample management workbench after they have reached a state that is configured with the property **Sample scrapped**. Learn more about how to define the life cycle state in: [Configure lifecycle states](quality-sample-management-admin.md#configure-lifecycle-states).

For each activity performed in the sample management workers can get instructions and information from sample procedures. Learn more about sample procedures in: 