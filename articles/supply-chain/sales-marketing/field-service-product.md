---
# required metadata

title: Synchronize Agreement invoices from Field Service to Free text invoices in Finance and Operations
description: This topic discusses the templates and underlying tasks that are used to synchronize Agreement invoices in Microsoft Dynamics 365 for Field Service to sales order in Microsoft Dynamics 365 for Finance and Operations.
author: ChristianRytt
manager: AnnBe
ms.date: 04/09/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: yuyus
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: crytt
ms.dyn365.ops.version: July 2017 update 
ms.search.validFrom: 2017-07-8

---

#  Synchronize Agreement invoices from Field Service to Free text invoices in Finance and Operations

[!include[banner](../includes/banner.md)]

This topic discusses the templates and underlying task that are used to synchronize Agreement invoices from Microsoft Dynamics 365 for Field Service to Free text invoices in Microsoft Dynamics 365 for Finance and Operations.

## Templates and tasks

The following templates and underlying tasks are used to run synchronization of
Agreement invoices from Field Service to Free text invoices in Finance and
Operations:

**Name of the template in Data integration:**

-   Agreement invoices (Field Service to Fin and Ops)

**Names of the tasks in the Data integration project:**

-   Invoice headers
-   Invoice lines

The following synchronization is required before synchronization can occur:

-   Accounts (Sales to Fin and Ops) – Direct

### Entity set

| **Field Service** | **Finance and Operations** |
|----------------|----------------------------------------|
| invoices       | CDS customer free text invoice headers |
| invoicedetails | CDS customer free text invoice lines   |

### Entity flow

**Invoices** created from an **Agreement** in Field Service can synchronize to Finance
and Operations via a CDS Data Integration project. Updates on these invoices
will sync to the **Free text invoice** in Finance and Operations, if the **Accounting status** in the **Free text
invoice** is **In process**. Once the **Free text invoice** is
posted in Finance and Operations and the **Accounting status** is **Completed**, you can’t synchronize updates from Field Service anymore.

### Field Service CRM solution

The field **Has Lines With Agreement Origin** is added to the **Invoice** entity and
is used to ensure that only invoices created from an **Agreement** are synchronized.
The value is true if this invoice contains at least one invoice line originating
from an agreement.

The field **Has Agreement Origin** is added to the **Invoice Line** entity and is
used to ensure that only invoice lines created from an **Agreement** is
synchronized. The value is true if the invoice line originates from an
agreement.

**Invoice date** is a mandatory field in Finance and Operations and hence needs
to have a value in Field service before synchronization. To meet the requirement, the
following logic is added:

-   If the field **Invoice Date** is blank (no value) on the **Invoice** entity, it
    is set to today’s date when an **Invoice line** originating from an Agreement is
    added.

-   The **Invoice Date** can be changed by the user. However, a business process
    error will be shown if the user tries to save an **Invoice** without a value for
    the **Invoice date** when the invoice originates from an **Agreement**.

### Preconditions and mapping setup

Setup of **Invoice origin** for the integration is needed to distinguish the
**Free text invoices** in Finance and Operations created from the Field Service **Agreement
invoices** in . When the **Invoice origin** on an invoice has **Invoice origin type**
Agreement invoice integration the field **External invoice number** is shown.

Besides having the information on the invoice header, it can be used to ensure
that invoices orders created from Field Service Agreement invoices are filtered
out during invoice synchronization from Finance and Operations to Field Service.

Go to **Accounts receivable** \> **Setup** \> **Invoice origin codes**, click **New** to
create a new **Invoice origin**

-   Enter the **Invoice origin**, for example, FS.

-   Enter the **Description**, for example, Field Service Agreement Invoice.

-   Select the **Origin type assignment** check box.

-   Set **Invoice origin type** to **Agreement invoice integration**.

-   Click **Save**.







Synchronization of Finance and Operations Products to Field Service Products
============================================================================

This topic discusses the templates and underlying task that are used for
synchronization of Products from Microsoft Dynamics 365 for Finance and
Operations, Enterprise edition to Products in Microsoft Dynamics 365 for Field
Service.

This used template is based on the **Products (Fin and Ops to Sales) – Direct**
template from Prospect to Cash. Link on the detail on: [Products (Fin and Ops to
Sales) –
Direct](https://docs.microsoft.com/en-us/dynamics365/unified-operations/supply-chain/sales-marketing/products-template-mapping-direct)

Only differences between the **Field Service Products (Fin and Ops to Field
Service)** and **Products (Fin and Ops to Sales) – Direct** templates are
described in the follow topic.

Templates and tasks

**Name of the template in Data integration:**

-   Field Service Products (Fin and Ops to Field Service)

**Name of the task in the Data integration project:**

-   Products - Products

One additional mapping is added on the templates compared to the **Products (Fin
and Ops to Sales) – Direct** template to ensure the required Field service
specific field is set correctly:

          FIELDSERVICEPRODUCTTYPE        Fn        msdyn_fieldserciveproducttype 

With the following value mapping:

          inventory    : 690970000
          nonInventory : 690970001
          service      : 690970002


In Finance and Operations, the **Field Service Product type** on the **Sellable
released products** data entity is calculated as follows:

-   Inventory:    Product type = Product and Item model group, Stocked product =
    True

-   NonInventory: Product type = Product and Item model group, Stocked product =
    False

-   Service:      Product type = Service

