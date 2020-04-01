--- 
# required metadata 
 
title: LT-00003 Generate a fixed asset transfer between warehouses document
description: If your organization needs to move a fixed asset from one department to another and the two departments are not in the same location, the transfer must be verified by a packing slip. 
author: KimANelson
manager: AnnBe 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: VehicleModelTable_W, LtInvoiceAutoNumberingGroups, LtInvoiceAutonumberingTable, AssetWarehouseTransfer, HcmWorkerLookUp, SysQueryForm, LtAssetPackingSlip, TransportationDocument, LogisticsPostalAddressLookup   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Lithuania
# ms.search.industry: 
ms.author: knelson
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# LT-00003 Generate a fixed asset transfer between warehouses document

[!include [banner](../../includes/banner.md)]

If your organization needs to move a fixed asset from one department to another and the two departments are not in the same location, the transfer must be verified by a packing slip. You also need to generate a transfer packing slip if the employee responsible for the fixed asset is changed. Depending on the parameters that are enabled, the packing slip can be numbered automatically or manually.

This procedure applies only for Lithuanian functionality. 

The procedure was created using the demo data company USMF and requires changing USMF legal entity primary address to LTU manually before starting. 

This procedure is intended for accountants who are responsible for fixed assets.


## Preset vehicle models
1. Go to Organization administration > Setup > Vehicle > Vehicle models.
2. Click New.
3. In the Model field, type a value.
    * This value will be printed on the packing slip.  
4. In the Description field, type a value.
5. Click Save.

## Set up packing slip auto-numbering
1. Go to Organization administration > Number sequences > Counters management.
2. Click Edit.
3. In the Module field, select an option.
4. In the Account code field, select an option.
5. Select the Auto numbering check box.
6. Click Save.
7. Go to Organization administration > Number sequences > Invoice numbering setup.
8. Click Edit.
9. In the Numbering field, type a value.
10. In the Module field, select an option.
11. In the Number sequence code field, enter or select a value.
    * The number sequence selected here should be used for packing slip auto-numbering.  
12. In the Account code field, select an option.
13. Select the Continue check box.
14. Click Save.

## Generate packing slip

## Specify transportation details
1. Go to Fixed assets > Inquiries and reports > Packing slips.
2. On the Action Pane, click General.
3. Click Transportation details.
4. Click Edit.
5. Select Yes in the Print transportation details field.
    * If selected, transportation details that you can specify on this form will be printed on the Packing slip.  
6. In the Goods issued by field, enter or select a value.
7. In the Package field, type a value.
8. In the Carrier type field, select an option.
9. In the Carrier field, enter or select a value.
10. In the Model field, enter or select a value.
11. In the Registration number field, type a value.
12. In the Trailer registration number field, type a value.
13. In the Driver field, enter or select a value.
14. In the Driver name field, type a value.
15. In the Loading date and time field, enter a date and time.
16. In the Loading address field, enter or select a value.
17. Click Save.
    * After the asset unloading process is completed, yo can also fill in unloading information for the packing slip.  
18. In the Unloading date and time field, enter a date and time.
19. In the Unloading address field, enter or select a value.
20. Click Save.
21. Close the page.

## Verify the Packing slip report
1. On the Action Pane, click General.
2. Click Fixed asset packing slip.
3. Click OK.
    * After the report is generated, all transportation details will be printed.  

