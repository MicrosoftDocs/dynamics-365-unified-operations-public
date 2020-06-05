---
# required metadata

title: Adjust an ER format to generate a custom electronic document
description: This topic explains how to adjust a Microsoft provided Electronic reporting (ER) format to generate a custom electronic document.
author: NickSelin
manager: AnnBe
ms.date: 06/04/2020
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

# Adjust an ER format to generate a custom electronic document

[!include[banner](../includes/banner.md)]

The procedures in this topic explain how a user in the System Administrator or Electronic Reporting Functional Consultant role can:

- Configure the [ER framework](general-electronic-reporting.md) parameters.
- Import ER configurations that are provided by Microsoft to generate a payment file while a [vendor payment](../../finance/cash-bank-management/tasks/vendor-payment-overview.md) is processed.
- Create a custom version of an ER format configuration based on the standard ER format configuration provided by Microsoft.
- Modify a custom ER format configuration to generate payment files according to requirements specified by a particular bank.
- Adopt changes made to the standard ER format configuration in a custom ER format configuration.

These procedures can be performed in **GBSI** company with no coding required.

-   [Configure ER framework](#ConfigureFramework)
    -   [Configure ER parameters](#ConfigureParameters)
    -   [Activate an ER configuration provider](#ActivateProvider)
        -   [Review ER configuration providers list](#ReviewProvidersList)
        -   [Add a new ER configuration provider](#ActivateProvider)
        -   [Activate an ER configuration provider](#ActivateAddedProvider)
-   [Import the provided ER configurations](#ImportERSolution1)
    -   [Import the provided ER format configuration](#ImportERFormat1)
    -   [Review the imported ER configurations](#ReviewImportedERSolution)
-   [Prepare a vendor payment for processing](#PrepareVendorPayment)
    -   [Add bank information for a vendor account](#AddBankAccount)
    -   [Enter a vendor payment](#EnterVendorPayment)
-   [Process a vendor payment by using the standard ER format](#ProcessVendorPayment1)
    -   [Set up the electronic payment method](#ConfigureMethodOfPayment1)
    -   [Process a vendor payment](#ProcessPayment1)
-   [Customize the standard ER format](#CustomizeProvidedFormat)
    -   [Create your custom format](#DeriveProvidedFormat)
    -   [Edit your custom format](#ConfigureDerivedFormat)
    -   [Mark a custom format as runnable](#ConfigureDerivedFormat)
-   [Process a vendor payment by using custom ER format](#ProcessVendorPayment2)
    -   [Set up the electronic payment method](#ConfigureMethodOfPayment2)
    -   [Process a vendor payment](#ProcessPayment2)
-   [Import the new versions of the standard ER format configurations](#ImportERSolution2)
    -   [Import the new version of the standard ER format configuration](#ImportERFormat2)
    -   [Review the imported ER format configuration](#ReviewImportedERFormat)
-   [Adopt changes of the new version of an imported format into a custom format](#AdoptNewBaseVersion)
    -   [Complete the current draft version of a custom format](#CompleteDerivedFormat)
    -   [Rebase your custom format to a new base version](#RebaseDerivedFormat)
    -   [Process a vendor payment by using a rebased ER format](#ProcessPayment3)
-   [Additional resources](#References)

## <a name="ConfigureFramework">Configure ER framework</a>

As the Electronic Reporting Functional Consultant, you must configure the minimal set of ER parameters to start using the ER framework to design your custom version of the standard ER format.

### <a name="ConfigureParameters">Configure ER parameters</a>

1.  Open the **Electronic reporting** workspace page and select **Electronic reporting parameters**.
2.  On the **Electronic reporting parameters** page, on the **General** tab, set **Enable design mode** to **Yes**.
3.  On the **Attachments** tab, set the following parameters:
   - For the **USMG** company, set **Configurations** to **File**.
   - Set **Job archive**, **Temporary**, **Baseline**, and **Others** to **File**.

For more information about ER parameters, see [Configure the ER framework](electronic-reporting-er-configure-parameters.md).

### <a name="ActivateProvider">Activate an ER configuration provider</a>

Every ER configuration that is added, is marked as owned by an ER configuration provider. The ER configuration provider that is activated in the ER workspace is used for that. This means that you must activate an ER configuration provider in the ER workspace before you start adding or editing any ER configuration.

> [!NOTE]
> Only the owner of an ER configuration can edit it. This means that the appropriate ER configuration provider must be activated in the ER workspace so that an ER configuration can be edited.

#### <a name="ReviewProvidersList">Review  the list of ER configuration providers</a>

1.  In the **Navigation pane**, in the upper left corner, select **Organization administration**.
2.  Go to **Workspaces** \> **Electronic reporting**, and then select **Related links** \> **Configuration providers**.

A provider record has a unique name and URL. Review the content of this page and skip the remaining steps of the [Add a new ER configuration provider](#ActivateProvider) section  if a record for Litware, Inc. ([https://www.litware.com](https://www.litware.com/)) already exists.

#### <a name="ActivateProvider">Add a new ER configuration provider</a>

1.  On the **Configuration providers** page, select **New**.
2.  In the **Name** field, type **Litware, Inc.**.
3.  In the **Internet address** field, type <https://www.litware.com>.
4.  Select **Save**.

#### <a name="ActivateAddedProvider">Activate an ER configuration provider</a>

1.  Go to **Workspaces** \> **Electronic reporting**.
2.  Select the provider, **Litware, Inc.**,and then select **Set active**.

To learn more about ER configuration provider, see [Create configuration providers and mark them as active](tasks/er-configuration-provider-mark-it-active-2016-11.md).

## <a name="ImportERSolution1">Import the provided ER configurations</a>

### <a name="ImportERFormat1">Import the provided ER format configuration</a>

To add the standard ER configurations to you current Finance instance, you must import them from the ER
[repository](general-electronic-reporting.md#Repository)that was configured for the instance.

1.  From the **Navigation pane**, select **Organization administration**.
2.  Go to **Workspaces** \> **Electronic reporting**, and innthe **Providers** grid, select the **Microsoft** tile.
3.  Select **Repositories** to open the list of repositories for the Microsoft provider.
4.  Select the repository of **Global** type.
5.  Select **Open**. If prompted, follow the authorization instructions.
6.  In the configurations tree in the left pane, select the **BACS (UK)** format configuration.
7.  On the **Versions** FastTab, select the version 1.1.
9.  Select **Import** to download the selected version from Global repository to the current Finance instance.

![ER repository page](./media/er-quick-start2-import-solution1.png)

If you experience difficulties with accessing the [Global repository](er-download-configurations-global-repo.md), use the alternative way to [download configurations](download-electronic-reporting-configuration-lcs.md) from Microsoft Lifecycle Services (LCS).

### <a name="ReviewImportedERSolution">Review the imported ER configurations</a>

1.  From the **Navigation pane**, select **Organization administration**.
2.  Go to **Workspaces** \> **Electronic reporting**, and then select **Reporting configurations**.
3.  In the configurations tree, expand **Payment model**.

Note that in addition to the selected **BACS (UK)** ER format, other required ER configurations were imported. Make sure that the following ER configurations are available in the configurations tree:

-   Payment model: Contains the [data model](general-electronic-reporting.md#data-model-and-model-mapping-components) ER component that represents the data structure of the payment business domain.
-   Payment model mapping 1611: Contains the [model mapping](general-electronic-reporting.md#data-model-and-model-mapping-components) ER component that describes how the data model is filled in by application data at runtime.
-   BACS (UK): Contains the [format](general-electronic-reporting.md#FormatComponentOutbound) and format mapping ER components. The format component specifies the report layout. The format mapping component contains the model data source and specifies how the report layout is filled in at runtime by using this data source.

![ER configurations page](./media/er-quick-start2-imported-solution1.png)

## <a name="PrepareVendorPayment">Prepare a vendor payment for processing</a>

### <a name="AddBankAccount">Add bank information for a vendor account</a>
You must add bank information for a vendor account that will be referred to later in a registered payment.

1.  Go to **Accounts payable** \> **Vendors** \> **All vendors**.
2.  Select the **GB_SI_000001** vendor account, and on the Action pane, on the **Vendor** tab, in the **Set up** group, select **Bank accounts**.
3.  Select **New**.
    1.  In the **Bank account** field, type **GBP OPER**.
    2.  In the **Bank groups** field, select **BankGBP**.
    3.  In the **Bank account number** field, type 202015.
    4.  In the **SWIFT code** field, type <a name="DefineSWIFTCode">CHASDEFXXXX</a>.
    5.  In the **IBAN** field, type GB33BUKB20201555555555.
    6.  In the **Routing number** field, keep <a name="DefineRoutingNumber">123456</a>.
4.  Select **Save**.
    <br>![Vendor bank accounts page](./media/er-quick-start2-bank-account.png)
5.  Close the page.
6.  On the **All vendors** page, open the **GB_SI_000001** vendor account.
7.  Expand the **Payment** FastTab, and if needed, select **Edit** to make this page editable.
8.  In the **Bank account** field, select **GBP OPER**, and then select**Save**.
    <br>![Vendor page](./media/er-quick-start2-bank-account-reference.png)
9.  Close the page.

### <a name="EnterVendorPayment">Enter a vendor payment</a>
You must enter a new vendor payment by using a [payment proposal](https://docs.microsoft.com/dynamics365/finance/accounts-payable/create-vendor-payments-payment-proposal).

1.  From the Navigation pane, go to **Modules** \> **Accounts payable** \> **Payments** \> **Vendor payment journal**.
2.  Select **New**, and in the **Name** field, select **VendPay**.
3.  Select **Lines**.
4.  Select **Payment proposal**.
5.  Select **Create payment proposal**.
6.  Configure conditions to filter the only records for the **GB_SI_000001** vendor account, and then select **OK**.
7.  Select the line for the **00000007_Inv** invoice.
    <br>![Vendor payment proposal page](./media/er-quick-start2-payment-proposal.png)
8. Select **Create payment**.
    <br>![Vendor payments page](./media/er-quick-start2-payment-line.png)

Verify that the entered payment is configured to use the **Electronic** method of payment.

## <a name="ProcessVendorPayment1">Process a vendor payment by using provided ER format</a>

### <a name="ConfigureMethodOfPayment1">Set up the electronic payment method</a>
You must configure the electronic method of payment to use the imported ER format configuration.

1.  Go to **Accounts payable** \> **Payment setup** \> **Methods of payment**.
2.  Expand the **File format** FastTab and select the **Electronic** method of payment.
3.  Select **Edit**.
4.  Set the **General electronic export format** field to **Yes**.
5.  In the **Export format configuration** field, select the **BACS (UK)** format configuration.
    <br>![Methods of payment - vendors page](./media/er-quick-start2-method-of-payment1.png)
6.  Select **Save**.

### <a name="ProcessPayment1">Process a vendor payment</a>

1.  From the Navigation pane, go to **Modules** \> **Accounts payable** \> **Payments** \> **Vendor payment journal**.
2.  Select payment journal you added earlier, and then select **Lines**.
3.  On the **Vendor payments** page, select **Generate payment**.
4.  On the **Generate payments** dialog, enter the following information:
    -   In the **Method of payment** field, select **Electronic**.
    -   In the **Bank account** field, select **GBSI OPER**.
    -   Select **OK**.
5.  On the **Electronic report parameters** dialog page, enter the following
    information:
    -   Set **Print control report** to **Yes**.
    -   Select **OK**.
        <br>![Electronic report parameters dialog page](./media/er-quick-start2-payment-dialog1.png)
        > [!Note]
        > In addition to the payment file, you can now generate the control report.
6.  Download the zipped file and then extract:
    - The control report in Excel
    - The payment file in TXT
    <br>![Payment file preview](./media/er-quick-start2-payment-file1.png)
    > [!Note]
    > Note that, in accordance to the [structure](#PositionRoutingNumber) of the provided ER format, the payment line starts from the routing number that has been [defined](#DefineRoutingNumber) for the configured bank account.

## <a name="CustomizeProvidedFormat">Customize the provided ER format</a>

Assume that you want to use the ER configurations provided by Microsoft to generate vendor payment files in BACS format, but you need to add a customization that is required to support the specific requirements of a particular bank. You also want to keep the ability to upgrade your custom format when new versions of of ER configurations become available, all while performing this upgrade with the lowest cost.

As the representative of the Litware, Inc., to do this you need to create (derive) a new ER format configuration using the Microsoft configuration **BACS (UK)** as a bas.

### <a name="DeriveProvidedFormat">Create your custom format</a>

1.  From the Navigation pane, go to **Modules** \> **Organization administration** \> **Electronic reporting** \> **Configurations**.
2.  In the configurations tree, expand the **Payment model**.
3.  Select **BACS (UK)**. Version 1.1 of the **BACS (UK)** ER format configuration will be used by Litware, Inc. as a base for the custom version.
4.  Select **Create configuration** to open the dialog. You can use this dialog to create a new configuration for a custom payment format.
5.  In the **New** field, select **Derive from Name: BACS (UK), Microsoft**.
6.  In the **Name** field, type **BACS (UK custom)**.
    <br>![Create configuration dialog page](./media/er-quick-start2-add-derived-format.png)
7.  Select **Create configuration**.

Note that version 1.1.1 of the **BACS (UK custom)** ER format configuration has been created. This version is in the
[status](general-electronic-reporting.md#component-versioning) of  **Draft** and can be edited. The current content of your custom ER format equals the content of the format that has been provided by Microsoft.

![ER configurations page](./media/er-quick-start2-derived-format-configuration1.png)

### <a name="ConfigureDerivedFormat">Edit your custom format</a>

You must configure your custom format so that it is compliant with specific bank requirements. For example, there may be a requirement to populate a generated payment file with the SWIFT code (an international bank code that identifies particular banks worldwide also known as a Bank Identifier Code (BIC)) of a bank that is assigned the agent role in the processed vendor payment. This code must be 11 characters long and placed at the beginning of every payment line in a generated file.

1.  On the **Configurations** page, select **BACS (UK custom)**,and for version 1.1.1 of the selected configuration, select **Designer**.
3.  Select **Show details** to see more information about format elements.
3. Expand the following elements for information:
    - The **BACSReportsFolder** element of the **Folder** type used to generate an output in ZIP format.
    - The **file** element of the **File** type used to generate a payment file in TXT format.
    - The **transactions** element of the **Sequence** type used to generate a single payment line of a payment file.
    - The **transaction** element of the **Sequence** type used to generate individual fields of a single payment line.
4.  Select the **transaction** element.
    <br>![ER Operations designer](./media/er-quick-start2-derived-format0.png)
    > [!Note]
    > The provided report is configured to <a name="PositionRoutingNumber">start</a> every payment line from the bank routing number by using the **vendBankRouteNum** format element.
5.  Select **Add**,and then select the **Text\\String** type of the format element you are adding.
    1.  In the **Name** field, type **vendBankSWIFT**.
    2.  In the **Minimum length** field, enter 11.
    3.  In the **Maximum length** field, enter 11.
    4.  Select **OK**.
6. In the format structure tree, select **vendBankSWIFT**.
7. Select **Move up** to shift the selected format element one level above. Repeat this step to position the selected **vendBankSWIFT** element as the <a name="PositionSWIFTCode">first element</a> under the parent **transaction** element.
    <br>![ER Operations designer](./media/er-quick-start2-derived-format1.png)
    > [!NOTE]
    > The **vendBankSWIFT** element is added to populate to a generated file the SWIFT code of a vendor bank.
8. Keep the **vendBankSWIFT** selected in the format tree.
9. Select the **Mapping** tab and expand **model** data source.
10. Expand **model.Payment** > **model.Payment.CreditorAgent**, and select the **model.Payment.CreditorAgent.BICFI** data source field.
    The **model.Payment.CreditorAgent.BICFI** data source field exposes a SWIFT code of a vendor bank that is assigned the agent role in the processed vendor payment.
11. Select **Bind**. You have bound the **vendBankSWIFT** format element with the **model.Payment.CreditorAgent.BICFI** data source field to populate a SWIFT code to a generated payment file.
12. Select **Save**.
    <br>![ER Operations designer](./media/er-quick-start2-derived-format2.png)
13. Close the designer page.

### <a name="MakrFormatRunnable">Mark a custom format as runnable</a>

Now that the first version of a custom format has been created and has a status of **Draft**, you can run it for testing purposes. To run this report, you must process a vendor payment using the payment method that refers to your custom ER format. By default, when you call an ER format from the application, only versions with a status of **Completed** or **Shared** are [considered](general-electronic-reporting.md#component-versioning) to prevent using ER formats that have unfinished designs. For your test runs, you can force the application to use the version of your ER format with a status of **Draft**. This allows you to adjust the current format version if any modifications are needed. For more details, see [Applicability](electronic-reporting-destinations.md#applicability) section.

To use the draft version of an ER format, you must explicitly mark the ER format.

1.  Go to **Organization administration** \> **Electronic reporting** \> **Configurations**.
2.  On the **Configurations** page, on the Action Pane, on the **Configurations** tab, in the **Advanced settings** group, select **User parameters**.
3.  Set the **Run setting** option to **Yes**, and if needed, select **Edit** to make the current page editable.
4.  In the configurations tree, select **BACS (UK custom)**.
5.  Set the **Run draft** option to **Yes**.
    <br>![ER Operations designer](./media/er-quick-start2-derived-format-configuration2.png)

## <a name="ProcessVendorPayment2">Process a vendor payment by using custom ER format</a>

### <a name="ConfigureMethodOfPayment2">Set up the electronic payment method</a>

You must configure the electronic method of payment to use your custom ER format for vendor payments processing.

1.  Go to **Accounts payable** \> **Payment setup** \> **Methods of payment**.
2.  Expand the **File format** FastTab and select the **Electronic** method of payment.
3.  Select **Edit**, and then set the **General electronic export format** field, to **Yes**.
4.  In the **Export format configuration** field, select **BACS (UK custom)** format configuration.
5.  Select **Save**.
    <br>![Methods of payment - vendors page](./media/er-quick-start2-method-of-payment2.png)

### <a name="ProcessPayment2">Process a vendor payment</a>

1.  From the Navigation pane, go to **Modules** \> **Accounts payable** \> **Payments** \> **Payment journal**.
2.	Select the payment journal that you created earlier.
3.  Select **Lines**, and then select **Payment status**.
4.  Select **None**.
5.  On the **Vendor payments** page, select **Generate payment**.
7.  On the **Generate payments** dialog page, enter the following information:
    -   In the **Method of payment** field, select **Electronic**.
    -   In the **Bank account** field, select **GBSI OPER**.
    -   Select **OK**.
8.  On the **Electronic report parameters** dialog page, enter the following
    information:
    -   Set **Print control report** to **Yes**.
    -   Select **OK**.
    > [!Note]
    > In addition to the payment file, you can generate the control report only.
9.  Download the zip file.
10. Extract the control report in Excel format from the zip file.
11. Extract the payment file in TXT format from the zip file.
    <br>![Payment file preview](./media/er-quick-start2-payment-file2.png)
    > [!Note]
    > In accordance with the structure of your custom ER format, the payment line in a generated file now [starts](#PositionSWIFTCode) from the SWIFT code that has been [entered](#DefineSWIFTCode) for the bank account of a vendor whose payment has been processed.

## <a name="ImportERSolution2">Import the new versions of the provided ER format configurations</a>

Assume that you have received a notification about the knowledge base article [KB3763330](https://fix.lcs.dynamics.com/Issue/Details?kb=3182046) informing about the new version of the **BACS (UK)** ER format that has been published by Microsoft. In addition to the control report, this new version offers the possibility to generate the payment advice and the attending note reports while a vendor payment is processed. You want to start using the functionality.

### <a name="ImportERFormat2">Import the new version of the ER format configuration</a>

To add new versions of the ER configurations to the current Finance instance, you must import them from the ER
[repository](general-electronic-reporting.md#Repository) you have configured.

1.  From the Navigation pane, select **Organization administration**.
2.  Go to **Workspaces** \> **Electronic reporting**.
3.  In the **Providers** grid, select the **Microsoft** tile.
4.  Select **Repositories** to open the list of repositories for the Microsoft provider.
5.  Select the repository of **Global** type.
6.  Select **Open**. If prompted, follow the authorization instructions.
7.  In the configurations tree in the left pane, select the **BACS (UK)** format configuration.
8.  On the **Versions** FastTab, select version 3.3 of the selected ER format configuration.
9.  On the **Versions** FastTab, click **Import** to download the selected version from the Global repository to the current Finance instance.

![ER repository page](./media/er-quick-start2-import-solution2.png)

If you experience difficulties with accessing the [Global repository](er-download-configurations-global-repo.md), use the alternative way of configuration [downloading](download-electronic-reporting-configuration-lcs.md) from Microsoft Lifecycle Services (LCS).

### <a name="ReviewImportedERFormat">Review the imported ER format configuration</a>

1.  From the Navigation pane, select **Organization administration**.
2.  Go to **Workspaces** \> **Electronic reporting**.
3.  Select **Reporting configurations**.
4.  Expand **Payment model** in the configurations tree, and then select **BACS (UK)**.
5.  On the **Versions** FastTab, select version 3.3.
6.  Select **Designer**.
7.  Expand the **BACSReportsFolder** format element.
    <br>![ER configurations page](./media/er-quick-start2-imported-solution2.png)
    > [!Note]
    > Version 3.3 contains the **PaymentAdviceReport** format element used to generate a payment advice report when a vendor payment is processed.     
8.  Close the **Designer** page.

## <a name="AdoptNewBaseVersion">Adopt changes of the new version of imported format in a custom format</a>

### <a name="CompleteDerivedFormat">Complete the current draft version of a custom format</a>

If you want to keep the current state of your custom format, complete the draft version 1.1.1 changing it's status from **Draft** to **Completed**.

1.  On the **Configurations** page, expand **Payment model**.
2.  Expand **BACS (UK)**, and then select **BACS (UK custom)**.
3.  On the **Versions** FastTab, select **Change status**.
4.  Select **Complete**, and then select **OK**.

The status of version 1.1.1 has been changed from **Draft** to **Completed** making it read-only. The new editable version 1.1.2 has been added wtih a status of **Draft**. You can use it to make further modifications in your custom ER format.

### <a name="RebaseDerivedFormat">Rebase your custom format to a new base version</a>

To start using a new functionality of the version 3.3 of the BACS (UK) format along with your customization, you need to change the base ([rebase](general-electronic-reporting.md#upgrading-a-format-selecting-a-new-version-of-base-format-rebase)) configuration version for the custom configuration **BACS (UK custom)**. Instead of version 1.1 of BACS (UK), use version 3.3.

1.  Go to **Organization administration** \> **Electronic reporting** \> **Configurations**.
2.  In the tree, expand **Payments model** and then select **BACS (UK custom)**.
3.  On the **Versions** FastTab, for the version 1.1.2 select **Rebase**.
4.  In the **Target version** field, select the version 3.3 of the base configuration to be applied as a new base for updating the configuration.
    <br>![ER configurations page](./media/er-quick-start2-rebase1.png)
5.  Select **OK**.
    <br>![ER configurations page](./media/er-quick-start2-rebase2.png)
    > [!Note]
    > Some conflicts might be discovered between merging the custom version and a new base version because of format changes that can't be merged automatically. If conflicts are discovered, they must be manually resolved in the format designer.
    > [!Note]
    > The number of the draft version has been changed from 1.1.2 to 3.3.2 reflecting the base version change.
6.  On the **Versions** FastTab, select version 3.3.2 and then select **Designer**.
7.  On the **Details** tab, for a rebase conflict record, select **Apply base value**.
    <br>![ER Operations designer](./media/er-quick-start2-rebase3.png)
8. Select **Save**.
    <br>![ER Operations designer](./media/er-quick-start2-rebase4.png)
    >
    > You resolved this conflict confirming that the version 3 of the base model must be used in this ER format.
9. Expand **BACSReportsFolder** > **file** > **transactions** > **transaction**.
10. Select the **Mapping** tab.
    <br>![ER Operations designer](./media/er-quick-start2-rebase5.png)
    > [!Note]
    > The version 3.3.2 of your custom ER format contains your customization (**vendBankSWIFT** format element and its binding) and new functionality of the version 3.3 of the base ER format which was provided by Microsoft(**PaymentAdviceReport** format element with nested elements and configured bindings). You adopted modifications of a new base version by merging them with your customization within a few clicks.
11. Close the designer. 
    The rebase action is reversible. If you want to cancel this rebase, select version 1.1.1 of the **BACS (UK custom)** format on the **Versions** FastTab and then select **Get this version**. After that, version 3.3.2 will be renumbered back to 1.1.2. The content of draft version 1.1.2 will be equal the content of version 1.1.1.

### <a name="ProcessPayment3">Process a vendor payment by using rebased ER format</a>

1.  From the Navigation pane, go to **Modules** \> **Accounts payable** \> **Payments** \> **Vendor payment journal**.
2.	Select the payment journal that has been created earlier.
3.  Select **Lines**, and then select **Payment status**.
4.  Select **None**.
5.  On the **Vendor payments** page, select **Generate payment**, and on the **Generate payments** dialog page, enter the following information:
    -   In the **Method of payment** field, select **Electronic**.
    -   In the **Bank account** field, select **GBSI OPER**.
    -   Select **OK**.
6.  On the **Electronic report parameters** dialog page, enter the following information:
    -   Set **Print control report** to **Yes**.
    -   Set **Print payment advice** to **Yes**.
        <br>![Electronic report parameters dialog page](./media/er-quick-start2-payment-dialog2.png)
        > [!Note]
        > In addition to the payment file you can now generate not only the control report but the payment advice report as well.
    -   Select **OK**.
7. Download the zip file.
8. Extract the control report in Excel format from the zip file.
9. Extract the payment advice report in Excel format from the zip file.
    <br>![Payment advice report preview](./media/er-quick-start2-payment-advice-report.png)
10. Extract the payment file in TXT format from the zip file.
    <br>![Payment file preview](./media/er-quick-start2-payment-file3.png)
    > [!Note]
    > The payment line in a generated file starts from the SWIFT code that has been entered for a bank account of a vendor whose payment has been processed.
    >
    > The zipped output contains a payment advice report in Excel format.

## <a name="References">Additional resources</a>

-   [Electronic Reporting overview](general-electronic-reporting.md)
-   [Download ER configurations from Lifecycle Services](download-electronic-reporting-configuration-lcs.md)
-   [Download ER configurations from Global repository of Configuration service](er-download-configurations-global-repo.md)

