---
# required metadata

title: Dimension Entry control dialog support
description: Describes the code pattern for putting a Dimension Entry control on a dialog.
author: twheeloc
manager: AnnBe
ms.date: 2015-12-12 23 - 48 - 02
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 2051
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 26321
ms.assetid: fb470d0d-7b44-4bba-993f-e4883f219f09
ms.search.region: Global
# ms.search.industry: 
ms.author: ghenriks
ms.dyn365.ops.intro: Feb-16
ms.dyn365.ops.version: AX 7.0.0

---

# Dimension Entry control dialog support

Describes the code pattern for putting a Dimension Entry control on a dialog.

The code pattern to add Dimension Entry controls to dialogs has changed for Microsoft Dynamics 365 for Operations. This is an example of the old model:

    DimensionDefaultingControllerNoDS dimDefaultingController;
    dimDefaultingController = DimensionDefaultingControllerNoDS::constructInGroupWithValues(true, true, true, 0, _formRun, financialDimensionGroup, "@SYS123456");
    dimDefaultingController.setNonActiveValueTolerance(ErrorTolerance::Error);
    dimDefaultingController.pageActivated();
    dimDefaultingController.loadValues(dimensionAttributeValueSetId);

In Dynamics 365 for Operations, this code would be converted to:

    DialogField dimensionEntryField;
    DimensionEntryControl dimensionEntryValues;
    dimensionEntryField = DimensionEntryControlBuild::addToDialog(dialog, classstr(LedgerDimensionEntryController));
    dimensionEntryValues = dimensionEntryField.control();
    dimensionEntryValues.parmNonActiveValueErrorTolerance(ErrorTolerance::Error);
    dimensionEntryValues.parmDisplayValues(true);
    dimensionEntryValues.reactivate();
    dimensionEntryValues.loadAttributeValueSet(dimensionAttributeValueSetId);

For the second parameter on `addToDialog`, choose the controller class that satisfies the requirements for your dialog.

See also
--------

[Dimension Entry control migration walkthrough](https://ax.help.dynamics.com/en/?p=175861)

[Dimension Entry control uptake](https://ax.help.dynamics.com/en/?p=154381)

