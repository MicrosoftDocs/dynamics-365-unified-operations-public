---
# required metadata

title: Dimension entry control migration
description: This topic describes the steps necessary to migrate default dimensions controls to Dimension Entry controls after code upgrade is run. It uses the PurchTable form as an example.
author: twheeloc
manager: AnnBe
ms.date: 2015-12-12 20 - 44 - 25
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
ms.custom: 25531
ms.assetid: f0815049-5eb7-44a5-8b5d-09208857fe70
ms.search.region: Global
# ms.search.industry: 
ms.author: ghenriks
ms.dyn365.ops.intro: Feb-16
ms.dyn365.ops.version: AX 7.0.0

---

# Dimension entry control migration

This topic describes the steps necessary to migrate default dimensions controls to Dimension Entry controls after code upgrade is run. It uses the PurchTable form as an example.

Simple migration scenario - PurchTable form
-------------------------------------------

1.  Search for the **PurchTable** form in the **Application Explorer**.
2.  Add the form to the current project.
3.  Open the form in the designer and code editor view.
4.  In the form design view
    1.  Locate the dimension entry controls (DECs), either by manually in the control tree or by searching for "DimensionEntry" in the search bar below the **File** tab.
    2.  Select the first **DEC** (DimensionEntryControlHeader) and verify the following:
        -   The type for the control, specified in parenthesis next the control, is Dimension Entry Control.
        -   The Controller class property is blank. This property indicates what type of controller will be used by this instance of DEC, which in turn governs the behavior of the control. When this property is blank, the controller is determined by the EDT of the field specified in the **Value Data** field (in this case, the **DefaultDimension** field on the **PurchTable** table). Search for the **PurchTable** table in the Application Explorer. Right-click **PurchTable** and select **Open Designer**. Expand the **Fields** node and select the **DefaultDimension** field. The EDT property of this field is set to LedgerDefaultDimensionValueSet. This EDT implies that this control will use the LedgerDefaultDimensionEntryController.

    3.  Back in the **PurchTable** form design view, select the second **DEC** (DimensionEntryControlLine) and verify the following:
        -   The type for the control, specified in parenthesis next to the control, is Dimension Entry Control.
        -   The Controller class property is blank. The controller will be determined by the EDT of the field specified in the **Value Data** Field, as it was for the DEC.

5.  Switch to the code editor view.
6.  Search for all occurrences of "TODO: (Code Upgrade) \[Dimension entry control\]" in the form source code.
7.  Go through each of the remaining TODO comments as follows.

## Data source PurchTable
**(Form &gt; Data sources &gt; PurchTable &gt; Methods**)

|                                                                                                                                                 |                                                                                                                                                                                                                                                                                                                                                                                                  |
|-------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Before**                                                                                                                                      | **After**                                                                                                                                                                                                                                                                                                                                                                                        |
| /\* TODO: (Code Upgrade) \[Dimension entry control\] Replace this based on the migration guidance. \*/DimensionEntryControlHeader.reactivate(); | Because this method call doesn’t have a parm method called before it, it can be deleted. The Dimension Entry Control only needs to be reactivated if the company or displayed dimension set changes. As a general rule with reactivate method calls, if it may not be needed, remove the call and test the control to make sure it works correctly. If it doesn’t, add the reactivate call back. |

## Data field OrderAccount
(**Form &gt; Data sources &gt; PurchTable &gt; Fields &gt; OrderAccount &gt; Methods**)

|                                                                                                                                                 |                                                                                                                                                                                                      |
|-------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Before**                                                                                                                                      | **After**                                                                                                                                                                                            |
| /\* TODO: (Code Upgrade) \[Dimension entry control\] Replace this based on the migration guidance. \*/DimensionEntryControlHeader.reactivate(); | Because this method call doesn’t have a parm method called before it, it can be deleted. The Dimension Entry Control only needs to be reactivated if the company or displayed dimension set changes. |

## Data field ProjId
(**Form &gt; Data sources &gt; PurchTable &gt; Fields &gt; ProjId &gt; Methods**)

|                                                                                                                                                 |                                                                                                                                                                                                                                                                                                                                                                             |
|-------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Before**                                                                                                                                      | **After**                                                                                                                                                                                                                                                                                                                                                                   |
| /\* TODO: (Code Upgrade) \[Dimension entry control\] Replace this based on the migration guidance. \*/DimensionEntryControlHeader.reactivate(); | Because this method call does not have a parm method called before it, it can be deleted. The Dimension Entry Control only needs to be reactivated if the company or displayed dimension set changes. The entire modified() method can be deleted as well because the super() call is all that remains. The ProjId class can be removed because there are no methods in it. |

## Data field VendGroup
(**Form &gt; Data sources &gt; PurchTable &gt; Fields &gt; VendGroup &gt; Methods**)

|                                                                                                                                                 |                                                                                                                                                                                                                                                                               |
|-------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Before**                                                                                                                                      | **After**                                                                                                                                                                                                                                                                     |
| /\* TODO: (Code Upgrade) \[Dimension entry control\] Replace this based on the migration guidance. \*/DimensionEntryControlHeader.reactivate(); | Because this method call doesn’t have a parm method called before it, it can be deleted. The Dimension Entry Control only needs to be reactivated if the company or displayed dimension set changes. The entire modified() method and VendGroup class can be deleted as well. |

## Data source PurchLine
(**Form &gt; Data sources &gt; PurchLine &gt; Methods**)

|                                                                                                                                                                                                                                            |                                                                                                                                                                                                      |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Before**                                                                                                                                                                                                                                 | **After**                                                                                                                                                                                            |
| /\* TODO: (Code Upgrade) \[Dimension entry control\] Replace this based on the migration guidance. \*/DimensionEntryControlLine.reactivate();**Note:** This is the reactivate method call in the itemIdModified method on the data source. | Because this method call doesn’t have a parm method called before it, it can be deleted. The Dimension Entry Control only needs to be reactivated if the company or displayed dimension set changes. |
| /\* TODO: (Code Upgrade) \[Dimension entry control\] Replace this based on the migration guidance. \*/DimensionEntryControlLine.reactivate();**Note:** This is the reactivate method call in the create() method on the data source.       | Because this method call doesn’t have a parm method called before it, it can be deleted. The Dimension Entry Control only needs to be reactivated if the company or displayed dimension set changes. |

## Data field AssetGroup
(**Form &gt; Data sources &gt; PurhcLine &gt; Fields &gt; AssetGroup &gt; Methods**)

|                                                                                                                                               |                                                                                                                                                                                                                                                                                 |
|-----------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Before**                                                                                                                                    | **After**                                                                                                                                                                                                                                                                       |
| /\* TODO: (Code Upgrade) \[Dimension entry control\] Replace this based on the migration guidance. \*/DimensionEntryControlLine.reactivate(); | Because this method call does not have a parm method called before it, it can be deleted. The Dimension Entry Control only needs to be reactivated if the company or displayed dimension set changes. The entire modified() method and AssetGroup class can be deleted as well. |

## Data field AssetId
(**Form &gt; Data sources &gt; PurchLine &gt; Fields &gt; AssetId &gt; Methods**)

|                                                                                                                                               |                                                                                                                                                                                                       |
|-----------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Before**                                                                                                                                    | **After**                                                                                                                                                                                             |
| /\* TODO: (Code Upgrade) \[Dimension entry control\] Replace this based on the migration guidance. \*/DimensionEntryControlLine.reactivate(); | Because this method call does not have a parm method called before it, it can be deleted. The Dimension Entry Control only needs to be reactivated if the company or displayed dimension set changes. |

## Data field ProcurementCategory
(**Form &gt; Data sources &gt; PurchLine &gt; Fields &gt; ProcurementCategory &gt; Methods**)

|                                                                                                                                               |                                                                                                                                                                                                      |
|-----------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Before**                                                                                                                                    | **After**                                                                                                                                                                                            |
| /\* TODO: (Code Upgrade) \[Dimension entry control\] Replace this based on the migration guidance. \*/DimensionEntryControlLine.reactivate(); | Because this method call doesn’t have a parm method called before it, it can be deleted. The Dimension Entry Control only needs to be reactivated if the company or displayed dimension set changes. |

## Data field ProjId
(**Form &gt; Data sources &gt; PurchLine &gt; Fields &gt; ProjId &gt; Methods**)

|                                                                                                                                               |                                                                                                                                                                                                      |
|-----------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Before**                                                                                                                                    | **After**                                                                                                                                                                                            |
| /\* TODO: (Code Upgrade) \[Dimension entry control\] Replace this based on the migration guidance. \*/DimensionEntryControlLine.reactivate(); | Because this method call doesn’t have a parm method called before it, it can be deleted. The Dimension Entry Control only needs to be reactivated if the company or displayed dimension set changes. |

## TabPage TabFinancialDimensionsLine
(Search for TabFinancialDimensionsLine in the search bar below the form tab)

|                                                                                                                                                                              |                                                                                                                                                                                                 |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Before**                                                                                                                                                                   | **After**                                                                                                                                                                                       |
| /\* TODO: (Code Upgrade) \[Dimension entry control\] This method can be removed if there is no custom implementation \*///dimensionDefaultingControllerLine.pageActivated(); | The pageActivated method no longer needs to be called. This entire method and the TabFinancialDimensionsLine class can be removed because there is no custom logic in the pageActivated method. |

## TabPage TabFinancialDimensionsHeader
(Search for TabFinancialDimensionsHeader in the search bar below the form tab)

|                                                                                                                                                                                |                                                                                                                                                                                                   |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Before**                                                                                                                                                                     | **After**                                                                                                                                                                                         |
| /\* TODO: (Code Upgrade) \[Dimension entry control\] This method can be removed if there is no custom implementation \*///dimensionDefaultingControllerHeader.pageActivated(); | The pageActivated method no longer needs to be called. This entire method and the TabFinancialDimensionsHeader class can be removed because there is no custom logic in the pageActivated method. |



See also
--------

[Dimension Entry control uptake](https://ax.help.dynamics.com/en/?p=154381)

[Dimension Entry control dialog support](https://ax.help.dynamics.com/en/?p=155791)

