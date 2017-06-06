---
# required metadata

title: Fixed asset management workspace
description: The Fixed asset management workspace shows information that is related to the fixed assets entered in the system. This workspace includes a summary and analytics view.
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
# ms.search.scope: 
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: [Global for most topics. Set Country/Region name for localizations]
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: saraschi
ms.search.validFrom: [month/year of release that feature was introduced in, in format yyyy-mm-dd]
ms.dyn365.ops.version: [name of release that feature was introduced in, see list here: https://microsoft.sharepoint.com/teams/DynDoc/_layouts/15/WopiFrame.aspx?sourcedoc={23419e1c-eb64-42e9-aa9b-79875b428718}&action=edit&wd=target%28Core%20Dynamics%20AX%20CP%20requirements%2Eone%7C4CC185C0%2DEFAA%2D42CD%2D94B9%2D8F2A45E7F61A%2FVersions%20list%20for%20docs%20topics%7CC14BE630%2D5151%2D49D6%2D8305%2D554B5084593C%2F%29]
---

# Fixed asset management workspace

[!include[banner](../includes/banner.md)]

---

The Fixed asset management workspace shows information that is related to fixed assets entered in the system. This workspace includes a summary and analytics view. The **My work** tab shows summary tiles, fixed asset details, and related information about fixed assets in the current company. You also have the ability to add analytics to the Power BI analytics section directly within the
workspace. The **Analytics – all company** tab uses capabilities of Microsoft Power BI to show visuals that are related to fixed assets in all companies.

## My work


### Summary

The tiles in the **Summary** section give an overview of your fixed assets, including metrics on assets that are not yet acquired, acquired this year, and disposed this year. It also has quick navigation to the fixed asset list page, batch depreciation proposal, and fixed asset journal.

### Find fixed assets

The **Find fixed assets** section allows you to quickly search for assets by supplying the fixed asset number, group, name, location, or person responsible. All assets matching the search criteria will show in the list. 
From the list, you can view the following pages: 
 - **Details** page for the fixed asset 
 - **Books** page for all books associated with the fixed asset 
 - **Valuations** page

### Valuations

The **Fixed asset valuations** page allow you to see the most important information about the asset as well as details for all books associated with the fixed asset on a single page. The **Balances** selection on the top left of the page will show the current valuation for each book on the fixed asset. You can drill back from the values to see the detailed transactions that make up the summary value. The **Profile** selection on the top left of the page will display the depreciation schedule for each book on the fixed asset.

You can access the **Valuations** page from the **Fixed asset workspace** or the **Fixed asset list page**.

### Related information

You can navigate directly to the **Books setup** page, **Fixed asset transactions inquiry** page, and a number of reports by using the links in the **Related information** section of the workspace.

### Analytics – all companies

The **Analytics** page provides important metrics about fixed assets in all legal entities in the system. Access to this tab is controlled by the View fixed asset analytics for all companies duty.

The following visualizations are available on each report page.

| Report page            | Visualization        |
|------------------------|----------------------|
| Fixed asset valuations | Total net book value |
| Fixed asset valuations | Net book values by fixed asset group |
| Fixed asset valuations | Acquisition values |
| Fixed asset valuations | Disposal values |
| Fixed asset valuations | Fixed asset details |
| Valuations maps      | Total net book value |
| Valuations maps      | Fixed asset locations |
| Valuations maps      | Fixed asset details |

