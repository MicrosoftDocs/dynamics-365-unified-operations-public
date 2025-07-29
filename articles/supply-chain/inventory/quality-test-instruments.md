---
title: Quality management test instruments
description: Learn how to create test instruments that can be used for tests on quality orders in Microsoft Dynamics 365 Supply Chain Management.
author: johanhoffmann
ms.author: johanho
ms.topic: article
ms.date: 03/23/2021
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

## Prerequisites for calibration-related settings (preview)

[!INCLUDE [preview-banner-section](~/../shared-content/shared/preview-includes/preview-banner-section.md)]
<!-- KFM: Preview until 10.0.45 GA -->

Most of the features that are described in this article are available as a standard part of all current versions of Supply Chain Management. However, the calibration-related settings (the **Tag number required**, **Used for calibration**, and **Calibration label layout** fields) add the following requirements:

- You must be running Supply Chain Management version 10.0.44 or later.
- The feature that is named *Advanced quality management* must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

Learn more in [Test instrument calibration (preview)](quality-instrument-calibration.md).

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Create a test instrument

1. Go to **Inventory management \> Setup \> Quality control \> Test instruments**.
1. On the Action Pane, select **New** to add a row to the grid. Then set the following fields for the new row:

    - **Test instrument** – Enter a unique ID or name for the test instrument.
    - **Description** – Enter a detailed description of the test instrument.
    - **Unit** – Select the unit that the instrument measures results in. The **Precision** field is automatically set based on the unit that you select.
    - **Tag number required** – Select this checkbox if a test instrument tag number (in addition to an instrument type) must be specified for the test instrument on quantity orders. The test instrument tag identifies the specific physical instrument that is used in the test. Selection of this checkbox triggers other functionality that is related to tracking and calibration of test instruments. To view, create, and edit the available test instrument tags, select **Test instrument tags** on the Action Pane.
    - **Used for calibration** – Select this checkbox for test instrument types that are used to calibrate other instruments and equipment.
    - **Calibration label layout** – For test instrument types where the **Tag number required** checkbox is selected, select the layout that is used to print calibration labels.

1. Close the page.

## Related information

- [Quality management test](quality-tests.md)
- [Quality management test groups](quality-test-groups.md)
- [Test instrument calibration (preview)](quality-instrument-calibration.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
