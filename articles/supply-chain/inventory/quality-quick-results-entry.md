---
title: Enter quality test results quickly
description: Learn how to use the Quick results entry page, which consolidates data from all tests into a single view to streamline the entry process.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: InventQualityOrderTable, QMSInventQualityOrderLineResults
ms.topic: how-to
ms.date: 04/25/2025
ms.custom: 
  - bap-template
---

# Enter quality test results quickly

[!include [banner](../../includes/banner.md)]

The **Quick results entry** page makes the process of entering quality order test results faster and more flexible than the **Quality order line results** page. The **Quick results entry** page consolidates data from all tests into a single view to streamline the result entry process. Quantities are automatically populated based on the quality order quantities. Other details are also populated, such as minimum, maximum, and target values.

## Prerequisites

Before you can use the features that are described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.44 or later.
- The feature that is named *Advanced quality management* must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). As of Supply Chain Management version 10.0.47, this feature is turned on by default.

## Enter quality test results

To enter quality test results by using the **Quick results entry** page, follow these steps:

1. Go to **Inventory management** \> **Periodic tasks** \> **Quality management** \> **Quality orders**.
1. Select a quality order, and then, on the Action Pane, select **Quick results entry**.
1. The **Quick results entry** page shows the tests that are associated with the selected quality order. Use the following buttons on the Action Pane to prepare the page for result entry:

    - **New** and **Delete** – Use these buttons to separate the test results that were entered for different quantities. For example, if the quality order quantity is *5*, you can use the **New** button to enter a total of five lines for the test. In this way, a different test result can be entered for each quantity. The sum of the quantities for each test must equal the total quantity of the quality order.
    - **Split** – Split an existing line into multiple lines. This button opens a dialog where you can set the following fields:

        - **Split quantity** – Split the selected line into two lines, one of which has the quantity that you enter here, and the other of which has the remaining quantity. For example, the quantity on the selected line is *8*, and you enter *3* in this field. In this case, the quantity on one of the resulting lines is *3*, and the quantity on the other line is *5*.
        - **Result quantity per line** – Split the selected line into multiple lines, each of which has the specified test quantity. For example, the quantity on the selected is *8*, and you enter *2* in this field. In this case, the line is split into four lines, each of which has a quantity of *2*.

            If the quantity can't be divided evenly, the last line has the remainder that is required to ensure that the total quantity equals the original quantity. For example, the quantity on the selected line is *8*, and you enter *3* in this field. In this case, the line is split into three lines. Each of the first two lines has a quantity of *3*, and the last line has a quantity of *2*, to produce a total quantity of *8*.

            If the item is a catch weight item, you must enter the catch weight quantity instead of the standard quantity.

    - **Skip** – Skip the selected test so that it doesn't affect whether the quality order passes of fails.
    - **Validate** – Validate the selected line, and evaluate whether it passes or fails. This action isn't required. Validation for all rows is automatically done when the page is closed.
    - **Reset test result** – Eliminate the test result for the selected line.

1. Fill in test results for each line.
1. Select the **Back** button to return to the **Quality orders** page.
1. On the Action Pane, select **Validate** to finalize the quality order with the appropriate status, based on the line results (*Pass* or *Fail*).
