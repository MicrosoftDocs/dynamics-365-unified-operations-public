--- 
# required metadata 
 
title: Maintain barcode types
description: This procedure shows you how to set up a new barcode definition which can then be used as part of the picking list report. 
author: perlynne
manager: tfehr 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: BarcodeSetup, InventParameters   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: perlynne
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Maintain barcode types

[!include [banner](../../includes/banner.md)]

This procedure shows you how to set up a new barcode definition which can then be used as part of the picking list report. You can walk through this procedure in demo data company USMF, or using your own data. If you are using USMF you can use the example values that are shown. These tasks would typically be carried out by a warehouse manager.

1. Go to Bar codes.
2. Click New.
3. In the Barcode setup field, type a value.
4. In the Description field, type a value.
5. In the Bar code type field, select an option.
    * If you're using USMF, you can select 'Code 39'.  
6. In the Size field, enter a number.
7. In the Maximum length field, enter a number.
8. Click Save.
9. Close the page.
10. Go to Inventory and warehouse management parameters.
11. In the Barcode setup field, enter or select a value.
    * Select the barcode setup that you created before, but be aware that the bar code format must match the format of the unique identifier for the record type used in the process. For example, for picking routes, the bar code format should match the format of the picking route reference, which is typically a number sequence.  
12. Click Save.
13. Close the page.

