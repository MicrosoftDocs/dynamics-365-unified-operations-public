---
title: Update features and functions 
description: This article introduces the features and functions that must be implemented to integrate a new transaction.
author: Qiuchen-Ren
ms.author: qire
ms.reviewer: kfend
ms.topic: conceptual
ms.date: 11/16/2022
ms.custom: bap-template
---

# Uptake features and functions

[!include [banner](../includes/banner.md)]

There is new functionality that is now supported in the tax integration of Dynamis 365 Finance. This functionality includes:

  - Override sales tax
  - Multiple VAT ID
  - List code
  - Cash discount

## Override sales tax

In tax integration, you can't edit the tax group and item tax group on a line item because taxes determined by the tax calculation service. The **Override sales tax group** functionality allows you to change the tax group or item tax group specified on a line item to calculate sales tax. This calculation overrides the tax groups determined by tax calculation service.

A new slider is added beside the tax group and item tax group. When **Override sales tax** is set to **Yes**, you can select a specific tax group and item tax group for tax calculation.

  ![OverrideSalesTax.jpg](./media/override-sales-tax.jpg)

Complete the following steps to enable this functionality.
**
1. Add the **Override Sales tax** field to the transaction line table schema.
    - Also add it to *Sales tax* field group if it exist.
    - Map it the **SalesPurchJournalLine** map. This map is used widely in tax integration. If not mapped, additional code may be need to realize the expected function.
    
     ![OverrideSalesTaxTableSchema.jpg](./media/override-sales-tax-table-schema.jpg)
     
2. Add `allowEdit` control to transaction form to control the editability of tax group and item tax group. Usually, 3 places to add:

    ```X++
            if (isTaxIntegrationEnabledForPurchase)
            {
                PurchLine_ds.object(fieldNum(PurchLine, TaxGroup)).allowEdit(purchLine.OverrideSalesTax == NoYes::Yes);
                PurchLine_ds.object(fieldNum(PurchLine, TaxItemGroup)).allowEdit(purchLine.OverrideSalesTax == NoYes::Yes);
            }
    ```

   - the `init()` method of the form
   - the `active` method of line
   - the modified() method of override sales tax field.

3. Set the value of override sales tax in data retrieval activity.
   
   `line.setOverrideSalesTax(this.vendInvoiceInfoLine.OverrideSalesTax);`

4. To keep the design consistent, the newly created charge will default override sales tax from it's origin. Modify `MarkupTrans::getOverrideSalesTaxFromParentRecord(MarkupTransRefTableId _tableId, MarkupTransRefRecId _refRecId)` for new transaction support.
5. (Optional) Modify related entity to support import/export of override sales tax.

## Multiple VAT ID

Multiple VAT ID(VAT ID, also known as registration number) is a feature that enables the determination of VAT ID from tax calculation service. It is controlled by feature management named **Support multiple VAT registration numbers**, see below pics. Please refer to [Multiple VAT registration numbers](./emea-multiple-vat-registration-numbers.md) for details.

  ![VATIDfeature.jpg](./media/vat-id-feature.jpg)

Two registration numbers need to be determined and saved in this feature, the registration number for the tax authority of the current legal entity, and the registration number for the counterparty. If the transaction does not have a customer or vendor as a counterparty, the counterparty registration number will not work for it.

> [!Note]
> There will be only one LE registration number and one counterparty registration number for all lines in a transaction.
Most code of this feature is done in `TaxIntegrationTaxIdActivityOnDocument.xpp`.

### DB schema

Two data fields(TaxId and PartyTaxId, which are the record IDs of registration numbers)) are added to related tables to store the registration numbers of a transaction. The tables are:

- TmpTaxWorkTrans
- TaxUncommitted
- TaxTrans
- CustPackingslipJour
- CustInvoiceJour
- VendPackingSlipJour
- VendInvoiceJour

The tax-related tables are line level tables, and the last 4 are header level tables since 1 transaction should have the same registration number.

### Registration number for legal entity

This part is relatively easy compared with the counterparty. LE registration number is enabled and mandatory if **Support multiple VAT registration numbers** is enabled. The determination and flow of LE VAT ID are:

  ![legal entity VAT ID](./media/le-vat-id.png)

LE registration number is enabled by the feature, and nothing to be done here for new transaction. As long as the tax code is determined, the LE registration number will be filled by the registration number assigned to the settlement period of that tax code.

It is determined at `TaxIntegrationTaxIdActivityOnDocument::populateTaxLineTaxId()` and saved to database together with the tax result.

There is also a validation logic for the LE registration number, in case different registration numer is determined for various lines in a transaction. Basically, it is done at `TaxIntegrationTaxIdActivityOnDocument::checkTaxIdConsistency()`.

### Counterparty Registration number

The counterparty registration number is determined by Tax calculation service. After received the response, it will be validated and saved to DB together with the LE registration number. However, if the number returned by the service is not in the user's master data, the default value on the transaction header will be written to the database instead of the returned one. Besides, the counterparty registration number is not applied to all transactions, there is extra logic to handle this.

#### Default logic

Originally there exists a default logic from customer/vendor master data to transaction header. We can set **Tax exempt number** at customer/vendor master data. When a new transaction is created, the exempt number will default to it. Users can also select a new number to override the default one. That number on the header before tax calculation will be used as the default number, if the number returned by the tax service is invalid.
But the tax exempt number is a string field(VATNum) instead of a record ID, and it has 2 data sources, not only from the tax registration number but tax exempt number. So 2 new fields(VATNumRecId, VATNumTableType) should be added to the below tables to distinguish the record:
When a new transaction is added, one should decide if similar fields should be added. If yes, also add the table to TaxExemptVATNumMap, then the record ID and table type will be saved to the header table automatically when users select a number from UI.
Also, need to identify the default logic and call `copyPrimaryRegistrationNumberToVATMap` to copy the 2 fields to the newly created transaction. Take the default code from customer table to sales order as an example, `SalesTable.xpp`:

```X++
    private void initRegistrationNumbers(CustTable _custTable)
    {
        this.vatNum = _custTable.getPrimaryRegistrationNumber(TaxRegistrationTypesList::TAXID);
        _custTable.copyPrimaryRegistrationNumberToVATMap(this);     // This line is to copy the new fields.
        this.EnterpriseNumber = _custTable.getPrimaryRegistrationNumber(TaxRegistrationTypesList::UID);
    }
```

#### Switch function

1. Modify switch function to support the new transaction when journalizing: `TaxIntegrationUtils::isMultipleTaxIdEnabledForJournalV3(RefTableId _journalHeaderTableId, RefRecId _journalHeaderRecId, Tax _tax = null)`.
2. If there is no counterparty, or counterparty registration number is not applicable for the new transaction, we should skip the counterparty logic at `TaxIntegrationTaxIdActivityOnDocument::shouldSetPartyTaxId()`:

    ```X++
        protected static boolean shouldSetPartyTaxId(TaxIntegrationDocumentObject _document)
        {
            // Sales Quotation for prospect customer does not apply to counterparty VAT ID
            if (_document.getHeadingTableId() == tableNum(SalesQuotationTable) && _document.getCustVendAccount() == '')
                return false;
            // Currently for PO and SO, party tax ID is set only if returned by tax service.
            // But for Transfer Order, its party tax ID doest not determined by tax service, it needs to set it for the first calculation round.
            return _document.isPartyTaxIdReturned()
                || ((_document.getBusinessProcess() == TaxIntegrationBusinessProcess::Inventory)
                    && !(TaxInventTransferCalcTaxContext::current() && TaxInventTransferCalcTaxContext::current().parmShouldSkipSetPartyTaxId()))
                // If default exists, always go through tax ID process.
                || _document.getPartyTaxIdRecIdDefault();
        }
    ```

### Number sequence group

Number sequence group is part of VAT ID feature. When VAT ID is updated to transction header, the corresponding number sequence group should also be updated. But it does not apply to all transactions. If it should be integrated to the new transaction added, follow below example in data persistence activity:

``` X++
    private void saveNumberSequenceGroupToTable()
    {
        NumberSequenceGroupId numberSequenceGroupId = document.getNumberSequenceGroupId();
        if (numberSequenceGroupId && custInvoiceTable.numberSequenceGroup != numberSequenceGroupId)
        {
            ttsbegin;
            custInvoiceTable.numberSequenceGroup = document.getNumberSequenceGroupId();
            custInvoiceTable.doUpdate();
            ttscommit;
        }
    }
```

The determination is done in Tax ID activity for all transactions, just add and call the logic in data persistence activity to persist the number sequence group.

## List Code

List code is similar with counterparty VAT ID, they are both determined by service and persist to the database. List code feature is always enabled, if list code tab is configured at RCS. The integration of list code is much easier.

### Data retrieval

Retrieve the default list code to `TaxIntegrationDocument`. Just add a line in the `copyToDocumentFromHeaderTable` of the newly created Data Retrieval class.

```X++
    protected void copyToDocumentFromHeaderTable()
    {
        super();
        ...
        document.setListCode(this.purchTable.ListCode);
        ...
    }
```

### Map list code to map

A SalesPurchJournalTable map is used in data persistence class to reduce duplicate code. So map the list code from header table to the map.

```X++
        <AxTableMapping>
        <MappingTable>SalesPurchJournalTable</MappingTable>
            <Connections>
                ...
                <AxTableMappingConnection>
                    <MapField>ListCode</MapField>
                    <MapFieldTo>ListCode</MapFieldTo>
                </AxTableMappingConnection>
            </Connections>
        </AxTableMapping>
```

If your transaction table is not mapped to this SalesPurchJournalTable. Just write your own logic in data persistence activity to update list code.

### Data persistence

Call the `TaxIntegrationListCodeUtility::saveListCodeFromDocumentToTable()` method in the `saveDocument` method of newly created Data Persistence class:

```X++
    /// <summary>
    /// Saves the document.
    /// </summary>
    /// <returns>Always true.</returns>
    protected boolean saveDocument()
    {
        TaxIntegrationTaxIdUtility::saveTaxIDFromDocumentToTable(document, salesTable);
        TaxIntegrationListCodeUtility::saveListCodeFromDocumentToTable(document, salesTable);
        return true;
    }
```

### Currency exchange/Rounding/penny difference adjustment

This function is enabled by default, just set the transaction currency, reporting currency fixed exchange rate and accounting currency fixed exchange rate to the document object. It is been done by `TaxIntegrationCurrencyExchangeActivityOnDocument` which is called in `TaxIntegrationFacade` without any condition. There is nothing to do to uptake it.

## Cash discount

Tax integration also provide function to determine the cash discount parameters by tax calculation service. Here just give a brief introduction on how to enable this funciton.

1. Replace the reference of cash discount parameters with parameters get tax calculation service. The parameters can be retrieved by any one of the 2 methods: `TaxIntegrationFacade:: getTaxJurisdictionParameters(RefTableId _sourceHeadingTableId, RefRecId _sourceHeadingRecId)` and  `TaxIntegrationFacade::getTaxJurisdictionParametersByTable(Common _sourceHeadingTable)`
2. Modify switch functions to enable the new transaction: `TaxIntegrationUtils::shouldRetrieveCashDiscParametersFromTaxService(RefTableId _refTableId, RefRecId _refRecId)` and `TaxIntegrationUtils::getBusinessProcessBySourceHeadingTable(RefTableId _sourceHeadingTableId, RefRecId _sourceHeadingRecId)`.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
