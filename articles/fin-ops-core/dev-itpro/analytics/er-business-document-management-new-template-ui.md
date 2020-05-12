---
# required metadata

title: New document user interface in Business document management
description: This topic provides information about how to use the new document user interface (UI) in the Business document management feature of the Electronic reporting (ER) framework.
author: v-anamir
manager: AnnBe
ms.date: 05/12/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: ERBDWorkspace, ERBDParameters
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
ms.author: v-anamir
ms.search.validFrom: 2019-08-01
ms.dyn365.ops.version: 10.0.5

---

# New document user interface in Business document management

[!include [banner](../includes/banner.md)]

Business document management lets business users edit business document templates by using a Microsoft Office 365 service or the appropriate Microsoft Office desktop application. Edits might include design changes or new deployments, or users might add placeholders to include additional data without having to change the source code. For more information about how to work with Business document management, see [Business document management overview](er-business-document-management.md).

The new document user interface (UI) is clearer and more comfortable to use. The **Business document** area shows only the templates that are available for the current provider.

The **New document** button lets users create and edit a template in an Electronic reporting (ER) format configuration that is provided by another provider. In the example in this topic, the provider is Microsoft.

## Make the new document UI in Business document management available

To start to use the new document UI in Business document management, you must turn on the **Office-like UI experience for Business document management** feature in the **Feature management** workspace.

Follow these steps to turn on this feature for all legal entities.

1. In the **Feature management** workspace, on the **New** tab, select the **Office-like UI experience for Business document management** feature in the list.
2. Select **Enable now** to turn on the selected feature.
3. Refresh the page to access the new feature.

### Edit templates that are owned by other providers

1. In the **Business document management** workspace, select **New document**.

    ![Business document management workspace](./media/BDM_overview_new_template1.png)

2. In the dialog box, select the document to use as a template, and then select **Create document**.

    ![Business documents dialog box](./media/BDM_overview_new_template2.png)

3. In the new dialog box, in the **Title** field, change the title as you require. The title text is used to name the new ER format configuration that is automatically created. The draft version of this configuration (**Customer FTI report (GER) Copy**) will contain the edited template and will be used to run this ER format for the current user. The original template from the base ER format configuration will be used to run this ER format for every other user.
4. In the **Name** field, change the name of the first revision of the editable template that will be automatically created.
5. In the **Comment** field, update the remarks for the revision of the editable template that will be automatically created.
6. Select **OK** to confirm the start of the editing process.

    ![Document creation dialog box](./media/BDM_overview_new_template3.png)

The **New document** button is used to create and edit a template in an ER format configuration that is provided by another provider. In this example, the provider is Microsoft. When you select **New document**, you can view all the templates that are owned by current and other providers. After you select the template, it's opened for editing. The edited template will then be stored in a new ER format configuration that is automatically generated.

For more information, see [Business document management overview](er-business-document-management.md).
