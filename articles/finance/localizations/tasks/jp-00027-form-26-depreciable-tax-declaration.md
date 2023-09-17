---
title: JP-00027 Form 26 for depreciable tax declaration
description: This task walks you through assigning a registration number to a fixed asset and printing the form 26 report.
author: kfend
ms.date: 08/29/2018
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Japan
ms.author: kfend
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: OMLegalEntity, LogisticsPostalAddress, SysLookupMultiSelectGrid, LogisticsAddressCityLookup, AssetLocation, AssetLocationEdit_JP, AssetGroup, AssetTable, LedgerJournalTable, LedgerJournalTransAsset, DefaultDashboard
---
# JP-00027 Form 26 for depreciable tax declaration

[!include [banner](../../includes/banner.md)]

This task walks you through assigning a registration number to a fixed asset and printing the form 26 report.

In order to complete this task, the Fixed Assets configuration key must be selected.

This task uses the JPMF demo company data. This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.


## Create a registration number
1. Go to Organization administration > Organizations > Legal entities.
2. Click Registration IDs.
3. Click New.
4. In the Purpose field, enter or select a value.
    * Purpose = Fixed asset  
5. In the Name or description field, type a value.
6. Expand the Address section.
7. In the Country/region field, type a value.
8. In the State field, enter or select a value.
9. In the City field, enter or select a value.
10. Click Save.
11. Expand the Registration ID section.
12. Click Add.
13. In the Registration type field, enter or select a value.
14. In the Registration number field, type a value.
15. Click the General tab.
16. In the Effective field, enter a date.
17. In the Depreciation method field, select an option.
18. Click Save.

## Create a fixed asset location and assign registration number
1. Go to Fixed assets > Setup > Fixed asset attributes > Fixed assets locations.
2. Click New.
3. In the Location field, type a value.
4. In the Name field, type a value.
5. Expand the Address section.
6. Click New.
7. In the Name or description field, enter or select a value.
8. In the Registration number field, enter or select a value.
9. Click OK.
10. Click Save.

## Define location to the Fixed asset group
1. Go to Fixed assets > Setup > Fixed asset groups.
2. In the list, find and select the desired record.
    * For example, select VEHI-A.  
3. Click Edit.
4. In the Location field, enter or select a value.
5. Click Save.

## Create a fixed asset
1. Go to Fixed assets > Fixed assets > Fixed assets.
2. Click New.
3. In the Fixed asset group field, enter or select a value.
4. Expand the Location section.
    * Validate Location defaults for the fixed asset  

## Create an acquisition
1. Go to Fixed assets > Journal entries > Fixed assets journal.
2. Click New.
3. In the Name field, enter or select a value.
4. Click Save.
5. Click Lines.
6. In the Date field, enter a date.
7. In the Account field, specify the desired values.
8. In the Debit field, enter a number.
9. Click Post.

## Verify the Form 26 report
1. Go to Fixed assets > Inquiries and reports > Depreciable asset declaration reports > Form 26: Depreciable assets taxation ledger report.
2. In the Calendar year field, enter or select a value.
3. In the Office building asset number field, enter or select a value.
4. In the Registration number field, enter or select a value.
    * Open/save the report in the required location.  Validate the printed report,  the Fixed assets been sorted and grouped by registration number  
    * Similar sorting n grouping of fixed asset is provided for the Form 26-1 n Form 26-2 reports  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
