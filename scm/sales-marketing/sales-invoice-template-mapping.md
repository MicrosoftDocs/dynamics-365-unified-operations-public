Sales invoice headers and lines
===============================

Template and Task
-----------------

The following templates and underlying tasks are used to synchronize products
from Microsoft Dynamics 365 for Finance and Operations, Enterprise edition to
Microsoft Dynamics 365 for Sales (Sales).

Name of template: Sales Invoices (Fin and Ops to Sales)

Name of task in project:

-   SalesInvoiceHeader

-   SalesInvoiceLine

 

Sync tasks required prior to Sales invoice header and lines sync:

-   Products

-   Accounts (if used)

-   Contacts (if used)

-   Sales order header and lines

 

 
-

Entity set
----------

| **Finance and Operations**                            | **CDS**          | **Sales**      |
|-------------------------------------------------------|------------------|----------------|
| Externally maintained customer sales invoice headers  | SalesInvoice     | Invoices       |
| Externally maintained customer sales invoice lines    | SalesInvoiceLine | InvoiceDetails |

 

Entity flow
-----------

**Sales invoices** are created in Finance and Operations and synchronized to
Sales.

 

Prospect to cash solution for Sales
-----------------------------------

An **Invoice Number** field is added to the **Invoice** entity and displayed on
the form.

 

The **Create Invoice** button on the **Sales order** form is hidden since
invoices will be created in Finance and Operations and synced to Sales. The
invoice form is non-editable since invoices will be synced from Finance and
Operations.

 

The **Sales order status** changes automatically to **Invoiced** once the
related invoice from Finance and Operations has synchronized to Sales. Also, the
**Owner** of the sales order from which the invoice was created is assigned as
the **Owner** of the invoice. This gives the **Owner** of the sales order the
ability to view the invoice.

 

Preconditions and mapping setup
-------------------------------

Before synchronizing invoices it is important to update Sales with the following
setting:

Under **Settings \> Administration \> System settings \> Sales** ensure that
**Use system prizing calculation system** is set to No. This is done to ensure
that the item price from Operations invoice is used when generating the invoice
in Sales.

###  InvoiceHeader

-   Update the mapping for **CDS Organization ID in Source -\> CDS.**

    -   Template value for **SalesOrder_Organization_OrganizationId** is
        defaulted to ORG001.

    -   Template value for **Account_Organization_OrganizationId** is defaulted
        to ORG001.

    -   Template value for **Organization_OrganizationId** is defaulted to
        ORG001.

-   Ensure that the needed mapping exist in **Source -\> CDS** for
    **InvoiceCountryRegionId** to **BillingAddress_Country**

    -   Template value is **ValueMap** with a number of Countries mapped.

-   **Price list** is required to create invoices in Sales. Update the
    **ValueMap** in **CDS -\> Destination** for **pricelevelid.name [Price List
    Name]** to the **Price list** used in Sales per currency. You can either
    default to a single **Price list** or use **ValueMap** if you have **Price
    lists** in multiple currencies.

    -   Template value for **pricelevelid.name [Price List Name]** is
        **ValueMap** based on Currency:

    -   usd : CRM Service USA (sample). 

### InvoiceLine

-   Ensure that the needed mapping exists in **Source -\> CDS for Unit of
    measure.**

-   Ensure that the needed **ValueMap** for **SalesUnitSymbol** in Finance and
    Operations exists in the **Source -\> CDS mapping.**

    -   Template value with **ValueMap** is defined for **SalesUnitSymbol to
        Quantity_UOM**.

-   Update the mapping for **CDS Organization ID in Source -\> CDS.**

    -   Template value for **SalesInvoicer_Organization_OrganizationId** is
        defaulted to ORG001.

    -   Template value for **Product_Organization_OrganizationId** is defaulted
        to ORG001.

>    

 

Template mapping in Data integrator
-----------------------------------

**Note:**

**Payment terms**, **Freight terms, Delivery terms, Shipping method,** and
**Delivery mode** are not part of the default mappings. Mapping of these fields
requires value mapping to be set up, which is specific to the data in the
organizations between which the entity is synchronized.

![](media/d38903f4d5ce687120cc0daba89bc6c8.png)

![](media/30d4db74ce47aebf3da2c061a75bea2a.png)

![](media/696bc771c5465e6b13f0088b1851713b.png)

![](media/550a4495ad6430efc162e0a53f43cc6b.png)
