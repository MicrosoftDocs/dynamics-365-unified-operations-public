---
# required metadata

title: Quality management test instruments
description: This article describes how to create test instruments that can be used for tests on quality orders in Microsoft Dynamics 365 Supply Chain Management.
author: yufeihuang
ms.date: 03/23/2021
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

ms.search.form: InventTestInstrument
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: kamaybac
# ms.tgt_pltfrm:
ms.assetid: a1d9417b-268f-4334-8ab6-8499d6c3acf0
ms.search.region: Global
ms.search.industry: Distribution
ms.author: yufeihuang
ms.search.validFrom: 2020-06-17
ms.dyn365.ops.version: AX 7.0.0

---

# Quality management test instruments

[!include [banner](../includes/banner.md)]

This article describes how to create test instruments that can be used for tests on quality orders in Microsoft Dynamics 365 Supply Chain Management.

You use the **Test instruments** page to define and view details about the devices that are used to perform tests on quality orders. Test instruments are optional. However, they can help quality workers know which device or tool they should use to perform a specific test.

## Test instrument example

You're performing various tests on electrical components. Some tests are for the voltage output of the components, one test is for their temperature, and one test is for their weight. Different tools, devices, or equipment is used to perform each test. For example, a voltage meter is used to measure voltage, a thermometer is used to measure temperature, and a scale is used to measure weight. You can configure each of these devices as a test instrument and indicate the unit of measure that the test results should be recorded in. For example, results from the voltage meter are recorded in volts, results from the thermometer are recorded in degrees Fahrenheit or degrees Celsius, and results from the scale are recorded in pounds or kilograms.

## Create a test instrument

1. Go to **Inventory management \> Setup \> Quality control \> Test instruments**.
1. On the Action Pane, select **New** to add a row to the grid. Then set the following fields for the new row:

    - **Test instrument** – Enter a unique ID or name for the test instrument.
    - **Description** – Enter a detailed description of the test instrument.
    - **Unit** – Select the unit that the instrument measures results in. The **Precision** field is automatically set, based on the unit that you select.

1. Close the page.

## Additional resources

- [Quality management test](quality-tests.md)
- [Quality management test groups](quality-test-groups.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
