---
title: Manage units of measure
description: This article describes how to define a unit of measure, provide translations for the unit and its description, and define conversion rules for related units.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form: EcoResProductMaintainWorkspace, EcoResProductOpenCasesFormPart, UnitOfMeasure, UnitOfMeasureReportingTranslation, UnitOfMeasureTranslation, UnitOfMeasureConversion, UnitOfMeasureConversionEditOrCreate, UnitOfMeasureLookup, UnitOfMeasureCalculator, UnitOfMeasureWizard, UnitOfMeasureLookupTest
ms.topic: how-to
ms.date: 12/08/2022
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Manage units of measure

[!include [banner](../../includes/banner.md)]

This article describes how to define a unit of measure, provide translations for the unit and its description, and define conversion rules for related units.

## Open the Units page

To create and work with the units of measure that are available in your system, go to **Organization administration \> Setup \> Units \> Units**.

The remaining sections of this article describe what you can do on the **Units** page.

## Create standard units and conversions

If your system doesn't already include the most commonly used units of measure for the metric system and/or the US customary system (USCS), the unit setup wizard can help you quickly get started with basic unit definitions and conversions. To complete the wizard, select **Unit creation wizard** on the Action Pane, and then follow the on-screen instructions.

## Create or edit a unit of measure

To create or edit a unit of measure, follow these steps.

1. Follow one of these steps:

    - To edit an existing unit, select it in the list pane.
    - To create a new unit, select **New** on the Action Pane.

1. On the header of the record, set the following fields:

    - **Unit** – Enter the ID or symbol to use to refer to the unit in the system language. This ID or symbol is usually a common abbreviation for the unit, such as *ea* for each or *cm* for centimeter.
    - **Description** – Enter a descriptive name for the unit in the system language. This name is usually the full name of the unit, such as *Each* or *Centimeter*.

1. On the **General** FastTab, set the following fields:<!-- KFM: confirm this:    - **Fixed unit assignment** and **Fixed unit** – These fields have an effect only if you're using the Microsoft Retail Essentials product. If the current unit can be mapped to one of the fixed units that are used by Retail Essentials, set the **Fixed unit assignment** option to *Yes*. Then select the fixed unit in the **Fixed unit** field. -->

    - **Unit class** – Select the property that the unit measures (such as length, area, mass, or quantity).
    - **System of units** – Select the measurement system that the unit belongs to (*Metric units* or *United States customary units*).
    - **Base unit** – Set this option to *Yes* to use the current unit as the base unit for its unit class. In this case, you only have to specify the conversion factor between the base unit and each additional unit in the unit class. The system can then convert between all units in that unit class. Therefore, it's easier to set up conversions.

        For example, if gallon is the base unit for the *Volume* unit class, you only have to set up conversion factors from quart to gallon and from pint to gallon. The system can then also convert from quart to pint.

        You can have only one base unit per unit class.

    - **System unit** – Set this option to *Yes* to use the current unit as the assumed unit for all unspecified measurements in its unit class. For example, if a field that is used to enter a quantity doesn't allow a unit to be specified (of if the user doesn't select a unit), the system uses the unit that is set as the system unit for the *Quantity* unit class. You can have only one system unit per unit class.
    - **Decimal precision** – Specify the number of decimal places that values that are specified for the current unit or converted to it should be rounded to.

1. On the Action Pane, select **Save**.

## Define unit translations

To define translations for the ID or symbol and the description for a unit of measure, follow these steps.

1. Create or select the unit to create translations for.
1. On the Action Pane, select **Unit texts**.

    The **Unit texts** page appears. You use this page to define translations for the ID or symbol for the selected unit. Those translations can then be used on external documents in customer-specific or vendor-specific languages.

1. On the Action Pane, select **New**.
1. In the **Language** field, select the language to translate the unit ID or symbol to.
1. In the **Text** field, enter the translation of the unit ID or symbol in the selected language.
1. On the Action Pane, select **Save**.
1. Close the page.
1. On the **Action Pane**, select **Translated unit descriptions**.

    The **Translated unit descriptions** page appears. You use this page to define language-specific descriptions for the selected unit.

1. On the Action Pane, select **New**.
1. In the **Language** field, select the language to translate the unit description to.
1. In the **Description** field, enter the translation of the unit description in the selected language.
1. On the Action Pane, select **Save**.
1. Close the page.

## Define unit conversion rules

To define rules for conversions between units of measure, follow these steps.

1. Create or select the unit to define conversion rules for.
1. On the Action Pane, select **Unit conversions**.

    The **Unit conversions** page appears. You use this page to define rules for converting the selected unit to and from other units in the unit class.

1. Select one of the following tabs, depending on the type of conversion that you want to set up:

    - **Standard conversions** – Set up standard conversion rules for all products.
    - **Intra-class conversions** – Set up product-specific conversion rules for units in the same unit class.
    - **Inter-class conversions** – Set up product-specific conversion rules for units across unit classes.

1. Follow one of these steps:

    - To create a new conversion, select **New** on the toolbar.
    - To edit an existing conversion, select the conversion in the grid, and then select **Edit** on the toolbar.

1. In the drop-down dialog box that appears, set the following fields:

    - **Product** – Select the specific product that the conversion applies to. This field is available only for intra-class and inter-class conversions.
    - **Formula layout** – Leave this field set to *Simple* to specify a simple conversion that has a single factor. Set it to *Advanced* to set up a more complex equation. The format for advanced equations varies, depending on the unit class.
    - **From unit** – This field shows the selected unit. Usually, you shouldn't change the value. (If you do change the value, you must open the **Unit conversions** page for the selected unit to view your new conversion after you save it.)
    - **To unit** – Select the unit to convert to.
    - **Rounding** – Select how fractions should be rounded, based on the **Decimal precision** value of the selected unit (*To nearest*, *Up*, or *Down*).
    - **Conversion formula** – Use the remaining fields at the top of the drop-down dialog box to specify the formula for converting between the two units. The available fields vary, depending on the unit class and formula layout that you've selected.

1. Select **OK**.
1. Close the page.

> [!TIP]
> You can also set up unit conversions per product variant. For more information, see [Unit of measure conversion per product variant](../uom-conversion-per-product-variant.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
