---
# required metadata

title: Waybill (Carta de Porte) complement
description: This topic explains how to set up and submit parking slips and transfer orders with the Waybill (Carta de Porte) complement.
author: v-oloski
ms.date: 09/07/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Mexico
# ms.search.industry: 
ms.author: v-oloski
ms.search.validFrom: 2021-08-31
ms.dyn365.ops.version: 10.0.23

---

# Waybill (Carta de Porte) complement

[!include [banner](../includes/banner.md)]

This topic provides information about how to set up and submit parking slips and transfer orders with the Waybill (Carta de Porte) complement. The Waybill (Carta de Porte) complement is mandatory for taxpayers who transport goods and merchandise in the national territory starting October 1st, 2021.

To generate the Waybill complement in CFDI documents, fill in transportation information in the **Transportation details** page from one of the following business documents:

- A sales order record. This includes sales orders for the project. Sales order records can be found under **Accounts receivable** > **Orders** > **All sales orders**, and on the Action Pane select **Pick and Pack**.
- A transfer order, which is located under **Inventory management** > **Outbound orders** > **Transfer orders**, and on the Action Pane select **Ship**.
- A shipment, which is located under **Inventory management** > **Outbound orders** > **Shipments**.
- Project requirements, which are under **Project management and accounting** > **Item tasks > Project requirements**, and on the Action Pane select **Manage**.

> [!NOTE] 
> You can view transportation information on the **CFDI - Packing Slip Electronic Invoices** and **CFDI - Invent Transfer Electronic Invoices** list pages.

## Transportation details page

This section provides information about the fields that are required on the **Transportation details field**. In the graphic, the required fields can been highlighted.

![Transportation details](media/latam-mx-transportation-details.png)


### **General** FastTab:

  - **Permission type**
  - **Transportation permission ID**
  - **Distance**
  - **Hours**

### **Vehicle** FastTab

**Truck** field group

  - **Registration number**
  - **Federal motor transport configuration**
  - **Model year**

**Insurance** field group

  - **Vendor account**
  - **Vendor number**

**Driver** field group

  - **RFC number** or **Registration number** 
  - **Country/region**
  - **Driver license**

If a trailer is used in the transportation of goods, enter the following field information in the **Trailer** field group:

  - **Trailer registration number**
  - **Trailer type**

> [!NOTE]
> If there is an additional trailer or an additional driver, include that information.

Excluding Federal motor transport configurations, fields for a truck, a trailer, and a driver can be filled in manually or by using information from fixed assetand worker records.

## Posting packing slips and shipping transfer orders with the Waybill (Carta de Porte) complement

If you select **Enable CFDI packing slip** in the **Packing slip posting** or **Shipment** pages, the **Generate transportation note** is selected automatically. However, you can clear this parameter if necessary. If **Generate transportation note** is selected, the Waybill (Carta de Porte) complement will be included in xml file.

## Setup

### Catalogs

Set up the following catalogs to add information to the **Permission type**, **Trailer type** and **Federal motor transport configuration** fields.

1. Go to **Organization administration** > **Setup** > **EInvoice** > **SAT classification** > **Transportation**.
2. On the **Transportation** page, create the following:

  - Trailer type (SAT catalog is c_SubTipoRem)
  - Permission type (SAT catalog is c_TipoPermiso)
  - Federal motor transport configuration (SAT catalog is c_ConfigAutotransporte)

### Permission number

1. Go to **Organization administration** > **Organizations** > **Legal entities**.
2. Expand the **Transportation permissions** FastTab and in the **Transportation permission ID** field, enter the permission number provided by the SCT.

### Items

1. Go to **Product information management** \> **Products** \> **All released products**.
2. Select and open the item record you want to work with and expand the**Manage inventory** FastTab.
3. Fill in the **Net weight** and **Tare weight** fields if necessary. The value in the **Gross weight** field is filled in automatically.

### Distance and time

To speed up filling distance and transportation time in the **Transportation details** form, a user can set up distance and time between the shipment and delivery spots:

Organization administration \> Setup \> EInvoice

  - Transportation spots.
  - Transit time and distance (between pick up and drop off spots).

Transportation spots are all shipment and delivery points. Spots can have different types:

  - Customer.
  - Warehouse.
  - Border, if goods are delivered to border.
  - Other

> [!NOTE] 
> This step can be skipped and in this case a user should fill in the distance and the transportation time manually in the **Transportation details** form. If this setting is executed a user can select pick up and drop off spots in the **Transportation details** form and the distance and the time are filling automatically.

### Fixed assets

If your company has implemented the **Fixed assets** module, enter information in the fixed asset record for vehicles or trailers. This information can then be used on the **Transportation details** page. This information is needed for the Waybill (Carta de Porte) complement.

1. Go to **Fixed assets** > **Fixed assets** > **Fixed assets**. 
2. On the **Technical information** FastTab, enter the following field information.

  - **SAT classification** field group:

      - Vehicle type
      - Federal motor transport configuration (for trucks only)
      - Trailer type

  - **Model** field group:

      - Model year
      - Serial number

### Workers

Complete the following steps to enter driver FRC numbers, registration numbers, and license information. Before you start, ensure that identification types have been set up under **Human resources** > **Setup** > **Identification types**.

1. Go to **Human resources** > **Workers** > **Employees/Contractors/Workers**.
2. On the Action Pane, select **Personal information** > **Identification numbers**.
3. In the **Identification type** field, select the corresponding type. For example, for a driver license identification type, select **Driver license**.

## Hazardous materials

If the company transports hazardous materials, enable the feature **Hazardous materials product information and shipping documentation** in the **Feature management** workspace. For more information, see [Feature management overview](../../fin-ops/get-started/feature-management/feature-management-overview.md).

1. After you enable the feature, go to **Product information management** \> **Products** \> **All released products**.
2. Open the item record and on the **Manage  inventory** FastTab, set the **Hazardous materials** field to **Yes**. 
3. On the Action Pane, select **Manage inventory** > **Compliance** and then enter addition hazardous material information.

![Hazardous materials](media/latam-mx-hazardous2.png)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
