---
title: Work with NFS-e service invoices for projects
description: Learn how to configure and generate Brazilian NFS-e service invoices for projects in Dynamics 365 Finance. Set up NBS codes, tax burdens, and fiscal documents step by step.
author: ankviklis
ms.author: ankviklis
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 04/15/2026
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 01/02/2026

---

# Work with NFS-e service invoices for projects

This article describes how to set up and use Nota Fiscal de Serviço Eletrônica (NFS-e) service invoices with the **Project management and accounting** module in Microsoft Dynamics 365 Finance and Microsoft Dynamics 365 Project Operations.

> [!NOTE]
> This functionality extends the existing NFS-e service invoice support to project-based transactions. Before you proceed, complete all the prerequisite setup steps described in [Set up Brazil reformed tax](brazil-reform-setup.md) and [Work with NFS-e Service Invoices](brazil-nfs-e-service-invoices.md), including enabling the **Brazil reformed tax** feature, enabling the **Tax calculation configuration**, importing **Electronic Reporting configurations**, and populating the Nomenclatura Brasileira de Serviços (NBS) and operation indicator code tables.

## Prerequisites

Before you can generate NFS-e XML for project invoices, the following project-specific configuration is required in addition to the general NFS-e prerequisites.

### Enable the tax calculation configuration

To enable the tax calculation configuration, follow this step:

- Go to **Tax** > **Setup** > **Tax calculation parameters** and enable **Advanced tax calculation** for the **Project** business process.

This setting is required. If you don't enable **Advanced tax calculation** for the **Project** business process, the Nomenclatura Brasileira de Serviços (NBS) code and operation indicator code fields aren't visible on project forms, and NFS-e data isn't propagated during posting.

### Set NFS-e tax burden percentages on the fiscal establishment

Set the approximate tax burden percentages for the Federal NFS-e format at the fiscal establishment level, so they apply to all project invoices issued from that establishment.

To set NFS-e tax burden percentages on the fiscal establishment, follow these steps:

1. Go to **Organization administration** > **Organizations** > **Fiscal establishments** > **Fiscal establishments**.
1. Select the fiscal establishment record.
1. Expand the **NFS-e** FastTab.
1. In the **NFS-E TAX BURDEN** group, enter values in the following fields:
   - **Approximate federal tax percentage** – the estimated portion of total tax that is federal.
   - **Approximate state tax percentage** – the estimated portion of total tax that is state.
   - **Approximate city tax percentage** – the estimated portion of total tax that is municipal.

Make sure you fill all three fields (use 0 where a level doesn't apply).

### Assign NBS and operation indicator codes to project categories

Assign NBS and operation indicator codes to each project category that represents a service. These codes default onto project transactions and carry through to the NFS-e XML.

To assign NBS and operation indicator codes to project categories, follow these steps:

1. Go to **Project management and accounting** > **Setup** > **Categories** > **Project categories**.
1. Select a project category.
1. On the **Project** FastTab, set the following fields:
   - **NBS code** – select the Nomenclatura Brasileira de Serviços code that classifies the type of service.
   - **Operation Indicator Code** – select the code that indicates the nature of the service operation, such as within city, outside city, or abroad.
1. Repeat for all service-related project categories.

> [!IMPORTANT]
> The **Operation Indicator Code** field depends on the selected **NBS code**. When you change the NBS code, the operation indicator code is automatically cleared. The lookup for the operation indicator code shows only codes that are linked to the currently selected NBS code. If you clear the NBS code, the operation indicator code is also cleared.

These values serve as defaults for project journal lines and on-account transactions that use the category.

## Provide NBS and operation indicator codes on project transactions

When you create project transactions, verify that the NBS code and operation indicator code are populated. The values default from the project category but you can manually override them on each transaction. When you select or change a project category on a transaction line, the NBS code and operation indicator code update to match the category defaults. However, if you clear the category, the existing NBS and operation indicator code values are preserved.

> [!NOTE]
> Expense transactions require a Time and Material project contract with billing rules. Ensure that the expense-related project categories are included as chargeable categories on the project contract.

### Provide NBS and operation indicator codes on on-account transactions

To provide NBS and operation indicator codes on on-account transactions, follow these steps:

1. Go to **Project management and accounting** > **Projects** > **All projects**.
1. Open a project, and then select **Manage** > **On-account transactions**.
1. On the on-account transaction form, on the **General** tab, verify or update the following fields:
   - **NBS code**
   - **Operation Indicator Code**

### Project journal lines

All project journal line types - **Hour**, **Fee**, **Expense**, and **Item** - include the NBS code and operation indicator code fields.

#### Provide NBS and operation indicator codes on hour journal lines

To provide NBS and operation indicator codes on hour journal lines, follow these steps:

1. Go to **Project management and accounting** > **Journals** > **Hour**.
1. Open a journal and select **Lines**.
1. On the **General** tab, verify or update the **NBS code** and **Operation Indicator Code** fields.

#### Provide NBS and operation indicator codes on fee journal lines

To provide NBS and operation indicator codes on fee journal lines, follow these steps:

1. Go to **Project management and accounting** > **Journals** > **Fee**.
1. Open a journal and select **Lines**.
1. On the **General** tab, verify or update the **NBS code** and **Operation Indicator Code** fields.

#### Provide NBS and operation indicator codes on expense journal lines

To provide NBS and operation indicator codes on expense journal lines, follow these steps:

1. Go to **Project management and accounting** > **Journals** > **Expense**.
1. Open a journal and select **Lines**.
1. On the **Project** tab, verify or update the **NBS code** and **Operation Indicator Code** fields.

#### Provide NBS and operation indicator codes on item journal lines

To provide NBS and operation indicator codes on item journal lines, follow these steps:

1. Go to **Project management and accounting** > **Journals** > **Item**.
1. Open a journal and select **Lines**.
1. On the **Project** tab, verify or update the **NBS code** and **Operation Indicator Code** fields.

## Set NFS-e fields on project invoice proposals

When you create an invoice proposal for a project, set additional NFS-e fields on both the header and the transaction lines.

### Set NFS-e fields on invoice proposal header

To set NFS-e fields on the invoice proposal header, follow these steps:

1. Go to **Project management and accounting** > **Project invoices** > **Project invoice proposals**.
1. Create or open an invoice proposal.
1. Select the **Header** tab and set the following fields:
   - **Reason for not providing Foreigner ID** – if the project customer doesn't have a Brazilian tax identification number (NIF), select the appropriate reason code from the dropdown. You can also set this value on the customer record itself, and it defaults onto the invoice proposal. The value is carried through to the fiscal document.
   - **LOCATION OF SERVICE PROVISION** group:
     - **Foreign** – set to **Yes** if the service was performed outside Brazil. The default is **No** (domestic). When you toggle this setting, the previously set location field (domestic or foreign) is cleared automatically.
     - **Domestic** – if **Foreign** is set to **No**, specify the city where the service was provided.
     - **Foreign** – if **Foreign** is set to **Yes**, select the country/region where the service was performed.

1. On the **Header** tab, in the **General** section, set the **Invoice template** field to **FiscalDocument_BR.Report**. This setting is required for the NFS-e fiscal document to be generated correctly when the proposal is posted.

### Invoice proposal transaction lines

On the invoice proposal form, select the **Lines** tab. In the **Invoice proposal transactions** section, you can see the **NBS code** and **Operation Indicator Code** columns on each transaction type tab:

- **Hour** – displays the NBS code and operation indicator code from the hour journal transactions.
- **Item** – displays the NBS code and operation indicator code from the item journal transactions.
- **Fee** – displays the NBS code and operation indicator code from the fee journal transactions.
- **On-account** – displays the NBS code and operation indicator code from the on-account transactions.
- **Expense** – displays the NBS code and operation indicator code from the expense transactions.

These values come from the originating project transactions. You can verify or update them before posting the invoice. The same dependency behavior applies here: changing the NBS code on a proposal line clears the operation indicator code, and the operation indicator code lookup filters by the selected NBS code.

## Verify NFS-e data on fiscal documents

After you post a project invoice proposal, the system generates a fiscal document. The NFS-e fields from the invoice proposal flow through to the fiscal document automatically. The fiscal document form doesn't introduce any new fields. The existing NFS-e fields are populated with data from the project invoice.

To verify NFS-e data on fiscal documents, follow these steps:

1. Go to **Project management and accounting** > **Fiscal documents** > **All fiscal documents**.
1. On the fiscal document form, verify the following items:
   - **Fiscal document lines** – confirm that the **NBS code** and **Operation Indicator Code** columns are populated for each line.
   - **Header** tab – confirm that the **Reason for not providing Foreigner ID** and **NIF exemption** fields are populated, if applicable to the customer.
   - **Services information** section on the **Header** tab – confirm that the **LOCATION OF SERVICE PROVISION** group shows the correct **Foreign** setting, and the **Domestic** or **Foreign** country/region fields are filled as expected.

## Generate NFS-e service electronic invoices for projects

After you complete all the required configuration steps and post the project invoice, you can generate electronic invoices for posted project invoices by going to **Accounts receivable** > **Periodic tasks** > **NFS-e export**.

The export process works the same way as for non-project NFS-e invoices. The NBS codes, operation indicator codes, service location, and tax burden percentages from the project transactions are included in the generated NFS-e XML.

## Additional resources

- [Work with NFS-e Service Invoices](brazil-nfs-e-service-invoices.md)
- [Set up Brazil reformed tax](brazil-reform-setup.md)
- [Use tax calculation in projects in Brazil tax reform](brazil-reform-calculation-project.md)
- [Use tax calculation in project quotation in Brazil tax reform](brazil-reform-calculation-project-quotation.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
