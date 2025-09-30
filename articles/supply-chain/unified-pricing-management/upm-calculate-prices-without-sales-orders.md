---
title: Calculate prices and discounts without creating sales orders
description: Learn how to calculate customer and volume-specific prices and discounts without requiring you to create a sales order. This capability is useful both when creating quotes and when integrating with external selling systems.
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 10/24/2025
ms.custom:
  - bap-template
---

# Calculate prices and discounts without creating sales orders

Unified pricing management in Dynamics 365 Supply Chain Management can calculate customer and volume-specific prices and discounts without requiring you to create a sales order. This capability is useful both when creating quotes and when integrating with external selling systems where you need to calculate prices without creating a sales order. To trigger pricing and discount calculations programmatically, you just need to provide product, quantity, and customer details.

This feature exposes key calculation methods and provides sample code that you can use to implement your own custom pricing logic. If you don't have a Commerce Scale Unit (CSU) API license but still want to integrate pricing with third-party systems, you can use this capability to build custom services to expose pricing via APIs. You can leverage this extensibility to connect pricing seamlessly with external applications.

Learn more about custom service development in [Custom service development](../../fin-ops-core/dev-itpro/data-entities/custom-services.md)

This article demonstrates a practical method for integrating with the Unified pricing management pricing engine using custom logic without requiring a Commerce Scale Unit. This approach enables flexible, attribute-driven pricing logic that can be embedded into your applications.

By carefully preparing transaction data, managing attributes consistently, and leveraging the pricing engine's capabilities, you can achieve accurate, dynamic pricing tailored to your business needs. (example code: `GUPCustomizationCalculator`) <!-- KFM: what does this text in parenthesis mean? Is this some code that we can download somewhere? -->

<!-- KFM: who is doing these steps? Where? How? What then? -->

## Step 1: Gather input data

Collect all relevant data for pricing calculations. Inputs might come from user entry, query strings, APIs, or other sources.

<!-- KFM: Introduce this list. -->

- **Item numbers** – Products being purchased.
- **Customer account numbers** *(optional)* – Identifies the buyer.
- **Quantities** *(optional)* – Number of units per item.
- **Attributes** *(optional)* – Custom fields for attributes such as site, materials... <!-- KFM: Why the ellipses here? -->
- ...... <!-- KFM: What is this? -->

<!-- KFM: I have assumed all blocks of sample code are in X++. Is this correct? -->

<!-- KFM: Introduce this sample code. What is this? Where does it go? What will it do? -->

```xpp
str itemid = urlUtil.getQueryParamValue('itemid');
str custAccount = urlUtil.getQueryParamValue('custAccount');
```

## Step 2: Prepare transaction objects

Create structured objects to represent the transaction. Populate these objects with the input data: <!-- KFM: More detail is needed here. What is this list about? What are we doing here? It's not clear how these relate to the following code sample. -->

- **Sales transaction** – Contains overall order details.
- **Sales lines** – Each line represents an item with its own attributes.

<!-- KFM: Introduce this sample code. What is this? Where does it go? What will it do? -->

```xpp
using Microsoft.Dynamics.Commerce.Runtime.Services.PricingEngine;
using CrtSalesTransaction = Microsoft.Dynamics.Commerce.Runtime.DataModel.SalesTransaction;
using CrtSalesLine = Microsoft.Dynamics.Commerce.Runtime.DataModel.SalesLine;
using CrtPriceAndDiscountCalculationParameters = Microsoft.Dynamics.Commerce.Runtime.Services.PricingEngine.PriceAndDiscountCalculationParameters;
int salesLinesOrderField = 1;
str lineId = strRFix(int2str(salesLinesOrderField), 3, '0');
InventTable invTbl = InventTable::find(iItemId);
CrtSalesTransaction crtSalesTransaction = new CrtSalesTransaction();
crtSalesTransaction.set\_CustomerId(custAccount);
CLRObject clrSalesLines = crtSalesTransaction.get\_SalesLines();
CrtSalesLine crtSalesLine = new CrtSalesLine();
crtSalesLine.set\_ItemId(itemId);
crtSalesLine.set\_Quantity(qty);
crtSalesLine.set\_SalesOrderUnitOfMeasure(invTbl.inventTableModuleSales().UnitId);
crtSalesLine.set\_LineId(lineId);
crtSalesLine.set\_LineNumber(salesLinesOrderField);
clrSalesLines.Add(crtSalesLine);
```

## Step 3: Handle pricing attributes

Calculate hash keys for pricing attributes at the header and line level. If there are custom attributes (at the order or item level), handle them by using some helper methods to generate attribute values for both the transaction header and each sales line. These attributes help the pricing engine apply the correct rules and logic for each scenario.

<!-- KFM: Introduce this sample code. What is this? Where does it go? What will it do? -->

```xpp
// Put the attribute value into the corresponding field in the temporary sales table. The sales table record don't need to be inserted into the database
SalesTable salesTable;
salesTable.CustAccount = custTable.AccountNum; // Put the customer account to make sure the customer attribute can be matched
SalesTable.InventSiteId = 'CENTRAL';
RetailTempOrderItem tempOrderItem;

// Put the attribute value into the corresponding field in the temporary sales line. The sale lines record don't need to be inserted into the database
SalesLine salesLine;
salesLine.ItemId = itemId; // Put the itemid to make sure the product attribute can be matched
salesLine.InventTransId = lineId;
Set headerHashSet = new Set(Types::String);
Map lineHashMap = new Map(Types::String, Types::Class);
Set lineHashSet = new Set(Types::String);
Set hashKeySet = GUPHashHelper::getPropertyHashKeySetForPricingObject(salesTable, GUPPricingAttributeSourceLevel::Header);
headerHashSet = GUPHashHelper::calculateHashValueForHashKeySet(hashKeySet);
hashKeySet = GUPHashHelper::getPropertyHashKeySetForPricingObject(salesLine, GUPPricingAttributeSourceLevel::Line);
Set lineHashSetOneLine = GUPHashHelper::calculateHashValueForHashKeySet(hashKeySet);
lineHashSet = Set::union(lineHashSet, lineHashSetOneLine);
lineHashMap.add(salesLine.InventTransId, lineHashSetOneLine);
ttsbegin;
tempOrderItem.itemId = itemId;
tempOrderItem.LineNum = salesLinesOrderField;
tempOrderItem.UnitOfMeasure = UnitOfMeasure::findBySymbol(invTbl.inventTableModuleSales().UnitId).RecId;
tempOrderItem.insert();
GUPPropertyHashTmp orderAttributeValueHeaderHash, orderAttributeValueLineHash;
GUPHashHelper::insertHashTempDB(orderAttributeValueHeaderHash, headerHashSet);
GUPHashHelper::insertHashTempDB(orderAttributeValueLineHash, lineHashSet);
ttscommit;

// Create pricing manager
GUPRetailPricingDataManagerV4 gupPricingManager = GUPRetailPricingDataManager::constructDefault(0, transId, tempOrderItem, true);
gupPricingManager.parmOrderAttributeValueHeaderHash(orderAttributeValueHeaderHash);
gupPricingManager.parmOrderAttributeValueLineHash(orderAttributeValueLineHash);
gupPricingManager.parmHeaderHashSet(headerHashSet);
gupPricingManager.parmLineHashMap(lineHashMap);
```

If some sales table attribute and sales line attribute need to be specified in some calculation scenario: <!-- KFM: Complete this sentence. I think we are introducing the following code, but a bit more detail is needed. -->

```xpp
Map salesTableAttributeValues = new Map(Types::String, Types::AnyType);
GUPPricingAttributeLink attrLink; // find the attribute that need to be specified
salesTableAttributeValues.add(attrLink.pricingAttribute().GetHashString(), &lt;particular attribute value&gt;);
Set hashKeySet = GUPHashHelper::getPropertyHashKeySetForPricingObject(salesTable, GUPPricingAttributeSourceLevel::Header, null, null, null, salesTableAttributeValues);
Map salesLineAttributeValues = new Map(Types::String, Types::AnyType);
GUPPricingAttributeLink attrLink; // find the attribute that need to be specified

// Put the sale table attribute value on the map
salesLineAttributeValues.add(attrLink.pricingAttribute().GetHashString(), &lt;particular attribute value&gt;);
Set hashKeySet = GUPHashHelper::getPropertyHashKeySetForPricingObject(salesLine, GUPPricingAttributeSourceLevel::Line, null, salesLineAttributeValues);
```

## Step 4: Specify price tree name

If your pricing logic depends on a specific pricing structure: <!-- KFM: complete this sentence. Make it more clear what the following list is.  -->

- Set the **Price Tree Name** in the pricing parameters. <!-- KFM: What does the bold indicate here? -->
- Alternatively, derive the tree name dynamically based on input attributes using code such as `unifiedPricingParameter.PriceTreeName = GUPPricingTree::getPriceTreeByEcoResValue(<EcoResValue>).Name;`.

This allows for differentiated pricing structures across scenarios.

<!-- KFM: Introduce this sample code. What is this? Where does it go? What will it do? -->

```xpp
Microsoft.Dynamics.Commerce.Runtime.DataModel.UnifiedPricingParameter unifiedPricingParameter = gupPricingManager.GetGlobalUnifiedPricingParameter();
unifiedPricingParameter.PriceTreeName = 'Inheritance';
```

## Step 5: Invoke pricing engine methods

Call the pricing engine's methods to calculate prices and discounts.

The engine processes the transaction, considering all attributes and business rules.

It returns calculated prices and discounts for each sales line.

This step is where the core pricing logic is executed, leveraging the engine's capabilities for dynamic, rule-based pricing.

<!-- KFM: I think the previous sentences are introducing the following code, but this needs to be more clear. It's still not clear where to pub this code or where/how to run it. -->

```xpp
RetailCurrencyOperations currencyAndRoundingHelper = new RetailCurrencyOperations(CompanyInfoHelper::standardCurrency());
System.DateTimeOffset dateTimeOffset = RetailPricingEngineHelper::getSessionDateTimeInChannelTimeZone(0, today());
CrtPriceAndDiscountCalculationParameters calculationParameters = new CrtPriceAndDiscountCalculationParameters();
CurrencyCode transactionCurrency = 'USD';
// Calculate price
PricingEngine::CalculatePricesForTransaction(
    crtSalesTransaction,
    gupPricingManager,
    currencyAndRoundingHelper,
    custTable.PriceGroup,
    transactionCurrency,
    dateTimeOffset);

// Calculate discount
PricingEngine::CalculateDiscountsForLines(
    gupPricingManager,
    crtSalesTransaction,
    currencyAndRoundingHelper,
    transactionCurrency,
    custTable.LineDisc,
    custTable.MultiLineDisc,
    custTable.EndDisc,
    false, // calculateSimpleDiscountOnly
    dateTimeOffset,
    calculationParameters);
```

## Step 6: Retrieve and display results

Extract the calculated prices and discounts from the transaction objects.

For each sales line, retrieve the final price and any discounts applied.

Present these results to the user, or use them in further business logic.

<!-- KFM: I think the previous sentences are introducing the following code, but this needs to be more clear. It's still not clear where to pub this code or where/how to run it. -->

```xpp
clrSalesLines = crtSalesTransaction.get\_SalesLines();
CLRObject enumeratorSalesLine = clrSalesLines.GetEnumerator();
while (enumeratorSalesLine.MoveNext())
{
    crtSalesLine = enumeratorSalesLine.get\_Current();
    Price price = crtSalesLine.get\_Price();
    Price discount = crtSalesLine.get\_DiscountAmount();
}
```
