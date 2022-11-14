---
title: Implement tax integration activities
description: This article introduces the activities that must be implemented to integrate a new transaction.
author: Qiuchen-Ren
ms.author: qire
ms.reviewer: kfend
ms.topic: conceptual
ms.date: 11/14/2022
ms.custom: bap-template
---

# Implement tax integration activities

[!include [banner](../includes/banner.md)]

The activities are the classes that really do the job in tax integration. A `TaxIntegrationDocumentObject` is passed from activity to activity. Activity is performed on the metadata in `TaxIntegrationDocumentObject`. All Tax Integration activities implement `TaxIntegrationAbstractActivity`, they can be appended to a sequence and executed by `TaxIntegrationFacade::calculate()` in the appended order.

To integrate a new transaction, not all of these activities need to be implemented or modified. In most cases, only 2 activities are enough. They are `TaxIntegrationDataRetrievalActivityOnDocument` and `TaxIntegrationDataPersistenceActivityOnDocument`. If more features are to enabled for this new transaction, please refer to [Uptake features of tax integration](./tax-integration-uptake-features.md) after this wiki.

## Data Retrieval Activity

Data retrieval activity copies all metadata needed for tax calculation from a database to a `TaxIntegrationDocumentObject`.

In this activity, it will first contruct and call a transaction-specific subclass of `TaxIntegrationAbstractDataRetrievalTemplate` class according to the `HeadingTableId` of the current processed transaction in factory pattern.

Then this subclass will query all the transaction lines and other useful information from database and save them to document object.

So the work here is to create and implement a new subclass of `TaxIntegrationAbstractDataRetrievalTemplate` and name it like
`TaxIntegration***DataRetrieval`. There already exist some data retrieval classes for integrated transactions:

- AxClass/TaxIntegrationPurchTableDataRetrieval
- AxClass/TaxIntegrationPurchParmTableDataRetrieval
- AxClass/TaxIntegrationPurchREQTableDataRetrieval
- AxClass/TaxIntegrationPurchRFQTableDataRetrieval
- AxClass/TaxIntegrationVendInvoiceInfoTableDataRetrieval
- AxClass/TaxIntegrationSalesTableDataRetrieval
- AxClass/TaxIntegrationSalesParmDataRetrieval
- ...

The names are consist of a *TaxIntegration* prefix, the header table name of transaction, and *DataRetrieval*. If the free text invoice transaction is to be integrated, a `TaxIntegrationCustInvoiceTableRetrieval` class should be implemented.

### Implementation of data retrieval class

This section introduces the implementation of data retrieval class.

First, Take `TaxIntegrationPurchTableDataRetrieval` as an example to introduce the outline of this class:

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

`TaxIntegrationPurchTableDataRetrieval.xpp:`

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

The class is declared with attribute `[TaxIntegrationDataRetrieval(tableStr(PurchTable))]`, which is used by the `TaxIntegrationDataRetrievalActivityOnDocument` to construct and call this class by factory pattern. The table name should be the transaction header table, which table id should be the same with `HeadingTableId` initialized in the `TaxIntegrationDocumentObject`.

Refer to `actStatic` method of `TaxIntegrationDataRetrievalActivityOnDocument.xpp`:

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

Then, declare at least 2 tables for each transaction, which are the header table and line table for this transaction. For purchase order, they are PurchTable and PurchLine. If other tables are used as input for the calculation, also declare it here.

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

#### Create query object

Queries in Tax Integration use the SysDaQuery method. After implementation of several `get***QueryObejct()`, the tax integration framework will call these methods, retrieve the data from the database and assign it to the table buffer declared above.
Four query object needs to be formatted. The idea is to:

1. Query the header level tables by `headingTableId` and `headingRecId` in `TaxIntegrationDocumentObject`. The header level tables refers to tables related to the transaction header table, like `vendTable` for purchase order.
   - Note, just assign the header table to the buffer directly, if the document object is constructed with record by `TaxIntegrationDocumentObject::constructWithRecord(Common _record)`. The header table is not needed to be queried again.
2. Query the line table by the relationship between header table and line table, after header table buffer is provided.
3. Query the header charge (`MarkupTrans`).
4. Query the line charge (`MarkupTrans`).

Example from `TaxIntegrationPurchTableDataRetrieval.xpp`:

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
> If some other tables are also needed, join them in the query object. Like, `transportationDocument` in the above `getDocumentQueryObject()` method.
#### Construct line object

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

Construct a `TaxIntegrationLineObject` by the line's table ID and record ID. This method is called by the framework, just replace the table buffer for the new transaction.

#### The copy methods

A bunch of methods that starts with *copy* need to be implemented to copy metadata from table buffer to document object. Please refer to [Step 2. Retrieve data from the database](./tax-service-add-data-fields-tax-integration-by-extension.md#step-2-retrieve-data-from-the-database) for this part. Just ignore the extension part, since new classes should be created.
Please decide which fields are necessary for tax calculation service when implementing these methods. Only copy the necessary metadata.
If new fields need to be added, also refer to [Step 1. Add the data variable in the object class](./tax-service-add-data-fields-tax-integration-by-extension.md#step-1-add-the-data-variable-in-the-object-class) and [Step 3. Add data to the request](./tax-service-add-data-fields-tax-integration-by-extension.md#step-3-add-data-to-the-request) to add them to the request.

Till now, the job of data retrieval activity is done.

### Data Persistence Activity

When data persistence activity is conducted, the tax calculation service has been called. The response has been processed and saved to `TaxIntegrationDocumentObject`. The job of data persistence activity is to update the necessary metadata in response to the database, including tax calculation result, tax Group, tax item group, VAT ID, list code and etc.

Like data retrieval class, `TaxIntegrationDataPersistenceActivityOnDocument` will construct and call the DataPersistence class according to the HeadingTableId of the current processed transaction. So the work here is to implement a `TaxIntegration***DataPersistence` class. Like `TaxIntegrationCustInvoiceTableDataPersistence` class for free text invoice.

However, unlike data retrieval activity, most of the persistence work (tax calculation result) is done by the `TaxIntegrationDataPersistenceActivityOnDocument` itself. This part is handled by standard code, no extra effort is needed when integrating a new transaction.

So the only work of the newly created persistence class is to save the transaction specific fields to databse, like tax group, tax item group, VAT ID, number sequence group and list code.

Also, below is the basic structure of `TaxIntegrationPurchTableDataPersistence`

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

It is obvious that in the above example that the data persistence class has a similar structure as the data retrieval class. The only difference is data retrieval class copies data from *database* to *document object*, while the data persistence copies data from *document object* to *database*. So will briefly introduce how to implement them in this part, will not attach all code example.

- `[TaxIntegrationDataPersistence(tableStr(PurchTable))]` is attribute for `TaxIntegrationDataPersistenceActivityOnDocument` to constrct in factory pattern.
- QueryObject is the same, except for 2 points:
  - `.forUpdate()` is called for persistence class is to update data to database.
  - Less table is used, for less table need to be updated.
- `getLine()` method is similar to `constructLine()` in the data retrieval class, only replace the table name with the new transaction table is enough.
- Methods start with "*save*" is the main job in this class, will introduce more on it.

#### Save methods

Example from `TaxIntegrationPurchTableDataPersistence`:

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

The `saveDocument()` method is to update fields in the header table, while `saveLine()` update fields in the transaction line table.
Currently, VAT ID, number sequence group and list code are updated to the header table, we will cover this part in the features uptake page.
In `saveLine()` method, the tax group and item tax group returned by tax calculation service need to be updated. This is true for most transactions.

> [!NOTE]
> Use doUpdate() instead of update() to avoid extra logic.
