---
title: Configure electronic invoice parameters for Paraguay
description: Learn how to configure the information required to generate the electronic invoice XML for Paraguay.
author: Fhernandez0088
ms.topic: how-to
ms.date: 04/17/2025
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Configure electronic invoice parameters for Paraguay

[!include [banner](../../includes/banner.md)]

This article explains how to configure the information that is required to generate the electronic invoice XML for Paraguay.

## Prerequisites

Before you complete the procedures in this article, the following prerequisites must be met:

- Both the country/region-specific Latin American (LATAM) feature for Paraguay and the general LATAM feature must be enabled.
- The company's address must be set to Paraguay.
- You must download the specific report configurations from the Dataverse configuration repository for Paraguay Electronic Invoices. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).
- You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Configuration required for Paraguay electronic invoices

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax application**, and select **New** to create a tax application record that has the code **PYFE** (Paraguayan electronic invoice). Use this tax application record to assign the fiscal codification to each element in Microsoft Dynamics 365 Finance as required.
1. Go to **Organization administration** \> **Organizations** \> **Legal entities**, and follow these steps:

    1. Select the legal entity that you want to work with.
    1. In the **LATAM** section, in the **Concept 1** field, add the activity code. You can change the label for this field in the **Concepts and notes** configuration.
    1. In the **Country identification number** field, enter the company ID number.
    1. Complete the contact information with the telephone number and email address, and set it to **Primary**.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class**, and follow these steps for each record in the list:

    1. Select the record, and then select **Tax application**.
    1. On the **Tax application** page, in the **Tax application id** field, enter the ID that is used for Paraguayan electronic invoicing.
    1. In the **Tax application code** field, enter the code according to the Paraguayan normative.
    1. In the **Legal Description** field, enter the electronic document description.
    1. In the **Additional data** section, enable lists 1 through 9.

        - List 1 is mandatory for all electronic documents.
        - List 2 is mandatory for all electronic documents except packing slips.
        - List 3 is optional for all electronic documents.
        - List 4 is mandatory for all electronic documents.
        - List 5 is mandatory for electronic invoices.
        - List 6 is mandatory for electronic credit and debit notes.
        - List 7 is mandatory for electronic packing slips.
        - List 8 is mandatory for electronic packing slips.
        - List 9 is mandatory for all electronic documents except packing slips.

    1. Go to **Document class sales point**, and then, for printing concept 1, enter the street name that the electronic document is issued from. For printing concept 2, enter the street number.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Sales point prefix**, and follow these steps for each record in the list:

    1. Select the record, and then select **Tax application**.
    1. On the **Tax application** page, in the **Tax application id** field, enter the ID that is used for Paraguayan electronic invoicing.
    1. In the **Tax application code** field, enter the branch/subsidiary code.
    1. In the **Prefix** field, for each sales point prefix, enter the sales point codes that the company uses.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax ID type**, and follow these steps for each record in the list:

    1. Select the record, and then select **Tax application**.
    1. On the **Tax application** page, in the **Tax application id** field, enter the code that is used for Paraguayan electronic invoicing.
    1. In the **Tax application code** field, enter the code for tax IDs according to the Paraguayan normative.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Taxpayer type**. In the records that are used, go to the **Tax application** menu, and then follow these steps:

    1. Create a record that has the tax application code that is used for Paraguayan electronic invoicing.
    1. In the **Tax application code** field, enter the taxpayer code according to the Paraguayan normative.
    1. In the **User defined field 1** field, enter the recipient nature code.

1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**. For each record (State, County, and City) that has an address in Paraguay, go **LATAM** \> **Tax application** to assign the tax application codes for Paraguayan states, counties, and cities (Departamento, Distrito, and Ciudad).
1. Go to **Accounts receivable** \> **Payments setup** \> **Methods of payment**, and follow these steps for each record in the list:

    1. Select the record, and then select **Tax application**.
    1. On the **Tax application** page, in the **Tax code** field, enter the code according to the Paraguayan normative.
    1. In the **General** section, configure the **Service level** field with the payment processing method code according to the Paraguayan normative.

1. Go to **Accounts receivable** \> **Payments setup** \> **Terms of payment**, and follow these steps for each record in the list:

    1. Select the record, and then select **Tax application**.
    1. On the **Tax application** page, in the **Tax code** field, enter the code according to the Paraguayan normative.

1. Go to **Product information management** \> **Products** \> **Released products**, and follow these steps for each record in the list:

    1. Select the record, and then select **Tax application**.
    1. On the **Tax application** page, in the **Tax code** field, enter the code according to the Paraguayan normative.

1. Go to **Organization administration** \> **Setup** \> **Units** \> **Units**, and follow these steps for each record in the list:

    1. Select the record, and then select **Tax application**.
    1. On the **Tax application** page, in the **Tax code** field, enter the code according to the Paraguayan normative.

1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax codes**, and follow these steps for each record in the list:

    1. Select the record, and then select **Tax application**.
    1. On the **Tax application** page, in the **Tax application id** field, select the code that is used for Paraguayan electronic invoicing.
    1. In the **Income tax code** field, enter the code that identifies the tax according to the Paraguayan normative (fiscal tax method).
    1. In the **User defined field 1** field, enter the tax description according to the Paraguayan normative.

1. Go to **General ledger** \> **Currencies** \> **Currencies**, and follow these steps for each record in the list:

    1. Select the record, and then select **Tax application**.
    1. On the **Tax application** page, in the **Tax code** field, enter the code according to the Paraguayan normative.

1. Go to **Sales and marketing** \> **Setup** \> **Distribution** \> **Modes of delivery**, and follow these steps:

    1. Select the record, and then go to **LATAM** \> **Tax application**.
    1. On the **Tax application** page, enter a new record.
    1. In the **Tax application Id** field, select the code that is used for Paraguayan electronic invoices.
    1. In the **Tax application code** field, enter the code according to the Paraguayan normative for types of transport.

1. Go to **Transportation management** \> **Setup** \> **Carriers** \> **Transportation methods**, and configure the codes and descriptions for transportation modalities.
1. Go to **Inventory management** \> **Setup** \> **Shipping carrier** \> **Shipping carriers**, and follow these steps:

    1. Configure the **Mode of delivery** field with the type of vehicle for transportation.
    1. Configure the **Carrier service** field with the vehicle brand for transportation.
    1. Configure the **Transportation method** field with the vehicle type for transportation.
    1. Configure the **External code** field with the vehicle identification number for transportation.
    1. In the **LATAM** section, complete the fields with the fiscal information according to the Paraguayan normative.

When you issue an electronic document that has an associated document, you must select **References** on the posting page and add the associated document. Complete the reason code and the reason description for the associated document.

Before you can use the **References** button on an electronic document, you must follow these steps:

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Electronic documents references**, and select the tax application that was created for Paraguayan electronic invoices.
1. In the document class that is used in the transaction, set the **Use reference document** option to **Yes**.

After you complete these steps, you can issue electronic invoices from free text invoices, sales orders, and projects.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
