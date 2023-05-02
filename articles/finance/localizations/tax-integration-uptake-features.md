---
title: Update features and functions 
description: This article introduces the features and functions that must be implemented to integrate a new transaction.
author: Qiuchen-Ren
ms.author: qire
ms.reviewer: kfend
ms.topic: conceptual
ms.date: 04/12/2022
ms.custom: bap-template
---

# Uptake features and functions

[!include [banner](../includes/banner.md)]

This article introduces the features and functions that you must implement to integrate a new transaction.

The following features and functionalities are supported in tax integration:

- Override sales tax
- Multiple VAT ID
- List code
- Cash discount

## Override sales tax

In tax integration, you can't edit the tax group and item tax group on a line, because taxes are determined by the Tax Calculation service. The **Override sales tax group** functionality lets you change the tax group or item tax group that's specified on a line to calculate sales tax. This calculation overrides the tax groups that are determined by the Tax Calculation service.

When the **Override sales tax** option is set to **Yes**, you can select a specific tax group and item tax group for tax calculation.

![Override sales tax option set to Yes.](./media/override-sales-tax.jpg)

Follow these steps to enable the functionality.

1. Add the **Override sales tax** field to the transaction line table schema and to the **Sales tax** section, if it exists.

    ![Override sales tax field added to the transaction line table schema.](./media/override-sales-tax-table-schema.jpg)

2. Set the default visibility to **false** on related transaction forms.
3. Map the **Override sales tax** field to the `SalesPurchJournalLine` map. This map is widely used in tax integration. If it isn't mapped, additional code might be required to realize the expected function.
4. Set the visibility and editability on the transaction form:

    - Set the default visibility to **false** on the transaction form data source.
    - Set the default visibility to **true** only if tax integration is enabled for this transaction.

        ```X++
        if (isTaxIntegrationEnabledForPurchase) // Condition should be modified according to the business process
        {
            PurchTable_ds.object(fieldNum(PurchTable, OverrideSalesTax)).visible(true);
            PurchLine_ds.object(fieldNum(PurchLine, OverrideSalesTax)).visible(true);
        }
        ```

    - Add an `allowEdit` control to the transaction form to control the editability of the tax group and item tax group. There are usually three places to add this control:

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

5. Set the value of the override sales tax in the data retrieval activity.

    `line.setOverrideSalesTax(this.vendInvoiceInfoLine.OverrideSalesTax);`

6. To keep the design consistent, the new charge will enter the default override sales tax from its origin. Modify `MarkupTrans::getOverrideSalesTaxFromParentRecord(MarkupTransRefTableId _tableId, MarkupTransRefRecId _refRecId)` for new transaction support.
7. Optional: Modify related entities to support the import and export of override sales tax.

## Multiple VAT ID

The **Multiple VAT ID** feature enables the value-added tax (VAT) ID to be determined from the Tax Calculation service. This feature is controlled by the **Support multiple VAT registration numbers** feature. For more information, see [Multiple VAT registration numbers](./emea-multiple-vat-registration-numbers.md).

![Support multiple VAT registration numbers feature in Feature management.](./media/vat-id-feature.jpg)

Two registration numbers must be determined and saved in this feature: the registration number for the tax authority of the current legal entity and the registration number for the counterparty. If a transaction doesn't have a customer or vendor as a counterparty, the counterparty registration number won't work for it.

> [!NOTE]
> There are only one legal entity registration number and one counterparty registration number for all lines in a transaction. Most of the code for this feature is done in `TaxIntegrationTaxIdActivityOnDocument.xpp`.

### Database schema

The **TaxId** and **PartyTaxId** data fields are used for the record IDs of registration numbers. These two fields are added to the following related tables to store the registration numbers of a transaction:

- TmpTaxWorkTrans
- TaxUncommitted
- TaxTrans
- CustPackingslipJour
- CustInvoiceJour
- VendPackingSlipJour
- VendInvoiceJour

The first three tables in the preceding list (tax-related tables) are line-level tables, whereas the last four are header-level tables, because one transaction should have the same registration number.

### Registration number for the legal entity

The legal entity registration number is enabled by the **Support multiple VAT registration numbers** feature. Nothing is required here for a new transaction. If the tax code is determined, the legal entity registration number is filled in by the registration number that's assigned to the settlement period of that tax code. It's determined at `TaxIntegrationTaxIdActivityOnDocument::populateTaxLineTaxId()` and saved to the database together with the tax result.

There's also validation logic for the legal entity registration number, in case a different registration number is determined for different lines in a transaction. This validation is done at `TaxIntegrationTaxIdActivityOnDocument::checkTaxIdConsistency()`.

### Counterparty registration number

The counterparty registration number is determined by the Tax Calculation service. After the response is received, the number is validated and saved to the database together with the legal entity registration number. However, if the number that's determined by the Tax Calculation service isn't in the user's master data, the default value on the transaction header will be written to the database instead of the returned value. The counterparty registration number isn't applied to all transactions. However, there's extra logic to handle this approach.

#### Default logic

There's default logic from customer and vendor master data to the transaction header. You can set the **Tax-exempt number** value at the customer and vendor master data levels. When a new transaction is created, the default tax-exempt number is entered on it. However, you can select a new number to override the default number. If the number that's returned by the tax service isn't valid, the number on the header before tax calculation will be used as the default number.

The tax-exempt number is a string field (**VATNum**) instead of a record ID, and it has two data sources. One data source is from the tax registration number, and the other is from the tax-exempt number. Tax integration supports only the tax registration number as its source. Two new fields, **VATNumRecId** and **VATNumTableType**, should be added to the appropriate tables to distinguish the record.

When a new transaction is added, decide whether the **VATNum**, **VATNumRecId**, and **VATNumTableType** fields should be added to the transaction header table. If they should be added, also add the table to `TaxExemptVATNumMap`. The record ID and table type will then automatically be saved to the header table when users select a number in the user interface (UI).

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

2. If there's no counterparty, or if the counterparty registration number isn't applicable to the new transaction, skip the counterparty logic at `TaxIntegrationTaxIdActivityOnDocument::shouldSetPartyTaxId()`.

    ```X++
    protected static boolean shouldSetPartyTaxId(TaxIntegrationDocumentObject _document)
    {
        // Sales quotation for a prospect customer doesn't apply to the counterparty VAT ID
        if (_document.getHeadingTableId() == tableNum(SalesQuotationTable) && _document.getCustVendAccount() == '')
            return false;
        // Currently for purchase order and sales order, the party tax ID is set only if returned by the tax service.
        // For Transfer Order, its party tax ID isn't determined by the tax service and must be set for the first calculation round.
        return _document.isPartyTaxIdReturned()
            || ((_document.getBusinessProcess() == TaxIntegrationBusinessProcess::Inventory)
                && !(TaxInventTransferCalcTaxContext::current() && TaxInventTransferCalcTaxContext::current().parmShouldSkipSetPartyTaxId()))
            // If a default exists, always go through the tax ID process.
            || _document.getPartyTaxIdRecIdDefault();
    }
    ```

### Number sequence group

The number sequence group is part of the **Multiple VAT ID** feature. When the VAT ID is updated on the transaction header, the corresponding number sequence group should also be updated. However, the update doesn't apply to all transactions. If the number sequence group should be integrated into the new transaction, use the following example in the data persistence activity.

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

The determination is done in the tax ID activity for all transactions. Add and call the logic in the data persistence activity to persist the number sequence group.

## List code

The list code resembles the counterparty VAT ID in that both are determined by the service and persist in the database. The list code feature is always enabled if the list code applicability matrix is configured in Regulatory Configuration Service (RCS).

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

A `SalesPurchJournalTable` map is used in the data persistence class to reduce duplicate code. Map the list code from the header table to the map.

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

If your transaction table isn't mapped to this `SalesPurchJournalTable` map, write your own logic in the data persistence activity to update the list code.

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

This functionality is enabled by default. Set the transaction currency, the fixed exchange rate for the reporting currency, and the fixed exchange rate for the accounting currency in the document object. This action is done by the `TaxIntegrationCurrencyExchangeActivityOnDocument` activity, which is called without any condition in `TaxIntegrationFacade`. No action is required on your part to uptake this functionality.

## Cash discount

If the cash discount function is already supported for the new transaction in your finance and operations apps, tax integration also enable the cash discount parameters to be determined by the Tax Calculation service. Here's a brief overview of the process for enabling this functionality.

1. In the code base, find all references of cash discount parameters.
2. Replace the references of cash discount parameters with parameters from the Tax Calculation service. The parameters can be retrieved by one of two methods:

    - `TaxIntegrationFacade:: getTaxJurisdictionParameters(RefTableId _sourceHeadingTableId, RefRecId _sourceHeadingRecId)`
    - `TaxIntegrationFacade::getTaxJurisdictionParametersByTable(Common _sourceHeadingTable)`

3. Extend the switch functions to enable the new transaction:

    - `TaxIntegrationUtils::shouldRetrieveCashDiscParametersFromTaxService(RefTableId _refTableId, RefRecId _refRecId)`
    - `TaxIntegrationUtils::getBusinessProcessBySourceHeadingTable(RefTableId _sourceHeadingTableId, RefRecId _sourceHeadingRecId)`

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
