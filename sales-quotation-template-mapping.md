Sales quotation headers and lines
=================================

Template and Task
-----------------

The following templates and underlying tasks are used to synchronize products
from Microsoft Dynamics 365 for Sales (Sales) to Microsoft Dynamics 365 for
Finance and Operations, Enterprise edition.

Name of template: Sales Quotes (Sales to Fin and Ops)

Name of task in project:

-   QuoteHeader

-   QuoteLine

 

Sync tasks required prior to Sales quotation header and lines sync:

-   Products

-   Accounts (if used)

-   Contacts (if used)

 
-

Entity set
----------

| **Sales**    | **CDS**       | **Finance and Operations** |
|--------------|---------------|----------------------------|
| Quotes       | Quotation     | Sales quotation headers    |
| QuoteDetails | QuotationLine | CDS sales quotation lines  |

Entity flow
-----------

Sales quotations are created in Sales and synchronized to Finance and
Operations.  
 

Sales quotations from Sales will be synchronized only under the following
conditions:

1.  All products on the quotation lines are externally maintained.

2.  The quotation is active or activated.

 

Prospect to cash solution for Sales
-----------------------------------

The field **Has Externally Maintained Products Only** is added to the **Quote**
entity to consistently keep track of whether the sales order is made up entirely
of **Externally Maintained Products**, in which case **Products** maintained in
Finance and Operations. This is done to ensure that you don't try to sync
**Sales order lines** with **Products** that are unknown to Finance and
Operations.

 

All **Quote products/lines** are updated with the **Externally Maintained**
information from the **Quote header** and this information can be found in the
field **Quote Has Externally Maintained Products Only** on the **Quote line**
entity.

**Discount**, **Charges** and **Tax** are controlled by a complex setup in
Finance and Operations, which does not allow for integration mapping at this
point. The current design is that **Price**, **Discount**, **Charge** and
**Tax** are mastered and handled by Finance and Operations.

In Sales, the solution makes the following fields read-only because these values
do not sync to Finance and Operations.

-   Read-only on SO Header: Discount %, Discount, Freight Amount

-   Read-only on SO Line: Tax

Preconditions and mapping setup
-------------------------------

-   Before synchronizing quotes, it is important to update Sales with the
    following setting:

>   Under **Settings \> Administration \> System settings \> Sales** ensure that
>   **Discount calculation method** is set to Per unit. This is done to ensure
>   that the line item discount from Sales match the setting in Finance and
>   Operations. Without this setting the discount would not be correct in
>   Finance and Operations, as Finance and Operations would read the discount as
>   a discount per unit, even if it was per line in Sales.

-   In Finance and Operations, **Number sequence** for **Quotations** must be
    set to **Manual**.

    -   **Account receivable \> Setup \> Account receivable parameters \> Number
        sequence - Number sequence for quotations. View details.** Under
        **General Setup,** set **Manual = Yes**.

-   To avoid sync failing for sales quotations, **Delivery date control** should
    be set to **None** as default in Finance and Operations. This is done under
    **Accounts receivable \> Setup \> Accounts receivable parameters \>
    Shipments**.

### QuoteHeader

-   **Requested delivery date** is required in Finance and Operations and sync
    will fail if this date is blank. To avoid this issue, the date is defaulted
    from **Source -\> CDS** in case of blank value. The date should be updated
    to a preferred value. Currently it is not possible to enter something like
    Today for today's date, so it must be a given date.

    -   Template value for Requested delivery date is defaulted to 1/1/2020.

-   **Address Country region code** is required in Finance and Operations. To
    avoid sync errors, you can default a value that is used if the field is left
    blank in Sales, which can also be useful to avoid having to type **Country
    region** for local addresses.

    -   Template value for **DeliveryAddressCountryRegionISOCode** is not
        defaulted.

-   Update the mapping for **CDS Organization ID in Source -\> CDS** to match
    the **CDS organization** in the **Organization** entity.

    -   Template value for **Organization_OrganizationId** is defaulted to
        ORG001.

    -   Template value for **Account_Organization_OrganizationId** is defaulted
        to ORG001.

    -   Template value for **InvoiceAccount_OrganizationId** is defaulted to
        ORG001.

### QuoteLine

-   Update the mapping for **CDS Organization ID in Source -\> CDS** to match
    the **CDS organization** in the **Organization** entity

    -   Template value for Organization_OrganizationId is defaulted to ORG001.

    -   Template value for **Product_Organization_Organization_OrganizationId**
        is defaulted to ORG001.

    -   Template value for
        **Quotation_Organization_Organization_OrganizationId** is defaulted to
        ORG001.

-   **Requested delivery date** is required in Finance and Operations and sync
    will fail if the date is blank. To avoid this issue, the date is defaulted
    from **Source -\> CDS** in case of blank value. The date should be updated
    to a preferred value. Currently, it is not possible to enter something like
    Today for today's date, so it must be a given date.

    -   Template value for **Requested delivery date** is defaulted to 1/1/2020.

-   It possible to add the following mappings from **CDS -\> Destination** to
    avoid that quotation line fails to import to Finance and Operations if the
    information is neither defaulted from customer, nor from product.

    -   **SiteId** - Site is required to generate **Quotes** and **Sales order
        lines** in Operations.

        -   Template value for SiteId is not defaulted.

    -   **WarehouseId** - Warehouse is required to process **Quote** and **Sales
        order lines** in Finance and Operations.

        -   Template value for WarehouseId is not defaulted.

-   Ensure that the needed **ValueMap** for selling UOM in Finance and
    Operations exists in the **CDS -\> Destination mapping** for **Quantity_UOM
    / SALESUNITSYMBOL.**

 

 

Template mapping in Data integrator
-----------------------------------

**Note:**

**Discount**, **Charges** and **Tax** are controlled by a complex setup in
Finance and Operations, which does not allow for integration mapping at this
point. The current design is that **Price**, **Discount**, **Charge** and
**Tax** are handled by Finance and Operations.

 

**Payment terms**, **Freight terms**, **Delivery terms**, **Shipping method**,
and **Delivery mode** are not part of the default mappings. Mapping of these
fields requires value mapping to be set up, which is specific to the data in the
organizations between which the entity is synchronized.

 

### QuoteHeader:

![Machine generated alternative text: SOURCE ENTITY quotes source \> CDS Search SOURCE FIELD CDS ENTITY Quotation CDS Destination MAP TYPE requestdeliveryby [Requested Delivery Date] shipto_city [Ship To City] shipto_country [Ship To Country/Region] totaldiscountamount [Total Discount Amount] description [Description] discountamount [Quote Discount Amount] shipto_linel [Ship To Street 1] name [Name] statecode [Status] shipto_postalcode [Ship To ZIP/Postal Code] quotenumber [Quote ID] shipto_line2 [Ship To Street 2] shipto_stateorprovince [Ship To State/Province] totalamount [Total Amount] transactioncurrencyid.isocurrencycode [Currency (Currency Code)] None None None customerid.Account(accountnumber).Contact(msdynce_contactnumber) [Potential Customer (Account Numbe transactioncurrencyid.isocurrencycode [Currency (Currency Code)] transactioncurrencyid.isocurrencycode [Currency (Currency Code)] DESTINATION ENTITY Sales quotation headers DESTINATION FIELD RequestedDeliveryDate [Requested delivery datel DeliveryAddress City [City of DeliveryAddress_Country [Country/region of TotalDiscountAmount [Total discount amount] Description [Description] DiscountAmount [Discount amount] DeliveryAddress_AddressLine1 [First line of {0}1 Name [Name] Status [Quotation status] DeliveryAddress_PostalCode [Postal code of Quotationld [Quotation ID] DeliveryAddress_AddressLine2 [Second line of DeliveryAddress_State [State of TotalAmount [Total amount] TotalAmount_CurrencyCode [Currency of Account_organization_organizationld [Organization IDI InvoiceAccount_Organization_Organizationld [Organization IDI Organization_organizationld [Organization ID] Account_Accountld [Account ID] TotalDiscountAmount_CurrencyCode [Currency of {Oh DiscountAmount_CurrencyCode [Currency of {OJI ](media/f23d793926b886532df9ada2aaf3305f.png)

 

![Machine generated alternative text: SOURCE ENTITY quotes Source \> CDS Search SOURCE FIELD CDS ENTITY Quotation DS \> Destinatio MAP TYPE Requested DeliveryDate [Requested delivery date] [E Account Accountld [Account ID] [E DeliveryAddress City [City of (Oh] DeliveryAddress_Country [Country/region of (Oh] TotalAmount CurrencyCode [Currency of [E Description [Description] [E DeliveryAddress AddressLine1 [First line of {Oh] [E DeliveryAddress_PostalCode [Postal code of [E Quotationld [Quotation ID] [E DeliveryAddress AddressLine2 [Second line of [E DeliveryAddress_State [State of (Oh] TotalAmount [Total amount) [E Name [Name] [E Account Accountld [Account ID] None [E Account Accountld [Account ID] DESTINATION ENTITY Sales quotation headers DESTINATION FIELD RequestedShippingDate [RequestedShippingDatel [E RequestingCustomerAccountNumber [RequestingCustomerAccountNumber] [E DeliveryAddressCity [DeliveryAddressCity] [E DeliveryAddressCountryRegionlSOCode [DeliveryAddressCountryRegionlSOCode] [E CurrencyCode [CurrencyCode] [E CustomersReference [CustomersReferencel [E DeliveryAddressStreetNumber [DeliveryAddressStreetNumber] [E DeliveryAddressZipCode [DeliveryAddressZipCodel [E SalesQuotationNumber [SalesQuotationNumberl [E DeliveryAddressStreet [DeliveryAddressStreet] [E DeliveryAddressStateld [DeliveryAddressStateld] QuotationTotalAmount [QuotationTotalAmount] [E SalesQuotationName [SalesQuotationNamel [E DeliveryAddressName [DeliveryAddressName] [E IsDeliveryAddressOrderSpecific [IsDeliveryAddressOrderSpecific] [E DeliveryAddressDescription [DeliveryAddressDescriptionl ](media/b21cccb4e842a7214f0050894808e7e0.png)

 

 

### Quote lines:

![Machine generated alternative text: SOURCE ENTITY quotedetails source \> CDS Search SOURCE FIELD None None CDS ENTITY Quotation Line CDS Destination requestdeliveryby [Requested Delivery Datel shipto_city [Ship To City) shipto_country [Ship To Country/Region) extendedamount [Extended Amount) manualdiscountamount [Manual Discount] shipto_linel [Ship To Street Il shipto_Iine2 [Ship To Street 21 shipto_postalcode [Ship To ZIP/PostaI Code) productid.productnumber [Existing Product (Product ID)] quantity [Quantity] quoteid.quotenumber [Quote (Quote ID)] sequencenumber [Sequence Number) shipto_stateorprovince [Ship To State,'Prcvincel uomid.name [Unit (Name)] priceperunit [Price Per Unit] transactioncurrencyid.isocurrencjn:ode [Currency (Currency Coden transactioncurrencyid.isocurrencjn:ode [Currency (Currency Coden transactioncurrencyid.isocurrencjn:ode [Currency (Currency Coden None DESTINATION ENTITY CDS sales quotation lines DESTINATION FIELD Quotation_organization Organizationld [Organization IDI [Organization ID) RequestedDeIiveryDate [Requested delivery date] DeliveryAddress_City [City of DeliveryAddress_Country [Country/region of LineAmount [Line amount] DiscountAmount [Discount amount) DeliveryAddress_AddressLineI [First lire of DeliveryAddress_AddressLine2 [Second line of DeliveryAddress_PostaICode [Postal code of {011 Product_productld [Product IDI Quantity IQuantityl Quotation_QuotationId [Quotation IDI Sequence [Sequence] DeliveryAddress_State [State of Quantity NOM [Unit of Measure of UnitPrice [Unit pricel LineAmount CurrencyCode [Currency of {Oil DiscountAmount_CurrencyCode [Currency of UnitPrice_CurrencyCode [Currency of Organization_organizationld [Organization IDI ](media/86d5fc259335c2e80305f9be5977d142.png)

 

![Machine generated alternative text: SOURCE ENTITY quotedetails source \> CDS Search SOURCE FIELD CDS ENTITY Quotation Line DS Destinatio Requested DeliveryDate [Requested delivery datel DeliveryAddress_City [City of DeliveryAddress_Country [Country/region of Description [Description) DeliveryAddress_AddressLireI [First lire of DeliveryAddress_PostaICode [Postal code of Product_productld [Product IDI Quantity [Quantity] Quotation_QuotatiorId [Quotation IDI DeliveryAddress_AddressLire2 [Second line of Sequence [Sequence] DeliveryAddress_State [State of Quantity_LlOM [Llnit of Measure of DiscountAmount [Discount amount] Unit Price [Unit price) ProductName [Product name) DeliveryAddress_City [City of DESTINATION ENTITY CDS sales quotation lines DESTINATION FIELD Requested ReceiptDate [RequestedReceiptDate) DeliveryAddressCity [DeliveryAddressCity] DeliveryAddressCountryRegionISOCode [DeliveryAddressCountryRegionISOCodel LineDescription [LineDescriptionl DeliveryAddressStreetNumber [DeliveryAddressStreetNumberl DeliveryAddressZipCode [DeliveryAddressZipCode) ProductNumber [ProductNumber] RequestedSaIesQuantity [RequestedSaIesQuantity] SalesQuotationNumber [SalesQuotationNumberl DeliveryAddressStreet [DeliveryAddressStreet) LineCreationSequenceNumber [LineCreationSequenceNumberl DeliveryAddressStateId [DeliveryAddressStateId] SaleslJnitSymboI [SaleslJnitSymboIl LineDiscountAmount [LineDiscountAmount) SSesPrice [Salesprice] ProductName [ProductName) DeliveryAddressDe-scription [DeliveryAddressDescription) ](media/aaab63f3b2af970980a078a072490589.png)
