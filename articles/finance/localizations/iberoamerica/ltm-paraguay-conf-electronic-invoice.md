---
title: Configure electronic invoice parameters for Paraguay
description: Learn how to configure the information required to generate the electronic invoice XML for Paraguay, including an outline on the required configuration.
author: Fhernandez0088
ms.topic: how-to
ms.date: 04/17/2025
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Configure electronic invoice parameters for Paraguay

[!include [banner](../../includes/banner.md)]

This article explains how to configure the information that's required to generate the electronic invoice XML for Paraguay.

## Prerequisites

Before you complete the procedures in this article, the following prerequisites must be met:

- The country/region-specific Latin American (LATAM) feature for Paraguay and the general LATAM feature must be enabled.
- The company address must be set to Paraguay.
-You must download the specific report configurations from the Dataverse configuration repository for Paraguay Electronic Invoices. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).
- You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Configuration required for Paraguay electronic invoices

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax application**, and select **New** to create a tax application record that has the code **PYFE** (Paraguayan electronic invoice). Use this tax application record to assign the fiscal codification to each element in Microsoft Dynamics 365 Finance as required.
1. Go to **Organization administration** \> **Organizations** \> **Legal entities**, and follow these steps.

    1. Select the legal entity that you want to work with.
    1. In the **LATAM** section, in the **Concept 1** field, add the activity code. The field label **Concept 1** can be changed in the **Concepts and notes** configuration.
    1. In the **Country identification number** field, enter the company ID number.
    1. Complete the contact information with the telephone number and e-mail and set it to **Primary**.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class**, and follow these steps for each record in the list:

    1. Select the record, and then select **Tax application**.
    1. On the **Tax application** page, in the **Tax application id** field, enter the ID that's used for Paraguayan electronic invoicing.
    1. In the **Tax application code** field, enter the code according to the Paraguayan normative.
    1. In **Legal Description** field enter the electronic document description.
    1. In the **Additional data** section enable **Lists** 1 to 9.

        - List 1 mandatory for all electronic documents.
        - List 2 mandatory for all electronic documents except packing slips.
        - List 3 optional for all electronic documents.
        - List 4 mandatory for all electronic documents.
        - List 5 mandatory for electronic invoices.
        - List 6 mandatory for electronic credit and debit notes.
        - List 7 mandatory for electronic packing slips.
        - List 8 mandatory for electronic packing slips.
        - List 9 mandatory for all electronic documents except packing slips.
        
    1. Go to **Document class sales point** and in printing concept 1 enter the street name from where the electronic document is issued, and in printing concept 2 enter the street number.
	
1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Sales point prefix**, and follow these steps for each record in the list.

    1. Select the record, and then select **Tax application**.
    1. On the **Tax application** page, in the **Tax application id** field, enter the ID that's used for Paraguayan electronic invoicing.
    1. In the **Tax application code** field, enter the branch/subsidiary code.
    1. In the **Prefix** field for each **Sales point prefix** enter the sales point codes used by the company.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax ID type**, and follow these steps for each record in the list.

    1. Select the record, and then select **Tax application**.
    1. On the **Tax application** page, in the **Tax application id** field, enter the code that's used for Paraguayan electronic invoicing.
    1. In the **Tax application code** field, enter the code for tax IDs according to the Paraguayan normative.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Taxpayer type** in the records used go to the **Tax application** menu and:

    1. Create a record with the tax application code used for Paraguay electronic invoicing.
    1. In the **Tax application code** field enter the taxpayer code according to the Paraguayan normative.
    1. In the **User defined field 1** enter the recipient nature code.

1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**. For each record (State, County and City) that has an address in Paraguay, go **LATAM** \> **Tax application** to assign the tax application codes for Paraguayan states, counties, and cities (Departamento, Distrito, Ciudad).
1. Go to **Accounts receivable** \> **Payments setup** \> **Methods of payment**, and follow these steps for each record in the list.

    1. Select the record, and then select **Tax application**.
    1. On the **Tax application** page, in the **Tax code** field, enter the code according to the Paraguayan normative.
    1. In the **General** section, configure the **Service level** with the payment processing method code according to the Paraguayan normative.

1. Go to **Accounts receivable** \> **Payments setup** \> **Terms of payment**, and follow these steps for each record in the list.

    1. Select the record, and then select **Tax application**.
    1. On the **Tax application** page, in the **Tax code** field, enter the code according to the Paraguayan normative.

1. Go to **Product information management** \> **Products** \> **Released products**, and follow these steps for each record in the list.

    1. Select the record, and then select **Tax application**.
    1. On the **Tax application** page, in the **Tax code** field, enter the code according to the Paraguayan normative.

1. Go to **Organization administration** \> **Setup** \> **Units** \> **Units**, and follow these steps for each record in the list.

    1. Select the record, and then select **Tax application**.
    1. On the **Tax application** page, in the **Tax code** field, enter the code according to the Paraguayan normative.

1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax codes**, and follow these steps for each record in the list.

    1. Select the record, and then select **Tax application**.
    1. On the **Tax application** page, in the **Tax application id** field, select the code that's used for Paraguayan electronic invoicing.
    1. In the **Income tax code** field, enter the code that identifies the tax according to the Paraguayan normative (fiscal tax method).
    1. In the **User defined field 1** enter the tax description according to the Paraguayan normative.
 

1. Go to **General ledger** \> **Currencies** \> **Currencies**, and follow these steps for each record in the list.

    1. Select the record, and then select **Tax application**.
    1. On the **Tax application** page, in the **Tax code** field, enter the code according to the Paraguayan normative.

1. Go to **Sales and marketing** \> **Setup** \> **Distribution** \> **Modes of delivery**, and:

    1. Select the record and go to **LATAM** \>**Tax application**.
    1. On the **Tax application** page, enter a new record.
    1. In the **Tax application Id** field, select the code used for Paraguay electronic invoice.
    1. In the **Tax application code** field enter the code according to the Paraguayan normative for type of transports.

1. Go to **Transportation management** \> **Setup** \> **Carriers** \> **Transportation methods** configure the codes and descriptions for transportation modalities.
1. Go to **Inventory management** \> **Setup** \> ** Shipping carrier** \> ** Shipping carriers**, and:

    1. Configure the **Mode of delivery** with the type of vehicle for transportation.
    1. Configure the **Carrier service** with the vehicle brand for transportation.
    1. Configure the **Transportation method** with the vehicle type for transportation.
    1. Configure the **External code** with the vehicle identification number for transportation.
    1. In the **LATAM** section complete the fields with the fiscal information according to the Paraguayan normative.

When issuing an electronic document with an associated document you have to select the **References** button in the posting form and add the associated document. 

Complete the reason code and the reason description for the associated documents.
To use the **References** on an electronic document you have to previously:

1.	Go to **Organization administration** \> **Setup** \> **LATAM** \> **Electronic documents references** and select the tax application created for Paraguay electronic invoices.
1.	In the document class used in the transaction set the **Use reference document** slider to yes.

After you complete these steps, you can issue electronic invoices from free text invoices, sales orders, and projects.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
