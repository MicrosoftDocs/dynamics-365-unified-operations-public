---
title: Microsoft Office-style user interface in Business document management
description: This article explains how to use the new user interface in the Business document management feature of Electronic reporting (ER) framework.
author: kfend
ms.author: johnmichalak
ms.topic: article
ms.date: 12/02/2025
ms.reviewer: johnmichalak 
ms.search.form: ERBDWorkspace, ERBDParameters
audience: Developer, IT Pro
ms.assetid: 
ms.search.region: Global
ms.search.validFrom: 2019-08-01
ms.dyn365.ops.version: 10.0.5
ms.custom:
  - sfi-image-nochange
---

# Microsoft Office-style user interface in Business document management

[!include [banner](../includes/banner.md)]

Business document management lets business users edit business document templates by using a Microsoft Office 365 service or the appropriate Microsoft Office desktop application. Edits might include design changes or new deployments, or users might add placeholders to include more data without having to change the source code. For more information about how to work with Business document management, see [Business document management overview](er-business-document-management.md).

The new user interface (UI) is clearer and easier to use. The **Business document** area shows only the templates that the current [active](tasks/er-configuration-provider-mark-it-active-2016-11.md) [provider](general-electronic-reporting.md#Provider) owns and that are located in the current instance of Dynamics 365 Finance. In the previous UI, the **Template** tab listed all the templates that were available for any provider. It also showed all the templates that any user with the same role created and edited.

Use the **New document** button in the **Business document management** workspace to create and edit a template in an [Electronic reporting (ER)](general-electronic-reporting.md) format [configuration](general-electronic-reporting.md#Configuration) that another provider supplies and that is located in the current Finance instance, or to upload a new template from an Excel workbook. Additionally, in version 10.0.25 and later, you can use the **New document** button to create and edit a template in an ER format configuration that is stored in the [Global repository](general-electronic-reporting.md#Repository).

In the examples in this article, the active provider is Contoso, and you use it to create a template that is based on a template that Microsoft provides. Alternatively, you can create a template by uploading your own template in Excel format.

> [!NOTE]
> In versions of Finance before 10.0.21, you had to explicitly enable Business document management functionality and the Microsoft Office–style UI. However, starting in version 10.0.21, the corresponding **Business document management**, and **Office-like UI experience for Business document management** features are turned on by default. Then, starting in version 10.0.29, these features became mandatory. In other words, they're turned on by default and can't be turned off.
>
> Starting in Finance version 10.0.32, both features are removed. Therefore, if you're using Finance version 10.0.32 and later, disregard the information about feature enablement later in this article.

> [!VIDEO https://learn-video.azurefd.net/vod/player?id=1c11ad8d-0615-4d8e-b3b4-996050800938]

The [Create a new business document using Business document management](https://youtu.be/gAIYl-mM_pw) video (shown earlier) is included in the [finance and operations playlist](https://www.youtube.com/playlist?list=PLcakwueIHoT_SYfIaPGoOhloFoCXiUSyW) available on YouTube.

## Make the new document UI in Business document management available

To start using the new document UI in Business document management, turn on the **Office-like UI experience for Business document management** feature in the **Feature management** workspace.

Follow these steps to turn on this feature for all legal entities.

1. In the **Feature management** workspace, on the **All** tab, select the **Office-like UI experience for Business document management** feature in the list.
1. Select **Enable now** to turn on the selected feature.
1. Refresh the page to access the new feature.

## Add or activate a provider

Each template of a business document is stored in an ER format configuration that is marked as owned by a specific configuration provider. When you create a new template, you also create a new ER format configuration to hold it. Therefore, you must identify a provider for that configuration. The active provider of the ER framework is used for this purpose. If there's no provider in ER, you can create one. If there's no *active* provider, you can activate one of the existing providers. When you start adding a new template, a dialog for adding or activating a provider opens if necessary.

### Add a new provider

To create a new provider, follow these steps on the **Configuration provider** dialog:

1. On the **Choose configuration provider** tab, in the **Name** field, enter the name of the new provider.
1. In the **Internet address** field, enter the internet address (URL) of the new provider. 
1. Select **OK**.

:::image type="content" source="./media/bdm_create_provider.png" alt-text="Screenshot of creating a new provider in Business Document Management.":::

The added provider is automatically activated.

### Activate a provider

To activate a provider, follow these steps on the **Configuration provider** dialog:

1. On the **Choose configuration provider** tab, in the **Configuration provider** field, select the provider.
1. Select **OK**.

:::image type="content" source="./media/bdm_choose_provider.png" alt-text="Screenshot of activating a provider in Business Document Management.":::

The selected provider is activated.

> [!NOTE]
> Each Business document management template is located in an ER format configuration that refers to the provider as configuration author. Therefore, you need an active provider for each template.

## Edit a template that another provider owns

This example shows how to use the **New document** button in the **Business document management** workspace to create and edit a template in an ER format configuration that another provider owns and that is located in the current Finance instance. In this example, the active provider is Contoso, which uses the ER format configuration that Microsoft provides. After you select **New document**, the **Select** tab on the **Create a new template** page shows all the templates of the current Finance instance that the current provider and other providers own. Select a template to open it. You can then create a new editable copy of the template. The edited template is stored in a new ER format configuration that is automatically generated.

1. In the **Business document management** workspace, select **New document**.

:::image type="content" source="./media/BDM_overview_new_template1.png" alt-text="Screenshot of Business document management workspace.":::

1. On the **Create a new template** page, on the **Select** tab, select the document to use as a template, then select **Create document**.

:::image type="content" source="./media/BDM_overview_new_template2.png" alt-text="Screenshot of Business documents dialog box.":::

1. In the new dialog box, in the **Title** field, change the title as you require. The title text is used to name the new ER format configuration that is automatically created. The draft version of this configuration (**Customer FTI report (GER) Copy**) contains the edited template and is used to run this ER format for the current user. The original template from the base ER format configuration is used to run this ER format for every other user.
1. In the **Name** field, change the name of the first revision of the editable template that is automatically created.
1. In the **Comment** field, update the remarks for the revision of the editable template that is automatically created.
1. Select **OK** to confirm the start of the editing process.

:::image type="content" source="./media/BDM_overview_new_template3.png" alt-text="Screenshot of Document creation dialog box.":::

## Upload a template that uses an existing Excel workbook

This example shows how to use the **New document** button in the **Business document management** workspace to create and edit a template in an ER format configuration, based on the available Excel workbook. In this example, the active provider is Contoso, and you use the ER [data model](er-overview-components.md#data-model-component) and ER [model mapping](er-overview-components.md#model-mapping-component) configurations that Microsoft provides. After you select **New document**, select the **Upload** tab on the **Create a new template** page. There, you can specify the details of an Excel workbook upload. After you upload the Excel workbook, the system transforms it into a business document template that you can open for editing. The edited template is stored in a new ER format configuration that the system automatically generates.

Follow these steps to provide the required information before you upload a template.

1. In the **Business document management** workspace, select **New document**.
1. On the **Create a new template** page, on the **Upload** tab, on the **Template** tab, select **Browse** to find and select the Excel file that you want to use as a template. In the **Template** section, the **Title** and **Description** fields are automatically filled in. They specify the name and description of the new ER format configuration that the system automatically creates. You can edit these fields as needed.
1. In the **Document Type** section, in the **Name** field, specify the type of business document. The system uses this value to search the correct data source (that is, the ER model configuration).

:::image type="content" source="./media/BDM_overview_new_UI_import_21.jpg" alt-text="Screenshot of Template tab on the Upload tab of the Create a new template page.":::

1. On the **Data source** tab, on the **Filter** FastTab, select **Apply filter**. In the **Data source** section, the **Name** field is automatically filled in, or you can manually select a value. You can use the filter to search for the appropriate data source name by name, description, country/region code, and business document type.

   :::image type="content" source="./media/BDM_overview_new_UI_import_31.jpg" alt-text="Screenshot of Data source tab on the Upload tab of the Create a new template page.":::

    > [!NOTE]
    > The **Filter** FastTab is used to search the correct data source (that is, the ER model configuration). You can edit all filter fields to find the most appropriate data source for the document that you're uploading.
    > 
    > The conditions on the **Filter** FastTab are used as **OR** conditions.

1. On the **Mapping** tab, select **Auto detect**. The **Root definition** field is automatically filled in, or you can manually select a value. This tab shows the end mapping for the elements from the template and the model.

   :::image type="content" source="./media/BDM_overview_new_UI_import_41.jpg" alt-text="Screenshot of Mapping tab on the Upload tab of the Create a new template page.":::

    > [!NOTE]
    > The mapping in the **Template structure** section uses the full match of the labels or descriptions in the data source in the user's language, and in the cell name in the template.

1. Select **Create document** to confirm that you want to create a template and start the editing process.

For more information, see [Business document management overview](er-business-document-management.md).

## Upload a template from the Global repository

This example shows how to use the **New document** button in the **Business document management** workspace to create and edit a template in an ER format configuration that Microsoft provides and that is located in the Global repository. In this example, the active provider is Contoso, which uses the ER format configuration that Microsoft provides. After you select **New document**, the **Import from Global repository** tab on the **Create a new template** page shows all the business document templates that the Global repository stores but that are missing in the current Finance instance. After you select a template, you import it from the Global repository into the current Finance instance to create a new editable copy. You store the edited template in a new ER format configuration that the system automatically generates.

1. In the **Business document management** workspace, select **New document**.
1. On the **Create a new template** page, on the **Import from Global repository** tab, select the document to use as a template, then select **Create document**.

:::image type="content" source="./media/BDM_overview_new_template22.png" alt-text="Screenshot of Import from Global repository tab on the Create a new template page.":::

1. In the message box, select **Yes** to confirm that you want to import the selected document from the Global repository into the current Finance instance. If you're prompted for authorization, follow the on-screen instructions.
1. In the new dialog box, in the **Title** field, change the title as you require. The title text is used to name the new ER format configuration that the system automatically creates. The draft version of this configuration (**Collection letter note (Excel) Copy**) contains the edited template and is used to run this ER format for the current user. The original template from the base ER format configuration is used to run this ER format for every other user.
1. In the **Name** field, change the name of the first revision of the editable template that is automatically created.
1. In the **Comment** field, update the remarks for the revision of the editable template that is automatically created.
1. Select **OK** to confirm the start of the editing process.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
