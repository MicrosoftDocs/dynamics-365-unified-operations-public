---
# required metadata

title: Settle transactions using CustTrans::settleTransaction
description: This topics describes the new CustTrans::settleTransaction method and explains why CustTrans::settleTransact is now obsolete.
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

# Settle transactions using CustTrans::settleTransaction

## CustTrans::settleTransact is obsolete
The **settleTransact** method on the **CustTrans** table has been marked as obsolete.

```X++
public static boolean settleTransact(
CustTable _custTable,
        LedgerVoucher _ledgerVoucher = null,
        boolean _balancePostingProfile = true,
        SettleDatePrinc _saveDatePrinciple = SettleDatePrinc::DateOfPayment,
        TransDate _saveDate = dateNull()
        ,DimSettlementType_RU _dimSettlementType = DimSettlementType_RU::None
        ,CustTrans _parentCustTrans = null)
```

### Why is it marked as obsolete?
When many settlements are being performed at the same time for the same customer, there is database blocking. Database blocking impacts performance.

### What does the method do?
The **settleTransact** settles a set of invoices and payments for a given customer. Settlement identifies this set using the the **SpecCompany**, **SpecTableId**, and **SpecRecId** columns of the **SpecTrans** table. Together, the columns define a settlement context.  

The **\_custTable** parameter of the **settleTransact** method defines the settlement context as the CustTable DataAreaId, TableId, and RecId. The following example shows two contexts.

| SpecCompany | SpecTableId | SpecRecId | Transaction |
|---|---|---|---|
| USMF | 7589 | 22565451428 | 1 |
| USMF | 7589 | 22565451428 | 2 |

## Replacement method
The **settleTransaction** method on the **CustTrans** table is the replacement method.

```X++
public static boolean settleTransaction(
    SpecTransExecutionContext _specTransExecutionContext,
    CustTransSettleTransactionParameters _parameters)
```

### How blocking will be avoided
Each customer settlement will get a unique settlement context.  Because each settlement will be done with a unique context, each transaction will not block.  The following example shows two contexts. Each context has a unique **SpecRecId**.

| SpecCompany | SpecTableId | SpecRecId | Transaction |
|---|---|---|---|
|USMF | 7599 | 68719604825 | 1 |
|USMF | 7599 | 68719604826 | 2 |
	
### Replacement method parameters
The **SpecTransExecutionContext** class defines a unique settlement execution context. It contains two parts. First, it defines the customer or vendor for the settlement. Second, it defines the source for the settlement. 

+ The **newFromSource** method takes a customer or vendor and a source. The customer or vendor is always the customer and the source is always the customer. 

```X++
public static SpecTransExecutionContext newFromSource(
    CustVendTable _custVendTable, 
    Common _source = _custVendTable)
```

+ The **parmSpecContext** method exposes the generated settlement context.

```X++
public Common parmSpecContext()
```

**CustTransSettleTransactionParamters** contains the other method parameters. It has a constructor method that initializes the class with default values. An example is **LedgerVoucher**.

### How to use the **settleTransaction** method
Settlement is done in two parts. First, mark the invoices and payments for settlement.  Then, perform the settlement.    

#### Obsolete code example

```X++
//Mark for settlement
SpecTransManager specTransManager = SpecTransManager::construct(custTable);

specTransManager.insert(…) //Invoice(s)
specTransManager.insert(…) //Payment(s)

//Settle
CustTrans::settleTransact(recipientCustVendTable);
```

#### New code example

```X++
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

### Testing
This functionality uses flights. You must enable the flight in a non-production environment to test it. To understand how to enable a flight in a non-production environment, read [Features flighted in data management and enabling flighted features](../data-entities/data-entities-data-packages.md#features-flighted-in-data-management-and-enabling-flighted-features).

The flight name is **EnableCustTransSettleTransaction**.
