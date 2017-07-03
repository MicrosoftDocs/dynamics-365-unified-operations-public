Sales order headers and lines
=============================

Template and Task
-----------------

The following templates and underlying tasks are used to synchronize products
from Microsoft Dynamics 365 for Sales (Sales) to Microsoft Dynamics 365 for
Finance and Operations, Enterprise edition.

Name of template: Sales Orders (Sales to Fin and Ops)

Name of task in project:

-   OrderHeader

-   OrderLine

 

Sync tasks required prior to Sales order header and lines sync:

-   Products

-   Accounts (if used)

-   Contacts (if used)

 
-

Entity set
----------

| **Sales**         | **CDS**        | **Operations**          |
|-------------------|----------------|-------------------------|
| SalesOrders       | SalesOrder     | Sales order headers V2  |
| SalesOrderDetails | SalesOrderLine | CDS sales order lines   |

 

 

Entity flow
-----------

**Sales orders** are created in Sales and synchronized to Finance and
Operations. **Sales orders** from Sales will be synchronized only under the
following conditions:

 

1.  All products on the sales order lines are externally maintained.

2.  The sales order has been submitted.

>    

Prospect to cash solution for Sales
-----------------------------------

The field **Has Externally Maintained Products Only** is added to the **Order
header** to consistently keep track of whether the sales order is made up
entirely of **Externally Maintained Products**, in which case Products are
maintained in Finance and Operations. This is done to ensure that you don't try
to sync sales order lines with Products that are unknown to Finance and
Operations.

 

All **Order Products/lines** are updated with the **Externally Maintained**
information from the **Sales order header** and this information can be found in
the field **Order Has Externally Maintained Products Only** on the **Order
line** entity.

 

Orders with **Has Externally Maintained Products Only = Yes** can be submitted
by clicking the **Submit Order** button. Only **Submitted Orders** and **Order
products/lines** will sync to CDS and Finance and Operations.

 

The **Order status** changes automatically to **Invoiced** once the related
invoice from Finance and Operations has synchronized to Sales. Also, the
**Owner** of the sales order from which the invoice was created from is assigned
as the **Owner** of the invoice. This gives the **Owner** of the sales order the
ability to view the invoice.

 

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

-   Before synchronizing sales orders, it is important to update Sales with the
    following setting:

>   Under **Settings \> Administration \> System settings \> Sales** ensure that
>   **Discount calculation method** is set to Per unit. This is done to ensure
>   that the line item discount from Sales match the setting in Finance and
>   Operations. Without this setting the discount would not be correct in
>   Finance and Operations, as Finance and Operations would read the discount as
>   a discount per unit, even if it was per line in Sales.

-   In Finance and Operations, **Number sequence** for **Sales orders** must be
    set to **Manual**.

    -   **Account receivable \> Setup \> Account receivable parameters \> Number
        sequence - Number sequence for sales orders. View details**; Under
        **General Setup**, set **Manual = Yes**.

-   To avoid sync failing for sales orders, **Delivery date control** should be
    set to **None** as default in Finance and Operations. This is done under
    **Accounts receivable \> Setup \> Accounts receivable parameters \>
    Shipments**.

### SalesHeader

-   **Requested delivery date** is required in Finance and Operations and sync
    will fail if the date is blank. To avoid this issue, the date is defaulted
    from **Source -\> CDS** in case of blank value. The date should be updated
    to a preferred value. Currently, it is not possible to enter something like
    [today] for today's date, so it must be a given date.

    -   Template value for **Requested delivery date** is defaulted to 1/1/2020.

-   **Order date** is required in CDS and sync will fail if the field is blank.
    To avoid this issue, the date is defaulted from **Source -\> CDS** in case
    of blank value. The date should be updated to a preferred value. Currently,
    it is not possible to enter something like [today] for today's date, so it
    must be a given date.

    -   Template value for Order date is defaulted to 1/1/2020.

-   **Address Country region code** is required in Finance and Operations. To
    avoid sync errors, you can default a value that is used if the field is left
    blank in Sales.

    -   Template value for **DeliveryAddressCountryRegionISOCode** is defaulted
        to USA.

-   Update the mapping for **CDS Organization ID Organization_OrganizationId in
    Source -\> CDS.**

    -   Template value for **SalesOrder_Organization_OrganizationId** is
        defaulted to ORG001.

    -   Template value for **Product_Organization_OrganizationId** is defaulted
        to ORG001.

### SalesLine

-   It is possible to add the following mappings from **CDS -\> Destination** to
    avoid that sales line fails to import to Finance and Operations if the
    information is neither defaulted from customer, nor from product:

    -   **SiteId** - Site is required to generate **Quotes** and **Sales
        orders** in Finance and Operations.

        -   Template value for SiteId is defaulted to 1.

    -   **WarehouseId** - Warehouse is required to process **Quote** and **Sales
        orders** in Finance and Operations.

        -   Template value for WarehouseId is defaulted to 13.

-   Ensure that the needed **ValueMap** for selling UOM in Finance and
    Operations exists in the **CDS -\> Destination mapping** for **Quantity_UOM
    / SALESUNITSYMBOL**.

>    

Template mapping in Data integrator
-----------------------------------

**Note:**

**Payment terms**, **Freight terms, Delivery terms, Shipping method,** and
**Delivery mode** are not part of the default mappings. Mapping of these fields
requires value mapping to be set up, which is specific to the data in the
organizations between which the entity is synchronized.

>    

### OrderHeader

![Machine generated alternative text: SOURCE ENTITY salesorders Source \> CDS Search SOURCE FIELD CDS \> CDS ENTITY SalesOrder Destination MAP TYPE requestdeliveryby [Requested Delivery Date] [Z] shipto_city [Ship To City] [Z] shipto_country [Ship To Country/Region] totaldiscountamount [Total Discount Amount] [Z] description [Description] discountamount [Order Discount Amount] [Z] shipto_linel [Ship To Street 1] name [Name] submitdate [Date Submitted] statecode [Status] [Z] shipto_postalcode [Ship To ZIP/Postal Code] [Z] ordernumber [Order ID] [Z] shipto_line2 [Ship To Street 2] [Z] shipto_stateorprovince [Ship To State/Province] totalamount [Total Amount] [Z] transactioncurrencyid.isocurrencycode [Currency (Currency Code)] [Z] customerid.Account(accountnumber).Contact(msdynce_contactnumber) [Cus None None DESTINATION ENTITY Sales order headers V2 DESTINATION FIELD RequestedDeliveryDate [Requested delivery date] DeliveryAddress_City [City of DeliveryAddress_Country [Country/region of TotalDiscountAmount [Total discount amount] Description [Description] DiscountAmount [Discount amount] DeliveryAddress_AddressLine1 [First line of Name [Name] OrderDate [Order date] Status [Order status] DeliveryAddress_PostalCode [Postal code of SalesOrderld [Sales order ID] DeliveryAddress_AddressLine2 [Second line of DeliveryAddress_State [State of TotalAmount [Total amount] TotalAmount_CurrencyCode [Currency of Account Accountld [Account ID] Organization Organizationld [Organization ID] Account Organization_Organizationld [Organization ID] ](media/62560288682dce097c304d3fdc4d21d8.png)

 

![SOURCE ENTITY salesorders Source \> CDS Search SOURCE FIELD CDS ENTITY SalesOrder Destinatio MAP TYPE RequestedDeliveryDate [Requested delivery date] [E Account_AccountId [Account ID] [Z DeliveryAddress_City [City of DeliveryAddress_Country [Country/region of TotalAmount_CurrencyCode [Currency of [Z Description [Description] [Z DeliveryAddress_AddressLine1 [First line of [Z DeliveryAddress_PostalCode [Postal code of [Z SalesOrderld [Sales order ID] [Z DeliveryAddress_AddressLine2 [Second line of [Z DeliveryAddress_State [State of TotalAmount [Total amount] Name [Name] [E Account_AccountId [Account ID] OrderDate [Order date] None DESTINATION ENTITY Sales order headers V2 DESTINATION FIELD RequestedShippingDate [RequestedShippingDate] [Z OrderingCustomerAccountNumber [OrderingCustomerAccountNumber] [Z DeliveryAddressCity [DeliveryAddressCity] [Z DeliveryAddressCountryRegionld [DeliveryAddressCountryRegionId] [Z CurrencyCode [CurrencyCode] [Z CustomersOrderReference [CustomersOrderReference] [Z DeliveryAddressStreetNumber [DeliveryAddressStreetNumber] [Z DeliveryAddressZipCode [DeliveryAddressZipCode] [Z SalesOrderNumber [SalesOrderNumber] [Z DeliveryAddressStreet [DeliveryAddressStreet] [Z DeliveryAddressStateId [DeliveryAddressStateld] Order TotalAmount [Order TotalAmount] [Z SalesOrderName [SalesOrderName] [Z DeliveryAddressName [DeliveryAddressName] PaymentTerms8aseDate [PaymentTerms8aseDate] [Z IsDeliveryAddressOrderSpecific [IsDeliveryAddressOrderSpecific] ](media/20f6cc00326770aa1256d7c718819312.png)

 

### OrderLine

![SOURCE ENTITY salesorderdetails Source \> CDS Search SOURCE FIELD CDS ENTITY SalesOrderLine CDS \> Destination MAP TYPE requestdeliveryby [Requested Delivery Date] [Z] shipto_city [Ship To City] [Z] shipto_country [Ship To Country/Region] [Z] shipto_linel [Ship To Street 1] [Z] shipto_line2 [Ship To Street 2] extendedamount [Extended Amount] [Z] shipto_postalcode [Ship To ZIP/Postal Code] [Z] productid.productnumber [Existing Product (Product ID)] quantity [Quantity] [Z] salesorderid.ordemumber [Order (Order ID)] sequencenumber [Sequence Number] [Z] shipto_stateorprovince [Ship To State/Province] [Z] uomid.name [Unit (Name)] priceperunit [Price Per Unit] [Z] transactioncurrencyid.isocurrencycode [Currency (Currency Code)] None None [Z] transactioncurrencyid.isocurrencycode [Currency (Currency Code)] [Z] transactioncurrencyid.isocurrencycode [Currency (Currency Code)] [Z] description [Description] DESTINATION ENTITY CDS sales order lines DESTINATION FIELD RequestedDeliveryDate [Requested delivery date] DeliveryPostalAddress_City [City of DeliveryPostalAddress_Country [Country/region of DeliveryPostalAddress AddressLine1 [First line of DeliveryPostalAddress AddressLine2 [Second line of LineAmount [Line amount] DeliveryPostalAddress PostalCode [Postal code of Product_Productld [Product ID] Quantity [Quantity] SalesOrder_SalesOrderld [Sales order ID] Sequence [Sequence] DeliveryPostalAddress State [State of Quantity_UOM [Unit of Measure of UnitPrice [Unit price] LineAmount CurrencyCode [Currency of SalesOrder_Organization Organizationld [Organization ID] Product_Organization Organizationld [Organization ID] DiscountAmount_CurrencyCode [Currency of UnitPrice CurrencyCode [Currency of Description [Description] ](media/1e64b1597909498542b3f25911be3f86.png)

 

![SOURCE ENTITY salesorderdetails Source \> CDS Search SOURCE FIELD CDS ENTITY SalesOrderLine Destinatio MAP TYPE RequestedDeliveryDate [Requested delivery date] [Z] DeliveryPostalAddress_City [City of DeliveryPostalAddress_Country [Country/region of [Z] Description [Description] [Z] DeliveryPostalAddress_AddressLine1 [First line of [Z] DeliveryPostalAddress_PostalCode [Postal code of [Z] Product Productld [Product ID] Quantity [Quantity] [Z] SalesOrder_SalesOrderld [Sales order ID] [Z] DeliveryPostalAddress_AddressLine2 [Second line of Sequence [Sequence] [Z] DeliveryPostalAddress_State [State of Quantity_UOM [Unit of Measure of LineAmount [Line amount] UnitPrice [Unit price] None None [Z] ProductName [Product name] [Z] DeliveryPostalAddress_City [City of DESTINATION ENTITY CDS sales order lines DESTINATION FIELD REQUESTEDRECEIPTDATE [REQUESTEDRECEIPTDATE] DELIVERYADDRESSCITY [DELIVERYADDRESSCITY] DELIVERYADDRESSCOUNTRYREGIONISOCODE [DELIVERYADDRESSCOUNTRY LINEDESCRIPTION [LINEDESCRIPTION] DELIVERYADDRESSSTREETNUMBER [DELIVERYADDRESSSTREETNUMBER] DELIVERYADDRESSZIPCODE [DELIVERYADDRESSZIPCODE) PRODUCTNUM3ER [PRODUCTNIJMBER] ORDEREDSALESQUANTITY [ORDEREDSALESQUANTITY] SALESORDERNUMBER [SALESORDERNUMBER] DELIVERYADDRESSSTREET [DELIVERYADDRESSSTREET] LINECREATIONSEQUENCENUMBER [LINECREATIONSEQUENCENUMBER] DELIVERYADDRESSSTATEID [DELIVERYADDRESSSTATEID] SALESUNlTSYM30L [SALESUNITSYMBOL] LINEAMOUNT [LINEAMOUNT] SALESPRICE [SALESPRICE] SHIPPINGSITEID [SHIPPINGSITEID] SHIPPINGWAREHOUSEID [SHIPPINGWAREHOUSEID] PRODUCTNAME [PRODUCTNAME] DELIVERYADDRESSDESCRIPTION [DELIVERYADDRESSDESCRIPTION] ](media/bb57a16aa4dccea0a99509d23cd7fd5f.png)
