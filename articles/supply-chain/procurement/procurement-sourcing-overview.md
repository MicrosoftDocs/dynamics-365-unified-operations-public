---
title: Procurement and sourcing overview
description: Get an overview of the functionality that's available in the Procurement and sourcing module, including an outline on needs for products and services.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form: CatProcureCatalogListPage, CatVendorCatalogListPage, PurchTable, PurchTablePart
ms.topic: overview
ms.date: 07/21/2025
ms.custom:
- bap-template
---

# Procurement and sourcing overview

[!include [banner](../includes/banner.md)]

This article gives an overview of the functionality that's available in the Procurement and sourcing module.

Procurement and sourcing covers all the steps from identifying a need for product and services through procuring the product, receipt, invoicing, and processing of payment with vendors. Procurement processes can be configured toward specific business needs by defining purchasing policies and workflows.

## Identifying a need for product and services

The need for products or services can arise from *requisitions*, for example, when an employee requires a product. *Product catalogs* can be set up to guide the selection of available products to select from, or requests can be made for products that aren't yet made available in a catalog, allowing the purchasing department to consider how the product can be supplied.  

*Spending limits* can be used to constrain requisition spending, and the *purchasing workflow* adds the option of requiring approval before ordering happen. It's also possible to specify budget fund allocation if necessary.  

The procurement department identifies suppliers for required products and services, and this can involve a *request for quotation* being sent out to multiple potential suppliers. It's possible to share the specifications of the product that's being requested and potential vendors can view these to see if they can deliver a product that conforms with them. Vendors return their bids, which the procurement department then reviews before they select the supplier that they want to procure from.  

Purchase orders include an option to send out a *purchase inquiry* to the vendor as an alternative to a more comprehensive request for quotation process. The purchase inquiry can be used to help establish terms like prices, discounts, and receipt date for the order. If vendors are set up to use the **Vendor** portal, purchase inquiry functionality is disabled. Instead the order is shared on the **Vendor** portal, and when a *confirmation request* is sent, the vendor can directly confirm the order.  

*Vendor catalogs* can be used to collect information on the product assortment that vendors can supply. Vendors can publish their own catalog, so it's easier to keep the catalog up to date. It's possible to attach an *approved vendor list* to a product, and this can help guide vendor selection when new purchase orders are opened, and prevent the use of unintended vendors.

## Procurement

*Purchase orders* can be created in several different ways including:

- As an outcome of a master planning fun that identified a demand that requires a purchase. This process generates planned purchase orders, and when these are released, purchase orders are generated.
- Through the processing of purchase requisitions that result in procurement.
- Through the processing of purchase agreements, where purchase orders are created as released orders from the agreements. This is commonly used when purchase agreements are used to represent blanket orders.
- Manually, when the purchase order that's created isn't based on another document.

Purchase orders that are configured with *purchase approval workflows* require approval before they're recorded as approved, and this is required before the order can be processed further.

Purchase orders are *confirmed* to represent that an agreement has been established with the vendor. The purchase order will then gradually progress through different states until ultimately being invoiced or canceled.  

When you create a purchase order, many of the fields are prepopulated with values that default from the information stored about the vendor in the **Vendors** page. This means that there are a limited number of fields that you need to fill in on the purchase order, although you can choose to override the default values.

### Prices and discounts

Prices and discounts include information about the prices, discounts, and rebate terms that they offer. Prices and discounts can be represented as *trade agreements*. Trade agreements represent vendor price lists with prices or discounts, and have a specific set of dates for which the agreement is valid. Prices and discounts can be negotiated and represented through *purchase agreements* with conditions like commitments to buy certain volumes or monetary amounts as a precondition for the negotiated terms. *Rebate agreements* can be created with vendors where the procurement of specific products or groups of products might trigger a rebate from the vendor depending on the purchase amount or volume.

### Delivery options

There are different options for the delivery process associated with a purchase order. Ordered products can be split into *delivery* schedules, where parts of the ordered quantity can be planned for delivery on different dates. Delivery can also include *direct delivery* initiated from a sales order, which automates the generation of the packing slip on the sales order at the same time as the product receipt is recorded on the purchase order. Purchase orders can also be part an *intercompany order* chain, also referred to as intercompany purchase orders, where products are ordered from a matching intercompany sales order. In this situation, some steps are automated across the two related intercompany orders.

### Supplementary items

Products can be set up to include *supplementary items*. This is to propose products that are related to the product that's being ordered. The additional products might be required, or might be optional. In some cases, supplementary items might be added as free products that accompany the purchase of other products.

### Purchase order charges

Charges can be assigned to the purchase order. This can happen automatically through setup of automatic charges or by adding the charges manually. Charges can be assigned to the order at the header level, or at the order line level. Accounting of charges can be set up in different ways. For example, you can set up a charge to be accounted as a product cost. If you do this, the charges must be assigned at the order line level before the order can be confirmed. There's an option that can help allocate charges from the order header to the lines.

## Product receipt and invoicing

Purchase orders that include physical products commonly require *arrival registration* to happen within a warehouse, and after this a *product receipt* is registered for the order.

Some purchase orders include products that are services or other nonphysical products where receipt in a warehouse isn't needed. Products can be created as services or *procurement categories* can be used directly on the purchase order for such orders. With these orders, accounting of product receipt is sometimes skipped and the order is invoiced directly, or alternatively product receipt registration is done on the purchase order without any prior arrival registration.  

Receipt of products can result in automatic consumption for a specific purpose. This includes implied consumption with direct delivery, consumption towards a project, or accounting the product as a fixed asset.  

When *vendor invoices* arrive from the vendor, they can first be recorded in the *invoice register* independent of the purchase order, and then later approved as a record against the purchase order. Recording the vendor invoice with the purchase order includes matching of the product receipt toward the invoice.  

*Accounting distributions* can be specified on the purchase order to describe how accounting should be done within the ledger, and can also define how budget fund allocation is obtained when this is included in your configuration.  

Invoiced purchase orders will record the liability into the vendor account within accounts payable, from where the *vendor payment* can be processed.

## Vendor performance

Performance and review of purchasing is supported through *procurement and account payable reports*, which include spend analysis and vendor performance analysis.

## Related information

### Documentation resources

- [Monitor consignment inventory using vendor collaboration](../inventory/tasks/monitor-consignment-inventory-vendor-collaboration.md)
- [Create a purchase order from a sales order](../sales-marketing/tasks/create-purchase-order-sales-order.md)
- [Create a consignment replenishment order](../inventory/tasks/create-consignment-replenishment-order.md)
- [Overview of vendor invoices](../../finance/accounts-payable/vendor-invoices-overview.md)
- [Vendor posting profiles](../../finance/accounts-payable/vendor-posting-profiles.md)
- [Importing vendor catalogs](https://blogs.msdn.microsoft.com/dynamicsaxscm/2016/05/25/vendor-catalogs-in-dynamics-ax/) (blog post)

### White papers

The following white papers explore various aspects of procurement in Dynamics 365 Supply Chain Management:

- [Defining business process workflows for purchase requisitions](https://www.microsoft.com/download/details.aspx?id=101821)
- [Inbound consignment inventory demo script](https://www.microsoft.com/download/details.aspx?id=101945)
- [Defining business process workflows for purchase requisitions](https://www.microsoft.com/download/details.aspx?id=101821)
- [Trade agreements](https://download.microsoft.com/download/0/2/9/02972c8b-0159-4936-a3ef-1e64252b2d2f/TradeAgreementsInAX.pdf)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
