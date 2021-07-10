---
title: 
description: 
ms.date: 07.10.2021
ms.topic: article
ms.service: dynamics365-financials
author: and
ms.author: Andosip
manager: anasyash
---

# Italian Intrastat

## Overview

The **Intrastat** page is used to generate and report information about trade among European Union (EU) countries. Italian Intrastat contains information about the trade of goods and services for monthly or quarterly reporting.

The following table shows the fields that appear on the Italian Intrastat declaration.

| **Value**                                                                                    | **Intrastat journal field**                                                                                           | **Goods**      | **Services**  |                |               |     |     |
|----------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------|----------------|---------------|----------------|---------------|-----|-----|
|                                                                                              |                                                                                                                       | **Dispatches** | **Arrivals**  | **Dispatches** | **Arrivals**  |     |     |
|                                                                                              |                                                                                                                       | **Monthly**    | **Quarterly** | **Monthly**    | **Quarterly** |     |     |
| Your company's value-added tax (VAT) registration number                                     |                                                                                                                       | X              | X             | X              | X             | X   | X   |
| The customer's or vendors tax-exempt number                                                  | **Tax exempt number** field in the **General** section                                                                | X              | X             | X              | X             | X   | X   |
| The invoice amount in the accounting currency                                                | **Invoice amount** field in the **Invoice value** section                                                             | X              | X             | X              | X             | X   | X   |
| The invoice amount in the transaction currency                                               | **Invoice amount in transaction currency** field in the **Invoice value** section                                     |                |               | X              | X             |     | X   |
| The invoice number                                                                           | **Invoice** field in the **General** section                                                                          |                |               |                |               | X   | X   |
| The invoice date                                                                             |                                                                                                                       |                |               |                |               | X   | X   |
| The transaction code                                                                         | **Transaction code** field in the **Codes** section                                                                   | X              | X             | X              | X             |     |     |
| The commodity code                                                                           | **Commodity** field in the **Codes** section                                                                          | X              | X             | X              | X             | X   | X   |
| The weight                                                                                   | **Weight** field in the **Data** section                                                                              | X              |               | X              |               |     |     |
| Additional units                                                                             | **Quantity of additional units** field in the **Unit** section                                                        | X              |               | X              |               |     |     |
| The statistical value in the accounting currency                                             | **Statistical value** field in the **Statistical value** section                                                      | X              |               | X              |               |     |     |
| The delivery terms                                                                           | **Delivery terms** field in the **Codes** section                                                                     | X              |               | X              |               |     |     |
| The delivery schedule                                                                        | **Delivery schedule** field in the **Codes** section                                                                  |                |               |                |               | X   | X   |
| The transport mode                                                                           | **Transport** field in the **Codes** section                                                                          | X              |               | X              |               |     |     |
| The method of payment                                                                        | **Method of payment** field in the **Codes** section                                                                  |                |               |                |               | X   | X   |
| The International Organization for Standardization (ISO) code for the payment country/region | The ISO code for your company's country/region (for dispatches) or the vendor company's country/region (for arrivals) |                |               |                |               | X   | X   |
| The country/region                                                                           | **Country/region field** in the **Dispatches/destination** section                                                    | X              |               |                |               |     |     |
| The county of origin or destination                                                          | **County of origin/destination** field in the **Dispatch/destination** section                                        | X              |               |                |               |     |     |
| The country/region of origin                                                                 | **Country/region of origin** field in the **Country/region of origin** section                                        |                |               | X              |               |     |     |
| The county of origin                                                                         | **County of origin** field in the **Country/region of origin** section                                                |                |               | X              |               |     |     |

You must send two reports to the authority. One report is for intracommunity dispatches, and the other is for intracommunity arrivals. Each report consists of five parts:

- **Cover page**

- **Section 1. Goods** – This section contains information about normal transactions and credit notes that are related to invoices for goods in the same reporting period as the Intrastat declaration period.

- **Section 2. Corrections for goods** – This section contains information about corrections and credit notes that are related to invoices for goods in previous Intrastat reporting periods.

- **Section 3. Services** – This section contains information about normal transactions and credit notes that are related to invoices for services in the same reporting period as the Intrastat declaration period.

- **Section 4. Corrections for services** – This section contains information about corrections and credit notes that are related to invoices for services in previous Intrastat reporting periods.

## Set up Intrastat

### Preliminary setup

The following general information should be set up before you start to work with Intrastat:

-   Commodity codes. For services, you should define six-digit commodity codes.

-   Transaction codes. Note that Italy uses one-digit transaction codes.

-   Transport methods.

-   Statistics procedures.

-   Foreign trade parameters.

-   Warehousing.

-   Released product details.

-   Agent contact information.

For more information, see [Intrastat overview](https://docs.microsoft.com/dynamics365/finance/localizations/emea-intrastat).

### Set up Italian Intrastat

Follow these steps to set up Italian-specific options so that you can work with Intrastat.

1.  In [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/Logon/Index), in the Shared asset library, download the latest version of the following Electronic reporting (ER) configurations for the Intrastat declaration:

    -   Intrastat model

    -   Intrastat report

    -   Intrastat (IT)

For more information, see [Download Electronic reporting configurations from Lifecycle Services](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs).

2.  In Dynamics 365 Finance, go to **Tax** &gt; **Setup** &gt; **Foreign trade parameters**.

3.  On the **Intrastat** tab, on the **General** FastTab, set the following fields:

    - **County of origin/destination** – Select your company's county. This county will be used on dispatches.

    <!-- -->

    - **Transaction code** – Select the transaction code for property transfers. This code will be used for transactions that cause an actual or planned transfer of property against compensation, and also for corrections.

    - **Credit note** – Select the transaction code for the return of goods. This code will be used for the return of goods after the original transaction is recorded under the transaction code.

    - **Sales reporting period** – Select the reporting period for the export declaration: **Month** or **Quarter**. Quarterly declarations are exported in simplified format.

    - **Purchase reporting period** – Select the reporting period for the import declaration: **Month** or **Quarter**. Quarterly declarations are exported in simplified format.

4.  On the **Electronic reporting** FastTab, set the following fields:

    - **File format mapping** – Select **Intrastat (IT)**.

    <!-- -->

    - **Report format mapping** – Select **Intrastat report**.

5.  On the **Commodity code hierarchy** FastTab, in the **Category hierarchy** field, select **Intrastat**.

6.  On the **Statistical value** FastTab, set the **Print and export statistical data** option to **Yes** if necessary. This setting activates transfer of the statistical section. The statistical section consists of data about weights, additional units, statistical values, delivery terms, delivery schedules, transport modes, and regions of origin.

&gt; !Note

&gt;

&gt; For a quarterly declaration, the Intrastat report won't include the statistical section, or information about delivery terms and transport modes. For more information, see the table in the [Overview](#overview) section of this topic.

7.  On the **Country/region properties** tab, list all the countries or regions that your organization does business with. For each country or region, set the following fields:

- **Party country/region** – Select the country/region code.

- **Intrastat code** – Enter the two-digit Intrastat code.

- **Currency** – Specify the national currency of the country or region. If the vendor is based in an EU country that doesn't use the euro, invoice amounts will be reported in both the vendor's currency and euros. For example, if the vendor is based in Denmark, the reported amounts for the import declaration will be in both Danish kroner (DKK) and euros (EUR).

- **Country/region type** – Select the country's or region's type in relation to your organization. For the Intrastat journal, only countries or regions of the **EU** and **Special domestic** type will be transferred.

&gt; !Note

&gt;

&gt; For countries or regions of the **Special domestic** type, the following fields are omitted from the Intrastat report file: **Weight**, **Additional units**, **Statistical value**, **Delivery terms**, **Transport code**, **Country/region of origin/destination**, and **County of origin/destination**. For example, in the **Party country/region** field, select **SMR (San Marino)**, and then, in the **Country/region type** field, select **Special domestic**.

8.  Go to **Accounts payable** &gt; **Setup** &gt; **Terms of delivery**.

9.  In the grid, select the delivery terms.

10. On the **General** FastTab, in the **Intrastat code** field, enter the one-digit code that will be used on the Intrastat report.

11. Assign tax-exempt numbers to customers and vendors by following these steps. These numbers will appear on the Intrastat report.

-   Go to **Tax** &gt; **Setup** &gt; **Sales tax** &gt; **Tax exempt numbers**, and list all tax-exempt numbers for your customers and vendors. For each partner, set the following fields:

    - **Country/region** – Select the partner's country or region.

    - **Tax exempt number** – Enter the partner's tax-exempt number.

    - **Company name** – Enter the partner's name.

<!-- -->

-   Go to **Accounts receivable** &gt; **Customers** &gt; **All customers**, and follow these steps for every customer:

    1.  Select a customer.

    2.  On the **Invoice and delivery** FastTab, in the **Sales tax** section, in the **Tax exempt number** field, select **All**.

    3.  Select the customer's tax-exempt number.

-   Go to **Accounts payable** &gt; **Vendors** &gt; **All vendors**, and follow these steps for every vendor:

    1.  Select a vendor.

    2.  On the **Invoice and delivery** FastTab, in the **Sales tax** section, in the **Tax exempt number** field, select **All**.

    3.  Select the vendor's tax-exempt number.

12. Go to **Tax** &gt; **Setup** &gt; **Foreign trade** &gt; **Compression of Intrastat**, and select the fields that should be compared when Intrastat information is summarized. For Italy, select **Tax exempt number**, **Transaction code**, **Commodity**, **Delivery terms**, **Transport**, **Country/region**, **Country/region of origin**, **County of origin**, **County of origin/destination**, **Currency**, **Month**, **Quarter**, and **Correction year**.

## Italian vendor invoice journal for foreign trade

When you work with the vendor invoice journal, it's crucial that you consider some parameters that affect your Intrastat report. On the **Foreign trade** tab, you can review and set the following Italy-specific fields.

| **Field**                    | **Description**                                                                                 |
|------------------------------|-------------------------------------------------------------------------------------------------|
| Transaction code             | Select the transaction code.                                                                    |
| Transport                    | Select the transport that is used for the transfer.                                             |
| Commodity                    | Select the item commodity code.                                                                 |
| Additional units             | Enter additional units, if additional units should be reported for the selected commodity code. |
| Country/region               | Select the partner's country/region.                                                            |
| County of origin/destination | Select the destination county.                                                                  |

## Intrastat journal

You use the Intrastat journal to manage information about trade among EU countries.

To open the Intrastat journal, go to **Tax** &gt; **Declarations** &gt; **Foreign trade** &gt; **Intrastat**. The following information is shown for each transaction:

| **Field**                              | **Description**                                                                                                                                                                                                                                                                                                                                                                                                         |
|----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Date                                   | The date of the transaction posting.                                                                                                                                                                                                                                                                                                                                                                                    |
| Direction                              | This field is set to **Arrivals** for purchases or **Dispatches** for sales.                                                                                                                                                                                                                                                                                                                                            |
| Item type                              | This field can be set to **Goods** or **Services**.                                                                                                                                                                                                                                                                                                                                                                     |
| Correction                             | When this option is set to **Yes**, the transaction is a correction. In that case, you can report corrections to Intrastat transactions that have already been reported. On the **General** tab, in the **Corrections** section, use the **Month**, **Quarter**, and **Correction year** fields to specify the original transaction period. Use the **Original Intrastat record** field to specify the original record. |
| Item number                            | The code for the released product.                                                                                                                                                                                                                                                                                                                                                                                      |
| Category                               | The ode for the procurement category.                                                                                                                                                                                                                                                                                                                                                                                   |
| Commodity                              | The item commodity code. This value is specified on the **Released product details** page for products, or it can be manually set on the transaction line.                                                                                                                                                                                                                                                              |
| Weight                                 | The weight for the transaction line in kilograms (kg). This value is specified on the **Released product details** page for products, or it can be manually set on the transaction line.                                                                                                                                                                                                                                |
| Invoice amount                         | The amount in the accounting currency                                                                                                                                                                                                                                                                                                                                                                                   |
| Invoice amount in transaction currency | The amount in the national currency of the partner.                                                                                                                                                                                                                                                                                                                                                                     |
| Currency                               | The national currency of the partner.                                                                                                                                                                                                                                                                                                                                                                                   |

&gt; !Note

&gt;

&gt; If you receive a negative correction (credit note) in the same period as the reporting period, you must manually change the Intrastat journal by following these steps.

1.  Go to **Tax** &gt; **Declarations** &gt; **Foreign trade** &gt; **Intrastat**.

2.  Find and delete the transaction that is marked as a correction.

3.  Find the original transaction, and change the value of the **Invoice amount** field as appropriate.

&gt; For example, you have an invoice for 10,000, and you receive a credit note for -2,000. In this case, you must open the Intrastat journal, and find and delete the transaction for -2,000. Then find the original transaction for 10,000, and set the invoice amount to 8,000 (= 10,000 - 2,000).

### Intrastat transfer

On the Action Pane, you can select **Transfer** to automatically transfer the information about intracommunity trade from your sales orders, free text invoices, purchase orders, vendor invoices, vendor product receipts, project invoices, and transfer orders. Only documents that have an EU country as the country or region of destination (for dispatches) or consignment (for arrivals) will be transferred.

Alternatively, you can manually enter transactions by selecting **New** on the Action Pane.

For each transaction, you can set several Italy-specific parameters on the **General** tab.

| **Field** | **Description** |
|-------------------------|-------------------------|
| **General** section |  |
| Item type | This field can be set to **Goods** or **Services**.</br>For a transaction to be considered a service, your invoice line should be set up in one of the following ways:</br><ul></br><li>It has no commodity code.</li></br><li>It has a six-digit commodity code</li></br></ul> |
| **Country/region of origin** section |  |
| County of origin | The county of origin of the product or service. This value is specified on the **Released products** page. |
| **Codes** section |  |
| Mode of delivery | The mode of delivery. To specify the mode of delivery, go to **Sales and marketing** &gt; **Setup** &gt; **Distribution** &gt; **Modes of delivery**. |
| **Corrections** section |  |
| Month | The month of the original transaction. |
| Quarter | The quarter of the original transaction. |
| Correction year | The year of the original transaction. |
| Original Intrastat record | For service corrections, enter the number of the original Intrastat record. |
| **Invoice value** section |  |
| Currency | The national currency of the partner. |
| Invoice amount in transaction currency | The invoice amount in the national currency of the partner. |
| Invoice charges amount in transaction currency | The invoice charges in the national currency of the partner. For more information, see [Intrastat overview prerequisites (Miscellaneous charges)](https://docs.microsoft.com/dynamics365/finance/localizations/emea-intrastat#prerequisites). |
| Invoice value in transaction currency | The invoice value in the national currency of the partner. |


### Generate an Intrastat report

1.  To generate an Intrastat report, go to **Tax** &gt; **Declarations** &gt; **Foreign trade** &gt; **Intrastat**.

2.  On the Action Pane, select **Output** &gt; **Report**.

3.  In the **Intrastat Report** dialog box, set the following fields.

| **Field**                       | **Description**                                                                                                                                 |
|---------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| **Date** section                |                                                                                                                                                 |
| From date                       | Select the start date for the report.                                                                                                           |
| To date                         | Select the end date for the report.                                                                                                             |
| **Export options** section      |                                                                                                                                                 |
| Generate file                   | Set this option to **Yes** to generate a .txt file.                                                                                             |
| File name                       | Enter the name of the .txt file for your Intrastat report.                                                                                      |
| Generate report                 | Set this option to **Yes** to generate an .xlsx file.                                                                                           |
| Report file name                | Enter the name of the .xlsx file for your Intrastat report.                                                                                     |
| Direction                       | Select **Arrivals** for a report about intracommunity arrivals. Select **Dispatches** for a report about intracommunity dispatches.             |
| **File format mapping** section |                                                                                                                                                 |
| Reference number                | Enter the document number. This value will affect the **File number** code on the Intrastat file report. For more information, see File format. |

