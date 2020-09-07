---
# required metadata

title: Customize the provided ER configurations to generate a custom electronic document
description: This topic explains how to customize the Microsoft-provided Electronic reporting (ER) configurations that are used to generate a custom electronic document.
author: NickSelin
manager: AnnBe
ms.date: 06/25/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: ERWorkspace, ERSolutionTable, ERParameters, ERDataModelDesigner, ERModelMappingTable, ERModelMappingDesigner, EROperationDesigner, ERVendorTable
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 220314
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0

---

# Customize the provided ER configurations to generate a custom electronic document

[!include[banner](../includes/banner.md)]

 The [Electronic reporting (ER) framework](general-electronic-reporting.md) lets you upload to your Microsoft Dynamics 365 Finance application the provided by Microsoft ER [configurations](general-electronic-reporting.md#Configuration) as the ER solution using to generate electronic customer invoices (e-invoices). You can use the provided ER solution for configuring your custom ER solution with no source code changes to access your custom database fields and generate e-invoices that are compliant with your specific requirements.

 ## Overview

Assume that you need to specify a federal tax identification code as a new custom attribute of every customer that you are electronically invoiced. Accordingly, you must customize the structure of the currently using invoice by adding a new item that must be populated with this tax code in every generated e-invoice. The procedures in this topic explain how a user in the System Administrator, Electronic Reporting Developer, or Electronic Reporting Functional Consultant role can perform these tasks in your Finance instance:

- [Configure the minimal set of ER parameters to start using the ER framework](#ConfigureER).
- [Import the initial versions of standard ER configurations provided to generate e-invoices](#ImportERConfigurations1).
- [Configure the Accounts receivable parameters to start using the standard ER configurations](#ConfigureAR1).
- [Configure the legal entity parameters to invoice customers](#ConfigureLE).
- [Prepare a customer record for invoicing electronically](#ConfigureCustomer1).
- [Add, post, and send a customer invoice by using the standard ER configurations](#ProcessInvoice1).
- [Add a custom database field to manage a federal tax identification code for customers](#AddCustomField).
- [Refresh ER metadata to enable database changes for ER model mapping designer](#RefreshERMetadata).
- [Design the custom ER configurations to generate e-invoices containing the new tax code](#DesignCustomERConfigurations).
- [Configure the Accounts receivable parameters to start using the custom ER configurations](#ConfigureAR2).
- [Update a customer record for invoicing electronically](#ConfigureCustomer2).
- [Add, post, and send a customer invoice by using the custom ER configurations](#ProcessInvoice2).
- [Import the new versions of standard ER configurations provided to generate e-invoices](#ImportERConfigurations2).
- [Adopt the changes in the new versions of the standard ER configurations in your custom ER configurations](#RebaseCustomERConfigurations).
- [Add, post, and send a customer invoice by using new versions of the custom ER configurations](#ProcessInvoice3).

All the following procedures can be done in the **DEMF** company.

## <a name="ConfigureER"></a>Configure the ER framework

As a user in the Electronic Reporting Functional Consultant or the Electronic Reporting Developer role, you must configure the minimal set of ER parameters before you can start to use the ER framework to design a custom version of every standard ER configuration of the ER solution using to generate e-invoices.

### Configure ER parameters

1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**.
2. On the **Localization configurations** page, in the **Related links** section, select **Electronic reporting parameters**.
3. On the **Electronic reporting parameters** page, on the **General** tab, set the **Enable design mode** option to **Yes**.
4. On the **Attachments** tab, set the following parameters:
    - In the **Configurations** field, select the **File** type for the **DEMF** company.
    - In the **Job archive**, **Temporary**, **Baseline**, and **Others** fields, select the **File** type.

For more information about ER parameters, see [Configure the ER framework](electronic-reporting-er-configure-parameters.md).

### Activate an ER configuration provider

Every ER configuration that is added is marked as owned by an ER configuration provider. The ER configuration provider that is activated in the **Electronic reporting** workspace is used for this purpose. Therefore, you must activate an ER configuration provider in the **Electronic reporting** workspace before you start to add or edit ER configurations.

> [!NOTE]
> Only the owner of an ER configuration can edit it. Therefore, before an ER configuration can be edited, the appropriate ER configuration provider must be activated in the **Electronic reporting** workspace.

#### Review the list of ER configuration providers

1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**.
2. On the **Localization configurations** page, in the **Related links** section, select **Configuration providers**.
3. On the **Configuration provider table** page, each provider record has a unique name and URL. Review the contents of this page. If a record for **Litware, Inc.** (`https://www.litware.com`) already exists, skip the next procedure, [Add a new ER configuration provider](#AddProvider).

#### <a id="AddProvider"></a> Add a new ER configuration provider

1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**.
2. On the **Localization configurations** page, in the **Related links** section, select **Configuration providers**.
3. On the **Configuration providers** page, select **New**.
4. In the **Name** field, enter **Litware, Inc.**
5. In the **Internet address** field, enter `https://www.litware.com`.
6. Select **Save**.

#### Activate an ER configuration provider

1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**.
2. On the **Localization configurations** page, in the **Configuration providers** section, select the **Litware, Inc.** tile, and then select **Set active**.

For more information about ER configuration providers, see [Create configuration providers and mark them as active](tasks/er-configuration-provider-mark-it-active-2016-11.md).

## <a name="ImportERConfigurations1"></a>Import the initial versions of standard ER configurations

To add the standard ER configurations to your current Finance instance, you must import them from the ER [repository](general-electronic-reporting.md#Repository) that was configured for that instance.

1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**.
2. On the **Localization configurations** page, in the **Configuration providers** section, select the **Microsoft** tile, and then select **Repositories** to view the list of repositories for the Microsoft provider.
3. On the **Configuration repositories** page, select the repository of the **Global** type, and then select **Open**. If you're prompted for authorization to connect to Regulatory Configuration Service, follow the authorization instructions.
4. On the **Configuration repository** page, in the configuration tree in the left pane, select the **Peppol Sales Invoice** format configuration.
5. On the **Versions** FastTab, select version **11.2.2** of the selected ER format configuration.
6. Select **Import** to download the selected version from the Global repository to the current Finance instance.

![Configuration repository page](./media/er-quick-start3-import-solution1.png)

> [!TIP]
> If you have trouble accessing the [Global repository](er-download-configurations-global-repo.md), you can [download configurations](download-electronic-reporting-configuration-lcs.md) from Microsoft Dynamics Lifecycle Services (LCS) instead.

### Review the imported ER configurations

1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**.
2. On the **Localization configurations** page, in the **Configurations** section, select the **Reporting configurations** tile.
3. Expand the **Configuration components** FastTab.
4. On the **Configurations** page, in the configuration tree in the left pane, expand **Invoice model**.
5. In the configuration tree in the left pane, expand **UBL Sales invoice**.

Notice that, in addition to the selected **Peppol Sales Invoice** ER format, other required ER configurations were imported as part of the provided ER solution. Since new versions of ER configurations are constantly published to the Global and LCS repositories to keep the corresponding ER solutions compliant with new requirements, at the current moment the latest versions of the required [data model](general-electronic-reporting.md#data-model-and-model-mapping-components) configuration and its [model mapping](general-electronic-reporting.md#data-model-and-model-mapping-components) configurations were imported.

![Configurations page](./media/er-quick-start3-imported-solution1a.png)

To simulate the state of ER configurations that you would have in the current Finance instance if you would import the version **11.2.2** of the **Peppol Sales Invoice** ER format in the past (for example, in August 7th, 2019), do the following:

- Use the **Delete** option on the Action pane to delete all ER configurations that have been published after August 7th, 2019.
- Use the **Delete** option on the **Versions** FastTab to delete all versions of ER configurations that have been published after August 7th, 2019.

Make sure that the following ER configurations are eventually available in the configuration tree:

- **Invoice model** ER data model configuration (initially named as **Customer invoice model**):
    - Version 11 of it contains the version 10 of the [data model](general-electronic-reporting.md#data-model-and-model-mapping-components) ER component that represents the data structure of the invoicing business domain. This ER configuration has been imported as an ancestor of the selected for import **Peppol Sales Invoice** ER format.
    - Version 50 of it contains the version 31 of the data model ER component. This ER configuration has been imported as an ancestor of the latest for the August 7th, 2019 version of the **Invoice model mapping** ER model mapping configuration.
    <br>![Configurations page](./media/er-quick-start3-imported-solution1b1.png)
        > If you do not see the version 50 of this data model, open the Global repository, and import the version 50.19 of the **Invoice model mapping** ER configuration.
- **Invoice model mapping** ER model mapping configuration (initially named as **Customer invoice model mapping**):
    - Version 50.19 of it has been imported as the latest implementation of the version 50 of the **Invoice model** ER data model configuration. It contains two [model mapping](general-electronic-reporting.md#data-model-and-model-mapping-components) ER components that describe how the data model is filled in with application data at runtime.
    <br>![Configurations page](./media/er-quick-start3-imported-solution1b2.png)
        > If you do not see the version 50.19 of this model mapping, open the Global repository, and import the version 50.19 of the **Invoice model mapping** ER configuration.
- **UBL Sales invoice** ER format configuration:
    - Version 11.2 of it contains the [format](general-electronic-reporting.md#FormatComponentOutbound) and format mapping ER components. The format component specifies the report layout. The format mapping component contains the model data source and specifies how the report layout is filled in by using this data source at runtime. This ER format was configured to generate e-invoices in UBL format. It has been imported as a parent of the selected for import **Peppol Sales Invoice** ER format.
- **Peppol Sales Invoice** ER format configuration:
    - Version 11.2.2 of it contains the format and format mapping ER components that were configured to generate e-invoices in PEPPOL format.
    <br>![Configurations page](./media/er-quick-start3-imported-solution1b3.png)

## <a name="ConfigureAR1"></a>Configure the AR parameters

1.  Go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.
2.  Select the **Electronic documents** tab.
3.  On the **Set up options for electronic documents** page, on the **Electronic reporting** tab, in the **Sales and Free text invoice** field, select **Peppol Sales Invoice**.
4.  Select **Save**.

![Set up options for electronic documents page](./media/er-quick-start3-configure-ar1.png)

## <a name="ConfigureLE"></a>Configure the legal entity parameters

1. Go to **Organization administration \> Organizations \> Legal entities**.
2. For the selected **DEMF** company, expand the **Bank account information** FastTab.
3. In the **Routing number** field, type 1234.
4. Select **Save**.
5. Close the **Legal entities** page.

## <a name="ConfigureCustomer1"></a>Prepare a customer record

1. Go to **Accounts receivable** \> **Customers** \> **All customers**.
2. On the **All customers** page, open the **DE-014** customer account link.

### Add a customer contact

1. On the Action Pane, select the **Customer** tab.
2. In the **Accounts** group, select **Contacts**.
3. Select **Add contacts**.
4. On the **Contacts** page, in the **First name** field, open the lookup page.
5. On the lookup page, select **Adam Carter** and select the **Select** option to close the lookup page.
6. Select **Save**.
7. Close the **Contacts** page.

### Define a primary contact

1. On the **All customers** page, expand the **Sales demographics** FastTab.
2. In the **Primary contact** field, select **Adam Carter**.

### Specify the e-invoicing option

1.  On the **All customers** page, expand the **Invoice and delivery** FastTab.
2.  Set the **eInvoice** field to **Yes**.
3.  Select **Save**.
4.  Close the **All customers** page.

## <a name="ProcessInvoice1"></a>Process a customer invoice by using the standard ER configurations

You can now use the imported standard ER configurations to electronically send a customer free text invoice.

### Add a new invoice

1.  Go to **Accounts receivables \> Invoices \> All free text invoices**.
2.  On the **Free text invoice** page, select **New**.
3.  On the **Free text invoice** page, on the **Free text invoice header** FastTab, in the **Customer account** field, select **DE-014**.
4.  On the **Invoice lines** FastTab, in the added by default invoice line, specify the following:
    1. In the **Description** field, type **Notebook**.
    2. In the **Main account** field, select  **401100**.
    3. In the **Unit price** field, type **1000**.
5.  Select **Save**.
    <br>![Free text invoice page](./media/er-quick-start3-add-invoice.png)

Review [Create a free text invoice](https://docs.microsoft.com/dynamics365/finance/accounts-receivable/create-free-text-invoice-new) for more.

### Post a new invoice

1.  On the **Free text invoice** page, on the Action pane, select **Post**.
2.  On the **Post free text invoice** dialog page, select **OK**.
    <br>![Free text invoice page](./media/er-quick-start3-post-invoice.png)

### Send a posted invoice
1.  On the **Free text invoice** page, on the Action pane, in the **Document** group, select **Send \> Original**.
    <br>![Free text invoice page](./media/er-quick-start3-send-invoice.png)
2.  Close the **Free text invoice** page.

### Analyze a generated e-invoice
1.  Go to **Organization administration \> Electronic reporting \> Electronic reporting jobs**.
2.  On the **Electronic reporting jobs** page, select the initial record having the **Send the eInvoice XML** task description.
3.  Select **Show files** to access the list of generated files.
    <br>![Electronic reporting jobs page](./media/er-quick-start3-jobs-list.png)
4.  Select **Open** to download the generated e-invoice XML file.
5.  Analyze the generated e-invoice XML file. 
    <br>![Preview of the generated e-invoice XML file](./media/er-quick-start3-e-invoice1.png)

>[!NOTE] Note that the customer tax schema is currently represented by the `schemeID` and `schemeAgencyID` XML attributes.

>[!NOTE] Note that the `cbc:CustomizationID` XML element currently contains the following text: **urn:www.cenbii.eu:transaction:biicoretrdm010:ver1.0:# urn:www.peppol.eu:bis:peppol5a:ver1.0**.

## <a name="AddCustomField"></a>Add a custom database field

You can use the [Custom field](https://docs.microsoft.com/dynamics365/fin-ops-core/fin-ops/get-started/user-defined-fields) feature to do the following in the current Finance instance:

- Customize the database structure by adding a new custom database field to store a federal tax identification code for every customer.
- Customize the customer page by adding on it a new data entry field to fill in the added custom database field with a tax code value.

Perform the following steps to implement the described customization:

1.  Go to **Accounts receivables \> Customers \> All customers**.
2.  Open the DE-014 customer link in the **All customers** page.
3.  Right-click in the **General** FastTab under the **Language** field.
4.  In the drop-down menu, select **Personalize: UpperGroup**.
5.  In the pop-up **Personalize** menu, select **Add a field**.
6.  On the **Add columns** dialog page, select **Create new field**.
7.  In the **Table name** field, select **Customers**.
8.  In the **Name prefix** field, type **FederalTaxID**. Note that the entire field name has been automatically defined as
    **FederalTaxID_Custom**.
9. In the **Label** field, type **Federal Tax ID**.
10. In the **Type** field, select **Text**.
11. In the **Length** field, type **20**.
12. Select **Save**.
13. Select **Yes** in the user dialog confirming a new **FederalTaxID** field entry for the **Customers** table.
14. Select **Insert** to <a name="insert_custom_field">add</a> the **FederalTaxID_Custom** field to the current page.
    <br>![All customers page](./media/er-quick-start3-create-new-field.gif)
15. Close the **All customers** page.

## <a name="RefreshERMetadata"></a>Refresh ER metadata

You must refresh the ER metadata to make the added custom field [visible](electronic-reporting-er-configure-parameters.md#frequently-asked-questions) in the ER model mapping designer.

1.  Go to **Organization administration \> Electronic reporting \> Rebuild table references**.
2.  On the **Update data model** dialog page, select **OK**.

## <a name="DesignCustomERConfigurations"></a>Design the custom ER configurations

You can use the provided ER configurations to design your custom ER configurations for generation of e-invoices containing the new tax code.

### Customize the data model configuration

As a user in the Electronic Reporting Functional Consultant role, you can design your custom ER data model.

#### Add a custom data model configuration

1.  Go to **Organization administration \> Electronic reporting \> Configurations**.
2.  On the **Configurations** page, in the configuration tree in the left pane, select **Customer invoice model**.
3.  On the Action pane, select **Create configuration**.
4.  In the **New** field, select **Derive from Name: Customer invoice model, Microsoft** to indicate that you want to create your custom ER data model configuration based on the provided by Microsoft ER data model configuration.
5.  In the **Name** field, type **Invoice model (Litware)**.
6.  On the current dialog page, select **Create configuration** to confirm a new ER configuration entry.

The version 50.1 of the **Invoice model (Litware)** in the **Draft** [status](general-electronic-reporting.md#component-versioning) is available for editing by using the ER data model designer.

![Configurations page](./media/er-quick-start3-added-custom-model.png)

#### Configure a custom data model

You need to modify your custom data model by adding a new field to provide the value of a federal tax identification code as part of customer's data for every ER format that will use this data model as a data source.

1.  On the **Configurations** page, in the configuration tree in the left pane, select **Invoice model (Litware)**.
2.  On the **Versions** FastTab, select version 51.1 of the selected ER data model configuration in the **Draft** status.
3.  On the Action pane, select **Designer** for the selected configuration version.
4.  On the **Data model designer** page, in the data model tree, select **Customer information (Customer)**.
5.  Select **New**.
6.  In the **New node as a** field, keep **Child of an active node**.
7.  In the **Name** field, type **FederalTaxID_Litware**.
8.  In the **Item type** field, keep **String**.
9.  Select **Add**.
10. Select **Save**.
    <br>![Data model designer page](./media/er-quick-start3-add-data-model-field.png)
    > You can fill in the **Label** and **Description** fields for the added field of the data model describing the purpose of this field in multiple languages. See [Design multilingual reports in Electronic reporting](er-design-multilingual-reports.md) for more.
11. Close the **Data model designer** page.

#### Complete a custom data model configuration

You need to [complete](general-electronic-reporting.md#component-versioning) your work with the version 50.1 of your custom ER data model configuration to make it available for adding other custom ER configurations.

1.  Go to **Organization administration \> Electronic reporting \> Configurations**.
2.  On the **Configurations** page, in the configuration tree in the left pane, expand **Invoice model**.
3.  Select **Invoice model (Litware)**.
4.  On the **Versions** FastTab, select **Change status \> Complete**, and then select **OK**.

The status of version 50.1 is changed from **Draft** to **Completed**, and the version becomes read-only. A new editable version, 50.2, has been added and has a status of **Draft**. You can use this version to make further changes in your custom ER data model configuration.

![Configurations page](./media/er-quick-start3-completed-custom-model1.png)

### Customize the model mapping configuration

As a user in the Electronic Reporting Developer role, you can design your custom ER model mapping.

#### Add a custom model mapping configuration

1.  Go to **Organization administration \> Electronic reporting \> Configurations**.
2.  On the **Configurations** page, in the configuration tree in the left pane, expand **Customer invoice model**.
3.  Select **Customer invoice model mapping**.
4.  On the Action pane, select **Create configuration**.
5.  In the **New** field, select **Derive from Name: Customer invoice model mapping, Microsoft** to indicate that you want to create your custom ER model mapping configuration based on the provided by Microsoft ER model mapping configuration.
6.  In the **Name** field, type **Invoice model mapping (Litware)**.
7.  In the **Target model** field, select **Invoice model (Litware)**.
    > [!NOTE] This step is very important. If you missed it, you will not be able to use your custom data model in the configured model mapping.
8.  On the current dialog page, select **Create configuration** to confirm a new ER configuration entry.
    <br>![Configurations page](./media/er-quick-start3-adding-custom-mapping.png)

#### Configure a custom model mapping

You need to modify your custom model mapping specifying how your custom **FederalTaxID_Litware** field of the custom data model is filled in by the application data at runtime.

1.  Go to **Organization administration \> Electronic reporting \> Configurations**.
2.  On the **Configurations** page, in the configuration tree in the left pane, expand **Customer invoice model**.
3.  Expand **Customer invoice model mapping**.
4.  Select **Invoice model mapping (Litware)**.
5.  On the Action pane, select **Designer**.
6.  On the **Model to datasource mapping** page, select the **Customer invoice** mapping.
    <br>![Model to datasource mapping page](./media/er-quick-start3-select-customer-mapping.png)
7.  Select **Designer** to open the **Model mapping designer** page.
8.  On the **Data sources** pane, expand the **CustInvoiceJour** data source that represents the **CustInvoiceJour** application table.
9.  Expand **CustInvoiceJour>Relations** to review the list of relations of the many-to-one type of the **CustInvoiceJour** table.
10.  Expand **CustInvoiceJour>Relations>Customers (CustTable)** to access fields and relations of the **Customers (CustTable)** table.
11.  Select the **FederalTaxID_Custom** data source field that has been impemented [earlier](#insert_custom_field).
12.  On the **Data model** pane, expand **Customer information (Customer)**.
13.  Select the **FederalTaxID_Litware** data model field.
14. Select **Bind**.
15. Select **Save**.
    <br>![Model mapping designer page](./media/er-quick-start3-customize-model-mapping.gif)
16. Close the **Model mapping designer** page.
17. Close the **Model to datasource mapping** page.

#### Complete a custom model mapping configuration

You need to [complete](general-electronic-reporting.md#component-versioning) your work with the version 50.19.1 of your custom ER model mapping configuration to make it available for usage.

1.  Go to **Organization administration \> Electronic reporting \> Configurations**.
2.  On the **Configurations** page, in the configuration tree in the left pane, expand **Customer invoice model**.
3.  Expand **Customer invoice model mapping**.
3.  Select **Invoice model mapping (Litware)**.
4.  On the **Versions** FastTab, select **Change status \> Complete**, and then select **OK**.

The status of version 50.19.1 is changed from **Draft** to **Completed**, and the version becomes read-only. A new editable version, 50.19.2, has been added and has a status of **Draft**. You can use this version to make further changes in your custom ER model mapping configuration.

![Configurations page](./media/er-quick-start3-completed-custom-mapping1.png)

> [!NOTE]
> Note that the supported in the ER framework configurations [lifecycle](general-electronic-reporting-manage-configuration-lifecycle.md) does not cover lifecycle of database changes. If you would export the version 50.19.1 of the **Invoice model mapping (Litware)** configuration from the current Finance instance and try to import it to another Finance instance containing no custom **FederalTaxID_Custom** field in the **CustTable** table, an exception will be thrown informing that the imported ER configuration is not compatible with the metadata of the target Finance instance.  

### Customize the format configuration

As a user in the Electronic Reporting Functional Consultant role, you can design your custom ER format.

#### Add a custom format configuration

1.  Go to **Organization administration \> Electronic reporting \> Configurations**.
2.  On the **Configurations** page, in the configuration tree in the left pane, expand **Customer invoice model**.
3.  Expand **UBL Sales invoice**.
4.  Select **Peppol Sales Invoice**.
5.  In the **New** field, select **Derive from Name: Peppol Sales Invoice, Microsoft** to indicate that you want to create your custom ER format configuration based on the provided by Microsoft ER format configuration.
6.  In the **Name** field, type **Peppol Sales Invoice (Litware)**.
7.  In the **Data model** field, select **Invoice model (Litware)** to use your custom data model and model mapping components.
    > [!NOTE] This step is very important. If you missed it, you will not be able to use your custom data model in the configured format.
8.  In the **Data model** field, select the **InvoiceCustomer** root definition.
9.  On the current dialog page, select **Create configuration** to confirm a new ER configuration entry.
    <br>![Configurations page](./media/er-quick-start3-adding-custom-format.png)

The version 11.2.2.1 of the **Peppol Sales Invoice (Litware)** in the **Draft** [status](general-electronic-reporting.md#component-versioning) is available for editing by using the ER Operations designer.

![Configurations page](./media/er-quick-start3-added-custom-format.png)

#### Configure a custom format

You need to modify your custom format by adding a new format element to populate it with the value of a federal tax identification code of an invoiced customer.

1.  Go to **Organization administration \> Electronic reporting \> Configurations**.
2.  On the **Configurations** page, in the configuration tree in the left pane, expand **Customer invoice model**.
3.  Expand **UBL Sales invoice**.
4.  Expand **Peppol Sales Invoice**.
5.  Select **Peppol Sales Invoice (Litware)**.
6.  On the Action pane, select **Designer**.
7.  In the format tree, expand **XMLHeader**.
8.  Expand **XMLHeader \> Invoice**.
9.  Expand **XMLHeader \> Invoice \> cac:AccountingCustomerParty**.
10. Expand **XMLHeader \> Invoice \> cac:AccountingCustomerParty \> cac:Party**.
11. Expand **XMLHeader \> Invoice \> cac:AccountingCustomerParty \> cac:Party \> cac:PartyTaxScheme**.
12. Expand **XMLHeader \> Invoice \> cac:AccountingCustomerParty \> cac:Party \> cac:PartyTaxScheme \> cac:TaxScheme**.
13. Select **XMLHeader \> Invoice \> cac:AccountingCustomerParty \> cac:Party \> cac:PartyTaxScheme \> cac:TaxScheme \> cbc:ID**.
14. Select **Add**.
15. Select **XML \> Attribute**.
16. On the **Component property** dialog page, in the **Name** field, type **FederalTaxID**.
17. Select **OK** to confirm a new format element entry for making a new **FederalTaxID** XML attribute in a generated XML file.
18. Select **XMLHeader \> Invoice \> cac:AccountingCustomerParty \> cac:Party \> cac:PartyTaxScheme \> cac:TaxScheme \> cbc:ID \> FederalTaxID**.
19. Select **Move up**.
    <br>![Format designer page](./media/er-quick-start3-customized-format.png)

#### Configure a custom format mapping

1.  On the **Format designer** page, select the **Mapping** tab.
2.  Expand the **Invoice** data source of the **Model** type.
3.  Expand **Invoice \> Customer information (Customer)**.
4.  Select **Invoice \> Customer information (Customer) \> FederalTaxID_Litware**.
    <br>![Format designer page](./media/er-quick-start3-customized-format-mapping.png)
5.  Select **Bind**.
6.  Select the **Invoice** data source of the **Model** type.
    1. Select **Edit**.
    2. In the **Version** field, select the version 1 of your custom data model.
    3. Select **OK**.    
7.  Select **Save**.
8.  Close the **Format designer** page.

#### Complete a custom format configuration

You need to [complete](general-electronic-reporting.md#component-versioning) your work with the version 11.2.2.1 of your custom ER format configuration to make it available for usage.

1.  Go to **Organization administration \> Electronic reporting \> Configurations**.
2.  On the **Configurations** page, in the configuration tree in the left pane, expand **Customer invoice model**.
3.  Expand **UBL Sales invoice**.
4.  Expand **Peppol Sales Invoice**.
5.  Select **Peppol Sales Invoice (Litware)**.
6.  On the **Versions** FastTab, select **Change status \> Complete**, and then select **OK**.

The status of version 11.2.2.1 is changed from **Draft** to **Completed**, and the version becomes read-only. A new editable version, 11.2.2.2, has been added and has a status of **Draft**. You can use this version to make further changes in your custom ER format configuration.

![Configurations page](./media/er-quick-start3-completed-custom-format1.png)

## <a name="ConfigureAR2"></a>Configure the AR parameters to start using the custom ER configurations

1.  Go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.
2.  Select the **Electronic documents** tab.
3.  On the **Set up options for electronic documents** page, on the **Electronic reporting** tab, in the **Sales and Free text invoice** field, select **Peppol Sales Invoice (Litware)**.
4.  Select **Save**.

![Set up options for electronic documents page](./media/er-quick-start3-configure-ar2.png)

## <a name="ConfigureCustomer2"></a>Update a customer record by adding a federal tax identification code

1.  Go to **Accounts receivable** \> **Customers** \> **All customers**.
2.  On the **All customers** page, open the **DE-014** customer account link.
3.  On the **General** FastTab, in the **Federal Tax ID** field, type **LITWARE-6789**.
4.  Select **Save**.
    <br>![All customers page](./media/er-quick-start3-added-tax-id-value.png)
5.  Close the **All customers** page.

## <a name="ProcessInvoice2"></a>Process a customer invoice by using the custom ER configurations

### Select and send a posted invoice

1.  Go to **Accounts receivables \> Invoices \> All free text invoices**.
2.  On the **Free text invoice** page, select the earlier added and posted invoice.
3.  On the Action pane, in the **Document** group, select **Send \> Original**.
4.  Close the **Free text invoice** page.

### Analyze a generated e-invoice

1.  Go to **Organization administration \> Electronic reporting \> Electronic reporting jobs**.
2.  On the **Electronic reporting jobs** page, select the latest record having the **Send the eInvoice XML** task description.
3.  Select **Show files** to access the list of generated files.
4.  Select **Open** to download the generated e-invoice XML file.
5.  Analyze the generated e-invoice XML file. 
    <br>![Preview of the generated e-invoice XML file](./media/er-quick-start3-e-invoice2.png)

>[!NOTE] Note that, in accordance to your customization, the customer tax schema, in addition to the `schemeID` and `schemeAgencyID` XML attributes, includes now the custom `FederalTaxID` XML attribute. The value of this new XML attribute is specified by the federal tax id **LITWARE-6789** that was entered for an invoiced customer.

## <a name="ImportERConfigurations2"></a>Import the latest versions of standard ER configurations

To keep the set of standard ER configurations in your Finance instance [up-to-date](general-electronic-reporting-manage-configuration-lifecycle.md), you must import new versions of them whenever they became available in the ER [repository](general-electronic-reporting.md#Repository) that was configured for that instance.

1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**.
2. On the **Localization configurations** page, in the **Configuration providers** section, select the **Microsoft** tile, and then select **Repositories** to view the list of repositories for the Microsoft provider.
3. On the **Configuration repositories** page, select the repository of the **Global** type, and then select **Open**. If you're prompted for authorization to connect to Regulatory Configuration Service, follow the authorization instructions.
4. On the **Configuration repository** page, in the configuration tree in the left pane, select the **Peppol Sales Invoice** format configuration.
5. On the **Versions** FastTab, select version **32.6.7** of the selected ER format configuration that has been released to support customers electronic invoices in PEPPOL BIS 3 format. See the [KB4490320](https://support.microsoft.com/help/4490320/an-update-for-european-union-to-support-export-of-customers-electronic) for more.
6. Select **Import** to download the selected version from the Global repository to the current Finance instance.

![Configuration repository page](./media/er-quick-start3-import-solution2.png)

See [Import updated versions of ER configurations](er-download-updated-versions-global-repo.md) to learn how it can be automated.

### Review the imported ER configurations

1.  Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**.
2.  On the **Localization configurations** page, in the **Configurations** section, select the **Reporting configurations** tile.
3.  Expand the **Configuration components** FastTab.
4.  On the **Configurations** page, in the configuration tree in the left pane, expand **Invoice model**.
    > [!NOTE] The name of the **Customer invoice model** has been changed to the **Invoice model** in one of the imported ER data model configurations.
5.  In the configuration tree in the left pane, expand **Invoice model mapping**.
    > [!NOTE] The name of the **Customer invoice model mapping** has been changed to the **Invoice model mapping** in one of the imported ER model mapping configurations.
6.  Expand **UBL Sales invoice**.
7.  Expand **Peppol Sales Invoice**.

Notice that, in addition to the selected **Peppol Sales Invoice** ER format, the latest versions of other required ER configurations were imported. Since new versions of ER configurations are constantly published to the Global and LCS repositories to keep the corresponding ER solutions compliant with new requirements, at the current moment the latest versions of the required data model configuration and its model mapping configurations were imported.

Make sure that the following ER configurations are eventually available in the configuration tree:

- **Invoice model** ER data model configuration:
    - Version 206 (or higher) of it contains the version 24 (or higher) of the data model ER component that represents the data structure of the invoicing business domain. This ER configuration has been imported as an ancestor of the latest available **Invoice model mapping** ER model mapping configuration.
    <br>![Configurations page](./media/er-quick-start3-imported-solution2b1.png)
- **Invoice model mapping** ER model mapping configuration:
    - Version 206.132 (or higher) of it has been imported as the latest implementation of the version 206 of the **Invoice model** ER data model configuration. It contains several model mapping ER components that describe how the data model is filled in with application data at runtime.
    <br>![Configurations page](./media/er-quick-start3-imported-solution2b2.png)
- **UBL Sales invoice** ER format configuration:
    - Version 32.6 of it contains the format and format mapping ER components. The format component specifies the report layout. The format mapping component contains the model data source and specifies how the report layout is filled in by using this data source at runtime. This ER format was configured to generate e-invoices in UBL format. It has been imported as a parent of the selected for import **Peppol Sales Invoice** ER format.
- **Peppol Sales Invoice** ER format configuration:
    - Version 32.6.7 of it contains the format and format mapping ER components that were configured to generate e-invoices in PEPPOL format.
    <br>![Configurations page](./media/er-quick-start3-imported-solution2b3.png)

## <a name="RebaseCustomERConfigurations"></a>Adopt the changes in the new standard ER configurations in your custom ER configurations

### Adopt your custom ER data model

1.  Go to **Organization administration \> Electronic reporting \> Configurations**.
2.  On the **Configurations** page, in the configuration tree in the left pane, expand **Invoice model**.
3.  Select **Invoice model (Litware)**.
4.  On the **Versions** FastTab, for the draft version 50.2 of the selected data model configuration, select **Rebase**.
5.  In the **Target** version field, confirm the selection of the version 206 of the base ER data model configuration.
6.  Select **OK**.
    > The draft version of your custom ER data model configuration has been renumbered from 50.2 to 206.2 indicating that it now contains your customization that has been merged with the changes in the latest version 206 of the base ER data model configuration.
    >
    > [!NOTE] The rebase action is reversible. To cancel this rebase, select version 50.1 of the **Invoice model (Litware)** model on the **Versions** FastTab, and then select **Get this version**. Version 206.2 will then be renumbered back to 50.2, and the content of draft version 50.2 will match the content of version 50.1.
7.  On the **Versions** FastTab, select **Change status \> Complete**, and then select **OK**.

The status of version 206.2 is changed from **Draft** to **Completed**, and the version becomes read-only. A new editable version, 206.3, has been added and has a status of **Draft**. You can use this version to make further changes in your custom ER data model configuration.

![Configurations page](./media/er-quick-start3-completed-custom-model2.png)

### Adopt your custom ER model mapping

1.  Go to **Organization administration \> Electronic reporting \> Configurations**.
2.  On the **Configurations** page, in the configuration tree in the left pane, expand **Invoice model**.
3.  Expand **Invoice model mapping**.
3.  Select **Invoice model mapping (Litware)**.
4.  On the **Versions** FastTab, for the draft version 50.19.2 of the selected model mapping configuration, select **Rebase**.
5.  In the **Target** version field, confirm the selection of the version 206.132 of the base ER model mapping configuration.
6.  Select **OK**.
    > The draft version of your custom ER model mapping configuration has been renumbered from 50.19.2 to 206.132.2 indicating that it now contains your customization that has been merged with the changes in the latest version 206.132 of the base ER model mapping configuration.
    > Note that some rebase conflicts has been discovered. They must be resolved manually.
    <br>![Configurations page](./media/er-quick-start3-rebase-conflicts-model-mapping1.png)
7.  On the Action pane, select **Designer**.
8.  In the list of mappings, select **Customer Invoice**.
    1.  For each rebase conflict in this case, select **Retain own value** as you need to keep the version number of your custom data model for every mentioned component.
    <br>![Model mapping designer page](./media/er-quick-start3-rebase-conflicts-model-mapping2.png)
    2. Select **Save**.
    3. Close the **Model mapping designer** page.
9. In the list of mappings, select **Project Invoice**.
    1. For each rebase conflict in this case, select **Retain own value** as you need to keep the version number of your custom data model for every mentioned component.
    2. Select **Save**.
    3. Close the **Model mappings** page.
    > [!NOTE] The rebase action is reversible. To cancel this rebase, select version 50.19.1 of the **Invoice model mapping (Litware)** model mapping on the **Versions** FastTab, and then select **Get this version**. Version 206.132.2 will then be renumbered back to 50.19.2, and the content of draft version 50.19.2 will match the content of version 50.19.1.
10. On the **Versions** FastTab, select **Change status \> Complete**, and then select **OK**.

The status of version 206.132.2 is changed from **Draft** to **Completed**, and the version becomes read-only. A new editable version, 206.132.3, has been added and has a status of **Draft**. You can use this version to make further changes in your custom ER model mapping configuration.

![Configurations page](./media/er-quick-start3-completed-custom-mapping2.png)

### Adopt your custom ER format

1.  Go to **Organization administration \> Electronic reporting \> Configurations**.
2.  On the **Configurations** page, in the configuration tree in the left pane, expand **Invoice model**.
3.  Expand **UBL Sales invoice**.
4.  Expand **Peppol Sales Invoice**.
5.  Select **Peppol Sales Invoice (Litware)**.
6.  On the **Versions** FastTab, for the draft version 11.2.2.2 of the selected format configuration, select **Rebase**.
7.  In the **Target** version field, confirm the selection of the version 32.6.7 of the base ER format configuration.
8.  Select **OK**.
    > The draft version of your custom ER format configuration has been renumbered from 11.2.2.2 to 32.6.7.2 indicating that it now contains your customization that has been merged with the changes in the latest version 32.6.7 of the base ER format configuration.
    > Note that some rebase conflicts has been discovered. They must be resolved manually.
9.  On the Action pane, select **Designer**.
    1. For each rebase conflict, select **Retain own value** as you need to keep the version number of your custom data model for every mentioned component.
    2. Select **Save**.
10. Select the **Mapping** tab.
    1. Select the **Invoice** data source of the **Model** type.
    2. Select **Edit**.
    3. In the **Version** field, select the version 2 of your custom data model.
    4. Select **OK**.
11. Select **Save**.
    > [!NOTE] The rebase action is reversible. To cancel this rebase, select version 11.2.2.1 of the **Peppol Sales Invoice (Litware)** format on the **Versions** FastTab, and then select **Get this version**. Version 32.6.7.2 will then be renumbered back to 11.2.2.2, and the content of draft version 11.2.2.2 will match the content of version 11.2.2.1.
12. Close the **Format designer** page.
13. On the **Versions** FastTab, select **Change status \> Complete**, and then select **OK**.

The status of version 32.6.7.2 is changed from **Draft** to **Completed**, and the version becomes read-only. A new editable version, 32.6.7.3, has been added and has a status of **Draft**. You can use this version to make further changes in your custom ER format configuration.

![Configurations page](./media/er-quick-start3-completed-custom-format2.png)

## <a name="ProcessInvoice3"></a>Process a customer invoice by using new versions of the custom ER configurations

### Select and send a posted invoice

1.  Go to **Accounts receivables \> Invoices \> All free text invoices**.
2.  On the **Free text invoice** page, select the earlier added and posted invoice.
3.  On the Action pane, in the **Document** group, select **Send \> Original**.
    >[!NOTE] As you have now two versions of the **Peppol Sales Invoice (Litware)** ER format configuration and each of them contains no [effective date](general-electronic-reporting.md#component-date-effectivity) value, the latest version of this ER format configuration is used to generate an e-invoice.
4.  Close the **Free text invoice** page.

### Analyze a generated e-invoice

1.  Go to **Organization administration \> Electronic reporting \> Electronic reporting jobs**.
2.  On the **Electronic reporting jobs** page, select the latest record having the **Send the eInvoice XML** task description.
3.  Select **Show files** to access the list of generated files.
4.  Select **Open** to download the generated e-invoice XML file.
5.  Analyze the generated e-invoice XML file.
    >[!NOTE] Note that, in accordance to your customization, the customer tax schema, in addition to the `schemeID` and `schemeAgencyID` XML attributes, still contains the custom `FederalTaxID` XML attribute. 
    >
    > In addition to that, due to the merge of changes in the new version of the base **UBL Sales invoice** format with your customization, the text of the `cbc:CustomizationID` XML element has been changed from **urn:www.cenbii.eu:transaction:biicoretrdm010:ver1.0:# urn:www.peppol.eu:bis:peppol5a:ver1.0** to **urn:cen.eu:en16931:2017#compliant#urn:fdc:peppol.eu:2017:poacc:billing:3.0**.
    <br>![Preview of the generated e-invoice XML file](./media/er-quick-start3-e-invoice3.png)

## Additional resources

- [Electronic Reporting overview](general-electronic-reporting.md)
- [Download ER configurations from Lifecycle Services](download-electronic-reporting-configuration-lcs.md)
- [Download ER configurations from Global repository of Configuration service](er-download-configurations-global-repo.md)
- [Create a free text invoice](https://docs.microsoft.com/dynamics365/finance/accounts-receivable/create-free-text-invoice-new) 
- [Create and work with custom fields](https://docs.microsoft.com/dynamics365/fin-ops-core/fin-ops/get-started/user-defined-fields)
