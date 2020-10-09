---
# required metadata

title: Synchronize project actuals directly from Project Service Automation to the project integration journal for posting in Finance and Operations
description: This topic describes the templates and underlying tasks that are used to synchronize project actuals directly from Microsoft Dynamics 365 Project Service Automation to Finance and Operations.
author: KimANelson
manager: AnnBe
ms.date: 07/20/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 87983
ms.assetid: b454ad57-2fd6-46c9-a77e-646de4153067
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-11-28
ms.dyn365.ops.version: AX 7.3.0

---
# Synchronize project actuals directly from Project Service Automation to the project integration journal for posting in Finance and Operations

[!include[banner](../includes/banner.md)]

This topic describes the templates and underlying tasks that are used to synchronize project actuals directly from Dynamics 365 Project Service Automation to Dynamics 365 Finance.

The template synchronizes transactions from Project Service Automation into a staging table in Finance. After synchronization is completed, you **must** import the data from the staging table into the integration journal.

> [!NOTE]
> - Project actuals integration is available starting in version 8.0.1.
> - If you're using Enterprise edition 7.3.0 after you install KB 4132657 and KB 4132660, you will be able to use the templates to integrate project tasks, expense transaction categories, hour estimates, expense estimates, and actuals, and to configure functionality locking. If you must reset the accounting distributions, we recommend that you also install KB 4131710.
> - If you're using version 7.3.0, and you are bringing fee transactions over from Project Service Automation, you must install KB 4345320 in order to include those fees in the project invoice.
> - If you're entering sales tax amounts on time or expense transactions in Project Service Automation, you must install Project Service Automation Update 7. Otherwise, the tax actuals won't be linked to the associated time or expense actuals, and they won't be synchronized to Finance. For more information, contact Support.

## Data flow for Project Service Automation to Finance

The Project Service Automation to Finance integration solution uses the Data integration feature to synchronize data across instances of Project Service Automation and Finance. The integration templates that are available with the Data integration feature enable the flow of data about project actuals from Project Service Automation to Finance.

The following illustration shows how the data is synchronized between Project Service Automation and Finance.

[![Data flow for Project Service Automation integration with Finance and Operations](./media/ProjectActualsFlow.jpg)](./media/ProjectActualsFlow.jpg)

## Project actuals from Project Service Automation

### Template and tasks

To access the available templates, in the Microsoft Power Apps admin center, select **Projects**, and then, in the upper-right corner, select **New project** to select public templates.

The following template and underlying tasks are used to synchronize project actuals from Project Service Automation to Finance:

- **Name of the template in Data integration:** Project actuals (PSA to Fin and Ops)
- **Name of the tasks in the project:**

    - Actuals
    - TransactionConnections

### Entity set

| Project Service Automation | Finance                                   |
|----------------------------|----------------------------------------------------------|
| Actuals                    | Integration entity for project actuals                   |
| Transaction Connections    | Integration entity for project transaction relationships |

### Entity flow

Project actuals are managed in Project Service Automation, and they are synchronized to the project integration journal in Finance. The accounting will be applied based on default financial dimensions and the posting setup.

### Prerequisites

Before synchronization of actuals can occur, you must configure the Project Service Automation integration parameters and synchronize projects, project tasks, and project expense transaction categories.

### Power Query

In the project actuals template, you must use Microsoft Power Query for Excel to complete these tasks:

- Transform the transaction type in Project Service Automation to the correct transaction type in Finance. This transformation is already defined in the Project actuals (PSA to Fin and Ops) template.
- Transform the billing type in Project Service Automation to the correct billing type in Finance. This transformation is already defined in the Project actuals (PSA to Fin and Ops) template. The billing type is then mapped to the line property, based on the configuration on the **Project Service Automation integration parameters** page.
- Filter to specific resource organizational units that must be synchronized with this template.
- If intercompany time or intercompany expense actuals will be synchronized to Finance, you must transform the contract organizational unit to the correct legal entity in Finance. In the Project actuals (PSA to Fin and Ops) template, a conditional column is defined based on demo data. You must update the last inserted conditional column to the correct legal entities. Otherwise, either an integration error might occur, or incorrect actual transactions might be imported into Finance.
- If intercompany time or intercompany expense actuals won't be synchronized to Finance, you must delete the last inserted conditional column from your template. Otherwise, either an integration error might occur, or incorrect actual transactions might be imported into Finance.

#### Contract organizational unit
To update the inserted conditional column in the template, click the **Map** arrow to open the mapping. Select the **Advanced Query and Filtering** link to open Power Query.

- If you're using the default Project actuals (PSA to Fin and Ops) template, in Power Query, select the last **Inserted Condition** from the **Applied Steps** section. In the **Function** entry, replace **USSI** with the name of the legal entity that should be used with the integration. Add additional conditions to the **Function** entry as you require, and update the **else** condition from **USMF** to the correct legal entity.
- If you're creating a new template, you must add the column to support intercompany time and expenses. Select **Add Conditional Column**, and enter a name for the column, such as **LegalEntity**. Enter a condition for the column, where, if **msdyn\_contractorganizationalunitid.msdyn\_name** is \<organizational unit\>, then \<enter the legal entity\>; else null.

### Template mapping in Data integration

The following illustrations show an example of the template task mapping in Data integration. The mapping shows the field information that will be synchronized from Project Service Automation to Finance.

[![Template mapping](./media/ActualsMapping.jpg)](./media/ActualsMapping.jpg)

[![Template mapping](./media/TransactionConnections.jpg)](./media/TransactionConnections.jpg)

## Import from staging table after integration from Project Service Automation

The Import from staging table periodic process must be run after the synchronization of actuals from Project Service Automation to Finance. This process will import the project transactions from the staging table into the Project Service Automation integration journal, where the accounting is applied and the imported transactions can be posted. We recommend that you run this process in batch mode; it can optionally be set up to run as a recurring batch.

## Update actuals from Finance

### Template and tasks

The following template and underlying tasks are used to synchronize the voucher number and sales taxes for posted project transactions from Finance to Project Service Automation:

- **Name of the template in Data integration:** Project actuals update (Fin Ops to PSA)
- **Name of the tasks in the project:**

    - Actuals 
    - TransactionConnections

### Entity set

| Finance                                                  | Project Service Automation |
|----------------------------------------------------------|----------------------------|
| Integration entity for project actuals                   | Actuals                    |
| Integration entity for project transaction relationships | Transaction Connections    |

### Entity flow

Project actuals are managed in Project Service Automation, and they are synchronized to the project integration journal in Finance. After actuals are posted in Finance, they are updated in Project Service Automation with the voucher number from Finance. If sales taxes were added in Finance, new tax actuals are created in Project Service Automation.

### Power Query

In the project actuals update template, you must use Power Query to complete these tasks:

- Transform the transaction type in Finance to the correct transaction type in Project Service Automation. This transformation is already defined in the Project actuals update (Fin Ops to PSA) template.
- Transform the billing type in Finance to the correct billing type in Project Service Automation. This transformation is already defined in the Project actuals update (Fin Ops to PSA) template.

### Template mapping in Data integration

The following illustrations show examples of the template task mappings in Data integration. The mapping shows the field information that will be synchronized from Finance to Project Service Automation.

[![Template mapping](./media/ActualsUpdateMapping.jpg)](./media/ActualsUpdateMapping.jpg)

[![Template mapping](./media/TransactionConnectionsUpdate.jpg)](./media/TransactionConnectionsUpdate.jpg)
