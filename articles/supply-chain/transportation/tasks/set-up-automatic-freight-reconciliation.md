--- 
# required metadata 
 
title: Set up automatic freight reconciliation
description: This procedure shows how to set up data for automatic freight reconciliation. 
author: Weijiesa
ms.date: 10/16/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: TMSFreightBillType, TMSFreightBillTypeAssignment, TMSCarrierCodeLookup, DefaultDashboard, TMSAuditMaster   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: weijiesa
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Set up automatic freight reconciliation

[!include [banner](../../includes/banner.md)]

This procedure shows how to set up data for automatic freight reconciliation. This is typically done by a warehouse manager. You can use this procedure in demo data company USMF.


## Set up the freight bill type
1. Go to Transportation management > Setup > Freight reconciliation > Freight bill type.
    * The freight bill type defines how freight bills and carrier invoices  should be matched.  
2. Click New.
3. In the Freight bill type field, type a value.
4. In the Engine assembly field, type 'Microsoft.Dynamics.Ax.Tms.dll'.
    * This is the standard Transportation management matching engine code library.  
5. In the Engine class field, type 'Microsoft.Dynamics.Ax.Tms.Bll.GenericNormalizer'.
    * This is the standard Transportation management matching engine class.  
6. Click New.
7. In the Description field, choose the value that should match on the freight bill and the carrier invoice.  
8. In the Match required field, select 'Yes'.
    * If you set this field to Yes this means that the value selected in the Description field needs to match on both the freight bill and the carrier invoice. If you set it to No, the field can be blank on one of these.  
9. Click Save.

## Set up the freight bill type assignment
1. Close the page.
2. Go to Transportation management > Setup > Freight reconciliation > Freight bill type assignments.
    * The freight bill type assignment is used to specify which freight bill type is used for a particular carrier.   
3. Click New.
4. In the Mode field, enter or select a value.
5. In the Shipping carrier field, enter or select a value.
6. In the Freight bill type field, select the freight bill type that you created earlier.
7. Close the page.

## Set up the audit master
1. Go to Transportation management > Setup > Freight reconciliation > Audit master.
    * The audit master defines the tolerance limits for automatic freight reconciliation. It specifies by how much the monetary amounts on the freight bill and the carrier invoice can differ and still allow reconciliation to occur. It also defines how to handle discrepancies.  
2. Click New.
3. In the Audit master ID field, type a value.
4. In the Shipping carrier  field, select the same shipping carrier as you did earlier.
5. In the Freight bill type field, select the freight bill type that you created earlier.
6. Expand the Tolerance section.
7. In the Minimum tolerance level field, enter a number.
8. In the Maximum tolerance level field, enter a number.
9. Expand the Result section.
10. In the Overpayment reason code field, enter or select a value.
    * If the monetary amounts differ on the freight bill and the carrier invoice, the overpayment and underpayment reason codes specify the accounts that the difference should be registered on, as long as the difference is within the tolerance levels.  
11. In the Underpayment reason code field, enter or select a value.
12. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]