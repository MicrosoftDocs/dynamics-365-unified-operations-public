---
title: Parm methods for Segmented Entry controls
description: Learn about the parm methods that can be set in code on an instance of a Segmented Entry control, including a table that defines various methods.
author: twheeloc
ms.author: twheeloc
ms.topic: article
ms.custom: 
  - bap-template
ms.date: 03/27/2026
ms.reviewer: johnmichalak
ms.assetid: 0090efe3-3fd8-4988-83df-745d25b063d3
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Parm methods for Segmented Entry controls

[!include [banner](../includes/banner.md)]

Describes the parm methods that you can set in code on an instance of a Segmented Entry control.

The Segmented Entry control has multiple parm methods that influence how the control behaves. Here's a description of each method.

| Method                               | Description                                                                                                                                                                                                                                                                                                                    |
|--------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| parmDataAreaId                       | The company context that the control runs under. In most cases, the context is `curext()`, but there are scenarios where forms can manually set different company contexts and surface records from different companies. Forms need to evaluate which context the SEC should run under the various conditions of the form. |
| parmCurrency                         | Account controls use this method for main account validation. If you set this property, the system calls `mainAccount.checkAccountCurrency()` during main account validation.                                                                                                                                                       |
| parmControlDate                      | This method is used in validating segment values and in some internal queries. The default is to use the current date but there are scenarios when the form would want to set a custom date based on business requirements.    |
| parmDimensionAutoCompleteFilter      | Adds extra restrictions to filter dimension auto-complete data.                                                                     |
| parmJournalName                      | This method is used in enforcing Journal control.                |
| parmAccountTypeEnumType              |                                               |
| parmDimensionAccountStorageUsageType | This method allows the form or class to specify how the segmented entry control is being used on the form. This property is of type: DimensionAccountStorageUsage (an enumeration with values: Setup, Transactional, Alias).                                                                                                          |
| parmTaxCode                          | This method was unused and is removed.                                             |
| parmAccountType                      |  |
| parmIncludeFinancialAccounts         | Correlates to the design-time property. For more information, see the Segmented Entry control Metadata Specification.                                                                                                                                                                                                          |
| parmIncludeTotalAccounts             | Correlates to the design-time property. For more information, see the Segmented Entry control Metadata Specification.                                                                                                                                                                                                          |
| parmIsDefaultAccount                 | Correlates to the design-time property. For more information, see the Segmented Entry control Metadata Specification.                                                                                                                                                                                                          |
| parmLockMainAccountSegment           | Correlates to the design-time property. For more information, see the Segmented Entry control Metadata Specification.                                                                                                                                                                                                          |
| parmPostingType                      | Correlates to the design-time property.  For more information, see the Segmented Entry control Metadata Specification.                                                                                                                                                                                                         |
| parmValidateBlockedForManualEntry    | Correlates to the design-time property.  For more information, see the Segmented Entry control Metadata Specification.                                                                                                                                                                                                         |

## Additional resources

[Support for Segmented Entry controls on dialogs](segmented-entry-control-dialog-support.md)

[Design-time metadata for Segmented Entry controls](segmented-entry-control-metadata-specification.md)

[Migrate Segmented Entry controls](segmented-entry-control-conversion.md)

[Migration guidance for Segmented Entry controls](segmented-entry-control-migration-guidance.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
