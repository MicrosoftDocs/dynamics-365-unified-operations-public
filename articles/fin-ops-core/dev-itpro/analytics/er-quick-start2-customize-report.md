---
title: Adjust an ER format to generate a custom electronic document
description: Learn how to adjust a Microsoft-provided Electronic reporting (ER) format so that it generates a custom electronic document.
author: kfend
ms.author: filatovm
ms.topic: how-to
ms.date: 04/08/2026
ms.reviewer: johnmichalak
ms.collection: get-started
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: ERWorkspace, ERSolutionTable, ERParameters, ERDataModelDesigner, ERModelMappingTable, ERModelMappingDesigner, EROperationDesigner, ERVendorTable
ms.dyn365.ops.version: Version 7.0.0
ms.assetid: 
---

# Adjust an ER format to generate a custom electronic document

[!include[banner](../includes/banner.md)]

The procedures in this article explain how a user in the System Administrator or Electronic Reporting Functional Consultant role can perform these tasks:

- Configure parameters for the [Electronic reporting (ER) framework](general-electronic-reporting.md).
- Import ER configurations that Microsoft provides and that are used to generate a payment file while a [vendor payment](../../../finance/cash-bank-management/tasks/vendor-payment-overview.md) is being processed.
- Create a custom version of a standard ER format configuration that Microsoft provides.
- Modify the custom ER format configuration so that it generates payment files that meet the requirements of a specific bank.
- Adopt changes that are made to the standard ER format configuration in the custom ER format configuration.

You can perform all the following procedures in the **GBSI** company. No coding is required.

- [Configure the ER framework](#ConfigureFramework)

  - [Configure ER parameters](#ConfigureParameters)
  - [Activate an ER configuration provider](#ActivateProvider)

    - [Review the list of ER configuration providers](#ReviewProvidersList)
    - [Add a new ER configuration provider](#ActivateProvider)
    - [Activate an ER configuration provider](#ActivateAddedProvider)

- [Import the standard ER format configurations](#ImportERSolution1)

  - [Import the standard ER configurations](#ImportERFormat1)
  - [Review the imported ER configurations](#ReviewImportedERSolution)

- [Prepare a vendor payment for processing](#PrepareVendorPayment)

  - [Add bank information for a vendor account](#AddBankAccount)
  - [Enter a vendor payment](#EnterVendorPayment)

- [Process a vendor payment by using the standard ER format](#ProcessVendorPayment1)

  - [Set up the electronic payment method](#ConfigureMethodOfPayment1)
  - [Process a vendor payment](#ProcessPayment1)

- [Customize the standard ER format](#CustomizeProvidedFormat)

  - [Create a custom format](#DeriveProvidedFormat)
  - [Edit a custom format](#ConfigureDerivedFormat)
  - [Mark a custom format as runnable](#MarkFormatRunnable)

- [Process a vendor payment by using the custom ER format](#ProcessVendorPayment2)

  - [Set up the electronic payment method](#ConfigureMethodOfPayment2)
  - [Process a vendor payment](#ProcessPayment2)

- [Import new versions of the standard ER format configurations](#ImportERSolution2)

  - [Import new versions of the standard ER configurations](#ImportERFormat2)
  - [Review the imported ER format configurations](#ReviewImportedERFormat)

- [Adopt the changes in the new version of an imported format in a custom format](#AdoptNewBaseVersion)

  - [Complete the current draft version of a custom format](#CompleteDerivedFormat)
  - [Rebase a custom format to a new base version](#RebaseDerivedFormat)
  - [Process a vendor payment by using a rebased ER format](#ProcessPayment3)

- [Additional resources](#References)

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

Each ER configuration that you add is owned by an ER configuration provider. The ER configuration provider that you activate in the **Electronic reporting** workspace serves this role. Therefore, you must activate an ER configuration provider in the **Electronic reporting** workspace before you start to add or edit ER configurations.

> [!NOTE]
> Only the owner of an ER configuration can edit it. Therefore, before you can edit an ER configuration, you must activate the appropriate ER configuration provider in the **Electronic reporting** workspace.

#### <a id="ReviewProvidersList"></a>Review the list of ER configuration providers

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
1. On **Localization configurations**, in the **Related links** section, select **Configuration providers**.
1. On **Configuration provider table**, each provider record has a unique name and URL. Review the contents of this page. If a record for **Litware, Inc.** (`https://www.litware.com`) already exists, skip the next procedure, [Add a new ER configuration provider](#ActivateProvider).

#### <a id="ActivateProvider"></a>Add a new ER configuration provider

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
1. On **Localization configurations**, in the **Related links** section, select **Configuration providers**.
1. On **Configuration providers**, select **New**.
1. In the **Name** field, enter **Litware, Inc.**
1. In the **Internet address** field, enter `https://www.litware.com`.
1. Select **Save**.

#### <a id="ActivateAddedProvider"></a>Activate an ER configuration provider

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
1. On **Localization configurations**, in the **Configuration providers** section, select the **Litware, Inc.** tile, and then select **Set active**.

For more information about ER configuration providers, see [Create configuration providers and mark them as active](tasks/er-configuration-provider-mark-it-active-2016-11.md).

## <a id="ImportERSolution1"></a>Import the standard ER format configurations

### <a id="ImportERFormat1"></a>Import the standard ER configurations

To add the standard ER configurations to your current instance of Microsoft Dynamics 365 Finance, import them from the ER [repository](general-electronic-reporting.md#Repository) that you configured for that instance.

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
1. On **Localization configurations**, in the **Configuration providers** section, select the **Microsoft** tile, and then select **Repositories** to view the list of repositories for the Microsoft provider.
1. On **Configuration repositories**, select the repository of the **Global** type, and then select **Open**. If you're prompted for authorization to connect to Regulatory Configuration Service, follow the authorization instructions.
1. On **Configuration repository**, in the configuration tree in the left pane, select the **BACS (UK)** format configuration.
1. On the **Versions** FastTab, select version **1.1** of the selected ER format configuration.
1. Select **Import** to download the selected version from the Global repository to the current Finance instance.

:::image type="content" source="./media/er-quick-start2-import-solution1.png" alt-text="Screenshot of the Configuration repository page.":::

> [!TIP]
> If you have trouble accessing the [Global repository](er-download-configurations-global-repo.md), you can [download configurations](download-electronic-reporting-configuration-lcs.md) from Microsoft Dynamics Lifecycle Services (LCS) instead.

### <a id="ReviewImportedERSolution"></a>Review the imported ER configurations

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
1. On **Localization configurations**, in the **Configurations** section, select the **Reporting configurations** tile.
1. On **Configurations**, in the configuration tree in the left pane, expand **Payment model**.
1. In addition to the selected **BACS (UK)** ER format, the import process adds other required ER configurations. Make sure that the following ER configurations are available in the configuration tree:

    - **Payment model** – This configuration contains the data model ER component that represents the data structure of the payment business domain.
    - **Payment model mapping 1611** – This configuration contains the model mapping ER component that describes how the data model is filled in with application data at runtime.
    - **BACS (UK)** – This configuration contains the format and format mapping ER components. The format component specifies the report layout. The format mapping component contains the model data source and specifies how the report layout is filled in by using this data source at runtime.

:::image type="content" source="./media/er-quick-start2-imported-solution1.png" alt-text="Screenshot of the Configurations page with specified ER configurations available in the tree.":::

## <a id="PrepareVendorPayment"></a>Prepare a vendor payment for processing

### <a id="AddBankAccount"></a>Add bank information for a vendor account

Add bank information for a vendor account that you refer to later in a registered payment.

1. Go to **Accounts payable** > **Vendors** > **All vendors**.
1. On **All vendors**, select the **GB_SI_000001** vendor account. On the Action Pane, on the **Vendor** tab, in the **Set up** group, select **Bank accounts**.
1. On **Vendor bank accounts**, select **New**, and then enter the following information:

    1. In the **Bank account** field, enter **GBP OPER**.
    1. In the **Bank groups** field, select **BankGBP**.
    1. In the **Bank account number** field, enter **202015**.
    1. In the **SWIFT code** field, enter <a id="DefineSWIFTCode"></a>**CHASDEFXXXX**.
    1. In the **IBAN** field, enter **GB33BUKB20201555555555**.
    1. In the **Routing number** field, keep the default value, <a id="DefineRoutingNumber"></a>**123456**.

    :::image type="content" source="./media/er-quick-start2-bank-account.png" alt-text="Screenshot of the Vendor bank accounts page.":::

1. Select **Save**.
1. Close the page.
1. On **All vendors**, open the **GB_SI_000001** vendor account.
1. On the vendor details page, select **Edit** to make the page editable, if required.
1. On the **Payment** FastTab, in the **Bank account** field, select **GBP OPER**.

    :::image type="content" source="./media/er-quick-start2-bank-account-reference.png" alt-text="Screenshot of the Vendor details page.":::

1. Select **Save**.
1. Close the page.

### <a id="EnterVendorPayment"></a>Enter a vendor payment

Enter a new vendor payment by using a [payment proposal](../../../finance/accounts-payable/create-vendor-payments-payment-proposal.md).

1. Go to **Accounts payable** > **Payments** > **Vendor payment journal**.
1. On the **Vendor payment journal** page, select **New**.
1. In the **Name** field, select **VendPay**.
1. Select **Lines**.
1. Select **Payment proposal** > **Create payment proposal**.
1. In the **Vendor payment proposal** dialog box, set conditions to filter for records for the **GB_SI_000001** vendor account only, and then select **OK**.
1. Select the line for the **00000007_Inv** invoice, and then select **Create payment**.

    :::image type="content" source="./media/er-quick-start2-payment-proposal.png" alt-text="Screenshot of the Vendor payment proposal dialog box.":::

1. Verify that the payment that you entered is configured to use the **Electronic** method of payment.

    :::image type="content" source="./media/er-quick-start2-payment-line.png" alt-text="Screenshot of the Vendor payments page.":::

## <a id="ProcessVendorPayment1"></a>Process a vendor payment by using the standard ER format

### <a id="ConfigureMethodOfPayment1"></a>Set up the electronic payment method

You must configure the electronic method of payment so that it uses the imported ER format configuration.

1. Go to **Accounts payable** > **Payment setup** > **Methods of payment**.
1. On **Methods of payment - vendors**, select the **Electronic** method of payment in the left pane.
1. Select **Edit**.
1. On the **File formats** FastTab, set the **General electronic Export format** option to **Yes**.
1. In the **Export format configuration** field, select the **BACS (UK)** format configuration.

    :::image type="content" source="./media/er-quick-start2-method-of-payment1.png" alt-text="Screenshot of the Methods of payment - vendors page to set up electronic payment method to process vendor payments using a standard format.":::

1. Select **Save**.

### <a id="ProcessPayment1"></a>Process a vendor payment

1. Go to **Accounts payable** > **Payments** > **Vendor payment journal**.
1. On **Vendor payment journal**, select the payment journal that you added earlier, and then select **Lines**.
1. On **Vendor payments**, select **Generate payments**.
1. In **Generate payments**, enter the following information:

    - In **Method of payment**, select **Electronic**.
    - In **Bank account**, select **GBSI OPER**.

1. Select **OK**.
1. In **Electronic report parameters**, set the **Print control report** option to **Yes**, and then select **OK**.

    :::image type="content" source="./media/er-quick-start2-payment-dialog1.png" alt-text="Screenshot of the Electronic report parameters dialog page.":::

    > [!NOTE]
    > In addition to the payment file, you can now generate the control report.

1. Download the ZIP file, and then extract the following files from it:

    - The control report in Excel format
    - The payment file in TXT format

        Notice that, in accordance with the [structure](#PositionRoutingNumber) of the provided ER format, the payment line in the generated file starts with the routing number that you [defined](#DefineRoutingNumber) for the configured bank account.

        :::image type="content" source="./media/er-quick-start2-payment-file1.png" alt-text="Screenshot of the payment file in TXT format.":::

## <a id="CustomizeProvidedFormat"></a>Customize the standard ER format

For the example in this section, you want to use the ER configurations that Microsoft provides to generate vendor payment files in BACS format, but you must add a customization to support the requirements of a specific bank. You also want to be able to upgrade your custom format when new versions of ER configurations become available. However, you want to do the upgrade at the lowest cost.

In this case, as the representative of Litware, Inc., you must create (derive) a new ER format configuration by using the **BACS (UK)** Microsoft-provided configuration as a base.

### <a id="DeriveProvidedFormat"></a>Create a custom format

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. On **Configurations**, in the configuration tree in the left pane, expand **Payment model**, and then select **BACS (UK)**. Litware, Inc. uses version 1.1 of this ER format configuration as the base for the custom version.
1. Select **Create configuration** to open the drop-down dialog box. Use this dialog box to create a new configuration for a custom payment format.
1. In the **New** field group, select the **Derive from Name: BACS (UK), Microsoft** option.
1. In the **Name** field, enter **BACS (UK custom)**.

    :::image type="content" source="./media/er-quick-start2-add-derived-format.png" alt-text="Screenshot of the Create configuration drop-down dialog box.":::

1. Select **Create configuration**.

Version 1.1.1 of the **BACS (UK custom)** ER format configuration is created. This version has a status of **Draft** and can be edited. The current content of your custom ER format matches the content of the format that Microsoft provides.

:::image type="content" source="./media/er-quick-start2-derived-format-configuration1.png" alt-text="Screenshot of the Configurations page with Version 1.1.1 of the BACS (UK custom) ER format configuration.":::

### <a id="ConfigureDerivedFormat"></a>Edit a custom format

You must configure your custom format so that it meets bank-specific requirements. For example, a bank might require that generated payment files include the Society for Worldwide Interbank Financial Telecommunication (SWIFT) code of a bank that is assigned the agent role in the processed vendor payment. SWIFT codes are international bank codes that identify specific banks worldwide. They're also known as Bank Identifier Codes (BICs). The SWIFT code must be 11 characters long, and it must be entered at the beginning of every payment line in a generated payment file.

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. On **Configurations**, in the configuration tree in the left pane, expand **Payment model**, and then select **BACS (UK custom)**.
1. On the **Versions** FastTab, select version **1.1.1** of the selected configuration.
1. Select **Designer**.
1. On **Format designer**, select **Show details** to view more information about the format elements.
1. Expand and review the following elements:

    - The **BACSReportsFolder** element of the **Folder** type. This element generates output in ZIP format.
    - The **file** element of the **File** type. This element generates a payment file in TXT format.
    - The **transactions** element of the **Sequence** type. This element generates a single payment line in a payment file.
    - The **transaction** element of the **Sequence** type. This element generates individual fields of a single payment line.

1. Select the **transaction** element.

    :::image type="content" source="./media/er-quick-start2-derived-format0.png" alt-text="Screenshot of the Transaction element in the ER Operations designer.":::

    > [!NOTE]
    > The provided report is configured so that <a id="PositionRoutingNumber"></a>every payment line starts with the bank routing number. The **vendBankRouteNum** format element is used for this purpose.

1. Select **Add**, and then select the **Text\\String** type of the format element that you're adding:

    1. In the **Name** field, enter **vendBankSWIFT**.
    1. In the **Minimum length** field, enter **11**.
    1. In the **Maximum length** field, enter **11**.
    1. Select **OK**.

    > [!NOTE]
    > Use the **vendBankSWIFT** element to enter the SWIFT code of a vendor bank in generated files.

1. In the format structure tree, select **vendBankSWIFT**.
1. Select **Move up** to move the selected format element up one level. Repeat this step until the **vendBankSWIFT** element is the <a id="PositionSWIFTCode"></a>first element under the parent **transaction** element.

    :::image type="content" source="./media/er-quick-start2-derived-format1.png" alt-text="Screenshot of VendBankSWIFT as the first element under transaction in the ER Operations designer.":::

1. While the **vendBankSWIFT** is still selected in the format structure tree, select the **Mapping** tab, and then expand the **model** data source.
1. Expand **model.Payment** > **model.Payment.CreditorAgent**, and select the **model.Payment.CreditorAgent.BICFI** data source field. This data source field exposes the SWIFT code of a vendor bank that is assigned the agent role in the processed vendor payment.
1. Select **Bind**. The **vendBankSWIFT** format element is now bound with the **model.Payment.CreditorAgent.BICFI** data source field, so that SWIFT codes are entered in generated payment files.

    :::image type="content" source="./media/er-quick-start2-derived-format2.png" alt-text="Screenshot of the vendBankSWIFT format element bound with the model.Payment.CreditorAgent.BICFI data source field in the ER Operations designer.":::

1. Select **Save**.
1. Close the designer page.

### <a id="MarkFormatRunnable"></a>Mark a custom format as runnable

After you create the first version of your custom format and set its status to **Draft**, you can run it for testing purposes. To run the report, you must process a vendor payment by using the payment method that refers to your custom ER format. By default, when you call an ER format from the application, only versions that have a status of **Completed** or **Shared** are considered. This behavior helps prevent ER formats that have unfinished designs from being used. However, for your test runs, you can force the application to use the version of your ER format that has a status of **Draft**. By using this approach, you can adjust the current format version if any modifications are required. For more information, see [Applicability](electronic-reporting-destinations.md#applicability).

To use the draft version of an ER format, you must explicitly mark the ER format.

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. On **Configurations**, on the Action Pane, on the **Configurations** tab, in the **Advanced settings** group, select **User parameters**.
1. In **User parameters**, set the **Run settings** option to **Yes**, and then select **OK**.
1. Select **Edit** to make the current page editable, as required.
1. In the configuration tree in the left pane, select **BACS (UK custom)**.
1. Set the **Run Draft** option to **Yes**.

    :::image type="content" source="./media/er-quick-start2-derived-format-configuration2.png" alt-text="Screenshot of the Run Draft option on the Configurations page.":::

## <a id="ProcessVendorPayment2"></a>Process a vendor payment by using the custom ER format

### <a id="ConfigureMethodOfPayment2"></a>Set up the electronic payment method

You must configure the electronic method of payment so that your custom ER format is used to process vendor payments.

1. Go to **Accounts payable** > **Payment setup** > **Methods of payment**.
1. On **Methods of payment - vendors**, select the **Electronic** method of payment in the left pane.
1. Select **Edit**.
1. On the **File format** FastTab, set the **General electronic export format** option to **Yes**.
1. In the **Export format configuration** field, select the **BACS (UK custom)** format configuration.

    :::image type="content" source="./media/er-quick-start2-method-of-payment2.png" alt-text="Screenshot of the Methods of payment - vendors page to set up electronic payment method to process vendor payments using a custom format.":::

1. Select **Save**.

### <a id="ProcessPayment2"></a>Process a vendor payment

1. Go to **Accounts payable** > **Payments** > **Vendor payment journal**.
1. On **Vendor payment journal**, select the payment journal that you created earlier.
1. Select **Lines**.
1. On **Vendor payments**, above the grid, select **Payment status** > **None**.
1. Select **Generate payment**.
1. In **Generate payments**, enter the following information:

    - In **Method of payment**, select **Electronic**.
    - In **Bank account**, select **GBSI OPER**.

1. Select **OK**.
1. In **Electronic report parameters**, set the **Print control report** option to **Yes**, and then select **OK**.

    > [!NOTE]
    > In addition to the payment file, you can generate only the control report.

1. Download the ZIP file, and then extract the following files from it:

    - The control report in Excel format
    - The payment file in TXT format

        Notice that, in accordance with the structure of your custom ER format, the payment line in the generated file now [starts](#PositionSWIFTCode) with the SWIFT code that you [entered](#DefineSWIFTCode) for the bank account of the vendor whose payment you processed.

        :::image type="content" source="./media/er-quick-start2-payment-file2.png" alt-text="Screenshot of the payment file in TXT format used to process the vendor payment.":::

## <a id="ImportERSolution2"></a>Import new versions of the standard ER format configurations

In the following example, you receive a notification about Knowledge Base article [KB3763330](https://fix.lcs.dynamics.com/Issue/Details?kb=3182046). This notification informs you about the new version of the **BACS (UK)** ER format that Microsoft published. In addition to the control report, this new version lets users generate the payment advice report and the attending note report while a vendor payment is being processed. You want to start using that functionality.

### <a id="ImportERFormat2"></a>Import new versions of the standard ER configurations

To add new versions of the ER configurations to the current Finance instance, import them from the ER [repository](general-electronic-reporting.md#Repository) that you configured.

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
1. On **Localization configurations**, in the **Configuration providers** section, select the **Microsoft** tile, and then select **Repositories** to view the list of repositories for the Microsoft provider.
1. On **Configuration repositories**, select the repository of the **Global** type, and then select **Open**. If you're prompted for authorization to connect to Regulatory Configuration Service, follow the authorization instructions.
1. On **Configuration repository**, in the configuration tree in the left pane, select the **BACS (UK)** format configuration.
1. On the **Versions** FastTab, select version **3.3** of the selected ER format configuration.
1. Select **Import** to download the selected version from the Global repository to the current Finance instance.

:::image type="content" source="./media/er-quick-start2-import-solution2.png" alt-text="Screenshot of the Configuration repository page, Versions FastTab, Import button.":::

> [!TIP]
> If you have trouble accessing the [Global repository](er-download-configurations-global-repo.md), you can [download configurations](download-electronic-reporting-configuration-lcs.md) from LCS instead.

### <a id="ReviewImportedERFormat"></a>Review the imported ER format configurations

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
1. On **Localization configurations**, in the **Configurations** section, select the **Reporting configurations** tile.
1. On **Configurations**, in the configuration tree in the left pane, expand **Payment model**, and then select **BACS (UK)**.
1. On the **Versions** FastTab, select version **3.3**.
1. Select **Designer**.
1. On **Format designer**, expand the **BACSReportsFolder** format element.
1. Notice that version 3.3 contains the **PaymentAdviceReport** format element that you use to generate a payment advice report when a vendor payment is processed.

    :::image type="content" source="./media/er-quick-start2-imported-solution2.png" alt-text="Screenshot of the PaymentAdviceReport format element in the ER Operations designer.":::

1. Close the designer page.

## <a id="AdoptNewBaseVersion"></a>Adopt the changes in the new version of an imported format in a custom format

### <a id="CompleteDerivedFormat"></a>Complete the current draft version of a custom format

If you want to keep the current state of your custom format, complete the draft version 1.1.1 by changing its status from **Draft** to **Completed**.

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
1. On **Localization configurations**, in the **Configurations** section, select the **Reporting configurations** tile.
1. On **Configurations**, in the configuration tree in the left pane, expand **Payment model**, expand **BACS (UK)**, and then select **BACS (UK custom)**.
1. On the **Versions** FastTab, select **Change status** > **Complete**, and then select **OK**.

The status of version 1.1.1 changes from **Draft** to **Completed**, and the version becomes read-only. A new editable version, 1.1.2, is added and has a status of **Draft**. Use this version to make further changes in your custom ER format.

### <a id="RebaseDerivedFormat"></a>Rebase a custom format to a new base version

To use the new functionality of version 3.3 of the **BACS (UK)** format in your customization, change the base configuration version for the custom configuration, **BACS (UK custom)**. This process is known as [rebasing](general-electronic-reporting.md#upgrading-a-format-selecting-a-new-version-of-base-format-rebase). Instead of version 1.1 of **BACS (UK)**, use version 3.3.

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. On **Configurations**, in the configuration tree in the left pane, expand **Payment model**, and then select **BACS (UK custom)**.
1. On the **Versions** FastTab, select version **1.1.2**, and then select **Rebase**.
1. In **Rebase**, in the **Target version** field, select version **3.3** of the base configuration to apply it as the new base and use it to update the configuration.

    :::image type="content" source="./media/er-quick-start2-rebase1.png" alt-text="Screenshot of the Rebase dialog box.":::

1. Select **OK**.
1. The number of the draft version changes from **1.1.2** to **3.3.2** to reflect the change in the base version.

    When the custom version and a new base version merge, some conflicts might be discovered because of format changes that can't be merged automatically.

    :::image type="content" source="./media/er-quick-start2-rebase2.png" alt-text="Screenshot of the Rebased configuration with conflicts on the Configurations page.":::

    If conflicts are discovered, you must resolve them manually in the format designer.

1. On the **Versions** FastTab, select version **3.3.2**.
1. Select **Designer**.
1. On **Format designer**, on the **Details** FastTab, select a rebase conflict record, and then select **Apply base value**.

    :::image type="content" source="./media/er-quick-start2-rebase3.png" alt-text="Screenshot of the Rebase conflict record in the ER Operations designer.":::

1. Select **Save**.

    The rebase conflict record no longer appears on the **Details** FastTab.

    :::image type="content" source="./media/er-quick-start2-rebase4.png" alt-text="Screenshot of the Conflict resolved in the ER Operations designer.":::

    > [!NOTE]
    > You resolved the conflict by confirming that version 3 of the base model must be used in this ER format.

1. Expand **BACSReportsFolder** > **file** > **transactions** > **transaction**.
1. On the **Mapping** tab, version 3.3.2 of your custom ER format contains both your customization (the **vendBankSWIFT** format element and its binding) and the new functionality of version 3.3 of the base ER format that Microsoft provides (the **PaymentAdviceReport** format element together with its nested elements and configured bindings). In just a few mouse clicks, you adopted the modifications of a new base version by merging them with your customization.

    :::image type="content" source="./media/er-quick-start2-rebase5.png" alt-text="Screenshot of the Merged format in the ER Operations designer.":::

1. Close the designer page.

> [!NOTE]
> The rebase action is reversible. To cancel this rebase, select version **1.1.1** of the **BACS (UK custom)** format on the **Versions** FastTab, and then select **Get this version**. Version 3.3.2 is renumbered 1.1.2, and the content of draft version 1.1.2 matches the content of version 1.1.1.

### <a id="ProcessPayment3"></a>Process a vendor payment by using a rebased ER format

1. Go to **Accounts payable** > **Payments** > **Vendor payment journal**.
1. On **Vendor payment journal**, select the payment journal that you created earlier.
1. Select **Lines**.
1. On **Vendor payments**, above the grid, select **Payment status** > **None**.
1. Select **Generate payment**.
1. In **Generate payments**, enter the following information:

    - In **Method of payment**, select **Electronic**.
    - In **Bank account**, select **GBSI OPER**.

1. Select **OK**.
1. In **Electronic report parameters**, enter the following information:

    - Set the **Print control report** option to **Yes**.
    - Set the **Print payment advice** option to **Yes**.

    :::image type="content" source="./media/er-quick-start2-payment-dialog2.png" alt-text="Screenshot of the Electronic report parameters dialog box.":::

    > [!NOTE]
    > In addition to the payment file, you can now generate both the control report and the payment advice report.

1. Select **OK**.
1. Download the ZIP file, and then extract the following files from it:

    - The control report in Excel format
    - The payment advice report in Excel format

        :::image type="content" source="./media/er-quick-start2-payment-advice-report.png" alt-text="Screenshot of the payment advice report in Excel format.":::

    - The payment file in TXT format

        Notice that the payment line in the generated file starts with the SWIFT code that you entered for the bank account of a vendor whose payment you processed.

        :::image type="content" source="./media/er-quick-start2-payment-file3.png" alt-text="Screenshot of the payment file in TXT format used to process the vendor payment using a rebased ER format.":::

## <a id="References"></a>Additional resources

- [Electronic Reporting overview](general-electronic-reporting.md)
- [Download ER configurations from Lifecycle Services](download-electronic-reporting-configuration-lcs.md)
- [Download ER configurations from Global repository of Configuration service](er-download-configurations-global-repo.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
