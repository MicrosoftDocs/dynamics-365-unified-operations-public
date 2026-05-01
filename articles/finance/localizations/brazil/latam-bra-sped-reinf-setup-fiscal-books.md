---
title: Set up fiscal books
description: Learn how to set up SPED-Reinf events by using Fiscal books in Microsoft Dynamics 365 Finance for Brazil, including an overview on setting up service types.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/05/2026
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2016-11-30
---

# Set up fiscal books

This article explains how to set up the **Fiscal books** module to generate and issue events to the tax authorities. 

## Set up service types

The service type table represents table 06. The tax authorities use this table to classify the services that are provided, based on the assignment of labor. You can find a detailed list of available values on the public digital bookkeeping system (SPED) website.

1. Go to **Fiscal books** > **Setup** > **SPED Reinf** > **Service types**.
1. Select **New**.
1. Enter a classification code that the tax authorities established, and then enter a description.

    :::image type="content" source="../media/bra-service-type-setup21.png" alt-text="Screenshot of the Service types page.":::

1. After you create the list of service types, assign the service types to service codes. Go to **Inventory management** > **Setup** > **Fiscal information** > **Service code**, and then, for each service, assign the related service type.

## Set up the income classification

After you create the list of service types, assign them to service codes. Include the yield income code that the tax authority provides in the SPED REINF manual.

1. Go to **Inventory management** > **Setup** > **Fiscal information** > **Service code**.
1. For each service, assign the related service type and income code.
 
:::image type="content" source="../media/bra-income-classification-setup21.png" alt-text="Screenshot of the Income classification setup on the Service code page.":::

## Set up tax classification codes

1. Go to **Fiscal books** > **Setup** > **SPED Reinf** > **Tax classification codes**.
1. Enter the available classification types.

:::image type="content" source="../media/bra-tax-classification-codes21.png" alt-text="Screenshot of the Tax classification codes page.":::

Assign this information to the fiscal organization. You can find it on the **General** FastTab of the **Fiscal organization** page (**Fiscal books** > **Setup** > **Fiscal organization**).

:::image type="content" source="../media/bra-fiscal-organization-setup21.png" alt-text="Screenshot of the Fiscal organization page.":::

## Set up codes explanation suspension

1. Go to **Fiscal books** > **Setup** > **SPED Reinf** > **Codes explanation suspension**.
1. Set up the codes that are used in event R-1070 when suspension of withholding applies. Assign these codes on the **Administrative and judicial process** page (**Fiscal books** > **Periodic** > **SPED Reinf** > **Administrative and judicial process**).

:::image type="content" source="../media/bra-codes-explanation-suspension21.png" alt-text="Screenshot of the Codes explanation suspension page.":::

## Set up acquisition type determination

Use this setup to determine the agriculture acquisition type of incoming fiscal documents that you report in the **indAquis** tag for event R-2055. 

1. Go to **Fiscal books** > **Setup** > **SPED Reinf** > **Acquisition of rural production**.
1. Define the classification of fiscal documents, based on the following criteria:

    - **Vendor account:** All, group, or table
    - **CFOP:** All, group, or table
    - **Fiscal classification**

## Set up GILRAT and SENAR taxes

**GILRAT:** The tax contribution for the degree of incidence of labor disability resulting from occupational environmental risks.

**SENAR:** The tax contribution related to rural production.

1. Go to **Fiscal books** > **Setup** > **SPED Reinf** > **GILRAT tax codes** or **SENAR tax codes**.
1. Identify the sales tax codes that represent GILRAT and SENAR taxes. In the definition of the sales tax codes, set the tax type to **Other**. Use the amount of these taxes in the **vlrRatDescPR** and **vlrSenarDesc** tags for event R-2055.

## Set up SPED REINF and Fiscal books parameters

1. Go to **Fiscal books** > **Tax statements parameters** > **SPED REINF** > **SPED REINF parameters**.
1. On the **General** tab, select the SPED REINF version.
1. Select the environment type and the status of the fiscal organization.

    :::image type="content" source="../media/bra-sped-parameters21.png" alt-text="Screenshot of parameters set on the General tab of the SPED Reinf parameters page.":::

1. Go to **Fiscal books** > **Setup** > **Fiscal books parameters**.
1. On the **Number sequences** tab, set up the number sequence for events.

    :::image type="content" source="../media/bra-number-sequence21.png" alt-text="Screenshot of number sequence set up on the Number sequences tab of the Fiscal books parameters page.":::

> [!NOTE] 
> If you didn't initialize the number sequences during the setup checklist for KB installation, you can generate them by using a wizard. To open the wizard, go to **Organization administration** > **Number sequences** > **Number sequences**, and select **Generate**. Then configure the related number sequence:
>
> - **Area:** Fiscal books
> - **Reference:** SPED-REINF event ID

## Vendor setup – Events R-2055, R-4010, R-4020, and R-4040

1. Go to **Accounts payable** > **Vendors** > **All vendors**, and select a vendor.
1. On the **Fiscal information** tab, set the **REINF taxation over payroll** attribute. This new attribute determines the type of taxation, because the system needs this information for the **indOpcCP** tag in event R-2055.

## Event R-4010 Person Vendor setup

1. Go to **Accounts payable** > **Vendors** > **All vendors**.
1. In the **Type** field, select **Person**.

:::image type="content" source="../media/bra-new_vendor21.png" alt-text="Screenshot of the New Person Vendor.":::

## Event R-4020 Legal Entity Vendor setup

1. Go to **Accounts payable** > **Vendors** > **All vendors**.
1. In the **Type** field, select **Organization**.

:::image type="content" source="../media/bra-new_org21.png" alt-text="Screenshot of the New Organization Vendor.":::

## Event R-4040 Unidentified Beneficiary Vendor setup

1. Go to **Accounts payable** > **Vendors** > **All vendors**.
1. In the **Type** field, select **Organization** or **Person**.
1. Set the **Unidentified beneficiary** option to **Yes**.

:::image type="content" source="../media/bra-beneficiary21.png" alt-text="Screenshot of the New Unidentified Beneficiary Vendor.":::

## Event R-4080 Withholding tax on receipt (auto-withholding) Customer setup

In the customer registration, fill in the **Withholding tax** field with the provided information. After you configure this information, issue new invoices and generate new events.

1. Go to **Accounts receivable** > **Customers** > **All customers**, and select the customer.
1. On the **Fiscal information** tab, select **Withholding tax** > **Customer contribution type**, and then select one of the following options:

    - **Federal government foundation or agency**
    - **Federal government administration**
    - **Legal entity**
    - **Cooperative**
    - **Machine or vehicle manufacturer**
    - **OTHER** – This option isn't considered in the event.

1. In the **Withholding tax** field, select a value.

:::image type="content" source="../media/bra-withholding-tax21.png" alt-text="Screenshot of the Withholding tax setup.":::

## Vendor setup

- Go to **Accounts payable** > **Vendors** > **All vendors**.
- Select a vendor.
- On the **Fiscal information** tab, set up **Reinf taxation over payroll**. This new attribute determines the type of taxation, because this information is required in the **indOpcCP** tag for event R-2055.

## Set up Fiscal books parameters

1. Go to **Fiscal books** > **Tax statements parameters** > **SPED Reinf** > **SPED Reinf parameters**.
1. On the **General** tab, select **SPED Reinf version**.
1. Select the environment type and the status of the fiscal organization.
1. Go to **Fiscal books** > **Setup** > **Fiscal books parameters**.
1. On the **Number sequences** tab, set up the number sequence for events R-2010, R-2020, and R-2055.

:::image type="content" source="../media/bra-sped-fiscal-books-parameters.png" alt-text="Screenshot of the Number sequences tab on the Fiscal books parameters page.":::

> [!NOTE]
> If the setup checklist for KB installation didn't initialize the number sequences, use the wizard to generate them. To open the wizard, go to **Organization administration** > **Number sequences** > **Number sequences**, and select **Generate**. You can then configure the related number sequence:
>
> - **Area:** Fiscal books
> - **Reference:** SPED-Reinf event ID

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]