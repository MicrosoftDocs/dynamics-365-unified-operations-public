This topic describes how to set up and work with the functionality for creation
and sending sales and project invoices in electronic format (FatturaPA).  
  
Effective June 6, 2014, the Italian Ministries, the Tax Authorities (Agenzia
delle Entrate, Agenzia del Demanio, Agenzia del Territorio, Agenzia delle
Dogane), and various national social security and welfare entities that are
listed by the Istituto Nazionale di Statistica (Istat) (for example, INARCASSA,
cassa forense, cassa geometri, cassa del notariato) will no longer be entitled
to accept paper invoices. Additionally, three months after the June 6 date,
these same groups will no longer process payments (even partly) until an invoice
is submitted in electronic format.

In addition the format for electronic invoices "FatturaPA" version 1.2 can be
used for all types of businesses, including public administrations and private
companies and professionals.  
Specifically, the invoices in question must be in .xml format, must be endorsed
by using a qualified or digital electronic signature, and must be transmitted
through an interchange data system or an authorized intermediary on the
following websites:

-   Italian: <http://www.fatturapa.gov.it/export/fatturazione/it/index.htm>

-   English: <http://www.fatturapa.gov.it/export/fatturazione/en/index.htm?l=en>

Setup
-----

>   Before starting work with the electronic invoice functionality, it is
>   necessary to fulfil the following settings:

### Accounts receivable parameters

Select the configurations which are used for creation electronic invoices xml
files for Sales and Free text invoices, Sales and Free text credit notes,
Project invoice, Project credit notes (**Accounts receivable \> Setup \>
Accounts receivable parameters**, **Electronic documents** tab).

![](media/61978787ad8b1b2cc43951c15e6d87a9.png)

>   Note. Before selection it is necessary to import the configurations.

>   See [Download Electronic reporting configurations from Lifecycle
>   Services](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/analytics/download-electronic-reporting-configuration-lcs).

E-Invoices parameters

**Accounts receivable \> Setup \> Electronic invoice parameters**)

Use these parameters to specify business scenarios and company specific data
(**General**, **Company information** and **Art. 2250 Civil code registratio**n
tabs).

On **Number sequences** tab fill in number sequences for e-invoice file number
and transmission number.

### Customers 

-   Authority office (**Accounts receivable \> Customers \> All customers,**
    open a customer in **Edit** mode**, Sales demographics** FastTab**,
    Authority office** field).

>   The system uses this field value for defining the type of communication (B2G
>   or B2B): if the length of this value is 6 then the customer will be
>   considered as public administration (Transmission Format is **FPA12**) and
>   if the length of this value is 7 then this customer will be considered as
>   private companies or professionals (Transmission Format is **FPR12**). In
>   these both cases the system fills in the CodiceDestinatario tag (xml file)
>   with this field value.

![](media/0c7bf0e30d7c567b33f1239539d4c3a0.png)

>   If **Authority office** field value is empty, the system considers a
>   customer as a private company or professional (Transmission Format is
>   **FPR12**) and fills in the CodiceDestinatario tag (xml file) with
>   **0000000**.

>   In this case a certified e-mail address (**PEC**) should be entered on
>   Customer level.

>   To do this:

-   Set up Electronic document property types (**Accounts receivable \> Setup \>
    Electronic document property types**).

>   Note. The **Description** field (left) is filled in automatically when a
>   user is filling **Group description** and **Description** (right) fields.

>   Use **Applicability** button and fill in CustTable in the **Table name**
>   field

![](media/9682e5f4c1e943f95fd4d8394aa4a574.png)

  
After this setting it is possible to fill in **Electronic document properties**
for a customer (**Accounts receivable \> Customers \> All customers, Customer**
tab, **Properties**). Fill in **Value** field. The system fills in the
**PECDestinatario** tag with this value.

-   Activate automatic creation of e-invoices  
    **Accounts receivable \> Customers \> All customers,** open a customer in
    **Edit** mode**, Invoice and delivery** FastTab**, E-INVOICE** field
    group**, eInvoice register** option.

>   If this option is set to **Yes**, the system automatically creates the
>   record in **Electronic customer invoices** page list (see Overview of
>   electronic invoices page.)

![](media/e4b1537f04c5879042ccee49f204549b.png)

Digital Certificates

Open **Accounts receivable \> Setup \> Electronic invoice digital certificates**

Functionality can perform electronic singing of e-Invoices by using either a
**Company** certificate or **User** certificate.

![](media/2ebc2d6ff94ecfac79495f941a250f3b.png)

Each [FatturaPA
file](http://www.fatturapa.gov.it/export/fatturazione/en/b-2.htm) that is
transmitted to the [Exchange
System](http://www.fatturapa.gov.it/export/fatturazione/en/sdi.htm) must be
signed by using a qualified signature certificate by the party that is issuing
the invoice.  
A qualified signature certificate may be obtained from one of the certifiers in
the [list of authorized
certifiers](http://www.digitpa.gov.it/firma-digitale/certificatori-accreditati).  
  
The current release supports the **XAdES-BES** signature format.  
To be able to support FatturaPA you must perform the following steps:

-   Install and configure digital certificates that have private and public keys
    in Certificate Server to the **Personal** node on client computers.  
      
    Note You can do this by using standard Windows functionality.

-   Define Company-level certificates and User-level certificates, as required.

Destination for xml file
------------------------

If it is necessary to output xml files to specified place (for example,
SharePoint folder) when invoices are posting (**Print invoice** option must be
set to **Yes**), first set up a document type (**Organization administration \>
Document management \> Document types**) and then set up a destination
(**Organization administration \> Electronic reporting \> Electronic reporting
destination**) (see setting details under the links [Configure document
management](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/organization-administration/configure-document-management)
and [Electronic reporting (ER)
destinations](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations)).

Note. **Print invoice** option must be set to **Yes** and destination is set up
the e-invoice record for this invoice automatically is set to **Sent** status
**(**see Overview of electronic invoices page)**.**

Example of setup:

Document type

![](media/8135efc23a86ab6e3cce18968f51bbc6.png)

Destination for **Sales invoice (IT)** format:

![](media/878f926d89de95507701ba1fcd20e983.png)

Overview of electronic invoices page 
-------------------------------------

To overview all customer e-invoices and fulfil different actions open
**Electronic customer invoices** page list (**Accounts receivable \> Invoices \>
E-invoices \> Electronic invoices**).

In this page list a user can:

-   Select invoice manually by different criteria (Select button). This function
    is useful if the **eInvoice register** option is not set to **Yes** in
    customers.

-   Create xml files, digital signature for selected invoices and send them

-   Export the selected invoice to xml file.

-   Overview details of the electronic invoice.

Note. The similar page list with the same functions is in **Project management
and accounting \> Project invoices \> E-invoices \> Electronic invoices.**

![](media/840e8c82e59042cf282bbdc621e8022f.png)

 
