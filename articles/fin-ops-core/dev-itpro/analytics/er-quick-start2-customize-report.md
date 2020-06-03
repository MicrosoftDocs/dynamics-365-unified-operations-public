---
# required metadata

title: Quick start guide - adjust a provided ER format to generate a custom electronic document
description: This topic explains how to adjust a provided Electronic reporting (ER) format to generate a custom electronic document.
author: NickSelin
manager: AnnBe
ms.date: 05/29/2020
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

# Customize the provided ER solution to generate a custom electronic document

[!include[banner](../includes/banner.md)]

The following steps explain how a user in the System Administrator or Electronic Reporting Functional Consultant role can do the following:

- Configure parameters of the [ER framework](general-electronic-reporting.md) in Finance instance
- Import to this instance an ER solution that is provided by Microsoft for generation of a payment file while [vendor payment](https://docs.microsoft.com/dynamics365/finance/cash-bank-management/tasks/vendor-payment-overview) is processed
- Create a custom version of ER format based on ER format of the provided ER solution
- Modify a custom ER format to generate payment files in accordance to specific requirements of a particular bank
- Adopt changes of a new versions of provided by Microsoft ER format in a custom ER format

These steps can be performed in **GBSI** company with no coding.

-   [Configure ER framework](#ConfigureFramework)
    -   [Configure ER parameters](#ConfigureParameters)
    -   [Activate an ER solution provider](#ActivateProvider)
        -   [Review ER solution providers list](#ReviewProvidersList)
        -   [Add a new ER solution provider](#ActivateProvider)
        -   [Activate an ER solution provider](#ActivateAddedProvider)
-   [Import the provided ER solution](#ImportERSolution1)
    -   [Import the ER format of the provided ER solution](#ImportERFormat1)
    -   [Review the imported ER solution](#ReviewImportedERSolution)
-   [Prepare a vendor payment for processing](#PrepareVendorPayment)
    -   [Add bank information for a vendor account](#AddBankAccount)
    -   [Enter a vendor payment](#EnterVendorPayment)
-   [Process a vendor payment by using provided ER format](#ProcessVendorPayment1)
    -   [Set up the electronic payment method](#ConfigureMethodOfPayment1)
    -   [Process a vendor payment](#ProcessPayment1)
-   [Customize the provided ER format](#CustomizeProvidedFormat)
    -   [Create your custom format](#DeriveProvidedFormat)
    -   [Edit your custom format](#ConfigureDerivedFormat)
    -   [Mark a custom format as runnable](#ConfigureDerivedFormat)
-   [Process a vendor payment by using custom ER format](#ProcessVendorPayment2)
    -   [Set up the electronic payment method](#ConfigureMethodOfPayment2)
    -   [Process a vendor payment](#ProcessPayment2)
-   [Import the new version of the provided ER solution](#ImportERSolution2)
    -   [Import the new version of the ER format of the provided ER solution](#ImportERFormat2)
    -   [Review the imported ER format](#ReviewImportedERFormat)
-   [Adopt changes of the new version of imported format in a custom format](#AdoptNewBaseVersion)
    -   [Complete the current draft version of a custom format](#CompleteDerivedFormat)
    -   [Rebase your custom format to a new base version](#RebaseDerivedFormat)
    -   [Process a vendor payment by using rebased ER format](#ProcessPayment3)
-   [Additional resources](#References)

## <a name="ConfigureFramework">Configure ER framework</a>

As the Electronic Reporting Functional Consultant, you must configure the minimal set of ER parameters to start using the ER framework for designing your custom version of the provided ER format.

### <a name="ConfigureParameters">Configure ER parameters</a>

1.  Open the **Electronic reporting** workspace page.
2.  Select **Electronic reporting parameters**.
3.  On the **General** tab of the **Electronic reporting parameters** page, set the **Enable design mode** parameter to **Yes.**
4.  On the **Attachments** tab of the **Electronic reporting parameters** page, set the following parameters:
    1.  Set the **Configurations** parameter to **File** for the **USMF** company.
    2.  Set **Job archive**, **Temporary**, **Baseline**, and **Others** parameters to **File**.

To learn more about ER parameters, review the [Configure the ER framework](electronic-reporting-er-configure-parameters.md) page.

### <a name="ActivateProvider">Activate an ER solution provider</a>

Every added ER configuration is marked as owned by an ER solution provider. The activated in the ER workspace ER solution provider is used for that. Therefore, you must activate an ER solution provider in the ER workspace before you start adding or editing any ER configuration.

> [!NOTE]
>
> The only owner of an ER configuration can edit it. Therefore, the appropriate ER solution provider must be activated in the ER workspace for editing an ER configuration.

#### <a name="ReviewProvidersList">Review ER solution providers list</a>

1.  Go to the **Navigation pane** in the upper left corner.
2.  Select **Organization administration** module.
3.  Go to **Workspaces \> Electronic reporting**.
4.  Go to **Related links \> Configuration providers**.

A provider record has a unique name and URL. Review the content of this page and skip the remaining steps of the [Add a new ER solution provider](#ActivateProvider) section  if a record for Litware, Inc. ([https://www.litware.com](https://www.litware.com/)) already exists.

#### <a name="ActivateProvider">Add a new ER solution provider</a>

1.  Select **New**.
2.  In the **Name** field, type **Litware, Inc.**.
3.  In the **Internet address** field, type <https://www.litware.com>.
4.  Select **Save**.

#### <a name="ActivateAddedProvider">Activate an ER solution provider</a>

1.  Go to **Workspaces \> Electronic reporting**.
2.  Select the Litware, Inc. provider.
3.  Select **Set active**.

To learn more about ER solution provider, review the [Create configuration providers and mark them as active](tasks/er-configuration-provider-mark-it-active-2016-11.md) page.

## <a name="ImportERSolution1">Import the provided ER solution</a>

### <a name="ImportERFormat1">Import the ER format of the provided ER solution</a>

To bring the provided ER solution to the current Finance instance, you must import it from the configured for this ER
[repository](general-electronic-reporting.md#Repository).

1.  Go to the **Navigation pane** and select **Organization administration**.
2.  Go to **Workspaces \> Electronic reporting**.
3.  In the **Providers** grid, select the **Microsoft** tile.
4.  Select **Repositories** to open the list of repositories for the Microsoft provider.
5.  Select the repository of **Global** type.
6.  Select **Open**. If prompted, follow the authorization instructions.
7.  In the configurations tree in the left pane, select the **BACS (UK)** format configuration.
8.  On the **Versions** FastTab, select the version 1.1 of the selected ER format configuration.
9.  On the **Versions** FastTab, click **Import** to download the selected version from Global repository to the current Finance instance.

![ER repository page](./media/er-quick-start2-import-solution1.png)

If you experience difficulties with accessing [Global repository](er-download-configurations-global-repo.md), use the alternative way
of configuration [downloading](download-electronic-reporting-configuration-lcs.md) from Microsoft Lifecycle Services (LCS).

### <a name="ReviewImportedERSolution">Review the imported ER solution</a>

1.  Go to the **Navigation pane** and select **Organization administration**.
2.  Go to **Workspaces \> Electronic reporting**.
3.  Select **Reporting configurations**.
4.  Expand **Payment model** in the configurations tree.

Note that, in addition to the selected **BACS (UK)** ER format, other ER configurations were imported as parts of the provided ER solution. Make sure that the following ER configurations are available in the configurations tree:

-   Payment model
    > Contains [data model](general-electronic-reporting.md#data-model-and-model-mapping-components) ER component that represents the data structure of the payment business domain
-   Payment model mapping 1611
    > Contains [model mapping](general-electronic-reporting.md#data-model-and-model-mapping-components) ER component that describes how data model is filled in by application data at runtime
-   BACS (UK)
    > Contains [format](general-electronic-reporting.md#FormatComponentOutbound) and format mapping ER components. Format component specifies the report layout. Format mapping component contains the model data source and specifies how the report layout is filled in at runtime by using this data source.

![ER configurations page](./media/er-quick-start2-imported-solution1.png)

## <a name="PrepareVendorPayment">Prepare a vendor payment for processing</a>

### <a name="AddBankAccount">Add bank information for a vendor account</a>
You must add bank information for a vendor account that will be later referred in a registered payment.

1.  Go to **Accounts payable \> Vendors \> All vendors**.
2.  Select the **GB_SI_000001** vendor account.
3.  On the Action pane, on the **Vendor** tab, in the **Set up** group, select **Bank accounts**.
4.  Select **New**.
    1.  In the **Bank account** field, type **GBP OPER**.
    2.  In the **Bank groups** field, select **BankGBP**.
    3.  In the **Bank account number** field, type 202015.
    4.  In the **SWIFT code** field, type <a name="DefineSWIFTCode">CHASDEFXXXX</a>.
    5.  In the **IBAN** field, type GB33BUKB20201555555555.
    6.  In the **Routing number** field, keep <a name="DefineRoutingNumber">123456</a>.
5.  Select **Save**.
    <br>![Vendor bank accounts page](./media/er-quick-start2-bank-account.png)
6.  Close the page.
7.  On the **All vendors** page, open the **GB_SI_000001** vendor account.
8.  Expand the **Payment** FastTab.
9.  If needed, select **Edit** to make this page editable.
10.  In the **Bank account** field, select **GBP OPER**.
11.  Select **Save**.
    <br>![Vendor page](./media/er-quick-start2-bank-account-reference.png)
12.  Close the page.

### <a name="EnterVendorPayment">Enter a vendor payment</a>
You must enter a new vendor payment by using a [payment proposal](https://docs.microsoft.com/dynamics365/finance/accounts-payable/create-vendor-payments-payment-proposal).

1.  Go to **Navigation pane \> Modules \> Accounts payable \> Payments \> Vendor payment journal**.
2.  Select **New**.
3.  In the **Name** field, select **VendPay**.
4.  Select **Lines**.
5.  Select **Payment proposal**.
6.  Select **Create payment proposal**.
7.  Configure conditions to filter the only records for the **GB_SI_000001** vendor account.
8.  Select **OK**.
9.  Select the offered line for the **00000007_Inv** invoice.
    <br>![Vendor payment proposal page](./media/er-quick-start2-payment-proposal.png)
10. Select **Create payment**.
    <br>![Vendor payments page](./media/er-quick-start2-payment-line.png)

Make sure that the entered payment is configured to use the **Electronic** method of payment.

## <a name="ProcessVendorPayment1">Process a vendor payment by using provided ER format</a>

### <a name="ConfigureMethodOfPayment1">Set up the electronic payment method</a>
You must configure the electronic method of payment to use the ER format of the imported ER solution.

1.  Go to **Accounts payable \> Payment setup \> Methods of payment**.
2.  Expand the **File format** FastTab.
3.  Select the **Electronic** method of payment.
4.  Select **Edit**.
5.  Set the **General electronic export format** field to **Yes**.
6.  In the **Export format configuration** field, select **BACS (UK)** format configuration.
    <br>![Methods of payment - vendors page](./media/er-quick-start2-method-of-payment1.png)
7.  Select **Save**.

### <a name="ProcessPayment1">Process a vendor payment</a>

1.  Go to **Navigation pane \> Modules \> Accounts payable \> Payments \> Vendor payment journal**.
2.  Select earlier added payment journal.
3.  Select **Lines**.
4.  On the **Vendor payments** page, select **Generate payment**.
5.  On the **Generate payments** dialog page, enter the following information:
    -   In the **Method of payment** field, select **Electronic**.
    -   In the **Bank account** field, select **GBSI OPER**.
    -   Select **OK**.
6.  On the **Electronic report parameters** dialog page, enter the following
    information:
    -   Set **Print control report** to **Yes**.
    -   Select **OK**.
        <br>![Electronic report parameters dialog page](./media/er-quick-start2-payment-dialog1.png)
        > [!Note]
        > Note that in addition to the payment file you can now generate the control report only.
7.  Download the offered by using web browser zipped file.
8.  Extract from the downloaded zipped file the control report in Excel format.
9.  Extract from the downloaded zipped file the payment file in TXT format.
    <br>![Payment file preview](./media/er-quick-start2-payment-file1.png)
    > [!Note]
    > Note that, in accordance to the [structure](#PositionRoutingNumber) of the provided ER format, the payment line starts from the routing number that has been [defined](#DefineRoutingNumber) for the configured bank account.

## <a name="CustomizeProvidedFormat">Customize the provided ER format</a>

Assume that you want to use the provided by Microsoft ER solution to generate vendor payment files in BACS format but you need to add a customization that is required to support specific requirements of a particular bank. You also want to keep the ability to upgrade your custom format as soon as a new version of provided by Microsoft ER solution becomes available performing this upgrade with the lowest cost.

To do this, as the representative of the Litware, Inc., you need to create (derive) a new ER format configuration using the Microsoft configuration **BACS (UK)** as a base.

### <a name="DeriveProvidedFormat">Create your custom format</a>

1.  Go to **Navigation pane \> Modules \> Organization administration \> Electronic reporting \> Configurations**.
2.  Expand the **Payment model** in the configurations tree.
3.  Select **BACS (UK)**.
    >   Provided by Microsoft version 1.1 of the **BACS (UK)** ER format configuration will be used by Litware, Inc. as a base for the custom version.
4.  Select **Create configuration** to open the drop dialog.
    >   This lets you create a new configuration for a custom payment format.
5.  In the **New** field, select **Derive from Name: BACS (UK), Microsoft**.
6.  In the **Name** field, type **BACS (UK custom)**.
    <br>![Create configuration dialog page](./media/er-quick-start2-add-derived-format.png)
7.  Select **Create configuration**.

Note that the version 1.1.1 of the **BACS (UK custom)** ER format configuration has been created. This version is in the **Draft**
[status](general-electronic-reporting.md#component-versioning) now and available for editing. The current content of your custom ER format equals the content of the format that has been provided by Microsoft.

![ER configurations page](./media/er-quick-start2-derived-format-configuration1.png)

### <a name="ConfigureDerivedFormat">Edit your custom format</a>

You must configure your custom format to make it compliant with specific requirements of a bank. For example, it could be required to populate to a generated payment file the SWIFT code of a bank (an international bank code that identifies particular banks worldwide also known as a Bank Identifier Code (BIC)) playing the agent role in the processed vendor payment. This code must be up to 11 characters long and placed at the beginning of every payment line in a generated file.

1.  On the configurations page, select **BACS (UK custom)**.
2.  For the version 1.1.1 of the selected configuration, select **Designer**.
3.  Select **Show details** to see more information about format elements.
4.  Expand the **BACSReportsFolder** element of the **Folder** type using to generate an output in ZIP format.
5.  Expand the **file** element of the **File** type using to generate a payment file in TXT format.
6.  Expand the **transactions** element of the **Sequence** type using to generate a single payment line of a payment file.
7.  Expand the **transaction** element of the **Sequence** type using to generate individual fields of a single payment line.
8.  Select the **transaction** element.
    <br>![ER Operations designer](./media/er-quick-start2-derived-format0.png)
    > [!Note]
    > Note that the provided report is configured to <a name="PositionRoutingNumber">start</a> every payment line from the bank routing number by using the **vendBankRouteNum** format element.
9.  Select **Add**.
10. Select the **Text\\String** type of the adding format element.
    1.  In the **Name** field, type **vendBankSWIFT**.
    2.  In the **Minimum length** field, enter 11.
    3.  In the **Maximum length** field, enter 11.
    4.  Select **OK**.
11. In the format structure tree, select **vendBankSWIFT**.
12. Select **Move up** to shift the selected format element one level above. Repeat this step to position the selected **vendBankSWIFT** element as the <a name="PositionSWIFTCode">first element</a> under the parent **transaction** element.
    <br>![ER Operations designer](./media/er-quick-start2-derived-format1.png)
    >
    > Note that the **vendBankSWIFT** element is added to populate to a generated file the SWIFT code of a vendor bank.
13. Keep the **vendBankSWIFT** selected in the format tree.
14. Select the **Mapping** tab.
15. Expand **model** data source.
16. Expand **model.Payment** data source field.
17. Expand **model.Payment.CreditorAgent** data source field.
18. Select **model.Payment.CreditorAgent.BICFI** data source field.
    > The **model.Payment.CreditorAgent.BICFI** data source field exposes a SWIFT code of a vendor bank that is playing the agent role in the processed vendor payment.
19. Select **Bind**.
    > You bound the **vendBankSWIFT** format element with the **model.Payment.CreditorAgent.BICFI** data source field to populate a SWIFT code to a generated payment file.
20. Select **Save**.
    <br>![ER Operations designer](./media/er-quick-start2-derived-format2.png)
21. Close the designer page.

### <a name="MakrFormatRunnable">Mark a custom format as runnable</a>

You created your first version of a custom format that is in the **Draft** status now and want to run it for testing purposes. For running this report, you must process a vendor payment using the payment method that refers to your custom ER format. By default, when you call an ER format from application, the only versions in **Completed** or **Shared** status are [considered](general-electronic-reporting.md#component-versioning) to prevent usage of ER formats the design of which has not been finished. You can force application to use for your test runs the version of your ER format in the **Draft** status allowing you to adjust the current format version if any modification will be needed. For more details, see [Applicability](electronic-reporting-destinations.md#applicability) section.

To use the draft version of an ER format, you must explicitly mark the ER format accordingly.

1.  Go to **Organization administration** \> **Electronic reporting** \> **Configurations**.
2.  On the **Configurations** page, on the Action Pane, on the **Configurations** tab, in the **Advanced settings** group, select **User parameters**.
3.  Set the **Run setting** option to **Yes**.
4.  If needed, select **Edit** to make the current page editable.
5.  In the configurations tree, select **BACS (UK custom)**.
6.  Set the **Run draft** option to **Yes**.
    <br>![ER Operations designer](./media/er-quick-start2-derived-format-configuration2.png)

## <a name="ProcessVendorPayment2">Process a vendor payment by using custom ER format</a>

### <a name="ConfigureMethodOfPayment2">Set up the electronic payment method</a>

You must configure the electronic method of payment to use your custom ER format for vendor payments processing.

1.  Go to **Accounts payable \> Payment setup \> Methods of payment**.
2.  Expand the **File format** FastTab.
3.  Select the **Electronic** method of payment.
4.  Select **Edit**.
5.  Set the **General electronic export format** field to **Yes**.
6.  In the **Export format configuration** field, select **BACS (UK custom)** format configuration.
7.  Select **Save**.
    <br>![Methods of payment - vendors page](./media/er-quick-start2-method-of-payment2.png)

### <a name="ProcessPayment2">Process a vendor payment</a>

1.  Go to **Navigation pane \> Modules \> Accounts payable \> Payments \> Payment journal**.
2.	Select the payment journal that has been created earlier.
3.  Select **Lines**.
4.  Select **Payment status**.
5.  Select **None**.
6.  On the **Vendor payments** page, select **Generate payment**.
7.  On the **Generate payments** dialog page, enter the following information:
    -   In the **Method of payment** field, select **Electronic**.
    -   In the **Bank account** field, select **GBSI OPER**.
    -   Select **OK**.
8.  On the **Electronic report parameters** dialog page, enter the following
    information:
    -   Set **Print control report** to **Yes**.
    -   Select **OK**.
    > [!Note]
    > Note that in addition to the payment file you can now generate the control report only.
9.  Download the offered by using web browser zipped file.
10. Extract from the downloaded zipped file the control report in Excel format.
11. Extract from the downloaded zipped file the payment file in TXT format.
    <br>![Payment file preview](./media/er-quick-start2-payment-file2.png)
    > [!Note]
    > Note that in accordance to the structure of your custom ER format, the payment line in a generated file now [starts](#PositionSWIFTCode) from the SWIFT code that has been [entered](#DefineSWIFTCode) for a bank account of a vendor whose payment has been processed.

## <a name="ImportERSolution2">Import the new version of the provided ER solution</a>

Assume that you have got a notification about the knowledge base article [KB3763330](https://fix.lcs.dynamics.com/Issue/Details?kb=3182046) informing about the new version of the **BACS (UK)** ER format that has been published by Microsoft. In addition to the control report, this new version offers the possibility to generate the payment advice and the attending note reports while a vendor payment is processed. You want to start using the functionality in you Finance instance.

### <a name="ImportERFormat2">Import the new version of the ER format of the provided ER solution</a>

To bring a new version of the provided ER solution to the current Finance instance, you must import it from the configured for this ER
[repository](general-electronic-reporting.md#Repository).

1.  Go to the **Navigation pane** and select **Organization administration**.
2.  Go to **Workspaces \> Electronic reporting**.
3.  In the **Providers** grid, select the **Microsoft** tile.
4.  Select **Repositories** to open the list of repositories for the Microsoft provider.
5.  Select the repository of **Global** type.
6.  Select **Open**. If prompted, follow the authorization instructions.
7.  In the configurations tree in the left pane, select the **BACS (UK)** format configuration.
8.  On the **Versions** FastTab, select the version 3.3 of the selected ER format configuration.
9.  On the **Versions** FastTab, click **Import** to download the selected version from Global repository to the current Finance instance.

![ER repository page](./media/er-quick-start2-import-solution2.png)

If you experience difficulties with accessing [Global repository](er-download-configurations-global-repo.md), use the alternative way
of configuration [downloading](download-electronic-reporting-configuration-lcs.md) from Microsoft Lifecycle Services (LCS).

### <a name="ReviewImportedERFormat">Review the imported ER format</a>

1.  Go to the **Navigation pane** and select **Organization administration**.
2.  Go to **Workspaces \> Electronic reporting**.
3.  Select **Reporting configurations**.
4.  Expand **Payment model** in the configurations tree.
5.  Select **BACS (UK)**.
6.  On the **Versions** FastTab, select the version 3.3.
7.  Select **Designer**.
8.  Expand the **BACSReportsFolder** format element.
    <br>![ER configurations page](./media/er-quick-start2-imported-solution2.png)
    > [!Note]
    > Note that the version 3.3 additionally contains the **PaymentAdviceReport** format element using to generate a payment advice report when a vendor payment is processed.     
9.  Close the designer page.

## <a name="AdoptNewBaseVersion">Adopt changes of the new version of imported format in a custom format</a>

### <a name="CompleteDerivedFormat">Complete the current draft version of a custom format</a>

If you want to keep the current state of your custom format, you can complete the draft version 1.1.1 changing its status from **Draft** to **Completed**.

1.  On the configurations page, expand **Payment model**.
2.  Expand **BACS (UK)**.
3.  Select **BACS (UK custom)**.
4.  On the **Versions** FastTab, select **Change status**.
5.  Select **Complete**.
6.  Select **OK**.

The status of the version 1.1.1 has been changed from **Draft** to **Completed** making it read-only. The new editable version 1.1.2 has been added in the **Draft** status. You can use it for making further modifications in your custom ER format.

### <a name="RebaseDerivedFormat">Rebase your custom format to a new base version</a>

To start using a new functionality of the version 3.3 of the BACS (UK) format along with your customization, you need to change the base ([rebase](general-electronic-reporting.md#upgrading-a-format-selecting-a-new-version-of-base-format-rebase)) configuration version for the custom configuration **BACS (UK custom)**. Instead of version 1.1 of BACS (UK), use new version 3.3.

1.  Go to **Organization administration** \> **Electronic reporting** \> **Configurations**.
2.  In the tree, expand **Payments model**.
3.  In the tree, select **BACS (UK custom)**.
4.  On the **Versions** FastTab, for the version 1.1.2 select **Rebase**.
5.  In the **Target version** field, select the new version 3.3 of the base configuration to be applied as a new base for updating the configuration.
    <br>![ER configurations page](./media/er-quick-start2-rebase1.png)
6.  Select **OK**.
    <br>![ER configurations page](./media/er-quick-start2-rebase2.png)
    > [!Note]
    > Note that some conflicts might be discovered between merging custom version and a new base version representing some format changes that can't be merged automatically. If conflicts are discovered, they must be resolved in the format designer manually.
    > [!Note]
    > Note that the number of the draft version has been changed from 1.1.2 to 3.3.2 reflecting the base version change.
7.  On the **Versions** FastTab, select the version 3.3.2.
8.  Select **Designer**.
9.  On the **Details** tab, for a rebase conflict record, select **Apply base value**.
    <br>![ER Operations designer](./media/er-quick-start2-rebase3.png)
10. Select **Save**.
    <br>![ER Operations designer](./media/er-quick-start2-rebase4.png)
    >
    > You resolved this conflict confirming that the version 3 of the base model must be used in this ER format.
11. Expand **BACSReportsFolder**.
12. Expand **BACSReportsFolder\file**.
13. Expand **BACSReportsFolder\file\transactions**.
14. Expand **BACSReportsFolder\file\transactions\transaction**.
15. Select the **Mapping** tab.
    <br>![ER Operations designer](./media/er-quick-start2-rebase5.png)
    > [!Note]
    > Note that the version 3.3.2 of your custom ER format contains your customization (**vendBankSWIFT** format element and its binding) and new functionality of the provided by Microsoft version 3.3 of the base ER format (**PaymentAdviceReport** format element with nested elements and configured bindings). You adopted modifications of a new base version merging them with your customization within a few clicks.
16. Close the designer.
    > Note that the rebase action is reversible. If you want to cancel this rebase, select the version 1.1.1 of the **BACS (UK custom)** format on the **Versions** FastTab and select the **Get this version** option. After that, the version 3.3.2 will be renumbered back to 1.1.2. The content of the draft version 1.1.2 will be equal the content of the version 1.1.1.

### <a name="ProcessPayment3">Process a vendor payment by using rebased ER format</a>

1.  Go to **Navigation pane \> Modules \> Accounts payable \> Payments \> Vendor payment journal**.
2.	Select the payment journal that has been created earlier.
3.  Select **Lines**.
4.  Select **Payment status**.
5.  Select **None**.
6.  On the **Vendor payments** page, select **Generate payment**.
7.  On the **Generate payments** dialog page, enter the following information:
    -   In the **Method of payment** field, select **Electronic**.
    -   In the **Bank account** field, select **GBSI OPER**.
    -   Select **OK**.
8.  On the **Electronic report parameters** dialog page, enter the following
    information:
    -   Set **Print control report** to **Yes**.
    -   Set **Print payment advice** to **Yes**.
        <br>![Electronic report parameters dialog page](./media/er-quick-start2-payment-dialog2.png)
        > [!Note]
        > Note that in addition to the payment file you can now generate not only the control report but the payment advice report as well.
    -   Select **OK**.
9.  Download the offered by using web browser zipped file.
10. Extract from the downloaded zipped file the control report in Excel format.
11. Extract from the downloaded zipped file the payment advice report in Excel format.
    <br>![Payment advice report preview](./media/er-quick-start2-payment-advice-report.png)
12. Extract from the downloaded zipped file the payment file in TXT format.
    <br>![Payment file preview](./media/er-quick-start2-payment-file3.png)
    > [!Note]
    >
    > The payment line in a generated file starts from the SWIFT code that has been entered for a bank account of a vendor whose payment has been processed.
    >
    > The zipped output additionally contains a payment advice report in Excel format.

## <a name="References">Additional resources</a>

-   [Electronic Reporting overview](general-electronic-reporting.md)
-   [Download ER configurations from Lifecycle Services](download-electronic-reporting-configuration-lcs.md)
-   [Download ER configurations from Global repository of Configuration service](er-download-configurations-global-repo.md)
