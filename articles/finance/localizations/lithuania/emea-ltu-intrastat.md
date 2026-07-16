---
title: Lithuanian Intrastat
description: Learn how to set up the Lithuanian Intrastat report in Microsoft Dynamics 365 Finance.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/25/2026
ms.reviewer: johnmichalak
ms.search.region: Global
---

# Lithuanian Intrastat

[!include [banner](../../includes/banner.md)]

This article explains how to set up and generate the Lithuanian Intrastat report in Microsoft Dynamics 365 Finance.

Use the **Intrastat** page to generate and report information about trade among European Union (EU) countries and regions. The Lithuanian Intrastat declaration contains information about the trade of goods for reporting. It's generated as an XML file in the IDAIS (Data on the Republic of Lithuania's trade flows with EU countries collection and processing system, *Duomenų apie Lietuvos Respublikos prekybos srautus su Europos Sąjungos šalimis narėmis surinkimo ir apdorojimo sistema*) format that is defined by the `INTRASTATReportSubmission.xsd` schema.

## Overview 

The Lithuanian Intrastat declaration is submitted as an XML message that has three logical parts: information about the **submitter** (a value-added tax [VAT] payer or a broker), optional **report preparation** data, and the **Intrastat report** itself with its lines. The following sections describe the fields in each part.

### Submitter and declaration header

| Field name | Description |
| --- | --- |
| Submitter type | The type of party that submits the declaration. The value is **VAT_PAYER** when the VAT payer submits the declaration directly, or **BROKER** when an intermediary (a broker) submits it. The value is derived automatically: if an agent is set up on the **Agent** tab of the **Foreign trade parameters** page, the declaration is submitted as **BROKER**. Otherwise, it's submitted as **VAT_PAYER**. |
| VAT payer – Title | The name of the legal entity, or the first name and last name of the individual, that is the VAT payer. |
| VAT payer – VAT identifier | The VAT code (VAT registration number) of the company that provides the statistical declaration. If the company's VAT number isn't available, the tax registration number is used instead. |
| VAT payer – Address | The VAT payer's address. The street, building, city or village, and municipality are reported together with the postal (ZIP) code. |
| VAT payer – Contact | The VAT payer's email address and phone number. |
| Broker – Title | The name of the broker's legal entity. This information is reported only when the submitter type is **BROKER**. |
| Broker – Legal entity identifier (JAR) | The legal entity registration code (*juridinio asmens kodas*) of the broker. This code is the company-register number (for example, **302345678**), not the broker's VAT code (for example, **LT302345678**). This information is reported only when the submitter type is **BROKER**. |
| Broker – Contact | The broker's email address and phone number. This information is reported only when the submitter type is **BROKER**. |
| Reporting year | The year that the declaration applies to. |
| Reporting month | The month that the declaration applies to. The value is a number from 1 through 12. |
| Trade direction | The direction of trade. For arrivals, **IMPORT** is reported. For dispatches, **EXPORT** is reported. |
| Zero trade indicator | A Boolean value that indicates that no intracommunity trade occurred in the reference period. When this value is **true**, a null (nil) declaration is submitted, and no report lines are included. |

### Report preparation

The report preparation block is optional. It provides additional information about who prepared the declaration and how much time the preparation took.

| Field name | Description |
| --- | --- |
| VAT payer document registration | The registration date and registration number that the VAT payer assigns to the declaration. The registration number is the number that the VAT payer gives to the report (for example, **INTRA-2026-06**), which you enter in the **Declaration identifier** field when you generate the report. It isn't the VAT number. The registration date is set to the current date. This block is reported only when you enter a declaration identifier. |
| Responsible person – Name | The first name and last name of the responsible person who prepared the declaration. This person is the head of the company or an authorized representative. |
| Responsible person – Contact | The email address and phone number of the responsible person. |
| Preparation time (hours) | The number of hours that it took to prepare the declaration. The value is from 0 through 99. According to the authority requirements, this information is mandatory once a year, in September. |
| Preparation time (minutes) | The number of minutes that it took to prepare the declaration. The value is from 0 through 59. |

### Report lines

Each report line represents a commodity item. The system excludes lines when you set the **Zero trade indicator** field to **true**.

| Field name | Description |
| --- | --- |
| Report item number | The sequential number of the line in the declaration. |
| Combined Nomenclature code | The eight-character commodity code according to the Combined Nomenclature (CN) classification. Set this code on the product page. |
| Partner identifier | The trading partner's VAT identifier in the EU member state. Report this field only for dispatches (EXPORT). Don't report it for arrivals (IMPORT). If the partner isn't VAT-registered, or the VAT number is unknown, report the value **QV999999999999**. |
| Country of dispatch or destination code | The two-character International Organization for Standardization (ISO) code of the country or region of the counterparty. For arrivals, it's the country of consignment. For dispatches, it's the country of destination. |
| Country of origin code | The two-character ISO code of the country or region where the goods were produced. |
| Region code | The one-character county code for the company's region. This code is required for dispatches (EXPORT) only when the country of origin of the goods is Lithuania. Otherwise, it's left empty. |
| Nature of transaction code | The transaction code. |
| Delivery terms code | The code for the terms of delivery of goods. |
| Mode of transport code | The code for the mode of transport. |
| Net mass | The net mass of the goods in kilograms. The value is a decimal number that has up to three decimal places (for example, **125.500**). |
| Quantity in supplementary unit of measure | For some commodities, you must report the quantity in a supplementary unit. The value is a decimal number that has up to three decimal places. |
| Supplementary unit of measure code | The code of the supplementary unit of measure that the quantity is expressed in. |
| Invoiced amount | The invoice value. You can view the invoice value in the **Invoice amount** field in the Intrastat journal. |
| Statistical value | The statistical value. You can view the statistical value in the **Statistical value** field in the Intrastat journal. |

## System preparation

### Set up ER configurations for Intrastat

Import the latest version of the following Electronic reporting (ER) configurations from Dataverse:

- Intrastat model
- Intrastat report
- INSTAT XML (LT)

> [!NOTE]
> The **INSTAT XML (LT)** format mapping generates files that conform to the IDAIS `INTRASTATReportSubmission.xsd` schema. Make sure that you import the latest version of the configurations before you generate declarations.

For more information, see [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

### Set up region code

The Intrastat declaration requires that you report a region code.

To set up the region code, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** > **Global address book** > **Addresses** > **Address setup**.
1. On the **State/province** tab, select **New**.
1. In the **Country/region** field, select **LTU**.
1. In the **State** field, enter the name of the state.
1. In the **Intrastat code** field, enter the code according to the authority requirements.

### Set up an address for a legal entity

To set up an address for a legal entity, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** > **Organizations** > **Legal entities**.
1. In the grid, select your company.
1. On the **Addresses** FastTab, select **Edit**.
1. In the **Edit address** dialog box, in the **Country/region** field, select **LTU**.
1. In the **ZIP/postal code** field, select your company's ZIP/postal code.
1. In the **Street** field, enter your address.
1. In the **City** field, select your city.
1. In the **State** field, select your company's state.

### Set up contact information

Set up your company's telephone number, email address, URL, and fax number.

To set up contact information, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** > **Organizations** > **Legal entities**.
1. In the grid, select your company.
1. On the **Contact information** FastTab, select **Add** to create a contact.
1. In the **Type** field, select the type of communication.
1. In the **Contact number/address** field, enter your company's contact information.
1. Select the **Primary** option to print this contact information on the report.

> [!NOTE]
> The IDAIS XML format reports the VAT payer's email address and phone number. Make sure that the **Email address** and **Phone** contact types are set up and marked as **Primary** for your legal entity.

### Set up the broker (intermediary)

If a broker (an intermediary, *tarpininkas*) submits the Intrastat declaration on behalf of your company, set up the broker as an agent. When you set up an agent, the submitter type in the declaration automatically sets to **BROKER**, and the **Broker** block is included in the XML message. When you don't set up an agent, the submitter type is **VAT_PAYER**, and the **Broker** block isn't included.

To set up the broker, follow these steps:

1. In Dynamics 365 Finance, go to **Tax** > **Setup** > **Foreign trade** > **Foreign trade parameters**.
1. On the **Agent** tab, enter the following information:

    - In the **Name** field, enter the name of the broker's legal entity. This value is reported in the **Broker – Title** field.
    - In the **Tax exempt number** field, enter the broker's VAT number (for example, **LT302345678**). When you fill in this field, the submitter type is set to **BROKER**.
    - In the **Branch/Subsidiary** field, enter the broker's legal entity registration code (JAR). This code is the nine-digit company-register number (for example, **302345678**), not the VAT number. This value is reported in the **Broker – Legal entity identifier (JAR)** field.
    - Enter the broker's contact information (for example, the phone number). This value is reported in the **Broker – Contact** field.

> [!NOTE]
> The **Broker – Legal entity identifier (JAR)** field reports the company-register code from the **Branch/Subsidiary** field (for example, **302345678**), without the country prefix. The country-prefixed VAT number in the **Tax exempt number** field is used only to determine that a broker submits the declaration.

### Set up the responsible person

The responsible person is the person who prepares and submits the declaration. The responsible person's name, email address, and phone number are reported in the **Responsible person** fields of the **Report preparation** block.

To set up the responsible person, follow these steps:

1. In Dynamics 365 Finance, go to **Tax** > **Setup** > **Foreign trade** > **Foreign trade parameters**.
1. On the **Contact** tab, enter the name, telephone number, and email address of the person who is submitting the declaration.

### Set up VAT IDs

#### Set up the VAT ID for your company

To set up the VAT ID for your company, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** > **Organizations** > **Legal entities**.
1. In the grid, select your company.
1. On the **Tax registration** FastTab, in the **Tax registration number** field, enter the VAT ID for your company.

#### Set up the VAT number of a trading partner

Report the trading partner's VAT identifier in the **Partner identifier** field of the report line for dispatches (EXPORT).

##### Create a registration type for the company code

Create VAT ID registration types for all the countries or regions that your company does business with.

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
1. Repeat steps 2 and 3 for the other registration types that you created for the countries or regions that your company does business with.

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

### Set up product parameters for the Intrastat declaration

To set up product parameters for the Intrastat declaration, follow these steps:

1. In Dynamics 365 Finance, go to **Product information management** > **Products** > **Released products**.
1. In the grid, select a product.
1. On the **Foreign trade** FastTab, in the **Intrastat** section, in the **Commodity** field, select the commodity code. The commodity code is reported in the **Combined Nomenclature code** field in the Intrastat declaration.
1. In the **Statistics procedure** field, select the statistical sign if it's required. The values that you can select depend on the commodity code that you selected.
1. In the **Origin** section, in the **Country/region** field, select the product's country or region of origin.
1. On the **Manage inventory** FastTab, in the **Net weight** field, enter the product's weight in kilograms.

### Set up the transport method and delivery terms

To set up the transport method and delivery terms, follow these steps:

1. Set up transport codes.
    1. In Dynamics 365 Finance, go to **Tax** > **Setup** > **Foreign trade** > **Transport method**.
    1. On the Action Pane, select **New**.
    1. In the **Transport** field, enter a unique code. Lithuanian companies use one-digit transport codes.
1. Set up mode of delivery Intrastat codes.
    1. Go to **Procurement and sourcing** > **Setup** > **Distribution** > **Terms of delivery**.
    1. In the grid, select a set of delivery terms.
    1. On the **General** FastTab, in the **Intrastat code** field, enter the unique code.

### Set up the Intrastat authority

- In Dynamics 365 Finance, go to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax authorities**, and enter the following information for the Intrastat authority:

    - Authority identification
    - Address
    - Contact information

    For more information, see [Set up sales tax authorities](../../general-ledger/tasks/set-up-sales-tax-authorities.md).

### Set up foreign trade parameters

To set up foreign trade parameters, follow these steps:

1. In Dynamics 365 Finance, go to **Tax** > **Setup** > **Foreign trade parameters**.
1. On the **Intrastat** tab, on the **Electronic reporting** FastTab, in the **File format mapping** field, select **INSTAT XML (LT)**.
1. In the **Report format mapping** field, select **Intrastat report**.
1. On the **Commodity code hierarchy** FastTab, in the **Category hierarchy** field, select **Intrastat**.
1. In the **Transaction code** field, select the transaction code for property transfers.
1. In the **Credit note** field, select the transaction code for the return of goods.
1. In the **Authority** field, select the authority that receives the Intrastat declaration.
1. On the **Contact** tab, enter the name, telephone number, and email address of the person who is submitting the declaration. This information is reported as the responsible person in the **Report preparation** block.
1. If a broker submits the declaration on behalf of your company, set up the broker on the **Agent** tab, as described in the [Set up the broker (intermediary)](#set-up-the-broker-intermediary) section.
1. On the **Country/region properties** tab, in the **Country/region** field, list all the countries or regions that your company does business with. For each country that is part of the EU, select **EU** in the **Country/region type** field, so that the country appears on your Intrastat report. For Lithuania, select **Domestic** in the **Country/region type** field.

### Set up compression of Intrastat

In Dynamics 365 Finance, go to **Tax** > **Setup** > **Foreign trade** > **Compression of Intrastat**, and select the fields to compare when summarizing Intrastat information. For Lithuanian Intrastat, select the following fields:

- Commodity
- Transaction code
- Country/region of origin
- State
- Country/region of sender
- State of sender
- Correction
- Country/region
- Tax exempt number
- Direction
- Delivery terms
- Transport

## Intrastat transfer

On the **Intrastat** page, on the Action Pane, select **Transfer** to automatically transfer the information about intracommunity trade from your sales orders, free-text invoices, purchase orders, vendor invoices, vendor product receipts, project invoices, and transfer orders. The system transfers only documents that have an EU country as the country or region of destination or consignment.

You can also manually enter transactions by selecting **New** on the Action Pane.

### Generate an Intrastat report

To generate an Intrastat report, follow these steps:

1. In Dynamics 365 Finance, go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**.
1. On the Action Pane, select **Output** > **Report**.
1. In the **Intrastat Report** dialog box, enter the start date for the report.
1. Set the **Generate file** option to **Yes** to generate an .xml file in the IDAIS format.
1. Set the **Generate report** option to **Yes** to generate an .xlsx file, and then enter a name for the file.
1. In the **Direction** field, select **Arrivals** if the report is about intracommunity arrivals (IMPORT) or **Dispatches** if the report is about intracommunity dispatches (EXPORT).
1. If no intracommunity trade occurred in the reference period, set the option for a null (zero) declaration. The generated XML message has the zero trade indicator set to **true** and doesn't include report lines.
1. Select **OK**, and review the generated reports.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

