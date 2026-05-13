---
title: Debug data sources of an executed ER format to analyze data flow and transformation
description: Learn about you can debug the data sources of an executed ER format to better understand the configured data flow and transformation.
author: kfend
ms.author: filatovm
ms.topic: how-to
ms.date: 04/01/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2020-04-01
ms.search.form: ERSolutionTable, EROperationDesigner
ms.dyn365.ops.version: Release 10.0.11
ms.assetid: 
ms.custom:
  - sfi-image-nochange
---

# Debug data sources of an executed ER format to analyze data flow and transformation

[!include[banner](../includes/banner.md)]

When you [configure](tasks/er-format-configuration-2016-11.md) an Electronic reporting (ER) solution to generate outbound documents, you define the methods that get data out of the application and enter it in the generated output. To make the life cycle support of the ER solution more efficient, your solution should consist of an ER data model and its mapping components, and also an ER format and its mapping components. The model mapping is application-specific, whereas other components remain application-agnostic. Therefore, several ER components might affect the process of entering data in the generated output.

Sometimes, the data in the generated output looks different from the same data in the application database. In these cases, you want to determine which ER component is responsible for the data transformation. The ER data source debugger feature significantly reduces the time and cost that are involved in this investigation. You can interrupt the execution of an ER format and open the data source debugger interface. There, you can browse the available data sources and select an individual data source for execution. This manual execution simulates the execution of the data source during the real run of an ER format. The result is presented on a page where you can analyze the data that is received.

To turn on the data source debugging feature, set the **Enable data debugging at format run** option to **Yes** in the ER user parameters. You can then start data source debugging while you run an ER format to generate outbound documents. You can also use the **Start debugging** option to initiate data source debugging for an ER format that is configured in the [ER Operation designer](./tasks/er-format-configuration-2016-11.md#design-the-format-of-an-electronic-document).

This article provides guidelines for initiating data source debugging for executed ER formats. It explains how the information can help you understand the data flow and data transformations. The examples in this article use the business process for vendor payments processing.

## Limitations

You can use the data source debugger to access the data of data sources that are used in ER formats that run to generate outbound documents. You can't use it to debug data sources of ER formats that are designed to parse inbound documents.

The following settings of ER formats aren't currently accessible for data source debugging:

- Format transformations
- Format and mapping validation rules
- Enabling expressions
- Details of in-memory data collection

## Prerequisites

- To complete the examples in this article, you must have access to one of the following [roles](../sysadmin/tasks/assign-users-security-roles.md):

    - Electronic reporting developer
    - Electronic reporting functional consultant
    - System administrator

- Set the company to **DEMF**.

- Follow the steps in [Appendix 1](#appendix1) of this article to download the components of the Microsoft ER solution that are required to process vendor payments.
- Follow the steps in [Appendix 2](#appendix2) of this article to prepare Accounts payable for vendor payment processing by using the ER solution that you download.

## Process a vendor payment to get a payment file

1. Follow the steps in [Appendix 3](#appendix3) of this article to process vendor payments.

    :::image type="content" source="./media/er-data-debugger-process-payment.png" alt-text="Screenshot of vendor payment processing in progress.":::

1. Download and save the ZIP file to your local computer.
1. Extract the **ISO20022 Credit transfer.xml** payment file from the ZIP file.
1. Open the extracted payment file by using the XML file viewer.

    In the payment file, the International Bank Account Number (IBAN) code of the vendor bank account contains no spaces. Therefore, it differs from the value that was [entered](#enteredIBANcode) on the **Bank accounts** page.

    :::image type="content" source="./media/er-data-debugger-payment-file.png" alt-text="Screenshot of IBAN code without spaces in the payment file.":::

    Use the ER data source debugger to learn which component of the ER solution truncates spaces in the IBAN code.

## Turn on data source debugging

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. On **Configurations**, on the Action Pane, on the **Configurations** tab, in the **Advanced settings** group, select **User parameters**.
1. Set the **Enable data debugging at format run** option to **Yes**.

    > [!NOTE]
    > This parameter is user-specific and company-specific.

    :::image type="content" source="./media/er-data-debugger-user-parameters.png" alt-text="Screenshot of User parameters dialog box with Enable data debugging at format run option.":::

## Process a vendor payment for debugging

1. Follow the steps in [Appendix 3](#appendix3) of this article to process vendor payments.
1. In the message box, select **Yes** to confirm that you want to interrupt vendor payment processing and instead start data source debugging on the **Debug Datasources** page.

    :::image type="content" source="./media/er-data-debugger-start-debugging.png" alt-text="Screenshot of confirmation message box for starting data source debugging.":::

## Debug data sources that are used in payment processing

### Debug the model mapping

1. On **Debug Datasources**, on the Action Pane, select **Model mapping** to start debugging from this ER component.
1. In the data source pane on the left, select the **$notSentTransactions** data source, and then select **Read all records**.

    To force the appropriate number of records to be read from the selected data source, select **Read 1 record**, **Read 10 records**, **Read 100 records**, or **Read all records**. By using this approach, you can simulate access to the data source from the running ER format.

1. In the data pane on the right, select **Expand all**.

    You see that the selected data source of the **Record list** type contains a single record.

1. Expand the **$notSentTransactions** data source, and select the nested **vendBankAccountInTransactionCompany()** method.
1. Expand the **vendBankAccountInTransactionCompany()** method, and select the nested **IBAN** field.
1. Select **Get value**.

    Select **Get value** to force the value of a selected field of the selected data source to be read. By using this approach, you can simulate access to this field from the running ER format.

1. Select **Expand all**.

    :::image type="content" source="./media/er-data-debugger-debugging-model-mapping.png" alt-text="Screenshot of the value of the IBAN field in the model mapping.":::

    As you can see, the model mapping isn't responsible for the truncated spaces, because the IBAN code that it returns for the vendor bank account includes spaces. Therefore, you must continue data source debugging.

### Debug the format mapping

1. On **Debug Datasources**, on the action pane, select **Format mapping** to continue debugging from this ER component.
1. Select the **\$PaymentByDebtor** data source, and then select **Read all records**.
1. Expand **\$PaymentByDebtor**.
1. Expand **\$PaymentByDebtor.Lines**, and then select **Read all records**.
1. Expand **\$PaymentByDebtor.Lines.CreditorAccount**.
1. Expand **\$PaymentByDebtor.Lines.CreditorAccount.Identification**, and then select **\$PaymentByDebtor.Lines.CreditorAccount.Identification.IBAN**.
1. Select **Get value**.
1. Select **Expand all**.

    :::image type="content" source="./media/er-data-debugger-debugging-format-mapping.png" alt-text="Screenshot of the value of the IBAN field in the format mapping.":::

    As you can see, the data sources of the format mapping aren't responsible for the truncated spaces, because the IBAN code that they return for the vendor bank account includes spaces. Therefore, you must continue data source debugging.

### Debug the format

1. On **Debug Datasources**, on the action pane, select **Format** to continue debugging from this ER component.
1. Expand the format elements to select **ISO20022CTReports** > **XMLHeader** > **Document** > **CstmrCdtTrfInitn** > **PmtInf**, and then select **Read all records**.
1. Expand the format elements to select **ISO20022CTReports** > **XMLHeader** > **Document** > **CstmrCdtTrfInitn** > **PmtInf** > **CdtTrfTxInf**, and then select **Read all records**.
1. Expand the format elements to select **ISO20022CTReports** > **XMLHeader** > **Document** > **CstmrCdtTrfInitn** > **PmtInf** > **CdtTrfTxInf** > **CdtrAcct** > **Id** > **IBAN** > **BankIBAN**, and then select **Get value**.
1. Select **Expand all**.

    :::image type="content" source="./media/er-data-debugger-debugging-format.png" alt-text="Screenshot of the value of the IBAN field in the format.":::

   As you can see, the format binding isn't responsible for the truncated spaces because the IBAN code that it returns for the vendor bank account includes spaces. Therefore, the **BankIBAN** element is configured to use a format transformation that truncates spaces.

1. Close the data source debugger.

### Review the format transformations

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. On **Configurations**, select **Payment model** > **ISO20022 Credit transfer**.
1. Select **Designer**, and then expand the elements to select **Document** > **CstmrCdtTrfInitn** > **PmtInf** > **CdtTrfTxInf** > **CdtrAcct** > **Id** > **IBAN** > **BankIBAN**.

    :::image type="content" source="./media/er-data-debugger-referred-transformation.png" alt-text="Screenshot of BankIBAN element on the Format designer page.":::

    As you can see, the **BankIBAN** element is configured to use the **remove not alphanumeric** transformation.

1. Select the **Transformations** tab.

    :::image type="content" source="./media/er-data-debugger-transformation.png" alt-text="Screenshot of Transformations tab for the BankIBAN element.":::

    As you can see, the **remove not alphanumeric** transformation uses an expression that truncates spaces from the provided text string.

## Start to debug in the Operation designer

When you configure a draft version of the ER format that you can run directly from the Operation designer, you can access the data source debugger by selecting **Start Debugging** on the Action Pane.

:::image type="content" source="./media/er-data-debugger-run-from-designer.png" alt-text="Screenshot of Start Debugging button on the Format designer page.":::

You can debug the format mapping and format components of the ER format that you're editing.

## Start debugging in the Model mapping designer

When you configure an ER model mapping that you can run from the **Model mapping** page, select **Start Debugging** on the Action Pane to access the data source debugger.

:::image type="content" source="./media/er-data-debugger-run-from-designer-mapping.png" alt-text="Screenshot of Start Debugging button on the Model mapping designer page.":::

You can debug the model mapping component of the ER mapping that you're editing.

## <a name="appendix1"></a>Appendix 1: Get an ER solution

### Download an ER solution

To use an ER solution to generate an electronic payment file for a processed vendor payment, [download](download-electronic-reporting-configuration-lcs.md) the **ISO20022 Credit transfer** ER payment format from the Shared asset library in Microsoft Dynamics Lifecycle Services (LCS) or from the Global repository.

:::image type="content" source="./media/er-data-debugger-import-from-repo.png" alt-text="Screenshot of importing the ER payment format on the Configuration repository page.":::

In addition to the selected ER format, automatically import the following [configurations](general-electronic-reporting.md#Configuration) into your Microsoft Dynamics 365 Finance instance as part of the **ISO20022 Credit transfer** ER solution:

- **Payment model** ER data model configuration
- **ISO20022 Credit transfer** ER format configuration
- **Payment model mapping 1611** ER model mapping configuration
- **Payment model mapping to destination ISO20022** ER model mapping configuration

You can find these configurations on the **Configurations** page of the ER framework (**Organization administration** \> **Electronic reporting** \> **Configurations**).

:::image type="content" source="./media/er-data-debugger-configurations.png" alt-text="Screenshot of configurations imported on the Configurations page.":::

If any of the previously listed configurations are missing in the configuration tree, manually download them from the LCS Shared asset library in the same way that you downloaded the **ISO20022 Credit transfer** ER payment format.

### Analyze the downloaded ER solution

#### Review the model mapping

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. Select **Payment model** > **Payment model mapping 1611**.
1. Select **Designer**.
1. Select the **Payment model mapping ISO20022 CT** mapping record.
1. Select **Designer**, and then review the model mapping that opens.

    Notice that the **Payments** field of the data model is bound to the **$notSentTransactions** data source that returns the list of vendor payment lines that are being processed.

    :::image type="content" source="./media/er-data-debugger-model-mapping.png" alt-text="Screenshot of Payments field on the Model mapping designer page.":::

#### Review the format mapping

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. Select **Payment model** > **ISO20022 Credit transfer**.
1. Select **Designer**.
1. On the **Mapping** tab, review the format mapping that opens.

    Notice that the **Document** > **CstmrCdtTrfInitn** > **PmtInf** element of the **ISO20022CTReports** > **XMLHeader** file is bound to the **$PaymentByDebtor** data source that is configured to group records of the data model's **Payments** field.

    :::image type="content" source="./media/er-data-debugger-format-mapping.png" alt-text="Screenshot of PmtInf element on the Format designer page.":::

#### Review the format

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. Select **Payment model** > **ISO20022 Credit transfer**.
1. Select **Designer**, and then review the format that opens.

    Notice that the format element under **Document** > **CstmrCdtTrfInitn** > **PmtInf** > **CdtTrfTxInf** > **CdtrAcct** > **Id** > **IBAN** > **BankIBAN** is configured to enter the IBAN code of the vendor account in the payment file.

    :::image type="content" source="./media/er-data-debugger-format.png" alt-text="Screenshot of BankIBAN format element on the Format designer page.":::

## <a name="appendix2"></a>Appendix 2: Configure Accounts payable

### Modify a vendor property

1. Go to **Accounts payable** > **Vendors** > **All vendors**.
1. Select vendor **DE-01002**. On the Action Pane, on the **Vendor** tab, in the **Set up** group, select **Bank accounts**.
1. On the **Identification** FastTab, in the **IBAN** field, <a name="enteredIBANcode"></a>enter **GB33 BUKB 2020 1555 5555 55**.
1. Select **Save**.

:::image type="content" source="./media/er-data-debugger-iban.png" alt-text="Screenshot of IBAN field set on the Vendor bank accounts page.":::

### Set up a method of payment

1. Go to **Accounts payable** > **Payment setup** > **Methods of payment**.
1. Select the **SEPA CT** payment method.
1. On the **File formats** FastTab, in the **File formats** section, set the **Generic electronic Export format** option to **Yes**.
1. In the **Export format configuration** field, select the **ISO20022 Credit transfer** ER format.
1. Select **Save**.

:::image type="content" source="./media/er-data-debugger-payment-method.png" alt-text="Screenshot of file format settings on the Methods of payment page.":::

### Add a vendor payment

1. Go to **Accounts payable** > **Payments** > **Vendor payment journal**.
1. Add a new payment journal.
1. Select **Lines**, and add a new payment line.
1. In the **Account** field, select vendor **DE-01002**.
1. In the **Debit** field, enter a value.
1. In the **Method of payment** field, select **SEPA CT**.
1. Select **Save**.

:::image type="content" source="./media/er-data-debugger-payment-journal.png" alt-text="Screenshot of vendor payment added on the Vendor payments page.":::

## <a name="appendix3"></a>Appendix 3: Process a vendor payment

1. Go to **Accounts payable** > **Payments** > **Vendor payment journal**.
1. On the **Vendor payment journal** page, select the payment journal that you previously created, and then select **Lines**.
1. Select the payment line, and then select **Payment status** > **None**.
1. Select **Generate payments**.
1. In the **Method of payment** field, select **SEPA CT**.
1. In the **Bank account** field, select **DEMF OPER**.
1. In the **Generate payments** dialog box, select **OK**.
1. In the **Electronic report parameters** dialog box, select **OK**.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
