---
title: Latvian Intrastat
description: Learn how to set up the Latvian Intrastat report in Microsoft Dynamics 365 Finance.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 05/04/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 
---

# Latvian Intrastat

[!include [banner](../../includes/banner.md)]

This article explains how to set up the Latvian Intrastat report in Microsoft Dynamics 365 Finance.

Use the **Intrastat** page to generate and report information about trade among European Union (EU) countries and regions. The Latvian Intrastat declaration contains information about the trade of goods for reporting.

The Latvian Intrastat declaration consists of two parts:

- **Header**: The header contains information about the company, the person who is employed by the company to fill in the declaration, and the trading items.
- **Intrastat formats**: The second part of the declaration has two formats: Intrastat format A for a simplified report and Intrastat format B for a full report.

The following table shows the fields that are included on the header. The header is the same in Intrastat format A and Intrastat format B.

| Field on the Intrastat declaration | Description |
|-------------------------|-------------------------|
| VAT registration number | The value-added tax (VAT) ID of the company. Set this ID in the **Tax registration number** field on the **Tax registration** FastTab of the **Legal entity** page. |
| Legal address | The full address of the legal entity. Set this address on the **Addresses** FastTab of the **Legal entity** page. |
| Contact address | The address of the legal entity for communication. This address is the same as the legal address. |
| Company's phone | The company's primary telephone number. Set this number on the **Contact information** FastTab of the **Legal entity** page. |
| Company's fax | The company's primary fax number. Set this number on the **Contact information** FastTab of the **Legal entity** page. |
| Company's email | The company's primary email address. Set this address on the **Contact information** FastTab of the **Legal entity** page. |
| Contact person name | The name of the employee who is filling in the declaration. Set this name on the **Agent** tab of the **Foreign trade parameters** page. |
| Contact person phone | The contact telephone number of the employee who is filling in the declaration. Set this number on the **Agent** tab of the **Foreign trade parameters** page. |
| Declaration type | This field contains information about the direction of the Intrastat report and the format of the declaration.<ul><li>For a full Intrastat report about arrivals, "Ievedums-1B" is printed.</li><li>For a full Intrastat report about dispatches, "Izvedums-2B" is printed.</li><li>For a simplified Intrastat report about arrivals, "Ievedums-1A" is printed.</li><li>For a simplified Intrastat report about dispatches, "Izvedums-2A" is printed.</li></ul> |
| Reporting year | The reference year of the declaration. |
| Reporting month | The reference month of the declaration. |
| Total number of records | The total number of records for the declaration. |
| Hours required for completion the report | The number of hours that the employee spent filling in the report. Specify this number in the **Intrastat report** dialog box. |
| Minutes required for completion the report | The number of minutes that the employee spent filling in the report. Specify this number in the **Intrastat report** dialog box. |

For full declarations (Intrastat format B), the second part of the report describes the intracommunity trade and includes the following fields. All the fields except **Statistical value** and **Partner ID** are included on both arrivals and dispatches. The **Statistical value** and **Partner ID** fields are included only on dispatches.

| Field on the Intrastat declaration | Description                                                                                                                                    |
|------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------|
| Commodity code                     | The commodity code according to the Combined Nomenclature (CN) classification. Set this code on the product page.                           |
| Invoice value                      | The invoice value. You can view the invoice value in the **Invoice amount** field in the Intrastat journal.                                    |
| Net mass                           | The net mass of the goods item in kilograms. The unit itself ("kg") isn't printed.                                                             |
| Supplementary units                | For some commodities, you must report the supplementary unit. The unit itself (for example, "pairs" or "dozens") isn't reported.               |
| Partner country                    | The International Organization for Standardization (ISO) code for the country or region of the partner (counterparty).                         |
| Country of origin                  | The ISO code for the country or region where the goods were produced. Set this code in the **Country of origin** field on the product page. |
| Nature of transaction              | The code that indicates the nature of the transaction.                                                                                         |
| Mode of transport                  | The code for the mode of transport.                                                                                                            |
| Delivery terms                     | The code that indicates the way that the commodities are transported to or from Latvia.                                                        |
| Statistical value                  | The statistical value. You can view the statistical value in the **Statistical value** field in the Intrastat journal.                         |
| Partner ID                         | The tax-exempt number of the counterparty.                                                                                                     |

For simplified declarations (Intrastat format A), the second part of the report includes only the following fields:

- Commodity code
- Invoice value
- Net mass
- Supplementary units
- Partner country
- Country of origin
- Nature of transaction

All the fields except **Country of origin** are included on both arrivals and dispatches. The **Country of origin** field is included only on arrivals.

For more information, see [https://e.csb.gov.lv](https://e.csb.gov.lv/HelpDesk/UI/Page.aspx?pid=41).

## Set up Intrastat

### Import Electronic reporting configurations

To set up Intrastat, import the latest version of the following Electronic reporting (ER) configurations:

- Intrastat model
- Intrastat report
- Intrastat A (LV)
- Intrastat B (LV)

For more information, see [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

### Set up contact information

Set up your company's telephone number, email address, and fax number.

To set up contact information, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** > **Organizations** > **Legal entities**.
1. In the grid, select your company.
1. On the **Contact information** FastTab, select **Add** to create a contact.
1. In the **Type** field, select the type of communication.
1. In the **Contact number/address** field, enter your company's contact information.
1. Select the **Primary** option to print this contact information on the report.

### Set up VAT IDs

#### Set up the VAT ID for your company

To set up the VAT ID for your company, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** > **Organizations** > **Legal entities**.
1. In the grid, select your company.
1. On the **Tax registration** FastTab, in the **Tax registration number** field, enter the VAT ID for your company.

#### Set up the VAT number for a trading partner

##### Create a registration type for the company code

You must create VAT ID registration types for all the countries or regions that your company does business with.

To create a registration type for the company code, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** > **Global address book** > **Registration types** > **Registration types**.
1. On the Action Pane, select **New** to create a registration type for the VAT ID.
1. In the **Enter registration type details** dialog box, in the **Name** field, enter a name for the new registration type. For example, enter **VAT ID**.
1. In the **Country/region** field, select the country or region that your company does business with.
1. Select **Create**.

##### Match the registration type with a registration category

To match the registration type with a registration category, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** > **Global address book** > **Registration types** > **Registration categories**.
1. On the Action Pane, select **New** to create a link between a registration type and a registration category.
1. For the registration type for the VAT ID, select the **VAT ID** registration category.
1. Repeat steps 2 through 3 for the other registration types that you created for the countries or regions that your company does business with.

##### Create a customer's VAT registration number

To create a customer's VAT registration number, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable** > **Customers** > **All customers**.
1. In the grid, select a customer.
1. On the Action Pane, on the **Customer** tab, in the **Registration** group, select **Registration IDs**.
1. On the **Registration ID** FastTab, select **Add** to create a registration ID.
1. In the **Registration type** field, select the registration type that you previously created for the company code.
1. In the **Registration number** field, enter the company's VAT number.
1. On the Action Pane, select **Save**. Then close the page.

For more information, see [Registration IDs](../europe/emea-registration-ids.md).

Alternatively, you can create a customer's VAT registration number by using the **Tax exempt number** page.

To create a customer's VAT registration number by using the **Tax exempt number** page, follow these steps:

1. In Dynamics 365 Finance, go to **Tax** > **Setup** > **Sales tax** > **Tax exempt numbers**.
1. For each tax-exempt number, create a record that includes the following information:
    - **Country/region**: Select the tax registration of the counterparty.
    - **Tax exempt number**: Enter the tax-exempt number of the counterparty.
    - **Company name**: Enter the name of the counterparty.
1. Go to **Accounts receivable** > **Customers** > **All customers**.
1. In the grid, select a customer.
1. On the **Invoice and delivery** FastTab, in the **Sales tax** section, in the **Tax exempt number** field, select the registration number that you just created.

### Set up foreign trade parameters

To set up foreign trade parameters, follow these steps:

1. In Dynamics 365 Finance, go to **Tax** > **Setup** > **Foreign trade** > **Foreign trade parameters**.
1. On the **Intrastat** tab, on the **Electronic reporting** FastTab, in the **File format mapping** field, select **Intrastat A (LV)** or **Intrastat B (LV)**.
1. In the **Report format mapping** field, select **Intrastat report**.
1. On the **Commodity code hierarchy** FastTab, in the **Category hierarchy** field, select **Intrastat**.
1. In the **Transaction code** field, select the transaction code for property transfers. Use this code for transactions that send actual or planned transfers of property against compensation (financial or otherwise). Use it also for corrections.
1. In the **Credit note** field, select the transaction code for the return of goods.
1. On the **Agent** tab, add information about the person who is employed by the enterprise to fill in the report.
    1. In the **Agent** section, in the **Name** field, enter the first and last names of the agent.
    1. In the **Contact information** section, in the **Telephone** field, enter the telephone number of the agent.
1. On the **Country/region properties** tab, in the **Country/region** field, list all the countries or regions that your company does business with. For each country or region that is part of the EU, select **EU** in the **Country/region type** field, so that the country or region appears on your Intrastat report.

### Set up the product parameters for the Intrastat declaration

To set up the product parameters for the Intrastat declaration, follow these steps:

1. In Dynamics 365 Finance, go to **Product information management** > **Products** > **Released products**.
1. In the grid, select a product.
1. On the **Foreign trade** FastTab, in the **Intrastat** section, in the **Commodity** field, select a commodity code.
1. In the **Origin** section, in the **Country/region** field, select the product's country or region of origin.
1. On the **Manage inventory** FastTab, in the **Net weight** field, enter the product's weight in kilograms.

### Set up the transport method and mode of delivery

To set up the transport method and mode of delivery, follow these steps:

1. Set up transport codes.
    1. In Dynamics 365 Finance, go to **Tax** > **Setup** > **Foreign trade** > **Transport method**.
    1. On the Action Pane, select **New**.
    1. In the **Transport** field, enter a unique code. Latvian companies use one-digit transport codes.
1. Set up mode of delivery Intrastat codes.
    1. Go to **Procurement and sourcing** > **Setup** > **Distribution** > **Terms of delivery**.
    1. In the grid, select a set of terms of delivery.
    1. On the **General** FastTab, in the **Intrastat code** field, enter a unique code.

### Set up compression of Intrastat

To set up compression of Intrastat, complete the following steps:

In Dynamics 365 Finance, go to **Tax** > **Setup** > **Foreign trade** > **Compression of Intrastat**, and select the fields that should be compared when Intrastat information is summarized. For Latvian Intrastat, select the following fields:

- Commodity
- Transaction code
- Country/region of origin
- Country/region of sender
- Country/region
- Correction
- Tax exempt number
- Direction
- Invoice
- Delivery terms
- Transport

### Intrastat transfer

On the **Intrastat** page, on the Action Pane, select **Transfer** to automatically transfer the information about intracommunity trade from your sales orders, free text invoices, purchase orders, vendor invoices, vendor product receipts, project invoices, and transfer orders. Only documents that have an EU country/region as the country or region of destination (for dispatches) or consignment (for arrivals) are transferred.

Alternatively, you can manually enter transactions by selecting **New** on the Action Pane.

### Generate an Intrastat report

To generate an Intrastat report, follow these steps:

1. In Dynamics 365 Finance, go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**.
1. On the Action Pane, select **Output** &gt; **Report**.
1. In the **Intrastat Report** dialog box, enter the start and end dates for the report.
1. Set the **Generate file** option to **Yes** to generate a .xml file, and then enter the name of the .xml file for the Intrastat report.
1. Set the **Generate report** option to **Yes** to generate an .xlsx file, and then enter a name for the file.
1. In the **Direction** field, select **Arrivals** if the report is about intracommunity arrivals or **Dispatches** if the report is about intracommunity dispatches.
1. In the **File format mapping** section, in the **Hours required for completion** and **Minutes required for completion** fields, specify the amount of time that you spent filling in the report.
1. Select **OK**, and review the generated reports.

## Example

The following example shows how to set up Latvian Intrastat and create the Intrastat report. It uses the **DEMF** legal entity.

1. In Dynamics 365 Finance, go to **Organization administration** > **Organization** > **Legal entities**, and select the **DEMF** legal entity.
1. On the **Addresses** FastTab, select **Edit**.
1. In the **Country/region** field, select **LVA** (Latvia).
1. Import the latest version of the following ER configurations:

    - Intrastat model
    - Intrastat report
    - Intrastat B (LV)

### Set up an address format

To set up an address format, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** > **Organization** > **Legal entities**, and select the **DEMF** legal entity.
1. On the **Addresses** FastTab, select **Edit**.
1. In the **Street** field, enter **454 1st Street**.

### Set up contact information

To set up contact information, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** > **Organization** > **Legal entities**, and select the **DEMF** legal entity.
1. On the **Contact information** FastTab, select **Add** to create a contact.
1. In the **Type** field, select **Phone**.
1. In the **Contact number/address** field, enter **+49 123 456 789**.
1. Select the **Primary** option.
1. In the **Type** field, select **Fax**.
1. In the **Contact number/address** field, enter **425-555-5013**.
1. Select the **Primary** option.
1. In the **Type** field, select **Email address**.
1. In the **Contact number/address** field, enter **<jodi@contoso.com>**.
1. Select the **Primary** option.

### Set up VAT IDs

#### Set up the VAT ID for your company

To set up the VAT ID for your company, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** > **Organizations** > **Legal entities**.
1. In the grid, select **DEMF**.
1. On the **Tax registration** FastTab, in the **Tax registration number** field, enter **LV12345678**.

#### Create registration types for company codes

To create registration types for company codes, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** > **Global address book** > **Registration types** > **Registration types**.
1. On the Action Pane, select **New** to create a registration type for the VAT ID.
1. In the **Enter registration type details** dialog box, in the **Name** field, enter **VATID**.
1. In the **Country/region** field, select **DEU**.
1. In the **Restricted to** field, select **Organization**.
1. Select **Create**.

#### Match the registration type with a registration category

To match the registration type with a registration category, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** > **Global address book** > **Registration types** > **Registration categories**.
1. On the Action Pane, select **New** to create a link between the registration type and the registration category.
1. For the **VATID** registration type, select the **VAT ID** registration category.

#### Set up the customer's VAT registration number

To set up the customer's VAT registration number, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable** > **Customers** > **All customers**.
1. In the grid, select **DE-016**.
1. On the Action Pane, on the **Customer** tab, in the **Registration** group, select **Registration IDs**.
1. On the **Registration ID** FastTab, select **Add** to create a registration ID.
1. In the **Registration type** field, select **VATID**.
1. In the **Registration number** field, enter **DE9012**.
1. On the Action Pane, select **Save**. Then close the page.

### Set up foreign trade parameters

To set up foreign trade parameters, follow these steps:

1. In Dynamics 365 Finance, go to **Tax** > **Setup** > **Foreign trade** > **Foreign trade parameters**.
1. On the **Intrastat** tab, on the **General** FastTab, in the **Transaction** **code** field, select **11**.
1. On the **Electronic reporting** FastTab, in the **File format mapping** field, select **Intrastat B (LV)**.
1. In the **Report format mapping** field, select **Intrastat Report**.
1. On the **Commodity code hierarchy** FastTab, verify that the **Category hierarchy** field is set to **Intrastat**.
1. On the **Country/region properties** tab, select **New**.
1. In the **Party country/region** field, select **LVA**. Then, in the **Country/region type** field, select **Domestic**.
1. In the **Party country/region** field, select **DEU** (Germany). Then, in the **Country/region type** field, select **EU**.
1. On the **Agent** tab, in the **Name** field, enter **Manish Chopra**.
1. In the **Telephone** field, enter **425-555-5068**.

### Set up product information

To set up product information, follow these steps:

1. In Dynamics 365 Finance, go to **Product information management** > **Products** > **Released products**.
1. In the grid, select **D0001**.
1. On the **Foreign trade** FastTab, in the **Intrastat** section, in the **Commodity** field, select **100 200 30**.
1. In the **Origin** section, in the **Country/region** field, select **LVA**.
1. On the **Manage inventory** FastTab, in the **Weight measurements** section, in the **Net weight** field, enter **2**.
1. On the Action Pane, select **Save**.
1. In the grid, select **D0003**.
1. On the **Foreign trade** FastTab, in the **Intrastat** section, in the **Commodity** field, select **100 200 30**.
1. In the **Origin** section, in the **Country/region** field, select **DEU**.
1. On the **Manage inventory** FastTab, in the **Weight measurements** section, in the **Net weight** field, enter **5**.
1. On the Action Pane, select **Save**.

### Change the site address

To change the site address, follow these steps:

1. In Dynamics 365 Finance, go to **Warehouse management** > **Setup** > **Warehouse** > **Sites**.
1. In the grid, select **1**.
1. On the **Addresses** FastTab, select **Edit**.
1. In the **Edit address** dialog box, in the **Country/region** field, select **LVA**.
1. Select **OK** to close the **Edit address** dialog box.

### Set up a transport method

To set up a transport method, follow these steps:

1. Create a transport method.

    1. In Dynamics 365 Finance, go to **Tax** > **Setup** > **Foreign trade** > **Transport method**.
    1. On the Action Pane, select **New**.
    1. In the **Transport** field, enter **3**.
    1. In the **Description** field, enter **Road transport**.
1. Assign the transport method to the mode of delivery. When you assign the transport method to the mode of delivery, you set up the default values that are used for the transport method when the corresponding mode of delivery is selected.

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

1. Set up the Intrastat code for the terms of delivery.

    1. In Dynamics 365 Finance, go to **Procurement and sourcing** > **Setup** > **Distribution** > **Terms of delivery**.
    1. In the grid, select **CIF**.
    1. On the **General** FastTab, in the **Intrastat code** field, enter **CIF**.
1. Select the default delivery terms for a customer.

    1. Go to **Accounts receivable** > **Customers** > **All customers**.
    1. In the grid, select **DE-016**.
    1. On the **Invoice and delivery** FastTab, in the **Delivery terms** field, select **CIF**.
1. Select the default delivery terms for a vendor.

    1. Go to **Accounts payable** > **Vendors** > **All vendors**.
    1. In the grid, select **DE-001**.
    1. On the **Invoice and delivery** FastTab, in the **Delivery terms** field, select **CIF**.

### Create a sales order with an EU customer

To create a sales order with an EU customer, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable** > **Orders** > **All sales orders**.
1. On the Action Pane, select **New**.
1. In the **Create sales order** dialog box, on the **Customer** FastTab, in the **Customer** section, in the **Customer account** field, select **DE-016**.
1. On the **General** FastTab, in the **Storage dimensions** section, in the **Site** field, select **1**.
1. In the **Warehouse** field, select **11**.
1. On the **Address** tab, verify that the **Address** field is set to **Teichgasse 12, Kiel, 24103, DEU**, because the vendor is from Germany.
1. Select **OK**.
1. On the **Header** tab, on the **Delivery** FastTab, verify that the **Delivery terms** field is set to **CIF**.
1. On the **Lines** tab, on the **Sales order lines** FastTab, in the **Item number** field, select **D0001**. Then, in the **Quantity** field, enter **8**.
1. On the **Line details** FastTab, on the **Foreign trade** tab, verify that the **Transaction code** field is set to **11**, the **Transport** field is set to **3**, the **Commodity** field is set to **100 200 30**, and the **Country/region of origin** field is set to **LVA**.
1. On the Action Pane, select **Save**.
1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
1. In the **Posting invoice** dialog box, on the **Parameters** FastTab, in the **Parameter** section, in the **Quantity** field, select **All**.
1. Select **OK** to post the invoice.

### Transfer the transaction to the Intrastat journal and review the result

To transfer the transaction to the Intrastat journal and review the result, follow these steps:

1. In Dynamics 365 Finance, go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**.
1. On the Action Pane, select **Transfer**.
1. In the **Intrastat (Transfer)** dialog box, in the **Parameters** section, set the **Customer invoice** option to **Yes**.
1. Select **Filter**.
1. In the **Intrastat Filter** dialog box, on the **Range** tab, select the first line, and verify that the **Field** field is set to **Date**.
1. In the **Criteria** field, select the current date.
1. Select **OK** to close the **Intrastat Filter** dialog box.
1. Select **OK** to close the **Intrastat (Transfer)** dialog box, and review the result. The line represents the sales order that you created earlier.

    :::image type="content" source="../media/intrastat_lva_1.png" alt-text="Screenshot of the line that represents the sales order on the Intrastat page.":::

1. Select the transaction line, and then select the **General** tab to view more details.

    :::image type="content" source="../media/intrastat_lva_2.png" alt-text="Screenshot of sales order details on the General tab of the Intrastat page.":::

1. On the Action Pane, select **Output** > **Report**.
1. In the **Intrastat Report** dialog box, on the **Parameters** FastTab, in the **Date** section, select the month of the sales order that you created.
1. In the **Export** **options** section, set the **Generate file** option to **Yes**. Then, in the **File name** field, enter the required name.
1. Set the **Generate report** option to **Yes**. Then, in the **Report file name** field, enter the required name.
1. In the **Direction** field, select **Dispatches**.
1. In the **File format mapping** section, in the **Hours required for completion** field, enter **11**.
1. In the **Minutes required for completion** field, enter **22**.
1. Select **OK**, and review the report in XML format that is generated. The following table shows the values in the example report.

      | Field on the Intrastat declaration         | Value              |
      |--------------------------------------------|--------------------|
      | VAT registration number                    | LV12345678         |
      | Legal address                              | 454 1st Street LVA |
      | Contact address                            | 454 1st Street LVA |
      | Phone                                      | +49 123 456 789    |
      | Fax                                        | 425-555-5013       |
      | Email                                      | <jodi@contoso.com>   |
      | Contact person name                        | Manish Chopra      |
      | Contact person phone                       | 425-555-5068       |
      | Direction                                  | Izvedums-2B        |
      | Reporting year                             | 2021               |
      | Reporting month                            | M10                |
      | Total number of records                    | 1                  |
      | Hours required for completion the report   | 11                 |
      | Minutes required for completion the report | 22                 |
      | Commodity code                             | 10020030           |
      | Invoice value                              | 2632               |
      | Net mass                                   | 16                 |
      | Supplementary units                        | 0                  |
      | Partner country                            | DE                 |
      | Nature of transaction                      | 11                 |
      | Mode of transport                          | 3                  |
      | Delivery terms                             | CIF                |
      | Statistical value                          | 2632               |
      | Country of origin                          | LV                 |
      | Partner ID                                 | DE9012             |

1. Review the generated report file.

    :::image type="content" source="../media/intrastat_lva_3.png" alt-text="Screenshot of the Intrastat report on dispatches.":::

### Create a purchase order

To create a purchase order, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts payable** > **Purchase orders** > **All purchase orders**.
1. On the Action Pane, select **New**.
1. In the **Create purchase order** dialog box, in the **Vendor account** field, select **DE-001**.
1. In the **Site** field, select **1**.
1. In the **Warehouse** field, select **11**.
1. Select **OK**.
1. On the **Header** tab, on the **Delivery** FastTab, verify that the **Mode of delivery** field is set to **10**, and the **Delivery terms** field is set to **CIF**.
1. On the **Lines** tab, on the **Purchase order lines** FastTab, in the **Item number** field, select **D0003**. Then, in the **Quantity** field, enter **6**.
1. On the **Line details** FastTab, on the **Foreign trade** tab, verify that the **Transaction code** field is set to **11**, the **Transport** field is set to **3**, the **Commodity** field is set to **100 200 30**, and the **Country/region of origin** field is set to **DEU**.
1. On the Action Pane, on the **Purchase** tab, in the **Actions** group, select **Confirm**.
1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
1. On the Action Pane, select **Default from**. In the **Default quantity for lines** field, select **Ordered quantity**. Then select **OK**.
1. On the **Vendor Invoice header** FastTab, in the **Invoice identification** section, in the **Number** field, enter **001**.
1. On the Action Pane, select **Post** to post the invoice.

### Create an Intrastat declaration for arrivals

To create an Intrastat declaration for arrivals, follow these steps:

1. In Dynamics 365 Finance, go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**.
1. On the Action Pane, select **Transfer**.
1. In the **Intrastat (Transfer)** dialog box, set the **Vendor invoice** option to **Yes**.
1. Select **Filter**.
1. In the **Intrastat Filter** dialog box, on the **Range** tab, select the **Vendor invoice journal** line, and verify that the **Field** field is set to **Date**.
1. In the **Criteria** field, select the current date.
1. Select **OK** to close the **Intrastat Filter** dialog box.
1. Select **OK** to transfer the transactions, and review the Intrastat journal.

    :::image type="content" source="../media/intrastat_lva_4.png" alt-text="Screenshot of the line that represents the purchase order on the Intrastat page.":::

1. Review the **General** tab for the purchase order.

    :::image type="content" source="../media/intrastat_lva_5.png" alt-text="Screenshot of purchase order details on the General tab of the Intrastat page.":::

1. On the Action Pane, select **Output** > **Report**.
1. In the **Intrastat Report** dialog box, on the **Parameters** FastTab, in the **Date** section, select the month of the purchase order that you created.
1. In the **Export** **options** section, set the **Generate file** option to **Yes**. Then, in the **File name** field, enter the required name.
1. Set the **Generate report** option to **Yes**. Then, in the **Report file name** field, enter the required name.
1. In the **Direction** field, select **Arrivals**.
1. In the **File format mapping** section, in the **Hours required for completion** field, enter **11**.
1. In the **Minutes required for completion** field, enter **22**.
1. Select **OK**, and review the report in XML format that is generated. The following table shows the values in the example report.

      | Field on the Intrastat declaration         | Value              |
      |--------------------------------------------|--------------------|
      | VAT registration number                    | LV12345678         |
      | Legal address                              | 454 1st Street LVA |
      | Contact address                            | 454 1st Street LVA |
      | Phone                                      | +49 123 456 789    |
      | Fax                                        | 425-555-5013       |
      | Email                                      | <jodi@contoso.com>   |
      | Contact person name                        | Manish Chopra      |
      | Contact person phone                       | 425-555-5068       |
      | Direction                                  | Izvedums-1B        |
      | Reporting year                             | 2021               |
      | Reporting month                            | M10                |
      | Total number of records                    | 1                  |
      | Hours required for completion the report   | 11                 |
      | Minutes required for completion the report | 22                 |
      | Commodity code                             | 10020030           |
      | Invoice value                              | 965                |
      | Net mass                                   | 30                 |
      | Supplementary units                        | 0                  |
      | Partner country                            | DE                 |
      | Country of origin                          | DE                 |
      | Nature of transaction                      | 11                 |
      | Transport mode                             | 3                  |
      | Delivery terms                             | CIF                |
      | Invoice value in euro                      | 965                |

1. Review the generated Excel report.

    :::image type="content" source="../media/intrastat_lva_6.png" alt-text="Screenshot of the Intrastat report on arrivals.":::

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
