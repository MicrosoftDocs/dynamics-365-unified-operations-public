# Work with NFS-e service invoices for projects

This article describes how to set up and use NFS-e (Nota Fiscal de Serviço Eletrônica) service invoices with the **Project management and accounting** module in Microsoft Dynamics 365 Finance and Dynamics 365 Project Operations.

> [!NOTE]
> This functionality extends the existing NFS-e service invoice support to project-based transactions. Before you proceed, complete all the prerequisite setup steps described in [Work with NFS-e Service Invoices](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/brazil/brazil-nfs-e-service-invoices), including enabling the Brazil reformed tax feature, importing Electronic Reporting configurations, and populating the NBS and operation indicator code tables.

## Prerequisites

Before you can generate NFS-e XML for project invoices, the following project-specific configuration is required in addition to the general NFS-e prerequisites.

### Set NFS-e tax burden percentages on the fiscal establishment

The approximate tax burden percentages for the Federal NFS-e format can now be set at the fiscal establishment level, so they apply to all project invoices issued from that establishment.

1. Go to **Organization administration** \> **Organizations** \> **Fiscal establishments** \> **Fiscal establishments**.
2. Select the fiscal establishment record.
3. Expand the **NFS-e** FastTab.
4. In the **NFS-E TAX BURDEN** group, enter values in the following fields:
   - **Approximate federal tax percentage** – the estimated portion of total tax that is federal.
   - **Approximate state tax percentage** – the estimated portion of total tax that is state.
   - **Approximate city tax percentage** – the estimated portion of total tax that is municipal.

Make sure all three fields are filled (use 0 where a level doesn't apply) and that they total 100%.

### Assign NBS and operation indicator codes to project categories

Each project category that represents a service must be assigned NBS and operation indicator codes. These codes default onto project transactions and are carried through to the NFS-e XML.

1. Go to **Project management and accounting** \> **Setup** \> **Categories** \> **Project categories**.
2. Select a project category.
3. On the **Project** FastTab, set the following fields:
   - **NBS code** – select the Nomenclatura Brasileira de Serviços code that classifies the type of service.
   - **Operation Indicator Code** – select the code that indicates the nature of the service operation (for example, within city, outside city, or abroad).
4. Repeat for all service-related project categories.

These values serve as defaults for project journal lines and on-account transactions that use the category.

## Provide NBS and operation indicator codes on project transactions

When you create project transactions, verify that the NBS code and operation indicator code are populated. The values default from the project category but can be overridden on each transaction.

### On-account transactions

1. Go to **Project management and accounting** \> **Projects** \> **All projects**.
2. Open a project, and then select **Manage** \> **On-account transactions**.
3. On the on-account transaction form, on the **General** tab, verify or update the following fields:
   - **NBS code**
   - **Operation Indicator Code**

### Project journal lines

The NBS code and operation indicator code fields are available on all project journal line types: **Hour**, **Fee**, **Expense**, and **Item**.

#### Hour journal lines

1. Go to **Project management and accounting** \> **Journals** \> **Hour**.
2. Open a journal and select **Lines**.
3. On the **General** tab, verify or update the **NBS code** and **Operation Indicator Code** fields.

#### Fee journal lines

1. Go to **Project management and accounting** \> **Journals** \> **Fee**.
2. Open a journal and select **Lines**.
3. On the **General** tab, verify or update the **NBS code** and **Operation Indicator Code** fields.

#### Expense journal lines

1. Go to **Project management and accounting** \> **Journals** \> **Expense**.
2. Open a journal and select **Lines**.
3. On the **Project** tab, verify or update the **NBS code** and **Operation Indicator Code** fields.

#### Item journal lines

1. Go to **Project management and accounting** \> **Journals** \> **Item**.
2. Open a journal and select **Lines**.
3. On the **Project** tab, verify or update the **NBS code** and **Operation Indicator Code** fields.

## Set NFS-e fields on project invoice proposals

When you create an invoice proposal for a project, additional NFS-e fields are available on both the header and the transaction lines.

### Invoice proposal header

1. Go to **Project management and accounting** \> **Project invoices** \> **Project invoice proposals**.
2. Create or open an invoice proposal.
3. Select the **Header** tab and set the following fields:
   - **Reason for not providing Foreigner ID** – if the project customer doesn't have a Brazilian tax identification number (NIF), select the appropriate reason code from the dropdown. This field is enabled when the customer's Foreign ID is blank.
   - **LOCATION OF SERVICE PROVISION** group:
     - **Foreign** – set to **Yes** if the service was performed outside Brazil. The default is **No** (domestic).
     - **Domestic** – if the service was performed within Brazil, specify the state or city where the service was provided.
     - **Foreign** – if **Foreign** is set to **Yes**, select the country/region where the service was performed.

### Invoice proposal transaction lines

On the invoice proposal form, select the **Lines** tab. In the **Invoice proposal transactions** section, the **NBS code** and **Operation Indicator Code** columns are visible on each transaction type tab:

- **Hour** – displays the NBS code and operation indicator code from the hour journal transactions.
- **Item** – displays the NBS code and operation indicator code from the item journal transactions.
- **Fee** – displays the NBS code and operation indicator code from the fee journal transactions.
- **On-account** – displays the NBS code and operation indicator code from the on-account transactions.
- **Expense** – displays the NBS code and operation indicator code from the expense transactions.

These values are carried from the originating project transactions. You can verify or update them before posting the invoice.

## Verify NFS-e data on fiscal documents

After you post a project invoice proposal, the system generates a fiscal document. The NFS-e fields from the invoice proposal flow through to the fiscal document automatically. No new fields are introduced on the fiscal document form; the existing NFS-e fields are populated with data from the project invoice.

1. Go to **Project management and accounting** \> **Fiscal documents** \> **All fiscal documents**.
2. On the fiscal document form, verify the following:
   - **Fiscal document lines** – confirm that the **NBS code** and **Operation Indicator Code** columns are populated for each line.
   - **Header** tab – confirm that the **Reason for not providing Foreigner ID** and **NIF exemption** fields are populated (if applicable to the customer).
   - **Services information** section on the **Header** tab – confirm that the **LOCATION OF SERVICE PROVISION** group shows the correct **Foreign** setting, and the **Domestic** or **Foreign** country/region fields are filled as expected.

## Generate NFS-e service electronic invoices for projects

After you complete all the required configuration steps and post the project invoice, you can generate electronic invoices for posted project invoices by going to **Accounts receivable** \> **Periodic tasks** \> **NFS-e export**.

The export process works the same way as for non-project NFS-e invoices. The NBS codes, operation indicator codes, service location, and tax burden percentages from the project transactions are included in the generated NFS-e XML.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
