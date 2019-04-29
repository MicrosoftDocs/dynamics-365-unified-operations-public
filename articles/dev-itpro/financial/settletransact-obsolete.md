---
# required metadata

title: CustTrans::settleTransact is obsolete
description: Describes why this method is obsolete and what method to use for development going forward.
author: RobinARH
manager: AnnBe
ms.date: 06/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 25631
ms.assetid: 0090efe3-3fd8-4988-83df-745d25b063d3
ms.search.region: Global
# ms.search.industry: 
ms.author: markskun
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: AX 10.0.4

---

# CustTrans::settleTransact is obsolete

## Obsolete method
The settleTransact method on the CustTrans table has been marked as obsolete.

``` X++
public static boolean settleTransact(
CustTable _custTable,
        LedgerVoucher _ledgerVoucher = null,
        boolean _balancePostingProfile = true,
        SettleDatePrinc _saveDatePrinciple = SettleDatePrinc::DateOfPayment,
        TransDate _saveDate = dateNull()
        ,DimSettlementType_RU _dimSettlementType = DimSettlementType_RU::None
        ,CustTrans _parentCustTrans = null)
```

## Why was it marked as obsolete?
When many settlements are being performed at the same time for the same customer, we get database blocking.  This impacts performance.

## What does the method do?
The method CustTrans::settleTransact settles a set of invoices and payments for a given customer.  
Settlement identifies this set by the SpecTrans table and the SpecCompany, SpecTableId, SpecRecId columns.  Together, they define a settlement context.  

The CustTrans::settleTransact method parameter _custTable defines the settlement context as the CustTable DataAreaId, TableId, and RecId.  

Example
SpecCompany			SpecTableId		SpecRecId		Transaction
USMF				7589			22565451428		1
USMF				7589			22565451428		2

## How blocking will be avoided
Each customer settlement will get a unique settlement context.  Because each settlement will be done with a unique context, each transaction will not block.  Example:

## Example

| SpecCompany | SpecTableId | SpecRecId | Transaction |
|---|---|---|---|
|USMF | 7599 | 68719604825 | 1 |
|USMF | 7599 | 68719604826 | 2 |
			
## Replacement method
The settleTransaction method on CustTrans table is the replacement method.

```
public static boolean settleTransaction(
    SpecTransExecutionContext _specTransExecutionContext,
    CustTransSettleTransactionParameters _parameters)
```

## Replacement method parameters
The SpecTransExecutionContext class defines a unique settlement execution context.  It contains two parts.  First, it defines the customer or vendor for the settlement.  Second, it defines the source for the settlement. 

+ The newFromSource method will take a customer or vendor and a source.  In this release, the customer or vendor will always be the customer and the source will always be the customer. 

```
    public static SpecTransExecutionContext newFromSource(
CustVendTable _custVendTable, 
Common _source = _custVendTable)
```

+ The parmSpecContext method exposes the generated settlement context.

```
public Common parmSpecContext()
```

CustTransSettleTransactionParamters contains the other method parameters.  It has been created with a constructor method that will initialize the class with default values.  Example: LedgerVoucher.

## How to uptake the new method
Settlement is done in two parts.  First, the invoices and payments are marked for settlement.  Second, the settlement is performed.    

### OLD

```
//Mark for settlement
SpecTransManager specTransManager = SpecTransManager::construct(custTable);

specTransManager.insert(…) //Invoice(s)
specTransManager.insert(…) //Payment(s)

//Settle
CustTrans::settleTransact(recipientCustVendTable);
```

### NEW

```
//Mark for settlement
SpecTransExecutionContext specTransExecutionContext = SpecTransExecutionContext::newFromSource(custTable);
specTransManager = SpecTransManager::construct(specTransExecutionContext.parmSpecContext());

specTransManager.insert(…) //Invoice(s)
specTransManager.insert(…) //Payment(s)

//Settle
CustTrans::settleTransaction(
specTransExecutionContext, 
CustTransSettleTransactionParameters::construct());
```

## Testing
This functionality uses flights.  The flight must be enabled in a non-production environment so it can be tested.   

To understand how to enable a flight in a non-production environment, read [Features flighted in data management and enabling flighted features](../dev-itpro/data-entities/data-entities-data-packages.md#features-flighted-in-data-management-and-enabling-flighted-features).

Flight Name = EnableCustTransSettleTransaction


