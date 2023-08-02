---
# required metadata

title: Parm methods for Segmented Entry controls
description: Describes the parm methods that can be set in code on an instance of a Segmented Entry control.
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
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.assetid: 0090efe3-3fd8-4988-83df-745d25b063d3
ms.search.region: Global
# ms.search.industry: 
ms.author: rcarlson
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Parm methods for Segmented Entry controls

[!include [banner](../includes/banner.md)]

Describes the parm methods that can be set in code on an instance of a Segmented Entry control.

The Segmented Entry control has multiple parm methods that influence how the control will behave. Here is a description of each method.

| Method                               | Description                                                                                                                                                                                                                                                                                                                    |
|--------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| parmDataAreaId                       | The company context that the control is running under. In most cases, the context is `curext()` but there are scenarios where forms can manually set things like different company contexts and surface records from different companies. Forms need to evaluate which context the SEC should be running under the various conditions of the form. |
| parmCurrency                         | This method is used by Account controls for Main account validation. If this property is set, then mainAccount.checkAccountCurrency() is called during Main account validation.                                                                                                                                                       |
| parmControlDate                      | This method is used in validating segment values and in some internal queries. The default is to use the current date but there are scenarios when the form would want to set a custom date based on business requirements.    |
| parmDimensionAutoCompleteFilter      | Adds additional restrictions to filter dimension auto-Complete data.                                                                     |
| parmJournalName                      | This method is used in enforcing Journal control.                |
| parmAccountTypeEnumType              |                                               |
| parmDimensionAccountStorageUsageType | This method allows the form or class to specify how the segmented entry control is being used on the form. This property is of type: DimensionAccountStorageUsage (an enumeration with values: Setup, Transactional, Alias).                                                                                                          |
| parmTaxCode                          | This method was unused and has been removed.                                             |
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
