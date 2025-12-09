---
title: Set up and report value-added tax (VAT)
description: Learn how to set up and report value-added tax (VAT) for United Arab Emirates (UAE) in Microsoft Dynamics 365 Finance.
author: liza-golub
ms.author: johnmichalak
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 12/09/2025
ms.reviewer: johnmichalak
ms.search.region: UAE
ms.search.validFrom: 2019-05-29
---

# Set up and report value-added tax (VAT)

[!include [banner](../../includes/banner.md)]

This article explains how to set up and report value-added tax (VAT) for the United Arab Emirates (UAE) in Microsoft Dynamics 365 Finance.

The United Arab Emirates (UAE) introduced value-added tax (VAT) on January 1, 2018. Businesses in the UAE are responsible for carefully documenting their business income, costs, and associated VAT charges.

Registered businesses and traders charge VAT to all their customers at the current rate, and they incur VAT on goods and services that they buy from suppliers. The difference between these sums is reclaimed or paid to the government. Federal Decree Law No. (8) of 2017 on Value Added Tax outlines the tax scope, rate, responsibility for tax, and supply of goods and services in all cases. These cases include supply in special cases, supply of more than one component, supply via agent, supply by government entities, and cases of deemed supply. For more detailed information about VAT regulations, see the [Federal Tax Authorities of United Arab Emirates website](https://government.ae/information-and-services/finance-and-investment/taxation/valueaddedtaxvat).

## <a name="header-information"></a>Configure a legal entity for VAT

According to the *Requirements Document for Tax Accounting Software* that the Federal Tax Authority (FTA) issued, you must set up additional information when you configure a legal entity.

To configure a legal entity for VAT, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration** \> **Organizations** \> **Legal entities**.
1. On the **Value added tax** FastTab, set the following fields:

    - **Taxable person name** – Electronic VAT reports require the name of the taxable person. Reports include names in English and Arabic. If you set the user interface (UI) language of the legal entity to English, you can use the **Known as** field on the **Global address book** page to store names in another language, such as Arabic.
    - **Tax agency name** and **Tax agent name** – When a contracted tax agent or vendor prepares electronic VAT reports, you must provide the name and Tax Agency Number (TAN) of the tax agency, and the name and Tax Agent Approval Number (TAAN) of the tax agent.
    - **Declarant name** – The electronic VAT report includes information about the person who prepares a VAT declaration.
    - **VAT refund required (if any)** – Set this option to **Yes** if a VAT refund is due and the company requests to receive it.
    - **Profit margin scheme** – Set this option to **Yes** if the company operates in a special business scheme by using the Profit Margin scheme.
    - **VAT on behalf of customer** – Set this option to **Yes** if the company operates as an agent that pays import VAT on behalf of another taxable person.

:::image type="content" source="../media/uae_vat_02.jpg" alt-text="Screenshot of the Value added tax FastTab on the Legal entities page.":::

To prepare your legal entity in Finance for VAT accounting and reporting, use the [Sales tax](../../general-ledger/indirect-taxes-overview.md) functionality. For more detailed information, see the following articles:

- [Setting up sales tax authorities](../../general-ledger/tasks/set-up-sales-tax-authorities.md)
- [Set up a sales tax settlement period](../../general-ledger/tasks/set-up-sales-tax-settlement-periods.md)
- [Ledger posting groups](../../general-ledger/tasks/set-up-ledger-posting-groups-sales-tax.md)
- [Sales tax exempt codes](/dynamicsax-2012//sales-tax-exempt-codes-form)
- [Sales tax reporting codes](../../general-ledger/tasks/set-up-sales-tax-reporting-codes.md)
- [Setting up sales tax codes](../../general-ledger/tasks/set-up-sales-tax-codes.md)
- [Setting up sales tax groups and item sales tax groups](../../general-ledger/tasks/set-up-sales-tax-groups-item-sales-tax-groups.md)
- [Set up conditional sales taxes](/dynamicsax-2012/appuser-itpro/set-up-conditional-sales-taxes) (used for cash accounting)
- [Set up tax registration IDs](../europe/emea-registration-ids.md)
- [Set up reverse charge mechanism](../global/emea-reverse-charge.md)

## Configure the tax authority

Set up the FTA as a sales tax authority. When you associate the vendor account with the tax authority, the system automatically creates payments to vendor payables during the settlement process.

Go to **Tax** \> **Sales tax** \> **Sales tax authorities**, and enter the address information for your FTA office. Be sure to select **UAE report layout** in the **Report layout** field.

:::image type="content" source="../media/uae_vat_03.jpg" alt-text="Screenshot of the Sales tax authorities page.":::

When you're done, associate sales tax settlement periods with the tax authority that you configured and with sales tax codes.

## Configure sales tax codes and sales tax reporting codes

The electronic VAT declaration report is based on the configuration of a specific UAE report layout for sales tax. Select this layout as the default layout in the setup of the tax authority.

Set up sales tax codes by following the appropriate procedure for the profile of your company's business in the [Sales Tax section](../../general-ledger/indirect-taxes-overview.md) of the Help documentation.

To run the UAE report layout that includes the electronic VAT declaration, you must first set up the appropriate number of reporting codes that are associated with the amount that's reporting in each VAT declaration.

Go to **Tax** \> **Indirect tax** \> **Sales tax** \> **Sales tax reporting codes**, and create or update sales tax reporting codes according to the information in the following table.

| Sales tax code | VAT reporting code | Report setup                    | Description                                                                             | VAT rate |
|----------------|--------------------|---------------------------------|-----------------------------------------------------------------------------------------|----------|
| SRSAD          | 10                 | Sale \> Taxable sales           | Standard rated supplies in Abu Dhabi                                                    | 5        |
|        -        | 11                 | Sale \> Tax Payable             | Standard rated supplies in Abu Dhabi                                                    | 5        |
| SRSAD-A        | 15                 | Sale \> Tax Payable             | Standard rated supplies in Abu Dhabi – Adjustment                                       | 5        |
| SRSD           | 20                 | Sale \> Taxable sales           | Standard rated supplies in Dubai                                                        | 5        |
|     -           | 21                 | Sale \> Tax Payable             | Standard rated supplies in Dubai                                                        | 5        |
| SRSD-A         | 25                 | Sale \> Tax Payable             | Standard rated supplies in Dubai – Adjustment                                           | 5        |
| SRSS           | 30                 | Sale \> Taxable sales           | Standard rated supplies in Sharjah                                                      | 5        |
|      -          | 31                 | Sale \> Tax Payable             | Standard rated supplies in Sharjah                                                      | 5        |
| SRSS-A         | 35                 | Sale \> Tax Payable             | Standard rated supplies in Sharjah – Adjustment                                         | 5        |
| SRSA           | 40                 | Sale \> Taxable sales           | Standard rated supplies in Ajman                                                        | 5        |
|    -            | 41                 | Sale \> Tax Payable             | Standard rated supplies in Ajman                                                        | 5        |
| SRSA-A         | 45                 | Sale \> Tax Payable             | Standard rated supplies in Ajman – Adjustment                                           | 5        |
| SRSRQ          | 50                 | Sale \> Taxable sales           | Standard rated supplies in Umm Al Quwain                                                | 5        |
|      -          | 51                 | Sale \> Tax payable             | Standard rated supplies in Umm Al Quwain                                                | 5        |
| SRSRQ-A        | 55                 | Sale \> Tax payable             | Standard rated supplies in Umm Al Quwain – Adjustment                                   |    -      |
| SRSRK          | 60                 | Sale \> Taxable sales           | Standard rated supplies in Ras Al Khaimah                                               | 5        |
|      -          | 61                 | Sale \> Tax payable             | Standard rated supplies in Ras Al Khaimah                                               | 5        |
| SRSRK-A        | 65                 | Sale \> Tax payable             | Standard rated supplies in Ras Al Khaimah – Adjustment                                  | 5        |
| SRSF           | 70                 | Sale \> Taxable sales           | Standard rated supplies in Fujairah                                                     | 5        |
|     -           | 71                 | Sale \> Tax Payable             | Standard rated supplies in Fujairah                                                     | 5        |
| SRSF-A         | 75                 | Sale \> Tax payable             | Standard rated supplies in Fujairah – Adjustment                                        | 5        |
| TRPTS          | 80                 | Sale \> Taxable sales           | Tax Refunds provided to Tourists                                                        | 5        |
|       -         | 81                 | Sale \> Tax Payable             | Tax Refunds provided to Tourists                                                        | 5        |
| TRPTS-A        | 85                 | Sale \> Tax payable             | Tax Refunds provided to Tourists – Adjustment                                           | 5        |
| SSRCP-R        | 90                 | Purchases \> Taxable Purchases  | Supplies subject to the reverse charge provisions-Sales                                 | 5        |
|      -          | 91                 | Purchases \> Taxable Receivable | Supplies subject to the reverse charge provisions-Sales                                 | 5        |
| SSRCP-R-A      | 95                 | Purchases \> Taxable Receivable | Supplies subject to the reverse charge provisions-Sales – Adjustment                    | 5        |
| ZRS            | 100                | Sale \> Taxable sales           | Zero rated supplies                                                                     | 0        |
| SOGSRC         | 110                | Sale \> Taxable sales           | Supplies of goods and services to registered customers in other GCC implementing states | 5        |
| ES             | 120                | Sale \> Taxable sales           | Exempt supplies                                                                         | 0        |
| GITUAE         | 170                | Purchases \> Taxable Purchases  | Goods imported into the UAE                                                             | 5        |
|      -          | 171                | Purchases \> Sales tax payable  | Goods imported into the UAE                                                             | 5        |
| GITUAE-R       | 130                | Sale \> Taxable sales           | Goods imported into the UAE reverse charge                                              | -5       |
|      -          | 131                | Sale \> Tax Payable             | Goods imported into the UAE reverse charge                                              | -5       |
| SSRCP-R        | 90                 | Sale \> Taxable sales           | Supplies subject to the reverse charge provisions                                       | -5       |
|      -          | 91                 | Sale \> Tax Payable             | Supplies subject to the reverse charge provisions                                       | -5       |
| SSRCP          | 170                | Sale \> Taxable sales           | Supplies subject to the reverse charge provisions                                       | 5        |
|    -            | 171                | Sale \> Tax Payable             | Supplies subject to the reverse charge provisions                                       | 5        |
| SRE-A          | 160                | Purchases \> Taxable Receivable | Standard rated expenses – Adjustment                                                    | 5        |
| SSRCP          | 170                | Sale \> Taxable sales           | Supplies subject to the reverse charge provisions                                       |  -        |
|     -           | 171                | Sale \> Tax Payable             | Supplies subject to the reverse charge provisions                                       | -5       |
| SSRCP-A        | 175                | Sale \> Tax Payable             | Supplies subject to the reverse charge provisions – Adjustment                          |     -     |
| GTTKOB         | 180                | Sale \> Taxable sales           | Goods transferred to the Kingdom of Bahrain                                             |     -     |
|      -          | 181                | Sale \> Tax Payable             | Goods transferred to the Kingdom of Bahrain                                             | 5        |
| GTTKOB-A       | 185                | Sale \> Tax Payable             | Goods transferred to the Kingdom of Bahrain – Adjustment                                |   -       |
| GTTSOK         | 190                | Sale \> Taxable sales           | Goods transferred to the State of Kuwait                                                |   -       |
|     -           | 191                | Sale \> Tax Payable             | Goods transferred to the State of Kuwait                                                | 5        |
| GTTSOK-A       | 195                | Sale \> Tax Payable             | Goods transferred to the State of Kuwait – Adjustment                                   |    -      |
| GTTSOO         | 200                | Sale \> Taxable sales           | Goods transferred to the Sultanate of Oman                                              |   -       |
|      -          | 201                | Sale \> Tax Payable             | Goods transferred to the Sultanate of Oman                                              | 5        |
| GTTSOO-A       | 205                | Sale \> Tax Payable             | Goods transferred to the Sultanate of Oman – Adjustment                                 |   -       |
| GTTSOQ         | 210                | Sale \> Taxable sales           | Goods transferred to the State of Qatar                                                 | 5        |
|     -           | 211                | Sale \> Tax Payable             | Goods transferred to the State of Qatar                                                 | 5        |
| GTTSOQ-A       | 215                | Sale \> Tax Payable             | Goods transferred to the State of Qatar – Adjustment                                    | 5        |
| GTTKOSA        | 220                | Sale \> Taxable sales           | Goods transferred to the Kingdom of Saudi Arabia                                        |   -       |
|      -          | 221                | Sale \> Tax Payable             | Goods transferred to the Kingdom of Saudi Arabia                                        |     -     |
| GTTKOSA-A      | 225                | Sale \> Tax Payable             | Goods transferred to the Kingdom of Saudi Arabia – Adjustment                           | 5        |
| RVPKOB         | 230                | Purchases \> Taxable Purchases  | Recoverable VAT paid in the Kingdom of Bahrain                                          |    -      |
|        -        | 231                | Purchases \> Taxable Receivable | Recoverable VAT paid in the Kingdom of Bahrain                                          |    -      |
| RVPKOB-A       | 235                | Purchases \> Taxable Receivable | Recoverable VAT paid in the Kingdom of Bahrain – Adjustment                             | 5        |
| RVPSOK         | 240                | Purchases \> Taxable Purchases  | Recoverable VAT paid in the State of Kuwait                                             |    -      |
|       -         | 241                | Purchases \> Taxable Receivable | Recoverable VAT paid in the State of Kuwait                                             |    -      |
| RVPSOK-A       | 245                | Purchases \> Taxable Receivable | Recoverable VAT paid in the State of Kuwait – Adjustment                                | 5        |
| RVPSOO         | 250                | Purchases \> Taxable Purchases  | Recoverable VAT paid in the Sultanate of Oman                                           |     -     |
|      -          | 251                | Purchases \> Taxable Receivable | Recoverable VAT paid in the Sultanate of Oman                                           |    -      |
| RVPSOO-A       | 255                | Purchases \> Taxable Receivable | Recoverable VAT paid in the Sultanate of Oman – Adjustment                              | 5        |
| RVPSOQ         | 260                | Purchases \> Taxable Purchases  | Recoverable VAT paid in the State of Qatar                                              |    -      |
|     -          | 261                | Purchases \> Taxable Receivable | Recoverable VAT paid in the State of Qatar                                              |    -      |
| RVPSOQ-A       | 265                | Purchases \> Taxable Receivable | Recoverable VAT paid in the State of Qatar – Adjustment                                 | 5        |
| RVPKOSA        | 270                | Purchases \> Taxable Purchases  | Recoverable VAT paid in the Kingdom of Saudi Arabia                                     |    -      |
|      -          | 271                | Purchases \> Taxable Receivable | Recoverable VAT paid in the Kingdom of Saudi Arabia                                     |    -      |
| RVPKOSA-A      | 275                | Purchases \> Taxable Purchases  | Recoverable VAT paid in the Kingdom of Saudi Arabia –  Adjustment                     | 5        |

Use the information in the "Report setup" column of the preceding table to configure sales tax codes and associate them with sales tax reporting codes on the **Report setup** FastTab of each sales tax code that is relevant to your company's business.

:::image type="content" source="../media/uae_vat_05.jpg" alt-text="Screenshot of the Report setup FastTab.":::

## Set up the VAT declaration for UAE

The implementation of VAT reporting for the UAE is based on Electronic reporting (ER) configurations. For more information about the capabilities and concepts of configurable reporting, see [Electronic reporting](../../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md).

To use the VAT declaration in a legal entity that has its primary address in UAE, import the latest version of the following ER configurations:

- VAT declaration model
- VAT declaration model mapping
- VAT declaration Excel (AE)

For more information, see [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

After you upload all the configurations, the configuration tree appears in **Electronic reporting** > **Reporting configurations**.

:::image type="content" source="../media/uae-vat-er.png" alt-text="Screenshot of the configuration tree.":::

> [!IMPORTANT]
> After you import all the ER configurations from the previous table, set the **Default for model mapping** option to **Yes** for the **VAT declaration model mapping** configuration.

## Generate a VAT declaration in Excel

To generate the VAT declaration report for UAE in Excel, use the standard **Report sales tax for settlement reporting period** procedure (**Tax** \> **Declarations** \> **Sales tax** \> **Report sales tax for settlement reporting period**), and print the VAT declaration report.

To generate the VAT declaration after a VAT settlement is completed, go to **Tax** \> **Sales tax inquiries** \> **Sales tax payments**, and select the required sales tax payment. Then, on the Action Pane, select **Export VAT file**. For more information, see [Create a sales tax payment](../../general-ledger/tasks/create-sales-tax-payment.md).

:::image type="content" source="../media/uae_vat_12.jpg" alt-text="Screenshot of the Sales tax parameters line item.":::

In the **Export VAT file** dialog box, specify the required information.

:::image type="content" source="../media/uae_vat_13.jpg" alt-text="Screenshot of the Export VAT file dialog box.":::

You're prompted to save the downloaded Excel file for the VAT declaration to your local computer. Save the file, and verify the content of the reported data.

According to the requirements of the FTA accounting systems, you can't edit an electronic reporting file after it's generated from the system. You must make any corrections in the system. After you finish making corrections, generate a new reporting file.

After the reporting file is validated, upload it to the FTA e-Tax portal by using procedures that are specific to your company registration with FTA.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]