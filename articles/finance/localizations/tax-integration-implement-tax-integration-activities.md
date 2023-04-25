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

This article introduces how to implement necessary activities for a new transaction.

Activities are the classes that complete the job in tax integration. A `TaxIntegrationDocumentObject` is passed from activity to activity. An activity is performed on the metadata in `TaxIntegrationDocumentObject`. All Tax Integration activities extend `TaxIntegrationAbstractActivity` and can be appended to a sequence and executed by `TaxIntegrationFacade::calculate()` in the appended order.

To integrate a new transaction, not all of these activities need to be implemented or modified. In most cases, there are two specific activities that are enough. They are `TaxIntegrationDataRetrievalActivityOnDocument` and `TaxIntegrationDataPersistenceActivityOnDocument`. If more features are enabled for this new transaction, see [Uptake features of tax integration](./tax-integration-uptake-features.md).

## Data retrieval activity

Data retrieval activity copies all the metadata needed for tax calculation from a database to a `TaxIntegrationDocumentObject`.

In this activity, it will construct and then call a transaction-specific subclass of the `TaxIntegrationAbstractDataRetrievalTemplate` class according to the `HeadingTableId` of the current processed transaction in the factory pattern. Next, the subclass queries all the transaction lines, charges, and other useful information from the database and saves it to the document object.

To begin the data retrieval activity, create and implement a new subclass of `TaxIntegrationAbstractDataRetrievalTemplate`. Give the subclass a name. For example,
`TaxIntegration***DataRetrieval`. The following is a list of data retrieval classes for the integrated transactions:

- AxClass/TaxIntegrationPurchTableDataRetrieval
- AxClass/TaxIntegrationPurchParmTableDataRetrieval
- AxClass/TaxIntegrationPurchREQTableDataRetrieval
- AxClass/TaxIntegrationPurchRFQTableDataRetrieval
- AxClass/TaxIntegrationVendInvoiceInfoTableDataRetrieval
- AxClass/TaxIntegrationSalesTableDataRetrieval
- AxClass/TaxIntegrationSalesParmDataRetrieval
- ...

The names include *TaxIntegration* as a prefix, the header table name of the transaction, and *DataRetrieval*. If the free text invoice transaction is to be integrated, a `TaxIntegrationCustInvoiceTableRetrieval` class should be implemented.

### Implementing data retrieval class

This section introduces the implementation of the data retrieval class and uses `TaxIntegrationPurchTableDataRetrieval` as an example to introduce the outline of this class.

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

The class is declared with attribute `[TaxIntegrationDataRetrieval(tableStr(PurchTable))]`, which is used by the `TaxIntegrationDataRetrievalActivityOnDocument` to construct and call this class by factory pattern. The table name should be the transaction header table, and its table ID should be the same as `HeadingTableId` initialized in the `TaxIntegrationDocumentObject`.

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

Declare at least two tables for each transaction. For this transaction, it's the header table and line table. For purchase orders, it would be the PurchTable and PurchLine. If fields from other tables are used as input for the calculation, declare that here.

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

Queries in Tax Integration use the SysDaQuery method. After the implementation of several `get***QueryObejct()`, the tax integration framework will call these methods, retrieve the data from the database, and assign it to the table buffer declared above.
Four query objects must formatted so that you can:

- Query the header level tables by `HeadingTableId` and `HeadingRecId` in `TaxIntegrationDocumentObject`. The header level tables refer to tables related to the transaction header table, like `PurchTable` for purchase orders. If the document object is constructed with a record by `TaxIntegrationDocumentObject::constructWithRecord(Common _record)`, assign the header table to the buffer by `this.document.getLocalRecord()` directly. The header table doesn't to be queried again.
- Query the line table by the relationship between the header table and the line table, after the header table buffer is provided.
- Query the header charge (`MarkupTrans`).
- Query the line charge (`MarkupTrans`).

The following is an example from `TaxIntegrationPurchTableDataRetrieval.xpp`.

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
> If fields from other tables are needed, join them in the query object. For example, `transportationDocument` in the `getDocumentQueryObject()` method above.

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

Construct a `TaxIntegrationLineObject` by the line's table ID and record ID. This method is called by the framework. Replace the table buffer for the new transaction.

#### The copy methods

Several methods that start with "*copy*" must be implemented to copy metadata from the table buffer to the document object. For more information, see [Retrieve data from the database](./tax-service-add-data-fields-tax-integration-by-extension.md#step-2-retrieve-data-from-the-database). Because new classes should be created, you can disregard the information about extensions.

Determine which fields are necessary for the Tax Calculation service when you implement the methods and only copy the necessary fields.
To add new fields, see [Add the data variable in the object class](./tax-service-add-data-fields-tax-integration-by-extension.md#step-1-add-the-data-variable-in-the-object-class) and [Add data to the request](./tax-service-add-data-fields-tax-integration-by-extension.md#step-3-add-data-to-the-request) to add them to the request.

### Data persistence activity

When the data persistence activity is conducted, the tax calculation service is called. The response is processed and saved to `TaxIntegrationDocumentObject`. The job of the data persistence activity is to update the necessary metadata in response to the database. The metadata includes tax calculation results, tax group, tax item group, VAT ID, and list code.

Like the data retrieval class, `TaxIntegrationDataPersistenceActivityOnDocument` constructs and calls the data persistence class according to the `HeadingTableId` of the current processed transaction. The work here is to implement a `TaxIntegration***DataPersistence` class. For example, implement the `TaxIntegrationCustInvoiceTableDataPersistence` class for free text invoices.

However, unlike the data retrieval activity, most of the persistence work, or tax calculation result, is done by the `TaxIntegrationDataPersistenceActivityOnDocument` itself. This part is handled by standard code. No additional work is needed when integrating a new transaction.

The new persistence class will save the transaction-specific fields, like tax group, tax item group, VAT ID, number sequence group, and list code to the database.

The following is the basic structure of `TaxIntegrationPurchTableDataPersistence`:

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

In the example above, you can see that the data persistence class has a similar structure as the data retrieval class. The only difference is that the data retrieval class copies data from the *database* to the *document object*, while the data persistence copies data from the *document object* to the *database*. The following briefly introduces how to implement these. Not all code examples will be attached.

- `[TaxIntegrationDataPersistence(tableStr(PurchTable))]` is an attribute for `TaxIntegrationDataPersistenceActivityOnDocument` to construct in the factory pattern.
- QueryObject is almost the same as data retrieval, except for two points:
  - `.forUpdate()` is called for the persistence class to update data to the database.
  - The Less table is used because it needs to be updated.
- The `getLine()` method is similar to `constructLine()` in the data retrieval class, only replacing the table name with the new transaction table is enough.
- Methods starting with "*save*" are the main job in this class, will introduce more on it.

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

The `saveDocument()` method updates fields in the header table, while `saveLine()` updates fields in the transaction line table.
Currently, VAT ID, number sequence group, and list code are updated in the header table. the In `saveLine()` method, the tax group and item tax group returned by the tax calculation service must be updated. This is true for most transactions.

> [!NOTE]
> Use doUpdate() instead of update() to avoid extra logic.

[!include [banner](../includes/banner.md)]
