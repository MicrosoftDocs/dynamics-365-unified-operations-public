# Work with NFS-e service invoices for projects

This article describes how to set up and use NFS-e (Nota Fiscal de Serviço Eletrônica) service invoices with the **Project management and accounting** module in Microsoft Dynamics 365 Finance and Dynamics 365 Project Operations.

> [!NOTE]
> This functionality extends the existing NFS-e service invoice support to project-based transactions. Before you proceed, complete all the prerequisite setup steps described in [Set up Brazil reformed tax](brazil-reform-setup.md) and [Work with NFS-e Service Invoices](brazil-nfs-e-service-invoices.md), including enabling the Brazil reformed tax feature, enabling the tax calculation configuration, importing Electronic Reporting configurations, and populating the NBS and operation indicator code tables.

## Prerequisites

Before you can generate NFS-e XML for project invoices, the following project-specific configuration is required in addition to the general NFS-e prerequisites.

### Enable the tax calculation configuration

1. Go to **Tax** \> **Setup** \> **Tax calculation parameters** and enable **Advanced tax calculation** for the **Project** business process.

This settings is required. If the Advanced tax calculation is not enabled for the Project business process, the NBS code and operation indicator code fields are not visible on project forms, and NFS-e data is not propagated during posting.

### Set NFS-e tax burden percentages on the fiscal establishment

The approximate tax burden percentages for the Federal NFS-e format can now be set at the fiscal establishment level, so they apply to all project invoices issued from that establishment.

1. Go to **Organization administration** \> **Organizations** \> **Fiscal establishments** \> **Fiscal establishments**.
2. Select the fiscal establishment record.
3. Expand the **NFS-e** FastTab.
4. In the **NFS-E TAX BURDEN** group, enter values in the following fields:
   - **Approximate federal tax percentage** – the estimated portion of total tax that is federal.
   - **Approximate state tax percentage** – the estimated portion of total tax that is state.
   - **Approximate city tax percentage** – the estimated portion of total tax that is municipal.

Make sure all three fields are filled (use 0 where a level doesn't apply).

### Assign NBS and operation indicator codes to project categories

Each project category that represents a service must be assigned NBS and operation indicator codes. These codes default onto project transactions and are carried through to the NFS-e XML.

1. Go to **Project management and accounting** \> **Setup** \> **Categories** \> **Project categories**.
2. Select a project category.
3. On the **Project** FastTab, set the following fields:
   - **NBS code** – select the Nomenclatura Brasileira de Serviços code that classifies the type of service.
   - **Operation Indicator Code** – select the code that indicates the nature of the service operation (for example, within city, outside city, or abroad).
4. Repeat for all service-related project categories.

> [!IMPORTANT]
> The **Operation Indicator Code** field depends on the selected **NBS code**. When you change the NBS code, the operation indicator code is automatically cleared. The lookup for the operation indicator code shows only codes that are linked to the currently selected NBS code. If you clear the NBS code, the operation indicator code is also cleared.

These values serve as defaults for project journal lines and on-account transactions that use the category.

## Provide NBS and operation indicator codes on project transactions

When you create project transactions, verify that the NBS code and operation indicator code are populated. The values default from the project category but can be manually overridden on each transaction. When you select or change a project category on a transaction line, the NBS code and operation indicator code are updated to match the category defaults. However, if you clear the category, the existing NBS and operation indicator code values are preserved.

> [!NOTE]
> Expense transactions require a Time & Material project contract with billing rules. Ensure that the expense-related project categories are included as chargeable categories on the project contract.

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
   - **Reason for not providing Foreigner ID** – if the project customer doesn't have a Brazilian tax identification number (NIF), select the appropriate reason code from the dropdown. This value can also be set on the customer record itself and defaults onto the invoice proposal. The value is carried through to the fiscal document.
   - **LOCATION OF SERVICE PROVISION** group:
     - **Foreign** – set to **Yes** if the service was performed outside Brazil. The default is **No** (domestic). When you toggle this setting, the previously set location field (domestic or foreign) is cleared automatically.
     - **Domestic** – if **Foreign** is set to **No**, specify the city where the service was provided.
     - **Foreign** – if **Foreign** is set to **Yes**, select the country/region where the service was performed.

4. On the **Header** tab, in the **General** section, set the **Invoice template** field to **FiscalDocument_BR.Report**. This is required for the NFS-e fiscal document to be generated correctly when the proposal is posted.

### Invoice proposal transaction lines

On the invoice proposal form, select the **Lines** tab. In the **Invoice proposal transactions** section, the **NBS code** and **Operation Indicator Code** columns are visible on each transaction type tab:

- **Hour** – displays the NBS code and operation indicator code from the hour journal transactions.
- **Item** – displays the NBS code and operation indicator code from the item journal transactions.
- **Fee** – displays the NBS code and operation indicator code from the fee journal transactions.
- **On-account** – displays the NBS code and operation indicator code from the on-account transactions.
- **Expense** – displays the NBS code and operation indicator code from the expense transactions.

These values are carried from the originating project transactions. You can verify or update them before posting the invoice. The same dependency behavior applies here: changing the NBS code on a proposal line clears the operation indicator code, and the operation indicator code lookup filters by the selected NBS code.

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

## Additional resources

- [Work with NFS-e Service Invoices](brazil-nfs-e-service-invoices.md)
- [Set up Brazil reformed tax](brazil-reform-setup.md)
- [Use tax calculation in projects in Brazil tax reform](brazil-reform-calculation-project)
- [Use tax calculation in project quotation in Brazil tax reform](brazil-reform-calculation-project-quotation)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
