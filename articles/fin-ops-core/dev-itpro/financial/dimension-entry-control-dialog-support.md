---
title: Support for Dimension Entry controls on dialogs
description: Learn about the code pattern for putting a Dimension Entry control on a dialog, including code examples for old models and current releases.
author: RyanCCarlson2
ms.author: rcarlson
ms.topic: article
ms.date: 02/06/2019
ms.reviewer: kfend
audience: Developer
ms.assetid: ec5f2f8c-eb9b-4fbe-a388-be145b2bf98b
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form:
ms.dyn365.ops.version: AX 7.0.0
---

# Support for Dimension Entry controls on dialogs

[!include [banner](../includes/banner.md)]

Describes the code pattern for putting a Dimension Entry control on a dialog.

The code pattern to add Dimension Entry controls to dialogs has changed from Dynamics AX 2012. This is an example of the old model:

```xpp
DimensionDefaultingControllerNoDS dimDefaultingController;
dimDefaultingController = DimensionDefaultingControllerNoDS::constructInGroupWithValues(true, true, true, 0, _formRun, financialDimensionGroup, "@SYS123456");
dimDefaultingController.setNonActiveValueTolerance(ErrorTolerance::Error);
dimDefaultingController.pageActivated();
dimDefaultingController.loadValues(dimensionAttributeValueSetId);
```

In the current release, this code would be converted to:
    
```xpp
//When you create a dialog
DialogField dimensionEntryField;
DimensionEntryControl dimensionEntryValues;
dimensionEntryField = DimensionEntryControlBuild::addToDialog(dialog, classstr(LedgerDimensionEntryController));

//These lines should be executed after the dialog form is created (for example on “dialogPostRun()” or “postRun()”)
dimensionEntryValues = dimensionEntryField.control();
dimensionEntryValues.parmNonActiveValueErrorTolerance(ErrorTolerance::Error);
dimensionEntryValues.parmDisplayValues(true);
dimensionEntryValues.reactivate();
dimensionEntryValues.loadAttributeValueSet(dimensionAttributeValueSetId);
```

For the second parameter on `addToDialog`, choose the controller class that satisfies the requirements for your dialog.

## Additional resources

[Migrate default dimensions controls to Dimension Entry controls](dimension-entry-control-migration.md)

[Uptake of Dimension Entry controls](dimension-entry-control-uptake.md)





[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
