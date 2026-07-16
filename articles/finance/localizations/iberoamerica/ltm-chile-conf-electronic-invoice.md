---
title: Configure electronic invoice parameters for Chile
description: Learn how to configure the information required to generate the electronic invoice XML for Chile, including prerequisites and a process of electronic invoices.
author: SandraYamamoto0602
ms.author: v-sandraya
ms.topic: how-to
ms.date: 06/09/2026
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Configure electronic invoice parameters for Chile

[!include [banner](../../includes/banner.md)]

This article explains how to configure the information that's required to generate the electronic invoice XML for Chile.

## Prerequisites

Before you complete the procedure in this article, ensure that the following prerequisites are met:

- Enable the country/region-specific Latin American (LATAM) feature for Chile and the general LATAM feature.
- Set the company address to Chile.

## Configuration required for Chilean electronic invoices

The following steps explain the information that the XML tags require, in the specific order that they require it.

1. Go to **Organization administration** > **Setup** > **LATAM** > **Tax application**, and select **New** to create tax application records that use the code **CHFE** (Chilean electronic invoice). Use this tax application record to assign the fiscal codification to each element in Microsoft Dynamics 365 Finance as required.
1. Go to **Organization administration** > **Organizations** > **Legal entities**, and follow these steps:
 
    1. In the **LATAM** section, in the **Country identification number** field, enter the complete Rol Único Tributario (RUT) number.
    1. In the **Concept 1** field, enter **Giro emisor** as the business activity. You can change the title of this field in the **Concept and notes** configuration on the **LATAM parameters** page.
    1. In the **Contact information** section, add a telephone number and an email address, and set them as **Primary**.
    1. In the **Statutory reporting** section, in the **Branch/Subsidiary** field, enter the code for the business activity according to the Chilean normative.

1. Go to **Organization administration** > **Setup** > **LATAM** > **Document class**, and follow these steps:

    1. On the Action Pane, select **Tax application**.
    1. Assign a tax code to each document class that you use, according to the updated Chilean normative.
    1. Add the letter **R** to the credit note and debit note to require the reference documents when those types of transactions are posted.

1. Go to **Accounts receivable** > **Payments setup** > **Terms of payment**, and follow these steps:

    1. Create the terms of payments for cash payments, credits, and donations.
    1. Assign a tax code to the terms of payment according to the Chilean normative.

1. Go to **Organization administration** > **Setup** > **LATAM** > **Document class sales point**, and assign a document number sequence to the document class sales point configuration. This number sequence is used for the document number for the fiscal document.
1. In the **Document class sales point** form, complete the **Printing concept** 1, 2, and 3 with the street and street number, province, and commune respectively.
1. Go to **Organization administration** > **Setup** > **LATAM** > **Sales point prefix**, and set the tax application code to the sales points that you use with the codification that the fiscal authority assigned to it.
1. Go to **Accounts receivable** > **Customers** > **All customers**, and follow these steps:

    1. Select and open a customer record.
    1. In the **LATAM** section, in the **Country identification number** field, select the customer's RUT number.

1. Go to **Accounts receivable** > **Customers** > **All customers**, and follow these steps:

    1. On the Action Pane, in the **General** group, select **Business classification**.
    1. Create a record to add the business classification that's declared in the fiscal records to each customer record.

1. Go to **Organization administration** > **Setup** > **LATAM** > **Document class**, and configure the required information for fiscal documents.

    1. For remission document classes, select each class that you created. Then, in the **General** section, set the **Concept Label 1** field to **RUT Chofer**, set the **Concept Label 2** field to **RUT Transportista**, and set the **Concept Label 3** field to **Nombre Chofer**.
    1. In the **Additional data** section, configure the fields for each remission document class to match the information requirements for electronic invoicing. For remission document classes, the **Free text 1** field is required and should be for the driver's RUT number. The **Free text 2** field is required and should be for the transporter's RUT. The **Free text 3** field is required and should be for the driver's name. 
    1. In the **Additional data** section, enable lists 1, 3, 4, 5, 6, 7, and 8 as the electronic document requires.

    For more information, see [Document classes for Latin America](ltm-core-document-class.md).

1. Go to **Sales and marketing** > **Setup** > **Distribution** > **Reasons for delivery**, and set the options for selling modes according to the Chilean normative that's established by the customs office. This information is used only for export documents. Add a **Tax application code** for these records.
1. Go to **Sales and marketing** > **Setup** > **Distribution** > **Terms of delivery**, and set the options for selling clauses according to the Chilean normative (FOB, CIF, and so on). Add a **Tax application code** for these records.
1. Go to **Sales and marketing** > **Setup** > **Distribution** > **Modes of delivery**, and set the options for transportation routes according to the Chilean normative (aerial, terrestrial, maritime, and so on). Add a **Tax application code** for these records.
1. Go to **General ledger** > **Currencies** > **Currencies**. For each currency that you use in transactions, set the **Tax application** code with the currency indicator according to the electronic invoice schema (PESO CL, DOLAR USA, EURO, and so on).	
1. Go to **Organization administration** > **Setup** > **LATAM** > **Electronic documents references**. Set the **Tax application id** value that you created for electronic invoicing for Chile (**CHFE**), and set the limit to trigger the global indicator according to the Chilean normative (**20**). These settings trigger the limit for references in one document and make a summary of the references.
1. Go to **Organization administration** > **Setup** > **Units** > **Units**, and configure the tax application code for the units that you use, according to the Chilean customs office normative.
1. Go to **Organization administration** > **Setup** > **LATAM** > **Field master list**, and create the following field lists:
    - **Field list 1:** Add elements that have the type of services included in the document according to the Chilean normative.
    - **Field list 3:** Add elements that have the ports of shipment and their codes according to the Chilean normative.
    - **Field list 4:** Add elements that have the landing ports and their codes according to the Chilean normative.
    - **Field list 5:** Add elements that have the options for transport type indicators and their codes according to the Chilean normative.
    - **Field list 6:** Add elements that have the patents used in transport transactions. To add the trailer license plate, use **User-defined field 1** in the Tax Application. 
    - **Field list 7:** Add elements that have the options for remission types and their codes according to the Chilean normative.
    - **Field list 8:** Add elements that have the options for products transfer types and their codes according to the Chilean normative.
    - **Field list 9:** Add elements that have the options for reference document codes according to the Chilean normative.
    - **Field list 10:** Add elements that have fiscal document type codes according to the Chilean normative.


1. Go to **Inventory management** > **Setup** > **Inventory breakdown** > **Warehouses**, and set the primary address for each warehouse you use.
1. Go to **Organization administration** > **Setup** > **LATAM** > **SSRS Reports / Services references**, and create a record for the Chilean Electronic Invoice.
1. In the **SSRS Reports / Services references** form, enter the **ID** and **Report/Service name**.
1. In the **SSRS Reports / Services references** form, set the **Report/Service type** field to **Service** and the **Sales point type** to **Pre-printed**.
1. In the **SSRS Reports / Services references** form, in the **Parameters** section, create a new record. In the **Name** field, enter **TaxApplicationID**. In the **Value** field, enter the tax application ID for the Chilean electronic invoice.
1. Go to **Organization administration** > **Workspaces** > **Electronic reporting** and configure the format application specific parameters. Set the **Tax type** lookup condition **No** with the tax codes for taxed transactions and the lookup condition **Yes** with the tax codes for untaxed transaction. Set up the **NA** condition with the tax code **Blank** and **Not blank** at the end of the list.

After you complete these steps, you can issue electronic invoices from free text invoices, sales orders, and projects.

## Inventory transfer format for internal product movements

Print the inventory transfer format (**Invent transfer (CL)**) from the Electronic Reporting configuration.

### Prerequisites

1. Download the specific report configurations from the Dataverse configuration repository for Chile Electronic Invoices (**Invent transfer (CL)**). For more information, see [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).
1. Configure the Electronic reporting (ER) parameters. For more information, see [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
1. Enable the general LATAM feature and the specific LATAM feature for Chile.
1. Go to **Organization administration** > **Workspaces** > **Electronic reporting** and configure the format application specific parameters by setting the tax codes for taxed (no) and not taxed (yes) transactions.

## For packing slip and inventory transfer

The following considerations apply when entering this type of transaction:

1. **Departure date**: The system takes the date from the LATAM document.
1. **Departure time**: The system takes the time from the posting time of the LATAM document.
1. **Arrival date**:
 	-  For Sales Orders, in the **Line details section** for each item line, go to the **Delivery tab**, and complete the **Confirmed receipt date** field.
	- For Item Requirements, for each item line go to **Setup** and complete the **Confirmed receipt date** field.
	- For Transfer Orders, for each transfer order line, complete the **Receipt date** field.  

## Print the Inventory transfer format for Chile

To print the Inventory transfer format for Chile, follow these steps:

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
1. Select the format report **Invent transfer (CL)**.
1. Select the latest version and select **Run**.
1. Enter the desired filters, and select **Ok**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
