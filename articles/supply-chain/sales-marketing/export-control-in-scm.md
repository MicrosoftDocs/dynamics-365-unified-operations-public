---
title: New settings added by the Advanced export control feature
description:
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: overview
ms.date: 07/31/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

<!-- KFM: I think we might be missing info on how to configure exceptions, requirements, rules. Maybe something about "licenses" (it's not clear what those are)? -->

# New settings added by the advanced export control feature

The advanced export control feature lets you apply export control rules to sales orders. Individual jurisdictions can be enabled or disabled for each legal entity (company), which means that each company can have have different export control behaviors and rules.


## Global products

When Advanced Export Control is enabled, a new tab is available on the global products form (EcoResProductDetails). This grid allows an ECCN to be selected for any of the export control jurisdictions that exist in the export control jurisdictions configuration. This list is _not_ filtered by jurisdictions used in any given legal entity, since global products can be released to various legal entities. When a product is released to a legal entity as an InventTable record, the current ECCN data is copied to the InventTable record, but then can be changed to override behavior in a specific legal entity. The defaulting rules for ECCN data are the same as all other product attribute defaulting to items.

[<img src="media/export-control-product-jurisdictions.png" alt="Export control settings for products." title="Export control settings for products" width="720" />](media/export-control-product-jurisdictions.png#lightbox)

## Inventory items

Inventory items (InventTable, EcoResProductDetailsExtended form) also have a tab for advanced export control configuration when enabled. The ECCN from the product is defaulted when the product is originally released. After that the ECCN on the item can be overridden, deleted, or new ECCNs for other jurisdictions can be added. The list of jurisdictions in this grid is restricted to only the jurisdictions enabled for this legal entity. The ECCN specified on the inventory item is the only one that impacts export control checks on sales orders. The product ECCN is only used for defaulting. If the product ECCN is changed after releasing the product, it will not be updated on the related items unless the product is re-released, similar to other product field defaulting.

[<img src="media/export-control-item-jurisdictions.png" alt="Export control settings for released products." title="Export control settings for released products" width="720" />](media/export-control-item-jurisdictions.png#lightbox)

## Sales orders

When advanced export control is enabled for a legal entity, an new button named **Check export control** will show up on sales orders. Clicking this button will perform an ad-hoc check to show the current export control status of this document. During confirmation, picking, packing, shipping, and invoicing, the same check will be performed. License quantity will only be consumed and history will only be tracked during confirmation and similar steps. Ad-hoc checks will not change license consumption, nor will the bye tracked in history.

[<img src="media/export-control-sales-order-check.png" alt="The Check export control dialog." title="The Check export control dialog" width="720" />](media/export-control-sales-order-check.png#lightbox)

The sales order header has a tab to specify licenses per jurisdiction. Any licenses specified on the header are assumed to default to all lines of the document, though the license can be overridden at the line level. Licenses are only required to pass export control checks if restrictions and exceptions require a license. Blanket exemptions or corporate policies do not require licenses.

During confirmation and similar posting steps, the history of export control checks is provided tracked. This can be accessed from the sales order header by clicking on the **Result** button which will show the details of the check performed at that time. This data is available for reference from reports and other processes in the COOExportControlSalesTableHistory table, which also provides helper methods to access common information.

The document level deminimis value is _not_ computed and will always be zero by default. To provide a computation of document-level deminimis, extend the COOValidateSalesTable::createRequest() API. <!-- KFM: What is "deminimis" (x2)? Dimensions? -->

[<img src="media/export-control-sales-order-header.png" alt="Export control settings for sales order headers." title="Export control settings for sales order headers" width="720" />](media/export-control-sales-order-header.png#lightbox)

Sales order lines allow the license from the header to be overridden. This allows different lines to be related to different licenses. Lines also provide the ability to override the export control check. When a line is overridden, the export control check is still performed and tracked, but any failures will not block the document processing. The user who edited the override information is automatically tracked on the record. Auditing of this information can be performed using the standard [logging](../../fin-ops-core/dev-itpro/sysadmin/configure-manage-database-log.md) functionality for finance and operations apps.

 The SalesLine.QtyOrdered field is passed for quantity, and the SalesLine.LineAmount is passed for the value. No currency conversion is performed on these values. To override and pass different values, extend the COOValidateSalesTable::createRequest() method to update the values. The deiminimis percentage from the associated item is passed for the line without calculation. <!-- KFM: What is "deiminimis"? Dimensions? -->

[<img src="media/export-control-sales-order-line.png" alt="Export control settings for sales order lines." title="Export control settings for sales order lines" width="720" />](media/export-control-sales-order-line.png#lightbox)
