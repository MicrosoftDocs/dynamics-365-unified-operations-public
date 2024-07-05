---
title: Support for Segmented Entry controls on dialogs
description: Learn about the code pattern to add Segmented Entry controls to dialogs, including various code examples for legacy and current releases.
author: RyanCCarlson2
ms.author: rcarlson
ms.topic: conceptual
ms.custom: 
  - bap-template
ms.date: 06/19/2024
ms.reviewer: johnmichalak
ms.assetid: cd09af5e-2e6e-41fd-8e74-6612afb016f5
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Support for Segmented Entry controls on dialogs

[!include [banner](../includes/banner.md)]

Describes the code pattern to add Segmented Entry controls to dialogs.

The process to add Segmented Entry controls to dialogs has changed. This code is an example from Dynamics AX 2012:

```xpp
DialogField dialogFeeLedgerDimension;
LedgerDimensionAccountController ledgerDimensionAccountController;
dialogFeeLedgerDimension = dialog.addFieldValue(extendedtypestr(LedgerDimensionAccount),feeLedgerDimension,"@SYS119703");
ledgerDimensionAccountController = LedgerDimensionAccountController::constructForDialog(dialogFeeLedgerDimension);
```

In the current release, this code would be converted to:

```xpp
DialogField dialogFeeLedgerDimension;
dialogFeeLedgerDimension = SegmentedEntryControlBuild::addToDialog(
    dialog, 
    classstr(LedgerDimensionAccountController), 
    extendedTypeStr(LedgerDimensionAccount), 
    "@SYS119703", 
    feeLedgerDimension);
```

For the second parameter, choose the class that satisfies the requirements for your dialog.  The options are:

-   LedgerDimensionAccountController
-   LedgerDimensionDefaultAccountController
-   DimensionDynamicAccountController
-   BudgetLedgerDimensionController
-   BudgetPlanningLedgerDimensionController

This scenario is a simple dialog scenario around Segmented Entry. More advanced scenarios include:

-   Binding the dynamic account type.
-   Company selection support.
-   Account structure selection support.


## Additional resources

[Design-time metadata for Segmented Entry controls](segmented-entry-control-metadata-specification.md)

[`Parm` methods for Segmented Entry controls](segmented-entry-control-parm-method-specification.md)

[Migrate Segmented Entry controls](segmented-entry-control-conversion.md)

[Migration guidance for Segmented Entry controls](segmented-entry-control-migration-guidance.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
