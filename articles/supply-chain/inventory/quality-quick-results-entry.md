---
title: Enter quality test results quickly (preview)
description: Learn how to use the quick result entry page, which consolidates data from all tests into a single view to streamline the entry process.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: InventQualityOrderTable, QMSInventQualityOrderLineResults
ms.topic: how-to
ms.date: 04/25/2025
ms.custom: 
  - bap-template
---

# Enter quality test results quickly (preview)

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

The **Quick result entry** page adds speed and flexibility when entering quality order test results (compared to using the **Quality order line results** page). The **Quick result entry** page consolidates data from all tests into a single view, which streamlines the result-entry process. Quantities are automatically populated based on the quality order quantities, along with other details such as minimum, maximum, and target values.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.44 or later.
- The feature that is named *(Preview) Advanced quality management* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). <!-- KFM-AQM: more here? right FM? -->

## Enter quality test results

To enter quality test results using the **Quick result entry** page, follow these steps:

1. Go to **Inventory management** \> **Periodic tasks** \> **Quality management** > **Quality orders**.
1. Select a quality order and then select **Quick result entry** on the Action Pane.
1. The **Quick result entry** page opens, showing the tests that are associated with the selected quality order. Use the following buttons on the Action Pane to prepare the form for entering results:

    - **New** and **Delete** – Use these options to separate the test results entered for different quantities. For example, if the quality order quantity is *5*, using the **New** action, a total of five lines can be entered for that test so that a different test result can be entered for each quantity. The sum of the quantities for each test must still equal the total quantity of the quality order. 
    - **Split** - Split an existing line into multiple lines. This button opens a dialog where you can specify the following options:
        - **Split quantity** – Split the selected line into two lines, with one line containing the quantity specified here and the second line containing the remaining quantity. For example, if the line quantity was *8* you enter *3* int this field, the result will be two lines, one with quantity of *3* and one with a quantity of *5*.
        - **Result quantity per line** – Split the selected line into multiple lines, each containing the specified test quantity. For example, if the current line has a quantity of *8* and you enter *2* here, the line is split into four lines, each with quantity *2*. If the quantity doesn't divide evenly, the last row will contain the remainder required to ensure the total quantity remains the same as the original quantity. For example, if the current line has a quantity of *8* and you set this field to *3*, the system creates three result lines, two lines with the quantity of *3* and the third line with the residual quantity of *2* for a total quantity of *8*. If the item is a catch weight item, you must enter the catch weight quantity instead of the standard quantity.
    - **Skip** – Skip the selected test so that it doesn't affect whether the quality order passes of fails.
    - **Validate** – Validate the selected line. This action also evaluates whether the line is passes or fails. This action is not required. Validation for all rows is performed automatically when the form is closed.
    - **Reset test result** – Eliminates the test result for the selected line.

1. Fill out test results for each line.
1. Select the Back button to return to the **Quality orders** page.
1. On the Action Pane, select **Validate** to finalize the quality order with the appropriate status based on the line results (*Pass* or *Fail*).
