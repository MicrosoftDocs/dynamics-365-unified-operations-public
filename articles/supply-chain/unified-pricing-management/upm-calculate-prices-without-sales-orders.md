---
title: Calculate prices and discounts without creating sales orders
description: Learn how to calculate customer and volume-specific prices and discounts without needing to create a sales order. This capability is useful both when creating quotes and when integrating with external selling systems.
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

This feature exposes key calculation methods and provides sample code that you can use to implement your own custom pricing logic. If you don't have a Commerce Scale Unit (CSU) API license but still want to integrate pricing with third-party systems, use this capability to build custom services to expose pricing via APIs. You can leverage this extensibility to connect pricing seamlessly with external applications.

By carefully preparing transaction data, managing attributes consistently, and leveraging the pricing engine's capabilities, you can achieve accurate, dynamic pricing tailored to your business needs.

This article demonstrates a practical method for integrating external systems with the Unified pricing management pricing engine by using custom logic without requiring a Commerce Scale Unit. This approach enables flexible, attribute-driven pricing logic that you can embed into your applications.

Learn more about custom service development in [Custom service development](../../fin-ops-core/dev-itpro/data-entities/custom-services.md).

## Step 1: Gather input data

The first step in the pricing workflow is to collect all relevant input data required for accurate and context-aware pricing calculations. These inputs serve as the foundation for building the transaction and determining which pricing rules apply. You might get these inputs from various sources such as user input, query strings in URLs, external APIs, or other integrated systems. Gathering input data ensures that the pricing engine receives all necessary context to evaluate and apply the correct pricing logic. Missing or incomplete inputs can lead to inaccurate pricing or skipped discount rules.

The following list outlines the most common data elements used in pricing scenarios. Use these inputs to populate transaction objects and influence pricing calculations.

- **Item numbers** – Unique identifiers for the products that customers purchase. These identifiers are mandatory.
- **Customer account numbers** *(optional)* – Identify the buyer and apply customer-specific pricing, discounts, or loyalty-based rules.
- **Quantities** *(optional)* – Specifies the number of units per item. Quantity can affect volume-based pricing or tiered discount structures.
- **Attributes** *(optional)* – Custom fields that provide additional context, such as:
    - **Site** – Indicates the location or warehouse, which might influence regional pricing.
    - **Channel ID** – Helps apply channel-specific pricing rules.
    - **Delivery mode**, **Tax group**, or **Promotion code** – Other optional fields that might trigger specific pricing logic.

```xpp
// Sample Code: Extracting Input Parameters from URL
// This X++ snippet demonstrates how to retrieve parameter values for item numbers and Customer account numbers from the URL input. This is typically used in runnable classes.
str itemid = urlUtil.getQueryParamValue('itemid');
str custAccount = urlUtil.getQueryParamValue('custAccount');
```

## Step 2: Prepare transaction objects

After you collect the input data, construct structured transaction objects that represent the sales order and its individual lines. These objects serve as the core data model for the pricing engine. They're essential for passing all relevant information—such as item details, quantities, customer context, and unit of measure—into the pricing logic. This step transforms raw input parameters into structured Commerce Runtime (CRT) objects that the pricing engine can process. These objects encapsulate the full context of the transaction, enabling accurate and rule-based price calculations.

The pricing engine expects the transaction to be represented by two primary object types:

- **Sales transaction** – A container for the overall order. It includes customer information, currency, channel context, and a collection of sales lines.
- **Sales lines** – Each line represents a single item in the order. It includes item-specific data such as product ID, quantity, unit of measure, and line identifiers.

The following X++ code demonstrates how to initialize a sales transaction and populate it with one or more sales lines by using the input data. You need this setup before invoking the pricing engine.

```xpp
// This code initializes the transaction and populates it with sales lines using the input data. It sets up the necessary fields for each item, preparing the data for pricing calculations.
using Microsoft.Dynamics.Commerce.Runtime.Services.PricingEngine;
using CrtSalesTransaction = Microsoft.Dynamics.Commerce.Runtime.DataModel.SalesTransaction;
using CrtSalesLine = Microsoft.Dynamics.Commerce.Runtime.DataModel.SalesLine;
using CrtPriceAndDiscountCalculationParameters = Microsoft.Dynamics.Commerce.Runtime.Services.PricingEngine.PriceAndDiscountCalculationParameters;
int salesLinesOrderField = 1;
str lineId = strRFix(int2str(salesLinesOrderField), 3, '0');
InventTable invTbl = InventTable::find(iItemId);
CrtSalesTransaction crtSalesTransaction = new CrtSalesTransaction();
crtSalesTransaction.set_CustomerId(custAccount);
CLRObject clrSalesLines = crtSalesTransaction.get_SalesLines();
CrtSalesLine crtSalesLine = new CrtSalesLine();
crtSalesLine.set_ItemId(itemId);
crtSalesLine.set_Quantity(qty);
crtSalesLine.set_SalesOrderUnitOfMeasure(invTbl.inventTableModuleSales().UnitId);
crtSalesLine.set_LineId(lineId);
crtSalesLine.set_LineNumber(salesLinesOrderField);
clrSalesLines.Add(crtSalesLine);
```

## Step 3: Handle pricing attributes

To ensure accurate and context-aware pricing, the pricing engine relies on attribute-based logic. These attributes can exist at both the header level (order context) and the line level (item context). Calculating hash keys for these attributes is essential, as they serve as identifiers that help the pricing engine match the correct pricing rules. It prepares the pricing context by generating and storing attribute hash keys, enabling the pricing engine to match and apply the correct pricing rules based on attributes. This step enables the pricing engine to apply differentiated pricing rules based on custom attributes such as site, channel, product category, or customer type. By generating hash keys, you create a consistent and secure way to reference attribute values during pricing evaluation.

The following X++ sample code demonstrates how to process pricing attributes and generate hash keys for both the transaction header and each sales line that the pricing engine uses to evaluate applicable pricing rules.

```xpp
// Put the attribute value into the corresponding field in the temporary sales table. The sales table record doesn't need to be inserted into the database
SalesTable salesTable;
salesTable.CustAccount = custTable.AccountNum; // Put the customer account to make sure the customer attribute can be matched
SalesTable.InventSiteId = 'CENTRAL'; // Put the sales table attribute if that is provided in parameter
RetailTempOrderItem tempOrderItem;

// Put the attribute value into the corresponding field in the temporary sales line. The sale lines record doesn't need to be inserted into the database
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

// Create pricing manager
GUPRetailPricingDataManagerV4 gupPricingManager = GUPRetailPricingDataManager::constructDefault(0, transId, tempOrderItem, true);
gupPricingManager.parmHeaderHashSet(headerHashSet);
gupPricingManager.parmLineHashMap(lineHashMap);

/* For version 10.0.45.
GUPPropertyHashTmp orderAttributeValueHeaderHash, orderAttributeValueLineHash;
GUPHashHelper::insertHashTempDB(orderAttributeValueHeaderHash, headerHashSet);
GUPHashHelper::insertHashTempDB(orderAttributeValueLineHash, lineHashSet);
gupPricingManager.parmOrderAttributeValueHeaderHash(orderAttributeValueHeaderHash);
gupPricingManager.parmOrderAttributeValueLineHash(orderAttributeValueLineHash);
*/ 

// For version 10.0.46.
gupPricingManager.parmLineHashSet(headerHashSet);
gupPricingManager.processHash();

ttscommit;
```

If your input attribute values include custom attributes (such as a customer's loyalty tier), use specialized helper methods to generate, hash, and register these attributes before passing them to the pricing engine. These attributes aren't part of the standard transaction schema, so you need to explicitly handle them to ensure the pricing logic recognizes and evaluates them correctly.

To support these scenarios, you must:

- Identify the relevant attributes at either the header (order-level) or line (item-level).
- Map them to pricing attribute definitions by using `GUPPricingAttributeLink`.
- Generate hash keys by using `GUPHashHelper::getPropertyHashKeySetForPricingObject()`.

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

If your pricing logic depends on a specific pricing structure with different price components, you must define the price tree name. This configuration determines which pricing tree the engine uses to evaluate and apply pricing rules. It allows for differentiated pricing structures across scenarios. The price tree acts as a logical framework that organizes pricing rules. By specifying the correct tree, you ensure that the pricing engine applies the appropriate pricing component structure.

- **Set the Price Tree Name from input parameters** – Use a predefined value passed into your service or class to assign the price tree name directly. Use this approach when the pricing structure is known and consistent across transactions.
- **Derive the Price Tree Name dynamically based on input attributes** – In more flexible scenarios, you can compute the tree name at runtime by using product or customer attributes. For example, you might derive the tree name from an input attribute value by using code such as `unifiedPricingParameter.PriceTreeName = GUPPricingTree::getPriceTreeByEcoResValue(<EcoResValue>).Name;`.

This sample code demonstrates how to set a static tree name directly.

```xpp
Microsoft.Dynamics.Commerce.Runtime.DataModel.UnifiedPricingParameter unifiedPricingParameter = gupPricingManager.GetGlobalUnifiedPricingParameter();
unifiedPricingParameter.PriceTreeName = 'Inheritance';
```

## Step 5: Invoke pricing engine methods

With all input data, transaction objects, and pricing attributes prepared, the next step is to invoke the pricing engine to calculate prices and discounts. This step is the core execution phase of the pricing workflow. The engine applies business rules, evaluates attribute-based conditions, and returns computed pricing results. This step activates the pricing logic by passing the prepared transaction and attribute data to the pricing engine. It ensures that all relevant pricing rules—such as discounts, price groups, and attribute-based conditions—are applied consistently and accurately.

The pricing engine processes the transaction object, which includes sales lines, customer information, and pricing attributes. It evaluates applicable pricing rules based on the configured price tree, attribute hash keys, and business logic. The engine returns calculated unit prices and discount amounts for each sales line.

The following X++ code demonstrates how to invoke the pricing engine methods to calculate prices and discounts:

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

After the pricing engine completes its calculations, the final step is to extract and use the computed prices and discounts from the transaction object. This step transforms the pricing engine's output into actionable data that you can present to users or integrate into downstream business processes such as order creation or analytics.

The pricing engine populates each sales line in the transaction object with calculated values. These values include the final unit price, discount amount, and potentially other pricing-related metadata. You can iterate through the sales lines to extract these values and format them for display or further processing. This step is critical for ensuring that the pricing logic is correctly applied and that the results are visible and usable.

The following X++ code demonstrates how to loop through each sales line in the transaction and retrieve the final price and discount amount. Typically, you place this code at the end of your pricing service or runnable class, after the pricing engine has been invoked.

```xpp
clrSalesLines = crtSalesTransaction.get_SalesLines();
CLRObject enumeratorSalesLine = clrSalesLines.GetEnumerator();
while (enumeratorSalesLine.MoveNext())
{
    crtSalesLine = enumeratorSalesLine.get_Current();
    Price price = crtSalesLine.get_Price();
    Price discount = crtSalesLine.get_DiscountAmount();
}
```
