---
# required metadata

title: USMCA certification of origin
description: This feature lets you print the certification of origin documents required by the United States-Mexico-Canada Agreement (USMCA).
author: Weijiesa
ms.date: 08/09/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: WHSShipPlanningListPage, WHSShipmentDetails
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for articles migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: weijiesa
ms.search.validFrom: 2020-10-23
ms.dyn365.ops.version: 10.0.16
---

# USMCA certification of origin

[!include [banner](../includes/banner.md)]

This feature lets you print the certification of origin documents required by the United States-Mexico-Canada Agreement (USMCA).

The *USMCA certification of origin document* contains the minimum data elements required for declaration. Some data elements can be pre-filled before printing while others must be filled in manually after printing. To obtain preferential tariff treatment, the document must be completed and in the possession of the importer at the time the declaration is made. The document may be completed by the importer, exporter, or producer.

You can print the document for a single shipment from the **All shipments** list page or from the **Shipment details** page.

The document is only accessible when the country/region on the primary address for the legal entity is the United States.

Depending on the document print selection, the document can be pre-filled with data from your system. It is possible to change or add data to the printed document by exporting the printed document to an editable format, such as Microsoft Word. After export, you can apply any required changes before a declaration is made.

## Turn the USMCA feature on or off

To use this feature, it must be turned on for your system. As of Supply Chain Management version 10.0.29, the feature is turned on by default. Admins can turn this functionality on or off by searching for the *USMCA certification of origin document* feature in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

## Document content

The USMCA certification of origin document contains the following data elements:

- Address elements
- Role of the certifying party
- Single shipment
- Invoices
- Blanket period
- Item details
- Certifier signature
- Number of pages

For more information about each of these elements and how their values are found, see the remaining sections in this article.

## Print a USMCA certification of origin document

To print a USMCA certification of origin document for a shipment, do the following:

1. Do one of the following:
    - Go to **Transportation management \> Planning \> Shipments \> All shipments** and select the shipment you want to print the document for.
    - Open the **Shipment details** page for the shipment you want to print the document for (there are several ways to get here, including from the **All shipments** page).
1. On the Action Pane, open the **Shipments** tab and, from the **Print** group, select **USMCA certificate of origin**.
1. The **Certificate or origin** dialog box opens. Make the settings described in the following subsections and then select **OK** to generate the document.
1. A preview of the document opens. Use the commands provided on the Action Pane to print or export the document as needed.

### Certifying party

Use the **Certifying party** drop-down list to identify the type  of party that is printing the document. Specify whether the certifying party is the *Exporter*, *Exporter and Producer*, *Producer*, or *Importer*; or leave it blank if the certifying party is none of these. The option you select determines what is printed in the address sections of the document.

The **Certifying party** that you choose will be included in the printed document.

The document can be printed for both inbound and outbound shipments. Select *Importer* as **Certifying party** for inbound shipments only.

The following table describes the types of information that are included in the document based on the **Certifying party** that you choose.

| Certifying&nbsp;party | Description |
|---|---|
| *\[Blank\]* | Adds the following details to the document:<ul><li>**Certifier details**: Uses the address details for the shipping warehouse, if available; otherwise it uses the shipping site address, if available; otherwise it uses the address of the legal entity (company) selected in Supply Chain Management.</li><li>**Exporter details**: Blank</li><li>**Producer details**: Blank</li><li>**Importer details**: Blank</li><ul>|
| *Exporter* | Adds the following details to the document:<ul><li>**Certifier details**: Uses the address details for the shipping warehouse, if available; otherwise it uses the shipping site address, if available; otherwise it uses the address of the legal entity (company) selected in Supply Chain Management.</li><li>**Exporter details**: Uses the address details for the legal entity.</li><li>**Producer details**: Blank</li><li>**Importer details**: Uses the invoice account for the related sales order.</li><ul>|
| *Exporter and Producer* | Adds the following details to the document:<ul><li>**Certifier details**: Uses the address details for the shipping warehouse, if available; otherwise it uses the shipping site address, if available; otherwise it uses the address of the legal entity (company) selected in Supply Chain Management.</li><li>**Exporter details**: Uses the address details for the legal entity.</li><li>**Producer details**: Uses the address details for the legal entity.</li><li>**Importer details**: Uses the invoice account for the related sales order.</li><ul>|
| *Importer* | Adds the following details to the document:<ul><li>**Certifier details**: Uses the address details for the shipping warehouse, if available; otherwise it uses the shipping site address, if available; otherwise it uses the address of the legal entity (company) selected in Supply Chain Management.</li><li>**Exporter details**: Blank</li><li>**Producer details**: Blank</li><li>**Importer details**:  Uses the address details for the legal entity.</li><ul>|
| *Producer* | Adds the following details to the document:<ul><li>**Certifier details**: Uses the address details for the shipping warehouse, if available; otherwise it uses the shipping site address, if available; otherwise it uses the address of the legal entity selected in Supply Chain Management.</li><li>**Exporter details**: Blank</li><li>**Producer details**:  Uses the address details for the legal entity.</li><li>**Importer details**: Blank</li><ul>|

### Has various producers

The **Certifying party** drop-down list controls the text to be used for the producer details in the document. Choose one of the following:

- *Various producers* - Prints the text "Various" in the producer details.
- *Available upon request* - Prints the text "Available upon request by the importing authorities" in the producer details.

When the **Certifying party** is set to *Exporter and Producer* or *Producer*, then the **Has various producers** setting is overruled, and the producer address details will be the same as the certifier.

### Blanket period

Use the **Blanket period from** and **Blanket period to** settings to establish a blanket period, during which the document will cover multiple shipments of identical goods, even though the document is printed for only one shipment. You can set the blanket period dates without any constraints, and it will be added to the document. You can also leave these settings blank or set them in the past.

### Is single shipment

In the **Certificate of origin** dialog box, set **Is single shipment** to one of the following:

- *Yes* - Adds "Single Shipment: Yes" next to the invoice number.
- *No* - Adds nothing.

## Other information included in the document

In addition to the optional elements that you select using the **Certificate or origin** dialog box, the USMCA certification of origin document will include the information and custom fields summarized in the following subsections. Some of this information must be entered manually after you generate the document.

### Invoice number

The IDs of sales invoices related to shipments are printed on the document irrespective of the blanket period. Invoice numbers are printed irrespective of the **Is single shipment** selection.

### Item details

The document provides several sections that list specific item details, which are:

- **SKU number**: Prints the item number of the released product.

- **Description**: Prints either the description or name for the released product. If a description in the user's language exists, then this is printed. If no such description exists, then the name in the user's language is printed. If that name doesn't exist, then the item name is printed.

- **Harmonized System (HS) Tariff Classification**: Prints the Harmonized Tariff Schedule associated to the product. You can set up these schedules by going to **Transportation Management \> Setup \> Transportation standard \> Harmonized Tariff Schedules**.

- **Origin criterion:** You must manually enter data in this section the first time you release the document.

- **Country of origin:** Prints the country of origin, which you apply by going to **Product information management \> Setup \> Product compliance \> Country of origin** (see also [Country of origin](../pim/country-of-origin.md)). The ISO code for the country of origin is printed based on the country/region of destination in the shipment delivery address and the item. If no country of origin data has been set up, then this value reverts back to the setting found at **Released product \> Foreign trade \> Origin**. If still no country of origin data is found, then you must manually enter the country of origin after generating the document.

### Certifier signature and date

You must enter this manually after generating the document.

### Consists of number of pages

The user signing the certification must manually enter the number of pages (for verification) after generating the document.

### Page numbers

Current page and number of pages printed at the bottom of the document.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]