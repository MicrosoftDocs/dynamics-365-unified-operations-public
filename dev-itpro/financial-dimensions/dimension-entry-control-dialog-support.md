---
# required metadata

title: Dimension Entry control dialog support
description: Describes the code pattern for putting a Dimension Entry control on a dialog.
author: annbe
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
ms.reviewer: annbe
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 26321
ms.assetid: 2f446cae-4b0b-4db0-bb23-0953a371a2a0
ms.search.region: Global
# ms.search.industry: 
ms.author: annbe
ms.dyn365.intro: Feb-16
ms.dyn365.version: AX 7.0.0

---

# Dimension Entry control dialog support

Describes the code pattern for putting a Dimension Entry control on a dialog.

The code pattern to add Dimension Entry controls to dialogs has changed for Microsoft Dynamics AX. This is an example of the old model:

    DimensionDefaultingControllerNoDS dimDefaultingController;
    dimDefaultingController = DimensionDefaultingControllerNoDS::constructInGroupWithValues(true, true, true, 0, _formRun, financialDimensionGroup, "@SYS123456");
    dimDefaultingController.setNonActiveValueTolerance(ErrorTolerance::Error);
    dimDefaultingController.pageActivated();
    dimDefaultingController.loadValues(dimensionAttributeValueSetId);

In Dynamics AX, this code would be converted to:

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

