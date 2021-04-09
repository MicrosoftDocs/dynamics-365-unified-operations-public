--- 
# required metadata 
 
title: Manage units of measure
description: This topic describes how to define a unit of measure, provide translations for the unit and it's description, and define conversion rules for related units.
author: sorenva
ms.date: 04/09/2021
ms.topic: business-process 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: EcoResProductMaintainWorkspace, EcoResProductOpenCasesFormPart, UnitOfMeasure, UnitOfMeasureReportingTranslation, UnitOfMeasureTranslation, UnitOfMeasureConversion, UnitOfMeasureConversionEditOrCreate, UnitOfMeasureLookup, UnitOfMeasureCalculator, UnitOfMeasureWizard, UnitOfMeasureLookupTest
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: sorenand
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Manage units of measure

[!include [banner](../../includes/banner.md)]

This topic describes how to define a unit of measure, provide translations for the unit and it's description, and define conversion rules for related units.

## Open the units page

To create and work with the units of measure available on your system, go to **Organization administration \> Setup \> Units \> Units**.

The remaining sections of this topic describe what you can do here.

## Create standard units and conversions

If your system doesn't already include the most commonly used units of measure for the metric and/or United States unit systems, the unit setup wizard can help you get started quickly with basic unit definitions and conversions. To run the wizard, select **Unit creation wizard** from the Action Pane and then follow the instructions on your screen.

## Create or edit a unit of measure

To create or edit a unit of measure:

1. Do one of the following:
    - To edit an existing unit, select it on the list pane.
    - To create a new unit, select **New** on the Action Pane.
1. In the **Unit** field, enter the ID or symbol to use when referring to the unit of measure in the system language.  
1. In the **Description** field, enter a descriptive name for the unit of measure in the system language.  
1. In the **Unit class** field, select the type of thing the unit measures (such as length, area, mass, or quantity).  
1. In the **System of units** field, select which measurement system the unit belongs to (*Metric  units* or *United States customary units*).
1. In the **Decimal precision** field, specify the number of decimals to round to when specifying quantities or converting to this unit.
1. On the Action Pane, select **Save**.

## Define unit translations

To define language translations for unit symbols and descriptions:

1. Create or select the unit you want to create translations for.
1. On the Action Pane, select **Unit texts**.
1. The **Unit texts** page opens. Unit texts establish a translation of the unit ID or symbol that for use on external documents in customer- or vendor-specific languages.
1. On the Action Pane, select **New**.
1. In the **Language** field, select the language you want to translate to.
1. In the **Text** field, enter the translated ID or a symbol for this unit in the selected language.
1. On the Action Pane, select **Save**.
1. Close the page.
1. On the **Action Pane**, select **Translated unit descriptions**.
1. The **Translated unit descriptions** page opens. Use this page to define language-specific descriptions for the unit of measure.
1. On the Action Pane, select **New**.
1. In the **Language** field, select the language you want to translate to.
1. In the **Description** field, enter the translated description.
1. On the Action Pane, select **Save**.
1. Close the page.

## Define unit conversion rules

To define rules for converting between different units:

1. Create or select the unit you want to create translations for.
1. On the Action Pane, select **Unit conversions**.
1. The **Unit conversions page** opens. Use this page to define rules for converting the unit of measure to and from other units of measure in the selected unit class.
1. Depending on which type of conversion you want to set up, select one of the following tabs:
    - **Standard conversions** – Set up standard conversion rules for all products.
    - **Intra-class conversions** – Set up product-specific conversion rules for units of measure in the same unit class.
    - **Inter-class conversions** – Set up product-specific conversion rules for units of measure across unit classes.
1. Do one of the following:
    - To create a new conversions, select **New** from the tab toolbar.
    - To edit an existing conversion, select the conversion in the grid and select **Edit** from the tab toolbar.
1. A drop-down dialog opens. Make the following settings:
    - **Product** – Select the specific product your conversion applies to. This is only available for intra-class and inter-class conversions.
    - **Formula layout** – Leave this set to *Simple* to specify a simple conversion with a single factor. Set this to *Advanced* to set up a more complex equation. The format for advanced equations varies according to the unit class.
    - **From unit** – This already shows your selected unit. Usually, you shouldn't change it (if you do, you will need to open the **Unit conversions** page for the selected unit to see your new conversion after you save it).
    - **To unit** – Select the unit you want to convert to.
    - **Rounding** - Choose how fractions should be rounded based on the **Decimal precision** of your selected unit (*To nearest*, *Up*, or *Down*).
    - **Conversion formula** - Use the remaining fields at the top of the drop-down dialog to specify the formula for converting between the two units. The fields available depend on the unit class and formula layout you have selected.
1. Select **OK**.
1. Close the page.

> [!TIP]
> It's also possible to set up unit conversions per product variant. To learn how, see [Unit of measure conversion per product variant](../uom-conversion-per-product-variant.md).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]