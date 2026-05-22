---
title: Migrate default dimensions controls to Dimension Entry controls
description: Learn about the steps necessary to migrate default dimensions controls to Dimension Entry controls after code upgrade is run.
author: twheeloc
ms.author: twheeloc
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/27/2026
ms.reviewer: johnmichalak
ms.assetid: 05e85771-44e1-4b0a-8dd2-a878be5a3309
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Migrate default dimensions controls to Dimension Entry controls

[!include [banner](../includes/banner.md)]

This article describes the steps necessary to migrate default dimensions controls to Dimension Entry controls after running code upgrade. It uses the PurchTable form as an example.

## Simple migration scenario - PurchTable form

1. Search for the **PurchTable** form in **Application Explorer**.
1. Add the form to the current project.
1. Open the form in the designer and code editor view.
1. In the form design view:
    1. Locate the dimension entry controls (DECs), either by manually in the control tree or by searching for "DimensionEntry" in the search bar below the **File** tab.
    1. Select the first **DEC** (DimensionEntryControlHeader) and verify the following properties:
        - The type for the control, specified in parenthesis next the control, is Dimension Entry Control.
        - The Controller class property is blank. This property indicates what type of controller the DEC instance uses, which governs the behavior of the control. When this property is blank, the controller is determined by the EDT of the field specified in the **Value Data** field (in this case, the **DefaultDimension** field on the **PurchTable** table). Search for the **PurchTable** table in **Application Explorer**. Right-click **PurchTable** and select **Open Designer**. Expand the **Fields** node and select the **DefaultDimension** field. The EDT property of this field is set to LedgerDefaultDimensionValueSet. This EDT implies that this control uses the LedgerDefaultDimensionEntryController.

    1. Back in the **PurchTable** form design view, select the second `DEC` (DimensionEntryControlLine) and verify the following properties:
        - The type for the control, specified in parenthesis next to the control, is Dimension Entry Control.
        - The Controller class property is blank. The controller is determined by the EDT of the field specified in the **Value Data** Field, as it was for the `DEC`.

1. Switch to the code editor view.
1. Search for all occurrences of "TODO: (Code Upgrade) \[Dimension entry control\]" in the form source code.
1. Go through each of the remaining TODO comments as follows.

## Data source PurchTable

**(Form > Data sources > PurchTable > Methods**)

| Before | After   |
|-------|--------|
| /\* TODO: (Code Upgrade) \[Dimension entry control\] Replace this TODO based on the migration guidance. \*/DimensionEntryControlHeader.reactivate(); | Because this method call doesn't have a parm method called before it, you can delete it. The Dimension Entry Control only needs to be reactivated if the company or displayed dimension set changes. As a general rule with reactivate method calls, if it might not be needed, remove the call and test the control to make sure it works correctly. If it doesn't, add the reactivate call back. |

## Data field OrderAccount

(**Form > Data sources > PurchTable > Fields > OrderAccount > Methods**)

| Before | After   |
|-------|--------|
| /\* TODO: (Code Upgrade) \[Dimension entry control\] Replace this TODO based on the migration guidance. \*/DimensionEntryControlHeader.reactivate(); | Because this method call doesn't have a parm method called before it, you can delete it. The Dimension Entry Control only needs to be reactivated if the company or displayed dimension set changes. |

## Data field ProjId (PurchTable)

(**Form > Data sources > PurchTable > Fields > ProjId > Methods**)

| Before | After   |
|-------|--------|
| /\* TODO: (Code Upgrade) \[Dimension entry control\] Replace this TODO based on the migration guidance. \*/DimensionEntryControlHeader.reactivate(); | Because this method call doesn't have a parm method called before it, you can delete it. The Dimension Entry Control only needs to be reactivated if the company or displayed dimension set changes. You can also delete the entire modified() method because the super() call is all that remains. Remove the ProjId class because it has no methods. |

## Data field VendGroup

(**Form > Data sources > PurchTable > Fields > VendGroup > Methods**)

| Before | After   |
|-------|--------|
| /\* TODO: (Code Upgrade) \[Dimension entry control\] Replace this TODO based on the migration guidance. \*/DimensionEntryControlHeader.reactivate(); | Because this method call doesn't have a parm method that comes before it, you can delete it. The Dimension Entry Control only needs to be reactivated if the company or displayed dimension set changes. You can also delete the entire modified() method and VendGroup class. |

## Data source PurchLine

(**Form > Data sources > PurchLine > Methods**)

| Before | After   |
|-------|--------|
| /\* TODO: (Code Upgrade) \[Dimension entry control\] Replace this TODO based on the migration guidance. \*/DimensionEntryControlLine.reactivate(); **Note:** This method call is in the itemIdModified method on the data source. | Because this method call doesn't have a parm method that comes before it, you can delete it. The Dimension Entry Control only needs to be reactivated if the company or displayed dimension set changes. |
| /\* TODO: (Code Upgrade) \[Dimension entry control\] Replace this TODO based on the migration guidance. \*/DimensionEntryControlLine.reactivate();**Note:** This method call is in the create() method on the data source. | Because this method call doesn't have a parm method that comes before it, you can delete it. The Dimension Entry Control only needs to be reactivated if the company or displayed dimension set changes. |

## Data field AssetGroup

(**Form > Data sources > PurchLine > Fields > AssetGroup > Methods**)

| Before | After   |
|-------|--------|
| /\* TODO: (Code Upgrade) \[Dimension entry control\] Replace this TODO based on the migration guidance. \*/DimensionEntryControlLine.reactivate(); | Because this method call doesn't have a parm method that comes before it, you can delete it. The Dimension Entry Control only needs to be reactivated if the company or displayed dimension set changes. You can also delete the entire modified() method and AssetGroup class. |

## Data field AssetId(**Form &gt; Data sources &gt; PurchLine &gt; Fields &gt; AssetId &gt; Methods**)

| Before | After   |
|-------|--------|
| /\* TODO: (Code Upgrade) \[Dimension entry control\] Replace this TODO based on the migration guidance. \*/DimensionEntryControlLine.reactivate(); | Because this method call doesn't have a parm method called before it, you can delete it. The Dimension Entry Control only needs to be reactivated if the company or displayed dimension set changes. |

## Data field ProcurementCategory

(**Form &gt; Data sources &gt; PurchLine &gt; Fields &gt; ProcurementCategory &gt; Methods**)

| Before        |  After                                        |
|--------|--------------------------------------------------|
| /\* TODO: (Code Upgrade) \[Dimension entry control\] Replace this TODO based on the migration guidance. \*/DimensionEntryControlLine.reactivate(); | Because this method call doesn't have a parm method called before it, you can delete it. The Dimension Entry Control only needs to be reactivated if the company or displayed dimension set changes. |

## Data field ProjId (PurchLine)

(**Form &gt; Data sources &gt; PurchLine &gt; Fields &gt; ProjId &gt; Methods**)

| Before | After   |
|-------|--------|
| /\* TODO: (Code Upgrade) \[Dimension entry control\] Replace this TODO based on the migration guidance. \*/DimensionEntryControlLine.reactivate(); | Because this method call doesn't have a parm method called before it, you can delete it. The Dimension Entry Control only needs to be reactivated if the company or displayed dimension set changes. |

## TabPage TabFinancialDimensionsLine

(Search for TabFinancialDimensionsLine in the search bar below the form tab)

| Before | After   |
|-------|--------|
| /\* TODO: (Code Upgrade) \[Dimension entry control\] This method can be removed if there is no custom implementation \*///dimensionDefaultingControllerLine.pageActivated(); | The pageActivated method no longer needs to be called. You can remove this entire method and the TabFinancialDimensionsLine class because there's no custom logic in the pageActivated method. |

## TabPage TabFinancialDimensionsHeader

(Search for TabFinancialDimensionsHeader in the search bar below the form tab)

| Before | After   |
|-------|--------|
| /\* TODO: (Code Upgrade) \[Dimension entry control\] This method can be removed if there is no custom implementation \*///dimensionDefaultingControllerHeader.pageActivated(); | The pageActivated method no longer needs to be called. You can remove this entire method and the TabFinancialDimensionsHeader class because there's no custom logic in the pageActivated method. |

## Additional resources

- [Uptake of Dimension Entry controls](dimension-entry-control-uptake.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
