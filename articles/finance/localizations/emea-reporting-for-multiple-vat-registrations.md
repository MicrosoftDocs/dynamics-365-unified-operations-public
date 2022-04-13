---
# required metadata

title: Reporting for multiple VAT registrations
description: This topic provides information about reporting for multiple value-added tax (VAT) registrations.
author: anasyash
ms.date: 02/15/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 261354
ms.search.region: 
# ms.search.industry: 
ms.author: anasyash
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Reporting for multiple VAT registrations 

[!include [banner](../includes/banner.md)]

This topic explains how to do reporting for multiple value-added tax (VAT) registrations from a single legal entity. The functionality is available for the following countries or regions: 

- Austria
- Belgium
- Denmark
- Finland
- France
- Germany
- Netherlands
- United Kingdom
- Norway
- Spain
- Sweden
- Switzerland
  
The scope of reporting is limited to generation of the following reports:

- VAT declaration
- EU sales list
- Intrastat

For an overview of the functionality, view the following TechTalk session from September 29, 2021: [VAT Reporting for Multiple Tax Registrations in Single Legal Entity](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/vat-reporting-for-multiple-tax-registrations-in-single-legal-entity-september-29-2021)

## Prerequisites

Configure the Tax Calculation service. For more information, see [Tax Calculation](global-tax-calcuation-service-overview.md).

### Enable features in the feature management

1. Go to **Workspaces** > **Feature management**.
2. In the feature list, select and enable the following features:

    - Support multiple VAT registration numbers
    - EU sales list transfer based on tax transactions only

> [!NOTE]
> If you transfer between warehouses in different countries that have a tax registration, you must also enable the **Tax in transfer order** feature and configure the Tax Calculation service for tax in transfer orders. For more information, see [Tax feature support for transfer orders](tasks/tax-feature-support-for-transfer-order.md).

### Set up the Multiple VAT registrations feature

For information about how to set up the **Multiple VAT registrations** feature, see [Multiple VAT registration numbers](emea-multiple-vat-registration-numbers.md).

## Enable features

In the **Feature management** workspace, enable the following features:

- Intrastat reporting for multiple VAT registrations
- EU Sales list reporting for multiple VAT registrations
- Sales tax declaration for multiple VAT registrations

## Activate feature for specific legal entity

1. Go to **Tax** > **Setup** > **Tax configuration** > **Tax calculation parameters**.
2. On the **General** tab, set **Enable tax service** to **Yes**.
3. On the **Multiple VAT registrations** tab, set **VAT declaration**, **EU Sales List**, and **Intrastat** to **Yes** to activate VAT reporting, EU sales list reporting, or Intrastat reporting respectively, for the selected legal entity.

> [!NOTE]
> Only country-specific functionality that is applicable to the country of the selected legal entity is available. Formats for the VAT declaration, EU sales list, and Intrastat are available for countries of other VAT registrations. Other country-specific functionality that is applicable to the countries of other VAT registrations isn't available in this legal entity.

## Set up intra-community reporting for multiple VAT registrations

### Set up country/region properties

1. Go to **Tax** > **Set up** > **Foreign trade** > **Foreign trade parameters**.
2. On the **Country/region properties** tab, set up the following country types: **EU**, **EFTA**, or **Third country/region**.

    The following information applies to documents about movements of goods between European Union (EU) countries, except movements within the same country (for example from Belgium to Belgium):

      - By default, the list code is **EU trade**, and it's transferred to the EU sales list.
      - Documents are transferred to Intrastat.

### Set up Intrastat

#### Set up Intrastat parameters

All tax registrations have the same settings for Intrastat parameters.

1.  Go to **Tax** > **Set up** > **Foreign trade** > **Foreign trade parameters**.
2.  On the **Intrastat** tab, set up the parameters on the following FastTabs:

    - Default transaction codes
    - Minimum limit
    - Transfer
    - Check setup
    - Rounding rules
    - Commodity code hierarchy

    ![Foreign trade parameters1.](media/Multipleid-image2.png)

For more information about how to configure Intrastat, see [Intrastat overview](emea-intrastat.md).

#### Set up Intrastat reporting formats

1. Go to **Tax** > **Set up** > **Foreign trade** > **Foreign trade parameters**.
2. On the **Intrastat** tab, on the **Electronic reporting for countries/regions** FastTab, select the Intrastat reporting format for each country of your tax registration.
3. In the **File format mapping** field, select the Electronic reporting (ER) format for Intrastat file export, for example, select **Intrastat (NL)** for Netherlands.
4. In the **Report format mapping** field, select the ER format for printable report layout, for example, select **Intrastat report**.

    ![Foreign trade parameters2.](media/Multipleid-image3.png)

    > [!NOTE]
    > You can select an ER format if the **ISO Country/region codes** field on the **ISO Country/region codes** FastTab is blank in this format.

    The following table shows the earliest ER format versions that you can select the format for.

    | Release | Country | ER format |
    |---------|---------|-----------|
    | 10.0.19 | All | Intrastat model.version.16 |
    | 10.0.19 | Netherlands | Intrastat (NL).version.1.3 |
    | 10.0.20 | France | Intrastat INTRACOM (FR).version.13.5<br>Intrastat SAISUNIC (FR).version.1.3 |
    | 10.0.20 | United Kingdom (Northern Ireland) | Intrastat (UK).version.1.2 |
    | 10.0.21 | Austria | Intrastat (AT).version.16.3 |
    | 10.0.21 | Germany | INSTAT XML (DE).version.22.9.9 |
    | 10.0.21 | Spain | Intrastat (ES).version.16.7 |
    | 10.0.21 | Sweden | Intrastat (SE).version.16.4 |
    | 10.0.23 | Finland | Intrastat (FI).version.2.3 |
    | 10.0.23 | Denmark | Intrastat (DK).version.25.4 |
    | 10.0.23 | Poland | Intrastat (PL).version.25.5 |
    | 10.0.25 | Belgium | Intrastat (BE).version.2.9 |

For more information, see [Download ER configurations from the Global repository of Configuration service](../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

#### Set up transaction codes

A system of two-digit transaction codes is used to differentiate types of trade at the European level. For more information, see [European business statistics compilers' manual for international trade in goods statistics — 2021 edition - Products Manuals and Guidelines - Eurostat (europa.eu)](https://ec.europa.eu/eurostat/web/products-manuals-and-guidelines/-/ks-gq-21-004).

As of January 1, 2022, a unified system of two-digit transaction codes is used in EU countries.

1. Go to **Tax** > **Set up** > **Foreign trade** > **Transaction codes**.
2. Create the required transaction codes.

    ![transaction codes.](media/Multipleid-image4.png)

For each transaction code that you create, you must set up the rules that are used to calculate invoice amounts and statistical amounts for transfer orders, and for sales orders and purchase orders.

- For transfer orders, set up one of the following rules:

    - **Empty:** The amount will be 0 (zero).
    - **Financial cost amount:** The amount will equal the financial cost.
    - **Total cost:** The amount will equal the total cost of the transaction.
    - **Manual:** The amount will equal the amount that is specified in the **Invoiced amount** and **Statistical value** fields on the transfer order line. These values are taken from the **Amount** field on the transfer order line.

    ![transfer order.](media/Multipleid-image5.png)

-   For sales orders and purchase orders, set up one of the following rules:

    - **Empty:** The amount will be 0 (zero).
    - **Invoice amount:** The amount will equal the amount that is invoiced for the commodity.
    - **Base amount:** The amount will equal the invoice amount that would be invoiced before any discount is applied.

#### Set up Intrastat compression rules

All tax registrations have the same setup for compression rules.

1. Go to **Tax** > **Setup** > **Foreign trade** > **Compression of Intrastat**.
2. Select the values to use in the **Compression** function. Select all the values that are reported in any of the countries where you have tax registrations. 

For example, in 2022, the following values should be reported in some countries.

**Mandatory elements**

**Direction** (flow), **Commodity code**, **Country/region** (partner member state), **Transaction code**, **Tax exempt number** (partner's VAT number) on dispatches, and **Country/region of origin** are reported in all countries from the following table.

**Optional elements**

| Value | Austria | Belgium | Denmark | Finland | France | Germany | Netherlands | Poland | Spain | Sweden | United Kingdom (Northern Ireland) |
|-------|---------|---------|---------|---------|--------|---------|-------------|-----------------------------------|--------|-------|--------|
| Delivery terms | No | **Yes** | No | No | No | No | No | **Yes** | **Yes** | No | **Yes**|
| Mode of transport | **Yes** | **Yes** | No | **Yes** | **Yes** | **Yes** | No | **Yes** | **Yes** | No | No |
| State of origin (Region of origin) | No | **Yes** | No | No | No | **Yes** | No |  No | No | No | No |
| County of origin (Region of origin) | No | No | No | No | **Yes** | No | No |  No | **Yes** | No | No |
| Statistics procedure | **Yes** | No | No | No | **Yes** | No | **Yes** |  No | **Yes** | No | No |

**Additional elements for country purposes**

| Value | Austria | Belgium | Denmark | Finland | France | Germany | Netherlands | Poland | Spain | Sweden | United Kingdom (Northern Ireland) |
|-------|---------|---------|---------|---------|--------|---------|-------------|-----------------------------------|--------|-------|--------|
| Transport document (Invoice, Identification of packing slip or product receipt) | No | No | No | No | No | No | **Yes** | No | No | No | No|
| Port ((Air)port of (un)loading) | No | No | No | No | No | No | No | No | **Yes** | No | No | 

> [!NOTE]
> Select all values that must be reported on the **Compression of Intrastat** page.

### Set up the EU sales list

#### Set up sales tax codes

1. Go to **Tax** > **Sales tax** > **Sales tax codes**.
2. Create unique sales tax codes for each of your tax registrations.
3. On the **Report setup** FastTab, in the **EU sales list** section, set the **Excluded** option to **Yes** if tax transactions that have a selected sales tax code should **not** be transferred to the EU sales list.
4. In the **Country/region type** section, in the **Country/region type** field, define the tax transaction type for VAT reporting: **EU**, **Domestic**, or **Third country**.

    This setting is mandatory in some countries, such as the United Kingdom.

    ![sales tax code.](media/Multipleid-image6.png)

#### Set up item sales tax groups

1. Go to **Tax** > **Sales tax** > **Item sales tax groups**.
2. In the **Reporting type** field, select the reporting type for EU sales list reporting: **Item**, **Service**, or **Investment** (for Belgium).

#### Set up EU sales list parameters

All tax registrations have the same settings for EU sales list parameters.

1. Go to **Tax** > **Setup** > **Foreign trade** > **Foreign trade parameters**.
2. On the **EU sales list** tab, set up the parameters on the **Transfer** and **Rounding rules** FastTabs.

> [!NOTE]
> If one of your tax registrations is in Poland or Hungary (countries that report purchases in addition to sales), set the **Transfer purchases** option to **Yes**.

#### Set up EU sales list reporting formats

1. Go to **Tax** > **Set up** > **Foreign trade** > **Foreign trade parameters**.
2. On the **EU sales list** tab, on the **Electronic reporting for countries/regions** FastTab, select EU sales list reporting formats for each country of your tax registration.
3. In the **File format mapping** field, select the ER format for EU sales list report electronic format. For example, for Netherlands, select **EU Sales list (NL)**.
4. In the **Report format mapping** field, select the ER format for printable report layout. For example, select either **EU sales list by rows report**, or **EU sales list by columns report**.

    ![foreign trade parameters 3.](media/Multipleid-image7.png)

    > [!NOTE]
    > You can select an ER format if the **ISO Country/region codes** field on the **ISO Country/region codes** FastTab is blank in this format.

    The following table shows the earliest ER format versions that you can select the format for.

    | Release | Country | ER format |
    |---------|---------|-----------|
    | 10.0.19 | All | EU Sales list model.version.9 |
    | 10.0.19 | Netherlands | EU Sales list (NL).version.1.10 |
    | 10.0.20 | France | EU Sales list (FR).version.1.2 |
    | 10.0.20 | United Kingdom (Northern Ireland) | EU Sales list XML (UK).version.9.6<br>EU Sales list TXT (UK).version.9.7 |
    | 10.0.21 | Austria | EU Sales list (AT).version.9.5 |
    | 10.0.21 | Germany | EU Sales list (DE).version.9.5 |
    | 10.0.21 | Spain | EU Sales list (ES).version.9.2 |
    | 10.0.21 | Sweden | EU Sales list (SE).version.13.7 |
    | 10.0.23 | Finland | EU Sales list (FI).version.2.5 |
    | 10.0.23 | Denmark | EU Sales list (DK).version.13.4 |
    | 10.0.24 | Poland | EU Sales list (PL).version.14.7 |
    | 10.0.25 | Belgium | EU Sales list (BE).version.2.3 |

## Generate intra-community reporting for multiple VAT registrations

### Transfer and report Intrastat

1. Go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**.
2. Select **Transfer**.
3. In the **Tax registration number** dialog box, select the tax registration number to transfer transactions for, and then select **OK**.

    ![transfer intrastat.](media/Multipleid-image8.png)

4. In the **Intrastat (Transfer)** dialog box, select the documents to transfer: **Free text invoice**, **Customer invoice**, **Customer packing slips**, **Vendor invoice**, **Vendor product receipts**, **Project invoice**, or **Transfer order**. Then and select **OK**.

    ![Intrastat  Transfer  dialog box.](media/Multipleid-image9.png)

5. Transactions for the selected tax registration and documents are transferred. Review the transactions, and make any adjustments that are required.

    > [!NOTE]
    > 
    > In the 10.0.19, 10.0.20 release, Intrastat **Transfer** function has country-specific logic that isn't yet covered in the **Intrastat transfer for Multiple Tax ID** feature for the following countries: Czech Republic, Finland, Germany, Hungary, Italy, Latvia, Lithuania, Poland, and Spain.

6. Select **Output** > **Report**.
7. In the **Tax registration number** dialog box, select the tax registration number to generate the Intrastat report for, and then select **OK**.

    ![Intrastat  Reporting  dialog box.](media/Multipleid-image10.png)

8. In the **Intrastat Report** dialog box, in the **From date** and **To date** fields, define the period to generate the Intrastat report for.
9. Set the **Generate file** option to **Yes** to generate an electronic reporting file. Then, in the **File name** field, enter the name of the output electronic file if applicable.
10. Set the **Generate report** option to **Yes** to generate an Excel report. Then, in the **Report file name** field, enter the name of the output Excel file if applicable.

    ![Intrastat report dialog box.](media/Multipleid-image11.png)

11. The dialog box also contains country-specific fields that are required in the country-specific Intrastat report. Set these fields as required.
12. Select **OK** to generate the report.

### Transfer and report the EU sales list

1. Go to **Tax** > **Declarations** > **Foreign trade** > **EU sales list**.
2. Select **Transfer**.
3. In the **Tax registration number** dialog, select the tax registration number to transfer transactions for, and then select **OK**.

    ![ESL transfer dialog box.](media/Multipleid-image12.png)

4. In the **Transfer transactions for EU sales list** dialog box, select the documents and reporting types to transfer.

    ![ESL transfer dialog box2.](media/Multipleid-image13.png)

5. Select **Select** to adjust the default filter for transactions that should be transferred, and then select **Transfer**.
6. Transactions for the selected tax registration, documents, and reporting types are transferred. Review the transactions, and make any adjustments that are required.
7. Select **Reporting**.
8. In the **Tax registration number** dialog box, select the tax registration number to generate the EU sales list report for, and then select **OK**.
9. In the **EU reporting** dialog box, in the **From date** field, specify the first date to generate the EU sales list report for.
10. Set the **Generate file** option to **Yes** to generate an electronic reporting file. Then, in the **File name** field, enter the name of the output electronic file.
11. Set the **Generate report** option to **Yes** to generate an Excel report. Then, in the **Report file name** field, enter the name of the output Excel file.

    ![ESL report dialog box.](media/Multipleid-image14.png)

12. The dialog box also contains country-specific fields that are required in the country-specific EU sales list report. Set these fields as required.
13. Select **OK** to generate the report.

## Set up VAT reporting for multiple VAT registrations

1. Go to **Tax &gt; Set up &gt; Parameters &gt; General ledger parameters**.
2. On the **Sales tax** tab, on the **Electronic reporting for countries/regions** FastTab, select the VAT reporting formats for each country of your tax registration.

    ![GL parameters.](media/Multipleid-image15.png)

    > [!NOTE]
    > You can select an ER format if the **ISO Country/region codes** field on the **ISO Country/region codes** FastTab is blank in this format.

    The following table shows the earliest ER format versions that you can select the format for. For more information about how to run VAT declaration for specific country, review the related topic.
    
    | Release | Country | ER format | Link to topic |
    |---------|---------|-----------|---------------|
    | 10.0.19 | All | Tax declaration model.version.85<br>Tax declaration model mapping.version.85.138 | |
    | 10.0.19 | Netherlands | VAT Declaration XML (NL).version.85.14<br>VAT Declaration Excel (NL).version.85.14.17| [VAT declaration (Netherlands)](emea-nl-vat-declaration-netherlands.md) |
    | 10.0.20 | France | VAT Declaration Excel (FR).version.85.15 | [VAT declaration (France)](emea-fra-vat-declaration-preview-france.md) |
    | 10.0.21 | United Kingdom | MTD VAT importing model mapping (UK).version.31.36<br>Tax declaration model mapping.version.95.158<br>VAT Declaration Excel (UK).version.32.30.16<br>VAT Declaration JSON (UK).version.32.31 | [Prepare for integration with MRD for VAT](emea-gbr-mtd-vat-integration.md) |
    | 10.0.21 | Sweden | VAT Declaration XML (SE).version.95.11<br>VAT Declaration Excel (SE).version.95.11.13 | [VAT declaration (Sweden)](emea-swe-vat-declaration-sweden.md) |
    | 10.0.21 | Switzerland | Tax declaration model.version.96<br>Tax declaration model mapping.version.96.164<br>VAT Declaration XML (CH).version.96.16<br>VAT Declaration Excel (CH).version.96.16.9 | [VAT declaration (Switzerland)](emea-che-vat-declaration-switzerland.md) |
    | 10.0.22 | Austria | VAT Declaration XML (AT).version.101.23<br>VAT Declaration Excel (AT).version.101.23.17 | [VAT declaration (Austria)](emea-aut-vat-declaration-austria.md) |
    | 10.0.23 | Germany | VAT Declaration XML (DE).version.101.16<br>VAT Declaration Excel (DE).version.101.16.12 | [VAT declaration (Germany)](emea-deu-vat-declaration-germany.md) |
    | 10.0.21 | Norway | Tax declaration model.version.112<br>Tax declaration model mapping.version.112.192<br>VAT Declaration XML (NO).version.112.54<br>VAT Declaration Excel (NO).version.112.54.39 | [VAT return with direct submission to Altinn](emea-nor-vat-return.md) |
    | 10.0.23 | Spain | VAT Declaration TXT(ES).version.101.28<br>VAT Declaration Excel (ES).version.101.28.17 | [VAT declaration (Spain)](emea-esp-vat-declaration-spain.md) |
    | 10.0.25 | Denmark | VAT Declaration Excel (DK).version.101.8 | [VAT declaration (Denmark)](emea-dnk-vat-declaration-denmark.md) |

## Generate a VAT declaration for multiple VAT registrations

1. Go to **Tax** > **Declarations** > **Sales tax** > **Report sales tax for settlement period**.
2. In the **Report sales tax for settlement period** dialog box, in the **Settlement period** field, select a settlement period.
3. In the **From date** field, specify the first date to generate the VAT declaration for.
4. In the **Sales tax payment version** field, select one of the following values:

    - **Original:** Generate a report for sales tax transactions of the original sales tax payment or before the sales tax payment is generated.
    - **Corrections:** Generate a report for sales tax transactions of all subsequent sales tax payments for the period.
    - **Total list:** Generate a report for all sales tax transactions for the period, including the original and all corrections.

    ![Report sales tax.](media/Multipleid-image16.png)

5. Select **OK** to generate the report.

<!--## Known limitations-->

[!INCLUDE[footer-include](../../includes/footer-banner.md)]

