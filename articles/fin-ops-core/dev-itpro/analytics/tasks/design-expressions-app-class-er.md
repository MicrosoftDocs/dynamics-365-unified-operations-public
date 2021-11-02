--- 
# required metadata 
 
title: Design ER expressions to call application class methods
description: This topic describes how to reuse the existing application logic in Electronic reporting configurations by calling required methods of application classes. 
author: NickSelin
ms.date: 12/12/2017
ms.topic: business-process 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 

---
# Design ER expressions to call application class methods

[!include [banner](../../includes/banner.md)]

This guide provides information about how to reuse the existing application logic in [Electronic reporting (ER)](../general-electronic-reporting.md) configurations by calling required methods of application classes in ER expressions. Values of arguments for calling classes can be defined dynamically at run-time: for example, based on information in the parsing document to ensure its correctness. In this guide, you will create the required ER configurations for the sample company, Litware, Inc. This procedure is created for users with the assigned role of System administrator or Electronic reporting developer. 

These steps can be completed using any data set. You must also download and save the file, [SampleIncomingMessage.txt](https://download.microsoft.com/download/8/0/a/80adbc89-f23c-46d9-9241-e0f19125c04b/SampleIncomingMessage.txt).

To complete these steps, you must first complete the steps in the [Create configuration providers and mark them as active](er-configuration-provider-mark-it-active-2016-11.md) procedure.

1. Go to **Organization administration \> Workspaces \> Electronic reporting** to open the **Localization configurations** page.
    * Verify that the configuration provider for sample company, Litware, Inc. is available and marked as active. If you don't see this configuration provider, you must first complete the steps in the procedure, **Create configuration providers and mark them as active**.   
    * You are designing a process for parsing incoming bank statements for an application data update. You will receive the incoming bank statements as TXT files that contain IBAN codes. As part of the bank statement import process, you need to validate the correctness of this IBAN codes using the logic that is already available.   

## Import a new ER model configuration

1. On the **Localization configurations** page, in the **Configuration providers** section, select the **Microsoft** provider tile.
2. Select **Repositories**.
3. On the **Localization repositories** page, select **Show filters**.
4. To select the Global repository record, do the following:
    1. Add a filter field **Name**.
    2. In the **Name** field, enter the value "Global" and select the "contains" filter operator.
    3. Select **Apply**.
5. Select **[Open](../er-download-configurations-global-repo.md#open-configurations-repository)** to review the list of ER configurations in the selected repository.
6. On the **Configuration repository** page, in the configurations tree, select **Payment model**.
    * If the **Import** button on the **Versions** FastTab is enabled, select **Import**, and select **Yes**. Otherwise, you have already imported the selected version of the ER configuration **Payment model**.
7. Close the **Configuration repository** page.
8. Close the **Localization repositories** page.

## Add a new ER format configuration

Add a new ER format to parse incoming bank statements in TXT format.  

1. On the **Localization configurations** page, select the **Reporting configurations** tile.
2. On the **Configurations** page, in the configurations tree in the left pane, select **Payment model**.
3. Select **Create configuration** to open a new configuration entry dialog.
    1. In the **New** field, enter **Format based on data model PaymentModel**.
    2. In the **Name** field, type **Bank statement import format (sample)**.
    3. Select **Yes** in the **Supports data import** field.
    4. Select **Create configuration** to confirm a new configuration entry.

## Design the ER format configuration - format

Design an ER format that represents the expected structure of the external file in TXT format.  

1. For the added **Bank statement import format (sample)** format configuration, select **Designer**.
2. On the **Format designer** page, in the format structure tree in the left pane, select **Add root** to open a new component entry dialog.
3. In the tree, select **Text\Sequence** to add a **Sequence** format component.
    1. In the **Name** field, type **Root**.
    2. In the **Special characters** field, select **New line - Windows (CR LF)**. Based on this setting, each line in the parsing file is considered as a separate record.
    3. Select **OK**.
4. Select **Add** to open a new component entry dialog.
5. In the tree, select **Text\Sequence**.
    1. In the **Name** field, type **Rows**.
    2. In the **Multiplicity** field, select **One many**. Based on this setting, it is expected that at least one line will be presented in the parsing file.  
    3. Select **OK**.
6. In the tree, select **Root\Rows**.
7. Select **Add Sequence**.
    1. In the **Name** field, type **Fields**.
    2. In the **Multiplicity** field, select **Exactly one**.
    3. Select **OK**.
8. In the tree, select **Root\Rows\Fields**.
9. Select **Add** to open a new component entry dialog.
10. In the tree, select **Text\String**.
    1. In the **Name** field, type **IBAN**.
    2. Select **OK**.     
11. Select **Save**.

It has been configured that each line in the parsing file contains the only IBAN code.

![Format designer page.](../media/design-expressions-app-class-er-01.png)

## Design the ER format configuration – mapping to data model

Design an ER format mapping to use information from the parsing file for filling in a data model.  

1. On the **Format designer** page, on the Action Pane, select **Map format to model**.
2. On the **Model to datasource mapping** page, on the Action Pane, select **New**.
    1. In the **Definition** field, select **BankToCustomerDebitCreditNotificationInitiation**.
    2. In the **Name** field, type **Mapping to data model**.
    3. Select **Save**.
3. Select **Designer**.
4. On the **Model mapping designer** page, in the **Data source types** tree, select **Dynamics 365 for Operations\Class**.
5. In the **Data sources** section, select **Add root** to add a new data source to call the existing application logic for IBAN codes validation.  
    1. In the **Name** field, type **Check_codes**.
    2. In the **Class** field, type or select **ISO7064**.
    3. Select **OK**.
6. In the **Data source types** tree, do the following:
    1. Expand the data source **format**.
    2. Expand **format\Root: Sequence(Root)**.
    3. Expand **format\Root: Sequence(Root)\Rows: Sequence 1..\* (Rows)**.
    4. Expand **format\Root: Sequence(Root)\Rows: Sequence 1..\* (Rows)\Fields: Sequence 1..1 (Fields)**.
7. In the **Data model** tree, do the following:
    1. Expand the **Payments** field of the data model.
    2. Expand **Payments\Creditor Account(CreditorAccount)**.
    3. Expand **Payments\Creditor Account(CreditorAccount)\Identification**.
    4. Expand **Payments\Creditor Account(CreditorAccount)\Identification\IBAN**.
8. Bind components of the configured format to data model fields:
    1. Select **format\Root: Sequence(Root)\Rows: Sequence 1..\* (Rows)**.
    2. Select **Payments**.
    3. Select **Bind**.
    > Based on this setting, each line in the parsing file is considered as a single payment.
    4. Select **format\Root: Sequence(Root)\Rows: Sequence 1..\* (Rows)\Fields: Sequence 1..1 (Fields)\IBAN: String(IBAN)**.
    5. Select **Payments\Creditor Account(CreditorAccount)\Identification\IBAN**'.
    6. Select **Bind**.
    > Based on this setting, the IBAN field of the data model is filled in by the value from the parsing file.

    ![Model mapping designer page.](../media/design-expressions-app-class-er-02.png)

9. Select the **Validations** tab to add a new [validation](../general-electronic-reporting-formula-designer.md#Validation) rule that displays an error for any line in the parsing file that contains invalid IBAN code.  
    1. Select **New**.
        1. Select **Edit condition**.
        2. On the **Formula designer** page, in the **Data source** tree, expand the **Check_codes** data source that represents the `ISO7064` application class to see available methods of this class.
        3. Select **Check_codes\verifyMOD1271_36**.
        4. Select **Add data source**.
        5. In the **Formula** field, enter the following [expression](../general-electronic-reporting-formula-designer.md#Binding): `Check_codes.verifyMOD1271_36(format.Root.Rows.Fields.IBAN)`.
        6. Select **Save**.
        7. Close the page.
    2. Select **Edit message**.
        1. On the **Formula designer** page, in the **Formula** field, enter **CONCATENATE("Invalid IBAN code has been found:  ", format.Root.Rows.Fields.IBAN)**.
        2. Select **Save**.
        3. Close the page.
    > Based on this setting, the validation condition returns *[FALSE](../er-formula-supported-data-types-primitive.md#boolean)* for any invalid IBAN code by calling the existing method `verifyMOD1271_36` of the application class `ISO7064`. Note that the value of the IBAN code is defined dynamically at run-time as the argument of the calling method based on the content of the parsing TXT file.

    ![Model mapping designer page.](../media/design-expressions-app-class-er-03.png)

10. Select **Save**.
11. Close the **Model mapping designer** page.
12. Close the **Model to datasource mapping** page.

## Run the format mapping

For testing purposes, execute the format mapping using the **SampleIncomingMessage.txt** file that you downloaded. The generated output includes data that will be imported from the selected TXT file and populated to the custom data model during the real import.

1.  On the **Model to datasource mapping** page, select **Run**.
2.  On the **Electronic report parameters** page, select **Browse** and navigate to the **SampleIncomingMessage.txt** file that you previously downloaded.  
3.  Select **OK**.

    ![Model mapping designer page.](../media/design-expressions-app-class-er-04.png)
    
    > Review the output in XML format that represents the data that has been imported from the selected file and ported to the data model. Note that only 3 lines of the imported TXT file were processed without errors. The IBAN code on line 4 that is not valid was skipped and an error message is provided in the Infolog.

    ![Model mapping designer page.](../media/design-expressions-app-class-er-05.png)


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
