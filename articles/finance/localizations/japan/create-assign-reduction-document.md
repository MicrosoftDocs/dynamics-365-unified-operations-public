---
title: Create and assign a reduction entry document for a government grant subsidy
description: For Japan, a reduction entry document is a document that you can attach to a fixed asset that is sponsored using a government subsidy.
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
ms.search.form: AssetReductionEntryProfile_JP, AssetTable, AssetBook
---
# Create and assign a reduction entry document for a government grant subsidy

[!include [banner](../../includes/banner.md)]

For Japan, a reduction entry document is a document that you can attach to a fixed asset that is sponsored using a government subsidy. The reduction entry certificate contains the details about the government subsidy, such as the reduction entry method, depreciation convention, reason, validity, and subsidy threshold.



The details of the reduction entry document are used to calculate and post reduction entry amounts.



Use this task to learn how to create reduction entry documents and assign it to a fixed asset.



In order to complete this task, the Fixed Asset configuration key must be selected.



This task uses the JPMF demo company data.


## Create a new reduction entry document
1. Go to Fixed assets > Periodic tasks > Reduction entries > Reduction entry documents.
2. Click New.
3. In the Reduction entry document field, type a value.
4. In the Reduction entry type field, select an option.
    * Select a method to journalize the government grant.  
5. In the Depreciation convention field, select an option.
    * This field is available only if you select Reserve in the Reduction entry type field.     Depreciation convention should be the same as the one used for the fixed asset.  
    * You can choose to record some extra information such as subsidies reason, valid from, valid to, max percentage rate of max amount of the government grant subsidy.  
    * Under the Retirement of subsidies tab, you can enter terms that required by the government upon the retirement of the fixed asset and its related subsidies. This information is referred to if and when you dispose of the fixed asset.  
6. Click Save.

## Assign the reduction entry document to a fixed asset book
1. Go to Fixed assets > Fixed assets > Fixed assets.
2. Click New.
    * You can also choose to edit an existing fixed asset if the sponsored asset is already entered in the system.  
3. In the Fixed asset group field, type a value.
4. Click Books.
5. Use the quick filter to filter out the desired book.
6. In the Reduction entry document field, type a value.
7. Enter the document date.
8. Click Save.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
