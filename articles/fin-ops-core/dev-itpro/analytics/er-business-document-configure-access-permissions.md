---
title: Configure access permissions
description: Learn about how to manage access permissions to edit templates for configurable business documents
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.date: 08/06/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2024-07-15
ms.search.form: ERBDWorkspace, ERBDParameters, ERSecurityAccessEditor
ms.dyn365.ops.version: 10.0.5
ms.assetid: 
---

# Manage access permissions to edit templates for configurable business documents

[!include[banner](../includes/banner.md)]

By default, when you don't enable access to **Business document management** permissions, every user with access to the **Business document management** workspace sees all of the ER solution templates that are available. The **Business document management** workspace shows only those templates that reside in ER format configurations and that are marked by a **Business document type** tag.

:::image type="content" source="./media/BDM-Overview-ERFormatTags.png" alt-text="Screenshot of the ER configurations page with Business document type tag.":::

You can restrict the list of templates available in the **Business document management** workspace by configuring access permissions. This restriction is important when different templates produce business documents for different business domains (functional areas), and you want to allow specific users access to different templates for editing in the **Business document management** workspace.

Set **Business document management** access permissions on the **Configurator of access permissions**. Only the following users can access the page:

- Users assigned to the **System administrator** role.
- Users assigned to any other role that is configured to perform the duty, **Configure permissions to access Business document templates for editing** (AOT name **ERBDTemplatesSecurity**).

Use the following procedure to set up the access **Business document management** permissions for all legal entities.

1. Sign in as a user with access to the **Configurator of access permissions** page.
1. Go to **Organization administration** \> **Electronic reporting** \> **Business document management** \> **Manage access permissions**.

    Pay attention to the notification that informs you that the usage of access permissions for **Business document management** isn't currently enabled.

    :::image type="content" source="./media/BDM-Overview-TemplatesAccess1.png" alt-text="Screenshot of the Configurator of Business document management access permissions page.":::

    With this setting, every user assigned to any security role that is configured to perform the **Manage Business document templates** (AOT name **ERBDManageTemplates**) duty can open the Business document management workspace and can edit any template that is available.

    The following graphic shows what is available in the **Business document management** workspace for users assigned to the **Accounts receivable clerk** role. With the current access permissions setting, the user can edit business document templates from different functional areas including invoicing, regulatory reporting, and payments.

    :::image type="content" source="./media/BDM-Overview-TemplatesForAlice1.png" alt-text="Screenshot of the Business document management workspace page for Accounts receivable clerk.":::

1. On the **Configurator of access permissions** page, select **Access permissions setting**.
1. In the **Settings of access permissions to edit templates** dialog box, enable the **Apply configured access permissions** option.
1. Select **OK** to confirm that Business document management access permissions are enabled.

    :::image type="content" source="./media/BDM-Overview-TemplatesAccess2.png" alt-text="Screenshot of the confirmation dialog for Business document management access permissions.":::

1. Select **Add** to enter a new business role for which permissions to access Business document management templates must be configured.
1. In the **Security roles** dialog box, select the **Accounts receivable clerk** role and then select **OK** to confirm the role selection.
1. On the **Access permissions per tags of configurations** tab, select **New**.
1. In the **Tag type** field, select **Functional area**, and in the **ID** field, select **Invoicing**.
1. Select **Save** to store configured access permissions for the selected role.

    The current setting means that for any user who is assigned to the **Accounts receivable clerk** role and performing the duty, **Manage Business document templates** (AOT name **ERBDManageTemplates**), ER format configuration templates that have the **Invoicing** value for the **Functional area** tag are available to edit in the Business document management workspace.

1. Switch the **Related information** pane from the right side of the current page. The **Related information** pane shows how the configured access permissions are applied, including what ER configuration templates are available for users that are assigned to the **Accounts receivable clerk** role.

    :::image type="content" source="./media/BDM-Overview-TemplatesAccess3.png" alt-text="Screenshot of the Related information pane on the Configurator of access permissions page.":::

1. On the **Access permissions per configurations** tab, select the **Add** option.
1. In the **Select configuration** dialog box, mark the **Intrastat report** ER format configuration.
1. Select **OK** to confirm the entry of the selected configurations and then select **Save** to store the configured access permissions for the selected role.

The current setting means that for any user assigned to the **Accounts receivable clerk** role and performing the duty, **Manage Business document templates** (AOT name **ERBDManageTemplates**), the following templates are available to edit in the Business document management workspace:

- Templates that have the value, **Invoicing** for the **Functional area** tag.
- Templates from ER format configurations that are listed on the **Access permissions per configurations** tab (templates from the **Intrastat report** format configuration of the **Statutory reporting** domain in this example).

:::image type="content" source="./media/BDM-Overview-TemplatesAccess4.png" alt-text="Screenshot of the Access permissions FastTabs on the Configurator of access permissions page.":::

The following graphic shows what the **Business document management** workspace provides to a user assigned to the **Accounts receivable clerk** role. With the current Business document management access permissions setting, the user can edit business document templates from the **Invoicing** domain and the **Intrastat report** ER format configuration. Templates from the **Payments** domain aren't accessible for the **Accounts receivable clerk** role.

:::image type="content" source="./media/BDM-Overview-TemplatesForAlice2.png" alt-text="Screenshot of editing business document templates on the Business document management workspace page.":::

> [!NOTE]
> The **Access permissions per configurations** rules use the unique identification ID of an ER format configuration. These rules stay even if you delete an ER configuration that refers to them. When you import deleted configurations back to this instance, these rules refer to them again. You don't need to set up the rules again after you import the deleted configurations.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
