# Calculate Prices and Discounts Without Creating Sales Orders

## Introduction

Unified pricing management in Dynamics 365 Supply Chain Management can now calculate customer and volume-specific prices and discounts without requiring you to create a sales order. This capability is useful both when creating quotes and when integrating with external selling systems where you need to calculate prices without creating a sales order. Just provide product, quantity, and customer details to trigger pricing and discount calculations programmatically.

### Benefit

This feature exposes key calculation methods along with sample code, enabling customers to implement their own custom pricing logic. For UPM customers who do not have a Commerce Scale Unit API license but still want to integrate pricing with third-party systems, this capability makes it possible to build custom services to expose pricing via APIs. You can now leverage this extensibility to connect pricing seamlessly with external applications.

Learn more about custom service development: [Custom service development - Finance & Operations | Dynamics 365 | Microsoft Learn](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/extensibility/custom-services)

This document demonstrates a practical method for integrating with the Microsoft Dynamics pricing engine using custom logic—without requiring Commerce Scale Unit (CSU). This approach enables flexible, attribute-driven pricing logic that can be embedded into your applications.

By carefully preparing transaction data, managing attributes consistently, and leveraging the pricing engine’s capabilities, you can achieve accurate, dynamic pricing tailored to your business needs. (example code: `GUPCustomizationCalculator`)

Step-by-Step Process
Step 1: Gather Input Data
Collect all relevant data for pricing calculations. Inputs may come from
user entry, query strings, APIs, or other sources.
⦁	Item Numbers: Products being purchased.
⦁	Customer Account Numbers*(optional)*: Identifies the buyer.
⦁	Quantities*(optional)*: Number of units per item.
⦁	Attributes*(optional)*: Custom fields for attributes such as
site, materials...
⦁	......
        str itemid = urlUtil.getQueryParamValue('itemid');  
        str custAccount = urlUtil.getQueryParamValue('custAccount');
Step 2: Prepare Transaction Objects
Create structured objects to represent the transaction. Populate these
objects with the input data:
⦁	Sales Transaction: Contains overall order details.
⦁	Sales Lines: Each line represents an item with its own
attributes.
using Microsoft.Dynamics.Commerce.Runtime.Services.PricingEngine;  
using CrtSalesTransaction =
Microsoft.Dynamics.Commerce.Runtime.DataModel.SalesTransaction;  
using CrtSalesLine =
Microsoft.Dynamics.Commerce.Runtime.DataModel.SalesLine;  
using CrtPriceAndDiscountCalculationParameters =
Microsoft.Dynamics.Commerce.Runtime.Services.PricingEngine.PriceAndDiscountCalculationParameters;
        int salesLinesOrderField = 1;  
        str lineId = strRFix(int2str(salesLinesOrderField), 3, '0');  
        InventTable invTbl = InventTable::find(iItemId);
        CrtSalesTransaction crtSalesTransaction = new
CrtSalesTransaction();
        crtSalesTransaction.set_CustomerId(custAccount);  
        CLRObject clrSalesLines = crtSalesTransaction.get_SalesLines();  
        CrtSalesLine crtSalesLine = new CrtSalesLine();  
        crtSalesLine.set_ItemId(itemId);  
        crtSalesLine.set_Quantity(qty);  
       
crtSalesLine.set_SalesOrderUnitOfMeasure(invTbl.inventTableModuleSales().UnitId);  
        crtSalesLine.set_LineId(lineId);  
        crtSalesLine.set_LineNumber(salesLinesOrderField);  
        clrSalesLines.Add(crtSalesLine);
Step 3: Handle Pricing Attributes
Calculates hash keys for pricing attributes at the header and line
level. If there are custom attributes (at the order or item level),
handle them by using some helper methods to generate attribute values
for both the transaction header and each sales line. These attributes
help the pricing engine apply the correct rules and logic for each
scenario.
        // Put the attribute value into the corre sponding field in the
temporary sales table. The sales table record don't need to be inserted
into the database  
        SalesTable salesTable;  
        salesTable.CustAccount = custTable.AccountNum; // Put the
customer account to make sure the  customer attribute can be matched  
        SalesTable.InventSiteId = 'CENTRAL';          
  
        RetailTempOrderItem tempOrderItem;  
  
        // Put the attribute value into the corresponding field in the
temporary sales line. The sale lines record don't need to be inserted
into the database  
        SalesLine salesLine;  
        salesLine.ItemId = itemId;  // Put the itemid to make sure the
product attribute can be matched  
        salesLine.InventTransId = lineId;  
  
        Set headerHashSet = new Set(Types::String);  
        Map lineHashMap = new Map(Types::String, Types::Class);  
        Set lineHashSet = new Set(Types::String);  
  
        Set hashKeySet =
GUPHashHelper::getPropertyHashKeySetForPricingObject(salesTable,
GUPPricingAttributeSourceLevel::Header);  
        headerHashSet =
GUPHashHelper::calculateHashValueForHashKeySet(hashKeySet);  
       hashKeySet =
GUPHashHelper::getPropertyHashKeySetForPricingObject(salesLine,
GUPPricingAttributeSourceLevel::Line);
        Set lineHashSetOneLine =
GUPHashHelper::calculateHashValueForHashKeySet(hashKeySet);  
        lineHashSet = Set::union(lineHashSet, lineHashSetOneLine);  
        lineHashMap.add(salesLine.InventTransId, lineHashSetOneLine);
        ttsbegin;  
        tempOrderItem.itemId = itemId;  
        tempOrderItem.LineNum = salesLinesOrderField;  
        tempOrderItem.UnitOfMeasure =
UnitOfMeasure::findBySymbol(invTbl.inventTableModuleSales().UnitId).RecId;  
        tempOrderItem.insert();
        GUPPropertyHashTmp orderAttributeValueHeaderHash,
orderAttributeValueLineHash;
        GUPHashHelper::insertHashTempDB(orderAttributeValueHeaderHash,
headerHashSet);  
        GUPHashHelper::insertHashTempDB(orderAttributeValueLineHash,
lineHashSet);  
        ttscommit;  
  
        // Create pricing manager  
        GUPRetailPricingDataManagerV4 gupPricingManager =
GUPRetailPricingDataManager::constructDefault(0, transId, tempOrderItem,
true);  
       
gupPricingManager.parmOrderAttributeValueHeaderHash(orderAttributeValueHeaderHash);  
       
gupPricingManager.parmOrderAttributeValueLineHash(orderAttributeValueLineHash);  
        gupPricingManager.parmHeaderHashSet(headerHashSet);  
        gupPricingManager.parmLineHashMap(lineHashMap);
If some sales table attribute and sales line attribute need to be
specified in some calculation scenario:
       Map salesTableAttributeValues = new Map(Types::String,
Types::AnyType);  
       GUPPricingAttributeLink attrLink; // find the attribute that need
to be specified  
      
salesTableAttributeValues.add(attrLink.pricingAttribute().GetHashString(),
<particular attribute value>);  
       Set hashKeySet =
GUPHashHelper::getPropertyHashKeySetForPricingObject(salesTable,
GUPPricingAttributeSourceLevel::Header, null, null, null,
salesTableAttributeValues);  
  
       Map salesLineAttributeValues = new Map(Types::String,
Types::AnyType);  
       GUPPricingAttributeLink attrLink;  // find the attribute that
need to be specified  
       // Put the sale table attribute value on the map  
      
salesLineAttributeValues.add(attrLink.pricingAttribute().GetHashString(),
<particular attribute value>);  
       Set hashKeySet =
GUPHashHelper::getPropertyHashKeySetForPricingObject(salesLine,
GUPPricingAttributeSourceLevel::Line, null, salesLineAttributeValues);
 
Step 4: Specify Price Tree Name
If your pricing logic depends on a specific pricing structure:
⦁	Set the Price Tree Name in the pricing parameters.
⦁	Alternatively, derive the tree name dynamically based on input
attributes. for example, unifiedPricingParameter.PriceTreeName =
GUPPricingTree::getPriceTreeByEcoResValue(<EcoResValue>).Name;
This allows for differentiated pricing structures across scenarios.
      
Microsoft.Dynamics.Commerce.Runtime.DataModel.UnifiedPricingParameter
unifiedPricingParameter =                     
gupPricingManager.GetGlobalUnifiedPricingParameter();  
       unifiedPricingParameter.PriceTreeName = 'Inheritance';
Step 5: Invoke Pricing Engine Methods
Call the pricing engine's methods to calculate prices and discounts:
 
The engine processes the transaction, considering all attributes and
business rules.  
It returns calculated prices and discounts for each sales line.  
This step is where the core pricing logic is executed, leveraging the
engine's capabilities for dynamic, rule-based pricing.
 
        RetailCurrencyOperations currencyAndRoundingHelper = new
RetailCurrencyOperations(CompanyInfoHelper::standardCurrency());  
        System.DateTimeOffset dateTimeOffset =
RetailPricingEngineHelper::getSessionDateTimeInChannelTimeZone(0,
today());  
        CrtPriceAndDiscountCalculationParameters calculationParameters =
new CrtPriceAndDiscountCalculationParameters();  
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
 
Step 6: Retrieve and Display Results
Extract the calculated prices and discounts from the transaction
objects:
 
For each sales line, retrieve the final price and any discounts
applied.  
Present these results to the user, or use them in further business
logic.
        clrSalesLines = crtSalesTransaction.get_SalesLines();  
        CLRObject enumeratorSalesLine = clrSalesLines.GetEnumerator();  
        while (enumeratorSalesLine.MoveNext())  
        {  
            crtSalesLine = enumeratorSalesLine.get_Current();  
            Price price = crtSalesLine.get_Price();  
            Price discount = crtSalesLine.get_DiscountAmount();  
        }
