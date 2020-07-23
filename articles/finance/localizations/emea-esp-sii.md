---
# required metadata

title: Immediate Supply of Information on VAT (Suministro Inmediato de Información del IVA, SII)
description: This topic describes how to set up and use Microsoft Dynamics 365 Finance to interoperate with the SII system of Spain.
author: liza-golub
ms.date: 07/23/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Spain
# ms.search.industry: 
ms.author: elgolu
ms.search.validFrom: 2017-12-31
ms.dyn365.ops.version: 7.3

---

# Immediate Supply of Information on VAT (Suministro Inmediato de Información del IVA, SII)

[!include [banner](../includes/banner.md)]

According to R.D. 596/2016 in Spain, a new value-added tax (VAT) management
system that is based on the Immediate Supply of Information on VAT (Suministro
Inmediato de Información del IVA [SII]) allows for a two-way, automated
relationship between the Spanish Tax Agency (AEAT) and the taxpayer. In the rest
of this topic, this system will be referred to as the SII system. Starting July
1, 2017, taxpayers who are subject to SII, and those who voluntarily adopt it,
must send details of their billing records within four days through online
filing on the AEAT website.

For more information about the SII system of Spain, see the [Immediate Supply of
Information on VAT (SII) official
website](https://www.agenciatributaria.es/AEAT.internet/en_gb/Inicio/La_Agencia_Tributaria/Campanas/Suministro_Inmediato_de_Informacion_en_el_IVA__SII_/Suministro_Inmediato_de_Informacion_en_el_IVA__SII_.shtml).

## Overview

This topic describes how to set up and use Microsoft Dynamics 365 Finance to
interoperate with the SII system of Spain. It includes information about how to
complete the following tasks:

-   Import Electronic reporting (ER) configurations.

-   Set up Electronic messaging (EM) functionality.

-   Set up reporting to the SII system.

-   Work with EM functionality to interoperate with SII system.

## Import ER configurations

To prepare Finance to interoperate with the SII system, you must import the
following ER configurations.

| **Number** | **Configuration name**                  | **Configuration type** |
|------------|-----------------------------------------|------------------------|
| **1**      | **Invoices Communication Model**        | **Model**              |
| 2          | SII model mapping                       | Model mapping          |
| 3          | SII Invoice Issued Format (ES)          | Format                 |
| 4          | SII Invoice Received Format (ES)        | Format                 |
| 5          | SII Intra-Community Format (ES)         | Format                 |
| 6          | SII Customer Payment Format (ES)        | Format                 |
| 7          | SII Vendor Payment Format (ES)          | Format                 |
| 8          | SII Collection in Cash Format (ES)      | Format                 |
| **9**      | **Electronic Messages framework model** | **Model**              |
| 10         | ES SII import model mapping             | Model mapping          |
| 11         | SII import format (ES)                  | Format                 |

**Important:** Be sure to import the most recent versions of these
configurations. The version description usually includes the number of the
Microsoft Knowledge Base (KB) article that explains the changes that were
introduced in the configuration version.

**Note**: After all the ER configurations from the preceding table are imported,
set the **Default for model mapping option** to **Yes** for the **SII model
mapping** and **ES SII import model mapping** configurations.

For more information about how to download ER configurations from the Microsoft
global repository, see [Download ER configurations from the Global
repository](../../dev-itpro/analytics/er-download-configurations-global-repo.md).

## Import a package of data entities that includes a predefined EM setup

Electronic message functionality is provided to maintain the different processes
that are used in electronic reporting for different document types. For more
information about electronic messages, see [Electronic
messaging](https://docs.microsoft.com/dynamics365/finance/general-ledger/electronic-messaging).

The process of setting up the electronic message functionality to interoperate
with the SII system has many steps. Because the names of some predefined
entities are used in the ER configurations, it's important that you use a set of
predefined values that are delivered in a package of data entities for the
related tables, and that you import the ER configurations before you import the
data entities.

1.  In [Microsoft Dynamics Lifecycle Service
    (LCS)](https://lcs.dynamics.com/v2), go to the Shared asset library, and
    select the **Data package** asset type.

2.  In the list of data package files, find and download **ES SII setup.zip**.

![](media/emea-esp-sii-data-package-file.png)

3.  After the file is downloaded, open Finance, and select the company that you
    will interoperate with the SII system from.

4.  Go to **Workspaces \> Data management**.

5.  In the **Data management** workspace, go to **Framework parameters \> Entity
    settings**, and select **Refresh entity list**. Wait for confirmation that
    the refresh has been completed. For more information about how to refresh
    the entity list, see [Entity list
    refresh](https://docs.microsoft.com/dynamics365/dev-itpro/data-entities/data-entities#entity-list-refresh).

6.  Validate that the source data and target data are correctly mapped. For more
    information, see [Validate that the source data and target data are mapped
    correctly](https://docs.microsoft.com/dynamics365/dev-itpro/data-entities/data-import-export-job#validate-that-the-source-data-and-target-data-are-mapped-correctly).

7.  Before the data entities are used for the first time to import the data from
    the package, sync the mapping of the source data and target data. In the
    list for the package, select a data entity, and then, on the Action Pane,
    select **Modify target mapping**.

8.  Above the grid for the package, select **Generate mapping** to create a
    mapping from scratch, and then save the mapping.

9.  Repeat steps 7 and 8 for every data entity in the package before you start
    the import.

>   For more information about data management, see [Data management
>   overview](https://docs.microsoft.com/dynamics365/dev-itpro/data-entities/data-entities-data-packages).

You must now import data from the **ES SII setup.zip** file into the
    selected company. In the **Data management** workspace, select **Import**,
    specify a **Group name**, select **Add file**, and then, in the drop-down
    dialog box, set the **Source data format** field to **Package** and set the
    **Source data format** field to **Package**.

10.  Select **Upload and add**, select the **ES SII setup.zip** file on your
    computer, and upload it.

11.  After the data entities are uploaded, on the Action Pane, select **Import**.

![](media/emea-esp-sii-data-entities-upload.png)

You will receive a notification in **Action center**, or you can manually
refresh the page to view the progress of the data import. When the import is
completed, the **Execution summary** page shows the results.

After data entities are imported, you will find two types of electronic message
processing: **SII** and **CollectionInCash**. This processing contains almost
all the setup that is required in your legal entity.


| **Processing**   | **Name**                                                   | **Description**                                                                                                                                                                                                                                                                                                                                |
|------------------|------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SII              | Immediate Supply of Information (SII): Invoices, Payments  | This processing supports interoperation with the SII system to submit information about customer and vendor invoices, additional information about payments that are related to customer and vendor invoices where the **Special scheme code** value is set to **07**, and additional information that is related to intra-community invoices. |
| CollectionInCash | Immediate Supply of Information (SII): Collections in cash | This processing supports interoperation with the SII system to submit information about collections in cash reporting. This information is grouped by customer payment amounts that are evaluated from a specific account that is set up as a cash account, and that exceed the amount of 6,000 euros during the reporting period.             |

To review the imported processing, go to **Tax \> Setup \> Electronic messages
\> Electronic message processing**.

The electronic message processing from the previous table works with the
following electronic message item types.

| **Electronic messages item type** | **Description**                                                                                                                                                                                                                                                                                                                                                                                                               | **Processing**   |
|-----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|
| FacturasProveedores               | **Vendor invoices**                                                                                                                                                                                                                                                                                                                                                                                                           | SII              |
| FacturasСliente                   | **Customer invoices**                                                                                                                                                                                                                                                                                                                                                                                                         | SII              |
| PagosCliente                      | **Customer payments:** Message items of this type are created for previously created customers invoices where the **Special scheme code** value is set to **07**.                                                                                                                                                                                                                                                             | SII              |
| PagosProveedores                  | **Vendor payments:** Message items of this type are created for previously created vendor invoices where the **Special scheme code** value is set to **07**.                                                                                                                                                                                                                                                                  | SII              |
| OperacionesIntracomunitarias      | **Intra-community operations:** Message items of this type are created for previously created vendor invoices that meet specific intra-community criteria. For more information, see the description in the [Algorithm of to define the TipoOperacion (Intra-community operation type) additional field](#algorithm-to-define-the-tipooperacion-intra-community-operation-type-additional-field) section later in this topic. | SII              |
| CobrosEnMetálico                  | **Collections in cash records:** Message items of this type are filled in from preliminary information that is collected about payment transactions that are posted from customers to specific cash accounts.                                                                                                                                                                                                                 | CollectionInCash |

To review the imported electronic message item types, go to **Tax \> Setup \>
Electronic messages \> Message item types**.

## Set up the internet address and certificates for the SII system

To interoperate with the SII system, you must use a security certificate that is
provided by AEAT. There are two options for storing this sensitive data:

-   Azure Key Vault storage

-   Local storage

For more information about how to set up Key Vault, see [Setting up Azure Key
Vault
Client](https://support.microsoft.com/help/4040305/setting-up-azure-key-vault-client)
and [Maintaining Azure Key Vault
storage](https://support.microsoft.com/help/4040294/maintaining-azure-key-vault-storage).

1.  Go to **System administration \> Setup \> System parameters**.

2.  Set the **Use advanced certificate store** option to **No** to store
    sensitive data locally. Set the option to **Yes** to use Key Vault storage.

3.  If you set the **Use advanced certificate store** option to **Yes**, go to
    **System administration \> Setup \> Key Vault parameters** to set up the Key
    Vault parameters.

4.  Go to **Tax \> Setup \> Parameters \> Electronic messages \> Web service
    settings**.

5.  Enter the following information to define the internet address for web
    services.

| **Web service name** | **Description**                                                                                                                                                                                                                 | **Testing internet address**                               |
|----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------|
| Cust invoice         | This web service is provided by AEAT. It's used to submit information about issued invoices, and it sends back a response that contains information about invoice processing on the SII system side.                            | `https://www7.aeat.es/wlpl/SSII-FACT/ws/fe/SiiFactFEV1SOAP`  |
| Vend invoice         | This web service is provided by AEAT. It's used to submit information about received invoices, and it sends back a response that contains information about invoice processing on the SII system side.                          | `https://www7.aeat.es/wlpl/SSII-FACT/ws/fr/SiiFactFRV1SOAP`  |
| Intra-community      | This web service is provided by AEAT. It's used to submit information about intra-community invoices, and it sends back a response that contains information about invoice processing on the SII system side.                   | `https://www7.aeat.es/wlpl/SSII-FACT/ws/oi/SiiFactOIV1SOAP`  |
| Cust payment         | This web service is provided by AEAT. It's used to submit information about payments from customers for specific invoice types, and it sends back a response that contains information about processing on the SII system side. | `https://www7.aeat.es/wlpl/SSII-FACT/ws/fe/SiiFactCOBV1SOAP` |
| Vend payment         | This web service is provided by AEAT. It's used to submit information about payments to vendors for specific invoice types, and it sends back a response that contains information about processing on the SII system side.     | `https://www7.aeat.es/wlpl/SSII-FACT/ws/fr/SiiFactPAGV1SOAP` |
| CollectionInCash     | This web service is provided by AEAT. It's used to submit information about payment transactions in cash from customers, and it sends back a response that contains information about processing on the SII system side.        | `https://www7.aeat.es/wlpl/SSII-FACT/ws/pm/SiiFactCMV1SOAP`  |

>   Internet addresses are subject to change by AEAT. Therefore, we recommend
>   that you check for actual internet addresses on the [official website of the
>   SII system](https://www.agenciatributaria.es/AEAT.internet/en_gb/SII.html).
>   The official documentation also has information about the actual
>   *production* internet addresses that you should set up.

6.  On the **General** tab, in the **Key vault certificate** field, select the
    security certificate that you set up for all web services that you will use
    for interoperation with the SII system: **Cust invoice**, **Vend invoice**,
    **Intra-community**, **Cust payment**, **Vend payment**, and
    **CollectionInCash**.

![](media/emea-esp-sii-setup-key-vault-certificate.png)

>   This image shows you how to setup Key vault certificate for SII system.

## Set up EM parameters for the SII system

After the data entities are imported into the database, complete the following
tasks. When you've completed them, the electronic message functionality will be
ready to use.

1.  Set up executable class parameters.

2.  Set up additional fields and auto-definition rules.

3.  Set up number sequences for electronic messages.

4.  Set up batch settings for automated processing of interoperation with the
    SII system.

5.  Set up security roles for electronic message processing.

## Set up executable class parameters

Three executable classes are included in the two types of electronic messages
processing (**SII** and **CollectionInCash**) that are used to interoperate with
the SII system and imported into the system by using a package of data entities.

| **Executable class name**    | **Description**                                                                                                                                             |
|------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SIIGenerateItems             | This class fills in EM items of the following types:                                                                                                        |
| SIIPartyAttributesEvaluation | For filled-in EM items (in **Creado** status), this class evaluates the values for the following additional fields:                                         |
| MonitorCollectionInCash      | This class monitors changes in the data of records of the **Collections in cash** report and then updates the status of EM items in the appropriate manner. |

-   Customer invoice (FacturasСliente)

-   Vendor invoice (FacturasProveedores)

-   Customer payment (PagosCliente)

-   Vendor payment (PagosProveedores)

-   Intra-community operations (OperacionesIntracomunitarias)

For filled-in EM items, this class evaluates values for the following additional
fields:

-   Invoice type (TipoFactura)

-   Summary reference (NumSerieFactura)

-   Special schema code (ClaveRegimenEspecialOTrascendencia)

-   Intracommunity transaction ID (TipoOperacion)

-   Registration number (ID)

-   Tax ID type (IDType)

-   Party ISO code (CodigoPais)

### Set up the SIIGenerateItems executable class

1.  To set up parameters of the **SIIGenerateItems** executable class, go to
    **Tax \> Setup \> Electronic messages \> Executable class settings**.

2.  On the **Executable class settings** page, select the **SIIGenerateItems**
    executable class that is associated with the **EMCreateItemsController**
    executable class name.

3.  On the Action Pane, select **Parameters**, and then, in the dialog box that
    appears, set the following values for the parameters of the executable
    class.

| **Parameter name**            | **Value**                          |
|-------------------------------|------------------------------------|
| Invoice type                  | TipoFactura                        |
| Summary reference             | NumSerieFactura                    |
| Special scheme code           | ClaveRegimenEspecialOTrascendencia |
| Intracommunity transaction ID | TipoOperacion                      |
| Customer invoices             | FacturasСliente                    |
| Customer payments             | PagosCliente                       |
| Vendor invoices               | FacturasProveedores                |
| Vendor payments               | PagosProveedores                   |
| Intracommunity operations     | OperacionesIntracomunitarias       |

4.  Select **OK** to initiate the executable class.

![](media/emea-esp-sii-siigenerateitems-executable-class.png)

### Set up the SIIPartyAttributesEvaluation executable class

1.  To set up parameters of the **SIIPartyAttributesEvaluation** executable
    class, go to **Tax \> Setup \> Electronic messages \> Executable class
    settings**.

2.  On the **Executable class settings** page, select the
    **SIIPartyAttributesEvaluation** executable class that is associated with
    the **EMAdditionalFieldsEvaluationController_ES** executable class name.

3.  On the Action Pane, select **Parameters**, and then, in the dialog box that
    appears, set the following values for the parameters of the executable
    class.

| **Parameter name**  | **Value**  |
|---------------------|------------|
| Registration number | ID         |
| Tax ID type         | IDType     |
| Party ISO code      | CodigoPais |

4.  Select **OK** to initiate the executable class.

![](media/emea-esp-sii-siipartyattributesevaluation-executable-class.png)

### Set up the MonitorCollectionInCash executable class

1.  To set up parameters of the **MonitorCollectionInCash** executable class, go
    to **Tax \> Setup \> Electronic messages \> Executable class settings**.

2.  On the **Executable class settings** page, select the
    **MonitorCollectionInCash** executable class that is associated with the
    **EMCheckChangesCollectionInCashController_ES** executable class name.

3.  On the Action Pane, select **Parameters**, and then in the dialog box that
    appears, set the following values for the parameters of the executable
    class.

| **Parameter name** | **Value**            |
|--------------------|----------------------|
| Pending cancel     | CancelacionPendiente |
| Corrected          | Corregido            |

4.  Select **OK** to initiate the executable class.

![](media/emea-esp-sii-monitorcollectionincash-executable-class.png)

## Set up additional fields and auto-definition rules

EM items have additional fields that are included in the two types of electronic
message processing (**SII** and **CollectionInCash**) that are used to
interoperate with the SII system and imported into the system by using a package
of data entities. Additional fields are associated with EM items and are
required for their processing. The system automatically sets values for
additional fields when actions are run, but you can manually set and adjust the
values of additional fields before you submit the information to the SII system.
Additional fields are named according to related elements of the report. For
more information about what each related report element is, see the [official
documentation for the SII
system](https://www.agenciatributaria.es/AEAT.internet/en_gb/SII.html).

| **Additional field**               | **Description**                | **Type of processing where the field is used**                                                                                                                                                 | **Action/executable class that the field is set by**                                                                                                                                                                                                                                                               |
|------------------------------------|--------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| TipoComunicacion                   | Communication type             | **SII** and **CollectionInCash**. This field is applicable only to the **FacturasСliente**, **FacturasProveedores**, **OperacionesIntracomunitarias**, and **CobrosEnMetálico** EM item types. | **GenerateMessageItem** action for **SII** processing. The default value is **A0**. The value is updated to **A1** during import of the response by the **ImportResponse** action when the invoice is successfully accepted by the SII system. **PopulateMessageItem** action for **CollectionInCash** processing. |
| ID                                 | Registration ID                | **SII** and **CollectionInCash**. This additional field is applicable to all EM item types.                                                                                                    | **EvaluationFields** action, **SIIPartyAttributesEvaluation** executable class.                                                                                                                                                                                                                                    |
| IDType                             | Counterparty ID type           | **SII** and **CollectionInCash**. This field is applicable to all EM item types.                                                                                                               | **EvaluationFields** action, **SIIPartyAttributesEvaluation** executable class.                                                                                                                                                                                                                                    |
| CodigoPais                         | ISO code                       | **SII** and **CollectionInCash**. This field is applicable to all EM item types.                                                                                                               | **EvaluationFields** action, **SIIPartyAttributesEvaluation** executable class.                                                                                                                                                                                                                                    |
| ClaveRegimenEspecialOTrascendencia | Special scheme code            | **SII** only. This field is applicable only to the **FacturasСliente** and **FacturasProveedores** EM item types.                                                                              | **GenerateMessageItem** action, **SIIGenerateItems** executable class. The default value is **01**. Setup of auto-definition rules is available.                                                                                                                                                                   |
| NumSerieFactura                    | Summary reference              | **SII** only. This field is applicable only to the **FacturasСliente** and **FacturasProveedores** EM item types.                                                                              | **GenerateMessageItem** action, **SIIGenerateItems** executable class.                                                                                                                                                                                                                                             |
| TipoFactura                        | Invoice type                   | **SII** only. This field is applicable only to the **FacturasСliente** and **FacturasProveedores** EM item types                                                                               | **GenerateMessageItem** action, **SIIGenerateItems** executable class. The default value is **01**. Setup of auto-definition rules is available.                                                                                                                                                                   |
| TipoOperacion                      | Intra-community operation type | **SII** only. This field is applicable only to the **OperacionesIntracomunitarias** EM item type.                                                                                              | Manual definition. The default value is **A**. Setup of auto-definition rules is available and can be applied during execution of the **GenerateMessageItem** action.                                                                                                                                              |
| EmitidaPorTerceros                 | Issued by third parties        | **SII** only. This field is applicable only to the **FacturasСliente** EM item type.                                                                                                           | Manual definition only. The default value is **N**. Setup of auto-definition rules is available.                                                                                                                                                                                                                   |
| EntidadSucedidaNIF                 | Succeeded legal entity Tax ID  | **SII** only. This field is applicable only to the **FacturasСliente**, **FacturasProveedores**, and **OperacionesIntracomunitarias** EM item types.                                           | Manual definition. Setup of auto-definition rules is available.                                                                                                                                                                                                                                                    |
| EntidadSucedidaNombreRazon         | Succeeded legal entity name    | **SII** only. This field is applicable only to the **FacturasСliente**, **FacturasProveedores**, and **OperacionesIntracomunitarias** EM item types.                                           | Manual definition. Setup of auto-definition rules is available.                                                                                                                                                                                                                                                    |
| ReferenciaCatastral                | Cadastral reference            | **SII** only. This field is applicable only to the **FacturasСliente** EM item type.                                                                                                           | Manual definition. Setup of auto-definition rules is available.                                                                                                                                                                                                                                                    |
| SituacionInmueble                  | Property location              | **SII** only. This field is applicable only to the **FacturasСliente** EM item type.                                                                                                           | Manual definition. Setup of auto-definition rules is available.                                                                                                                                                                                                                                                    |

### Algorithm to define the value of the TipoComunicacion (Communication type) additional field

The **TipoComunicacion** (**Communication type**) additional field is
automatically defined by the system for message items of the
**FacturasСliente**, **FacturasProveedores**, **OperacionesIntracomunitarias**,
and **CobrosEnMetálico** types. For a list of values that can be assigned to
**TipoComunicacion**, see the [official documentation for the
SII](https://www.agenciatributaria.es/AEAT.internet/en_gb/SII.html) system.

The following values are available for the **TipoComunicacion** additional field
as part of the predefined setup for electronic messages.

| **Field value** | **Description (Spanish)**                                | **Description (English)** |
|-----------------|----------------------------------------------------------|---------------------------|
| A0              | Alta de facturas/registro                                | Invoice registration      |
| A1              | Modificación de facturas/registros (errores registrales) | Modification of invoices  |

The default value of the **TipoComunicacion** additional field is defined as
**A0** on the **Message item additional fields** FastTab in the definition of
**SII** and **CollectionInCash** processing (**Tax \> Setup \> Electronic
messages \> Electronic message processing**). Later, when Finance receives a
response from the SII system that the invoice was successfully accepted, the
invoice's **TipoComunicacion** value is updated to **A1** by the
**ImportResponse** action.

### Algorithm to define the value of the ID (Registration ID) additional field

The **ID** (**Registration ID**) additional field is automatically defined by
the system for EM items of all types during the evaluation of additional fields.
For counterparties that registered for VAT outside Spain, the value of the
**ID** additional field is reported in the **ID** tag under the **IDOtro** tag
of the report. For counterparties from Spain, the value is reported in the
**NIF** tag.

The value of the **ID** additional field is defined by the **EvaluationFields**
action that is associated with the **SIIPartyAttributesEvaluation** executable
class. This class retrieves the tax exempt number that is specified for the
invoice during invoice posting. If the tax exempt number isn't specified for an
invoice before posting, the system collects the value for the **ID** additional
field from the **Tax exempt number** field in the counterparty master data.

For counterparties from EU or outside of the EU, **ID** additionally field will
be supplemented with related ISO code.

### Algorithm to define the IDType (Counterparty ID type) additional field

The **IDType** (**Counterparty ID type**) additional field is automatically
defined by the system for EM items of all types during the evaluation of
additional fields. For the list of values that can be set for **IDType**, see
the [official documentation for the
SII](https://www.agenciatributaria.es/AEAT.internet/en_gb/SII.html) system.

The following values are available for the **IDType** additional field as part
of the predefined setup for electronic messages.

| **Field value** | **Description**                                                                |
|-----------------|--------------------------------------------------------------------------------|
| 02              | NIF-VAT                                                                        |
| 03              | Passport                                                                       |
| 04              | Official identification document issued by the country or region of residence. |
| 05              | Residence certificate                                                          |
| 06              | Other supporting document                                                      |
| 07              | Not registered                                                                 |

Value of the **IDType** additional field is reported in the **IDType** tag under
the **IDOtro** tag of the report.

By default, for counterparties outside of Spain, when **Registration ID** is not
defined in the counterparty’s master data, the system defines the following
values for the **IDType** additional field:

-   **02** – For EU counterparties

-   **04** – For third-country counterparties

When **Registration ID** is defined on the counterparty’s master data, system
analyzes the following types of the **Registration ID**:

1.  For Spanish counteragents:

    `TaxRegistrationTypesList::NotCensused`

    `TaxRegistrationTypesList::TAXID`

2.  For EU counteragents:

    `TaxRegistrationTypesList::TAXID`

    `TaxRegistrationTypesList::OfficialIdDoc`

    `TaxRegistrationTypesList::Passport`

    `TaxRegistrationTypesList::ResidenceCertificate`

    `TaxRegistrationTypesList::OtherIdDoc`

3.  All other counteragents:

    `TaxRegistrationTypesList::OfficialIdDoc`

    `TaxRegistrationTypesList::Passport`

    `TaxRegistrationTypesList::ResidenceCertificate`

    `TaxRegistrationTypesList::OtherIdDoc`

As a result of this analyzes system defined related **IDType**:

    `TaxRegistrationTypesList::TAXID : '02'`

    `TaxRegistrationTypesList::Passport : '03'`

    `TaxRegistrationTypesList::OfficialIdDoc : '04'`

    `TaxRegistrationTypesList::ResidenceCertificate : '05'`

    `TaxRegistrationTypesList::OtherIdDoc : '06'`

    `TaxRegistrationTypesList::NotCensused : '07'`

Sometimes, when a Spanish counteragent's tax exempt number (NIF) can't be found
in the SII system's database, an invoice can't be accepted by the SII system. At
the same time, a customer invoice where the counteragent isn't registered in the
SII system's database can be sent to the SII system when related tax exempt
number of the counteragent reported in the **IdOtro** tag by using an **IdType**
value of **07**. In this case, the SII system will “accept with errors” the
invoice.

You can manually adjust the value of the **IDType** additional field before you
submit the invoice to the SII system.

### Algorithm to define the CodigoPais (ISO code) additional field

The **CodigoPais** (**ISO code**) additional field is automatically defined by
the system for EM items of all types during the evaluation of additional fields.
The value of the **CodigoPais** additional field is reported in the
**CodigoPais** tag under the **IDOtro** tag of the report, and identifies the
country or region of the tax registration number of the counterparty from the
document.

By default, the system defines the value of the **CodigoPais** additional field
as the International Organization for Standardization (ISO) county/region code
from the primary address of the counterparty.


