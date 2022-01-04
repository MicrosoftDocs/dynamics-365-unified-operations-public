---
# required metadata

title: Microsoft Office-style user interface in Business document management (contains video)
description: This topic explains how to use the new user interface in the Business document management feature of Electronic reporting (ER) framework.
author: v-anamir
ms.date: 04/12/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ERBDWorkspace, ERBDParameters
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: v-anamir
ms.search.validFrom: 2019-08-01
ms.dyn365.ops.version: 10.0.5

---

# Microsoft Office-style user interface in Business document management

[!include [banner](../includes/banner.md)]

Business document management lets business users edit business document templates by using a Microsoft 365 service or the appropriate Microsoft Office desktop application. Edits might include design changes or new deployments, or users might add placeholders to include additional data without having to change the source code. For more information about how to work with Business document management, see [Business document management overview](er-business-document-management.md).

The new user interface (UI) is clearer and more comfortable to use. The **Business document** area shows only the templates that are available for the current provider. In the previous UI, the **Template** tab listed all the templates that were available for any providers. It also showed all the templates that were created and edited by any user who had the same role.

You can use the **New document** button to create and edit a template in an Electronic reporting (ER) format configuration that is provided by another provider. In the example in this topic, the provider is Microsoft. Alternatively, you can create a template by uploading your own template in Excel format.


> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWAVQg]

The [Create a new business document using Business document management](https://youtu.be/gAIYl-mM_pw) video (shown above) is included in the [Finance and Operations playlist](https://www.youtube.com/playlist?list=PLcakwueIHoT_SYfIaPGoOhloFoCXiUSyW) available on YouTube.

## Make the new document UI in Business document management available

To start to use the new document UI in Business document management, you must turn on the **Office-like UI experience for Business document management** feature in the **Feature management** workspace.

Follow these steps to turn on this feature for all legal entities.

1. In the **Feature management** workspace, on the **All** tab, select the **Office-like UI experience for Business document management** feature in the list.
2. Select **Enable now** to turn on the selected feature.
3. Refresh the page to access the new feature.

## Edit templates that are owned by other providers

1. In the **Business document management** workspace, select **New document**.

    ![Business document management workspace.](./media/BDM_overview_new_template1.png)

2. On the **Select** tab, select the document to use as a template, and then select **Create document**.

    ![Business documents dialog box.](./media/BDM_overview_new_template2.png)

3. In the new dialog box, in the **Title** field, change the title as you require. The title text is used to name the new ER format configuration that is automatically created. The draft version of this configuration (**Customer FTI report (GER) Copy**) will contain the edited template and will be used to run this ER format for the current user. The original template from the base ER format configuration will be used to run this ER format for every other user.
4. In the **Name** field, change the name of the first revision of the editable template that will be automatically created.
5. In the **Comment** field, update the remarks for the revision of the editable template that will be automatically created.
6. Select **OK** to confirm the start of the editing process.

    ![Document creation dialog box.](./media/BDM_overview_new_template3.png)

The **New document** button is used to create and edit a template in an ER format configuration that is provided by another provider. In this example, the provider is Microsoft. When you select **New document**, you can view all the templates that are owned by current and other providers. After you select the template, it's opened for editing. The edited template will then be stored in a new ER format configuration that is automatically generated.

## Upload a template that uses an existing Excel format
Follow these steps to provide required information before you upload a template.

1. In the **Business document management** workspace, select **New document**.

    ![Business document management workspace.](./media/BDM_overview_new_template1.png)
    
2. On the **Create a new template** page, on the **Upload** tab, on the **Template** tab, select **Browse** to find and select the Excel file that you want to use as a template. In the **Template** section, the **Title** and **Description** fields are automatically filled in. They specify the name and description of the new ER format configuration that is automatically created. You can edit these fields as you require.
3. In the **Document Type** section, in the **Name** field, specify the type of business document. This value will be used to search the correct data source (that is, the ER model configuration).

    ![Template tab.](./media/BDM_overview_new_UI_import_21.jpg)

4. On the **Data source** tab, on the **Filter** FastTab, select **Apply filter**. In the **Data source** section, the **Name** field is automatically filled in, or you can manually select a value. You can use the filter to search for the appropriate data source name by name, description, country/region code, and business document type.

    ![Data source tab.](./media/BDM_overview_new_UI_import_31.jpg)
    
    > [!NOTE]
    > The **Filter** FastTab is used to search the correct data source (that is, the ER model configuration). You can edit all filter fields to find the most appropriate data source for the document that you're uploading.
    > 
    > The conditions on the **Filter** FastTab are used as **OR** conditions.
    
5. On the **Mapping** tab, select **Auto detect**. The **Root definition** field is automatically filled in, or you can manually select a value. This tab shows the end mapping for the elements from the template and the model.

    ![Mapping tab.](./media/BDM_overview_new_UI_import_41.jpg)
    
   > [!NOTE]
   > The mapping in the **Template structure** section uses the full match of the labels or descriptions in the data source in the user's language, and in the cell name in the template.

6. Select **Create document** to confirm that you want to create a template and start the editing process.

For more information, see [Business document management overview](er-business-document-management.md).

If there isn't a provider in Electronic reporting, you can create one. If there's no active provider, you can select to activate one.

- To create a provider, change the name of the provider in the **Name** field, update the internet address of the new provider in the **Internet address** field, and select **OK** to confirm.

    ![Create new provider in BDM.](./media/bdm_create_provider.png)
    
- To activate existing provider, choose the name of the provider in the **Configuration provider** field, and select **OK** to set provider as active.

    ![Activate provider in BDM.](./media/bdm_choose_provider.png)

> [!NOTE]
> Each BDM template refers to the provider as the author of the configuration. This is why an active provider is required for the template.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
