---
# required metadata
title: Debug data sources of an executed ER format to analyze data flow and transformation
description: This topic explains how you can debug the data sources of an executed ER format to better understand the configured data flow and transformation.
author: NickSelin
manager: AnnBe
ms.date: 04/22/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: ERSolutionTable, EROperationDesigner
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2020-04-01
ms.dyn365.ops.version: Release 10.0.11

---

# Debug data sources of an executed ER format to analyze data flow and transformation

[!include[banner](../includes/banner.md)]

[!include[banner](../includes/preview-banner.md)]

When you [configure](tasks/er-format-configuration-2016-11.md) an Electronic reporting (ER) solution to generate particular outbound documents, you define the methods that are used to get data out of the application and enter it in the output that is generated. To make the life cycle support of this ER solution more efficient, your solution should consist of an ER [data
model](general-electronic-reporting.md#DataModelComponent) and its [mapping](general-electronic-reporting.md#ModelMappingComponent)
components as well as an ER [format](general-electronic-reporting.md#FormatComponentOutbound) and its mapping components to make the model mapping application-specific while keeping other components application agnostic. Therefore, several ER components may
[affect](general-electronic-reporting.md#FormatComponentOutbound) the process of entering data in a generated output.

Sometimes, the data of the generated output looks different when compared with same data in the application database. When this happens you will want to determine which ER component is responsible for the data transformation. The ER data sources debugger feature significantly reduces the time and costs that are involved in this investigation. This debugger allows you to interrupt the execution of an ER format and open the data sources debugger interface where you can browse available data sources and select an individual data source for execution. This manual execution simulates its execution during the real run of an ER format. The result is presented in the page whre you can analyze the received data.

To enable data sources debugging, set the ER user parameters field, **Enable data debugging at format run** to **Yes**. When you enable this function, you can start data sources debugging while you run an ER format to generate outbound documents. You can also use the **Start debugging** option to initiate data sources debugging for an ER format that is configured in the [ER Operation
designer](./tasks/er-format-configuration-2016-11.md#design-the-format-of-an-electronic-document).

This topic provides guidelines about how to initiate data sources debugging for executed ER formats, and how to use the information to help you understand the data flow and data transformations. The vendor payments processing business process is used in this topic.

## Limitations

Data sources debugger can be used for accessing data of data sources using in ER formats that are executed to generate outbound documents. The debugger can’t be used for debugging data sources of ER formats that are designed to parse inbound documents.

The following settings of ER formats are not currently accessible for data sources debugging:

- Format transformations
- Format and mapping validation rules
- Enabling expressions
- Details of in-memory data collection

## Prerequisites

- To complete the examples in this topic, you must have the access to one of the following [roles](../sysadmin/tasks/assign-users-security-roles.md):

    - Electronic reporting developer
    - Electronic reporting functional consultant
    - System administrator

- The company must be set to **DEMF**.

- Follow the steps in [Appendix 1](#appendix1) in this topic to download the required components of the Microsoft ER
solution to process vendor payments.
- Follow the steps in [Appendix 2](#appendix2) in this topic to prepare accounts payable for vendor payment processing by using
the ER solution you will download.

## Process a vendor payment to get a payment file

1.  Follow the steps in [Appendix 3](#appendix3) of this topic to process vendor payment.

    ![Vendor payments page](./media/er-data-debugger-process-payment.png)

2.  Download and save the zip file to your local machine.
3.  From the zop file, extract the **ISO20022 Credit transfer.xml** payment file.
4.  Open the extracted payment file by using the XML files viewer.

    The vendor bank account IBAN code in the payment file differs from the value that has been [entered](#enteredIBANcode) in the **Bank accounts** page as it contains no spaces.

    ![Payment file preview](./media/er-data-debugger-payment-file.png)

    You can use the ER data sources debugger to find a component of the ER solution that is used for truncating spaces of the IBAN code.

## Enable data sources debugging

1.  Go to **Organization administration \> Electronic reporting \> Configurations**.
2.  On the **Configurations** page, on the Action Pane, on the **Configurations** tab, in the **Advanced settings** group, select **User
    parameters**.
3.  Set the **Enable data debugging at format run** field to **Yes**.

> [!NOTE]
> This parameter is user- and company-specific.

    ![ER user parameters](./media/er-data-debugger-user-parameters.png)

## Process vendor payment for debugging

1.  Follow the steps in [Appendix 3](#appendix3) of this topic to process vendor payments.
2.  Select **Yes** to confirm that you want to interrupt vendor payment processing, and instead start data source debugging on the **Debug data sources** page.

    ![Data sources debugging initiation dialog](./media/er-data-debugger-start-debugging.png)

## Debug data sources using in payment processing

### Debug model mapping

1.  On the **Debug data sources** page, on the Action Pane, select **Model mapping** to start debugging from this ER component.
2.  On the left-side data sources panel, select **\$notSentTransactions** data source, and then select **Read all records**.

    You can select to **Read 1 record**, **Read 10 records**, **Read 100 records**, or **Read all records** to force reading the appropriate number of records from the selected data source. This will simulate access to this data source from the running ER format.

3.  On the right-side data panel, select **Expand all**.

    You can see that the selected data source of the *Record list* type contains a single record.

4. Expand the **\$notSentTransactions** data source, and select the nested **vendBankAccountInTransactionCompany()** method.
5. Expand the **vendBankAccountInTransactionCompany()** method, and select the nested **IBAN** field.
6.  Select **Get value**.

    You can select **Get value** to force the reading value of a selected field of the chosen data source. This will simulate access to this field from the running ER format.
    
7. Select **Expand all**.

    ![Data sources debugger page](./media/er-data-debugger-debugging-model-mapping.png)

    You can see that the model mapping is not responsible for the truncation spaces as it returns the vendor bank account IBAN code with non-truncated spaces. You need to continue your data source debugging.

### Debug format mapping

1. On the **Debug data sources** page, on the Action Pane, select **Format mapping** to continue debugging with this ER component.
2. Select the data source, **\$PaymentByDebtor**, and then select **Read all records**.
3. Expand **\$PaymentByDebtor**.
4. Expand **\$PaymentByDebtor.Lines**, and then select **Read all records**.
5. Expand **\$PaymentByDebtor.Lines.CreditorAccount**.
6. Expand **\$PaymentByDebtor.Lines.CreditorAccount.Identofication**, and then select **\$PaymentByDebtor.Lines.CreditorAccount.Identofication.IBAN**.
7. Select **Get value**.
8. Select **Expand all**.

    ![Data sources debugger page](./media/er-data-debugger-debugging-format-mapping.png)

    You can see that the format mapping data sources are not responsible for the truncation spaces as they return the vendor bank account IBAN code with non-truncated spaces. You need to continue your data source debugging.

### Debug format

1. On the **Debug data sources** page, on the Action Pane, select **Format** to continue debugging with this ER component.
2. Expand the format elements to select **ISO20022CTReports** \> **XMLHeader** \> **Document** \> **CstmrCdtTrfInitn \> PmtInf**, and the select **Read all records**.
3. Expand the format elements to select **ISO20022CTReports** \> **XMLHeader** \> **Document** \> **CstmrCdtTrfInitn** \> **PmtInf** \> **CdtTrfTxInf**, and then select **Read all records**.
4. Expand format elements to select **ISO20022CTReports** \> **XMLHeader** \> **Document** \> **CstmrCdtTrfInitn** \> **PmtInf** \> **CdtTrfTxInf** \> **CdtrAcct** \> **Id** \> **IBAN** \> **BankIBAN**, and then select **Get value**
5. Select **Expand all**.

    ![Data sources debugger page](./media/er-data-debugger-debugging-format.png)

    You can see that the format binding is not responsible for the truncation spaces as it returns the vendor bank account IBAN code with non-truncated spaces. This means that the **BankIBAN** element is configured to use a format transformation that performs the truncation of spaces.

6. Close the data sources debugger.

### Review format transformations

1. Got to **Organization administration** \> **Electronic reporting** \> **Configurations**.
2. On the **Configurations** page, select the configuration, **Payment model** \> **ISO20022 Credit transfer**.
3. Select **Designer**, and then expand the elements to select **Document** \> **CstmrCdtTrfInitn** \> **PmtInf** \> **CdtTrfTxInf** \> **CdtrAcct** \> **Id** \> **IBAN** \> **BankIBAN**.

    ![Format designer page](./media/er-data-debugger-referred-transformation.png)

    The **BankIBAN** element is configured to use the **Remove not alphanumeric** transformation.

4.  Select the **Transformations** tab.

    ![Format designer page](./media/er-data-debugger-transformation.png)

    The **Remove not alphanumeric** transformation is configured to use an expression that truncates spaces from the provided text string.

## Start debugging in Operation designer

When you configure a draft version of the ER format which can be executed right from the Operation designer, you can directly call the data sources debugger by selecting **Start debugging**.

![Format designer page](./media/er-data-debugger-run-from-designer.png)

The format mapping and format components of the editing ER format are available for debugging.

## Start debugging in the Model mapping designer

When you configure an ER model mapping that can be executed from the **Model mapping** page, you can directly call the data sources debugger by selecting **Start debugging**.

![Modle mapping designer page](./media/er-data-debugger-run-from-designer-mapping.png)

The model mapping component of the editing ER mapping is available for debugging.

## <a name="appendix1">Appendix 1: Get an ER solution</a>

### Download an ER solution

Assume that you want to use an ER solution to generate an electronic payment file for a processed vendor payment. You can
[download](download-electronic-reporting-configuration-lcs.md) the available **ISO20022 Credit transfer** ER payment format from the Microsoft Dynamics Lifecycle Services (LCS) shared asset library or Global repository.

![ER repository page](./media/er-data-debugger-import-from-repo.png)

In addition to the selected ER format, the following [configurations](general-electronic-reporting.md#Configuration) must be automatically imported to your Finance instance as part of the **ISO20022 Credit transfer** ER solution:

- **Payment model** [ER data model configuration](general-electronic-reporting.md#DataModelComponent)
- **ISO20022 Credit transfer** [ER format configuration](general-electronic-reporting.md#FormatComponentOutbound) 
- **Payment model mapping 1611** [ER model mapping configuration](general-electronic-reporting.md#ModelMappingComponent)
- **Payment model mapping to destination ISO20022** ER model mapping configuration

You can find these configurations in the **Configurations** page (**Organization administration** \> **Electronic reporting** \> **Configurations**) of the ER framework.

![ER configurations page](./media/er-data-debugger-configurations.png)

If some of the listed configurations are missing in the configurations tree, they must be manually downloaded from the LCS shared asset library in the same manner as the described for the **ISO20022 Credit transfer** ER payment format.

### Analyze the downloaded ER solution

#### Review model mapping

1.  Go to **Organization administration** \> **Electronic reporting** \> **Configurations**.
2.  Select the **Payment model** \> **Payment model mapping 1611** configuration.
3.  Select **Designer**.
4.  Select the **Payment model mapping ISO20022 CT** mapping record.
5.  Select **Designer**, and then review the opened model mapping.

> [!NOTE]
> The **Payments** field of the data model is bound to the **\$notSentTransactions** data source which returns the list of processing vendor payment lines.

![ER model mapping designer page](./media/er-data-debugger-model-mapping.png)

#### Review format mapping

1.  Go to **Organization administration** \> **Electronic reporting** \> **Configurations** page.
2.  Select **Payment model** \> **ISO20022 Credit transfer**.
3.  Select **Designer**.
4.  Select the **Mapping** tab, and then review the opened format mapping.

> [!NOTE]
> The **Document** \> **CstmrCdtTrfInitn** \> **PmtInf** element of the **ISO20022CTReports** \> **XMLHeader** file is bound to the **\$PaymentByDebtor** data source that is configured to group records of the data model **Payments** field.

![ER model mapping designer page](./media/er-data-debugger-format-mapping.png)

#### Review format

1.  Go to **Organization administration** \> **Electronic reporting** \> **Configurations**.
2.  Select **Payment model** \> **ISO20022 Credit transfer**.
3.  Select **Designer**, and then review the opened format.

> [!NOTE]
> The format element under **Document** \> **CstmrCdtTrfInitn** \> **PmtInf** \> **CdtTrfTxInf** \> **CdtrAcct** \> **Id** \> **IBAN** \> **BankIBAN** is configured to populate the vendor account’s IBAN code to the payment file.

![ER model mapping designer page](./media/er-data-debugger-format.png)

## <a name="appendix2">Appendix 2: Configure accounts payable</a>

### Modify a vendor property

1.  Go to **Accounts payable** \> **Vendors** \> **All vendors**.
2.  Select the vendor, **DE-01002**, and on the Action Pane, on the **Vendor** tab, in the **Set up** group, select **Bank accounts**.
3.  On the **Identification** FastTab, in the **IBAN** field, <a name="enteredIBANcode">enter</a> **GB33 BUKB 2020 1555 5555 55**.
4.  Select **Save**.

![Vendor bank accounts page](./media/er-data-debugger-iban.png)

### Set up a method of payment

1.  Go to **Accounts payable** \> **Payment setup** \> **Methods of payment**.
2.  On the **Methods of payment** page, select the **SEPA CT** payment method.
3.  On the **File format** FastTab, set the **Generic electronic export format** field to **Yes**.
4.  In the **Export format configuration** field, select the ER format, **ISO20022 Credit transfer**.
5.  Select **Save**.

![Methods of payment page](./media/er-data-debugger-payment-method.png)

### Add a vendor payment

1.  Go to **Accounts payable** \> **Payments** \> **Vendor payment journal**.
2.  Add a new payment journal.
3.  Select **Lines**, and add a new payment line.
4.  In the **Account** field, select **DE-01002** vendor.
5.  In the **Debit** field, enter a value.
6.  In the **Method of payment** field, select **SEPA CT**.
7.  Select **Save**.

![Vendor payments page](./media/er-data-debugger-payment-journal.png)

## <a name="appendix3">Appendix 3: Process vendor payment</a>

1.  Go to **Accounts payable** \> **Payments** \> **Vendor payment journal**.
2.  On the **Vendor payment journal** page, select the payment journal you previously created, and then select **Lines**.
3.  Select the payment line, and then select **Payment status** > **None**.
4.  Select **Generate payments**.
5.  In the **Method of payment** field, select **SEPA CT**.
6.  In the **Bank account** field, select **DEMF OPER**.
7.  On the **Generate payments** dialog page, select **OK**.
8. On the **Electronic report parameters** dialog page, select **OK**.
