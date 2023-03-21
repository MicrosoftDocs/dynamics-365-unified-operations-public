---
title: Entrance code to tax integration 
description: This article introduces the entry point code to tax integration.
author: Qiuchen-Ren
ms.author: qire
ms.reviewer: kfend
ms.topic: conceptual
ms.date: 11/14/2022
ms.custom: bap-template
---

# Entrance code to tax integration 

This article introduces the first step of integrating a new transaction to tax integration. Before going into the real tax integration world, it needs some code to inject the new logic and bypass the legacy tax engine. This article introduces how to realize the entrance code.

## Locate a code point

First, we need to locate a code point for the entrance code. This code point should meet below conditions:

1. It should be before tax is calculated by the legacy tax engine so as to bypass it. And it should only bypass tax calculation but no other extra process.
2. The code should be in a context where it contains the basic transaction information to initialize a `TaxIntegrationDocumentObject` object. The object can be initialized in 2 ways:
   - The transaction header table record itself.
   - Table ID and record ID to distinguish the header table record of the transaction.

Usually, if the transaction to be integrated is already supported by the legacy tax engine, it should have a specific derived class of `TaxCalculation` class, like `TaxSales` for sales orders and `TaxPurch` for purchase orders. This is an ideal code point. Currently, transactions like purchase orders and sales orders are all done in this way. Please refer to `TaxPurch.calculateTax()` and `TaxSales.calc()`.

If the transaction is not supported by legacy tax, then some extra effort should be taken to create the subclass of `Tax`. This article does not cover this scenario.

## Implement the entrance of tax integration

Take the entrance code of the *Sales order* as an example,
`TaxSales.xpp`:

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

- `Tax::isTaxIntegrationEnabledForBusinessProcess()` is used to determine whether to use **Tax Integration** for a transaction. This line is a switch so we can enable or disable a transaction for tax integration from the front end.
  -  This switch can be controlled by a drop-down list at **Tax** > **Setup** > **Tax configuration** > **Tax calculation** > **General** > **Feature setup** > **Business process**
  ![BusinessProcessDropDown.jpg](./media/Business-process-drop-down.jpg)

- TaxIntegrationBusinessProcess is an Enum type. It currently has 5 values: Sales, Purchase, Inventory(used for *Transfer order*), Free text invoice, and Journal.
  - Add a new business process enum value for your new transaction if it is not covered by the 5 above.

- All logic is wrapped in `this.calcUsingTaxIntegration()`.

### The calcUsingTaxIntegration method

This is the code that prepares a `TaxIntegrationDocumentObejct` and calls `TaxIntegrationFacade::calculate(document)`. Take the *Purchase order* as an example.

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

The steps are:

- Construct a `TaxIntegrationDocumentObject` object. There are 2 ways to construct the document object.
  - The first one is `TaxIntegrationDocumentObject::constructWithRecord(Common _record)`. It received a transaction header table record as its parameter. This one is **recommended** as it can avoid conflict when updating fields to the transaction table in data persistence activity.
  - The second one is `TaxIntegrationDocumentObject::construct(RefTableId _tableId, RefRecId _recId)`. It receives a table ID and a record ID as its parameters to distinguish a header table record of the transaction. But the header table record will be re-selected from the database, so potential conflict may happen.
- Set basic information to `TaxIntegrationDocumentObject` by its setter methods. This part is done by `this.setFieldsForTaxIntegrationDocumentObject(document)` method in the above example.
- Call `TaxIntegrationFacade::calculate(document)` to trigger the real tax integration flow.
- Get the `amountIncludingTax` map for compatibility to existed tax adjustment function.
- Call `this.finalizeCalculationForTaxIntegration()` method to handle the `TaxUncommitted` stuff. This step is only necessary when the transaction is using `TaxUncommitted`.
- Return the tax amount.

### Set fields for the document object

The `this.setFieldsForTaxIntegrationDocumentObject()` method is to initialize basic data fields for a taxable document, which will be used in the later activities.

Most of the data fields are recommended to be retrieved in the data retrieval activity. But some of them are set here because of the following reasons:

1. The field is fundamental and is used before data retrieval activity. For example the `headingTableId` and `headingRecId`.
2. The field can only be accessed in this context like the tax object is set by `_document.setLegacyTax(this);`
3. It is convenient to set some particular fields here since it can leverage local methods and methods in the subclass of `TradeCalcTax` so as to avoid duplicate code with the data retrieval class. For example, the document date, invoice date, and delivery date.

Please set them according to the new transaction before the facade is called. Usually, data can be retrieved by an object of **TradeCalcTax** in the context of the entrance point. Ex: `SalesFormLetter` for sales orders is an object of `SalesCalcTax_Sales`, `purchCalcTax` for purchase orders, and `custInvoiceCalcTax` for free text invoices.

Below is an example from `TaxPurch.xpp`:

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
