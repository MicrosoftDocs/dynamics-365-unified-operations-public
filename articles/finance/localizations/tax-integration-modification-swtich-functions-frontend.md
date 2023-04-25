---
title: Modification on switch functions and front-end
description: This article explains the modifications on switch functions and front-end to integrate a new transaction.
author: Qiuchen-Ren
ms.author: qire
ms.reviewer: kfend
ms.topic: conceptual
ms.date: 04/12/2022
ms.custom: bap-template
---

# Modification on switch functions and front end

[!include [banner](../includes/banner.md)]

This article explains the modifications on switch functions and front-end to integrate a new transaction.

## Switch functions to enable the new transaction

The switch function controls whether tax integration should be applied to a specific transaction, header table, and line table. As a developer, extend the switch function to enable the new transaction.

In `Tax.xpp`, add the header and line table of new transactions according to the business process. Extend the method to return true for the header and line tables of the new transaction.

  ```X++
    /// <summary>
    /// Checks whether Tax Integration is enabled.
    /// </summary>
    /// <param name = "_refTableId">The table id.</param>
    /// <returns>Whether Tax Integration is enabled.</returns>
    public static boolean isTaxIntegrationEnabledForTable(RefTableId _refTableId)
    {
        if (TaxIntegrationFlight::instance().isEnabled()
            && TaxIntegrationTaxServiceParameters::find().IsEnable)
        {
            switch (_refTableId)
            {
                case tableNum(SalesTable):
                case tableNum(SalesLine):
                case tableNum(SalesParmTable):
                case tableNum(SalesParmLine):
                case tableNum(SalesQuotationTable):
                case tableNum(SalesQuotationLine):
                    return TaxIntegrationBusinessProcessTable::exist(TaxIntegrationBusinessProcess::Sales);
                case tableNum(PurchTable):
                case tableNum(PurchLine):
                case tableNum(VendInvoiceInfoTable):
                case tableNum(VendInvoiceInfoSubTable):
                case tableNum(VendInvoiceInfoLine):
                case tableNum(PurchParmTable):
                case tableNum(PurchParmLine):
                case tableNum(PurchReqLine):
                case tableNum(PurchRFQCaseTable):
                case tableNum(PurchRFQCaseLine):
                case tableNum(PurchRFQTable):
                case tableNum(PurchRFQLine):
                    return TaxIntegrationBusinessProcessTable::exist(TaxIntegrationBusinessProcess::Purchase);
                default:
                    return false;
            }
        }

        return false;
    }
  ```

## Modification on the front-end

Uptake the front-end modification to adapt to the tax integration business logic.

In the transaction form, make the **Override sales tax** control visible. Don't allow users to edit the tax group or the item tax group. The following example uses a sales quotation in the `init()` method of the `SalesQuotationTable` form:

  ```X++
        if (Tax::isTaxIntegrationEnabledForBusinessProcess(TaxIntegrationBusinessProcess::Sales))
        {
            SalesQuotationTable_ds.object(fieldNum(SalesQuotationTable, OverrideSalesTax)).visible(true);
            SalesQuotationLine_ds.object(fieldNum(SalesQuotationLine, TaxGroup)).allowEdit(false);
            SalesQuotationLine_ds.object(fieldNum(SalesQuotationLine, TaxItemGroup)).allowEdit(false);
            SalesQuotationLine_ds.object(fieldNum(SalesQuotationLine, OverrideSalesTax)).visible(true);
        }
  ```

  ![TaxGroup.png](./media/tax-group.png)

Find all buttons that can trigger tax calculation and reread the data source after tax calculation. Because during the calculation of tax integration, several fields are updated, the data source of the form also needs a refresh to reflect the changes. Using free text invoices as an example, the following code is from `CustFreeInvoice.xpp`:

  ```X++
    private void refreshDataSourceForTaxIntegration()
    {
        if (isTaxIntegrationEnabledForFTI)
        {
            CustInvoiceTable_ds.reread();
            CustInvoiceLine_ds.research(true);
        }
    }
  ```

Make a method for the form and then call this method after the tax calculation is triggered by UI action. For example:

  ```X++
    [Control("MenuFunctionButton")]
    class CustInvoiceTableTotals
    {
        public void clicked()
        {
            super();

            element.refreshDataSourceForTaxIntegration();
        }

    }
  ```

  Usually, there can be three buttons:

- **Sales tax** button on the Action Pane:

    ![TaxOnHeader.png](./media/tax-on-header.png)

- **Total** button on the Action Pane:

    ![TotalOnHeader.png](./media/total-on-header.png)

- **Sales tax** button on line:

    ![TaxOnLine.png](./media/tax-on-line.png)

If there are other buttons that trigger tax calculation, call the refresh in the clicked() method of those buttons.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
