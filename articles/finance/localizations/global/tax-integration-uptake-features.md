---
title: Uptake features and functions 
description: Learn about the features and functions that must be implemented to integrate a new transaction, including an overview overriding sales tax.
author: Qiuchen-Ren
ms.author: qire
ms.topic: how-to
ms.date: 03/19/2026
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Uptake features and functions

[!include [banner](../../includes/banner.md)]

This article introduces the features and functions you need to implement to integrate a new transaction.

Tax integration supports the following features and functionalities:

- Override sales tax
- Multiple VAT ID
- List code
- Cash discount

## Override sales tax

In tax integration, you can't edit the tax group and item tax group on a line, because the Tax Calculation engine determines taxes. By using the **Override sales tax group** functionality, you can change the tax group or item tax group on a line for calculating sales tax. This calculation overrides the tax groups that the Tax Calculation engine determines.

When you set the **Override sales tax** option to **Yes**, you can select a specific tax group and item tax group for tax calculation.

:::image type="content" source="../media/override-sales-tax.jpg" alt-text="Screenshot of the Override sales tax option set to Yes.":::

Follow these steps to enable the functionality.

1. Add the **Override sales tax** field to the transaction line table schema and to the **Sales tax** section, if it exists.

    :::image type="content" source="../media/override-sales-tax-table-schema.jpg" alt-text="Screenshot of the Override sales tax field added to the transaction line table schema.":::

2. Set the default visibility to **false** on related transaction forms.
3. Map the **Override sales tax** field to the `SalesPurchJournalLine` map. This map is widely used in tax integration. If you don't map it, you might need extra code to realize the expected function.
4. Set the visibility and editability on the transaction form:

    - Set the default visibility to **false** on the transaction form data source.
    - Set the default visibility to **true** only if you enable tax integration for this transaction.

        ```X++
        if (isTaxIntegrationEnabledForPurchase) // Condition should be modified according to the business process
        {
            PurchTable_ds.object(fieldNum(PurchTable, OverrideSalesTax)).visible(true);
            PurchLine_ds.object(fieldNum(PurchLine, OverrideSalesTax)).visible(true);
        }
        ```

    - Add an `allowEdit` control to the transaction form to control the editability of the tax group and item tax group. Usually, add this control in three places:

        - The `init()` method of the form
        - The `active` method of line
        - The `modified()` method of the **Override sales tax** field

        ```X++
        if (isTaxIntegrationEnabledForPurchase) // Condition should be modified according to the business process
        {
            PurchLine_ds.object(fieldNum(PurchLine, TaxGroup)).allowEdit(purchLine.OverrideSalesTax == NoYes::Yes);
            PurchLine_ds.object(fieldNum(PurchLine, TaxItemGroup)).allowEdit(purchLine.OverrideSalesTax == NoYes::Yes);
        }
        ```

1. Set the value of the override sales tax in the data retrieval activity.

    `line.setOverrideSalesTax(this.vendInvoiceInfoLine.OverrideSalesTax);`

1. To keep the design consistent, the new charge enters the default override sales tax from its origin. Modify `MarkupTrans::getOverrideSalesTaxFromParentRecord(MarkupTransRefTableId _tableId, MarkupTransRefRecId _refRecId)` for new transaction support.
1. (Optional) Modify related entities to support the import and export of override sales tax.

## Multiple VAT ID

The **Multiple VAT ID** feature enables the value-added tax (VAT) ID to be determined from the Tax Calculation engine. The **Support multiple VAT registration numbers** feature controls this feature. For more information, see [Multiple VAT registration numbers](emea-multiple-vat-registration-numbers.md).

:::image type="content" source="../media/vat-id-feature.jpg" alt-text="Screenshot of the Support multiple VAT registration numbers feature in Feature management.":::

You must enter and save two registration numbers in this feature: the registration number for the tax authority of the current legal entity and the registration number for the counterparty. If a transaction doesn't have a customer or vendor as a counterparty, the counterparty registration number doesn't work for it.

> [!NOTE]
> There's only one legal entity registration number and one counterparty registration number for all lines in a transaction. Most of the code for this feature is in `TaxIntegrationTaxIdActivityOnDocument.xpp`.

### Database schema

The **TaxId** and **PartyTaxId** data fields are used for the record IDs of registration numbers. Developers add these two fields to the following related tables to store the registration numbers of a transaction:

- TmpTaxWorkTrans
- TaxUncommitted
- TaxTrans
- CustPackingslipJour
- CustInvoiceJour
- VendPackingSlipJour
- VendInvoiceJour

The first three tables in the preceding list (tax-related tables) are line-level tables. The last four tables are header-level tables, because one transaction should have the same registration number.

### Registration number for the legal entity

When you enable the **Support multiple VAT registration numbers** feature, you also enable the legal entity registration number. You don't need to enter anything here for a new transaction. If the system determines the tax code, it fills in the legal entity registration number with the registration number that's assigned to the settlement period of that tax code. The system determines this number at `TaxIntegrationTaxIdActivityOnDocument::populateTaxLineTaxId()` and saves it to the database together with the tax result.

The system also includes validation logic for the legal entity registration number in case it determines different registration numbers for different lines in a transaction. The system performs this validation at `TaxIntegrationTaxIdActivityOnDocument::checkTaxIdConsistency()`.

### Counterparty registration number

The Tax Calculation engine determines the counterparty registration number. After the system receives the response, it validates the number and saves it to the database together with the legal entity registration number. However, if the Tax Calculation engine determines a number that isn't in the user's master data, the system writes the default value on the transaction header to the database instead of the returned value. The counterparty registration number doesn't apply to all transactions. However, the system includes extra logic to handle this approach.

#### Default logic

The system applies default logic from customer and vendor master data to the transaction header. You can set the **Tax-exempt number** value at the customer and vendor master data levels. When you create a new transaction, the system enters the default tax-exempt number on it. However, you can select a new number to override the default number. If the number that the tax engine returns isn't valid, the system uses the number on the header before tax calculation as the default number.

The tax-exempt number is a string field (**VATNum**) instead of a record ID, and it has two data sources. One data source is from the tax registration number, and the other is from the tax-exempt number. Tax integration supports only the tax registration number as its source. You should add two new fields, **VATNumRecId** and **VATNumTableType**, to the appropriate tables to distinguish the record.

When you add a new transaction, decide whether to add the **VATNum**, **VATNumRecId**, and **VATNumTableType** fields to the transaction header table. If you add these fields, also add the table to `TaxExemptVATNumMap`. The record ID and table type are then automatically saved to the header table when users select a number in the user interface (UI).

A developer must identify the default logic and call `copyPrimaryRegistrationNumberToVATMap` to copy the two fields to the newly created transaction header table. Use the following default code from `CustTable` to `SalesTable` as an example in `SalesTable.xpp`.

```X++
private void initRegistrationNumbers(CustTable _custTable)
{
    this.vatNum = _custTable.getPrimaryRegistrationNumber(TaxRegistrationTypesList::TAXID);
    _custTable.copyPrimaryRegistrationNumberToVATMap(this);     // This line is to copy the new fields.
    this.EnterpriseNumber = _custTable.getPrimaryRegistrationNumber(TaxRegistrationTypesList::UID);
}
```

#### Switch function

1. Modify the switch function to support the new transaction during journalization:

    `TaxIntegrationUtils::isMultipleTaxIdEnabledForJournalV3(RefTableId _journalHeaderTableId, RefRecId _journalHeaderRecId, Tax _tax = null)`

1. If there's no counterparty, or if the counterparty registration number doesn't apply to the new transaction, skip the counterparty logic at `TaxIntegrationTaxIdActivityOnDocument::shouldSetPartyTaxId()`.

    ```X++
    protected static boolean shouldSetPartyTaxId(TaxIntegrationDocumentObject _document)
    {
        // Sales quotation for a prospect customer doesn't apply to the counterparty VAT ID
        if (_document.getHeadingTableId() == tableNum(SalesQuotationTable) && _document.getCustVendAccount() == '')
            return false;
        // Currently for purchase order and sales order, the party tax ID is set only if returned by the tax engine.
        // For Transfer Order, its party tax ID isn't determined by the tax engine and must be set for the first calculation round.
        return _document.isPartyTaxIdReturned()
            || ((_document.getBusinessProcess() == TaxIntegrationBusinessProcess::Inventory)
                && !(TaxInventTransferCalcTaxContext::current() && TaxInventTransferCalcTaxContext::current().parmShouldSkipSetPartyTaxId()))
            // If a default exists, always go through the tax ID process.
            || _document.getPartyTaxIdRecIdDefault();
    }
    ```

### Number sequence group

The number sequence group is part of the **Multiple VAT ID** feature. When you update the VAT ID on the transaction header, update the corresponding number sequence group. However, this update doesn't apply to all transactions. If you need to integrate the number sequence group into the new transaction, use the following example in the data persistence activity.

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

The tax ID activity determines this value for all transactions. Add and call the logic in the data persistence activity to persist the number sequence group.

## List code

The tax engine determines the list code, which resembles the counterparty VAT ID, and persists it in the database. Always enable the list code feature if you configure the list code applicability matrix in Tax calculation feature.

### Data retrieval

Retrieve the default list code to `TaxIntegrationDocument`. Add a line in the `copyToDocumentFromHeaderTable` method of the newly created data retrieval class.

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

The data persistence class uses a `SalesPurchJournalTable` map to reduce duplicate code. Map the list code from the header table to the map.

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

If you don't map your transaction table to this `SalesPurchJournalTable` map, write your own logic in the data persistence activity to update the list code.

### Data persistence

Call the `TaxIntegrationListCodeUtility::saveListCodeFromDocumentToTable()` method in the `saveDocument` method of the newly created data persistence class.

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

### Currency exchange, rounding, and penny difference adjustment

This functionality is enabled by default. Set the transaction currency, the fixed exchange rate for the reporting currency, and the fixed exchange rate for the accounting currency in the document object. The `TaxIntegrationCurrencyExchangeActivityOnDocument` activity performs this action. `TaxIntegrationFacade` calls this activity without any condition. You don't need to take any action to use this functionality.

## Cash discount

If your finance and operations apps already support the cash discount function for the new transaction, tax integration also enables the Tax Calculation engine to determine the cash discount parameters. Here's a brief overview of the process for enabling this functionality.

1. In the code base, find all references to cash discount parameters.
1. Replace the references to cash discount parameters with parameters from the Tax Calculation engine. You can retrieve the parameters by using one of two methods:

    - `TaxIntegrationFacade::getTaxJurisdictionParameters(RefTableId _sourceHeadingTableId, RefRecId _sourceHeadingRecId)`
    - `TaxIntegrationFacade::getTaxJurisdictionParametersByTable(Common _sourceHeadingTable)`

1. Extend the switch functions to enable the new transaction:

    - `TaxIntegrationUtils::shouldRetrieveCashDiscParametersFromTaxService(RefTableId _refTableId, RefRecId _refRecId)`
    - `TaxIntegrationUtils::getBusinessProcessBySourceHeadingTable(RefTableId _sourceHeadingTableId, RefRecId _sourceHeadingRecId)`

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
