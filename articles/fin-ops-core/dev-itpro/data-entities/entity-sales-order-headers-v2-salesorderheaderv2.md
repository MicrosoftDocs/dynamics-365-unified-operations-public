---
title: Sales order headers V2 entity
description: Definition of the Sales order headers V2 data entity in finance and operations migration projects with Dynamics 365.
ms.date: 04/28/2023
ms.topic: article
author: edupont04
ms.author: katiehav
searchScope: dynamics-365-daf
ms.service: dynamics-365
ms.subservice: guidance
ms.collection: FastTrack
---


# Sales order headers V2

The **Sales order headers V2** entity supports importing and updating sales order headers.

## When to use this entity

Use the **Sales order headers V2** entity first when you create sales orders. Then create sales line using the **Sales order lines V2** entity.

## Summary

|Type|Name|
|----|----|
| **Data management entity name** | Sales order headers V2|
| **OData public entity** | SalesOrderHeaderV2 |
| **OData public collection** | SalesOrderHeadersV2 |
| **Related menu items** | Accounts receivable / Orders / All sales orders</br>Sales and marketing/ Sales orders/ All sales orders |
| **Related entities** | Sales order lines V2 |
| **Performance pattern** | Single thread recommended |
| **Application Object Tree (AOT) name** | SalesOrderHeaderV2Entity |

## Fields

| Field | Description |
|--|--|
| SALESDORDERNUMBER | Specifies the primary key. This field is required. |
| CURRENCYCODE | Currency code. This field requires that currencies are configured in **General ledger/ Currencies/ Currencies**. |
| CUSTOMERPAYMENTMETHODNAME | Specifies the customer method of payment. This field requires that customers methods of payment are configured in **Accounts receivable/ Setup/ Payment setup/ Methods of payment**. |
| CUSTOMERPOSTINGPROFILEID | Customer posting profile. This field requires that customers posting profiles are configured in **Accounts receivable/ Setup/ Customer posting profiles**. |
| DELIVERYTERMSCODE | Specifies the terms of delivery. This field requires that terms of delivery are configured in **Sales and marketing/ Setup/ Distribution/ Terms of delivery**. |
| INVOICECUSTOMERACCOUNTNUMBER | Specifies the customer invoice account. This field requires that customers are configured in **Accounts receivable/ Customers/ All customers**. This field is required. |
| ORDERINGCUSTOMERACCOUNTNUMBER | Specifies the customer account. This field requires that customers are configured in **Accounts receivable/ Customers/ All customers**. This field is required. |
| PAYMENTTERMSNAME | Specifies the term of payment. This field requires that terms of payment are configured in **Accounts receivable/ Setup/ Payment setup/ Terms of payment**. |
| REQUESTEDRECEIPTDATE | Specifies the requested receipt date. |
| REQUESTEDSHIPPINGDATE | Specifies the requested shipping date. This field is required. |
| SALESTAXGROUPCODE | Specifies the sales tax group. This field requires that sales tax groups are configured in **Tax/ Indirect taxes/ Sales tax/ Sales tax groups**. |

## Issues and considerations

Sales order headers will contain general information like customer, delivery and payment details. To update a sales order header using the **Sales order headers V2** entity, the sales order needs to have an open order status.

## Related resources

[Import sales orders in Dynamics 365 projects](/dynamics365/guidance/resources/import-sales-orders)  
