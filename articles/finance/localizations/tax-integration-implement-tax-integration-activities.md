---
title: Implement tax integration activities
description: This article introduces the activities that must be implemented to integrate a new transaction.
author: Qiuchen-Ren
ms.author: qire
ms.reviewer: kfend
ms.topic: conceptual
ms.date: 04/25/2022
ms.custom: bap-template
---

# Implement tax integration activities

[!include [banner](../includes/banner.md)]

This article provides information about how to implement the required activities for a new transaction.

Activities are the classes that complete the job in tax integration. A document object, `TaxIntegrationDocumentObject`, is passed from activity to activity. An activity is performed on the metadata in `TaxIntegrationDocumentObject`. All tax integration activities extend the `TaxIntegrationAbstractActivity` class and can be appended to a sequence and run by `TaxIntegrationFacade::calculate()` in the appended order.

Not all the activities must be implemented or modified to integrate a new transaction. In most cases, two specific activities are enough: `TaxIntegrationDataRetrievalActivityOnDocument` and `TaxIntegrationDataPersistenceActivityOnDocument`. If more features are enabled for the new transaction, see [Uptake features of tax integration](./tax-integration-uptake-features.md).

## Data retrieval activity

The data retrieval activity (`TaxIntegrationDataPersistenceActivityOnDocument`) copies all the metadata that's required for tax calculation from a database to a `TaxIntegrationDocumentObject` object.

This activity constructs and then calls a transaction-specific subclass of the `TaxIntegrationAbstractDataRetrievalTemplate` class, according to the `HeadingTableId` value of the current processed transaction in the factory pattern. Next, the subclass queries all the transaction lines, charges, and other useful information from the database and saves it to the document object.

To begin the data retrieval activity, create and implement a new subclass of `TaxIntegrationAbstractDataRetrievalTemplate`. Give the subclass a name, such as
`TaxIntegration***DataRetrieval`. The following list shows some of the data retrieval classes for the integrated transactions:

- AxClass/TaxIntegrationPurchTableDataRetrieval
- AxClass/TaxIntegrationPurchParmTableDataRetrieval
- AxClass/TaxIntegrationPurchREQTableDataRetrieval
- AxClass/TaxIntegrationPurchRFQTableDataRetrieval
- AxClass/TaxIntegrationVendInvoiceInfoTableDataRetrieval
- AxClass/TaxIntegrationSalesTableDataRetrieval
- AxClass/TaxIntegrationSalesParmDataRetrieval

The names consist of the prefix *TaxIntegration*, the header table name of the transaction, and then *DataRetrieval*. If the free text invoice transaction must be integrated, a `TaxIntegrationCustInvoiceTableRetrieval` class should be implemented.

### Implementing the data retrieval class

This section introduces the implementation of the data retrieval class. It uses `TaxIntegrationPurchTableDataRetrieval` as an example to provide an outline of this class.

```X++
[TaxIntegrationDataRetrieval(tableStr(PurchTable))]     // Attribute for TaxIntegrationDataRetrievalActivityOnDocument to call this class
public class TaxIntegrationPurchTableDataRetrieval extends TaxIntegrationAbstractDataRetrievalTemplate
{
    protected PurchTable purchTable;        // Header table buffer
    protected PurchLine purchLine;          // Line table buffer
    // Query builder methods, for the SQL query for framework to execute
    [Replaceable]
    protected SysDaQueryObject getDocumentQueryObject()
    [Replaceable]
    protected SysDaQueryObject getLineQueryObject()
    [Replaceable]
    protected SysDaQueryObject getDocumentChargeQueryObject()
    [Replaceable]
    protected SysDaQueryObject getLineChargeQueryObject()
    // Construct a TaxIntegrationLineObject
    protected TaxIntegrationLineObject constructLine()
    // Data retrieval methods, copy the metadata from table buffer to Document object.
    protected void copyToDocument()
    protected void copyToDocumentFromHeaderTable()
    protected void copyToLine(TaxIntegrationLineObject _line)
    protected void copyToLineFromLineTable(TaxIntegrationLineObject _line)
    ...
}
```

#### Declaration

The following example is from `TaxIntegrationPurchTableDataRetrieval.xpp`.

```X++
/// <summary>
/// The <c>TaxIntegrationPurchTableDataRetrieval</c> class retrieves data from <c>PurchTable</c>, etc.
/// </summary>
[TaxIntegrationDataRetrieval(tableStr(PurchTable))]
public class TaxIntegrationPurchTableDataRetrieval
    extends TaxIntegrationAbstractDataRetrievalTemplate
{
    // ...
```

The class is declared with the `[TaxIntegrationDataRetrieval(tableStr(PurchTable))]` attribute, which `TaxIntegrationDataRetrievalActivityOnDocument` uses to construct and call this class by factory pattern. The table name should be the transaction header table, and the table ID should be the same as the `HeadingTableId` value that's initialized in the `TaxIntegrationDocumentObject` object.

Refer to the `actStatic` method of `TaxIntegrationDataRetrievalActivityOnDocument.xpp`, which is shown here.

```X++
protected static void actStatic(TaxIntegrationDocumentObject _document)
{
    // ...
    TaxIntegrationAbstractDataRetrievalTemplate dataRetrievalInstance = SysExtensionAppClassFactory::getClassFromSysAttributeWithInstantiationStrategy(
        classStr(TaxIntegrationAbstractDataRetrievalTemplate),
        new TaxIntegrationDataRetrievalAttribute(tableId2Name(_document.getLocalTableId())),
        new SysExtensionGenericInstantiation(_document));
    /// ...
    dataRetrievalInstance.execute();
}
```

Declare at least two tables for each transaction. For this transaction, the header table and line table are declared. (For example, for purchase orders, the tables will be `PurchTable` and `PurchLine`.) If fields from other tables are used as input for the calculation, declare them here.

```X++
[TaxIntegrationDataRetrieval(tableStr(PurchTable))]
public class TaxIntegrationPurchTableDataRetrieval
    extends TaxIntegrationAbstractDataRetrievalTemplate
{
    protected PurchTable purchTable;
    protected PurchLine purchLine;
    protected TransportationDocument transportationDocument;    // Other tables through join relationship
    protected VendTable vendTable;
    private LedgerDimensionDefaultAccount ledgerAccount;
```

#### Create a query object

Queries in tax integration use the `SysDaQuery` method. After the implementation of several `get***QueryObject()` methods, the tax integration framework will call those methods, retrieve the data from the database, and assign it to the table buffer that was declared earlier.

Four query objects must be formatted so that you can perform the following queries:

- Query the header level tables by `HeadingTableId` and `HeadingRecId` values in `TaxIntegrationDocumentObject`. The header-level tables refer to tables that are related to the transaction header table (for example, `PurchTable` for purchase orders). If the document object is constructed with a record by `TaxIntegrationDocumentObject::constructWithRecord(Common _record)`, assign the header table to the buffer by using `this.document.getLocalRecord()` directly. The header table doesn't have to be queried again.
- Query the line table by the relationship between the header table and the line table, after the header table buffer is provided.
- Query the header charge (`MarkupTrans`).
- Query the line charge (`MarkupTrans`).

The following example is from `TaxIntegrationPurchTableDataRetrieval.xpp`.

```X++
/// <summary>
/// Gets the query for the document.
/// </summary>
/// <returns>The query for the document.</returns>
[Replaceable]
protected SysDaQueryObject getDocumentQueryObject()
{
    this.purchTable = this.document.getLocalRecord();
    SysDaQueryObjectBuilder queryObjectBuilder = SysDaQueryObjectBuilder::from(this.vendTable)
        .where(this.vendTable, fieldStr(VendTable, AccountNum))
            .isEqualTo(this.purchTable, fieldStr(PurchTable, OrderAccount))
        .outerJoin(this.transportationDocument) // primary key
            .where(this.transportationDocument, fieldStr(TransportationDocument, RecId))
                .isEqualTo(this.purchTable, fieldStr(PurchTable, TransportationDocument));
        .outerJoin(this.vendTableInvoice) // alternate key
            .where(this.vendTableInvoice, fieldStr(VendTable, AccountNum))
                .isEqualTo(this.purchTable, fieldStr(PurchTable, InvoiceAccount));
    return queryObjectBuilder.toSysDaQueryObject();
}
/// <summary>
/// Gets the query for the lines of the document.
/// </summary>
/// <returns>The query for the lines of the document</returns>
[Replaceable]
protected SysDaQueryObject getLineQueryObject()
{
    return SysDaQueryObjectBuilder::from(this.purchLine)
        .where(this.purchLine, fieldStr(PurchLine, PurchId))
            .isEqualToLiteral(this.purchTable.PurchId)
        .toSysDaQueryObject();
}
/// <summary>
/// Gets the query for the charges of the document.
/// </summary>
/// <returns>The query for the charges of the document</returns>
[Replaceable]
protected SysDaQueryObject getDocumentChargeQueryObject()
{
    return SysDaQueryObjectBuilder::from(this.markupTransOfDocument)
        .where(this.markupTransOfDocument, fieldStr(MarkupTrans, TransTableId))
            .isEqualToLiteral(this.purchTable.TableId)
        .where(this.markupTransOfDocument, fieldStr(MarkupTrans, TransRecId))
            .isEqualToLiteral(this.purchTable.RecId)
        .toSysDaQueryObject();
}
/// <summary>
/// Gets the query for the charges of each line.
/// </summary>
/// <returns>The query for the charges of each line.</returns>
[Replaceable]
protected SysDaQueryObject getLineChargeQueryObject()
{
    return SysDaQueryObjectBuilder::from(this.markupTransOfLine)
        .where(this.markupTransOfLine, fieldStr(MarkupTrans, TransTableId))
            .isEqualToLiteral(this.purchLine.TableId)
        .where(this.markupTransOfLine, fieldStr(MarkupTrans, TransRecId))
            .isEqualToLiteral(this.purchLine.RecId)
        .toSysDaQueryObject();
}
```

> [!NOTE]
> If fields from other tables are required, join them in the query object. In the preceding example, this approach is used for `transportationDocument` in the `getDocumentQueryObject()` method.

#### Construct the line object

```X++
/// <summary>
/// Constructs a line of the document.
/// </summary>
/// <returns>The constructed line of the document.</returns>
protected TaxIntegrationLineObject constructLine()
{
    return TaxIntegrationLineObject::constructOnDocument(
        this.purchLine.TableId,
        this.purchLine.RecId,
        this.document);
}
```

Construct a `TaxIntegrationLineObject` object by using the line's table ID and record ID. This method is called by the framework. Replace the table buffer for the new transaction.

#### Copy methods

Several methods that begin with *copy* must be implemented to copy metadata from the table buffer to the document object. For more information, see [Retrieve data from the database](./tax-service-add-data-fields-tax-integration-by-extension.md#step-2-retrieve-data-from-the-database). Because new classes should be created, you can disregard the information about extensions.

When you implement the methods, determine which fields are required for the Tax Calculation service, and copy only the required fields. For information about how to add new fields, see [Add the data variable in the object class](./tax-service-add-data-fields-tax-integration-by-extension.md#step-1-add-the-data-variable-in-the-object-class). For information about how to add them to the request, see [Add data to the request](./tax-service-add-data-fields-tax-integration-by-extension.md#step-3-add-data-to-the-request).

### Data persistence activity

When the data persistence activity (`TaxIntegrationDataPersistenceActivityOnDocument`) is run, the Tax Calculation service is called. The response is processed and saved to `TaxIntegrationDocumentObject`. The job of the data persistence activity is to update the required metadata in response to the database. The metadata includes the tax calculation results, tax group, tax item group, VAT ID, and list code.

Like the data retrieval class, `TaxIntegrationDataPersistenceActivityOnDocument` constructs and calls the data persistence class according to the `HeadingTableId` value of the current processed transaction. The work here is to implement a `TaxIntegration***DataPersistence` class. For example, the `TaxIntegrationCustInvoiceTableDataPersistence` class is implemented for free text invoices.

However, unlike the data retrieval activity, `TaxIntegrationDataPersistenceActivityOnDocument` does most of the persistence work, or tax calculation result, by itself. This part is handled by standard code. No additional work is required when a new transaction is integrated.

The new persistence class will save the transaction-specific fields (such as the tax group, tax item group, VAT ID, number sequence group, and list code) to the database.

The following example shows the basic structure of `TaxIntegrationPurchTableDataPersistence`.

```X++
/// <summary>
/// The <c>TaxIntegrationPurchTableDataPersistence</c> class persists data to <c>PurchTable</c>, etc.
/// </summary>
[TaxIntegrationDataPersistence(tableStr(PurchTable))] // Attribute for TaxIntegrationDataPersistenceActivityOnDocument to call
public class TaxIntegrationPurchTableDataPersistence
    extends TaxIntegrationAbstractDataPersistenceTemplate
{
    // Table buffer to be updated
    protected PurchTable purchTable;
    protected PurchLine purchLine;
    // Query builder methods
    [Replaceable]
    protected SysDaQueryObject getDocumentQueryObject()
    [Replaceable]
    protected SysDaQueryObject getLineQueryObject()
    [Replaceable]
    protected SysDaQueryObject getDocumentChargeQueryObject()
    [Replaceable]
    protected SysDaQueryObject getLineChargeQueryObject()
    // Get line object
    protected TaxIntegrationLineObject getLine()
    // Save to database
    protected boolean saveDocument()
    protected boolean saveLine(TaxIntegrationLineObject _line)
    ...
}
```

As the preceding example shows, the structure of the data persistence class resembles the structure of the data retrieval class. The only difference is that the data retrieval class copies data from the *database* to the *document object*, whereas the data persistence class copies data from the *document object* to the *database*. Here's a brief introduction to the implementation. Not all code examples will be attached.

- `[TaxIntegrationDataPersistence(tableStr(PurchTable))]` is an attribute for `TaxIntegrationDataPersistenceActivityOnDocument` to construct in the factory pattern.
- `QueryObject` is almost the same as for data retrieval, except for two points:

    - `.forUpdate()` is called for the persistence class to update data to the database.
    - The `Less` table is used because it must be updated.

- The `getLine()` method resembles the `constructLine()` method in the data retrieval class. However, it's enough to replace the table name with the new transaction table.
- Methods that begin with *save* are the main job in this class. For more information, see the next section.

#### Save methods

The following example is from `TaxIntegrationPurchTableDataPersistence`.

```X++
/// <summary>
/// Saves the document.
/// </summary>
/// <returns>Always true.</returns>
protected boolean saveDocument()
{
    TaxIntegrationTaxIdUtility::saveTaxIDFromDocumentToTable(document, purchTable);
    TaxIntegrationListCodeUtility::saveListCodeFromDocumentToTable(document, purchTable);
    this.saveNumberSequenceGroupToTable();
    return true;
}
/// <summary>
/// Saves the current line of the document.
/// </summary>
/// <param name = "_line">The current line of the document.</param>
/// <returns>true if the operation is successful; otherwise, false.</returns>
protected boolean saveLine(TaxIntegrationLineObject _line)
{
    if (!_line.isTaxable())
    {
        return true;
    }
    TaxGroup taxGroup = _line.getTaxGroup();
    TaxItemGroup taxItemGroup = _line.getTaxItemGroup();
    this.checkGroup(taxGroup, taxItemGroup);
    purchLine.TaxGroup = taxGroup;
    purchLine.TaxItemGroup = taxItemGroup;
    purchLine.doUpdate();
    return true;
}
```

The `saveDocument()` method updates fields in the header table, whereas the `saveLine()` method updates fields in the transaction line table.

Currently, the VAT ID, number sequence group, and list code are updated in the header table. In the `saveLine()` method, the tax group and item tax group that are returned by the Tax Calculation service must be updated. This requirement applies to most transactions.

> [!NOTE]
> To help avoid extra logic, use `doUpdate()` instead of `update()`.

[!include [banner](../includes/banner.md)]
