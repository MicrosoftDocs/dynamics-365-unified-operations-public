---
title: Sample management reports and auditing (preview)
description: Learn how to view sample management reports and audit your sample and sample-testing records.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 10/24/2025
ms.custom: 
  - bap-template
---

# Sample management reports and auditing (preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

This section covers tools that support quality management through reporting, auditing, and procedural guidance. Reports provide insights into trends in test results for specific tests, helping to monitor quality performance over time. Audit trails track changes and actions for compliance and traceability. Sample procedures are step-by-step instructions that workers can access while processing samples through different life cycle states, ensuring consistency in activities such as collection and testing.

## Analyze sample test results

Reports provide visibility into how the results of a specific test evolve over time across multiple quality orders and samples for a given production or batch order. By analyzing these trends, you can identify patterns, monitor process stability, and detect potential quality issues early. This type of analysis can be performed for both inline sampling and continuous sampling, giving you flexibility to evaluate quality performance across different sampling strategies. These reports typically aggregate historical data for the selected test, allowing you to compare performance across different periods and make informed decisions for continuous improvement.

### Analyze inline sample results

To analyze sample test results for inline samples, follow these steps:

1. Create an inline sample as described in: [Initiate the sample](quality-sample-management-inline.md#initiate-the-sample).
1. Repeat the steps to create a second inline sample for the production or batch order.
1. From the Action pane in the sample management workbench, select **Quality orders**. You should see two quality orders, one for each inline sample created.
1. For each quality order enter a test result that is within the allowed threshold as described in: [Testing inline samples](quality-sample-management-use.md#testing-inline-samples).
1. Validate each quality order, so the are in *Passed* state.
1. From the Action pane in the production order list page, select **Analyze inline sample results**
1. In the dialog, set the following fields
    - **Test** – Select the test you want to analyze.
    - **Item** – Select the item that is being tested.
1. Select **OK** to see the chart.
  
Follow the same procedure for continuous samples in the sample management workbench.

## Sample procedures

Workers can access predefined procedures when working with samples. These procedures provide step-by-step guidance for different stages of sample handling, such as collecting samples and performing tests. By following these instructions, workers ensure that sampling and testing activities are carried out consistently and in compliance with defined quality standards. Learn more about how to define procedures in: [Define sample procedures](quality-sample-management-admin.md#define-sample-procedures).

To open a sample procedure follow these steps:

1. Create a batch or production order and inline samples as described in: [Initiate an inline sample (preview)](quality-sample-management-inline.md).
1. Make sure you have defined sample procedures and these are associated a sample association used for the production or batch order. Learn more about how to define sample procedures and sample associations in: [Enable and configure sample management (preview)](quality-sample-management-admin.md).
1. From the Action pane in the production order list page, select **Sample management workbench**.
1. From the Action pane, select **Sample procedures**.

## Audit trail

From the Sample management workbench, workers can open the audit trail for any sample. This view displays a detailed log of all actions performed on the sample, including the date and time of each change. For updates, the audit trail shows both the previous value and the new value, allowing users to track the full history of modifications. Each record in the audit trail corresponds to an insert or update event, providing a complete picture of the sample’s lifecycle changes.
