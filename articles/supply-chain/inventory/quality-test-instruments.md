---
title: Quality management test instruments
description: Learn how to create test instruments that can be used for tests on quality orders in Microsoft Dynamics 365 Supply Chain Management.
author: johanhoffmann
ms.author: johanho
ms.topic: article
ms.date: 10/24/2025
ms.reviewer: kamaybac
ms.search.form: InventTestInstrument
ms.assetid: a1d9417b-268f-4334-8ab6-8499d6c3acf0
---

# Quality management test instruments

[!include [banner](../includes/banner.md)]

This article describes how to create test instruments or instrument types that can be used for tests on quality orders in Microsoft Dynamics 365 Supply Chain Management.

You use the **Test instruments** page to define and view details about the instruments or instrument types that are used to perform tests on quality orders. Test instruments are optional. However, they can help quality workers determine which device or tool they should use to perform a specific test.

## Test instrument example

You're performing various tests on electrical components. Some tests are for the voltage output of the components, one test is for their temperature, and one test is for their weight. Different tools, devices, or equipment are used to perform each test. For example, a voltage meter is used to measure voltage, a thermometer is used to measure temperature, and a scale is used to measure weight. You can configure each of these device types as a test instrument and indicate the unit of measure that the test results should be recorded in. For example, results from a voltage meter are recorded in volts, results from a thermometer are recorded in degrees Fahrenheit or degrees Celsius, and results from a scale are recorded in pounds or kilograms.

## Prerequisites for calibration-related settings

Most of the features that are described in this article are available as a standard part of all current versions of Supply Chain Management. However, the calibration-related settings (the **Tag number required**, **Used for calibration**, and **Calibration label layout** fields) add the following requirements:

- You must be running Supply Chain Management version 10.0.44 or later.
- The feature that is named *Advanced quality management* must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

Learn more in [Test instrument calibration](quality-instrument-calibration.md).

## Create a test instrument

1. Go to **Inventory management \> Setup \> Quality control \> Test instruments**.
1. On the Action Pane, select **New** to add a row to the grid. Then set the following fields for the new row:

    - **Test instrument** – Enter a unique ID or name for the test instrument.
    - **Description** – Enter a detailed description of the test instrument.
    - **Unit** – Select the unit that the instrument measures results in. The **Precision** field is automatically set based on the unit that you select.
    - **Tag number required** – Select this checkbox if a test instrument tag number (in addition to an instrument type) must be specified for the test instrument on quantity orders. The test instrument tag identifies the specific physical instrument that is used in the test. Selection of this checkbox triggers other functionality that is related to tracking and calibration of test instruments. To view, create, and edit the available test instrument tags, select **Test instrument tags** on the Action Pane.
    - **Used for calibration** – Select this checkbox for test instrument types that are used to calibrate other instruments and equipment.
    - **Calibration label layout** – For test instrument types where the **Tag number required** checkbox is selected, select the layout that is used to print calibration labels.

    The below fields are only applicable when using asset management for managing test instruments. The fields are only enabled if the field **Tag number required** is selected.

    - **Asset type** - Link a test instrument type to an asset type to manage its tags using Asset Management. Calibration can be scheduled with time-based maintenance plans or, optionally, usage-based plans by linking a counter. To enable usage-based calibration, select a counter and link maintenance plan lines to it. All tags must be linked to assets.
    - **Test quantity counter type** - In asset management, a counter is a measurement mechanism that tracks values related to an asset over time. These values help plan maintenance and monitor equipment condition. Users can flexible define counters and relate them to asset types. Learn more about counters in:  ([Counters](../asset-management/setup-for-objects/counters.md)). Use the **Test quantity counter type** field to select a counter that should be incremented when a quality order is being validated. The system will increment the counter with the quantity that has been tested on the quality order. 
    - **Fixed increment counter type** - In asset management, a counter is a measurement mechanism that tracks values related to an asset over time. These values help plan maintenance and monitor equipment condition. Users can flexible define counters and relate them to asset types. Learn more about counters in:  ([Counters](../asset-management/setup-for-objects/counters.md)). Use the **Fixed increment counter type** field in to select a counter that should be incremented when a quality order is being validated. The counter will be incremented with the value specified in the field **Usage increment**.
    - **Usage increment** - If you chose a fixed increment counter type, then enter the value by which to increment the asset counter when a quality order is validated.
    - **Calibration state** - When an asset that is linked to the asset type specified on the record changes status to the value set in the **Calibration state**, the related test instrument tag is automatically set to *Calibration*. Learn more about asset stages in [Asset lifecycle states](../asset-management/setup-for-objects/object-stages.md).
    - **Out of service state** - When an asset, that is linked to the asset type specified on the line change status to the value set in **Out of service state** field changes status to the value set in the **Calibration state**, the related test instrument tag is automatically set to *Out of service*. Learn more about asset stages in [Asset lifecycle states](../asset-management/setup-for-objects/object-stages.md).
    - **Auto-create test instrument tag from asset** - Select this check box to automatically create a test instrument tag when you create a new asset of the linked **Asset type** (existing assets are not affected).

1. Close the page.

## Related information

- [Quality management test](quality-tests.md)
- [Quality management test groups](quality-test-groups.md)
- [Test instrument calibration](quality-instrument-calibration.md)
- [Calibrate test instruments with Asset Management (preview)](../asset-management/preventive-and-reactive-maintenance/asset-management-test-instrument-calibration.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
