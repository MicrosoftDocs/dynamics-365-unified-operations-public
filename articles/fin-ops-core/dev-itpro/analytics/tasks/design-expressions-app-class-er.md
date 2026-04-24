---
title: Design ER expressions to call application class methods
description: This article describes how to reuse the existing application logic in Electronic reporting configurations by calling required methods of application classes.
author: kfend
ms.date: 04/10/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
---

# Design ER expressions to call application class methods

[!include [banner](../../includes/banner.md)]

This article describes how to reuse existing application logic in [Electronic reporting (ER)](../general-electronic-reporting.md) configurations by calling required methods of application classes in ER expressions. You can dynamically define values of arguments for calling classes at runtime. For example, you can base values on information in the parsing document to ensure its correctness.

For the example in this article, you design a process that parses incoming bank statements for an application data update. You receive the incoming bank statements as text (.txt) files that contain International Bank Account Number (IBAN) codes. As part of the process of importing the bank statements, you must validate the correctness of the IBAN code by using the logic that's already available.

## Prerequisites

The procedures in this article are intended for users who are assigned the **System administrator** or **Electronic reporting developer** role.

You can complete the procedures by using any data set.

To complete the procedures, you must download and save the following file: [SampleIncomingMessage.txt](https://download.microsoft.com/download/8/0/a/80adbc89-f23c-46d9-9241-e0f19125c04b/SampleIncomingMessage.txt).

In this article, you will create the required ER configurations for the Litware, Inc. sample company. Therefore, before you complete the procedures in this article, you must follow these steps:

1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**.
1. On the **Localization configurations** page, verify that the configuration provider for the **Litware, Inc.** sample company is available and marked as active. If you don't see this configuration provider, you must first complete the steps in [Create configuration providers and mark them as active](er-configuration-provider-mark-it-active-2016-11.md).

## Import a new ER model configuration

1. On **Localization configurations**, in the **Configuration providers** section, select the tile for the **Microsoft** configuration provider.
1. Select **Repositories**.
1. On **Localization repositories**, select **Show filters**.
1. To select the Global repository record, add a **Name** filter field.
1. In the **Name** field, enter **Global**. Then select the **contains** filter operator.
1. Select **Apply**.
1. Select **[Open](../er-download-configurations-global-repo.md#open-configurations-repository)** to review the list of ER configurations in the selected repository.
1. On **Configuration repository**, in the configuration tree, select **Payment model**.
1. On the **Versions** FastTab, if the **Import** button is available, select it, and then select **Yes**.

    If the **Import** button isn't available, you already imported the selected version of the **Payment model** ER configuration.

1. Close **Configuration repository**, and then close **Localization repositories**.

## Add a new ER format configuration

Add a new ER format to parse incoming bank statements in TXT format.

1. On **Localization configurations**, select the **Reporting configurations** tile.
1. On **Configurations**, in the configuration tree in the left pane, select **Payment model**.
1. Select **Create configuration**. 
1. In the drop-down dialog box, follow these steps:

    1. In the **New** field, enter **Format based on data model PaymentModel**.
    1. In the **Name** field, enter **Bank statement import format (sample)**.
    1. In the **Supports data import** field, select **Yes**.
    1. Select **Create configuration** to finish creating the configuration.

## Design the ER format configuration – Format

Design an ER format that represents the expected structure of the external file in TXT format.

1. For the **Bank statement import format (sample)** format configuration that you added, select **Designer**.
1. On the **Format designer** page, in the format structure tree in the left pane, select **Add root**.
1. In the dialog box that appears, follow these steps:

    1. In the tree, select **Text\\Sequence** to add a **Sequence** format component.
    1. In the **Name** field, enter **Root**.
    1. In the **Special characters** field, select **New line - Windows (CR LF)**. Based on this setting, each line in the parsing file is a separate record.
    1. Select **OK**.

1. Select **Add**.
1. In the dialog box that appears, follow these steps:

    1. In the tree, select **Text\\Sequence**.
    1. In the **Name** field, enter **Rows**.
    1. In the **Multiplicity** field, select **One many**. Based on this setting, the parsing file contains at least one line.
    1. Select **OK**.

1. In the tree, select **Root\\Rows**, and then select **Add Sequence**.
1. In the dialog box that appears, follow these steps:

    1. In the **Name** field, enter **Fields**.
    1. In the **Multiplicity** field, select **Exactly one**.
    1. Select **OK**.

1. In the tree, select **Root\\Rows\\Fields**, and then select **Add**.
1. In the dialog box that appears, follow these steps:

    1. In the tree, select **Text\\String**.
    1. In the **Name** field, enter **IBAN**.
    1. Select **OK**.

1. Select **Save**.

The configuration is now set up so that each line in the parsing file contains only the IBAN code.

:::image type="content" source="../media/design-expressions-app-class-er-01.png" alt-text="Screenshot of the Bank statement import format (sample) format configuration on the Format designer page.":::

## Design the ER format configuration – Mapping to a data model

Design an ER format mapping that uses information from the parsing file to fill in a data model.

1. On the **Format designer** page, on the Action Pane, select **Map format to model**.
1. On the **Model to datasource mapping** page, on the Action Pane, select **New**.
1. In the **Definition** field, select **BankToCustomerDebitCreditNotificationInitiation**.
1. In the **Name** field, enter **Mapping to data model**.
1. Select **Save**.
1. Select **Designer**.
1. On the **Model mapping designer** page, in the **Data source types** tree, select **Dynamics 365 for Operations\\Class**.
1. In the **Data sources** section, select **Add root** to add a data source that calls the existing application logic for IBAN codes validation.
1. In the dialog box that appears, follow these steps:

    1. In the **Name** field, enter **Check\_codes**.
    1. In the **Class** field, enter or select **ISO7064**.
    1. Select **OK**.

1. In the **Data source types** tree, follow these steps:

    1. Expand the **format** data source.
    1. Expand **format\\Root: Sequence(Root)**.
    1. Expand **format\\Root: Sequence(Root)\\Rows: Sequence 1..\* (Rows)**.
    1. Expand **format\\Root: Sequence(Root)\\Rows: Sequence 1..\* (Rows)\\Fields: Sequence 1..1 (Fields)**.

1. In the **Data model** tree, follow these steps:

    1. Expand the **Payments** field of the data model.
    1. Expand **Payments\\Creditor Account(CreditorAccount)**.
    1. Expand **Payments\\Creditor Account(CreditorAccount)\\Identification**.
    1. Expand **Payments\\Creditor Account(CreditorAccount)\\Identification\\IBAN**.

1. Follow these steps to bind components of the configured format to data model fields:

    1. Select **format\\Root: Sequence(Root)\\Rows: Sequence 1..\* (Rows)**.
    1. Select **Payments**.
    1. Select **Bind**. Based on this setting, each line in the parsing file is a single payment.
    1. Select **format\\Root: Sequence(Root)\\Rows: Sequence 1..\* (Rows)\\Fields: Sequence 1..1 (Fields)\\IBAN: String(IBAN)**.
    1. Select **Payments\\Creditor Account(CreditorAccount)\\Identification\\IBAN**.
    1. Select **Bind**. Based on this setting, the **IBAN** field of the data model is filled with the value from the parsing file.

    :::image type="content" source="../media/design-expressions-app-class-er-02.png" alt-text="Screenshot of binding of format components to data model fields on the Model mapping designer page.":::

1. On the **Validations** tab, follow these steps to add a [validation](../general-electronic-reporting-formula-designer.md#Validation) rule that shows an error message for any line in the parsing file that contains an invalid IBAN code:

    1. Select **New**, and then select **Edit condition**.
    1. On the **Formula designer** page, in the **Data source** tree, expand the **Check\_codes** data source that represents the **ISO7064** application class to view the available methods of this class.
    1. Select **Check\_codes\\verifyMOD1271\_36**.
    1. Select **Add data source**.
    1. In the **Formula** field, enter the following [expression](../general-electronic-reporting-formula-designer.md#Binding): **Check\_codes.verifyMOD1271\_36(format.Root.Rows.Fields.IBAN)**.
    1. Select **Save**, and then close the page.
    1. Select **Edit message**.
    1. On the **Formula designer** page, in the **Formula** field, enter **CONCATENATE("Invalid IBAN code has been found:&nbsp;", format.Root.Rows.Fields.IBAN)**.
    1. Select **Save**, and then close the page.

    Based on these settings, the validation condition returns *[FALSE](../er-formula-supported-data-types-primitive.md#boolean)* for any invalid IBAN code by calling the existing **verifyMOD1271\_36** method of the **ISO7064** application class. The value of the IBAN code is dynamically defined at runtime as the argument of the calling method, based on the content of the parsing text file.

    :::image type="content" source="../media/design-expressions-app-class-er-03.png" alt-text="Screenshot of the validation rule on the Model mapping designer page.":::

1. Select **Save**.
1. Close the **Model mapping designer** page, and then close the **Model to datasource mapping** page.

## Run the format mapping

For testing purposes, run the format mapping by using the SampleIncomingMessage.txt file that you downloaded earlier. The generated output includes data that the process imports from the selected text file and ports to the custom data model during the real import.

1. On **Model to datasource mapping**, select **Run**.
1. On **Electronic report parameters**, select **Browse**, browse to the **SampleIncomingMessage.txt** file that you downloaded, and select it.
1. Select **OK**.
1. The **Model to datasource mapping** page shows an error message about an invalid IBAN code.

    :::image type="content" source="../media/design-expressions-app-class-er-04.png" alt-text="Screenshot of the result of running the format mapping on the Model to datasource mapping page.":::

1. Review the output in XML format that represents the data imported from the selected file and ported to the data model. Notice that the process handles only three lines of the imported text file without errors. The IBAN code on line 4 isn't valid and is skipped.

    :::image type="content" source="../media/design-expressions-app-class-er-05.png" alt-text="Screenshot of the XML output.":::

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
