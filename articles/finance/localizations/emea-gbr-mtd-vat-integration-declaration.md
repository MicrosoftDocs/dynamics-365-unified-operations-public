---
# required metadata

title: VAT setup details for VAT declaration of the United Kingdom
description: This topic gives an overview of details of VAT setup for VAT declaration of the United Kingdom (UK).
author: liza-golub
ms.date: 08/03/2021
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

# VAT setup details for VAT declaration of the United Kingdom

[!include [banner](../includes/banner.md)]

This topic gives an overview of details of VAT setup for VAT declaration of the United Kingdom (UK).

Information about the administration of VAT in the UK can be found on the official website for the Tax Authority of the UK – HM Revenue & Customs: https://www.gov.uk/topic/business-tax/vat.

Once a company is registered for VAT, this company is required by law of the UK to charge VAT on your sales of goods and services. The comapny is also entitled to reclaim VAT on Goods and Services that you have purchased.

There are currently three rates of VAT:

•	Standard rate - applies to most goods and services.

•	Reduced rate - applies to some goods and services, eg children’s car seats and home energy.

•	Zero rate	0% - applies to zero-rated goods and services, eg most food and children’s clothes.

The VAT rate businesses charge depends on their goods and services. Some things are exempt from VAT, such as postage stamps, financial and property transactions.
Some goods and services are outside the VAT tax system so you cannot charge or reclaim the VAT on them.
Rates can change and you must apply any changes to the rates from the date they change. For actuale information about VAT rates in the UK, see [VAT rates](https://www.gov.uk/vat-rates).

Company registered for VAT in the UK must submit a VAT Return to HM Revenue and Customs (HMRC) on periodical basis which is called accounting period. VAT return must be submitted even if ther is no VAT to pay or reclaim.

The VAT return for the UK is build in boxes:

Box 1: VAT due in the period on sales and other outputs

Box 2: VAT due in the period on acquisitions of goods made in Northern Ireland from EU Member States

Box 3: total VAT due

Box 4: VAT reclaimed in the period on purchases and other inputs (including acquisitions from the EU)

Box 5: net VAT to pay to HMRC or reclaim

Box 6: total value of sales and all other outputs excluding any VAT

Box 7: total value of purchases and all other inputs excluding any VAT

Box 8: total value of all supplies of goods and related costs, excluding any VAT, from Northern Ireland to EU Member States (from 1st January 2021)

Box 9: total value of acquisitions of goods and related costs, excluding any VAT, from EU Member States to Northern Ireland (from 1st January 2021)

In Dynamics 365 Finance, the described below setup must be done to ensure correctness of calculation of VAT return.

## Country/region type in Foreign trade parameters

1. Go to **Tax** > **Setup** > **Foreign trade** > **Foreign trade parameters**
2. Select **Countries/regions properties** fast tab
3. Set the country/region of the current legal entity to **Domestic**. 
4. If your current legal entity is in Northern Ireland, set the country/region of EU countries/regions that participate in EU trade with the current legal entity to **EU**. For each country/region, you also identify country/region code for foreign trade purposes.
5. Set the country/region of of all other countries/regions that do business operation with the current legal entity to **Third country/region**. 

## Company tax registration in customer invoices

If your company is in Northern Ireland and provides services to counterparties in EU, or if you trade in goods from locations 
in both Great Britain (England, Scotland, and Wales) and Northern Ireland, you should enable and use **Company tax registration in customer invoices** feature in **Feature management**.

1. Go to **Workspaces** > **Feature management**. 
2. Find **Company tax registration in customer invoices** and use button **Enable** to activate the feature. 

Find more information about feature management and available options in [Feature management overview](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview).

This feature allows to select company tax registration ID when user posts sales invoices or packing slips from:

- Sales order
- Free text invoice
- Projects.

This feature will let user to issue invoices that use tax registration number of the company with **GB** (for England, Scotland, and Wales) or **XI** (for Northern Ireland) prefix.

To use **Company tax registration in customer invoices** feature, tax registration ID must be set up in **Registration IDs** of your legal entity. Find more information about  how to setup registration ID master data in [Registration IDs](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/emea-registration-ids).

When **Company tax registration in customer invoices** feature is enabled, the **Registration type** that is set up as **Primary for country**, assosiated with **VAT ID** registration categoty and used for **Regiatratin ID** of the legal entity to define its tax registration number will be used as default value for **Tax registration number** field in sales orders during invoice and packing slip posting and in project invoice proposal posting.

## Sales tax authoritiy

1. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax authorities**.
2. Add **New** record and specify parameters of the tax authority. Find more information about how to [Set up sales tax authorities](https://docs.microsoft.com/en-us/dynamics365/finance/general-ledger/tasks/set-up-sales-tax-authorities).
3. Specify **English report layout** in the **Report layout** field.

## **Sales tax settlement periods**

1. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax settlement periods**.
2. Add **New** record and specify parameters of the sales tax settlement period. Use previously created **Sales tax authorities**. Find more information about how to [Set up sales tax settlement periods](https://docs.microsoft.com/en-us/dynamics365/finance/general-ledger/tasks/set-up-sales-tax-settlement-periods).
3. Make sure that setup of the **Sales tax settlement period** correlates with the VAT obligation periods specified for your company's account in HMRC.

## Ledger posting groups

1. Go to **Tax** > **Setup** > **Sales tax** > **Ledger posting groups**.
2. Add **New** record and specify parameters of the ledger posting group to define posting rules for the VAT posting in your legal entity. It is important that the G/L accounts for VAT are of **Sales Tax** **Posting pype**. Find more information about how to [Set up Ledger posting groups for sales tax](https://docs.microsoft.com/en-us/dynamics365/finance/general-ledger/tasks/set-up-ledger-posting-groups-sales-tax)

## Sales tax groups

1. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax groups**.
2. Add **New** record and specify parameters of the sales tax group. Find more information about how to [Set up sales tax groups and item sales tax groups](https://docs.microsoft.com/en-us/dynamics365/finance/general-ledger/tasks/set-up-sales-tax-groups-item-sales-tax-groups)
3. Add enough **Sales tax groups** for different kinds of business operations applicable for your company: Accounts payable Domestic, Accounts payable Third country, Accounts receivable Domestic, Accounts receivable Third country, Reverse charge VAT, etc.

## Item sales tax groups

1. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Item sales tax groups**.
2. Add **New** record and specify parameters of the item sales tax group. Find more information about how to [Set up sales tax groups and item sales tax groups](https://docs.microsoft.com/en-us/dynamics365/finance/general-ledger/tasks/set-up-sales-tax-groups-item-sales-tax-groups)
3. Specify **Reporting type** for item sales tax group. 
4. In relation with diferent **Reporting types** applicable for the business operations of your company, more than three **Item sales tax groups** are necessary:
- Full (Item)
- Full (Service)
- Reduced (Item)
- Reduced (Service)
- Zero (Item)
- Zero (Service)
- Reverse charge domestic (Reporting Type = empty)

## Sales tax codes

1. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax codes**.
2. Add **New** record and specify parameters of the sales tax code. It is important that the **Sales tax currency** is **GBP**. Use previously created **Ledger posting groups**, **Ledger posting groups**. Find more information about how to [Set up sales tax codes](https://docs.microsoft.com/en-us/dynamics365/finance/general-ledger/tasks/set-up-sales-tax-codes).
3. Specify for which country/region type the tax code will be used in **Country/region type** field.
4. For reverse charge VAT operations create two **Sales tax codes**: with negative and positive rate. Find more information about [Reverse charge mechanism for VAT/GST scheme](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/emea-reverse-charge).
5. Distribute **Sales tax codes** into previously created **Sales tax groups** and **Item sales tax groups**. Ensure that each **Sales tax code** is added to an **Item sales tax group** and a **Sales tax group** and nessesary properties are specified on **Setup** fast tab of the **Sales tax groups** page: Exempt, Exempt code, Reverse charge, Use tax. The combination of these groups must lead to **ONE** Sales tax code (with exeption for Reverse charge VAT setup), which Finance uses for VAT posting. Also these two groups together with the **Country/region type** of the **Sales tax code** will result in reporting in different [boxes of VAT declaration](#boxes).

## <a id="boxes"></a>Boxes calculation for VAT declaration

The default setup of the VAT declaration that is proposed in the scope of the MTD VAT feature is explaned in [Set up application-specific parameters for VAT Declaration format](emea-gbr-mtd-vat-integration-setup.md#declaration) section of this topic. It provides the following algorithm to calculate the VAT return amounts.

| Box number | Short description    | Calculation description       |
|------------|----------------------|-------------------------------|
| Box 1      | VAT due in the period on sales and other outputs   | To calculate the amount in this box, combine the tax amounts of tax transactions that are posted during the reporting period and that have the following classification values: <ul><li>Sales</li><li>SalesCreditNote</li><li>SalesReverseCharge</li><li>SalesReverseChargeCreditNote</li></ul> |
| Box 2      | VAT due in this period on intra-community acquisitions of goods made in Northern Ireland from EU Member States  | To calculate the amount in this box, combine the tax amounts of tax transactions that are posted during the reporting period, and that have a **Reporting type** value other than **Service**, a **Country/Region type** value of **EU**, and the following classification values: <ul><li>UseTax</li><li>UseTaxCreditNote</li></ul>  |
| Box 3      | Total VAT due   | Box 1 + Box 2.   |
| Box 4      | VAT reclaimed in the period on purchases and other inputs (including acquisitions from the EU)   | To calculate the amount in this box, combine the tax amounts of tax transactions that are posted during the reporting period and that have the following classification values: <ul><li>Purchase</li><li>PurchaseCreditNote</li><li>PurchaseReverseCharge</li><li>PurchaseReverseChargeCreditNote</li><li>PurchaseExempt</li><li>PurchaseExemptCreditNote</li><li>UseTax</li><li>UseTaxCreditNote</li></ul> |
| Box 5      | Net VAT to pay to HMRC or reclaim | The absolute value of the difference (Box 3 – Box 4).  |
| Box 6      | Total value of sales and all other outputs excluding any VAT  | To calculate the amount in this box, combine the tax base amounts of tax transactions that are posted during the reporting period and that have the following classification values: <ul><li>Sales</li><li>SalesCreditNote</li><li>SalesReverseCharge</li><li>SalesReverseChargeCreditNote</li><li>SaleExempt</li><li>SalesExemptCreditNote</li></ul> |
| Box 7      | Total value of purchases and all other inputs excluding any VAT | To calculate the amount in this box, combine the tax base amounts of tax transactions that are posted during the reporting period and that have the following classification values: <ul><li>Purchase</li><li>PurchaseCreditNote</li><li>PurchaseReverseCharge</li><li>PurchaseReverseChargeCreditNote</li><li>PurchaseExempt</li><li>PurchaseExemptCreditNote</li><li>UseTax</li><li>UseTaxCreditNote</li></ul>  |
| Box 8      | Total value of intra-community dispatches of goods and related costs (excluding VAT) from Northern Ireland to EU Member States        | To calculate the amount in this box, combine the tax base amounts of tax transactions that are posted during the reporting period, and that have a **Reporting type** other than **Service**, a **Country/Region type** value of **EU**, and the following classification values: <ul><li>SaleExempt</li><li>SalesExemptCreditNote</li><li>Sales</li><li>SalesCreditNote</li><li>SalesReverseCharge</li><li>SalesReverseChargeCreditNote</li></ul> |
| Box 9      | Total value of intra-community acquisitions of goods and related costs (excluding VAT) made in Northern Ireland from EU Member States | To calculate the amount in this box, combine the tax base amounts of tax transactions that are posted during the reporting period, and that have a **Reporting type** value other than **Service**, a **Country/Region type** value of **EU**, and the following classification values: <ul><li>UseTax</li><li>UseTaxCreditNote</li><li>Purchase</li><li>PurchaseCreditNote</li><li>PurchaseReverseCharge</li><li>PurchaseReverseChargeCreditNote</li><li>PurchaseExempt</li><li>PurchaseExemptCreditNote</li></ul> |

