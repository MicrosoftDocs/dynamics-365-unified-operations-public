---
title: Tax engine integration
description: Learn about Tax engine integration, including outlines on tax engine integration models, debugging, and various examples.
author: Kai-Cloud
ms.author: kailiang
ms.topic: article
ms.date: 8/11/2026
ms.reviewer: twheeloc
audience: IT Pro 
ms.search.region: India
ms.search.validFrom: 2017-12-31
ms.search.form: ERSolutionTable, ERDataModelDesigner, ERModelMappingTable
ms.dyn365.ops.version: 7.3
---

# Tax engine integration

[!INCLUDE [banner](../includes/banner.md)]

To integrate the [Tax engine](../general-ledger/tax-engine.md) (GTE) with Dynamics 365 Finance, you must implement X++ code that interacts with the Tax engine for tax calculation, and that consumes the results to show, account, and post tax for voucher and tax transactions. The tax calculation can either include or exclude tax adjustments.

> [!NOTE]
> The Tax engine functionality is only available for legal entities with a primary address in India.

## Tax engine integration models

There are three models for Tax engine integration:

- Tax engine interfaces with the Tax engine service
- Tax business service
- Finance application integration:
  - Application integration
  - Accounting integration

:::image type="content" source="../general-ledger/media/gte-3-models.PNG" alt-text="Screenshot of the three Tax engine integration models.":::

### Tax engine interfaces with the Tax engine service model

This model is part of the Finance integration framework. Therefore, partners or customers don't need to make significant changes.

The ITaxEngine interface and its implementation contain the basic operations of the Tax engine. These operations include calculating tax through the tax engine, persisting the calculated result to Finance tables, retrieving the tax document for the transaction, and deleting the tax document from both the Tax engine cache and Finance tables.

The set of ITaxDocument interfaces and implementations enables information to be read from a tax document that the Tax engine calculates and returns. This set includes ITaxDocument, ITaxDocumentLine, ITaxDocumentField, ITaxDocumentComponentLine, and ITaxDocumentMeasure.

:::image type="content" source="../general-ledger/media/gte-itaxdocument_interfaces.jpg" alt-text="Screenshot of the ITaxDocument interfaces and implementations.":::

These interfaces provide methods for retrieving a specified field value (**ITaxDocumentField**) from ITaxDocumentLine and an expected measure value (**ITaxDocumentMeasure**) from ITaxDocumentComponentLine.

- The set of ITaxDocumentMetaData interfaces enables you to read model information from a tax document. This set includes ITaxDocumentMetaData, ITaxDocumentLineMetaData, ITaxDocumentComponentLineMetaData, and ITaxDocumentMeasureMetaData.
- The set of ITaxDocumentEnumerator and ITaxDocumentMeataDataEnumerator interfaces provides an enumerator to read a list of tax document–related objects, such as ITaxDocumentLine, ITaxDocumentField, ITaxDocumentComponentLine, and ITaxDocumentMeasure.

### Tax business service model

The Tax business service model is part of the Finance integration framework, and partners or customers don't need to take it up. This model supports the interactions that the Finance application has with the Tax engine for basic operations. It uses both the interface model and the application model to calculate, account, and post tax. The Tax business service model provides the following methods:

| **Method** | **Description** |
|---|---|
| CalculateTax | Delete a tax document if it's marked as **Dirty**, and then calculate tax.<br>- **Input**: Taxable document identifier<br>- **Output**: Tax document object |
| RecalculateTax | Explicitly recalculate a tax document.<br>- **Input**: Taxable document identifier<br>- **Output**: Tax document object |
| SaveTaxDocument | Persist a tax document to the Finance database.<br>- **Input**: Taxable document identifier<br>- **Output**: Not applicable |
| GetTaxDocumentBySource | Read a tax document, based on the source transaction identifier.<br>- **Input**: Taxable document identifier<br>- **Output**: Tax document object |
| GetTaxDocumentLineBySource | Read a tax document line, based on the source transaction line identifier.<br>- **Input**: Transaction line identifier<br>- **Output**: Tax document line object |
| GetTaxDocumentTaxStatus | Read the status of a tax document for the associated transaction.<br>- **Input**: Taxable document identifier<br>- **Output**: Tax document object |
| MarkTaxDocumentTaxStatus | Mark a tax document as **Dirty** when the underlying transaction is updated.<br>- **Input**: Taxable document identifier, Tax document status<br>- **Output**: Not applicable |
| DeleteTaxDocument | Delete a tax document when the transaction is deleted.<br>- **Input**: Taxable document identifier<br>- **Output**: Not applicable |
| PostTax | Post tax for the transaction.<br>- **Input**: Ledger voucher for the tax that must be posted, Taxable document identifier<br>- **Output**: Not applicable |
| TransferTaxDocument | Transfer a tax document from one transaction that the source supports to another transaction.<br>- **Input**: Source transaction, Target transaction<br>- **Output**: Not applicable |
| PostTaxDocument | Change the status of the tax document to **Posted**.<br>- **Input**: Taxable document identifier<br>- **Output**: Not applicable |

### Finance application integration

Send transaction information from Finance to the Tax engine. At the same time, align the accounting and posting of tax with the Finance implementation. Create three parts in the Finance application:

- Taxable document
- Tax accounting
- Tax posting

Use the integration transit document framework to maintain the relationship between the Finance transaction and the tax document.

#### Application integration

##### Taxable document

A taxable document encapsulates transaction information by using a set of data providers. A TaxableDocument object wraps transaction information. A TaxableDocumentDescriptor object in this object describes the transaction and lists a set of data providers that bind tax model attributes with transaction data.

:::image type="content" source="../general-ledger/media/gte-taxable-doc.png" alt-text="Screenshot of the taxable document structure and data providers.":::

The **TaxableDocumentDescriptor** class implements a set of TaxableDocumentTypeDefinition interfaces and describes the transaction. Technically, TaxableDocumentDescriptors are the Finance table bases, whereas TaxableDocumentTypeDefinitions are more business-driven and are used mainly for tax configuration conditions.

In the following example, TaxableDocumentDescriptorPurchaseOrderParm implements three interfaces that share the same PurchParmTable table.

:::image type="content" source="../general-ledger/media/gte-example-shared-table.png" alt-text="Screenshot of the example where three interfaces share the same PurchParmTable table.":::

If you add attributes to a tax configuration for lookup, condition, formula, or other configurations, bind the attributes with transaction data. Modify the corresponding data provider classes for a transaction so that they do this type of data binding.

> [!NOTE]
> If you want to support GTE for additional transactions, create related TaxableDocumentTypeDefinitions, TaxableDocumentDescriptors, and TaxableDocumentDataProviders.

##### Transit document

A transit document is an existing framework in Finance that is used for the following two purposes:

- Maintain the relationship between a transaction and a transit document.
- Transfer the document from one transaction to another transaction.

Use this framework to easily find a transaction's document and track the transit history. For example, create a tax document from VendInvoiceInfoTable, and then the transit document maintains the relationship between VendInvoiceInfoTable and TaxDocument. When you invoice a purchase order, transfer the tax document from VendInvoiceInfoTable to VendInvoiceJour.

> [!NOTE]
> If you want to support the Tax engine for additional transactions, define a rule for the transit document framework to describe which transaction should have a tax document at both the header level and the line level. Define the transit action from the source transaction to the target transaction.

#### Transaction integration

Transaction integration occurs only on a case-by-case basis. For each transaction and scenario, call the Tax business service in the appropriate manner for tax calculation, tax assumption, and tax posting. For an example, see the [Finance integration example – Purchase order invoice](#example-finance-integration--purchase-order-invoice) section later in this article.

#### Accounting integration

##### Tax accounting

The accounting of Finance transactions has two parts: source document accounting and nonsource document accounting. The same behavior applies to Tax engine tax accounting, which is integrated with the Finance implementation on both sides:

- For source document transactions, such as a purchase order or free text invoice, fetch the account information for tax when you create the tax document.
- For nonsource document transactions, such as a sales order or general journal, determine the account information when you post tax.

> [!NOTE]
> If any additional source document transaction requires Tax engine support, create source document–related classes to extend AccountingJournalizationRule and AccountingDistributionRule for the specified business event and monetary amount.

##### Tax engine tax posting

Currently, Tax engine tax posting generates TaxTrans, TaxTrans\_IN (if you're running under the India country/region code), and a related voucher for TaxTrans. To fill the **taxTrans** field with attributes or measures from the tax document, provide the mapping via **TaxAcctTaxTransTaxDocAttrMapping** and **TaxAcctTxTransTaxDocMeasureMapping**.

The following illustration shows how TaxTrans and the voucher are created.

:::image type="content" source="../general-ledger/media/gte-create-taxtrans-voucher.png" alt-text="Screenshot of how TaxTrans and the voucher are created.":::

> [!NOTE]
> To fill **taxTrans** fields with extra fields from the tax document, update the **TaxAcctTaxTransTaxDocAttrMapping** class, the **TaxAcctTxTransTaxDocMeasureMapping** class, or the extended classes of these classes for data binding.

## Example: Finance integration – Purchase order invoice

This section provides an example of how the Tax engine integrates with purchase order invoices. Related transaction tables include VendInvoiceInfoTable, VendInvoiceInfoLine, VendInvoiceJour, and VendInvoiceTrans.

### Integration checklist

The following table summarizes all relevant changes related to the integration with purchase order invoices.

| Transaction uptake checklist | | Description | AOT object |
|---|---|---|---|
| Definition | Define a taxable document. | Create the taxable document type and description to describe what the transaction is. | TaxableDocumentTypeDefinitionPurchaseInvoice<br>TaxableDocumentDescriptorPurchaseInvoice |
| Definition | Define data providers. | Create data providers to provide transaction data to GTE. | TaxableDocumentTypeDefinitionPurchaseInvoice<br>TaxableDocumentDescriptorPurchaseInvoice |
| Creation | Add the **Tax document** button on a transaction. | Add the **Tax document** button to the transaction pages. | VendEditInvoice<br>VendInvoiceInfoListPage |
| Creation | Integrate with transaction totals. | Create the tax document when the **Totals** button is clicked. | PurchTotals_ParmTrans.calcTax()<br>PurchTotals_ParmTransEdit.calcTax()<br>PurchTotals_ParmTransEditInvoice.calcTax() |
| Creation | Integrate with a source document. | Because a purchase invoice is a source document transaction, create a source document when tax is calculated. | AccDistRuleProductTaxMeasure<br>AccJourRuleVendPaymReqTaxMeasure |
| Deletion | Delete a transaction. | Delete the tax document when a transaction is deleted. | VendInvoiceInfoTable.delete() |
| Deletion | Delete a transaction line. | Recalculate tax when a transaction line is deleted. | VendInvoiceInfoLine.delete() |
| Update | Update transaction header information. | Recalculate tax when fields that affect tax are updated at the transaction header level. | VendInvoiceInfoTable.update() |
| Update | Update transaction line information. | Recalculate tax when fields that affect tax are updated on a transaction line. | VendInvoiceInfoLine.update() |
| Update | Update tax information. | Recalculate tax when tax information fields are updated. | TransTaxinformation.Write() (page data source) |
| Posting | Define a tax document transition rule. | Define a rule for the transfer of a tax document from one transaction to another transaction. | TaxDocumentTransitRuleEventHandler.initTransitDocumentTransactionRuleList() |
| Posting | Transfer a tax document. | Transfer the tax document from one transaction to another transaction during posting. | PurchaseInvoiceJournalCreate.endCreate() |
| Posting | Post tax. | Post tax during transaction posting. | PurchaseInvoiceJournalPost.PostTax() |
| Posting | Add inventory tax. | Add tax to inventory if a tax load on inventory is available. | PurchaseInvoiceJournalPost.PostInventory() |
| Posting | Post a tax document. | Post the tax document after the transaction voucher is posted. As a result, the tax document status is updated to **Posted**, and records are generated in relation tables. | PurchaseInvoiceJournalPost.endUpdate() |
| Inquiry | Add the **Tax document** button on a journal. | Add the **Tax document** button to the journal page for inquiry purposes. | VendInvoiceJournal |

### Define a taxable document

The classes **TaxableDocumentTypeDefintionPurchaseInvoice** and **TaxableDocumentDescriptorPurchaseInvoice** define a purchase invoice as a taxable document for the Tax engine.

:::image type="content" source="../general-ledger/media/gte-classes-taxable-document.png" alt-text="Screenshot of the taxable document classes for a purchase invoice.":::

TaxableDocumentTypeDefinitionPurchaseInvoice is the interface that defines a purchase invoice as a taxable document.

:::image type="content" source="../general-ledger/media/gte-purch-invoice-taxable-doc.png" alt-text="Screenshot of the interface that defines a purchase invoice as a taxable document.":::

**TaxableDocumentDescriptorPurchaseInvoice.getDataProvider()** specifies the data provider class that's used for a purchase invoice.

:::image type="content" source="../general-ledger/media/gte-data-provider-class-purch.png" alt-text="Screenshot of the data provider class that's used for a purchase invoice.":::

### Define data providers

The following illustration shows the data providers that send transaction data to the Tax engine for any tax-related operation.

:::image type="content" source="../general-ledger/media/gte-data-providers.png" alt-text="Screenshot of the data providers that send transaction data to the Tax engine.":::

**TaxableDocPurchaseInvoiceDataProvider.buildQuery()** provides a query for all related transactions, such as VendInvoiceInfoTable and VendInvoiceInfoLine. It also registers each data source with a row data provider. For example, the VendInvoiceInfoTable data source is registered with TableDocVendInvoiceInfoTableRowDP.

:::image type="content" source="../general-ledger/media/gte-example-vend-invoice.png" alt-text="Screenshot of the VendInvoiceInfoTable data source registered with a row data provider.":::

TaxableDocVendInvoiceInfoTableRowDP extends the **TaxableDocPurchTableRowDataProvider** class to set up transaction header–related information, whereas TaxableDocVendInvoiceInfoLineRowDP extends **TaxableDocPurchLineRowDataProvider** to set up invoice line–related information.

The following table lists the taxable document fields that Finance maps.

| Taxable document field    | Logic in the AOT object                   | Required                     | Default value |
|--------------------------------|-------------------------------|------------------------------|---------------|
| SubLines       | TaxableDocumentLineObject.getSubLines             | Yes                          | |
| Fields      | TaxableDocumentLineObject.getFields                                         | Yes                          | |
| ModelFieldName   | TaxableDocumentLineObject.parmModelFieldName                          | Yes                          | |
| TaxAdjustment   | TaxEngineIntegrationAXContractEventHandler.getLineAdjustment                | No                           | |
| TableId     | TaxableDocumentLineObject.getTransactionLineTableId                         | Yes                          | |
| RecId      | TaxableDocumentLineObject.getTransactionLineRecordId                        | Yes                          | |
| Taxable document type    | TaxableDocumentDescriptor.createRow                       | Yes                          | |
| Skipped (document level)       | TaxableDocumentDescriptor.createRow                  | Yes                          | No |
| DistributionSide    | TaxableDocumentObject.getDistributionSide                    | Yes                          | Auto |
| ExchangeRates      | TaxEngineIntegrationAXContractEventHandler.getExchangeRate           | Yes                          | |
| ReportingCurrencyExchangeRates | TaxEngineIntegrationAXContractEventHandler.getReportingCurrencyExchangeRate | Yes          | |
| Tax document purpose  | TaxableDocumentRowDataProviderLine.fillInFrameworkFields   | Yes             | Transaction |
| Transaction currency  | TaxableDocumentRowDataProviderLine.fillInFrameworkFields           | Yes                          | |
| Transaction date  | TaxableDocumentRowDataProviderLine.fillInFrameworkFields               | Yes                          | |
| Skipped (line level)  | TaxableDocumentRowDataProviderLine.fillInFrameworkFields        | Yes                          | No |
| Tax direction  | TaxableDocumentRowDataProviderLine.fillInFrameworkFields         | Yes               | Sales tax receivable |
| Post to ledger | TaxableDocumentRowDataProviderLine.fillInFrameworkFields         | Yes                          | Yes |
| Enable accounting  | TaxableDocumentRowDataProviderLine.fillInFrameworkFields          | Yes                          | Yes |
| Line type  | TaxableDocumentRowDataProviderLine.fillInFrameworkFields                    | Yes                          | Line |
| Import order | TaxableDocumentRowDataProviderHeader.fillInFields                           | Yes                          | No |
| Export order | TaxableDocumentRowDataProviderHeader.fillInFields                           | Yes                          | No |
| GST composition scheme| TaxableDocumentRowDataProviderHeader.fillInFields          | Yes                          | No |
| Composition scheme  | TaxableDocumentRowDataProviderHeader.fillInFields             | No                           | No |
| Customer type  | TaxableDocumentRowDataProviderHeader.fillInFields            | Yes                          | None |
| Provisional assessment | TaxableDocumentRowDataProviderHeader.fillInFields          | No                           | No |
| Foreign party | TaxableDocumentRowDataProviderHeader.fillInFields               | No                           | No |
| Nature of assessment | TaxableDocumentRowDataProviderHeader.fillInFields         | No                           | Company |
| Preferential party  | TaxableDocumentRowDataProviderHeader.fillInFields             | No                           | No |
| GTA-Commercial vendor | TaxableDocumentRowDataProviderHeader.fillInFields           | No                           | No |
| Ledger currency   | TaxableDocumentRowDataProviderHeader.fillInFields              | Yes                          | |
| Total discount percentage | TaxableDocumentRowDataProviderHeader.fillInFields           | No                           | |
| Exempt  | TaxableDocumentRowDataProviderLine.fillInFields                             | Yes                          | No |
| Purpose  | TaxableDocumentRowDataProviderLine.fillInFields                  | Yes                          | Transaction |
| Prices include sales tax | TaxableDocumentRowDataProviderLine.fillInFields          | Yes                          | No |
| Delivery date   | TaxableDocumentRowDataProviderLine.fillInFields                             | No                           | |
| DiscountAmount  | TaxableDocumentRowDataProviderLine.fillInFields                             | No                           | |
| Net amount   | TaxableDocumentRowDataProviderLine.fillInFields                             | No                           | |
| Quantity        | TaxableDocumentRowDataProviderLine.fillInFields                             | No                           | |
| Consumption state | TaxableDocumentRowDataProviderLine.fillInFields                 | No                           | |
| Return       | TaxableDocumentRowDataProviderLine.fillInFields                             | Yes                          | No |
| Disposition action | TaxableDocumentRowDataProviderLine.fillInFields               | No (Yes for a return)        | Credit |
| Assessable value | TaxableDocumentRowDataProviderLine.fillInFields                   | Yes                          | |
| Inter-state  | TaxableDocumentRowDataProviderLine.fillInFields                             | Yes                          | No |
| Import custom tariff code | TaxableDocumentRowDataProviderLine.fillInFields              | No (Yes for an import order) | |
| Export custom tariff code | TaxableDocumentRowDataProviderLine.fillInFields               | No (Yes for an export order) | |
| IEC number     | TaxableDocumentRowDataProviderLine.fillInFields                             | No                           | |
| Maximum retail price  | TaxableDocumentRowDataProviderLine.fillInFields            | No                           | |
| Party GST registration number| TaxableDocumentRowDataProviderLine.fillInFields            | Yes                          | |
| GST registration number    | TaxableDocumentRowDataProviderLine.fillInFields              | Yes                          | |
| HSN code      | TaxableDocumentRowDataProviderLine.fillInFields                             | Yes                          | |
| SAC        | TaxableDocumentRowDataProviderLine.fillInFields                             | Yes                          | |
| Service category  | TaxableDocumentRowDataProviderLine.fillInFields            | Yes                          | Inward |
| ITC category   | TaxableDocumentRowDataProviderLine.fillInFields                      | Yes                          | Input |
| Is scrap    | TaxableDocumentRowDataProviderLine.fillInFields                             | No (Yes for a sales order)   | No |

### Add the Tax document button on a transaction

You can trigger tax calculation in the Tax engine by adding a **Tax document** button to a transaction. When you select this button, the transactional data is sent to the Tax engine as a predefined taxable document object, and the Tax engine starts the tax calculation. Add the button to a transaction page, such as **VendEditInvoice**. The tax document user interface displays the tax calculation result as soon as it's available.

:::image type="content" source="../general-ledger/media/gte-vend-taxdocument.png" alt-text="Screenshot of the Tax document button on the Action Pane.":::

:::image type="content" source="../general-ledger/media/gte-vend-taxdocumentlauncher.png" alt-text="Screenshot of the taxdocumentlauncher properties.":::

### Integrate with transaction totals

The **Totals** button displays a transaction's financial information, such as the tax amount, discount amount, and total amounts. The tax amount that appears on the total page will also be added to the invoiced amount of the journal.

For an existing implementation of Finance, a set of **PurchTotals** classes is created to handle this functionality. Therefore, Tax engine-related code is inserted into the class's **calcTax** method to help guarantee that the expected tax total amount is initiated.

:::image type="content" source="../general-ledger/media/gte-trx-totals.png" alt-text="Screenshot of the calcTax method code for transaction totals.":::

For alignment with the existing logic, the existing **taxTotal** parameter is used to show the tax amount for the whole transaction. A new parameter that is named **taxTotalGTE** is used to show the tax that is posted to the vendor. In some cases, such as a reverse charge, the **taxTotal** value doesn't equal the **taxTotalGTE** value. Therefore, **taxTotal** will be used for journal posting, whereas **taxTotalGTE** will be used on **Totals** pages to show the total tax amount.

### Integrate with a source document

A purchase invoice is a source document transaction. Therefore, the calculated tax result from the Tax engine should be integrated with the existing source document framework in Finance. The main logic is already completed and handled by the Tax engine integration framework. However, for each source document transaction, the distribution and journalization rules should still be defined for accounting purposes.

:::image type="content" source="../general-ledger/media/gte-distribution-journalization-rule.jpg" alt-text="Screenshot of the distribution and journalization rules.":::

Three classes are created for a purchase invoice: **AccPolicyVendPaymReqForExpensedProducts**, **AccDistRuleProductTaxMeasure** and **AccJourRuleVendPaymReqExpPurchTaxMeasure**.

:::image type="content" source="../general-ledger/media/PurchaseOrderTaxAccountingPolicy.png" alt-text="Screenshot of the AccPolicyVendPaymReqForExpensedProducts class.":::

:::image type="content" source="../general-ledger/media/gte-class1.png" alt-text="Screenshot of the AcctDistRuleProductTaxMeasure class.":::

:::image type="content" source="../general-ledger/media/gte-class2.png" alt-text="Screenshot of the AccJourRuleVendPaymReqTaxMeasure class.":::

When you create the source document classes correctly, the distribution page shows calculated tax together with the component label, tax amount, and ledger account.

:::image type="content" source="../general-ledger/media/gte-accounting-distribution.png" alt-text="Screenshot of the accounting distributions page showing calculated tax.":::

### Delete a transaction

When you delete a purchase invoice, also delete the associated tax document. To delete an associated tax document, call TaxBusinessService in the **delete** method of VendInvoiceInfoTable.

:::image type="content" source="../general-ledger/media/gte-delete-trx.png" alt-text="Screenshot of the transaction deletion method code.":::

### Delete a transaction line

When you delete a transaction line, you need to recalculate the tax document. For performance reasons, GTE doesn't recalculate tax immediately after a transaction line is deleted. Instead, it updates the tax document's status to **Dirty**. When you retrieve a tax document so that you can view or post it, GTE checks whether the status is **Dirty**. Depending on the status, recalculation occurs.

:::image type="content" source="../general-ledger/media/gte-tax-doc-status1.png" alt-text="Screenshot of the tax document status code.":::

:::image type="content" source="../general-ledger/media/gte-tax-doc-status2.png" alt-text="Screenshot of the tax document status change code.":::

### Update transaction header information

Some transaction header information can affect tax calculation. Examples include the transaction date and currency. Therefore, when you update this type of information to a different value, mark the tax document as **Dirty** so that it can be recalculated later.

:::image type="content" source="../general-ledger/media/gte-trx-header-info.png" alt-text="Screenshot of the code that marks the tax document as Dirty when header information changes.":::

The following method lists fields that might affect tax calculation for a purchase invoice.

:::image type="content" source="../general-ledger/media/gte-tax-calc-purchase.png" alt-text="Screenshot of the method that lists fields that affect tax calculation for a purchase invoice.":::

### Update transaction line information

Similarly, updating some transaction line fields affects tax calculation.

:::image type="content" source="../general-ledger/media/gte-update-trx-line-info.png" alt-text="Screenshot of the transaction line fields that affect tax calculation.":::

### Update tax information

The tax information of a transaction line has a major effect on tax calculation. The logic is maintained on the Application Object Tree (AOT) **TransTaxInformation** page. This page might not require further uptake.

### Define a tax document transit rule

Define a rule to associate a purchase invoice and journal with the tax document. In **TaxDocumentTransitRuleEventHandler::initTransitDocumentRuleList()**, define rules for VendInvoiceInfoTable, VendInvoiceInfoLine, VendInvoiceJour, and VendInvoiceTrans to specify that the tax document or tax document row should be associated with the transaction table.

:::image type="content" source="../general-ledger/media/gte-tax-doc-transit-rule.png" alt-text="Screenshot of the tax document transit rule definition.":::

**TaxDocumentTransitRuleEventHandler::initTransitDocumentRuleExtList()** includes extended rule definitions of a transit action from the transaction to the journal.

:::image type="content" source="../general-ledger/media/gte-tax-doc-transit-rule-ext.png" alt-text="Screenshot of the extended tax document transit rule definitions.":::

### Transfer a tax document

When you create a journal from a transaction, transfer the tax document to the journal. The following code transfers a tax document from a purchase invoice to a purchase invoice journal.

:::image type="content" source="../general-ledger/media/gte-transfer-tax-document.png" alt-text="Screenshot of the code that transfers a tax document to a purchase invoice journal.":::

### Post tax

Tax posting occurs when you post the purchase invoice journal. Therefore, call **TaxBusinessService::PostTax()** in the **FormLetterJournalPost.postTax()** base class to post the purchase invoice journal.

:::image type="content" source="../general-ledger/media/gte-post-tax.png" alt-text="Screenshot of the code that posts tax for the purchase invoice journal.":::

### Add inventory tax

Add tax that must be posted to inventory to an inventory transaction.

The following example shows logic in the **Inventory** module that posts tax for inventory by using the **taxEngineInventMovement().updateTaxFinancial()** class method.

:::image type="content" source="../general-ledger/media/gte-purchinvoicejournalpost.png" alt-text="Screenshot of the code that posts tax for inventory.":::

### Post a tax document

After you post tax, update the tax document to a status that indicates the tax document is posted.

:::image type="content" source="../general-ledger/media/gte-tax-document-status.png" alt-text="Screenshot of the code that updates the tax document to a posted status.":::

When you call the preceding method, it creates an additional record in the TaxDocumentGeneralJournalEntryLink table to maintain the relationship between GeneralJournalEntry and the journal transaction. This record helps GTE fetch the tax document at the GeneralJournalEntry level.

:::image type="content" source="../general-ledger/media/gte-taxdocumentgeneraljournalentrylink.png" alt-text="Screenshot of the TaxDocumentGeneralJournalEntryLink table record.":::

## Debugging

Debug the Tax engine mainly by validating transaction data and the calculated tax document result. Both the transaction data and the calculated result are in JavaScript Object Notation (JSON) string format.

### Debugging transaction data

Set a breakpoint in **TaxEngineServiceProxy.calculate()**, as shown in the following illustration.

:::image type="content" source="../general-ledger/media/gte-debug-transaction-data.png" alt-text="Screenshot of the breakpoint set in TaxEngineServiceProxy.calculate for debugging transaction data.":::

**JsonStr** contains all the transaction data information that is prepared by data providers. You can use any online JSON viewer to easily identify whether data is correctly set for tax model attributes.

### Debugging the tax document

If the tax engine returns errors for a calculation, the preceding method sets all the results to the **RET** attribute. By using the Quick Watch command on the attribute, you can easily understand the full error from the tax engine.

If the tax engine returns no issues, persist the tax document result into the following tables:

- TaxDocument
- TaxDocumentRow
- TaxDocumentJson

By querying these tables to obtain the JSON string, you can easily check the result details via any online JSON viewer.

## Additional resources

- [Tax engine overview](../general-ledger/tax-engine.md)
- [Extend tax engine configurations](extend-tax-engine-configurations.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
