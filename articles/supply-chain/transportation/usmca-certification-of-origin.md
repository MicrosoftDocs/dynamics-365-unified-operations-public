# USMCA Certification of Origin

This feature lets you print a USMCA certification of origin document. Before you can use this feature, it must be turned on in your system. Admins can use the [feature management](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview) settings to check the status of the feature and turn it on. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Transportation management*

- **Feature name:** *USMCA certification of origin document*

The *USMCA certification of origin document* contains the minimum data elements required for declaration. Some data elements can be pre-filled before printing while others must be filled in manually after printing. To obtain preferential tariff treatment, the *USMCA certification of origin document* must be completed and in the possession of the importer at the time the declaration is made. The*USMCA certification of origin document* may be completed by the importer, exporter, or producer.

The document can be printed for a single shipment from the Warehouse management&gt; Shipments &gt; All shipments list page or from the Shipment details page.

The document is only accessible when the country on the primary address for the legal entity is USA.

Depending on the document print selection, the document is prefilled with data from your system**.** It is possible to change or add data to the printed document, by exporting the printed document to an editable format, such as Word. This supports any required changes after the document has been printed and before a declaration is made.

## Print selection

The report contains a number of data elements: Address elements, role of the certifying party, invoices, blanket period, item details, Certifier Signature, and number of pages.

### Certifying Party

The **Certifying party** is the party printing the document. Specify whether the certifying party is the *Exporter*, *Exporter and Producer*, *Producer*, *Importer*, or neither exporter, producer, nor importer, by selecting the *\[blank\]* option. Which option you select, determines what is printed in the address sections of the document. See the table below.

The document can be printed for both inbound and outbound shipments. You should select *Importer* as Certifying party for inbound shipments only.

| **Certifying party** dialogue selection | *\[Blank\]*             | Print Certifier details (from company info)                     
                                                                    
   Exporter detail Blank                                            
                                                                    
   Producer Blank                                                   
                                                                    
   Importer Blank                                                   |
|-----------------------------------------|-------------------------|-----------------------------------------------------------------|
|                                         | *Exporter*              | Print Certifier details (from company info)                     
                                                                    
   Print Exporter details (same as certifier)                       
                                                                    
   Producer Blank                                                   
                                                                    
   Print Importer details (The delivery address from the shipment)  |
|                                         | *Exporter and Producer* | Print Certifier details (from company info)                     
                                                                    
   Print Exporter details (same as certifier)                       
                                                                    
   Print Producer details (same as certifier)                       
                                                                    
   Print Importer details (The delivery address from the shipment)  |
|                                         | *Importer*              | Print Certifier details (from company info)                     
                                                                    
   Print Importer details (Same as certifier)                       
                                                                    
   Exporter Blank                                                   
                                                                    
   Producer Blank                                                   |
|                                         | *Producer*              | Print Certifier details (from company info)                     
                                                                    
   Print Producer details (same as certifier)                       
                                                                    
   Exporter Blank                                                   
                                                                    
   Importer Blank                                                   |

The certifying party role selected is included in the printed document.

### Has various producers

This setting controls the text to be used for the producer details in the document. Set to *Various producers* to print the text "Various" in the producer details. Set to *Available upon request* to print the text "Available upon request by the importing authorities" in the producer details. When the certifying party is *Exporter and Producer* or*Producer*, then the**Has various producers** setting is overruled, and the producer address details will be the same as certifier.

### Blanket Period

Select *Yes* if the document is intended to cover multiple shipments of identical goods for a specified period up to 12 months even though the document is printed for only one shipment. The blanket period dates must afterwards be filled in manually. When*Yes* is selected, then no IDs of sales invoices related to shipments are printed, as more invoices are expected to follow after the document has been printed. Be aware that invoice IDs are only be printed for the invoiced sales orders related to the shipment.

Select *No* when the document is for a single shipment. When*No* is selected, then the IDs of sales invoices related to shipments are printed.

## Item details

Sections 6.1 to 9 in the printed document include specific item details. These are SKU Number, Description, Harmonized System (HS) Tariff Classification, Origin Criterion, Country of Origin.

**SKU Number**: The item number of the released product.

**Description**: Either the description or name for the released product. If a description in the user's language

exists, then this is printed. If no such exists, then the name in the user's language is printed. If no such

exists, then the item name is printed.

**Harmonized System (HS) Tariff Classification**: The Harmonized Tariff Schedule associated to the product.

The schedules are setup under Transportation Management&gt;Setup&gt;Transportation Standard&gt;Harmonized

Tariff Schedules.

**Origin Criterion:** Data in this section must be filled in manually.

**Country of origin:** The country of origin is applied using the Product Information Management &gt;

Setup&gt;Product Compliance&gt;Country of Origin. The ISO code for the country of origin is printed based on

the country of destination in the shipment delivery address and the item. If no country of origin data exists,

then the country of origin will have to be filled in manually.

## Certifier Signature and Date

Data in this section must be filled in manually.

## Number of pages

Current page and number of pages printed in the bottom of the document.
