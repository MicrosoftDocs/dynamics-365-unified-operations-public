---
# required metadata

title: VAT setup details for VAT declaration in the United Kingdom
description: This topic provides details about the VAT setup for VAT declaration in the United Kingdom (UK).
author: liza-golub
ms.date: 08/17/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: United Kingdom
# ms.search.industry: 
ms.author: elgolu
ms.search.validFrom: 08/03/2021
ms.dyn365.ops.version: AX 10.0.22

---

# VAT setup details for VAT declaration in the United Kingdom

[!include [banner](../includes/banner.md)]

This topic provides details about the VAT setup for VAT declaration in the United Kingdom (UK).

Information about the administration of VAT in the UK can be found on the official website for the [Tax Authority of the UK – HM Revenue & Customs](https://www.gov.uk/topic/business-tax/vat).

After a company registers for VAT, they are required by law of the UK to charge VAT on your sales of goods and services. The comapny is also entitled to reclaim VAT on goods and services that you purchase.

There are currently three rates of VAT:

   - Standard rate: Applies to most goods and services.
   - Reduced rate: Applies to some goods and services, such as children’s car seats and home energy.
   - Zero rate percent (0%): Applies to zero-rate percent goods and services, such as most food and children’s clothes.

The VAT rate that a business charges depends on their goods and services. Some things, such as postage stamps, and financial and property transactions, are exempt from VAT. Some goods and services are outside the VAT tax system so you can't charge or reclaim the VAT on them. Rates can change and you must apply any changes to the rates from the date they change. For actuale information about VAT rates in the UK, see [VAT rates](https://www.gov.uk/vat-rates).

Companies that are registered for VAT in the UK must submit a VAT Return to HM Revenue and Customs (HMRC) on a periodical basis. VAT return must be submitted even if there's no VAT to pay or reclaim.

The VAT return for the UK is built in boxes:

Box 1: VAT due in the period on sales and other outputs
Box 2: VAT due in the period on acquisitions of goods made in Northern Ireland from EU member states
Box 3: Total VAT due
Box 4: VAT reclaimed in the period on purchases and other inputs, including acquisitions from the EU
Box 5: Net VAT to pay to HMRC or to reclaim
Box 6: Total value of sales and all other outputs, excluding any VAT
Box 7: Total value of purchases and all other inputs, excluding any VAT
Box 8: Total value of all supplies of goods and related costs, excluding any VAT, from Northern Ireland to EU member states (from 1st, January, 2021)
Box 9: Total value of acquisitions of goods and related costs, excluding any VAT, from EU member states to Northern Ireland (from 1st, January, 2021)

In Dynamics 365 Finance, the following setup must be completed to ensure that VAT returns are calculated correcly.

## Country/region type in Foreign trade parameters

1. Go to **Tax** > **Setup** > **Foreign trade** > **Foreign trade parameters**.
2. On the **Countries/regions properties** FastTab, set the country/region of the current legal entity to **Domestic**. 
3. If your current legal entity is in Northern Ireland, set the country/region of EU countries/regions that participate in EU trade with the current legal entity to **EU**. For each country/region, identify the country/region code for foreign trade purposes.
5. Set the country/region of of all other countries/regions that do business operation with the current legal entity to **Third country/region**. 

## Company tax registration in customer invoices

If your company is in Northern Ireland and provides services to counterparties in the EU, or if you trade in goods from locations in Great Britain (England, Scotland, and Wales) and Northern Ireland,  enable and use teh feature, **Company tax registration in customer invoices**.

1. Go to **Workspaces** > **Feature management**. 
2. Find **Company tax registration in customer invoices** in the feature list and then select **Enable** to activate the feature. 

Fore more information about feature management and available options, see [Feature management overview](../../fin-ops/get-started/feature-management/feature-management-overview.md).

With this feature, you can select the company tax registration ID when you post sales invoices or packing slips from:

- Sales orders
- Free text invoices
- Projects

You can also issue invoices that use the tax registration number of the company with **GB** (for England, Scotland, and Wales) or **XI** (for Northern Ireland) prefix.

To use the **Company tax registration in customer invoices** feature, the tax registration ID must be set up in the **Registration IDs** of your legal entity. For more information about how to setup registration ID master data, see [Registration IDs](emea-registration-ids.md).

When the **Company tax registration in customer invoices** feature is enabled, the registration type, which is the value in the **Primary for country** field, is assosiated with the VAT ID registration category. The registration type is used for the regiatration ID of the legal entity to define its tax registration number. This number is used as the default value in the **Tax registration number** field in sales orders during invoicing, packing slip posting, and project invoice proposal posting.

## Sales tax authoritiy

1. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax authorities**.
2. Select **New** to create a new record, and specify the parameters of the tax authority. Fore more information, see [Set up sales tax authorities](../general-ledger/tasks/set-up-sales-tax-authorities.md).
3. In the **Report layout** field, select **English report layout**.

## Sales tax settlement periods

1. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax settlement periods**.
2. Select **New** to create a new record, and specify the parameters of the sales tax settlement period. For more information, see[Set up sales tax settlement periods](../general-ledger/tasks/set-up-sales-tax-settlement-periods.md).
3. Make sure that the sales tax settlement periods you create correlate with the VAT obligation periods specified for your company's account in HMRC.

## Ledger posting groups

1. Go to **Tax** > **Setup** > **Sales tax** > **Ledger posting groups**.
2. Select **New** to create a new record, and specify the parameters of the ledger posting group to define the posting rules for VAT posting in your legal entity. The posting type of general ledger accounts for VAT should be **Sales tax**. For more information, see [Set up Ledger posting groups for sales tax](../general-ledger/tasks/set-up-ledger-posting-groups-sales-tax.md).

## Sales tax groups

1. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax groups**.
2. Select **New** to create a record and specify the parameters of the sales tax group. For more information, see [Set up sales tax groups and item sales tax groups](../general-ledger/tasks/set-up-sales-tax-groups-item-sales-tax-groups.md).
3. Create sales tax groups for different kinds of business operations that are applicable for your company. These can include, Accounts payable Domestic, Accounts payable Third country, Accounts receivable Domestic, Accounts receivable Third country, and Reverse charge VAT.

## Item sales tax groups

1. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Item sales tax groups**.
2. Select **New** to create a new record and specify the parameters of the item sales tax group. For more information, see [Set up sales tax groups and item sales tax groups](../general-ledger/tasks/set-up-sales-tax-groups-item-sales-tax-groups.md)
3. Specify the reporting type for the item sales tax group. For the **Reporting types** that are applicable for the business operations of your company, more than three **Item sales tax groups** are necessary. Tou can select from the following:

    - Full (Item)
    - Full (Service)
    - Reduced (Item)
    - Reduced (Service)
    - Zero (Item)
    - Zero (Service)
    - Reverse charge domestic (Reporting type = Empty)

## Sales tax codes

1. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax codes**.
2. Select **New** to create a new record and specify the parameters of the sales tax code. 
3. In the **Sales tax currency** field, select **GBP**. For more information, see [Set up sales tax codes](../general-ledger/tasks/set-up-sales-tax-codes.md).
4. In the **Country/region** field, select the country/region type the tax code will be used in.
5. For reverse charge VAT operations, create two **Sales tax codes**, one with a negative rate and one with a positive rate. For more information, see [Reverse charge mechanism for VAT/GST scheme](emea-reverse-charge.md).
6. Distribute the new sales tax codes into sales tax groups and item sales tax groups. Ensure that each sales tax code is added to an item sales tax group and a sales tax group, and that the nessesary field are specified on the **Setup** FastTab of the **Sales tax groups** page. The necessary fields include: 

      - Exempt
      - Exempt code
      - Reverse charge
      - Use tax 
   
   The combination of these groups must lead to one sales tax code, with an exeption for Reverse charge VAT setup), which Finance uses for VAT posting. These two groups, together with the **Country/region type** of the sales tax code, will result in reporting in different [boxes of VAT declaration](#boxes).

## <a name="boxes"></a>Boxes calculation for VAT declaration

The default setup of the VAT declaration that is proposed in the scope of the MTD VAT feature is explained in the topic, [Set up application-specific parameters for VAT Declaration format](emea-gbr-mtd-vat-integration-setup.md#declaration). The following algorithm is used to calculate the VAT return amounts.

| Box number | Short description    | Calculation description       |
|------------|----------------------|-------------------------------|
| Box 1      | VAT due in the period on sales and other outputs.   | To calculate the amount in this box, combine the tax amounts of tax transactions that are posted during the reporting period and that have the following classification values: <ul><li>Sales</li><li>SalesCreditNote</li><li>SalesReverseCharge</li><li>SalesReverseChargeCreditNote</li></ul> |
| Box 2      | VAT due in this period on intra-community acquisitions of goods made in Northern Ireland from EU member states.  | To calculate the amount in this box, combine the tax amounts of tax transactions that are posted during the reporting period, and that have a **Reporting type** value other than **Service**, a **Country/Region type** value of **EU**, and the following classification values: <ul><li>UseTax</li><li>UseTaxCreditNote</li></ul>  |
| Box 3      | Total VAT due.   | Box 1 + Box 2.   |
| Box 4      | VAT reclaimed in the period on purchases and other inputs (including acquisitions from the EU).   | To calculate the amount in this box, combine the tax amounts of tax transactions that are posted during the reporting period and that have the following classification values: <ul><li>Purchase</li><li>PurchaseCreditNote</li><li>PurchaseReverseCharge</li><li>PurchaseReverseChargeCreditNote</li><li>PurchaseExempt</li><li>PurchaseExemptCreditNote</li><li>UseTax</li><li>UseTaxCreditNote</li></ul> |
| Box 5      | Net VAT to pay to HMRC or reclaim. | The absolute value of the difference (Box 3 – Box 4).  |
| Box 6      | Total value of sales and all other outputs excluding any VAT.  | To calculate the amount in this box, combine the tax base amounts of tax transactions that are posted during the reporting period and that have the following classification values: <ul><li>Sales</li><li>SalesCreditNote</li><li>SalesReverseCharge</li><li>SalesReverseChargeCreditNote</li><li>SaleExempt</li><li>SalesExemptCreditNote</li></ul> |
| Box 7      | Total value of purchases and all other inputs excluding any VAT. | To calculate the amount in this box, combine the tax base amounts of tax transactions that are posted during the reporting period and that have the following classification values: <ul><li>Purchase</li><li>PurchaseCreditNote</li><li>PurchaseReverseCharge</li><li>PurchaseReverseChargeCreditNote</li><li>PurchaseExempt</li><li>PurchaseExemptCreditNote</li><li>UseTax</li><li>UseTaxCreditNote</li></ul>  |
| Box 8      | Total value of intra-community dispatches of goods and related costs (excluding VAT) from Northern Ireland to EU member states.        | To calculate the amount in this box, combine the tax base amounts of tax transactions that are posted during the reporting period, and that have a **Reporting type** other than **Service**, a **Country/Region type** value of **EU**, and the following classification values: <ul><li>SaleExempt</li><li>SalesExemptCreditNote</li><li>Sales</li><li>SalesCreditNote</li><li>SalesReverseCharge</li><li>SalesReverseChargeCreditNote</li></ul> |
| Box 9      | Total value of intra-community acquisitions of goods and related costs (excluding VAT) made in Northern Ireland from EU member states. | To calculate the amount in this box, combine the tax base amounts of tax transactions that are posted during the reporting period, and that have a **Reporting type** value other than **Service**, a **Country/Region type** value of **EU**, and the following classification values: <ul><li>UseTax</li><li>UseTaxCreditNote</li><li>Purchase</li><li>PurchaseCreditNote</li><li>PurchaseReverseCharge</li><li>PurchaseReverseChargeCreditNote</li><li>PurchaseExempt</li><li>PurchaseExemptCreditNote</li></ul> |

