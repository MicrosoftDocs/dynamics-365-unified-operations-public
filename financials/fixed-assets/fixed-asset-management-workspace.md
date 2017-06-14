---
# required metadata

title: Fixed asset management workspace
description: This topic provides information about the Fixed asset management workspace. This workspace shows information that is related to the fixed assets that are entered in the system. It includes a summary view and an analytics view.
author: saraschi
manager: AnnBe
ms.date: 06/06/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Application User
# ms.devlang: 
# ms.reviewer: twheeloc
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
# ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: Enterprise edition, July 2017 update

---

# Fixed asset management workspace

[!include[banner](../includes/banner.md)]

The **Fixed asset management** workspace shows information that is related to fixed assets that are entered in the system. This workspace includes a summary view and an analytics view. The **My work** tab shows summary tiles, fixed asset details, and related information about fixed assets in the current company. You can also add analytics to the Power BI analytics section directly in the workspace. The **Analytics – all companies** tab uses capabilities of Microsoft Power BI to show visuals that are related to fixed assets in all companies.

## My work

### Summary

The tiles in the **Summary** section give an overview of your fixed assets. The information includes metrics about assets that aren't yet acquired, assets that have been acquired during the current year, and assets that have been disposed of during the current year. The **Summary** section also has quick navigation to the **Fixed asset** list page, batch depreciation proposal, and fixed asset journal.

### Find fixed assets

The **Find fixed assets** section lets you quickly search for assets by providing the fixed asset number, group, name, location, or person who is responsible. All assets that match the search criteria will appear in the list.

From the list, you can view the following pages:

 - **Details** page for the fixed asset
 - **Books** page for all books that are associated with the fixed asset
 - **Fixed asset valuations** page

### Valuations

The **Fixed asset valuations** page lets you see, on one page, the most important information about a fixed asset, and also details for all books that are associated with the fixed asset. The **Balances** option at the upper left of the page shows the current valuation for each book that is associated with the fixed asset. You can drill back from the values to see the detailed transactions that make up the summary value. The **Profile** option at the upper left of the page shows the depreciation schedule for each book that is associated with the fixed asset.

You can access the **Fixed asset valuations** page from the **Fixed asset management** workspace or the **Fixed asset** list page.

### Related information

You can navigate directly to the **Books setup** page, **Fixed asset transactions inquiry** page, and several reports by using the links in the **Related information** section of the workspace.

### Analytics – all companies

The **Analytics** page provides important metrics about fixed assets in all legal entities in the system. Access to this tab is controlled by the View fixed asset analytics for all companies duty.

The following table shows the visualizations that are available on each report page.

| Report page            | Visualization        |
|------------------------|----------------------|
| Fixed asset valuations | Total net book value |
| Fixed asset valuations | Net book values by fixed asset group |
| Fixed asset valuations | Acquisition values |
| Fixed asset valuations | Disposal values |
| Fixed asset valuations | Fixed asset details |
| Valuations maps        | Total net book value |
| Valuations maps        | Fixed asset locations |
| Valuations maps        | Fixed asset details |
