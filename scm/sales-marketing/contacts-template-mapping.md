Contact (Contacts) and Contact (Customers)
==========================================

Template and Task
-----------------

The following templates and underlying tasks are used to synchronize products
from Microsoft Dynamics 365 for Sales (Sales) to Microsoft Dynamics 365 for
Finance and Operations, Enterprise edition.

Name of template:

-   Contacts to Contact (Sales to Fin and Ops)

-   Contacts to Customer (Sales to Fin and Ops)

Name of task in project:

-   Contacts

-   ContactToCustomer

 

Sync tasks required prior to Contact sync: Accounts (Sales to Fin and Ops)

 

Entity sets
-----------

| **Sales** | **CDS** | **Finance and Operations** |
|-----------|---------|----------------------------|
| Contacts  | Contact | CDS Contacts               |
| Contacts  | Account | Customers V2               |

 

 

Entity flow
-----------

**Contacts** are managed in Sales and synchronized to CDS and Finance and
Operations.

 

A **Contact** in Sales can become either a **Contact** in CDS and Finance and
Operations, or it can become an **Account** in CDS and **Customer** in Finance
and Operations. When determining whether a given contact should be picked up in
Sales for synchronization to CDS and Finance and Operations, for example,
**Contacts** (Sales) -\> **Contact** (CDS) -\> **Contacts** (Operations)
synchronization, the system looks at the following properties on **Contact** in
Sales:

 

Sync to **Account** in CDS and **Customer** in Finance and Operations:

**Contacts** with **Is Active Customer = Yes**

 

Sync to **Contact** in CDS and **Contact** in Finance and Operations:

**Contacts** with **Is Active Customer = No** and **Company** (Parent
Account/Contact) pointing to an **Account** (not a Contact)

 

Prospect to cash solution for Sales 
------------------------------------

A new field **Is Active Customer** is added to the **Contact**. The purpose of
this field is to differentiate between contacts with and without sales activity.
Only contacts with related quotes, orders, or invoices have **Is Active Customer
= Yes** and synced to Finance and Operations as **Customers**.

 

A new field **IsCompanyAnAccount** is added to the **Contact**. The purpose of
this field is to identify contacts linked to a **Company (Parent
Account/Contact)** of type **Account**. This information is used to identify
**Contacts** who should be synced to Finance and Operations as **Contacts**.

 A new field **Contact Number** field is added to the **Contact** entity to
ensure a natural and unique key for the integration. When creating a new
contact, the **Contact Number** is automatically generated using a number
sequence starting with CON followed by an increasing number sequence and ending
with a suffix of 6 characters. For example, CON-01000-BVRCPS.

 

When the integration solution for Sales is added to Sales, an upgrade script
populates **Contact numbers** to existing **Contacts** using the number sequence
discussed in the previous section. The upgrade script also populates the **Is
Active Customer** field for contacts with any sales activity set to **Yes**.

 

In Finance and Operations 
--------------------------

Contacts are tagged with the property I**sContactPersonExternallyMaintained** to
indicate that the given contact is maintained externally, in this case from
Sales.

 

 

Preconditions and mapping setup
-------------------------------

###  Contact to Contact

-   Update the **CDS Organization ID in Source -\> CDS**

    -   Template value for **Organization_OrganizationId [Organization ID]** is
        defaulted to ORG001.

    -   Template value for **PrimaryAccount_Organization_OrganizationId
        [Organization ID]** is defaulted to ORG001.

-   **Address Country region code** is required in Finance and Operations. To
    avoid sync errors, you can default a value in the **CDS -\> Operations
    mapping** that is used if the field is left blank in Sales.

    -   Template value for **PrimaryAddressCountryRegionISOCode** is defaulted
        to USA.

-   Ensure that the following value exist in Finance and Operations. If the
    information is not desired in Finance and Operations, the mapping can be
    remove from **CDS -\> Destination** mapping.

    -   Field name in Finance and Operations: **Decision**

        -   Mapping: PrimaryAccountRole = DecisionMakingRole

### Contact to Customer

-   Update the **CDS Organization ID in Source -\> CDS**

    -   Template value for **Organization_OrganizationId [Organization ID]** is
        defaulted to ORG001.

-   **Address Country region code** is required in Finance and Operations. Fo
    avoid sync errors, you can default a value in the **CDS -\> Operations
    mapping** that is used if the field is left blank in Sales.

    -   Template value for **PrimaryAddressCountryRegionISOCode** is defaulted
        to USA.

-   **CustomerGroup** is required in Finance and Operations. To avoid sync
    errors, you can default a value in the **CDS -\> Operations mapping** that
    is used if the field is left blank in Sales.

    -   Template value for **CustomerGroupId** is defaulted to 10.

-   It is possible to add the following mappings from **CDS -\> Destination** to
    reduce the manual updates needed in Finance and Operations. This can be done
    with a default or a **ValueMap** from for example, **Country/Region** or
    **City**.

    -   **SiteId** - Site can also be defaulted on Products in Finance and
        Operations. Site is required to generate Quote and Sales order in
        Finance and Operations.

        -   Template value for **SiteId** is not defined.

    -   **WarehouseId** - Warehouse can also be defaulted on the Products in
        Finance and Operations. Warehouse is required to generate Quote and
        Sales order in Finance and Operations.

        -   Template value for **WarehouseId** is not defined.

    -   **LanguageId** - Language is required to generate Quote and Sales order
        in Finance and Operations.

        -   Template value for **LanguageId** is defaulted to en-us. 

 

 

Template mapping in Data integrator
-----------------------------------

### Contact to Contact

![ENTITY \> cos Search SOURCE CDs CDS \> Num,'xl Cal's) [Statu [Birth-Oy] 1: City] \_cuntry 1: [Email 21 [Email] 1: 21 [Gænder] [Fict Name not Mails] [Marital Status) [Middle N.rne] [Mobil. 1: Code] [Role] jobtitle [Job [Lut Numinc.ntact Number)) DESTNATION ENT'TY CDS type] [Is c.ntact Is contut Stytu s [Stat") [Organizat& D] [Organizat& D] [Birth-Ote [City of [Cm ntry/—iU. of 10}) [F.rst of of [Z [Gim of {01] Marital Satus [Writ—I stat") NarreMiddleName [Middle of primary] of URL] ](media/7662e3908e0a85c91bf202eb4a4613c5.png)

 

![scuRCE ENTITY CDS Search sougcE [City of {OJI identif\*r] [Myrityl of 10}] [Email of [Middle [Pa rty type] [Prim-My role] [State of Status [St REI of CDs DESTNATION ENT'TY CDS [ZrimMyA±ræsCityl Writ—IStatus [MaritalStätÆl NotE [ N otEl ZrimMyAZdræsStræ ZrimMyAZdræsZipCcde ZrimMyAZdræsStated Fri m. ryLl ](media/43412ba0de5b53451e5b42d4fbe98f4d.png)

 

Contact to Customer

![souRCE ENTITY cos CDS \> COS ENTITY MAP TYPE [First birth-date [Gender] [List Nam—I fami13Ætätu"oee [Maritäl St—tusl [Middle 2] not IDO not Calls] [Mobile [Address 1: City) [Address 1] [Address 1: 2] æ±itlimit Limit] statec±e [St—tu [Em-ill [Business website] Code)] de"ription [Dé"riptionl Code)] full name [Full DESTINATION ENTITY DESTINATION Birthdate [Birthdate) Gender of [Maritäl status] [Middle of Em\*ilAltemate 021 031 Mailing [City of [Cuntry/reg& of MailingPNtälAZdræs_State [State of {0}1 [FiÆt line of IO)] [Organiütion IDI [Post—I wee of (O" limit [Acæ.nt ID] Status [Email prim—ry] WebsitelJRI\_ [Website %rtyType [Party type] of [Org-netion ](media/539409a480db6de0f23f36e9f52be249.png)

 

![SOU RCE ENTITY CDS ENTITY Source CDS CDS Destination Search SOURCE FIELD PersonName_MiddIeName [Middle name of {011 PersonName_Surname [Surname of Mailing PostalAddress_Country [Country/region of [State of [First line of {0}1 [Postal code of {0)1 Accountld [Account ID) Organization Name [Organization namel PartyType [Patty type) EmailPrimary [Email primary) PhoneFax [Phone fax] PhonePrimary [Phone primary] WebsiteLlRL [Website URL) SilesCurrencyCode [Sales currency code] None None None PersonName_GivenName [Given name of [City of CreditLimitAmount [Credit limit amount] Description [Description) None Accountld [Account ID) DESTINATION ENTITY DESTINATION FIELD PersonMiddIeName [PersonMiddIeNamel PersonLastName [PersonLastName] AddressCountryRegionISOCode [AddressCountryRegionISOCodel AddressState [AddressState] AddressStreet [AddressStreetl AddressZipCode [AddressZipCode] CustomerAccount [CustomerAccountl OrganizationName [OrganizationNamel PartyType IPartyType) PrimaryContactEmaiI [PrimaryContactEmaiI] PrimaryContactFax [PrimaryContactFax] PrimaryContactPhone [PrimaryContactPhone] PrimaryContactlJRL [PrimaryContactURLl SalesCurrencyCode [SalesCurrencyCode] AddressLocationRdes [AddressLocationPdes) CustomerGroupId [CustomerGroupIdl Languageld [Languageld] PersonFirstName [PersonFirstNamel AddressCity [AddressCityl CreditLimit [CreditLimitl Sales Memo [SalesMemol IsExterraItyMaintained [IsExternaIIyMaintainedl PartyNumber [PartyNumber] ](media/0bed57950c9405c6e61d680f1daa727c.png)
