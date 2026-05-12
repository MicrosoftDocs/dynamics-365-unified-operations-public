---
title: LT-00003 Generate a fixed asset transfer between warehouses document
description: Learn how to move a fixed asset from one department to another and verify the transfer with a packing slip in Microsoft Dynamics 365 Finance.
author: evgenypopov
ms.author: evgenypopov
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 05/04/2026
ms.reviewer: johnmichalak
ms.search.region: Lithuania
ms.search.validFrom: 2016-06-30
ms.search.form: VehicleModelTable_W, LtInvoiceAutoNumberingGroups, LtInvoiceAutonumberingTable, AssetWarehouseTransfer, HcmWorkerLookUp, SysQueryForm, LtAssetPackingSlip, TransportationDocument, LogisticsPostalAddressLookup
---

# LT-00003 Generate a fixed asset transfer between warehouses document

[!include [banner](../../includes/banner.md)]

This article explains how to move a fixed asset from one department to another and verify the transfer with a packing slip in Microsoft Dynamics 365 Finance.

If your organization needs to move a fixed asset from one department to another and the two departments aren't in the same location, you must verify the transfer by a packing slip. You also need to generate a transfer packing slip if the employee responsible for the fixed asset changes. Depending on the parameters that you enable, the packing slip can be numbered automatically or manually.

The following procedures use the demo data company USMF and require you to manually change the USMF legal entity primary address to LTU before starting. The procedures are intended for accountants who are responsible for fixed assets, and they only apply to Lithuanian functionality. 

## Preset vehicle models

To preset vehicle models, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** > **Setup** > **Vehicle** > **Vehicle models**.
1. Select **New** and in the **Model** field, enter a value. This value prints on the packing slip.
1. In the **Description** field, enter a value, and then select **Save**.

## Set up packing slip autonumbering

To set up packing slip autonumbering, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** > **Number sequences** > **Counters management**.
1. Select **Edit**.
1. In the **Module** field, select an option.
1. In the **Account code** field, select an option.
1. Select the **Auto numbering** checkbox, and then select **Save**.
1. Go to **Organization administration** > **Number sequences** > **Invoice numbering setup**.
1. Select **Edit**.
1. In the **Numbering** field, enter a value.
1. In the **Module** field, select an option.
1. In the **Number sequence code** field, enter or select a value. Use the number sequence you select for packing slip autonumbering.  
1. In the **Account code** field, select an option.
1. Select the **Continue** checkbox, and then select **Save**.

## Generate packing slip

### Specify transportation details

To specify transportation details, follow these steps:

1. In Dynamics 365 Finance, go to **Fixed assets** > **Inquiries and reports** > **Packing slips**.
1. On the Action Pane, select **General**.
1. Select **Transportation details**.
1. Select **Edit**.
1. In the **Print transportation details** field, select **Yes**. The transportation details that you specify on this page are printed on the packing slip.  
1. In the **Goods issued by** field, enter or select a value.
1. In the **Package** field, enter a value.
1. In the **Carrier type** field, select an option.
1. In the **Carrier** field, enter or select a value.
1. In the **Model** field, enter or select a value.
1. In the **Registration number** field, type a value.
1. In the **Trailer registration number** field, type a value.
1. In the **Driver** field, enter or select a value.
1. In the **Driver name** field, type a value.
1. In the **Loading date and time** field, enter a date and time.
1. In the **Loading address** field, enter or select a value.
1. Select **Save**. After the asset unloading process is complete, enter or select unloading information for the packing slip.  
1. In the **Unloading date and time** field, enter a date and time.
1. In the **Unloading address** field, enter or select a value.
1. Select **Save** and close the page.

### Verify the packing slip report

To verify the packing slip report, follow these steps:

1. On the Action Pane, select **General**.
1. Select **Fixed asset packing slip**.
1. Select **OK**. After the report is generated, it prints all transportation details.    



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
