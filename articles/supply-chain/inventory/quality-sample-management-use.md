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
<!-- KFM: Preview until 10.0.47 GA -->

Sample management is a component of quality control in manufacturing. It ensures that products meet regulatory and quality standards. The processes described in this article serve as an example of how you can implement sample management. However, the specific details might vary depending on your company's branch, industry, and practices. By tailoring the sample management process to your organization's needs, you can maintain compliance, improve operational efficiency, and ensure product integrity. 

Use this guide as a framework to understand the key steps involved, and adapt them to align with your unique requirements and workflows. Proper implementation of sample management can significantly enhance traceability, accountability, and overall quality assurance.

The following video provides a high-level overview of sample management capabilities and a demo of how to work with them.

> [!VIDEO 36124ac5-86c0-44f6-a57e-3beb10c753ca]

## Understanding the lifecycle of a sample in sample management

In modern manufacturing and quality control environments, the ability to systematically manage product samples is essential for ensuring compliance, traceability, and consistent product quality. Sample management provides a structured framework for handling samples from their creation through to disposal. It integrates seamlessly with production workflows and quality assurance protocols.

The lifecycle of a sample begins with its registration. You can trigger registration either manually or automatically based on predefined sampling plans. Tailor these plans to the production context, whether *inline sampling*, which occurs during active production before inventory is finalized, or *continuous sampling*, which monitors quality at regular intervals throughout batch production.

Once registered, the system assigns each sample a unique identifier and categorizes it by sample type. The sample type determines its handling procedure, retention policy, and applicable lifecycle states. These lifecycle states, such as *Quality order created*, *Quality order validated*, and *Sample scrapped*, are system-defined and visually tracked to ensure clarity and accountability throughout the sample's journey.

Samples undergo testing through *quality orders*. You can automatically generate or manually initiate these quality orders. The outcome of these tests directly influences inventory control decisions. Passing results might release blocked inventory, while failed tests can trigger automatic blocking of related batches or license plates. This dynamic interaction between sample status and inventory disposition ensures that only quality-approved goods proceed through the supply chain.

Throughout the lifecycle, you manage samples by using tools like the *Sample management workbench*. It offers capabilities such as label printing, audit trail review, lifecycle state changes, and manual overrides. These features empower quality teams to maintain control and visibility over sample data, enabling informed decision-making and regulatory compliance.

In essence, sample management transforms quality control from a reactive process into a proactive, data-driven discipline. By embedding sample lifecycle tracking into production and inventory systems, organizations can uphold high standards of product integrity while streamlining operations across departments.

The remaining sections of this article provide an overview of the activities connected to what could be typical lifecycle states of a sample.

## Sample registration

*Sample registration* is the first step in the sample management process. It serves as the foundation for ensuring quality control in manufacturing. This step involves creating a database record that uniquely identifies each sample, which you can use for accurate tracking and management throughout its lifecycle. By registering samples, manufacturing managers can ensure that the system records all quality-related data and makes it easily accessible. You can register samples in multiple ways, but usually production personnel register them manually as [inline samples](quality-sample-management-inline.md), or periodically based on a [continuous sampling setup](quality-sample-management-continuous.md).

### Register new samples manually with inline sampling

The [inline sampling method](quality-sample-management-inline.md) lets you register new samples directly during the production or inspection process.

### Register new samples automatically with continuous sampling

Use the [continuous sampling method](quality-sample-management-continuous.md) to automatically register new samples based on predefined sampling plans.

### Register new samples manually from the sample management workbench

You can also use the sample management workbench to manually register new samples, providing flexibility for ad-hoc or planned sampling activities. You can only create manual samples from the workbench for existing license plates or batch numbers for products that are set up for continuous sampling.

Follow these steps to use the sample management workbench to manually register a new sample for a license plate or batch number for a product set up for the continuous sampling process:

1. Go to **Inventory management** > **Periodic tasks** > **Quality management** > **Sample Management Workbench**.
1. On the Action Pane, open the **Sample** tab, and select **Create sample**.
1. The **Create manual sample** page opens, showing a list of license plates or batch numbers that are available for sampling. Select the license plate or batch number from which you want to register a new sample.
1. From the Action Pane, select **Create sample**.
1. You return to the sample management workbench, which should now list the newly created sample.
1. Usually, you should also create a quality order for the newly created sample. To do so, go to the Action Pane, open the **Sample** tab, and select **Create manual quality order**. The **Create manual quality order** dialog opens. Review the information, edit it as needed, and select **OK** to create the quality order.

## Collect, label, and test a sample

Accurate sample collection and labeling are foundational to reliable testing and traceability. Proper collection ensures that the sample truly represents the intended material, while clear and consistent labeling safeguards identification throughout analysis and storage, preventing costly mix-ups. Learn more in [Enable and configure sample management](quality-sample-management-admin.md).

### Collect samples

Collecting samples is the physical process of extracting a small fraction of the produced material to represent the entire batch or license plate. This step is essential for quality control and traceability, ensuring that subsequent testing reflects the actual production output.

Workers typically use the sample management workbench to find sample registrations that require collection and labeling. It provides visibility and filtering options for finding sample registrations generated through either inline or continuous sampling methods. The sample registration includes details such as the sample type, size, license plate, associated production order, and [sampling procedures](quality-sample-management-audit-reports.md#sample-procedures), guiding workers on how to collect the sample correctly.

### Print labels

Printed labels ensure proper identification and traceability of a sample throughout the testing process. The label includes the sample ID and other information, such as batch or license plate ID. This prevents mix-ups and supports compliance. After you register a sample in the system, you can generate and print a label for it directly from the sample management workbench. First collect the sample, and then attach the label before storage or analysis. Use the following procedure to print labels for one or more samples.

1. Go to **Inventory management** > **Periodic tasks** > **Quality management** > **Sample Management Workbench**.
1. Find the sample registrations that you want to print a label for by using the **Filter** field or column filters.
1. Select one or more samples you want to print labels for.
1. Usually, use the default label layout, but if you want to choose an alternative layout, open the **Samples** tab on the Action Pane, and select **Change label layout**. Choose the desired layout in the drop-down dialog and select **OK**.
1. On the Action Pane, open the **Samples** tab and select **Print sample label**.
1. The **Print sample label** dialog opens. Make the following settings:
    - **Print destination** – Select *File* to save the label or *Print* to print it now.
    - **Name** – If you chose *Print* as the destination, select the printer you want to use.
1. Select **OK** to print (or save) the labels.

## Test your samples

The purpose of collecting samples is to test them to ensure your production run meets its defined specifications. Sample management uses your recorded test results to influence which produced items can be used or shipped by updating the status of associated license plates or batch numbers based on the outcome.

### Test inline samples

When you [create an inline sample](quality-sample-management-inline.md) from a production order, the system automatically links it to a new quality order. This link ensures that every inline sample has a defined testing process from the start.

Workers can identify inline samples that are ready for testing by using the sample management workbench and applying filters to find samples according to their inspection method or lifecycle state. For example, you might have a sample lifecycle state named *Quality order generated*, which indicates a sample that has an untested quality order, and your system could be configured so that any inline sample automatically moves to this state when a quality order is created for it. Learn more about configuring lifecycle states in [Configure lifecycle states](quality-sample-management-admin.md#configure-lifecycle-states).

Here's an example of how to test an inline sample:

1. Go to **Inventory management** \> **Periodic tasks** \> **Quality management** \> **Sample Management Workbench**.
1. Use the **Filter** field or column filters to find and select the sample registration that you want to test.
1. On the Action Pane, open the **Sample** tab and select **Quality orders**.
1. On the Action Pane, select **Quick result entry**.
1. In the **Result value** field, enter the result of your test. The test passes or fails based on whether your measure value is within the acceptable limits defined by the test.
1. On the Action Pane, select the **Back** button to return to the quality order. Then select **Validate** from the Action Pane.
1. Select **OK** to confirm the dialog and verify that the quality order shows the expected **Status** (either *Pass* or *Fail*).

### Test continuous samples

As with inline samples, workers can identify continuous samples that are ready for testing by using the sample management workbench and applying filters to find samples according to their inspection method or lifecycle state.

When you use continuous sampling, the system automatically generates samples according to a predefined sampling plan set up on the item sampling configuration. Learn more about item sampling in [Configure item sampling policies](quality-sample-management-admin.md#configure-item-sampling-policies). 

For example, if the item sampling plan specifies that a sample should be created for every second license plate produced and a quality order should be produced for every second sample, then for every four license plates manufactured, the system creates two sample registrations and one quality order. The one quality order covers all four license plates. This means that the validation of that single quality order determines the inventory status for all four plates. If the quality order fails, the system updates the status of all four plates to *Blocked*, ensuring that none of them can be used or shipped. 

If a worker wants to perform more detailed testing, they can manually create a quality order from the sample management workbench for a sample that doesn't yet have one associated. When this manual test passes, the system automatically updates the inventory status of the related plates, such as the first two, to indicate availability. This method reduces the number of quality orders required for routine checks while still allowing targeted testing when necessary, and it ensures that inventory status always reflects the outcome of quality validations across the linked items.

Here's an example of how to test a continuous sample:

1. Go to **Inventory management** \> **Periodic tasks** \> **Quality management** \> **Sample Management Workbench**.
1. Select a row that shows the **Item number** you want to test.
1. On the Action Pane, open the **Sample** tab and select **Sample relationships**. The **Sample relationships** page shows information about samples and license plates related to the selected sample. You can find the following information here:
    - There is a record for each license plate that has been reported as finished and is waiting for quality testing.
    - Some license plates have samples registered for them (for example, every second license plate), as configured in the item sampling setup.
    - Some of the sampled license plates also have quality orders created for them (for example, every second sample), as configured in the item sampling setup.
1. Go back to the sample management workbench and select the specific sample that you want to test. The sample should be for the item you selected that has a quality order associated with it.
1. On the Action Pane, open the **Sample** tab and select **Quality orders**.
1. On the Action Pane, select **Quick result entry**.
1. In the **Result value** field, enter the result of your test. The test passes or fails based on whether your measure value is within the acceptable limits defined by the test.
1. On the Action Pane, select the **Back** button to return to the quality order. Then select **Validate** from the Action Pane.
1. The **Validate the quality order** dialog opens. The **Sample management** section of the dialog shows the following information:
    - If the test passes, then the **Update inventory status to** field is set to *Available*. If the test fails, then the **Update inventory status to** field is set to *Blocked*. The statuses for each type of result are configured on the relevant [test group](quality-sample-management-admin.md#test-groups).
    - All the license plates listed in the grid will be assigned the **Update inventory status to** status, which is based on the test result.
    - A failed status typically prevents the license plate from being used in any warehouse or inventory transactions.
1. Select **OK** to confirm the dialog and assign the inventory status to each of the listed license plates.
1. Go back to the sample management workbench and confirm that the license plates for each sample have the updated inventory status that you expect to see. If you don't see the inventory status in the grid, select **Dimensions display** on the Action Pane to add it.

## Sample archiving

After you collect, label, and successfully test a sample, you can archive it for a defined period until it reaches its expiration date. The system sets the expiration date when you create the sample and calculates it based on the rules specified in the sample association. The system uses the sample lifecycle state to show when a sample is archived, marking its transition from active testing to storage. For details on how expiration periods are determined through sample associations, go to [Set up sample associations](quality-sample-management-admin.md#set-up-sample-associations).

To support archiving, make sure you define a lifecycle state that represents the archived state and select this state on the sample type configured for the product. Learn more in [Configure lifecycle states](quality-sample-management-admin.md) and [Define sample types](quality-sample-management-admin.md#define-sample-types).

Use the following procedure to change the lifecycle state:

1. Go to **Inventory management** \> **Periodic tasks** \> **Quality management** \> **Sample Management Workbench**.
1. Use the **Filter** field or column filters to find and select the sample registration that you want to archive.
1. On the Action Pane, open the **Sample** tab and select **Change lifecycle state**. Choose the desired lifecycle state in the drop-down dialog and select **OK**.

## Sample disposal

Disposal involves safely and compliantly disposing of samples that reach the end of their retention period or are no longer needed for testing or quality assurance. Proper disposal minimizes environmental impact, prevents contamination, and ensures compliance with regulatory requirements.

The system uses the sample lifecycle state to show when a sample is disposed, marking its transition from active testing to disposal. To identify samples that have expired in the sample management workbench, you can filter for those whose expiration date has passed.

To support sample disposal, make sure you define a lifecycle state that represents the disposed state and select this state on the sample type configured for the product. Learn more in [Configure lifecycle states](quality-sample-management-admin.md) and [Define sample types](quality-sample-management-admin.md#define-sample-types).

To dispose of a sample, follow these steps:

1. Go to **Inventory management** \> **Periodic tasks** \> **Quality management** \> **Sample Management Workbench**.
1. Use the **Filter** field or column filters to find and select the sample registration that you want to archive.
1. On the Action Pane, open the **Sample** tab and select **Change lifecycle state**. Choose the desired lifecycle state in the drop-down dialog and select **OK**.

The *Disposed* state is typically the final stage in a sample’s lifecycle. You can only delete samples from the sample management workbench after they reach a state that is configured with the property **Sample scrapped**. Learn more about how to define the lifecycle state in [Configure lifecycle states](quality-sample-management-admin.md#configure-lifecycle-states).
