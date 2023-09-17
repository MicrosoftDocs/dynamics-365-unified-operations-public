---
title: LT-00003 Generate a fixed asset transfer between warehouses document
description: Move a fixed asset from one department to another and verify the transfer with a packing slip.
author: AdamTrukawka
ms.date: 09/15/2021
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Lithuania
ms.author: atrukawk
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: VehicleModelTable_W, LtInvoiceAutoNumberingGroups, LtInvoiceAutonumberingTable, AssetWarehouseTransfer, HcmWorkerLookUp, SysQueryForm, LtAssetPackingSlip, TransportationDocument, LogisticsPostalAddressLookup
---

# LT-00003 Generate a fixed asset transfer between warehouses document

[!include [banner](../../includes/banner.md)]

If your organization needs to move a fixed asset from one department to another and the two departments are not in the same location, the transfer must be verified by a packing slip. You also need to generate a transfer packing slip if the employee responsible for the fixed asset is changed. Depending on the parameters that are enabled, the packing slip can be numbered automatically or manually.

This procedure applies only for Lithuanian functionality. 

The procedure was created using the demo data company USMF and requires changing USMF legal entity primary address to LTU manually before starting. 

This procedure is intended for accountants who are responsible for fixed assets.

## Preset vehicle models
1. Go to **Organization administration** > **Setup** > **Vehicle** > **Vehicle models**.
2. Select **New** and in the **Model** field, enter a value. This value will be printed on the packing slip.
3. In the **Description** field, enter a value and then select **Save**.


## Set up packing slip auto-numbering
1. Go to **Organization administration** > **Number sequences** > **Counters management**.
2. Select **Edit**.
3. In the **Module** field, select an option.
4. In the **Account code** field, select an option.
5. Select the **Auto numbering** check box and then select **Save**.
6. Go to **Organization administration** > **Number sequences** > **Invoice numbering setup**.
7. Select **Edit**.
8. In the **Numbering** field, enter a value.
9. In the **Module** field, select an option.
10. In the **Number sequence code** field, enter or select a value. The number sequence you select should be used for packing slip auto-numbering.  
11. In the **Account code** field, select an option.
12. Select the **Continue** check box and then select **Save**.


## Generate packing slip

### Specify transportation details
1. Go to **Fixed assets** > **Inquiries and reports** > **Packing slips**.
2. On the Action Pane, select **General**.
3. Select **Transportation details**.
4. Select **Edit**.
5. In the **Print transportation details** field, select **Yes**. The transportation details that you can specify on this page will be printed on the packing slip.  
6. In the **Goods issued by** field, enter or select a value.
7. In the **Package** field, enter a value.
8. In the **Carrier type** field, select an option.
9. In the **Carrier** field, enter or select a value.
10. In the **Model** field, enter or select a value.
11. In the **Registration number** field, type a value.
12. In the **Trailer registration number** field, type a value.
13. In the **Driver** field, enter or select a value.
14. In the **Driver name** field, type a value.
15. In the **Loading date and time** field, enter a date and time.
16. In the **Loading address** field, enter or select a value.
17. Select **Save**. After the asset unloading process is complete, enter or select unloading information for the packing slip.  
18. In the **Unloading date and time** field, enter a date and time.
19. In the **Unloading address** field, enter or select a value.
20. Select **Save** and close the page.


### Verify the Packing slip report
1. On the Action Pane, select **General**.
2. Select **Fixed asset packing slip**.
3. Select **OK**. After the report is generated, all transportation details will be printed.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
