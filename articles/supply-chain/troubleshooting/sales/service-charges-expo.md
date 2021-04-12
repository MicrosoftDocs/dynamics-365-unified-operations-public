---
title: Service Charges exported disappear if Sales order is Invoiced 
description: Service Charges exported disappear if Sales order is Invoiced 
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

# Service Charges exported disappear if Sales order is Invoiced 

KB Number: 4613100

Service charges for an Open sales order is exported viaSales order line charges V2 and visible in the Excel spreadsheet, however whenthe Sales order in Invoiced and the Sales order line charges V2 export is run again, the service charges are no longer exported. 



## Resolution
When miscellaneous charges of category fixed are added to a sales order header or sales order line, once the sales order and sales order line is fully invoiced they will not longer be present on the sales order line, as the charge has been invoiced. The keep flag on the miscellaneous charge determines if the miscellaneous charge record is removed or kept for the sales order or sales order line, also after invoicing, even though the charge is no longer needed for the sales order or sales order line. 

PowerBI reporting for invoiced sales, should not use the sales order and sales order line tables as data source, as this data can be changed after invoiced. PowerBI reporting for invoiced sales should use the CustInvoiceJournal and CustInvoiceLines as data source as this is static and represent always the actual and correct invoiced amounts. 

This is not a bug, but works as intended. 


