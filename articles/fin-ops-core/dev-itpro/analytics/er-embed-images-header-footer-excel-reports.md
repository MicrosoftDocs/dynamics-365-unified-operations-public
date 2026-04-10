---
title: Design an ER format to generate a report in Excel format with embedded images in page headers or footers
description: Learn about how to use Electronic reporting (ER) to generate business documents that have images and shapes embedded in page headers or footers.
author: kfend
ms.author: filatovm
ms.topic: how-to
ms.date: 04/08/2026
ms.custom: 
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2021-06-01
ms.search.form: EROperationDesigner, ERParameters
ms.dyn365.ops.version: 10.0.21
ms.assetid: 
---

# Design an ER format to generate a report in Excel format with embedded images in page headers or footers

[!include[banner](../includes/banner.md)]

This article explains how a user in the System Administrator or Electronic Reporting Functional Consultant role can perform these tasks:

- Configure parameters for the [Electronic reporting (ER)](general-electronic-reporting.md) framework.
- Import ER [configurations](general-electronic-reporting.md#Configuration) that Microsoft [provides](general-electronic-reporting.md#Provider) and use them to generate [free text invoices](../../../finance/accounts-receivable/create-free-text-invoice-new.md), based on a [template](er-fillable-excel.md#excel-file-component) in Microsoft Excel format.
- Create a [custom (derived)](general-electronic-reporting.md#building-a-format-by-selecting-another-format-as-a-base-customization) version of a standard ER format configuration that Microsoft provides.
- Modify the custom ER format configuration so that it generates a free text invoice report that has a company logo image in the footer.

You can complete the procedures in this article in the **USMF** company. No coding is required. Before you begin, download and save the following file.

| Description        | File name |
|--------------------|-----------|
| Company logo image | [Company logo.png](https://download.microsoft.com/download/8/2/e/82e6bd81-caac-4e9a-bfce-1392ce7c8616/Companylogo.png) |

## Content

- [Configure the legal entity](#ConfigureLegalEntity)
- [Configure the ER framework](#ConfigureFramework)

  - [Configure ER parameters](#ConfigureParameters)
  - [Activate an ER configuration provider](#ActivateProvider)

    - [Review the list of ER configuration providers](#ReviewProvidersList)
    - [Add a new ER configuration provider](#AddProvider)
    - [Activate the new ER configuration provider](#ActivateAddedProvider)

- [Import the standard ER format configurations](#ImportERSolution1)

  - [Import the standard ER configurations](#ImportERFormat)
  - [Review the imported ER configurations](#ReviewImportedERSolution)

- [Print a free text invoice by using the standard ER format](#PrintInvoice1)

  - [Set up print management](#ConfigurePrintManagement1)
  - [Print a free text invoice](#ProcessInvoice1)

- [Customize the standard ER format](#CustomizeProvidedFormat)

  - [Create a custom format](#DeriveProvidedFormat)
  - [Edit the custom format](#ConfigureDerivedFormat)
  - [Mark the custom format as runnable](#MarkFormatRunnable)

- [Print a free text invoice by using the custom ER format](#PrintInvoice2)

  - [Set up print management](#ConfigurePrintManagement2)
  - [Print a free text invoice](#ProcessInvoice2)

- [Additional resources](#References)

## <a id="ConfigureLegalEntity"></a>Configure the legal entity

1. Go to **Organization administration** > **Organizations** > **Legal entities**.
1. On **Legal entities**, on the **Report company logo image** FastTab, select **Change**.
1. In **Select image file to upload**, select **Browse**, and select the **Company logo.png** file that you downloaded earlier.
1. Select **Save**, and then close **Legal entities**.

:::image type="content" source="./media/er-embed-images-header-footer-excel-reports-company-logo-image.png" alt-text="Screenshot of company logo image selected on the Legal entities page.":::

## <a id="ConfigureFramework"></a>Configure the ER framework

As a user in the Electronic Reporting Functional Consultant role, you must configure the minimal set of ER parameters before you can start to use the ER framework to design a custom version of a standard ER format.

### <a id="ConfigureParameters"></a>Configure ER parameters

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
1. On **Localization configurations**, in the **Related links** section, select **Electronic reporting parameters**.
1. On **Electronic reporting parameters**, on the **General** tab, set the **Enable design mode** option to **Yes**.
1. On the **Attachments** tab, set the following parameters:

    - In the **Configurations** field, select the **File** type for the **USMF** company.
    - In the **Job archive**, **Temporary**, **Baseline**, and **Others** fields, select the **File** type.

For more information about ER parameters, see [Configure the ER framework](electronic-reporting-er-configure-parameters.md).

### <a id="ActivateProvider"></a>Activate an ER configuration provider

Every ER configuration that you add is marked as owned by an ER configuration provider. Use the ER configuration provider that you activate in the **Electronic reporting** workspace for this purpose. Therefore, you must activate an ER configuration provider in the **Electronic reporting** workspace before you start to add or edit ER configurations.

> [!NOTE]
> Only the configuration owner can edit an ER configuration. Before you can edit an ER configuration, you must activate the appropriate ER configuration provider in the **Electronic reporting** workspace.

#### <a id="ReviewProvidersList"></a>Review the list of ER configuration providers

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
1. On **Localization configurations**, in the **Related links** section, select **Configuration providers**.
1. On **Configuration provider table**, each provider record has a unique name and URL. Review the contents of this page. If a record for **Litware, Inc.** (`https://www.litware.com`) already exists, skip the next procedure, [Add a new ER configuration provider](#AddProvider).

#### <a id="AddProvider"></a>Add a new ER configuration provider

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
1. On **Localization configurations**, in the **Related links** section, select **Configuration providers**.
1. On **Configuration providers**, select **New**.
1. In the **Name** field, enter **Litware, Inc.**
1. In the **Internet address** field, enter `https://www.litware.com`.
1. Select **Save**.

#### <a id="ActivateAddedProvider"></a>Activate the new ER configuration provider

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
1. On **Localization configurations**, in the **Configuration providers** section, select the **Litware, Inc.** tile, and then select **Set active**.

For more information about ER configuration providers, see [Create configuration providers and mark them as active](tasks/er-configuration-provider-mark-it-active-2016-11.md).

## <a id="ImportERSolution1"></a>Import the standard ER format configurations

### <a id="ImportERFormat"></a>Import the standard ER configurations

To add the standard ER configurations to your current instance of Dynamics 365 Finance, import them from the ER [repository](general-electronic-reporting.md#Repository) that you configured for that instance.

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
1. On **Localization configurations**, in the **Configuration providers** section, select the **Microsoft** tile, and then select **Repositories** to view the list of repositories for the **Microsoft** provider.
1. On **Configuration repositories**, select the repository of the **Global** type, and then select **Open**. If you're prompted for authorization to connect to [Regulatory Configuration Service](../../../finance/localizations/rcs-overview.md), follow the authorization instructions.
1. On **Configuration repository**, in the configuration tree in the left pane, select the **Free text invoice (Excel)** format configuration.
1. On the **Versions** FastTab, select the latest version (for example, **240.112**) of the selected ER format configuration.
1. Select **Import** to download the selected version from the Global repository to the current Finance instance.

:::image type="content" source="./media/er-embed-images-header-footer-excel-reports-import-solution.png" alt-text="Screenshot of importing the standard ER configurations on the Configuration repository page.":::

> [!TIP]
> If you have trouble accessing the [Global repository](er-download-configurations-global-repo.md), you can [download configurations](download-electronic-reporting-configuration-lcs.md) from Microsoft Dynamics Lifecycle Services instead.

### <a id="ReviewImportedERSolution"></a>Review the imported ER configurations

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
1. On **Localization configurations**, in the **Configurations** section, select the **Reporting configurations** tile.
1. On **Configurations**, in the configuration tree in the left pane, expand **Invoice model**.
1. In addition to the selected **Free text invoice (Excel)** ER format, the import process brings in other required ER configurations. Make sure that the following ER configurations are available in the configuration tree:

    - **Invoice model** – This configuration contains the data model ER component that represents the data structure of the invoicing business domain.
    - **Invoice model mapping** – This configuration contains the model mapping ER component that describes how the data model is filled in with application data at runtime.
    - **Free text invoice (Excel)** – This configuration contains the format and format mapping ER components. The format component specifies the report layout, based on a template in Excel format. The format mapping component contains the model data source and specifies how this data source is used to fill in the report layout at runtime.

:::image type="content" source="./media/er-embed-images-header-footer-excel-reports-imported-solution.png" alt-text="Screenshot of imported ER configurations on the Configurations page.":::

## <a id="PrintInvoice1"></a>Print a free text invoice by using the standard ER format

### <a id="ConfigurePrintManagement1"></a>Set up print management

1. Go to **Accounts receivable** > **Invoices** > **All free text invoices**.
1. On **Free text invoice**, select the **FTI-00000002** invoice. Then, on the Action Pane, on the **Invoice** tab, in the **Print management** group, select **Print management**.
1. On **Print management setup**, in the tree on the left, expand **Module - accounts receivable** > **Documents** > **Free text invoice**, and then select the **Original \<Default\>** item.
1. In the **Report format** field, select **Free text invoice (Excel)**.
1. Select the **Esc** key to leave **Print management setup** and return to **Free text invoice**.

:::image type="content" source="./media/er-embed-images-header-footer-excel-reports-print-management.png" alt-text="Screenshot of print management settings for a free text invoice in the standard ER format on the Print management setup page.":::

### <a id="ProcessInvoice1"></a>Print a free text invoice

1. On **Free text invoice**, make sure that the **FTI-00000002** invoice is still selected. Then, on the Action Pane, on the **Invoice** tab, in the **Document** group, select **Print** \> **Selected**.
1. Download the generated invoice in Excel format, and open it for preview.
1. Notice that, in accordance with the structure of the Excel template for the provided ER format, the page footer of the generated invoice contains information about the current page number and the total number of pages in the report.

:::image type="content" source="./media/er-embed-images-header-footer-excel-reports-print-invoice1.gif" alt-text="Screenshot of generated free text invoice.":::

## <a id="CustomizeProvidedFormat"></a>Customize the standard ER format

For the example in this section, use the ER configurations that Microsoft provides to generate a free text invoice in Excel format. However, add a customization to put a company logo image in the page footer of generated invoices.

In this case, as the representative of Litware, Inc., create (derive) a new ER format configuration that's based on the Microsoft-provided **Free text invoice (Excel)** configuration.

### <a id="DeriveProvidedFormat"></a>Create a custom format

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. On **Configurations**, in the configuration tree in the left pane, expand **Invoice model**, and then select **Free text invoice (Excel)**. Litware, Inc. uses the imported version (for example, **240.112**) of this ER format configuration as the base for the custom version.
1. Select **Create configuration** to open the drop-down dialog box. Use this dialog box to create a new configuration for a custom payment format.
1. In the **New** field group, select the **Derive from Name: Free text invoice (Excel), Microsoft** option.
1. In the **Name** field, enter **Free text invoice (Excel) custom**.
1. Select **Create configuration**.

:::image type="content" source="./media/er-embed-images-header-footer-excel-reports-add-derived-format.png" alt-text="Screenshot of creating a configuration for a custom payment format in the Create configuration drop-down dialog box.":::

Version 240.112.1 of the **Free text invoice (Excel) custom** ER format configuration is created. This version has a status of **Draft** and can be edited. The current content of your custom ER format matches the content of the format that Microsoft provides.

:::image type="content" source="./media/er-embed-images-header-footer-excel-reports-derived-format-configuration1.png" alt-text="Screenshot of new version of the ER format configuration created on the Configurations page.":::

### <a id="ConfigureDerivedFormat"></a>Edit the custom format

Configure your custom format so that a company logo image appears in the footer on every page of the report.

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. On **Configurations**, in the configuration tree in the left pane, expand **Payment model**, and then select **Free text invoice (Excel) custom**.
1. On the **Versions** FastTab, select version **240.112.1** of the selected configuration.
1. Select **Designer**.
1. On **Format designer**, select **Show details** to view more information about the format elements.
1. Expand and review the following elements:

    - The **Free text invoice** element of the **Excel** type. This element generates an invoice in Excel workbook format.
    - The **Free text invoice \\ Invoice** element of the **Sheet** type. This element generates a worksheet of the generated Excel workbook.
    - The **Free text invoice \\ Invoice \\ Footer** element of the **Footer** type. This element fills in an invoice footer.

1. Select the **Free text invoice \\ Invoice \\ Footer** element.

    :::image type="content" source="./media/er-embed-images-header-footer-excel-reports-derived-format0.png" alt-text="Screenshot of footer element in the ER Operations designer.":::

    > [!NOTE]
    > Every page footer of a generated invoice contains information about the current page number and the total number of pages in the report. As you can see, the **Free text invoice \\ Invoice \\ Footer** element contains no child elements. Therefore, the Excel template that you're using is configured to show paging details in the center of every report's footer.

1. Select **Add**, and then select the **Excel \\ Picture** type of the format element that you're adding:

    1. In the **Alignment** field, select **Right**.
    1. In the **Scale the height** field, select **Relative**.
    1. In the **Scale in percentage** field, enter **70**.
    1. Select **OK**.

        > [!NOTE]
        > Use the **Excel \\ Picture** element to add a company logo image and align it on the right side of the page footer.

    :::image type="content" source="./media/er-embed-images-header-footer-excel-reports-derived-format1.png" alt-text="Screenshot of properties of the Picture element in the Component properties dialog box.":::

1. In the format structure tree on the left, select the **Picture** element that you just added. On the **Mapping** tab, expand the **model** data source.
1. Expand **model.Payment** > **model.InvoiceBase** > **model.InvoiceBase.CompanyInfo**, and then select the **model.InvoiceBase.CompanyInfo.Logo** data source field. The data source field of the [Container](er-formula-supported-data-types-composite.md#container) type exposes the company logo image as media content.
1. Select **Bind**. The **Picture** format element is now bound with the **model.InvoiceBase.CompanyInfo.Logo** data source field. Therefore, at runtime, a company logo image appears in the footer of generated invoices.

    :::image type="content" source="./media/er-embed-images-header-footer-excel-reports-derived-format2.png" alt-text="Screenshot of picture format element bound with the model.InvoiceBase.CompanyInfo.Logo data source field in the ER Operations designer.":::

1. Select **Save**, and then close the **Designer** page.

### <a id="MarkFormatRunnable"></a>Mark the custom format as runnable

After you create the first version of the custom format, it has a status of **Draft**. You can run the format to test it. To run the report, process a vendor payment by using the payment method that refers to your custom ER format. By default, when you call an ER format from the application, only versions that have a status of **Completed** or **Shared** are considered. This behavior helps prevent ER formats that have unfinished designs from being used. However, for your test runs, you can force the application to use the version of your ER format that has a status of **Draft**. In this way, you can adjust the current format version if any modifications are required. For more information, see [Applicability](electronic-reporting-destinations.md#applicability).

To use the draft version of an ER format, you must explicitly mark the ER format.

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. On **Configurations**, on the Action Pane, on the **Configurations** tab, in the **Advanced settings** group, select **User parameters**.
1. In **User parameters**, set the **Run settings** option to **Yes**, and then select **OK**.
1. Select **Edit** to make the current page editable. In the configuration tree in the left pane, select **Free text invoice (Excel) custom**.
1. Set the **Run Draft** option to **Yes**.

:::image type="content" source="./media/er-embed-images-header-footer-excel-reports-derived-format-configuration2.png" alt-text="Screenshot of marking the custom format as runnable on the Configurations page.":::

## <a id="PrintInvoice2"></a>Print a free text invoice by using the custom ER format

### <a id="ConfigurePrintManagement2"></a>Set up print management

1. Go to **Accounts receivable** > **Invoices** > **All free text invoices**.
1. On **Free text invoice**, select the **FTI-00000002** invoice. Then, on the Action Pane, on the **Invoice** tab, in the **Print management** group, select **Print management**.
1. On **Print management setup**, in the tree on the left, expand **Module - accounts receivable** > **Documents** > **Free text invoice**, and then select the **Original** **\<Default\>** item.
1. In the **Report format** field, select **Free text invoice (Excel) custom**.
1. Select **Esc** to leave **Print management setup** and return to **Free text invoice**.

### <a id="ProcessInvoice2"></a>Print a free text invoice

1. On **Free text invoice**, make sure that the **FTI-00000002** invoice is still selected. Then, on the Action Pane, on the **Invoice** tab, in the **Document** group, select **Print** \> **Selected**.
1. Download the generated invoice in Excel format, and open it for preview.
1. Notice that, in accordance with the structure of the custom ER format, the page footer of the generated invoice contains a company logo image in addition to information about the report's paging.

:::image type="content" source="./media/er-embed-images-header-footer-excel-reports-print-invoice2.gif" alt-text="Screenshot of generated free text invoice with a company logo image in the page footer.":::

## <a id="References"></a>Additional resources

- [Design a configuration for generating documents in Excel format](er-fillable-excel.md)
- [Embed images and shapes in documents that you generate by using ER](electronic-reporting-embed-images-shapes.md)
