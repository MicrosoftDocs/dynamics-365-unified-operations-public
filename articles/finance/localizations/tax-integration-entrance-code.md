---
title: Entrance code to tax integration
description: This article introduces the entry point code to tax integration.
author: Qiuchen-Ren
ms.author: qire
ms.reviewer: kfend
ms.topic: conceptual
ms.date: 04/12/2022
ms.custom: bap-template
---

# Entrance code to tax integration 

This article explains how to integrate a new transaction into tax integration. Before you start to use tax integration, some "entrance code" is required, so that you can bypass the legacy tax engine and use the new logic instead. This article describes how to introduce this entrance code.

## Find a code point

The first step is to find a code point for the entrance code. This code point should meet the following conditions:

- The code point should be before tax is calculated by the legacy tax engine, so that tax calculation can be bypassed. Additionally, the code point should bypass only tax calculation. No other processes should be bypassed.
- The code should be in a context that contains the basic transaction information that can be used to initialize a `TaxIntegrationDocumentObject` object. The object can be initialized in two ways:

    - From the transaction header table record itself
    - By using the table ID and record ID to distinguish the header table record of the transaction

Usually, if the transaction that must be integrated is already supported by the legacy tax engine, it should have a specific derived class of the `TaxCalculation` class, such as `TaxSales` for sales orders or `TaxPurch` for purchase orders. This class is an ideal code point. Currently, all transactions such as purchase orders and sales orders are done in this way. You can refer to `TaxPurch.calculateTax()` and `TaxSales.calc()`.

If the transaction isn't supported by the legacy tax engine, you should create the subclass of `Tax`. This article doesn't cover this scenario.

## Implement the entrance of tax integration

This example uses the entrance code of the sales order, `TaxSales.xpp`.

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

- `Tax::isTaxIntegrationEnabledForBusinessProcess()` is used to determine whether tax integration is used for a transaction. This line is a switch that lets you enable a transaction for tax integration from the front end.

    This switch can be controlled by the **Business process** field in the **Feature setup** section of the **General** tab on the **Tax calculation parameters** page (**Tax** \> **Setup** \> **Tax configuration** \> **Tax calculation**).

    ![Business process field on the Tax calculation parameters page](./media/Business-process-drop-down.jpg)

- `TaxIntegrationBusinessProcess` is an enumeration (enum) type that currently has five values: *Sales*, *Purchase*, *Inventory* (used for transfer orders), *Free text invoice*, and *Journal*. You can add a new business process enum value for your new transaction if it isn't covered by these five values.
- All logic is wrapped in `this.calcUsingTaxIntegration()`.

### The calcUsingTaxIntegration method

The `calcUsingTaxIntegration` method is the code that prepares a `TaxIntegrationDocumentObject` object and calls `TaxIntegrationFacade::calculate(document)`. The following example uses the purchase order.

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
    - `TaxIntegrationDocumentObject::construct(RefTableId _tableId, RefRecId _recId)` receives a table ID and a record ID as its parameters to distinguish the header table record of the transaction. However, because the header table record is re-selected from the database, a conflict might occur.

2. Use the setter methods to set basic information for the `TaxIntegrationDocumentObject` object. In the preceding example, this step is completed by the `this.setFieldsForTaxIntegrationDocumentObject(document)` method.
3. `TaxIntegrationFacade::calculate(document)` is called to trigger the real tax integration flow.
4. Get the `amountIncludingTax` map for compatibility with the existing tax adjustment function.
5. Call the `this.finalizeCalculationForTaxIntegration()` method to handle `TaxUncommitted`. This step is required only if the transaction is using `TaxUncommitted`.
6. Return the tax amount.

### Set fields for the document object

The `this.setFieldsForTaxIntegrationDocumentObject()` method initializes basic data fields for a taxable document to use in later activities.

Most of the data fields should be retrieved in the data retrieval activity. However, some of them are set here for the following reasons:

- The field is fundamental and is used before the data retrieval activity. Examples include `headingTableId` and `headingRecId`.
- The field can be accessed only in this context. For example, the tax object is set by `_document.setLegacyTax(this);`
- It's convenient to set some fields here because local methods and methods in the subclass of `TradeCalcTax` can be used to avoid duplicate code with the data retrieval class. Examples include the document date, invoice date, and delivery date.

Set the data fields according to the new transaction before the facade is called. Usually, data can be retrieved by an object of `TradeCalcTax` in the context of the entrance point. For example, `SalesFormLetter` is an object of `SalesCalcTax_Sales` for sales orders, `purchCalcTax` for purchase orders, and `custInvoiceCalcTax` for free text invoices.

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

[!include [banner](../includes/banner.md)]
