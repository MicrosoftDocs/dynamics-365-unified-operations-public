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

This article describes tools that support quality management through reporting, auditing, and procedural guidance. Reports provide insights into trends in test results for specific tests, helping you monitor quality performance over time. Audit trails track changes and actions for compliance and traceability. Sample procedures are step-by-step instructions that workers can access while processing samples through different life cycle states, ensuring consistency in activities such as collection and testing.

## Analyze sample test results

Sample reports provide visibility into how the results of a specific test evolve over time across multiple quality orders and samples for a given production or batch order. By analyzing these trends, you can identify patterns, monitor process stability, and detect potential quality issues early. You can perform this type of analysis for both inline sampling and continuous sampling, giving you flexibility to evaluate quality performance across different sampling strategies. These reports typically aggregate historical data for the selected test, allowing you to compare performance across different periods and make informed decisions for continuous improvement.

### Analyze sample test results for a production order

To analyze sample test results for a production order, follow these steps:

1. Go to **Production control** \> **Production orders** \> **All production orders**.
1. Find and select the order you want to analyze.
1. From the Action Pane, open the **View** tab and, from the **Manage quality** group, select **Analyze inline sample results** or **Analyze continuous sample results**, depending on which type of sample you want to analyze.
1. In the dialog, set the following fields
    - **Test** – Select the test you want to analyze.
    - **Item number** – For production orders, this value is read-only (the order you selected). For batch orders, select a formula item or co-product.
1. Select **OK** to see the report.
1. The report provides a graph that shows the upper and lower limits required to pass the test, along with the actual test results for each sample taken over time. You can hover over each data point to see more details about the specific sample and test result.

## Sample procedures

Supply Chain Management [stores detailed procedures](quality-sample-management-admin.md#define-sample-procedures) for working with each type of sample. Each procedure provides step-by-step guidance for different stages of sample handling, such as collecting samples and performing tests. By following these instructions, workers ensure that sampling and testing activities are consistent and comply with defined quality standards.

To see the procedures defined for any sample, follow these steps:

1. Go to **Inventory management** \> **Periodic tasks** \> **Quality management** \> **Sample management workbench**.
1. Find and select the sample for which you want to view the procedures.
1. From the Action Pane, open the **Sample** tab and select **Sample procedures**.

## Audit trail

Supply Chain Management maintains a full audit trail of all changes made to samples and sample testing records. It provides a detailed log of all actions performed on a selected sample, including the date and time of each change. For updates, the audit trail shows both the previous value and the new value, so you can track the full history of modifications. Each record in the audit trail corresponds to an insert or update event, providing a complete picture of the sample’s lifecycle changes.

To view the audit trail for a sample, follow these steps:

1. Go to **Inventory management** \> **Periodic tasks** \> **Quality management** \> **Sample management workbench**.
1. Find and select the sample for which you want to view the audit trail.
1. From the Action Pane, open the **Sample** tab and select **Audit trail**.
