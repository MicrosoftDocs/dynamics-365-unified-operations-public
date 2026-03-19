---
title: Entrance code to tax integration
description: Learn about the entry point code to tax integration, including overviews on finding code points and implementing the entrance of tax integration.
author: Qiuchen-Ren
ms.author: qire
ms.topic: how-to
ms.date: 03/19/2026
ms.reviewer: johnmichalak
ms.custom: 
  - bap-template
---

# Entrance code to tax integration

[!include [banner](../../includes/banner.md)]

This article explains how to integrate a new transaction into tax integration. Before you start to use tax integration, you need some "entrance code" so that you can bypass the legacy tax engine and use the new logic instead. This article describes how to introduce this entrance code.

## Find a code point

The first step is to find a code point for the entrance code. This code point should meet the following conditions:

- The code point should be before tax is calculated by the legacy tax engine, so that tax calculation can be bypassed. Additionally, the code point should bypass only tax calculation. No other processes should be bypassed.
- The code should be in a context that contains the basic transaction information that you can use to initialize a `TaxIntegrationDocumentObject` object. You can initialize the object in two ways:

  - From the transaction header table record itself
  - By using the table ID and record ID to distinguish the header table record of the transaction

Usually, if the transaction that you must integrate is already supported by the legacy tax engine, it has a specific derived class of the `TaxCalculation` class, such as `TaxSales` for sales orders or `TaxPurch` for purchase orders. This class is an ideal code point. Currently, all transactions such as purchase orders and sales orders use this approach. You can refer to `TaxPurch.calculateTax()` and `TaxSales.calc()`.

If the transaction isn't supported by the legacy tax engine, you should create the subclass of `Tax`. This article doesn't cover this scenario.

## Implement the entrance of tax integration

This example uses the entry point code of the sales order, `TaxSales.xpp`.

```X++
TaxAmount calc()
{
    TaxAmount taxAmount;
    if (Tax::isTaxIntegrationEnabledForBusinessProcess(TaxIntegrationBusinessProcess::Sales))
    {
        taxAmount = this.calcUsingTaxIntegration();
        return taxAmount;
    }
    boolean                  moreLines;
    TaxBaseCur               baseAmount;
    ...
}
```

- Use `Tax::isTaxIntegrationEnabledForBusinessProcess()` to check whether to use tax integration for a transaction. This line acts as a switch that you can use to enable tax integration for a transaction from the front end.

    You can control this switch by setting the **Business process** field in the **Feature setup** section of the **General** tab on the **Tax calculation parameters** page (**Tax** > **Setup** > **Tax configuration** > **Tax calculation**).

    :::image type="content" source="../media/Business-process-drop-down.jpg" alt-text="Screenshot of the Business process field on the Tax calculation parameters page.":::

- `TaxIntegrationBusinessProcess` is an enumeration (enum) type that currently has five values: *Sales*, *Purchase*, *Inventory* (used for transfer orders), *Free text invoice*, and *Journal*. If your new transaction isn't covered by these five values, you can add a new business process enum value for it.
- All logic is wrapped in `this.calcUsingTaxIntegration()`.

### The calcUsingTaxIntegration method

The `calcUsingTaxIntegration` method prepares a `TaxIntegrationDocumentObject` object and calls `TaxIntegrationFacade::calculate(document)`. The following example uses the purchase order.

```X++
private TaxAmount calcUsingTaxIntegration()
{
    // code on lock
    ...
    TaxAmountCur taxAmount;
    try
    {
        TaxIntegrationDocumentObject document;
        document = TaxIntegrationDocumentObject::constructWithRecord(purchCalcTax.getSource());
        this.setFieldsForLegacyTax();
        this.setFieldsForTaxIntegrationDocumentObject(document);
        TaxIntegrationFacade::calculate(document);
        amountInclTaxMap = document.getAmountIncludingTax();
        amountExclTaxMap = document.getAmountExcludingTax();
        ...
        taxAmount = this.finalizeCalculationForTaxIntegration(
            TaxParameters::isBankExchRateEnabled_W() && purchCalcTax.vendInvoiceInfoTable(),
            doIsolateTransactionScopeTrue);
    }
    // code on error handling
    ...
    return taxAmount;
}
```

This code completes the following steps.

1. Construct a `TaxIntegrationDocumentObject` object in one of two ways:

    - `TaxIntegrationDocumentObject::constructWithRecord(Common _record)` receives a transaction header table record as its parameter. This method is preferred because it avoids conflict when fields are updated in the transaction table in the data persistence activity.
    - `TaxIntegrationDocumentObject::construct(RefTableId _tableId, RefRecId _recId)` receives a table ID and a record ID as its parameters to distinguish the header table record of the transaction. However, because the header table record is reselected from the database, a conflict might occur.

1. Use the setter methods to set basic information for the `TaxIntegrationDocumentObject` object. In the preceding example, the code completes this step by calling the `this.setFieldsForTaxIntegrationDocumentObject(document)` method.
1. Call `TaxIntegrationFacade::calculate(document)` to trigger the real tax integration flow.
1. Get the `amountIncludingTax` map for compatibility with the existing tax adjustment function.
1. Call the `this.finalizeCalculationForTaxIntegration()` method to handle `TaxUncommitted`. This step is required only if the transaction is using `TaxUncommitted`.
1. Return the tax amount.

### Set fields for the document object

The `this.setFieldsForTaxIntegrationDocumentObject()` method initializes basic data fields for a taxable document to use in later activities.

Retrieve most of the data fields in the data retrieval activity. However, set some of them here for the following reasons:

- The field is fundamental and is used before the data retrieval activity. Examples include `headingTableId` and `headingRecId`.
- The field can be accessed only in this context. For example, the tax object is set by `_document.setLegacyTax(this);`
- It's convenient to set some fields here because you can use local methods and methods in the subclass of `TradeCalcTax` to avoid duplicate code with the data retrieval class. Examples include the document date, invoice date, and delivery date.

Set the data fields according to the new transaction before you call the facade. Usually, you can retrieve data by using an object of `TradeCalcTax` in the context of the entrance point. For example, `SalesFormLetter` is an object of `SalesCalcTax_Sales` for sales orders, `purchCalcTax` for purchase orders, and `custInvoiceCalcTax` for free text invoices.

The following example is from `TaxPurch.xpp`.

```X++
protected void setFieldsForTaxIntegrationDocumentObject(TaxIntegrationDocumentObject _document)
{
    _document.setTransactionDate(this.taxDate);
    // This deliveryDateMarkup() is for header.
    _document.setDeliveryDate(salesFormLetter.deliveryDateMarkup());
    _document.setDocumentDate(salesFormLetter.documentDate());
    _document.setInvoiceDate(salesFormLetter.invoiceDate());
    _document.setTransactionCurrencyCode(salesFormLetter.currencyCode());
    _document.setCompany(this.getCompany());
    _document.setHeadingTableId(this.headingTableId());
    _document.setHeadingRecId(this.headingRecId());
    // this sign is used as sign in TmpTaxWorkTrans, 1 for purchase and -1 for sales.
    _document.setSign(-1);
    _document.setSource(TaxModuleType::Sales);
    _document.setBusinessProcess(TaxIntegrationBusinessProcess::Sales);
    _document.setPrepaid(this.isPrePayment());
    _document.setEUROTriangulation(this.getTriangulation());
    _document.setLegacyTax(this);
    _document.setShouldSkipDocumentCharge(skipTableMarkup);
    _document.setShouldSkipLineCharge(skipLineMarkup);
}
```

[!include [banner](../../includes/banner.md)]
