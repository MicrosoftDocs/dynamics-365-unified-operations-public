---
title: Polish Intrastat
description: Learn how to set up Intrastat reporting for Poland in Microsoft Dynamics 365 Finance.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 05/05/2026
ms.reviewer: johnmichalak
ms.search.region: Global
---

# Polish Intrastat

[!include[banner](../../includes/banner.md)]

This article explains how to set up Intrastat reporting for Poland in Microsoft Dynamics 365 Finance.

Use the **Intrastat** page to generate and report information about trade among European Union (EU) countries and regions. The Polish Intrastat declaration contains information about the trade of goods for reporting.

The Polish Intrastat declaration includes the following fields. All of the fields are included on arrivals and dispatches except for **RodzajTransportu** (the transport mode) and **KrajPochodzenia** (the country or region of origin), which aren't included on dispatches, and **IdKontrahenta** (the customer's foreign VAT number), which isn't included on arrivals.

| Field name | Description |
|-------------------------|-------------------------|
| Deklaracja Data | The date when the document is created. |
| Miesiac | The reference month of the declaration. |
| Rok | The reference year of the declaration. |
| Numer | The declaration number in the reference period. |
| Wersja | The version number of the declaration. |
| NrWlasny | The declaration identifier. The value is automatically generated. |
| Typ | The report direction.</br><li>For arrivals, "P" is printed.</li><li>For dispatches, "W" is printed.</li> |
| Rodzaj | The type of declaration. The value indicates whether the report is the original declaration or a correction declaration. |
| UC | The unit code that the Intrastat declaration is addressed to. Specify the value in the **Tax exempt number** field in the **Sales tax** section on the **Agent** tab of the **Foreign trade parameters** page. |
| Nazwa | The name of the company. |
| Miejscowosc, UlicaNumer, KodPocztowy | The full address of the legal entity. |
| Nip | The Polish tax identification number (value-added tax [VAT] ID). |
| Regon | The Polish statistical identification number (enterprise number). |
| LacznaWartoscFaktur | The sum of invoice values. |
| LacznaWartoscStatystyczna | The sum of statistical values. |
| LacznaLiczbaPozycji | The total number of goods items. |
| PozId | The consecutive number of a given goods item. |
| OpisTowaru | The trade name of the commodity. |
| KrajPochodzeniaWysylki | The International Organization for Standardization (ISO) code for the country or region of the counterparty. |
| WarunkiDostawy | The Intrastat code for the delivery terms. |
| RodzajTransakcji | The code that indicates the nature of the transaction. Polish companies use two-digit transaction codes. |
| KodTowarowy | The eight-digit commodity code according to the Combined Nomenclature. |
| RodzajTransportu | The Intrastat code for the transport mode. |
| KrajPochodzenia | The ISO code for the country or region where the commodities were produced or manufactured. |
| MasaNetto | The net mass in full kilograms. |
| IloscUzupelniajacaJm | The quantity in the supplementary unit of measure, in whole numbers. |
| WartoscFaktury | The invoice value of all transactions that are covered by one item. |
| WartoscStatystyczna | The statistical value. |
| Wypelniajacy: NazwiskoImie, Telefon, Faks, Email | The first and last names, telephone number, fax number, and email address of the person who submits the declaration. |
| IdKontrahenta | The customer's foreign VAT number in an EU member state. |

## Set up Intrastat

From the Global repository, import the latest version of the following Electronic reporting (ER) configurations:

   - Intrastat model
   - Intrastat report
   - Intrastat (PL)

For more information, see [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

## Set up a VAT ID and an enterprise number for your company

### Create registration types for company codes

You must create two registration types for company codes: one for the VAT ID (NIP code) and one for the enterprise number (Regon code).

To create registration types for company codes, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** > **Global address book** > **Registration types** > **Registration types**.
1. On the Action Pane, select **New** to create a registration type for the VAT ID.
1. In the **Enter registration type details** dialog, in the **Name** field, enter a name for the new registration type. For example, enter "NIP".
1. In the **Country/region** field, select **POL**.
1. Select **Create**.
1. On the Action Pane, select **New** to create a registration type for the enterprise number.
1. In the **Enter registration type details** dialog, in the **Name** field, enter a name for the new registration type. For example, enter "Regon".
1. In the **Country/region** field, select **POL**.
1. Select **Create**.

### Match the registration types with registration categories

To match the registration types with registration categories, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** > **Global address book** > **Registration types** > **Registration categories**.
1. On the Action Pane, select **New** to create a link between each registration type that you created and a registration category.
    - For the registration type for the VAT ID (NIP code), select the **VAT ID** registration category.
    - For the registration type for the enterprise number (Regon code), select the **Enterprise ID (COID)** registration category.

### Set up a VAT ID and an enterprise number for your company

To set up a VAT ID and an enterprise number for your company, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** > **Organizations** > **Legal entities**.
1. In the grid, select your company.
1. On the Action Pane, select **Registration IDs**.
1. On the **Registration ID** FastTab, select **Add**.
1. In the **Registration type** field, select one of the registration types that you created earlier.
1. Enter your company's VAT ID (NIP code) or enterprise number (Regon code), depending on the registration type that you selected in the previous step.
1. Repeat steps 4 through 6 for the other registration type that you created earlier.

## Set up a company address

To set up a company address, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** > **Organizations** > **Legal entities**.
1. In the grid, select your company.
1. On the **Addresses** tab, select **Edit**.
1. In the **Edit address** dialog, in the **ZIP/postal code** field, select your company's ZIP/postal code.
1. In the **Street** field, enter your address.
1. In the **City** field, select your city.

## Set up foreign trade parameters

To set up foreign trade parameters, follow these steps:

1. In Dynamics 365 Finance, go to **Tax** > **Setup** > **Foreign trade parameters**.
1. On the **Intrastat** tab, on the **Electronic reporting** FastTab, in the **File format mapping** field, select **Intrastat (PL)**.
1. In the **Report format mapping** field, select **Intrastat report**.
1. On the **Commodity code hierarchy** FastTab, in the **Category hierarchy** field, select **Intrastat**. The **Category hierarchy type** of the **Category hierarchy** you select in the **Category hierarchy** field must be set to the **Commodity code hierarchy** on the **Category hierarchy role associations** page. (**Modules** > **Product information management** > **Setup** > **Categories and attributes** > **Category hierarchy**)
1. In the **Transaction code** field, select the transaction code for property transfers. Use this code for transactions that produce actual or planned transfers of property against compensation (financial or otherwise). Use it also for corrections. Companies in Poland use two-digit transaction codes.
1. In the **Credit note** field, select the transaction code for the return of goods.
1. On the **Country/region properties** tab, in the **Country/region** field, list all the countries or regions that your company does business with. For each country that is part of the EU, select **EU** in the **Country/region type** field, so that the country appears on your Intrastat report. For Poland, select **Domestic** in the **Country/region type** field.
1. On the **Agent** tab, on the **Agent** FastTab, in the **Sales tax** section, in the **Tax exempt number** field, enter "420000" to indicate the unit code that the Intrastat declaration is addressed to.
1. On the **Contact** tab, enter the name, telephone number, fax number, and email address of the person who is submitting the declaration.
1. On the **Number sequences** tab, in the **Number sequence code** field for the **XML file number** reference, specify a non-continuous number sequence that has a maximum of nine characters. This field is used to automatically generate a value for the **Declaration identifier** field on the Intrastat report.

## Set up product parameters for the Intrastat declaration

To set up product parameters for the Intrastat declaration, follow these steps:

1. In Dynamics 365 Finance, go to **Product information management** > **Products** > **Released products**.
1. In the grid, select a product.
1. On the **Foreign trade** FastTab, in the **Intrastat** section, in the **Commodity** field, select the commodity code. The name of the commodity prints in the **Description of commodities** field on the Intrastat report.
1. In the **Origin** section, in the **Country/region** field, select the product's country or region of origin.
1. On the **Manage inventory** FastTab, in the **Net weight** field, enter the product's weight in kilograms.

## Set up compression of Intrastat

-   In Dynamics 365 Finance, go to **Tax** > **Setup** > **Foreign trade** > **Compression of Intrastat**, and select the fields that should be compared when Intrastat information is summarized. For Polish Intrastat, select the following fields:

    - Commodity
    - Transaction code
    - Country/region of origin
    - Transport
    - Delivery terms
    - Country/region of sender
    - Country/region
    - Correction
    - Tax exempt number
    - Direction
    - Invoice

## Set up the transport method and delivery terms

To set up the transport method and delivery terms, follow these steps:

1.  Set up transport codes.

    1. In Dynamics 365 Finance, go to **Tax** > **Setup** > **Foreign trade** > **Transport method**.
    1. On the Action Pane, select **New**.
    1. In the **Transport** field, enter a unique code. Polish companies use one-digit transport codes.

1.  Set up mode of delivery Intrastat codes.

    1. Go to **Procurement and sourcing** > **Setup** > **Distribution** > **Terms of delivery**.
    1. In the grid, select a set of delivery terms.
    1. On the **General** FastTab, in the **Intrastat code** field, enter the unique code.

## Intrastat transfer

On the **Intrastat** page, on the Action Pane, select **Transfer** to automatically transfer the information about intracommunity trade from your sales orders, free-text invoices, purchase orders, vendor invoices, vendor product receipts, project invoices, and transfer orders. The system transfers only documents that have an EU country as the country or region of destination or consignment.

You can also manually enter transactions by selecting **New** on the Action Pane.

### Generate an Intrastat report

To generate an Intrastat report, follow these steps:

1. In Dynamics 365 Finance, go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**.
1. On the Action Pane, select **Output** > **Report**.
1. In the **Intrastat Report** dialog, set the following fields.

    | Field | Description |
    |-------------------------|-------------------------|
    | From date | Select the start date for the report. |
    | Generate file | Set this option to **Yes** to generate a .xml file for your Intrastat report. |
    | File name | Enter the name of the .xml file. |
    | Generate report | Set this option to **Yes** to generate an .xlsx file for your Intrastat report. |
    | Report file name | Enter the name of the .xlsx file. |
    | Direction | Select **Arrivals** for a report about intracommunity arrivals.</br>Select **Dispatches** for a report about intracommunity dispatches. |
    | Declaration identifier | The document ID is automatically generated and can be updated. |
    | Declaration type | Select **Declaration** for an original declaration.</br>Select **Declaration correction – replacement** for a correction declaration that is intended to fully replace an existing, previously submitted original or correction declaration. |
    | City of document creation | Enter the value that should be printed in the **Miejscowosc** field in the Intrastat declaration. |
    | Date of document creation | Enter the value that should be printed in the **Deklaracja Data** field in the Intrastat declaration. |
    | Document No | Enter the value that should be printed in the **Numer** field in the Intrastat declaration. |
    | Document version | Enter the value that should be printed in the **Wersja** field in the Intrastat declaration. |

1. Select **OK**, and review the generated reports.

## Example

This example shows how to post arrivals and dispatches for Intrastat by using the **DEMF** legal entity.

### Preliminary setup

Import the latest version of the following ER configurations:

   - Intrastat model
   - Intrastat report
   - Intrastat (PL)

### Set up a company address

To set up a company address, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** > **Global address book** > **Addresses** > **Address setup**.
1. On the **City** tab, select **New**.
1. In the **Country/region** field, select **POL**.
1. In the **City** field, enter "Warsaw".
1. On the **ZIP/postal code** tab, select **New**.
1. In the **Country/region** field, select **POL**.
1. In the **City** field, select **Warsaw**.
1. In the **ZIP/postal code** field, enter "00-844".
1. Go to **Organization administration** > **Organization** > **Legal entities**, and then select the **DEMF** legal entity.
1. On the **Addresses** FastTab, select **Edit**.
1. In the **Country/region** field, select **POL**.
1. In the **ZIP/postal code** field, select **31-111**.
1. In the **Street** field, enter "Statystyczna 22/1".
1. In the **City** field, select **Warsaw**.
1. Select **OK**.

## Set up a VAT ID and an enterprise number code for your company

### Create registration types for company codes

To create registration types for company codes, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** > **Global address book** > **Registration types** > **Registration types**.
1. On the Action Pane, select **New** to create a registration type for the VAT ID (NIP code).
1. In the **Enter registration type details** dialog, in the **Name** field, enter "NIP".
1. In the **Country/region** field, select **POL**.
1. Select **Create**.
1. On the Action Pane, select **New** to create a registration type for the enterprise number (Regon code).
1. In the **Enter registration type details** dialog, in the **Name** field, enter "Regon".
1. In the **Country/region** field, select **POL**.
1. Select **Create**.

### Match the registration types with registration categories

To match the registration types with registration categories, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** > **Global address book** > **Registration types** > **Registration categories**.
1. On the Action Pane, select **New** to create a link between each registration type that you created and a registration category.

    - For the **NIP** registration type, select the **VAT ID** registration category.
    - For the **Regon** registration type, select the **Enterprise ID (COID)** registration category.

### Set up a VAT ID and an enterprise number for your company

To set up a VAT ID and an enterprise number for your company, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** > **Organizations** > **Legal entities**.
1. In the grid, select **DEMF**.
1. On the Action Pane, select **Registration IDs**.
1. On the **Registration ID** FastTab, select **Add**.
1. In the **Registration type** field, select **NIP**.
1. In the **Registration number** field, enter "1234567890".
1. Select **Add**.
1. In the **Registration type** field, select **Regon**.
1. In the **Registration number** field, enter "12345678901234".

### Set up a number sequence code

To set up a number sequence code, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** > **Number sequences** > **Number sequences**.
1. On the Action Pane, on the **Number sequence** tab, in the **New** group, select **Number sequence**.
1. On the **Identification** FastTab, in the **Number sequence code** field, enter "XML\_file".
1. On the **Scope parameters** FastTab, in the **Scope** field, select **Company**.
1. In the **Company** field, select **DEMF**.
1. On the **Segments** FastTab, in the **Length** field for the **Alphanumeric** segment, enter "4".
1. On the **General** FastTab, in the **Setup** section, set the **Continuous** option to **No**.
1. In the **Number allocation** section, in the **Largest** field, enter "9999".

### Set up foreign trade parameters

To set up foreign trade parameters, follow these steps:

1. In Dynamics 365 Finance, go to **Tax** > **Setup** > **Foreign trade** > **Foreign trade parameters**.
1. On the **Intrastat** tab, on the **General** FastTab, in the **Transaction** **code** field, select **11**.
1. On the **Electronic reporting** FastTab, in the **File format mapping** field, select **Intrastat (PL)**.
1. In the **Report format mapping** field, select **Intrastat Report**.
1. On the **Commodity code hierarchy** FastTab, verify that the **Category hierarchy** field is set to **Intrastat**.
1. On the **Country/region properties** tab, select **New**.
1. In the **Party country/region** field, select **POL**. Then, in the **Country/region type** field, select **Domestic**.
1. In the **Party country/region** field, select **DEU**. Then, in the **Country/region type** field, select **EU**.
1. On the **Agent** tab, on the **Agent** FastTab, in the **Sales tax** section, in the **Tax exempt number** field, enter "420000".
1. On the **Contact** tab, in the **Name** field, enter "Manish Chopra".
1. In the **Telephone** field, enter "425-555-5068".
1. In the **Fax number** field, enter "425-555-5049".
1. In the **Email** field, enter "manishc@contoso.com".
1. On the **Number sequences** tab, in the **Number sequence code** field for the **XML file number** reference, select **XML_file**.

### Set up product information

To set up product information, follow these steps:

1. In Dynamics 365 Finance, go to **Product information management** > **Products** > **Released products**.
1. In the grid, select **D0001**.
1. On the **Foreign trade** FastTab, in the **Intrastat** section, in the **Commodity** field, select **100 200 30**.
1. On the **Manage inventory** FastTab, in the **Weight measurements** section, in the **Net weight** field, enter "2".
1. On the Action Pane, select **Save**.
1. In the grid, select **D0003**.
1. On the **Foreign trade** FastTab, in the **Intrastat** section, in the **Commodity** field, select **100 200 30**.
1. In the **Origin** section, in the **Country/region** field, select **DEU**.
1. On the **Manage inventory** FastTab, in the **Weight measurements** section, in the **Net weight** field, enter "5".
1. On the Action Pane, select **Save**.

### Change the site address

To change the site address, follow these steps:

1. In Dynamics 365 Finance, go to **Warehouse management** > **Setup** > **Warehouse** > **Sites**.
1. In the grid, select **1**.
1. On the **Addresses** FastTab, select **Edit**.
1. In the **Edit address** dialog, in the **Country/region** field, select **POL**.
1. Select **OK**.

### Set up a transport method

To set up a transport method, follow these steps:

1. Create a transport method.

    1. In Dynamics 365 Finance, go to **Tax** > **Setup** > **Foreign trade** > **Transport method**.
    1. On the Action Pane, select **New**.
    1. In the **Transport** field, enter "3".
    1. In the **Description** field, enter "Road transport".

1. Assign the new transport method to a mode of delivery. When you assign the transport method to a mode of delivery, you set up the default values that the system uses for the transport method when the corresponding mode of delivery is selected.

    1. Go to **Procurement and sourcing** > **Setup** > **Distribution** > **Modes of delivery**.
    1. In the grid, select **10**.
    1. On the **Foreign trade** FastTab, in the **Transport** field, select **3**.

1. Select the default mode of delivery for a customer.

    1. Go to **Accounts receivable** > **Customers** > **All customers**.
    1. In the grid, select **DE-016**.
    1. On the **Invoice and delivery** FastTab, in the **Mode of delivery** field, select **10**.

1. Select the default mode of delivery for a vendor.

    1. Go to **Accounts payable** > **Vendors** > **All vendors**.
    1. In the grid, select **DE-001**.
    1. On the **Invoice and delivery** FastTab, in the **Mode of delivery** field, select **10**.

### Set up codes for terms of delivery

To set up codes for terms of delivery, follow these steps:

1. Set up an Intrastat code for the terms of delivery.

    1. In Dynamics 365 Finance, go to **Procurement and sourcing** > **Setup** > **Distribution** > **Terms of delivery**.
    1. In the grid, select **CIF**.
    1. On the **General** FastTab, in the **Intrastat code** field, enter "CIF".

1. Select the default delivery terms for a customer.

    1. Go to **Accounts receivable** > **Customers** > **All customers**.
    1. In the grid, select **DE-016**.
    1. On the **Invoice and delivery** FastTab, in the **Delivery terms** field, select **CIF**.

1. Select the default delivery terms for a vendor.

    1. Go to **Accounts payable** > **Vendors** > **All vendors**.
    1. In the grid, select **DE-001**.
    1. On the **Invoice and delivery** FastTab, in the **Delivery terms** field, select **CIF**.

### Verify an EU customer's tax-exempt number code

To verify an EU customer's tax-exempt number code, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable** > **Customers** > **All customers**.
1. In the grid, select **DE-016**.
1. On the **Invoice and delivery** FastTab, in the **Sales tax** section, verify that the **Tax exempt number** field is set to **DE9012**.

### Create a sales order with an EU customer

To create a sales order with an EU customer, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable** > **Orders** > **All sales orders**.
1. On the Action Pane, select **New**.
1. In the **Create sales order** dialog, on the **Customer** FastTab, in the **Customer** section, in the **Customer account** field, select **DE-016**.
1. On the **General** FastTab, in the **Storage dimensions** section, in the **Site** field, select **1**.
1. In the **Warehouse** field, select **11**.
1. On the **Address** tab, verify that the **Address** field is set to **Teichgasse 12, Kiel, 24103, DEU**, because the customer is from Germany.
1. Select **OK**.
1. On the **Header** tab, on the **Delivery** FastTab, verify that the **Delivery terms** field is set to **CIF**, and the **Mode of delivery** field is set to **10**.
1. On the **Lines** tab, on the **Sales order lines** FastTab, in the **Item number** field, select **D0001**. Then, in the **Quantity** field, enter "8".
1. On the **Line details** FastTab, on the **Foreign trade** tab, verify that the **Transaction code** field is set to **11**, the **Commodity** field is set to **100 200 30**, and the **Country/region of origin** field is set to **POL**.
1. On the Action Pane, select **Save**.
1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
1. In the **Posting invoice** dialog, on the **Parameters** FastTab, in the **Parameter** section, in the **Quantity** field, select **All**.
1. On the **Setup** FastTab, in the **Sales date** field, select **10/18/2021** (October 18, 2021).
1. Select **OK** to post the invoice.

### Transfer the transaction to the Intrastat journal and review the result

To transfer the transaction to the Intrastat journal and review the result, follow these steps:

1. In Dynamics 365 Finance, go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**.
1. On the Action Pane, select **Transfer**.
1. In the **Intrastat (Transfer)** dialog, in the **Parameters** section, set the **Customer invoice** option to **Yes**.
1. Select **Filter**.
1. In the **Intrastat Filter** dialog, on the **Range** tab, select the first line, and verify that the **Field** field is set to **Date**.
1. In the **Criteria** field, select the current date.
1. Select **OK** to close the **Intrastat Filter** dialog.
1. Select **OK** to close the **Intrastat (Transfer)** dialog, and review the result. The line represents the sales order that you created earlier.

    :::image type="content" source="../media/intrastat_pl_1.png" alt-text="Screenshot of the line that represents the sales order on the Intrastat page.":::

1. Select the transaction line, and then select the **General** tab to view more details.

    :::image type="content" source="../media/intrastat_pl_2.png" alt-text="Screenshot of sales order details on the General tab of the Intrastat page.":::

1. On the Action Pane, select **Output** > **Report**.
1. In the **Intrastat Report** dialog, on the **Parameters** FastTab, in the **Date** section, in the **From date** field, select the first day of the current month.
1. In the **Export** **options** section, set the **Generate file** option to **Yes**. Then, in the **File name** field, enter the required name.
1. Set the **Generate report** option to **Yes**. Then, in the **Report file name** field, enter the required name.
1. In the **Direction** field, select **Dispatches**.
1. In the **File format mapping** section, verify that the **Declaration type** field is set to **Declaration**.
1. In the **City of document creation** field, enter "Krakow".
1. In the **Date of document creation** field, select **10/19/2021** (October 19, 2021).
1. In the **Document No** field, enter "11".
1. In the **Document version** field, enter "22".
1. Select **OK**, and review the report in XML format that is generated. The following table shows the values in the example report.

    | Field name | Field description | Value |
    |---|---|---|
    | **Information about the document** | | |
    | Deklaracja Data | The date when the document was created. | 2021-10-19 |
    | Miejscowosc | The city where the document was created. | Krakow |
    | LacznaLiczbaPozycji | The total number of items. | 1 |
    | LacznaWartoscStatystyczna | The total statistical value. | 2632 |
    | LacznaWartoscFaktur | The total invoice value. | 2632 |
    | UC | The unit code. | 420000 |
    | Rodzaj | The type of declaration. | D |
    | Wersja | The document version. | 22 |
    | Numer | The document number. | 11 |
    | Miesiac | The reference month. | 10 |
    | Rok | The reference year. | 2021 |
    | Typ | The report direction. | W |
    | NrWlasny | The declaration identifier. | 21ISTDEMF-0001 |
    | **Information about the company** | | |
    | Miejscowosc | The city where the company is located. | Warsaw |
    | Regon | The company's Regon code. | 12345678901234 |
    | Nip | The company's NIP code. | 1234567890 |
    | KodPocztowy | The company's ZIP/postal code. | 31-111 |
    | UlicaNumer | The street where the company is located. | Statystyczna 22/1 |
    | Nazwa | The name of the company. | Contoso Entertainment System Germany |
    | **Information about the good** | | |
    | WartoscStatystyczna | The statistical value. | 2632 |
    | WartoscFaktury | The invoice value. | 2632 |
    | MasaNetto | The net mass. | 16 |
    | IdKontrahenta | The customer's VAT number. | DE9012 |
    | KodTowarowy | The commodity code. | 10020030 |
    | RodzajTransakcji | The transaction code. | 11 |
    | WarunkiDostawy | The terms of delivery mode. | CIF |
    | KrajPochodzeniaWysylki | The code for the country or region of dispatch/destination. | DE |
    | OpisTowaru | A description of the commodities. | Hardware |
    | PozId | The item number. | 1 |
    | **Contact information** | | |
    | Email | The submitter's email address. | manishc@contoso.com |
    | Faks | The submitter's fax number. | 425-555-5049 |
    | Telefon | The submitter's telephone number. | 425-555-5068 |
    | NazwiskoImie | The submitter's name. | Manish Chopra |

1. Review the report in Excel format that is generated.

    :::image type="content" source="../media/intrastat_pl_3.png" alt-text="Screenshot of the Intrastat report on dispatches.":::

### Create a purchase order

To create a purchase order, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts payable** > **Purchase orders** > **All purchase orders**.
1. On the Action Pane, select **New**.
1. In the **Create purchase order** dialog, in the **Vendor account** field, select **DE-001**.
1. In the **Site** field, select **1**.
1. In the **Warehouse** field, select **11**.
1. Select **OK**.
1. On the **Header** tab, on the **Delivery** FastTab, verify that the **Mode of delivery** field is set to **10**, and the **Delivery terms** field is set to **CIF**.
1. On the **Lines** tab, on the **Purchase order lines** FastTab, in the **Item number** field, select **D0003**. Then, in the **Quantity** field, enter "6".
1. On the **Line details** FastTab, on the **Foreign trade** tab, verify that the **Transaction code** is set to **11**, the **Transport** field is set to **3**, the **Commodity** field is set to **100 200 30**, and the **Country/region of origin** field is set to **DEU**.
1. On the Action Pane, on the **Purchase** tab, in the **Actions** group, select **Confirm**.
1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
1. On the Action Pane, select **Default from**, and then, in the **Default quantity for lines** field, select **Ordered quantity**. Then select **OK**.
1. On the **Vendor Invoice header** FastTab, in the **Invoice identification** section, in the **Number** field, enter "00010".
1. In the **Invoice dates** section, in the **Invoice date** field, select the current date. This date is used for Intrastat transfer.
1. In the **Receive document date** field, select **10/18/2021** (October 18, 2021).
1. On the Action Pane, select **Post** to post the invoice.

### Create an Intrastat declaration for arrivals

To create an Intrastat declaration for arrivals, follow these steps:

1. In Dynamics 365 Finance, go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**.
1. On the Action Pane, select **Transfer**.
1. In the **Intrastat (Transfer)** dialog, set the **Vendor invoice** option to **Yes**.
1. Select **OK** to transfer the transactions, and then review the Intrastat journal.

    :::image type="content" source="../media/intrastat_pl_4.png" alt-text="Screenshot of the line that represents the purchase order on the Intrastat page.":::

1. Review the information on the **General** tab for the purchase order.

    :::image type="content" source="../media/intrastat_pl_5.png" alt-text="Screenshot of purchase order details on the General tab of the Intrastat page.":::

1. On the Action Pane, select **Output** > **Report**.
1. In the **Intrastat Report** dialog, on the **Parameters** FastTab, in the **Date** section, in the **From date** field, select the first day of the current month.
1. In the **Export** **options** section, set the **Generate file** option to **Yes**. Then, in the **File name** field, enter the required name.
1. Set the **Generate report** option to **Yes**. Then, in the **Report file name** field, enter the required name.
1. In the **Direction** field, select **Arrivals**.
1. In the **File format mapping** section, verify that the **Declaration type** field is set to **Declaration**.
1. In the **City of document creation** field, enter "Krakow".
1. In the **Date of document creation** field, select **10/19/2021** (October 19, 2021).
1. In the **Document No** field, enter "11".
1. In the **Document version** field, enter "22".
1. Select **OK**, and review the report in XML format that is generated. The following table shows the values in the example report.

    | Field name | Field description | Value |
    |---|---|---|
    | **Information about the document** | | |
    | Deklaracja Data | The date when the document was created. | 2021-10-19 |
    | Miejscowosc | The city where the document was created. | Krakow |
    | LacznaLiczbaPozycji | The total number of items. | 1 |
    | LacznaWartoscStatystyczna | The total statistical value. | 965 |
    | LacznaWartoscFaktur | The total invoice value. | 965 |
    | UC | The unit code. | 420000 |
    | Rodzaj | The type of declaration. | D |
    | Wersja | The document version. | 22 |
    | Numer | The document number. | 11 |
    | Miesiac | The reference month. | 10 |
    | Rok | The reference year. | 2021 |
    | Typ | The report direction. | P |
    | NrWlasny | The declaration identifier. | 21ISTDEMF-0002 |
    | **Information about the company** | | |
    | Miejscowosc | The city where the company is located. | Warsaw |
    | Regon | The company's Regon code. | 12345678901234 |
    | Nip | The company's NIP code. | 1234567890 |
    | KodPocztowy | The company's ZIP/postal code. | 31-111 |
    | UlicaNumer | The street where the company is located. | Statystyczna 22/1 |
    | Nazwa | The name of the company. | Contoso Entertainment System Germany |
    | **Information about the good** | | |
    | WartoscStatystyczna | The statistical value. | 965 |
    | WartoscFaktury | The invoice value. | 965 |
    | MasaNetto | The net mass. | 30 |
    | KrajPochodzenia | The code for the country or region of origin. | DE |
    | RodzajTransportu | The mode of transport code. | 3 |
    | KodTowarowy | The commodity code. | 10020030 |
    | RodzajTransakcji | The transaction code. | 11 |
    | WarunkiDostawy | The terms of delivery mode. | CIF |
    | KrajPochodzeniaWysylki | The code for the country or region of dispatch/destination. | DE |
    | OpisTowaru | A description of the commodities. | Hardware |
    | PozId | The item number. | 1 |
    | **Contact information** | | |
    | Email | The submitter's email address. | manishc@contoso.com |
    | Faks | The submitter's fax number. | 425-555-5049 |
    | Telefon | The submitter's telephone number. | 425-555-5068 |
    | NazwiskoImie | The submitter's name. | Manish Chopra |

1. Review the report in Excel format that is generated.

    :::image type="content" source="../media/intrastat_pl_6.png" alt-text="Screenshot of the Intrastat report on arrivals.":::
