---
title: Business document management overview
description: Learn about how to use the Business document management feature of the ER framework, including learning about supported Microsoft 365 applications.
author: kfend
ms.author: filatovm
ms.topic: overview
ms.date: 04/09/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2019-08-01
ms.search.form: ERBDWorkspace, ERBDParameters, ERSecurityAccessEditor
ms.dyn365.ops.version: 10.0.5
ms.assetid: 
ms.custom: sfi-image-nochange
---

# Business document management overview

[!include [banner](../includes/banner.md)]

Business users use the [Electronic reporting (ER)](general-electronic-reporting.md) framework to configure formats for outbound documents in accordance with the legal requirements of various countries and regions. Users can also define the dataflow to specify what application data goes into generated documents. The ER framework generates outbound documents in Microsoft Office formats (Excel workbooks or Word documents) by using predefined templates. The templates are populated with required data according to the configured dataflow while required documents are generated. Each configured format can be published as part of an ER solution to generate specific outbound documents. This configuration is represented by an ER format configuration that can contain templates you can use to generate different outbound documents. Business users can use this framework to manage required business documents.

**Business document management** is built on top of the ER framework and enables business users to edit business document templates by using Microsoft 365 service or appropriate Microsoft Office desktop application. Edits to the documents might include changing business document designs and adding placeholders for extra data without source code changes and new deployments. No knowledge of the ER framework is required to update templates of business documents.

> [!NOTE]
> Business document management enables you to modify templates that are used to produce business documents such as orders, invoices, and more. When you modify a template and publish a new version, the new version is used to generate required business documents. You can't use Business document management to modify already generated business documents.

## Supported deployments

Currently, the Business document management feature is implemented only for cloud deployments. If this feature is critical to your on-premises deployment, provide feedback on the [Ideas](https://experience.dynamics.com/ideas/) site.

## Supported Microsoft Office applications

To use Business document management for editing templates in Excel or Word formats by using Microsoft Office desktop applications, you must have Microsoft Office 2010 or later installed. This support is available in cloud and on-premises deployments.

To use Business document management for editing templates in Excel or Word formats by using Microsoft 365 applications, you must have Microsoft 365 Office for the web subscription. This support is available in cloud deployment.

## Business document availability

For a complete list of all the reports planned for the October 2019 release, see [Configurable business documents reporting in Word and Excel](/dynamics365-release-plan/2019wave2/dynamics365-finance-operations/configurable-business-documents-reporting-word-excel-pdf#feature-details).

For a complete list of all the reports planned for the October 2020 release, see [Configurable business documents – Word templates](/dynamics365-release-plan/2020wave1/dynamics365-finance/configurable-business-documents-word-templates).

More reports will become available in future releases. Special notifications about additional reports are sent separately. To learn how to review the list of currently available reports, see the section [List of ER configurations that have been released in Finance to support configurable business documents](#list-of-configurations-cbd).

To learn more about this feature, complete the example in this article.

## Configure ER parameters

Because Business document management is built on top of the ER framework, you must configure the ER parameters to start working with Business document management. Set up the ER parameters as described in [Configure the Electronic reporting (ER) framework](electronic-reporting-er-configure-parameters.md). You also need to add a new configuration provider as described in [Create configuration providers and mark them as active](tasks/er-configuration-provider-mark-it-active-2016-11.md).

:::image type="content" source="./media/BDM-Overview-ERSetting.png" alt-text="Screenshot of the ER workspace.":::

## Import ER solutions

This procedure uses sample ER configurations. You must import into your current instance of Dynamics 365 Finance the ER configurations that contain the business document templates you can edit by using Business document management. To complete this procedure, download and locally store the following files.

**Sample ER customer invoicing solution**

| File                                      | Content |
|-------------------------------------------|---------|
| Customer invoicing model.version.2.xml    | [ER data model configuration](https://download.microsoft.com/download/b/f/a/bfa5cb52-e6e2-42bc-a4c0-77014a4c54e6/Customerinvoicingmodel.version.2.xml) |
| Customer FTI report (GER).version.2.3.xml | [Free text invoice ER format configuration](https://download.microsoft.com/download/3/c/2/3c2e58f2-6e56-43d9-85ea-4c97252a108d/CustomerFTIreportGER.version.2.3.xml) |

**Sample ER payment checks solution**

| File                                     | Content |
|------------------------------------------|---------|
| Model for cheques.version.10.xml         | [ER data model configuration](https://download.microsoft.com/download/3/7/6/376cb0f6-181a-4895-a432-390ffca64162/Modelforcheques.version.10.xml) |
| Cheques printing format.version.10.9.xml | [Payment cheque ER format configuration](https://download.microsoft.com/download/6/d/6/6d61bfff-3d89-4377-9e34-2e3ee6d6df91/Chequesprintingformat.version.10.9.xml) |

**Sample ER foreign trade solution**

| File                             | Content |
|----------------------------------|---------|
| Intrastat model.version.1.xml    | [ER data model configuration](https://download.microsoft.com/download/2/0/0/200d6ed1-eff8-48ec-ab75-175a4acf9714/Intrastatmodel.version.1.xml) |
| Intrastat report.version.1.9.xml | [Intrastat control report ER format configuration](https://download.microsoft.com/download/7/a/2/7a2a27c3-a8a5-42a1-9d04-f0a8e1ec1707/Intrastatreport.version.1.9.xml) |

Use the following procedure to import each file. Import the ER *data model* configuration of each ER solution in the preceding tables before you import the corresponding ER *format* configuration.

1. Open **Organization administration** > **Electronic reporting** > **Configurations**.
1. At the top of the page, select **Exchange**.
1. Select **Load from XML file**.
1. Select **Browse** to load the required XML file.
1. Select **OK** to confirm the configuration import.

:::image type="content" source="./media/BDM-Overview-ERSolutions.png" alt-text="Screenshot of the ER configurations page confirming configuration import.":::

Alternatively, you can import the officially published ER format configurations from Microsoft Dynamics Lifecycle Services. For example, to complete this procedure, you can import the latest version of the **Free text invoice (Excel)** ER format configuration. The corresponding ER data model and ER model mapping configurations are imported automatically.

:::image type="content" source="./media/BDM-Overview-SharedAssetLibrary.png" alt-text="Screenshot of the Lifecycle Services shared asset library content page.":::

For more information about importing ER configurations, see [Manage the ER configuration lifecycle](general-electronic-reporting-manage-configuration-lifecycle.md).

## Enable Business document management

> [!NOTE]
> In versions of Finance before 10.0.21, you need to explicitly enable Business document management functionality. However, starting in version 10.0.21, the **Business document management** feature is automatically enabled. Then, starting in version 10.0.29, the feature becomes mandatory. In other words, it's automatically turned on and can't be turned off. In Finance version 10.0.32, the feature is eliminated.
>
> The system behavior assumes that Business document management functionality is enabled by default. This section applies to Finance versions earlier than 10.0.21.

To start Business document management, open the **Feature management** workspace and enable the **Business document management** feature.

Use the following procedure to enable Business document management functionality for all legal entities.

1. Open the **Feature management** workspace.
1. On the **New** tab, select the **Business document management** feature in the list.
1. Select **Enable now** to turn on the selected feature.
1. Refresh the page to access the new feature.

> [!NOTE]
> For more information about using the new document user interface in Business document management, see [New document user interface in Business document management](er-business-document-management-new-template-ui.md).

:::image type="content" source="./media/BDM-Overview-FMEnabling.png" alt-text="Screenshot of the Feature management workspace.":::

For more information about activating new features, see [Feature management overview](../../fin-ops/get-started/feature-management/feature-management-overview.md).

## Configure parameters

Use the information in the following sections to set up the basic parameters for Business document management.

### Prerequisites for parameter setup

Before you set up Business document management, set up the required document type in the Document management framework. Use this document type to specify a temporary storage of documents in Office formats (Excel and Word) that are used as templates for ER reports. You can edit the temporary storage template by using the Office desktop applications.

For this document type, select the following attribute values.

| Attribute name | Attribute value |
|----------------|-----------------|
| Class          | Attach file     |
| Group          | File            |
| Location       | SharePoint      |

For information about how to set up the required document management parameters and document types, see [Configure document management](../../fin-ops/organization-administration/configure-document-management.md).

:::image type="content" source="./media/BDM-Overview-DMSetting.png" alt-text="Screenshot of the Set up Document management document type page.":::

### <a name="SetupBdmParameters"></a>Set up parameters

Set up basic Business document management parameters on the **Business document parameters** page. Only specific users can access the page. This access includes the following users:

- Users assigned to the **System administrator** role.
- Users assigned to any role that is configured to perform the duty, **Maintain Business document management parameters** (AOT name **ERBDMaintainParameters**).

Use the following procedure to set up the basic parameters for all legal entities.

1. Sign in as a user with access to the **Business document parameters** page.
1. Go to **Organization administration** \> **Electronic reporting** \> **Business document management** \> **Business document parameters**.
1. On the **Business document parameters** page, on the **Attachments** tab, in the **SharePoint document type** field, define the document type that you want to use to temporarily store templates in Office formats while you edit them by using the Office desktop applications.

> [!NOTE]
> For this parameter, you can only select document types that are configured by using a SharePoint location.

:::image type="content" source="./media/BDM-Overview-BDMSetting.png" alt-text="Screenshot of the set up of Business document management parameters.":::

The selected document type is company-specific. Use it when working with Business document management in the company for which you configured the selected document type. When you work with Business document management in another company, use the same selected document type if you didn't configure a document type for that company. When you configure a document type, it takes precedence over the one selected in the **SharePoint document type** field.

> [!NOTE]
> The **SharePoint document type** parameter defines a SharePoint folder as temporary storage for templates that are editable by using either Microsoft Excel or Word. Set up this parameter if you plan to use these Office desktop applications for editing templates. For more information, see [Edit a template in the Office desktop application](#EditInOfficeDesktopApp). You can keep this parameter blank if you plan to modify the template by only using the functionality in Microsoft 365. For more information, see [Edit a template in Microsoft 365](#EditInOffice365).

## Configure access permissions

By default, if you don't enable access to Business document management permissions, every user with access to the Business document management workspace sees all of the ER solution templates that are available. The Business document management workspace shows only those templates that reside in ER format configurations and that are marked by a **Business document type** tag.

:::image type="content" source="./media/BDM-Overview-ERFormatTags.png" alt-text="Screenshot of the ER configurations page with Business document type tag.":::

You can restrict the list of templates available in the Business document management workspace by configuring access permissions. This restriction is important when different templates produce business documents for different business domains (functional areas), and you want to allow specific users access to different templates for editing in the Business document management workspace.

Set Business document management access permissions on the **Configurator of access permissions**. Only the following users can access the page:

- Users assigned to the **System administrator** role.
- Users assigned to any other role that is configured to perform the duty, **Configure permissions to access Business document templates for editing** (AOT name **ERBDTemplatesSecurity**).

Use the following procedure to set up the access Business document management permissions for all legal entities.

1. Sign in as a user with access to the **Configurator of access permissions** page.
1. Go to **Organization administration** > **Electronic reporting** > **Business document management** > **Manage access permissions**.

    Pay attention to the notification that informs you that the usage of access permissions for Business document management isn't currently enabled.

    :::image type="content" source="./media/BDM-Overview-TemplatesAccess1.png" alt-text="Screenshot of the Configurator of Business document management access permissions page.":::

    With this setting, every user assigned to any security role that is configured to perform the **Manage Business document templates** (AOT name **ERBDManageTemplates**) duty can open the Business document management workspace and can edit any template that is available.

    The following graphic shows what is available in the Business document management workspace for users assigned to the **Accounts receivable clerk** role. With the current access permissions setting, the user can edit business document templates from different functional areas including invoicing, regulatory reporting, and payments.

    :::image type="content" source="./media/BDM-Overview-TemplatesForAlice1.png" alt-text="Screenshot of the Business document management workspace page for Accounts receivable clerk.":::

1. On the **Configurator of access permissions** page, select **Access permissions setting**.
1. In the **Settings of access permissions to edit templates** dialog box, select the **Apply configured access permissions** option.
1. Select **OK** to confirm that Business document management access permissions are enabled.

    :::image type="content" source="./media/BDM-Overview-TemplatesAccess2.png" alt-text="Screenshot of the Confirm Business document management access permissions dialog.":::

1. Select **Add** to enter a new business role for which permissions to access Business document management templates must be configured.
1. In the **Security roles** dialog box, select the **Accounts receivable clerk** role and then select **OK** to confirm the role selection.
1. On the **Access permissions per tags of configurations** tab, select **New**.
1. In the **Tag type** field, select **Functional area**, and in the **ID** field, select **Invoicing**.
1. Select **Save** to store configured access permissions for the selected role.

    The current setting means that for any user who is assigned to the **Accounts receivable clerk** role and performing the duty, **Manage Business document templates** (AOT name **ERBDManageTemplates**), ER format configuration templates that have the **Invoicing** value for the **Functional area** tag are available to edit in the Business document management workspace.

1. Switch the **Related information** pane from the right side of the current page. The **Related information** pane shows how the configured access permissions are applied, including what ER configuration templates are available for users that are assigned to the **Accounts receivable clerk** role.

    :::image type="content" source="./media/BDM-Overview-TemplatesAccess3.png" alt-text="Screenshot of the Related information pane on Configurator of access permissions page.":::

1. On the **Access permissions per configurations** tab, select the **Add** option.
1. In the **Select configuration** dialog box, mark the **Intrastat report** ER format configuration.
1. Select **OK** to confirm the entry of the selected configurations and then select **Save** to store the configured access permissions for the selected role.

The current setting means that for any user assigned to the **Accounts receivable clerk** role and performing the duty, **Manage Business document templates** (AOT name **ERBDManageTemplates**), the following templates are available to edit in the Business document management workspace:

- Templates that have the value, **Invoicing** for the **Functional area** tag.
- Templates from ER format configurations that are listed on the **Access permissions per configurations** tab (templates from the **Intrastat report** format configuration of the **Statutory reporting** domain in this example).

:::image type="content" source="./media/BDM-Overview-TemplatesAccess4.png" alt-text="Screenshot of the Access permissions FastTabs on the Configurator of access permissions page.":::

The following graphic shows what the Business document management workspace provides to a user assigned to the **Accounts receivable clerk** role. With the current Business document management access permissions setting, the user can edit business document templates from the **Invoicing** domain and the **Intrastat report** ER format configuration. Templates from the **Payments** domain aren't accessible for the **Accounts receivable clerk** role.

:::image type="content" source="./media/BDM-Overview-TemplatesForAlice2.png" alt-text="Screenshot of editing business document templates on the Business document management workspace page.":::

> [!NOTE]
> The **Access permissions per configurations** rules use the unique identification ID of an ER format configuration. These rules stay in place even if you delete an ER configuration that refers to them. When you import deleted configurations back to this instance, these rules refer to them again. You don't need to set up the rules again after the deleted configurations are imported.

## Use Business document management to edit templates

Business users can access business document templates for editing in the Business document management workspace. Only the following users can access the Business document management workspace:

- Users assigned to the role, **System administrator**.
- Users assigned to any role that is configured to perform the duty, **Manage Business document templates** (AOT name **ERBDManageTemplates**).

Use the following procedure to edit free text invoice templates in the Business document management workspace. Before you complete this procedure, you must have completed all of the preceding procedures in this article.

1. Sign in as a user with access to the Business document management workspace.
1. Open the Business document management workspace.

> [!NOTE]
> Starting in Finance version 10.0.21, the **Office-like UI experience for Business document management** feature is turned on by default. Then, starting in Finance version 10.0.29, the feature became mandatory and can't be turned off. Starting in Finance version 10.0.32, the feature is eliminated.

When the **Office-like UI experience for Business document management** feature is turned off in the **Feature management** workspace, the main grid in the **Business document management** workspace shows the following templates:

- Templates that your ER configuration provider owns (that is, the provider that is currently marked as active in the **Electronic reporting** workspace). After you select one of these templates, you can select **Edit template** to start or continue to edit it.
- Templates that other ER configuration providers own. After you select one of these templates, you can select **New document** to create a copy of it that your ER configuration provider owns, and then start to edit the copy.

:::image type="content" source="./media/BDM-Overview-EditingTemplate1.png" alt-text="Screenshot of the template listings on the Business document management workspace page.":::

The **Template** tab presents the content of the selected template. Select the **Details** tab to review details of the selected template as well as details of an ER format configuration this template resides in. All of the templates have a status of **Published**, and contain no details in the **Revision** column. This status means that these templates aren't currently being edited.

<a name="UIturnedOn"></a>When the **Office-like UI experience for Business document management** feature is turned on in the **Feature management** workspace, the main grid in the **Business document management** workspace shows templates that your ER configuration provider owns (that is, the provider that is currently marked as active in the **Electronic reporting** workspace). After you select one of these templates, you can select **Edit template** to start or continue to edit it.

To work with templates that other ER configuration providers own, select **New document** to create a copy of the template that your ER provider owns. You can then start to edit the copy. For more information, see [New document user interface in Business document management](er-business-document-management-new-template-ui.md).

### Initiate editing templates owned by your configuration provider

1. In the Business document management workspace, select the **Cheques printing format** template in the list.
1. Select the **Details** tab.

:::image type="content" source="./media/BDM-Overview-EditingTemplate2.png" alt-text="Screenshot of the Business document management workspace page, Details tab.":::

The **Edit template** option is available for the selected template. This option is always available for a template in an ER format configuration that the active ER configuration provider owns (**Litware, Inc.** in this example). When you select **Edit template**, you can edit the existing template from the draft version of the underlying ER format configuration.

### Initiate editing templates owned by other providers

1. In the Business document management workspace, select the document that you want to use as a template.

    :::image type="content" source="./media/BDM-Overview-EditingTemplate3.png" alt-text="Screenshot of selecting a document on the Business document management workspace page.":::

1. Select **New document**, and in the **Title** field, change the title of the editable template if needed. The text you enter is used to name the ER format configuration that is automatically created. The draft version of this configuration (**Customer FTI report (GER) Copy**) automatically includes the edited template and is marked to run this ER format for the current user. At the same time, the non-modified original template from the base ER format configuration is used to run this ER format for any other user.
1. In the **Name** field, change the name of the first revision of the editable template that is created automatically.
1. In the **Comment** field, change the comment for the automatically created revision of the editable template.
1. Select **OK** to start the editing process.

:::image type="content" source="./media/BDM-Overview-EditingTemplate4.png" alt-text="Screenshot of confirming the start of the editing process to create a new template.":::

If no provider exists, you're prompted to create one. If no active provider exists, you're prompted to choose a provider to activate.

To create a provider, change the name of the provider in the **Name** field, update the internet address of the new provider in the **Internet address** field, and select **OK** to confirm.

   :::image type="content" source="./media/bdm_create_provider.png" alt-text="Screenshot of creating a new provider in BDM.":::

To activate an existing provider, choose the name of the provider in the **Configuration provider** field, and select **OK** to set the provider as active.

   :::image type="content" source="./media/bdm_choose_provider.png" alt-text="Screenshot of activating a provider in BDM.":::

> [!NOTE]
> Each BDM template refers to the provider as the author of the configuration. This is why an active provider is required for the template.

The **New document** option is always available for a template in an ER format configuration provided by current and another provider (Microsoft in this example) that doesn't have any revision. The edited template is stored in a new ER format configuration that is automatically generated.

### Start editing a template

1. Select **Edit document** from the selected template.
1. In the **Name** field, change the name of the first revision of the editable template that is created automatically.
1. In the **Comment** field, enter a remark for the automatically created revision of the editable template.

    :::image type="content" source="./media/BDM-Overview-EditingTemplate5.png" alt-text="Screenshot of editing a template on the Business document management workspace page.":::

1. Select **OK** to start the editing process.

The **BDM template editor** page opens. You can edit the selected template online by using Microsoft 365.

:::image type="content" source="./media/BDM-Overview-EditingLayout1.png" alt-text="Screenshot of the Business document management template editor page.":::

### <a name="EditInOffice365"></a>Edit a template in Microsoft 365

You can modify the template by using Microsoft 365. For example, in Office online, change the font of the field prompts in the template header from **Regular** to **Bold**. The editable template automatically stores these changes. The primary template's storage (by default, the Azure blob storage) stores the editable template. The ER framework configures this storage.

:::image type="content" source="./media/BDM-Overview-EditingLayout2.png" alt-text="Screenshot of changing font to bold in the template header on the Business document management template editor page.":::

### <a name="EditInOfficeDesktopApp"></a>Edit a template in the Office desktop application

> [!NOTE]
> This function is available only when you properly configure the **SharePoint document type** parameter. For more information, see [Configure parameters](#SetupBdmParameters).

1. Select the **Open in Desktop App** option to modify the template by using the functionality of the Office desktop application (Excel in this example). The editable template is copied from the permanent storage to the temporary storage configured in the Business document management parameters as a SharePoint folder.
1. Confirm that you want to open the template from the temporary file storage in the Office desktop Excel application.

    :::image type="content" source="./media/BDM-Overview-EditingLayout3.png" alt-text="Screenshot of the template opened in desktop Excel application.":::

1. Modify the template. For example, change the font of the fields prompts in the template header by updating color from **Black** to **Blue**.

    :::image type="content" source="./media/BDM-Overview-EditingLayout4.png" alt-text="Screenshot of modifying the font color in the template header using the desktop Excel application.":::

1. Select **Save** in the Excel desktop application to store the template changes in the temporary storage.

    :::image type="content" source="./media/BDM-Overview-EditingLayout5.png" alt-text="Screenshot of saving changes to the Business document management template editor page using the desktop Excel application.":::

1. Close the Excel desktop application.
1. Select **Sync stored copy** to synchronize the temporary template storage to the permanent template storage.

> [!NOTE]
> The copy of the editable template in the temporary file storage is kept only for the current session of template editing. When you finish this session by closing the **BDM template editor** page, this copy is deleted. If you adjusted the template in the temporary file storage and didn't select **Sync stored copy**, when you try to close the **BDM template editor** page, a message asks whether you want to store introduced changes. Select **Yes** if you want to save your changes to the template in the permanent file location.

### Validate a template

1. On **BDM template editor**, select **Check for issues** to validate the modified template against the underlying ER format configuration. Follow the recommendations (if any) to align the template with the structure of the format from the base ER format configuration.
1. Select **Show format** to view the current structure of the format from the base ER format configuration that you need to align with the editable template.
1. Select **Hide format** to close the pane.

    :::image type="content" source="./media/BDM-Overview-EditingTemplate6.png" alt-text="Screenshot of the BDM template editor page.":::

1. Close **BDM template editor**.

The **Template** tab shows the updated template. The status of the edited template is now **Draft** and the current revision isn't empty. This status means that the process of editing this template has started.

:::image type="content" source="./media/BDM-Overview-EditingTemplate5.png" alt-text="Screenshot of viewing the updated template on the Business document management workspace page.":::

### Test the modified template

1. In the application, change to the company, **USMF**.
1. Go to **Accounts receivable** > **Invoices** > **All free text invoices**.
1. Select the **FTI-00000002** invoice, and then select **Print management**.
1. Select the **Module - accounts receivable** > **Documents** > **Free text invoice** > **Original document** level to specify the scope of invoices for processing.
1. In the **Report format** field, select the **Customer FTI report (GER) Copy** ER format for the specified document level.

    :::image type="content" source="./media/BDM-Overview-TestRun1.png" alt-text="Screenshot of the Print management setting page.":::

1. Press **Escape** to close the current page.
1. Select **Print**, and then select **Selected**.
1. Download the document and open it by using the Excel desktop application.

:::image type="content" source="./media/BDM-Overview-TestRun2.png" alt-text="Screenshot of the Free text invoices page.":::

The modified template is used to generate the free text invoice report for the selected item. To analyze how this report is affected by the changes that you introduced to the template, run this report in one application session right after you modified the template in another application session.

### Create an alternative template revision

1. Open the **BDM template editor** page and select the **Customer FTI report (GER) Copy** template.
1. On the **Revisions** tab, select **New**.
1. If needed, change the name of the second revision in the **Name** field. This revision is based on the currently active first revision.
1. If needed, change the remark for the automatically created revision of the editable template in the **Comment** field.

    :::image type="content" source="./media/BDM-Overview-AddRevision.png" alt-text="Screenshot of creating revisions to the template on the Business document management workspace page.":::

    You created a new revision of your template that is stored in the permanent template storage. Now you can continue editing the template of the second revision that is currently selected as active.

1. Select the first revision and then select **Set active**. You can select another revision as active if you want to return to that revision of the template.
1. Select the second revision, and then select **Delete**.
1. Select **OK** to confirm that you want to delete the selected revision. You can delete any of the non-active revisions when they're no longer needed.

### Delete a modified template

1. On **BDM template editor**, select the **Template** tab.
1. Select **Delete**.
1. If you select **OK** to confirm deletion, the **Customer FTI report (GER) Copy** ER format with the modified template is deleted. Select **Cancel** to explore other options.

### Revoke changes to a template

When you edit the template from an ER format that the current active provider owns, you see the option to revoke changes you made to the template.

:::image type="content" source="./media/BDM-Overview-RevokeChanges.png" alt-text="Screenshot of rejecting changes to the template on the Business document management workspace page.":::

1. On **BDM template editor**, select the **Template** tab.
1. Select **Undo**.
1. If you select **OK** to revoke the changes you made to the template, the modified template is replaced by the original template and all changes are removed. When you revoke changes to the template, you can delete the template. Select **Cancel** to explore other options.

### Publish a modified template

1. On **BDM template editor**, on the **Template** tab, select **Publish**.
1. If you select **OK** to confirm publishing, the draft version of the derived **Customer FTI report (GER) Copy** ER format that contains the modified template is marked as completed. The modified template becomes available for other users. The completed versions of this ER format keep only the last active revision of your template. Other revisions are deleted. Select **Cancel** to explore other options.

## Frequently asked questions

### I selected Edit document, but instead of going to the BDM template editor page in Finance, I was sent to the Microsoft 365 webpage

This problem is a known problem that involves Microsoft 365 redirection. It occurs when you sign in to Microsoft 365 for the first time. To work around this problem, select **Back** in your browser to return to the previous page.

### I understand how to edit a template by using Microsoft 365 in the first application session, and how to use the template in the second application session and adjust the template to see how my changes affect the generated business document. Can I use the Office desktop application in the same way?

Yes, you can. In the first application session, select **Open in Desktop App**. Your template is stored in the temporary file storage and opened in the Office desktop application. Next, complete the following steps to preview your template changes in the generated business document:

1. Make changes in the template by using the Office desktop application.
1. Select **Save** in the Office desktop application.
1. On **BDM template editor** of the first application session, select **Sync stored copy**.
1. Execute this template ER format in the second application session.

### When I select Open in Desktop App, I receive the following error message: "Value cannot be null. Parameter name: externalId." How do I work around this issue?

Most likely, you signed in to the current instance of the app by using the Microsoft Entra domain that differs from the Microsoft Entra domain that you used to deploy this instance. Because the SharePoint service stores templates for editing by using the Office desktop applications, and it belongs to the same domain, the app has no permissions to access the SharePoint service. To resolve this issue, sign in to the current instance by using the credentials of a user with the correct Microsoft Entra domain.

## Additional resources

[Electronic reporting (ER) overview](general-electronic-reporting.md)

[ER Design a configuration for generating reports in OPENXML format (November 2016)](tasks/er-design-reports-openxml-2016-11.md)

[Design ER configurations to generate reports in Word format](tasks/er-design-configuration-word-2016-11.md)

[Embed images and shapes in documents that you generate by using ER](electronic-reporting-embed-images-shapes.md)

[Configure Electronic reporting (ER) to pull data into Power BI](general-electronic-reporting-report-configuration-get-data-powerbi.md)

## <a name="list-of-configurations-cbd"></a>List of ER configurations that Finance releases to support configurable business documents

The [list](general-electronic-reporting.md#list-of-configurations) of ER configurations for Finance is constantly updated. Open the [Global repository](er-download-configurations-global-repo.md) to review the list of ER configurations that are currently supported. You can [filter](../../../finance/localizations/enhanced-filtering-global-repo.md) the Global repository to review the list of ER configurations that support configurable business documents.

:::image type="content" source="./media/bdm-overview-filterglobalrepo.gif" alt-text="Screenshot of filtering the content of the Global repository on the Configuration repository page.":::

The following table shows the list of ER configurations that support configurable business documents and that Finance releases up until December 2020.

| Data model configuration    | Format configurations                           |
|-----------------------------|-------------------------------------------------|
| Bill of lading model        | Bill of lading (Excel)                          |
|                             | Bill of lading (Word)                           |
| Certificate of origin model | Certificate of origin (Excel)                   |
|                             | Certificate of origin (Word)                    |
| Invoice model               | Customer Debit and Credit Note (Excel)          |
|                             | Customer Debit and Credit Note (Word)           |
|                             | Free text invoice (Excel)                       |
|                             | Free text invoice (Excel) (BH)                  |
|                             | Free text invoice (FR) (Excel)                  |
|                             | Free text invoice (LT) (Excel)                  |
|                             | Free text invoice (LV) (Excel)                  |
|                             | Free text invoice (PL) (Excel)                  |
|                             | Free text invoice (CZ) (Excel)                  |
|                             | Free text invoice (EE) (Excel)                  |
|                             | Free text invoice (HU) (Excel)                  |
|                             | Free text invoice (TH) (Excel)                  |
|                             | Free text invoice (Word)                        |
|                             | Project contract line items (Excel)             |
|                             | Project contract line items (CZ) (Excel)        |
|                             | Project contract line items (Excel) (BH)        |
|                             | Project contract line items (HU) (Excel)        |
|                             | Project contract line items (LT) (Excel)        |
|                             | Project contract line items (PL) (Excel)        |
|                             | Project contract line items (Word)              |
|                             | Project customer retention release (Excel)      |
|                             | Project customer retention release (CZ) (Excel) |
|                             | Project customer retention release (HU) (Excel) |
|                             | Project customer retention release (LT) (Excel) |
|                             | Project customer retention release (PL) (Excel) |
|                             | Project customer retention release (TH) (Excel) |
|                             | Project customer retention release (Word)       |
|                             | Project invoice (Excel)                         |
|                             | Project Invoice (Word)                          |
|                             | Project invoice (AE) (Excel)                    |
|                             | Project invoice (CZ) (Excel)                    |
|                             | Project invoice (Excel) (BH)                    |
|                             | Project invoice (HU) (Excel)                    |
|                             | Project invoice (JP) (Excel)                    |
|                             | Project invoice (LT) (Excel)                    |
|                             | Project invoice (PL) (Excel)                    |
|                             | Project invoice (TH) (Excel)                    |
|                             | Project invoice full (MY) (Excel)               |
|                             | Project invoice simple (MY) (Excel)             |
|                             | Project manage invoice (Excel)                  |
|                             | Project manage invoice (CZ) (Excel)             |
|                             | Project manage invoice (Excel) (BH)             |
|                             | Project manage invoice (HU) (Excel)             |
|                             | Project manage invoice (JP) (Excel)             |
|                             | Project manage invoice (LT) (Excel)             |
|                             | Project manage invoice (PL) (Excel)             |
|                             | Project manage invoice (Word)                   |
|                             | Purchase advance invoice (Excel)                |
|                             | Purchase advance invoice (Word)                 |
|                             | Sales advance invoice (Excel)                   |
|                             | Sales advance invoice (Word)                    |
|                             | Sales advance invoice (PL) (Excel)              |
|                             | Sales invoice (Excel)                           |
|                             | Sales invoice (Excel) (BH)                      |
|                             | Sales invoice (Excel) (CZ)                      |
|                             | Sales invoice (Excel) (EE)                      |
|                             | Sales invoice (Excel) (FR)                      |
|                             | Sales invoice (Excel) (HU)                      |
|                             | Sales invoice (Excel) (IN)                      |
|                             | Sales invoice (Excel) (LT)                      |
|                             | Sales invoice (Excel) (LV)                      |
|                             | Sales invoice (Excel) (PL)                      |
|                             | Sales invoice (Excel) (TH)                      |
|                             | Sales invoice (Word)                            |
|                             | TMS Commercial Invoice (Excel)                  |
|                             | TMS Commercial Invoice (Word)                   |
|                             | Vendor invoice document (Excel)                 |
|                             | Vendor invoice document (CZ) (Excel)            |
|                             | Vendor invoice document (HU) (Excel)            |
|                             | Vendor invoice document (IN) (Excel)            |
|                             | Vendor invoice document (LT) (Excel)            |
|                             | Vendor invoice document (LV) (Excel)            |
|                             | Vendor invoice document (MY) (Excel)            |
|                             | Vendor invoice document (Word)                  |
| Order model                 | Agreement confirmation (Excel)                  |
|                             | Agreement confirmation (Word)                   |
|                             | Purchase agreement confirmation (Excel)         |
|                             | Purchase agreement confirmation (Word)          |
|                             | Purchase order (Excel)                          |
|                             | Purchase order (CZ) (Excel)                     |
|                             | Purchase order inquiry (CZ) (Excel)             |
|                             | Purchase order (HU) (Excel)                     |
|                             | Purchase order inquiry (HU) (Excel)             |
|                             | Purchase order (Word)                           |
|                             | Purchase order inquiry (Excel)                  |
|                             | Purchase order inquiry (Word)                   |
|                             | Sales order confirmation (Excel)                |
|                             | Sales order confirmation (CZ) (Excel)           |
|                             | Sales order confirmation (HU) (Excel)           |
|                             | Sales order confirmation (Word)                 |
| Packing list model          | Container contents (Excel)                      |
|                             | Container contents (Word)                       |
|                             | Load list (Excel)                               |
|                             | Load list (Word)                                |
|                             | Picking list (Excel)                            |
|                             | Picking list (CZ) (Excel)                       |
|                             | Picking list (Word)                             |
|                             | Production pick list (Excel)                    |
|                             | Production pick list (Word)                     |
|                             | Shipping pick list for load (Excel)             |
|                             | Shipping pick list for load (Word)              |
|                             | Shipping pick list for shipment (Excel)         |
|                             | Shipping pick list for shipment (Word)          |
|                             | Shipping pick list for wave (Excel)             |
|                             | Shipping pick list for wave (Word)              |
| Payment model               | Customer payment advice (Excel)                 |
|                             | Customer payment advice (Word)                  |
|                             | Vendor payment advice (Excel)                   |
|                             | Vendor payment advice (Word)                    |
| Quotation model             | Project quotation (Excel)                       |
|                             | Project quotation (Word)                        |
|                             | Request for quotation (Excel)                   |
|                             | Request for quotation (Accept) (Excel)          |
|                             | Request for quotation (Accept) (Word)           |
|                             | Request for quotation (Reject) (Excel)          |
|                             | Request for quotation (Reject) (Word)           |
|                             | Request for quotation (Return) (Excel)          |
|                             | Request for quotation (Return) (Word)           |
|                             | Request for quotation (Word)                    |
|                             | Sales quotation (Excel)                         |
|                             | Sales quotation (CZ) (Excel)                    |
|                             | Sales quotation (HU) (Excel)                    |
|                             | Sales quotation (Word)                          |
|                             | Sales quotation confirmation (Excel)            |
|                             | Sales quotation confirmation (Word)             |
| Reconciliation model        | Cust account statement, Ext (Excel)             |
|                             | Cust account statement, Ext (CN) (Excel)        |
|                             | Cust account statement, Ext (Word)              |
|                             | Cust account statement, France (Excel)          |
| Reminder model              | Collection letter note (Excel)                  |
|                             | Collection letter note (CN) (Excel)             |
|                             | Collection letter note (Word)                   |
|                             | Customer interest note (Excel)                  |
|                             | Customer interest note (Word)                   |
| Waybill model               | Load tender (Excel)                             |
|                             | Load tender (Word)                              |
|                             | Purchase order packing slip (Excel)             |
|                             | Purchase order packing slip (CZ) (Excel)        |
|                             | Purchase order packing slip (Word)              |
|                             | Route (Excel)                                   |
|                             | Route (Word)                                    |
|                             | Sales order packing slip (Excel)                |
|                             | Sales order packing slip (CZ) (Excel)           |
|                             | Sales order packing slip (LT) (Excel)           |
|                             | Sales order packing slip (PL) (Excel)           |
|                             | Sales order packing slip (Word)                 |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
