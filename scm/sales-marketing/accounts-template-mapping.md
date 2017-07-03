Accounts (Customers)
====================

Template and task
-----------------

The following templates and underlying tasks are used to synchronize products
from Microsoft Dynamics 365 for Sales (Sales) to Microsoft Dynamics 365 for
Finance and Operations, Enterprise edition (Finance and Operations).

-   Name of template: Accounts (Sales to Fin and Ops)

-   Name of task in project: Accounts - Account - Customers

 

Sync tasks required prior to Account / Customer sync: None

 

Entity set
----------

| **Sales** | **CDS** | **Finance and Operations** |
|-----------|---------|----------------------------|
| Accounts  | Account | Customers                  |

 

Entity flow
-----------

**Accounts** are managed in Sales and synchronized to Finance and Operations as
**Customers** where they are marked with **Is Externally Maintained = Yes**.
This is done to keep track of which **Customers** originate from Sales. During
invoicing, this information is used to filter invoices that sync to Sales.

 

Prospect to cash solution for Sales 
------------------------------------

**Account Number** is made visible on the **Account** form and made into a
natural and unique key to support the integration. The natural key feature of
the CRM solution may affect customers who already use the **Account Number**
field, but not use the unique **Account Numbers per account**. Currently, the
integration solution does not support this case.

 

When creating a new account, if the **Account Number** does not already exist,
it is automatically generated using a number sequence starting with ACC followed
by an increasing number sequence and ending with a suffix of 6 characters, for
example, ACC-01000-BVRCPS.

 

When the integration solution for Sales is applied, an upgrade script populates
**Account Numbers** for existing accounts in Sales. When there are no **Account
Numbers**, the above number sequence is used.

 

Preconditions and mapping setup
-------------------------------

-   **CustomerGroupId** must be updated to a valid value in Finance and
    Operations. This can be defaulted or set with **ValueMap**.

    -   Template value is defaulted to 10.

-   **Address country region code** is required in Finance and Operations. To
    avoid sync errors, you can default a value that is used if the field is left
    blank in Sales.

    -   Template value for **AddressCountryRegionISOCode** is defaulted to USA.

    -   Template value for **DeliveryAddressCountryRegionISOCode** is defaulted
        to USA.

-   It is possible to add the following mappings from **CDS-\>Destination** to
    reduce the manual updates needed in Finance and Operations. This can be done
    with a default or a **ValueMap** from, for example, Country/Region or City.

    -   **SiteId** - Site is required to generate **Quote** and **Sales order
        lines** in Finance and Operations. It can default from either the
        product, or the customer from the order header.

        -   Template value for **SiteId** is defaulted to 1.

    -   **WarehouseId** - Warehouse is required to process **Quote** and **Sales
        order lines** in Finance and Operations. Warehouse can be defaulted from
        either the product, or the customer from the order header in Finance and
        Operations.

        -   Template value for WarehouseId is defaulted to 13.

    -   **LanguageId** - Language is required to generate **Quote** and **Sales
        order** in Finance and Operations and defaults to the order header from
        the customer.

        -   Template value for **LanguageId** is defaulted to en-us.

-   Update the **CDS Organization ID Organization_OrganizationId** in **Source
    -\> CDS**.

    -   Template value is defaulted to ORG001.

Template mapping in Data integrator
-----------------------------------

**Note:**

**Payment terms**, **Freight terms**, **Delivery terms**, **Shipping method**,
and **Delivery mode** are not included in the default mappings. Mapping of these
fields requires value mapping to be set up, which is specific to the data in the
organizations between which the entity is synchronized.

![Machine generated alternative text: ENVY CDS æditlimit [Cr«lit Limit] [N. of 1: cir„l [Em—il 21 [Em—ill [Mai n [Stat"] Sym cyid. [Add 2: 21 2: City) 2: ZIP/PætAl Code) 2: CDs ENTITY DESTNATZN ENTITY DESTINATION limit El Accuntld D] [City of untact [ PMty type] [Country/ —Y of of Satoh Id [Sate of Stätus [St—tus] (Stock entity] El LRJ_I [Sal E cog [C—-cy of 10}] line of [City of of of {03] [Sate of ](media/f8086e426e33f0e277b2ec66f4fa777e.png)

![Machine generated alternative text: SOu ENVY limit my code) [A cuunt [St—te 'f E [Organiät&. E [ Organiät&. [CO of Sh ippirg ntry/rez CDs ENTITY ENTITY DESTINATION [CrElitLimitl of {OJI [Add prim. rj•CU.tætLlRL] El Sited [Sited] of {OJI [St—te 'f [ Organiät&. ](media/22d7a598dca7a102471abaa8f27676bd.png)
