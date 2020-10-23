---
# required metadata

title: USMCA certification of origin
description: This feature lets you print the certification of origin documents required by the United States-Mexico-Canada Agreement (USMCA).
author: Henrikan
manager: tfehr
ms.date: 10/23/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: henrikan
ms.search.validFrom: 2020-10-23
ms.dyn365.ops.version: Release 10.0.xx
---

# USMCA certification of origin

[!include [banner](../includes/banner.md)]

This feature lets you print the certification of origin documents required by the United States-Mexico-Canada Agreement (USMCA).

The *USMCA certification of origin document* contains the minimum data elements required for declaration. Some data elements can be pre-filled before printing while others must be filled in manually after printing. To obtain preferential tariff treatment, document must be completed and in the possession of the importer at the time the declaration is made. The document may be completed by the importer, exporter, or producer.

You can print the document for a single shipment from the **All shipments** list page or from the **Shipment details** page.

The document is only accessible when the country on the primary address for the legal entity is the United States.

Depending on the document print selection, the document can be pre-filled with data from your system. It is possible to change or add data to the printed document by exporting the printed document to an editable format, such as Microsoft Word. Once exported, you can apply any required changes before a declaration is made.

## Turn on the USMCA feature

Before you can use this feature, it must be turned on in your system. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Transportation management*
- **Feature name:** *USMCA certification of origin document*

## Print selection
<!-- KFM: I'm not sure what this section is telling me. Needs more intro I think -->
The USMCA certification of origin document contains the following data elements:

- Address elements
- Role of the certifying party
- Single shipment
- Invoices
- Banket period
- Item details
- Certifier signature
- Number of pages

SysLastValue is applied to the selection. <!-- KFM: What is this? I think we need few more details. -->

## Print a USMCA certification of origin document

To print a USMCA certification of origin document for a shipment, do the following:

1. Do one of the following:
    - Go to **Transportation management> Shipments > All shipments** and select the shipment you want to print the document for.
    - Open the **Shipment details** page for the shipment you want to print the document for (there are several ways to get here, including from the **All shipments** pages).
1. On the Action Pane, open the **Shipments** tab and, from the **Print** group, select **USMCA certificate of origin**.
1. The **Certificate or origin** dialog box opens. Make the settings described in the following subsections and then select **OK** to generate the document.
1. A preview of the document opens. Use the commands provided on the Action Pane to print or export the document as needed.

### Certifying party

In the **Certificate or origin** dialog box, use the **Certifying party** drop-down list to identify the type  of party that is printing the document. Specify whether the certifying party is the *Exporter*, *Exporter and Producer*, *Producer*, or *Importer*; or leave it blank if the certifying party is none of these. The option you select determines what is printed in the address sections of the document.

The **Certifying party** that you choose will be included in the printed document.

The document can be printed for both inbound and outbound shipments. Select *Importer* as **Certifying party** for inbound shipments only.

The following table describes which types of information are included in the document based on which **Certifying party** you choose.

| Certifying&nbsp;party | Description |
|---|---|
| *\[Blank\]* | Adds the following details to the document:<ul><li>**Certifier details**: Uses the address details for shipping warehouse, if available; otherwise it uses the shipping site address, if available; otherwise it uses the address of the legal entity (company) selected in Supply Chain Management.</li><li>**Exporter details**: Blank</li><li>**Producer details**: Blank</li><li>**Importer details**: Blank</li><ul>|
| *Exporter* | Adds the following details to the document:<ul><li>**Certifier details**: Uses the address details for shipping warehouse, if available; otherwise it uses the shipping site address, if available; otherwise it uses the address of the legal entity (company) selected in Supply Chain Management.</li><li>**Exporter details**: Uses the address details for the legal entity.</li><li>**Producer details**: Blank</li><li>**Importer details**: Uses the invoice account for the related sales order.</li><ul>|
| *Exporter and Producer* | Adds the following details to the document:<ul><li>**Certifier details**: Uses the address details for shipping warehouse, if available; otherwise it uses the shipping site address, if available; otherwise it uses the address of the legal entity (company) selected in Supply Chain Management.</li><li>**Exporter details**: Uses the address details for the legal entity.</li><li>**Producer details**: Uses the address details for the legal entity.</li><li>**Importer details**: Uses the invoice account for the related sales order.</li><ul>|
| *Importer* | Adds the following details to the document:<ul><li>**Certifier details**: Uses the address details for shipping warehouse, if available; otherwise it uses the shipping site address, if available; otherwise it uses the address of the legal entity (company) selected in Supply Chain Management.</li><li>**Exporter details**: Blank</li><li>**Producer details**: Blank</li><li>**Importer details**:  Uses the address details for the legal entity.</li><ul>|
| *Producer* | Adds the following details to the document:<ul><li>**Certifier details**: Uses the address details for shipping warehouse, if available; otherwise it uses the shipping site address, if available; otherwise it uses the address of the legal entity selected in Supply Chain Management.</li><li>**Exporter details**: Blank</li><li>**Producer details**:  Uses the address details for the legal entity.</li><li>**Importer details**: Blank</li><ul>|

### Has various producers

In the **Certificate or origin** dialog box, the **Certifying party** drop-down list controls the text to be used for the producer details in the document. Choose one of the following:

- *Various producers* - Prints print the text "Various" in the producer details.
- *Available upon request* - Prints the text "Available upon request by the importing authorities" in the producer details.

When the **Certifying party** is set to *Exporter and Producer* or *Producer*, then the **Has various producers** setting is overruled, and the producer address details will be the same as the certifier.

### Blanket period

In the **Certificate or origin** dialog box, use the **Blanket period from** and **Blanket period to** settings to establish a blanket period of up to 12 months, during which the document will cover multiple shipments of identical goods, even though the document is printed for only one shipment. You can set the blanket period dates without any constraints, and it will be added to the document. You can also leave these settings blank or even set them in the past.
<!-- KFM: Is the blanket period "max 12 months" or "without constraints"? I think we should add a bit more detail about the practical considerations, like how this will work (doc kept on file, or doc automatically printed for each shipment, or what?). -->

### Is single shipment

In the **Certificate or origin** dialog box, set **Single shipment** to one of the following:

- *Yes* - Prints "Single Shipment: Yes" next to the invoice number.
- *No* - Prints nothing.

## Other information included in the document

In addition to the optional elements that you select using the **Certificate or origin** dialog box, the USMCA certification of origin document will include the information and custom fields summarized in the following subsections. Some of this information must be entered manually after you generate the document (as described).

### Invoice number

IDs of sales invoice(s) related to shipments are printed on the document irrespective of the blanket period. Invoice numbers are printed irrespective of the Single Shipment selection. Only IDs of sales invoices are printed.

### Item details

Sections 6.1 to 9 in the printed document include specific item details. These are SKU Number, Description, Harmonized System (HS) Tariff Classification, Origin Criterion, Country of Origin.

- **SKU Number**: Prints the item number of the released product.

- **Description**: Prints either the description or name for the released product. If a description in the user's language exists, then this is printed. If no such exists, then the name in the user's language is printed. If no such exists, then the item name is printed.

- **Harmonized System (HS) Tariff Classification**: Prints the Harmonized Tariff Schedule associated to the product. The schedules are setup under Transportation Management&gt;Setup&gt;Transportation standard&gt;Harmonized Tariff Schedules.

- **Origin Criterion:** Data in this section must be filled in manually in the first release of the report.

- **Country of origin:** Prints the country of origin is applied using the Product Information Management &gt; Setup&gt;Product Compliance&gt;Country of Origin. The ISO code for the country of origin is printed based on the country of destination in the shipment delivery address and the item. If no country of origin data has been setup here, then fall back to released product&gt;foreign trade&gt;origin. If no country of origin data has been setup here, then the country of origin will have to be filled in manually.

### Certifier signature and date

Data in this section must be filled in manually.

### Consists of number of pages

Number of pages must be filled in manually by the user signing the certification.

### Number of pages

Current page and number of pages printed in the bottom of the document.
