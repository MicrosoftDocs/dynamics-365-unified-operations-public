---
# required metadata

title: Segmented entry control dialog support
description: Describes the code pattern to add Segmented Entry controls to dialogs.
author: twheeloc
manager: AnnBe
ms.date: 2015-12-12 20 - 44 - 50
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
ms.custom: 25571
ms.assetid: cd09af5e-2e6e-41fd-8e74-6612afb016f5
ms.search.region: Global
# ms.search.industry: 
ms.author: ghenriks
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Segmented entry control dialog support

Describes the code pattern to add Segmented Entry controls to dialogs.

The process to add Segmented Entry controls to dialogs has changed for Microsoft Dynamics 365 for Operations. This is an example from Dynamics AX 2012:

    DialogField dialogFeeLedgerDimension;
    LedgerDimensionAccountController ledgerDimensionAccountController;
    dialogFeeLedgerDimension = dialog.addFieldValue(extendedtypestr(LedgerDimensionAccount),feeLedgerDimension,"@SYS119703");
    ledgerDimensionAccountController = LedgerDimensionAccountController::constructForDialog(dialogFeeLedgerDimension);

In Dynamics 365 for Operations, this code would be converted to:

    DialogField dialogFeeLedgerDimension;
    dialogFeeLedgerDimension = SegmentedEntryControlBuild::addToDialog(
        dialog, 
        classstr(LedgerDimensionAccountController), 
        extendedTypeStr(LedgerDimensionAccount), 
        "@SYS119703", 
        feeLedgerDimension);

For the second parameter, choose the class that satisfies the requirements for your dialog.  The options are:

-   LedgerDimensionAccountController
-   LedgerDimensionDefaultAccountController
-   DimensionDynamicAccountController
-   BudgetLedgerDimensionController
-   BudgetPlanningLedgerDimensionController

This is a simple dialog scenario around Segmented Entry. More advanced scenarios include:

-   Binding the dynamic account type.
-   Company selection support.
-   Account structure selection support.


See also
--------

[Segmented Entry control Metadata Specification](https://ax.help.dynamics.com/en/?p=145441)

[Segmented Entry control Parm method Specification](https://ax.help.dynamics.com/en/?p=154321)

[Segmented Entry control migration walkthrough](https://ax.help.dynamics.com/en/?p=118381)

[Segmented Entry control - Migration guidance](https://ax.help.dynamics.com/en/?p=121441)

