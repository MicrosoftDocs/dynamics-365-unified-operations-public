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

# "Immediate Supply of Information on VAT (Suministro Inmediato de Información del IVA, SII)"

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

![](media/emea-esp-sii-data-package-file.png)

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


