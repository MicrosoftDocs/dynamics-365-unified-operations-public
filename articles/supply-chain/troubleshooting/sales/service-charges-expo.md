---
title: Service charges aren't included in exported sales orders that have been invoiced 
description: Service charges aren't included in exported sales orders that have been invoiced
author: SmithaNataraj
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: MarkupTable
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: smnatara
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# Service charges aren't included in exported sales orders that have been invoiced

KB Number: 4613100

## Symptoms

An open sales order is exported using the *Sales order line charges V2* entity. The order includes service charges, and these are visible in the exported Excel spreadsheet. However, when the same sales order is invoiced and then exported again using *Sales order line charges V2*, the service charges are no longer included in the exported file.

## Resolution

The system is behaving as designed.

Service charges are classified as miscellaneous charges of category *fixed*. You are able to add this type of charge to sales order headers and lines, but once a sales order header or line has been fully invoiced, these charges are removed because now they have been invoiced.

The **Keep** flag on a miscellaneous charge determines whether the charge record will be removed or kept for the sales order or sales order line after invoicing, even though the charge is no longer needed for the sales order or sales order line. <!-- KFM: It's not clear what we mean here. Are we recommending to use this setting as a solution to the issue? -->

As an additional result of this behavior, PowerBI reporting for invoiced sales should not use the sales order and sales order line tables as a data source, as these can be changed after invoicing. PowerBI reporting for invoiced sales should instead use the `CustInvoiceJournal` and `CustInvoiceLines` tables as a data sources because these are static and always represent the actual and correct invoiced amounts. <!-- KFM: We should probably use the internal names for all four of the tables mentioned in this paragraph. -->

