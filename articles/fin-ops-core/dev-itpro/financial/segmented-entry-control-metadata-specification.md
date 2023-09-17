---
# required metadata

title: Design-time metadata for Segmented Entry controls
description: Describes the design-time metadata properties for Segmented Entry controls.
author: RyanCCarlson2
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: tfehr
# ms.tgt_pltfrm: 
ms.assetid: b8c5d7a4-ee2b-4ab1-b042-88472b97f035
ms.search.region: Global
# ms.search.industry: 
ms.author: rcarlson
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Design-time metadata for Segmented Entry controls

[!include [banner](../includes/banner.md)]

Describes the design-time metadata properties for Segmented Entry controls.

The custom properties for the Segmented Entry control are found under the Controller group. Here is an example.

[![SEC Property Sheet Example.](./media/capture1.png)](./media/capture1.png)

Certain properties may be non-editable based on the Controller class that is selected. This is because only certain properties are relevant for each of the various controller classes.  For more information, see [Valid properties](#valid-properties).

## Property details

| Property | Valid values   | Usage            |
|----------------|--------------------------|------------------------------------|
| Account Type Field                | A field from the data source.                                                      | Determines the type of account used. Typically used for journal entry from a multi-segment ledger account to single segment values from other backing tables, such as Cust, Vend, Bank, Project, and similar. |
| Controller Class                  | One of 7 Controller classes. For example, LedgerDimensionDefaultAccountController. | Determines the pattern and behavior of the Segmented Entry control.                                                                                                                                          |
| Include Financial Accounts        | NoYes                                                                             | Determines if Main accounts that are Financial accounts are valid for use.                                                                                                                                   |
| Include Total Accounts            | NoYes                                                                             | Determines if Main accounts of type Total are valid for use.                                                                                                                                                 |
| Is Default Account                | TrueFalse                                                                         | For a Dynamic account, determines if the account should be a default or full account.                                                                                                                        |
| Lock Main Account Segment         | NoYes                                                                             | Controls whether the Main account segment is locked.  Typically used in journals and distributions based on configuration.                                                                                   |
| Posting Type                      | A value from the LedgerPostingType enumeration.                                   | The Main account is validated to see if the posting type can be with that account.                                                                                                            |
| Validate Blocked For Manual Entry | NoYes                                                                             | Determines if the 'Blocked for Manual Entry' status on the dimension should be respected.                                                                                                                    |

## Valid properties

The following sections show which properties are valid for each Controller type.

### Validate Blocked For Manual Entry

BudgetLedgerDimension: Yes

BudgetPlanningLedgerDimension: Yes

DimensionDynamicAccount: Yes

LedgerDimensionAccount: Yes

LedgerDimensionDefaultAccount: Yes

LedgerDimensionAccountAlias: Yes

### Account Type Field

BudgetLedgerDimension: No

BudgetPlanningLedgerDimension: No

DimensionDynamicAccount: Yes

LedgerDimensionAccount: No

LedgerDimensionDefaultAccount: No

LedgerDimensionAccountAlias: No

### Is Default Account

BudgetLedgerDimension: No

BudgetPlanningLedgerDimension: No

DimensionDynamicAccount: Yes

LedgerDimensionAccount: No

LedgerDimensionDefaultAccount: No

LedgerDimensionAccountAlias: No

### Lock Main Account Segment

BudgetLedgerDimension: No

BudgetPlanningLedgerDimension: Yes

DimensionDynamicAccount: Yes

LedgerDimensionAccount: Yes

LedgerDimensionDefaultAccount: Yes

LedgerDimensionAccountAlias: No

### Posting Type

BudgetLedgerDimension: No

BudgetPlanningLedgerDimension: Yes

DimensionDynamicAccount: Yes

LedgerDimensionAccount: Yes

LedgerDimensionDefaultAccount: Yes

LedgerDimensionAccountAlias: Yes

### Include Total Accounts

BudgetLedgerDimension: No

BudgetPlanningLedgerDimension: No

DimensionDynamicAccount: Yes

LedgerDimensionAccount: No

LedgerDimensionDefaultAccount: Yes

LedgerDimensionAccountAlias: No

### Include Financial Accounts

BudgetLedgerDimension: No

BudgetPlanningLedgerDimension: No

DimensionDynamicAccount: Yes

LedgerDimensionAccount: No

LedgerDimensionDefaultAccount: Yes

LedgerDimensionAccountAlias: No

## Additional resources

[Support for Segmented Entry controls on dialogs](segmented-entry-control-dialog-support.md)

[Parm methods for Segmented Entry controls](segmented-entry-control-parm-method-specification.md)

[Migrate Segmented Entry controls](segmented-entry-control-conversion.md)

[Migration guidance for Segmented Entry controls](segmented-entry-control-migration-guidance.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
