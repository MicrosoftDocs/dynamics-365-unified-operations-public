--- 
# required metadata 
 
title: USMCA certification of origin
description: This feature lets you print a USMCA certification of origin document
author: Henrikan
manager:  
ms.date: 10/8/2020
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: WHSShipPlanningListPage,WHSShipmentDetails   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: 
ms.search.validFrom: 2020-10-08 
ms.dyn365.ops.version: Version 7.0.0 
---

This feature lets you print a USMCA certification of origin document. Before you
can use this feature, it must be turned on in your system. Admins can use
the [feature
management](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview) settings
to check the status of the feature and turn it on. In the **Feature
management** workspace, the feature is listed in the following way:

-   **Module:** *Transportation management*

-   **Feature name:** *USMCA certification of origin document*

The *USMCA certification of origin document* contains the minimum data elements
required for declaration. Some data elements can be pre-filled before printing
while others must be filled in manually after printing. To obtain preferential
tariff treatment, the *USMCA certification of origin document* must be completed
and in the possession of the importer at the time the declaration is made. The
*USMCA certification of origin document* may be completed by the importer,
exporter, or producer.

The document is printed for a single shipment from the Warehouse management\>
Shipments \> All shipments list page or from the Shipment details page.

The document is only accessible when the country on the primary address for the
legal entity is USA.

Depending on the document print selection, the document is prefilled with data
from your system**.** It is possible to change or add data to the printed
document by exporting the printed document to an editable format, such as Word.
This supports any required changes after the document has been printed and
before a declaration is made.

Print selection
---------------

The report contains a number of data elements: Address elements, role of the
certifying party, single shipment, invoices, blanket period, item details,
certifier signature, and number of pages. SysLastValue is applied to the
selection.

### Certifying Party

The **Certifying party** is the party printing the document. Specify whether the
certifying party is the *Exporter*, *Exporter and Producer*, *Producer*,
*Importer*, or neither exporter, producer, nor importer, by selecting the
*[blank]* option. Which option you select determines what is printed in the
address sections of the document. See details below.

The document can be printed for both inbound and outbound shipments. You should
select *Importer* as **Certifying party** for inbound shipments only.

**Certifying party** dialogue selection:

*[Blank]* Prints certifier details (Address details from warehouse for shipment.
If not exist, then from site for shipment. If not exist, then from company
info).

>   Exporter details blank

>   Producer details blank

>   Importer details blank

*Exporter* Prints certifier details (Address details from warehouse for
shipment. If not exist, then from site for shipment. If not exist, then from
company info)

>   Prints exporter details (Company Info)

>   Producer details blank

>   Prints importer details (From Invoice account for related sales order)

*Exporter and Producer* Prints certifier details (Address details from warehouse
for shipment. If not exist, then from site for shipment. If not exist, then from
company info)

>   Prints exporter details (Company Info)

>   Prints producer details (Company Info)

>   Prints importer details (From Invoice account for related sales order)

*Importer* Prints certifier details (Address details from warehouse for
shipment. If not exist, then from site for shipment. If not exist, then from
company info)

>   Prints importer details (Company Info)

>   Exporter details blank

>   Producer details blank

*Producer* Prints certifier details (Address details from warehouse for
shipment. If not exist, then from site for shipment. If not exist, then from
company info)

>   Prints producer details (Company Info)

>   Exporter details blank

>   Importer details blank

The certifying party role selected is included in the printed document.

### Has various producers

This setting controls the text to be used for the producer details in the
document. Set to *Various producers* to print the text "Various" in the producer
details. Set to *Available upon request* to print the text "Available upon
request by the importing authorities" in the producer details. When the
certifying party is *Exporter and Producer* or *Producer*, then the **Has
various producers** setting is overruled, and the producer address details will
be the same as certifier.

### Blanket Period

Select the From/To date for the blanket period when the document is intended to
cover multiple shipments of identical goods for a specified period up to 12
months even though the document is printed for only one shipment. The blanket
period dates can be set by the user without any constraints and will be added to
the document. The blanket period can be left blank and can be in the past.

Single Shipment: Yes/No. 
-------------------------

When *Yes*, prints “Single Shipment: Yes” left to the invoice number. When *No*,
prints nothing.

Invoice Number
--------------

IDs of sales invoice(s) related to shipments are printed on the document
irrespective of the blanket period. Invoice numbers are printed irrespective of
the Single Shipment selection. Only IDs of sales invoices are printed.

Item details
------------

Sections 6.1 to 9 in the printed document include specific item details. These
are SKU Number, Description, Harmonized System (HS) Tariff Classification,
Origin Criterion, Country of Origin.

**SKU Number**: Prints the item number of the released product.

**Description**: Prints either the description or name for the released product.
If a description in the user’s language exists, then this is printed. If no such
exists, then the name in the user’s language is printed. If no such exists, then
the item name is printed.

**Harmonized System (HS) Tariff Classification**: Prints the Harmonized Tariff
Schedule associated to the

product. The schedules are setup under Transportation
Management\>Setup\>Transportation

standard\>Harmonized Tariff Schedules.

**Origin Criterion:** Data in this section must be filled in manually in the
first release of the report.

**Country of origin:** Prints the country of origin is applied using the Product
Information Management \>

Setup\>Product Compliance\>Country of Origin. The ISO code for the country of
origin is printed based on

the country of destination in the shipment delivery address and the item. If no
country of origin data has been setup here, then fall back to released
product\>foreign trade\>origin. If no country of origin data has been setup
here, then the country of origin will have to be filled in manually.

Certifier Signature and Date
----------------------------

Data in this section must be filled in manually.

Consists of number of Pages
---------------------------

Number of pages must be filled in manually by the user signing the
certification.

Number of pages
---------------

Current page and number of pages printed in the bottom of the document.
