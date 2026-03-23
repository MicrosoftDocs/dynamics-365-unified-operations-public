---
title: Waybill (Carta de Porte) complement
description: Learn how to set up and submit packing slips and transfer orders that include the Waybill (Carta de Porte) complement with an outline on transportaiton details.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/20/2026
ms.reviewer: johnmichalak
ms.search.region: Mexico
ms.search.validFrom: 2021-08-31
---

# Waybill (Carta de Porte) complement

[!include [banner](../../includes/banner.md)]

This article provides information about how to set up and submit packing slips and transfer orders that include the Waybill (Carta de Porte) complement. As of October 1, 2021, the Waybill (Carta de Porte) complement is mandatory for taxpayers who transport goods and merchandise in the national/regional territory.

To generate the Waybill (Carta de Porte) complement in electronic invoice (CFDI) documents, enter transportation information on the **Transportation details** page. You can open this page from any of the following business documents:

- **A sales order record:** These sales orders include sales orders for the project. Go to **Accounts receivable** > **Orders** > **All sales orders**. On the action pane, select **Pick and Pack**.
- **A transfer order:** Go to **Inventory management** > **Outbound orders** > **Transfer orders**. On the action pane, select **Ship**.
- **A shipment:** Go to **Inventory management** > **Outbound orders** > **Shipments**.
- **Project requirements:** Go to **Project management and accounting** > **Item tasks** > **Project requirements**. On the action pane, select **Manage**.

> [!NOTE]
> You can view transportation information on the **CFDI - Packing Slip Electronic Invoices** and **CFDI - Invent Transfer Electronic Invoices** list pages.

## Transportation details page

This section provides information about the fields that are required on the **Transportation details** page. In the following illustration, the required fields are highlighted.

:::image type="content" source="../media/latam-mx-transportation-details.png" alt-text="Screenshot of the Transportation details page.":::

> [!NOTE]
> As of version 10.0.23 (build 10.0.1037.160), the following functionality is available:
>
> - On the **Loading** FastTab of the **Transportation details** page, enter a value in the **Loading date and time** and **Name** (shipment address) fields. If you leave the **Loading date and time** field blank, the system selects the value from the transaction. If you leave the **Name** (shipment address) field blank, the system selects the value from the warehouse or site address.
> - Select a value in the **Weight unit** field. Before version 10.0.23, the **XAG** weight unit was a fixed value in an XML file. If you leave this field blank, the corresponding attribute in the XML file is filled in with **XAG**.
> - In addition to the data for two drivers, you can fill in transportation actors by selecting **Transportation actors** on the action pane. However, you should first fill in the actors catalog by going to **Organization administration** > **Setup** > **SAT clarification** > **Transportation**.

### General FastTab

The following fields are required:

- **Permission type**
- **Transportation permission ID**
- **Distance**
- **Hours**

### Vehicle FastTab

In the **Vehicle** section, make sure to fill in the following fields:

- **Registration number**
- **Federal motor transport configuration**
- **Model year**

In the **Insurance** section, fill in the following fields:

- **Vendor account**
- **Policy number**

In the **Driver** section, fill in the following fields:

- **Driver**
- **Registration number** or **RFC number**
- **Driver license**
- **Country/region**

In the **Trailer** section, set the following fields if you use a trailer in the transportation of goods:

- **Trailer registration number**
- **Trailer type**

> [!NOTE]
> If you use an additional trailer, set the fields in the **Additional trailer** section. If you use an additional driver, set the fields in the **Additional driver** section. For an additional driver, fill in the following fields in the **Additional driver** section:
>
> - **Driver**
> - **Registration number** or **RFC number**
> - **Driver license**
> - **Country/region**

You can fill in all the fields for a truck, trailer, and driver, except the **Federal motor transport configuration** field, manually or by using information from fixed asset and worker records.

## Posting packing slips and shipping transfer orders that include the Waybill (Carta de Porte) complement

If you select **Enable CFDI packing slip** on the **Packing slip posting** or **Shipment** page, the system automatically selects the **Generate transportation note** parameter. However, you can clear this parameter if you require. If you select **Generate transportation note**, the Waybill (Carta de Porte) complement is included in the XML file.

## Setup

### Catalogs

Set up the Mexican tax authorities (SAT) catalogs to add information to the **Permission type**, **Trailer type**, and **Federal motor transport configuration** fields.

1. Go to **Organization administration** > **Setup** > **EInvoice** > **SAT classification** > **Transportation**.
1. On the **Transportation** page, create the following SAT catalogs:

    - For the **Trailer type** field, use the SAT catalog **c\_SubTipoRem**.
    - For the **Permission type** field, use the SAT catalog **c\_TipoPermiso**.
    - For the **Federal motor transport configuration** field, use the SAT catalog **c\_ConfigAutotransporte**.
    - For the **Customs document type** field, use the SAT catalog **c\_DocumentoAduanero**.
    - For the **Customs regime** field, use the SAT catalog **c\_RegimenAduanero**.
    - For the **Customs material type** field, use the SAT catalog **c\_TipoMateria**.	

### Permission number

1. Go to **Organization administration** > **Organizations** > **Legal entities**.
1. On the **Transportation permissions** FastTab, in the **Transportation permission ID** field, enter the permission number that the Mexican Secretariat for Communications and Transport (SCT) provides.

### Items

1. Go to **Product information management** > **Products** > **All released products**.
1. Select and open the item record that you want to work with.
1. On the **Manage inventory** FastTab, set the **Net weight** and **Tare weight** fields if they're required. The **Gross weight** field is automatically set.

### Sales orders

1. Go to **Accounts receivable** > **Orders** > **All sales orders**.
1. Select an existing sales order that you want to work with, or create a new one.
1. On the **Header** tab, on the **General** FastTab, in the **Electronic invoices** section, in the **Customs regime** field, select a value. The list of available values is already defined in the **Customs regime** catalog. The **Customs regime** field is required when the **Foreign trade** option is turned on.

### Sales order lines

1. Go to **Accounts receivable** > **Orders** > **All sales orders**.
1. Select an existing sales order that you want to work with, or create a new one.
1. On the **Lines** tab, on the **Product** FastTab, in the **CFD - Electronic invoices** section, specify the following information:

    - In the **Customs material type** field, select a value. The list of available values is already defined in the **Customs material type** catalog. The **Customs material type** field is required when the **Foreign trade** option is turned on.
    - In the **Customs document type** field, select a value. The list of available values is already defined in the **Customs document type** catalog. The **Customs document type** field is required when the **Foreign trade** option is turned on.
    - In the **Material description** field, enter a value. The **Material description** field is required when the **Customs material type** attribute contains the value **05** that has the description **Other** (**Otra**).
    - Set the **Identifier of customs document** field. The **Identifier of customs document** field is required when the **Foreign trade** option is turned on.

### Distance and time

You can define information about the distance and transportation time between shipment delivery locations in advance. Then, when users enter distance and transportation time on the **Transportation details** page, they can save time by selecting existing values instead of having to calculate new values. Follow these steps to set up information about the distance and transportation time between transportation spots.

1. Go to **Organization administration** > **Setup** > **EInvoice**.
1. On the **EInvoice** page, enter or select transportation spots.
1. Enter the time and distance between the two spots. Transportation spots are all shipment and delivery points. Spots can have different types. Here are some examples:

    - Customer
    - Warehouse
    - Border (if goods are delivered to border)
    - Other

> [!NOTE] 
> You can skip this procedure. However, if you skip this procedure, you must manually enter the distance and transportation time on the **Transportation details** page.

### Fixed assets

If your company implements the **Fixed assets** module, enter information in the fixed asset record for vehicles or trailers. You can use this information on the **Transportation details** page. This information is required for the Waybill (Carta de Porte) complement.

1. Go to **Fixed assets** > **Fixed assets** > **Fixed assets**.
1. On the **Technical information** FastTab, set the following fields:

    - In the **SAT classification** section:

        - **Vehicle type**
        - **Federal motor transport configuration** (for trucks only)
        - **Trailer type**

            - **Registration number**
            - **Vehicle gross weight**

    - In the **Model** section:

        - **Model year**
        - **Serial number**

### Workers

Follow these steps to enter tax ID (RFC) numbers, registration numbers, and license information for drivers. Before you start, make sure that identification types are set up at **Human resources** > **Setup** > **Identification types**.

1. Go to **Human resources** > **Workers** > **Employees/Contractors/Workers**.
1. On the action pane, select **Personal information** > **Identification numbers**.
1. In the **Identification type** field, select the corresponding type. For example, for a driver license identification type, select **Driver license**.

## Hazardous materials

If your company transports hazardous materials, enable the **Hazardous materials product information and shipping documentation** feature in the **Feature management** workspace. For more information, see [Feature management overview](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

After you enable the feature, follow these steps to enter additional hazardous material information.

1. Go to **Product information management** > **Products** > **All released products**.
1. Open the item record, and then, on the **Manage inventory** FastTab, set the **Hazardous materials** option to **Yes**.
1. On the action pane, select **Manage inventory** > **Compliance**.
1. On the **Item hazardous materials** page, on the header, set the **Regulation code** field.
1. On the **Material management** FastTab, in the **Packing group** section, set the **Packing group** field.

> [!NOTE]
> - To select values for the **Regulation code** and **Packing group** fields, first fill in the **Hazardous material regulation** and **Hazardous material packing groups** tables in accordance with the **c\_MaterialPeligroso** and **c\_TipoEmbalaje** SAT catalogs. These catalogs are located at **Product information management** > **Setup** > **Hazardous material shipping documentation**.
> - As of version 10.0.23 (build 10.0.1037.149), you can work with the **Display hazardous status** option to send the **matrialPeligrosso** attribute as output in an XML file. If the **Display hazardous status** option is set to **Yes**, you can set the **Hazardous materials** option to **Yes**.

:::image type="content" source="../media/latam-mx-hazardous2.png" alt-text="Screenshot of the Item hazardous materials page.":::

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
