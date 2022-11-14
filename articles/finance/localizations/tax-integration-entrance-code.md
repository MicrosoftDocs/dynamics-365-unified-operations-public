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

his section introduces the code to enter the real **Tax Integration** world.

## Locate the code point to bypass legacy tax engine

To integrate a new transaction, the first step is to find the code point to inject the new logic and bypass the original core tax logic.

This code point should meet below conditions:

1. Before tax is calculated by the original tax engine so as to bypass it. And it should only bypass tax calculation but no other extra process.
2. The code should be in a context where it contains the basic transaction information to initialize a `TaxIntegrationDocumentObject` object. The object can be initialized in 2 ways:
   - The transaction header table record buffer it self.
   - Table Id and record ID to distinguish the header table record of the transaction.

Usually, if the transaction to be integrated is already supported by the legacy tax engine, it should have a specific derived classes of `TaxCalculation` class. Like `TaxSales` for sales order and `TaxPurch` for purchase order. This is a ideal code point. Currently, the integrated transactions like purchase order and sales order are all done in this way. Please refer to `TaxPurch.calculateTax()` and `TaxSales.calc()`.

If the transaction is not supported by legacy tax, then extra effort should be taken to create the subclass of `Tax`. We will not discuss it here.

## Implement the entrance of tax integration

Take the entrance code of the *Sales order* as an example:
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

- `Tax::isTaxIntegrationEnabledForBusinessProcess()` is used to determine whether to use **Tax Integration** for current transaction. Then the original logic can be bypassed. This switch can be controlled by a drop-down list at:
  - **Tax** > **Setup** > **Tax configuration** > **Tax calculation** > **General** > **Feature setup** > **Business process**
  ![BusinessProcessDropDown.jpg](./media/Business-process-drop-down.jpg)
- TaxIntegrationBusinessProcess is an Enum type, currently has 5 values: Sales, Purchase, Inventory(used for *Transfer order*), Free text invoice and Journal. Choose the business process according to the transaction to be integrated.
- All logic is wrapped in `this.calcUsingTaxIntegration()`.

### The calcUsingTaxIntegration method

This is the code to call `TaxIntegrationFacade::calculate(document)`. Take the *Purchase order* as an example.

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

- Constructs a `TaxIntegrationDocumentObject` object. Like mentioned before, there are 2 ways to contruct the document object. The first one is recommended as it can avoid update conflict when update fields to transaction table in data persistence activity. In above example, it it using the first method.
  - The transaction header table record buffer it self. Call method `TaxIntegrationDocumentObject::constructWithRecord(Common _record)`
  - Table Id and record ID to distinguish the header table record of the transaction. Call method `TaxIntegrationDocumentObject::construct(RefTableId _tableId, RefRecId _recId)`
- Sets basic information to `TaxIntegrationDocumentObject` by the setter methods of it. This part is done by `this.setFieldsForTaxIntegrationDocumentObject(document)` method in above example code.
- Call `TaxIntegrationFacade::calculate(document)` to trigger the real tax integration flow. This interface is the only entrance to the **Tax Integration** world. The supported transaction can easily be found by the references of `TaxIntegrationFacade::calculate(document)`.
- Gets the `amountIncludingTax` map for compatibility to existed tax adjustment function.
- Call `this.finalizeCalculationForTaxIntegration()` method to handle the `TaxUncommitted` stuff. This step is only necessary when transaction is using `TaxUncommitted`.
- Returns the tax amount.

### Set fields for document object

The `this.setFieldsForTaxIntegrationDocumentObject()` method is to initialized basic data for a taxable document, which will be used in following activities.

Actually, some of the data can also be retrieved and set in data retrieval activity. But they are set here because of following reasons:

1. The data is fundamental and is used before data retrieval activity. For example the `headingTableId` and `headingRecId`.
2. The data can only be accessed in this context, like the legacy tax object `_document.setLegacyTax(this);`
3. It is convenient to set some particular data here, since it can leverage local method and methods in subclass of TradeCalcTax so as to avoid duplicate codes in data retrieval class. For example, the document date, invoice date and delivery date.
Please set them according to the new transaction before the facade is called. Usually, data can be retrieved by an object of **TradeCalcTax** in the context of the entrance point. Ex: `SalesFormLetter` for Sales order is an object of `SalesCalcTax_Sales`, `purchCalcTax` for Purchase order, and `custInvoiceCalcTax` for Free text invoice.

If the data in only need copy from database to document object and no specific logic needed, it is recommended to set them in data retrival activity.

Below is example from `TaxPurch.xpp`:

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
