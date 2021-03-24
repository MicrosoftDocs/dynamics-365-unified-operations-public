---
# required metadata

title: Quality management test instruments
description: This topic describes how you can use and create test instruments for use with tests on quality orders in Dynamics 365 Supply Chain Management.
author: rachel-profitt
manager: tfehr
ms.date: 03/23/2021
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata

ms.search.form: InventTestInstrument
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: kamaybac
# ms.tgt_pltfrm:
ms.custom: 94003
ms.assetid: a1d9417b-268f-4334-8ab6-8499d6c3acf0
ms.search.region: Global
ms.search.industry: Distribution
ms.author: raprofit
ms.search.validFrom: 2020-06-17
ms.dyn365.ops.version: AX 7.0.0

---

# Quality management test instruments

[!include [banner](../includes/banner.md)]

This topic describes how to use and create test instruments for use with tests on quality orders in Dynamics 365 Supply Chain Management.

Use the **Test instruments** page to define and view the devices that will be used for performing tests on quality orders. Test instruments are optional; however, they allow you to define details about the devices or tools that will be used to perform a test. This additional information can be useful for the quality workers performing the tests to know which device or tool to use in order to perform a specific test.

## Test instrument example

You are performing a variety of tests on electrical components. Some tests are for the voltage output of the components, one test for temperature of the device, and another test for the weight. Each of these tests are performed using different tools, devices, or equipment. For example, a voltage meter to measure voltage, a thermometer to measure temperature, and a scale to measure the weight. Each of these devices can be configured as test instruments and indicate the unit of measure that the test results will be recorded in. For example, volts for the voltage meter, fahrenheit or centigrade for the thermometer, and pounds or kilograms for the scale.

## Create a test instrument

1. Go to **Inventory management > Setup > Quality control > Test instruments**.
1. Select **New** on the Action Pane to add a new row to the grid and then make the following settings for it:
    - **Test instrument** - Enter a unique ID or name for the test instrument.
    - **Description** - Enter a detailed description for the test instrument.
    - **Unit** - Select the unit the instrument measures results in. The **Precision** field will automatically populate with the unit of measure precision based on the selected unit.
1. Close the page.

## Additional resources

- [Quality management test](quality-tests.md)
- [Quality management test groups](quality-test-groups.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]