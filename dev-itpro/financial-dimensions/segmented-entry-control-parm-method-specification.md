---
# required metadata

title: Segmented entry control parm methods | Microsoft Docs
description: Describes the parm methods that can be set in code on an instance of a Segmented Entry control.
author: twheeloc
manager: AnnBe
ms.date: 2015-12-12 20:45:42
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: 2051
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 25631
ms.assetid: 1b9be8c9-9573-43a2-ac38-93265d1f1e24
ms.region: Global
# ms.industry: 
ms.author: ghenriks

---

# Segmented entry control parm methods

Describes the parm methods that can be set in code on an instance of a Segmented Entry control.

The Segmented Entry control has multiple parm methods that influence how the control will behave. Here is a description of each method.
| Method                               | Description                                                                                                                                                                                                                                                                                                                    |
|--------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| parmDataAreaId                       | The company context that the control is running under. In most cases this is curext() but there are scenarios where forms can manually set different company contexts, surface records from different companies, etc. Forms need to evaluate which context the SEC should be running under the various conditions of the form. |
| parmCurrency                         | This is used by Account controls for Main account validation. If this property is set, then mainAccount.checkAccountCurrency() is called during Main account validation.                                                                                                                                                       |
| parmControlDate                      | This is used in validating segment values and in some internal queries. The default is to use the current date but there are scenarios when the form would want to set a custom date based on business requirements.                                                                                                           |
| parmDimensionAutoCompleteFilter      | Adds additional restrictions in order to filter dimension autoComplete data.                                                                                                                                                                                                                                                   |
| parmJournalName                      | This is used in enforcing Journal control.                                                                                                                                                                                                                                                                                     |
| parmAccountTypeEnumType              | TBD                                                                                                                                                                                                                                                                                                                            |
| parmDimensionAccountStorageUsageType | This allows the form or class to specify how the segmented entry control is being used on the form. This property is of type: DimensionAccountStorageUsage (an enumeration with values: Setup, Transactional, Alias).                                                                                                          |
| parmTaxCode                          | This was unused and has been removed.                                                                                                                                                                                                                                                                                          |
| parmAccountType                      | TBD                                                                                                                                                                                                                                                                                                                            |
| parmIncludeFinancialAccounts         | Correlates to the design-time property. For more information, see the Segmented Entry control Metadata Specification.                                                                                                                                                                                                          |
| parmIncludeTotalAccounts             | Correlates to the design-time property. For more information, see the Segmented Entry control Metadata Specification.                                                                                                                                                                                                          |
| parmIsDefaultAccount                 | Correlates to the design-time property. For more information, see the Segmented Entry control Metadata Specification.                                                                                                                                                                                                          |
| parmLockMainAccountSegment           | Correlates to the design-time property. For more information, see the Segmented Entry control Metadata Specification.                                                                                                                                                                                                          |
| parmPostingType                      | Correlates to the design-time property.  For more information, see the Segmented Entry control Metadata Specification.                                                                                                                                                                                                         |
| parmValidateBlockedForManualEntry    | Correlates to the design-time property.  For more information, see the Segmented Entry control Metadata Specification.                                                                                                                                                                                                         |



See also
--------

[Segmented Entry control dialog support](https://ax.help.dynamics.com/en/?p=145221)

[Segmented Entry control Metadata Specification](https://ax.help.dynamics.com/en/?p=145441)

[Segmented Entry control migration walkthrough](https://ax.help.dynamics.com/en/?p=118381)

[Segmented Entry control - Migration guidance](https://ax.help.dynamics.com/en/?p=121441)

