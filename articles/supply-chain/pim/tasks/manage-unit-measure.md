--- 
# required metadata 
 
title: Manage unit of measure
description: This procedure shows how to define a unit of measure, provide translations for the unit and it's description, and define conversion rules for related units. 
author: sorenva
manager: AnnBe 
ms.date: 07/08/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: EcoResProductMaintainWorkspace, EcoResProductOpenCasesFormPart, UnitOfMeasure, UnitOfMeasureReportingTranslation, UnitOfMeasureTranslation, UnitOfMeasureConversion, UnitOfMeasureConversionEditOrCreate, UnitOfMeasureLookup   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: sorenand
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Manage unit of measure

[!include [banner](../../includes/banner.md)]

This procedure shows how to define a unit of measure, provide translations for the unit and it's description, and define conversion rules for related units. You can walk through this procedure using demo data, or using your own data.

1. Go to **Navigation pane > Modules > Product information management > Released product maintenance**.
2. Click **Units**.

## Create a unit of measure
1. Click **New**.
2. In the **Unit** field, type a value. Enter the ID or symbol to use when referring to the unit of measure.  
3. In the **Description** field, type a value. Enter a descriptive name for the unit of measure in the system language.  
4. In the **Unit class** field, select an option. The unit class defines what logical grouping, such as area, mass, or quantity, the unit of measure is part of.  
5. In the **Decimal precision** field, enter a number. Specify the number of decimals that the converted unit of measure must be rounded to when a calculation is completed for the unit of measure.  
6. Click **Save**.

## Define unit translations
1. On the **Action pane**, click **Unit texts**.
2. Click **New**. Use unit text to create a translation of the ID or a symbol representing the unit of measure for use on external documents in customer- or vendor-specific languages.  
3. In the **Language** field, enter or select a value.
4. In the **Text** field, type a value.
5. Click **Save**.
6. Close the page.
7. On the **Action pane**, click **Translated unit descriptions**.
8. Click **New**. Define language-specific descriptions for the unit of measure.  
9. In the **Language** field, enter or select a value.
10. In the **Description** field, type a value.
11. Click **Save**.
12. Close the page.

## Define unit conversion rules
1. On the **Action pane**, click **Unit conversions**. Define rules for converting the unit of measure to and from other units of measure in the selected unit class.  
2. Click **New** to open the drop dialog.
3. In the **Factor** field, enter a number. Conversion factor between the From unit and the To unit. For example, the conversion factor from centimeter to meter is 100 because there are 100 centimeters in one meter.  
4. In the **To unit** field, enter or select a value.
5. In the **Rounding** field, select an option. Define how the converted value should be rounded.  
6. Click **OK**.
7. Close the page.

