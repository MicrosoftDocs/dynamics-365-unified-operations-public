---
# required metadata

title: Use external catalogs for PunchOut e-procurement
description: This article explains how you can use external catalogs to create and submit requisitions.
author: GalynaFedorova
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: PurchVendorPortalRequests, CatExternalCatalogBasketWizard, CatExternalCatalogPunchoutDialog
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: 3c7e0e1c-703c-4bbf-b90c-84d29a131360
ms.search.region: Global
# ms.search.industry: 
ms.author: gfedorova
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Use external catalogs for PunchOut e-procurement

[!include [banner](../includes/banner.md)]

By using external catalogs for PunchOut e-procurement, you don't have to maintain information about your vendors' products in your own master data. 
Instead, the shopping cart on a vendor's website is converted to requisition lines that have the correct product information. 

You should avoid maintaining the descriptions and prices of your vendors’ products in your own product master data. Instead, use external catalogs for PunchOut e-procurement. Then, when employees create requisitions, they can “punch out” to a vendor’s external catalog site (in other words, they leave your system and go to the vendor’s site). The products that are added to the shopping cart on the vendor’s website can then be converted to requisition lines. Therefore, you get the correct product information: product ID, name, price, and so on.

To use external catalogs, an employee must create a requisition on the **My purchase requisitions** page.

The employee who creates a requisition is referred to as the preparer of the requisition. As a preparer, you can complete the following tasks.

Use the **External catalogs** line action to open a page that includes all external catalogs that are available for the specified requester, buying legal entity, and receiving operating unit.

Depending on your permissions, change the requester, buying legal entity, and receiving operating unit. A change in those values might change the list of external catalogs that are available to a requester. The external catalogs that are available depend on the current active purchasing policies for the buying legal entity or the receiving operating unit. These policies can allow or prevent access to specific procurement categories. Therefore, the list of external catalogs that are mapped to these procurement categories can be affected.

For more information about policies, see [Purchasing policies overview](../procurement/purchase-policies.md).

- To find external catalogs for specific procurement categories, enter text in the catalog search field.
- To add products from a vendor’s external catalog on the vendor’s website, click the external catalog. Then add products to the shopping cart, and check out. The shopping cart lines will be transferred to Microsoft Dynamics 365.

If there are multiple options for procurement categories, select the correct procurement category before you add the lines to the requisition.
After lines have been added to a requisition, you can add more lines without using external catalogs. Alternatively, you can continue to use external catalogs to add lines.

When the requisition is ready, use the **Workflow** > **Submit** action to submit it for approval.

### Additional resources

- [Set up an external catalog for PunchOut e-procurement](set-up-external-catalog-for-punchout.md)
- [Purchasing cXML enhancements](purchasing-cxml-enhancements.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]