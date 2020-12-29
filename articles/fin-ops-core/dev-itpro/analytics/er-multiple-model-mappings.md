--- 
# required metadata 
 
title: Manage several derived mappings for a single model root
description: The following steps explain how a user in either the System administrator or Electronic reporting developer role can manage  several derived mappings that were configured for a single model root. 
author: NickSelin
manager: AnnBe 
ms.date: 12/26/2020
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: ERSolutionTable, ERModelMappingTable   
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

# Manage several derived mappings for a single model root

[!include [banner](../includes/banner.md)]

An [Electronic reporting (ER)](general-electronic-reporting.md) data [model](general-electronic-reporting.md#data-model-and-model-mapping-components) component is used in every configured ER [format](general-electronic-reporting.md#FormatComponentOutbound) component as the source of data to generate outbound documents. To describe a single business domain, you can configure a data model component as having many root definitions. Every root definition allows you to represent data of this
domain in a particular way that suites most for certain reporting purposes. To describe how your data model is filled in at runtime, you can configure an ER [model mapping](general-electronic-reporting.md#data-model-and-model-mapping-components) component for every root definition as the Microsoft Dynamics 365 Finance specific implementation of your data model.

ER model mapping components may reside in ER data model [configurations](general-electronic-reporting.md#Configuration) and ER model mapping configurations. Note that a single ER configuration may hold many mapping components each of which is configured for a single root
definition. At the same time, a single ER configuration may hold the only one mapping component that is configured for a single root definition.

So, many configuration providers might offer ER model mapping configurations for the same ER data model that might contain mapping components for different root definitions. You might decide to use a model mapping for one root definition that is offered by one
[provider](general-electronic-reporting.md#Provider) and simultaneously use a model mapping for another root definition that is
offered by another provider.

The procedures in this topic explain how a user assigned to the System administrator or Electronic reporting developer role can manage multiple ER model mapping configurations of an ER data model when they contain different model mapping components that have been configured for the same root definition.

All the following procedures can be done in the USMF company. No coding is required.

## Configure the ER framework

As a user in the Electronic reporting developer role, you must [configure the minimal
set](er-quick-start2-customize-report.md#ConfigureFramework) of ER parameters before you can start using the ER framework to generate
business documents.

## Import the standard ER format configurations

To add the standard ER configurations to your current instance of Microsoft Dynamics 365 Finance, you must import them from the ER repository that was configured for that instance. Complete the steps of the [Download ER configurations from the Global repository of Configuration service](er-download-configurations-global-repo.md) procedure to import the following ER format configurations:

-   **Free text invoice (Excel)** version 220.106
-   **Project invoice (Excel)** version 226.27

## Review the imported ER configurations

1.  Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**.
2.  On the **Configurations** page, in the **Configurations** section, select the **Reporting configurations** tile.
3.  In the configuration tree in the left pane, expand **Invoice model**.

    ![Reviewing the imported configurations on the Configurations page](./media/er-multiple-model-mappings-image1.png)
4.  Review the **Free text invoice (Excel)** format:
    +   In the configuration tree in the left pane, select **Free text invoice (Excel)**.
    +   On the Action Pane, select **Designer**.
    +   On the **Format designer** page, select the **Mapping** tab.
    +   On the **Mapping** tab, in the data sources list, select **Model**.
    +   Select **View**.
        > [!TIP]
        > Notice that the current ER format is configured to use the **InvoiceCustomer** root definition of the **Invoice model**. Therefore, when this format is executed and the **Model** data source is called, the configured for the **InvoiceCustomer** root definition model mapping is used to access application data and fill in the data model.

    ![Reviewing the model data source on the Format designer page](./media/er-multiple-model-mappings-image2.png)
    +   Close the **Format designer** page.
5.  Review the content of the **Invoice model mapping** configuration:
    +   In the configuration tree in the left pane, select **Invoice model mapping**.
    +   On the Action Pane, select **Designer**.
        > [!TIP]
        > Notice that the current ER model mapping configuration contains several model mapping components.
        > + The **Customer Invoice** model mapping is configured for the **InvoiceCustomer** root definition of the **Invoice model**. Therefore, when the **Free text invoice (Excel)** ER format is executed, the **Customer Invoice** model mapping of this ER configuration can be chosen to access application data and fill in the data model.
        > + The **Project Invoice** model mapping is configured for the **InvoiceProject** root definition of the **Invoice model**. Therefore, when the **Project invoice (Excel)** ER format is executed, the **Project Invoice** model mapping of this ER configuration can be chosen to access application data and fill in the data model.

        ![Reviewing the model mappings on the Model to datasource mapping page](./media/er-multiple-model-mappings-image3.png)
    +   Close the **Model to datasource mapping** page.
    +   On the **Versions** FastTab, select **Delete** to delete all versions of this ER configuration that are higher than 240.175.
6.  Review the content of the **Project invoice model mapping (RDP)** configuration:
    +   In the configuration tree in the left pane, select **Project invoice model mapping (RDP)**.
    +   On the Action Pane, select **Designer**.
        > [!TIP]
        > Notice that the current ER model mapping configuration contains the **InvoiceProject** model mapping that is configured for the **InvoiceProject** root definition of the **Invoice model**. Therefore, when the **Project invoice (Excel)** ER format is executed, the **InvoiceProject** model mapping of this ER configuration can be chosen to access application data and fill in the data model.

        ![Reviewing the model mappings on the Model to datasource mapping page](./media/er-multiple-model-mappings-image4.png)
    +   Close the **Model to datasource mapping** page.
    +   On the **Versions** FastTab, select **Delete** to delete all versions of this ER configuration that are higher than 226.35.

## Customize the imported ER configurations

Assume that you need to [customize](er-quick-start3-customize-report.md#customize-the-model-mapping-configuration) the provided by Microsoft model mappings to implement your custom logic, add missing bindings, etc.

### Customize the 'Invoice model mapping' configuration

1.  On the **Configurations** page, in the configuration tree in the left pane, select **Invoice model mapping**.
2.  On the Action Pane, select **Create configuration**.
3.  In the **New** field, select **Derive from Name: Invoice model mapping, Microsoft**.
4.  In the **Name** field, enter **Invoice model mapping Litware**.
5.  In the **Create configuration** dialog box, select **Create configuration**.
6.  [Mark](er-quick-start2-customize-report.md#MarkFormatRunnable) the [draft](general-electronic-reporting.md#component-versioning) version of the derived mapping as available for usage at runtime:
    +   On the Action Pane, on the **Configurations** tab, in the **Advanced settings** group, select **User parameters**.
    +   In the **User parameters** dialog box, set the **Run settings** option to **Yes**, and then select **OK**.
    +   Select **Edit** to make the current page editable, as required.
    +   For the currently selected in the configuration tree **Invoice model mapping Litware** configuration, set the **Run Draft** option to **Yes**.
7.  On the Action Pane, select **Designer** to review model mappings of this configuration.

    ![Reviewing the model mappings on the Model to datasource mapping page](./media/er-multiple-model-mappings-image5.png)
    > [!TIP]
    > You can now open any of the ER model mapping components of this ER configuration in the designer to configure your custom logic. For more, see [Customize the model mapping configuration](er-quick-start3-customize-report.md#customize-the-model-mapping-configuration).
8.  Close the **Model to datasource mapping** page.
    > [!NOTE]
    > Notice that currently you have **Invoice model mapping** and **Invoice model mapping Litware** configurations in every of which you have a model mapping that is configured for the **InvoiceCustomer** root definition. You must explicitly assign one as a default for usage by any of ER formats like the **Free text invoice (Excel)** one that contains a model data source with the **InvoiceCustomer** root definition. Otherwise, when you run such an ER format, try to start editing or validate it, the exception will be thrown informing that none of model mappings was explicitly assigned for usage: *More than one model mapping exists for the `model name (root descriptor)` data model in the configurations `configuration names separated by comma`. Set one of the configurations as default*.
    ![Opening the format for editing on the Configurations page](./media/er-multiple-model-mappings-image6.gif)

### Customize the 'Project invoice model mapping (RDP)' configuration

1.  On the **Configurations** page, in the configuration tree in the left pane, select **Project invoice model mapping (RDP)**.
2.  On the Action Pane, select **Create configuration**.
3.  In the **New** field, select **Derive from Name: Project invoice model mapping (RDP), Microsoft**.
4.  In the **Name** field, enter **Project invoice model mapping Litware**.
5.  In the **Create configuration** dialog box, select **Create configuration**.
6.  For the currently selected in the configuration tree **Project invoice model mapping Litware** configuration, set the **Run Draft** option to **Yes**.
7.  On the Action Pane, select **Designer** to review model mappings of this configuration.

    ![Reviewing the model mappings on the Model to datasource mapping page](./media/er-multiple-model-mappings-image7.png)
8.  Close the **Model to datasource mapping** page.
    > [!NOTE]
    > Notice that currently you have **Invoice model mapping**, **Project invoice model mapping (RDP)**, and **Project invoice model mapping Litware** configurations in every of which you have a model mapping that is configured for the **InvoiceProject** root definition. You must explicitly assign one as a default for usage by any of ER formats like the **Project invoice (Excel)** one that contains a model data source with the **InvoiceProject** root definition. Otherwise, when you run such an ER format or try to start editing it, an exception will be thrown informing that none of the default model mapping assigned.

## Select the derived 'Invoice model mapping Litware' configuration as the one that contains model mappings for default usage

1.  On the **Configurations** page, in the configuration tree in the left pane, select **Invoice model mapping Litware**.
2.  For the selected configuration, set the **Default for model mapping** option to **Yes**.

    ![Set the model mapping as the default on the Configurations page](./media/er-multiple-model-mappings-image8.png)
    > [!NOTE]
    > Based on this setting, the **Customer Invoice Copy** model mapping from the **Invoice model mapping Litware** configuration will be used when you run the **Free text invoice (Excel)** or when you start editing or validating it. The **Customer invoice** model mapping from the **Invoice model mapping** configuration will be ignored. Now you can open the **Free text invoice (Excel)** format for reviewing in the format designer.

## Select the derived 'Project invoice model mapping Litware' configuration as the one that contains model mappings for default usage

1.  On the **Configurations** page, in the configuration tree in the left pane, select **Project invoice model mapping Litware**.
2.  For the selected configuration, set the **Default for model mapping** option to **Yes**.
    > [!IMPORTANT]
    > Unlike the case with the **Invoice model mapping Litware** configuration, it is not enough to start using the **InvoiceProject Copy** model mapping from the **Project invoice model mapping Litware** configuration as two configurations that contain a model mapping for the **InvoiceProject** root definition are currently marked as default which means that they both have the equal priority for usage. To resolve this issue, complete the steps of the current sub-task.
3.  On the **Configurations** page, in the configuration tree in the left pane, select **Invoice model mapping Litware**.
4.  On the Action Pane, select **Designer** to open the **Model to datasource mapping** page.
5.  Select **Edit** to make the current page editable, as required.
6.  Select the **Project Invoice Copy** model mapping and check **Is deleted** the option for it.

    ![Set the model mapping as the virtually deleted on the Model to datasource mapping page](./media/er-multiple-model-mappings-image9.png)
    > [!NOTE]
    > Based on this setting, the **Invoice model mapping Litware** configuration will be considered as having no model mapping for the **InvoiceProject** root definition. Therefore, the **InvoiceProject Copy** model mapping will be used by default as the holding this model mapping **Project invoice model mapping Litware** configuration is marked as default and, consequently, has higher priority than the **InvoiceProject** model mapping from the **Project invoice model mapping (RDP)** configuration.

## Other considerations

Notice that the **InvoiceProject Copy** model mapping of the **Project invoice model mapping Litware** configuration is designed to use the `ReportDataProvider` data source of the *Object* type that refers to the `PsaProjInvoiceDP` application class. This class is implemented as the data provider for the project invoice SSRS report of the Print management framework. You can select this data source as the ER [integration point](er-apis-app10-0-11.md#api-to-run-a-format-mapping-for-the-generation-of-outbound-documents). The current ER implementation for Print management reports takes this setting into account - review the source code of the `ERPrintMgmtDataProviderReport` application class for more details. So, the assignment of the `ReportDataProvider` data source as the model mapping integration point will force Finance application to consider this mapping component at runtime as having the higher priority than the **InvoiceProject** mapping component from the **Project invoice model mapping (RDP)** configuration for which the integration point was not configured.

## Additional resources

- [Manage ER model mapping in separate ER configurations](./tasks/er-manage-model-mapping-configurations-july-2017.md)
- [Configure country context dependent ER model mappings](er-country-dependent-model-mapping.md)
- [Electronic reporting framework API changes](er-apis-app10-0-11.md)
