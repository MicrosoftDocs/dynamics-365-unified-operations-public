---
title: Settle transactions by using CustTrans  settleTransaction
description: This article describes the new CustTrans  settleTransaction method and explains why CustTrans  settleTransact is now obsolete.
author: josaw1
ms.date: 06/01/2019
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: markskun
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: AX 10.0.4
ms.assetid: 0090efe3-3fd8-4988-83df-745d25b063d3
---

# Settle transactions by using CustTrans::settleTransaction

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

## CustTrans::settleTransact is obsolete

The **settleTransact** method on the CustTrans table has been marked as obsolete.

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

### What does obsolete mean?

When a method is marked as obsolete, it means the code is no longer required and we plan to eventually remove it from the product. The obsolete method will often recommend an alternative method that can be used. The referencing code will continue to work as expected with the obsolete method. No immediate action is required. But, referencing code should be refactored to use the replacement method.

For more information about obsolete processes, see [Deprecation of methods and metadata elements](../migration-upgrade/deprecation-deletion-apis.md).

### Why is it marked as obsolete?

When many settlements are done at the same time for the same customer, database blocking occurs. Database blocking affects performance.

### What does the method do?

The **settleTransact** method settles a set of invoices and payments for a specific customer. Settlement identifies this set of invoices by using the **SpecCompany**, **SpecTableId**, and **SpecRecId** columns of the SpecTrans table. Together, the columns define a settlement context.

The **\_custTable** parameter of the **settleTransact** method defines the settlement context as the CustTable **DataAreaId**, **TableId**, and **RecId** values. The following example shows two contexts.

| SpecCompany | SpecTableId | SpecRecId | Transaction |
|---|---|---|---|
| USMF | 7589 | 22565451428 | 1 |
| USMF | 7589 | 22565451428 | 2 |

## Replacement method

The **settleTransaction** method on the CustTrans table is the replacement method.

```X++
public static boolean settleTransaction(
    SpecTransExecutionContext _specTransExecutionContext,
    CustTransSettleTransactionParameters _parameters)
```

### How blocking will be avoided

Every customer settlement will get a unique settlement context. Because each settlement that is done will have a unique context, no transaction will cause blocking.  The following example shows two contexts. Each context has a unique **SpecRecId** value.

| SpecCompany | SpecTableId | SpecRecId | Transaction |
|---|---|---|---|
| USMF | 7599 | 68719604825 | 1 |
| USMF | 7599 | 68719604826 | 2 |
	
### Replacement method parameters

The **SpecTransExecutionContext** class defines a unique settlement execution context. It has two parts. The first part defines the customer or vendor for the settlement. The second part defines the source for the settlement.

+ The **newFromSource** method takes a customer or vendor and a source. The customer or vendor is always the customer, and the source is always the customer.

    ```X++
    public static SpecTransExecutionContext newFromSource(
        CustVendTable _custVendTable, 
        Common _source = _custVendTable)
    ```

+ The **parmSpecContext** method exposes the settlement context that is generated.

    ```X++
    public Common parmSpecContext()
    ```

**CustTransSettleTransactionParamters** contains the other method parameters. It has a constructor method that initializes the class with default values. An example is **LedgerVoucher**.

### How to use the settleTransaction method

Settlement is done in two parts. First, you mark the invoices and payments for settlement. Then you do the settlement.

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

This functionality uses flights. To test it, you must turn on the flight in a non-production environment. For information about how to turn on a flight in a non-production environment, see [Data management overview](../data-entities/data-entities-data-packages.md#features-flighted-in-data-management-and-enabling-flighted-features).

The name of the flight is **EnableCustTransSettleTransaction**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
