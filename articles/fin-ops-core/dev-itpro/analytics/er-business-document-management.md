---
# required metadata

title: Business document management overview
description: This topic provides information about how to use the Business document management feature of the ER framework.
author: NickSelin
manager: AnnBe
ms.date: 04/10/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: ERBDWorkspace, ERBDParameters, ERSecurityAccessEditor
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
ms.search.validFrom: 2019-08-01
ms.dyn365.ops.version: 10.0.5

---

# Business document management overview

[!include [banner](../includes/banner.md)]

Business users use the [Electronic reporting (ER)](general-electronic-reporting.md) framework to configure formats for outbound documents in accordance with the legal requirements of various countries/regions. Users can also define the dataflow to specify what application data is placed in generated documents. The ER framework generates outbound documents in Microsoft Office formats (Excel workbooks or Word documents) by using predefined templates. The templates are populated with required data in accordance to configured dataflow while required documents are generated. Each configured format can be published as part of an ER solution to generate specific outbound documents. This is represented by an ER format configuration that can contain templates you can use to generate different outbound documents. Business users can use this framework to manage required business documents.

**Business document management** is built on top of the ER framework and enables business users to edit business document templates by using Microsoft Office 365 service or appropriate Microsoft Office desktop application. Edits to the documents might include changing business document designs and adding placeholders for additional data without source code changes and new deployments. No knowledge of the ER framework is required to update templates of business documents.

> [!NOTE]
> Be aware that Business document management allows you to modify templates that are used to produce business documents such as orders, invoices, etc. While a template has been modified and a new version of it has been published, this version is used to generate required business documents. Business document management cannot be used to modify already generated business documents.

## Supported deployments

Currently, the Business document management feature is implemented only for cloud deployments. If this feature is critical to your on-premises deployment, let us know by providing feedback on the [Ideas](https://experience.dynamics.com/ideas/) site.

## Supported Microsoft Office applications

To use Business document management for editing templates in Excel or Word formats by using Microsoft Office desktop applications, you must have Microsoft Office 2010 or later installed. This is supported in cloud and on-premises deployment.

## Business document availability

The following reports, with Excel-based templates, will available with the release of the public preview:

**Accounts receivable** (August 2019)

- Sales advance invoice
- Sales order packing slip

**Accounts payable** (August 2019)

- Purchase advance invoice
- Purchase order
- Purchase order packing slip

More reports will become available. Special notifications about additional reports will be sent separately. 

A complete list of all the reports planned for the October 2019 release can be found in [Configurable business documents reporting in Word and Excel](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/dynamics365-finance-operations/configurable-business-documents-reporting-word-excel-pdf#feature-details). To learn more about this feature, complete the example in this topic.

## Configure ER parameters

Because Business document management is built on top of the ER framework, you must configure the ER parameters to start working with Business document management. To do this, you need to set up the ER parameters as described in [Configure the Electronic reporting (ER) framework](electronic-reporting-er-configure-parameters.md). You also need to add a new configuration provider as described in [Create configuration providers and mark them as active](tasks/er-configuration-provider-mark-it-active-2016-11.md).

![ER workspace](./media/BDM-Overview-ERSetting.png)

## Import ER solutions

Sample ER configurations are used in the example of this procedure. You must import, into your current instance of Dynamics 365 Finance, the ER configurations that contain the business document templates that can be edited by using Business document management. Download, and then locally store the following files to complete this procedure.

**Sample ER customer invoicing solution**

| **File**                                  | **Content**                                |
|-------------------------------------------|--------------------------------------------|
| Customer invoicing model.version.2.xml    | [ER data model configuration](https://mbs.microsoft.com/customersource/Global/AX/downloads/hot-fixes/365optelecrepeg) |
| Customer FTI report (GER).version.2.3.xml | [Free text invoice ER format configuration](https://mbs.microsoft.com/customersource/Global/AX/downloads/hot-fixes/365optelecrepeg) |

**Sample ER payment checks solution**

| **File**                                  | **Content**                                |
|-------------------------------------------|--------------------------------------------|
| Model for cheques.version.10.xml          | [ER data model configuration](https://mbs.microsoft.com/customersource/Global/AX/downloads/hot-fixes/365optelecrepeg) |
| Cheques printing format.version.10.9.xml  | [Payment cheque ER format configuration](https://mbs.microsoft.com/customersource/Global/AX/downloads/hot-fixes/365optelecrepeg) |

**Sample ER foreign trade solution**

| **File**                                  | **Content**                                |
|-------------------------------------------|--------------------------------------------|
| Intrastat model.version.1.xml             | [ER data model configuration](https://mbs.microsoft.com/customersource/Global/AX/downloads/hot-fixes/365optelecrepeg) |
| Intrastat report.version.1.9.xml          | [Intrastat control report ER format configuration](https://mbs.microsoft.com/customersource/Global/AX/downloads/hot-fixes/365optelecrepeg) |

Use the following procedure to import each file. Import the ER *data model* configuration of each ER solution in the tables above before you import the corresponding ER *format* configuration.

1. Open the **Organization administration** \> **Electronic reporting** \> **Configurations** page.
2. On the top of the page, select **Exchange**.
3. Select **Load from XML file**.
4. Select **Browse** to load the required XML file.
5. Select **OK** to confirm configuration's import.

![ER configurations page](./media/BDM-Overview-ERSolutions.png)


Alternatively, you can import the officially published ER format configurations from Microsoft Dynamics Lifecycle Service (LCS). For example, to complete this procedure you can import the latest version of the **Free text invoice (Excel)** ER format configuration. The corresponding ER data model and ER model mapping configurations will be imported automatically.

![LCS shared asset library content page](./media/BDM-Overview-SharedAssetLibrary.png)

For more information about importing ER configurations, see [Manage the ER configuration lifecycle](general-electronic-reporting-manage-configuration-lifecycle.md).


## Enable Business document management

To start Business document management, you need to open the **Feature management** workspace and enable the **Business document management** feature.

Use the following procedure to enable Business document management functionality for all legal entities.

1. Open the **Feature management** workspace.
2. On the **New** tab, select the **Business document management** feature in the list.
3. Select **Enable now** to turn on the selected feature.
4. Refresh the page to access the new feature.

>[!NOTE]
> For more information about using the new document user interface in Business document management, see [New document user interface in Business document management](er-business-document-management-new-template-ui.md).

![Feature management workspace](./media/BDM-Overview-FMEnabling.png)

For more information about activating new features, see [Feature management overview](../../fin-ops/get-started/feature-management/feature-management-overview.md).

## Configure parameters

Use the information in the following sections to set up the basic parameters for Business document management.

### Prerequisites for parameter setup
Before you can set up Business document management, you must set up the required document type in the Document management framework. This document type is used to specify a temporary storage of documents in Office formats (Excel and Word) that are used as templates for ER reports. The temporary storage template can be edited by using the Office desktop applications.

For this document type, the following attribute values must be selected.

| **Attribute name**  | **Attribute value**   |
|---------------------|-----------------------|
| Class               | Attach file           |
| Group               | File                  |
| Location            | SharePoint            |

For information about how to set up the required document management parameters and document types, see [Configure document management](../../fin-ops/organization-administration/configure-document-management.md).

![Set up Document management document type](./media/BDM-Overview-DMSetting.png)

### <a name="SetupBdmParameters">Set up parameters</a>

Basic Business document management parameters can be set up on the **Business document parameters** page. Only specific users can access the page. This includes:

- Users who are assigned to the **System administrator** role.
- Users who are assigned to any role that is configured to perform the duty, **Maintain Business document management parameters** (AOT name **ERBDMaintainParameters**).

Use the following procedure to set up the basic parameters for all legal entities.

1. Sign in as a user with access to the **Business document parameters** page.
2. Go to **Organization administration** \> **Electronic reporting** \> **Business document management** \> **Business document parameters**.
3.    On the **Business document parameters** page, on the **Attachments** tab, in the **SharePoint document type** field, define the document type that should be used to temporarily store templates in Office formats while they are edited using the Office desktop applications. 

> [!NOTE]
> Only document types that are configured using a SharePoint location are available for this parameter.

![Set up of Business document management parameters](./media/BDM-Overview-BDMSetting.png)

The selected document type is company-specific and will be used when the user is working with Business document management in the company for which the selected document type is configured. When the user is working with Business document management in another company, the same selected document type will be used if one has not been configured for this company. When a document type has been configured, it will be used instead of the one selected in the **SharePoint document type** field.

> [!NOTE]
> The **SharePoint document type** parameter defines a SharePoint folder as temporary storage for templates that are editable using either Microsoft Excel or Word. You need to set up this parameter if you plan to use these Office desktop applications for editing templates. For more information, see [Edit a template in the Office desktop application](#EditInOfficeDesktopApp). You can keep this parameter blank if you plan to modify the template by only using the functionality in  Office 365. For more information, see [Edit a template in Office 365](#EditInOffice365).

## Configure access permissions

By default, when access to Business document management permissions is not enabled, every user with access to the Business document management workspace will see all of the ER solution templates that are available. The Business document management workspace will show only those templates that reside in ER format configurations and that are marked by a **Business document type** tag.

![ER configurations page](./media/BDM-Overview-ERFormatTags.png)

The list of templates available in the Business document management workspace can be restricted by configuring access permissions. This may be important when different templates are used to produce business documents for different business domains (functional areas), and you want to allow specific users access to different templates for editing in the Business document management workspace.

Business document management access permissions can be set on the **Configurator of access permissions**. Only the following users can access the page:

- Users assigned to the **System administrator** role.
- Users assigned to any other role that is configured to perform the duty, **Configure permissions to access Business document templates for editing** (AOT name **ERBDTemplatesSecurity**).

Use the following procedure to set up the access Business document management permissions for all legal entities.

1. Sign in as a user with access to the **Configurator of access permissions** page.
2. Go to **Organization administration** \> **Electronic reporting** \> **Business document management** \> **Manage access permissions**.

    Pay attention to the notification informing you that the usage of access permissions for Business document management is currently not enabled.

    ![Configurator of Business document management access permissions page](./media/BDM-Overview-TemplatesAccess1.png)

    With this setting, every user assigned to any security role that is configured to perform the **Manage Business document templates** (AOT name **ERBDManageTemplates**) duty is able to open the Business document management workspace and can edit any template that is available.

    The following graphic shows what is available in the Business document management workspace for users assigned to the **Accounts receivable clerk** role. With the current access permissions setting, the user can edit business document templates from different functional areas including invoicing, regulatory reporting, and payments.

    ![Business document management workspace page](./media/BDM-Overview-TemplatesForAlice1.png)

3. On the **Configurator of access permissions** page, select **Access permissions setting**.
4. In the **Settings of access permissions to edit templates** dialog box, enable the **Apply configured access permissions** option.
5. Select **OK** to confirm that Business document management access permissions have been enabled.

    ![Configuration of Business document management access permissions page](./media/BDM-Overview-TemplatesAccess2.png)

6. Select **Add** to enter a new business role for which permissions to access Business document management templates must be configured.
7. In the **Security roles** dialog box, select the **Accounts receivable clerk** role and then select **OK** to confirm the role selection.
8. On the **Access permissions per tags of configurations** tab, select **New**.
9. In the **Tag type** field, select **Functional area**, and in the **ID** field, select **Invoicing**.
10. Select **Save** to store configured access permissions for the selected role.

    The current setting means that for any user who is assigned to the **Accounts receivable clerk** role and performing the duty, **Manage Business document templates** (AOT name **ERBDManageTemplates**), ER format configuration templates that have the **Invoicing** value for the **Functional area** tag will be available to edit in the Business document management workspace.

11. Switch the **Related information** pane from the right side of the current page. The **Related information** pane shows how the configured access permissions will be applied, including what ER configuration templates will be available for users that are assigned to the **Accounts receivable clerk** role.

    ![Configuration of Business document management access permissions page](./media/BDM-Overview-TemplatesAccess3.png)

12. On the **Access permissions per configurations** tab, select the **Add** option.
13. In the **Select configuration** dialog box, mark the **Intrastat report** ER format configuration.
14. Select **OK** to confirm the entry of the selected configurations and then select **Save** to store the configured access permissions for the selected role.

The current setting means that for any user assigned to the **Accounts receivable clerk** role and performing the duty, **Manage Business document templates** (AOT name **ERBDManageTemplates**), the following templates will be available to edit in the Business document management workspace:

- Templates that have the value, **Invoicing** for the **Functional area** tag.
- Templates from ER format configurations that are listed on the **Access permissions per configurations** tab (templates from the **Intrastat report** format configuration of the **Statutory reporting** domain in this example).

![Configuration of Business document management access permissions page](./media/BDM-Overview-TemplatesAccess4.png)

The following graphic shows what the Business document management workspace provides to a user assigned to the **Accounts receivable clerk** role. With the current Business document management access permissions setting, the user can edit business document templates from the **Invoicing** domain and the **Intrastat report** ER format configuration. Templates from the **Payments** domain are not accessible for the **Accounts receivable clerk** role.

![Business document management workspace page](./media/BDM-Overview-TemplatesForAlice2.png)

> [!NOTE]
> The **Access permissions per configurations** rules are stored by using the unique identification ID of an ER format configuration. This means that these rules will not be deleted when an ER configuration that refers to them are deleted. When you import deleted configurations back to this instance, these rules will refer to them again. There is no need to set up the rules again after the deleted configurations are imported again.

## Use Business document management to edit templates

Business users can access business document templates for editing in the Business document management workspace. Only the following users can access the Business document management workspace:

- Users assigned to the role, **System administrator**.
- Users assigned to any role that is configured to perform the duty, **Manage Business document templates** (AOT name **ERBDManageTemplates**).

Use the following procedure to edit free text invoice templates in the Business document management workspace. Before you complete this procedure, you must have completed all of the preceding procedures in this topic.

1. Sign in as a user with access to the Business document management workspace.
2. Open the Business document management workspace.


When the **Office-like UI experience for Business document management** feature in the **Feature management** workspace is turned off, the main grid of the **Business document management** workspace offers the following templates:

- Templates that are owned by your ER configurations provider. This is the provider that is currently marked as active in the ER workspace. For a selected template, you can select **Edit template** to either start or continue editing it.
- Templates that are owned by other ER configurations providers. For a selected template, you can select **New document** to create a copy of the template that is owned by your ER provider and start editing it.

![Business document management workspace page](./media/BDM-Overview-EditingTemplate1.png)

The **Template** tab presents the content of the selected template. Select the **Details** tab to review details of the selected template as well as details of an ER format configuration this template resides in. Notice that all of the templates have a status of **Published**, and contain no details in the **Revision** column. This means that these templates are not currently being edited.

When the **Office-like UI experience for Business document management** feature in the **Feature management** workspace is turned on, the main grid of the **Business document management** workspace offers templates that are owned by your ER configurations provider. This is the provider that is currently marked as active in the ER workspace. For a selected template, you can select the **Edit template** option to either start or continue editing it.

To start working with templates that are owned by other ER configurations providers. select the **New document** option to create a copy of it that is owned by your ER provider and start editing it. See [New document user interface
in Business document management](er-business-document-management-new-template-ui.md) for more.

### Initiate editing templates owned by your configuration provider

1. In the Business document management workspace, select the **Cheques printing format** template in the list.
2. Select the **Details** tab.

![Business document management workspace page](./media/BDM-Overview-EditingTemplate2.png)

The **Edit template** option is available for the selected template. This option is always available for a template in an ER format configuration that is owned by the active ER configuration provider (**Litware, Inc.** in this example). When **Edit template** is selected, the existing template from the draft version of the underlying ER format configuration will be available to edit.

### Initiate editing templates owned by other providers

1. In the Business document management workspace, select the document that you want to use as a template.

![Business document management workspace page](./media/BDM-Overview-EditingTemplate3.png)

3. Select **New document**, and in the **Title** field, change the title of the editable template if needed. The text will be used to name the ER format configuration that is automatically created. Note that the draft version of this configuration (**Customer FTI report (GER) Copy**) that will contain the edited template will automatically be marked to run this ER format for the current user. At the same time, the non-modified original template from the base ER format configuration will be used to run this ER format for any other user.
4. In the **Name** field, change the name of the first revision of the editable template that will be created automatically.
5. In the **Comment** field, change the comment for the automatically created revision of the editable template.
6. Select **OK** to confirm the start of the editing process

![Business document management workspace page](./media/BDM-Overview-EditingTemplate4.png)

The **New document** option is always available for a template in an ER format configuration provided by current and another provider (Microsoft in this example) that doesn't have any revision. The edited template will then be stored in a new ER format configuration that is automatically generated.

### Start editing a template

1. From the selected template, select **Edit document**.
2. In the **Name** field, change the name of the first revision of the editable template that will be created automatically.
3. In the **Comment** field, change the remark for the automatically created revision of the editable template.

    ![Business document management workspace page](./media/BDM-Overview-EditingTemplate5.png)

5. Select **OK** to confirm the start of the editing process.

The **BDM template editor** page will open. The selected template will be available for online editing by using Office 365.

![Business document management workspace page](./media/BDM-Overview-EditingLayout1.png)

### <a name="EditInOffice365">Edit a template in Office 365</a>

You can modify the template using Office 365. For example, in Office online, change the font of the field prompts in the template header from **Regular** to **Bold**. These changes are automatically stored in the editable template that is stored in the primary template's storage (by default, the Azure blob storage). This is configured for the ER framework.

![Business document management template editor page](./media/BDM-Overview-EditingLayout2.png)

### <a name="EditInOfficeDesktopApp">Edit a template in the Office desktop application</a>

> [!NOTE]
> This function is only available when the **SharePoint document type** parameter is properly configured. For more information, see [Configure parameters](#SetupBdmParameters).

1. Select the **Open in Desktop App** option to modify the template by using the functionality of the Office desktop application (Excel in this example). The editable template is copied from the permanent storage to the temporary storage configured in the Business document management parameters as a SharePoint folder.
2. Confirm that you want to open the template from the temporary file storage in the Office desktop Excel application.

    ![Business document management workspace page](./media/BDM-Overview-EditingLayout3.png)

3. Modify the template. For example, change the font of the fields prompts in the template header by updating color from **Black** to **Blue**.

    ![Business document management template editor page](./media/BDM-Overview-EditingLayout4.png)

4. Select **Save** in the Excel desktop application to store the template changes in the temporary storage.

    ![Business document management template editor page](./media/BDM-Overview-EditingLayout5.png)

5. Close the Excel desktop application.
6. Select **Sync stored copy** to synchronize the temporary template storage to the permanent template storage.

> [!NOTE]
> The copy of the editable template in the temporary file storage is kept for only the current session of template editing. When you finish this session by closing the **BDM template editor** page, this copy will be deleted. If you adjusted the template in the temporary file storage and did not select **Sync stored copy**, when you try to close the **BDM template editor** page, a message will ask whether you want to store introduced changes. Select **Yes** if you want to save your changes to the template in the permanent file location.

### Validate a template

1. On the **BDM template editor** page, select **Check for issues** to validate the modified template against the underlying ER format configuration. Follow the recommendations (if any) to align the template with the structure of the format from the base ER format configuration.
2. Select **Show format** to view the current structure of the format from the base ER format configuration that must be aligned with the editable template. 
3. Select **Hide format** to close the pane.

    ![BDM BDM template editor page](./media/BDM-Overview-EditingTemplate6.png)

4. Close the **BDM template editor** page.

The updated template is shown on the **Template** tab. Notice that the status of the edited template is now **Draft** and the current revision is no longer empty. This means that the process of this template's editing has been started.

![Business document management workspace page](./media/BDM-Overview-EditingTemplate5.png)

### Test the modified template 

1. In the application, change to the company, **USMF**.
2. Go to **Accounts receivable** \> **Invoices** \> **All free text invoices**.
3. Select the **FTI-00000002** invoice, and then select **Print management**.
4. Select the **Module - accounts receivable** \> **Documents** \> **Free text invoice** \> **Original document** level to specify the scope of invoices for processing.
5. In the **Report format** field, select the **Customer FTI report (GER) Copy** ER format for the specified document level.

    ![Print management setting page](./media/BDM-Overview-TestRun1.png)

6. Press **Escape** to close the current page.
7. Select **Print**, and then click **Selected**.
8. Download the document and open it using the Excel desktop application.

![Free text invoices page](./media/BDM-Overview-TestRun2.png)

The modified template is used to generate the free text invoice report for the selected item. To analyze how this report is affected by the changes that you introduced to the template, you can run this report in one application session right after you modified the template in another application session.

### Create an alternative template revision

1. Open the **BDM template editor** page and select the **Customer FTI report (GER) Copy** template.
2. On the **Revisions** tab, select **New**.
3. If needed, in the **Name** field, change the name of the second revision and base it on the currently active first revision.
4. If needed, in the **Comment** field, change the remark for the automatically created revision of the editable template.

    ![Business document management workspace page](./media/BDM-Overview-AddRevision.png)

    You created a new revision of your template that has been stored in the permanent template's storage. Now you can continue editing the template of the second revision that is currently selected as active.

5. Select the first revision and then select **Set active**. You can select another revision as active if at any time you want to return to that revision of the template.
6. Select the second revision, and then select **Delete**.
7. Select **OK** to confirm that you want to delete the selected revision. You can delete any of the non-active revisions when they are no longer needed.

### Delete a modified template

1. On the **BDM template editor** page, select the **Template** tab.
2. Select **Delete**.
3. If you select **OK** to confirm deletion, the **Customer FTI report (GER) Copy** ER format with the modified template will be deleted. Select **Cancel** to explore other options.

### Revoke changes of template

When you edit the template from an ER format that is owned by the current active provider, you will be offered the option to revoke changes introduced for the template.

![Business document management workspace page](./media/BDM-Overview-RevokeChanges.png)

1. On the **BDM template editor** page, select the **Template** tab.
2. Select **Undo**.
3. If you select **OK** to revoke the changes introduced for the template, the modified template will be replaced by the original template and all changes will be removed. When you revoke changes to the template, you will be able to delete the template. Select **Cancel** to explore other options.

### Publish a modified template
1. On the **BDM template editor** page, on the **Template** tab, select **Publish**.
2. If you select **OK** to confirm publishing, the draft version of the derived **Customer FTI report (GER) Copy** ER format that contains the modified template will be marked as completed. The modified template becomes available for other users. The completed versions of this ER format will keep only the last active revision of your template. Other revisions will be deleted. Select **Cancel** to explore other options.

## Frequently asked questions

#### I selected **Edit document**, but instead of opening the **BDM template editor** page in Finance and Operations, I have been sent to the Office 365 web page.
This is a known issue with the Office 365 redirection. This happens when you sign to Office 365 the first time. To work around this issue, select the **Back** button of your browser to navigate back.

#### I understand how to edit a template by using Office 365 in the first application session and how to use the template in the second application session adjusting the template to see how my changes affect the generated business document. Can I do this using the Office desktop application?
Yes, you can. In the first application session, select **Open in Desktop App**. Your template will be stored in the temporary file storage and opened in the Office desktop application. Next, complete the following steps to preview your template changes in the generated business document:

1. Make changes in the template by using the Office desktop application.
2. Select **Save** in the Office desktop application.
3. On the **BDM template editor** page of the first application session, select **Sync stored copy**.
4. Execute this template ER format in the second application session.

#### I get the error 'Value cannot be null. Parameter name: externalId' when I select **Open in Desktop App**. How do I work around this? 
Most likely you signed in to the current instance of the app of the Azure AD domain which differs from the Azure AD domain that was used to deploy this instance. Because the SharePoint service, which is used to store templates for making them available for editing by using the Office desktop applications, belongs to the same domain, we have no permissions to access the SharePoint service. To resolve this issue, sign in to the current instance using the credentials of a user with the correct Azure AD domain.

## Additional resources

[Electronic reporting (ER) overview](general-electronic-reporting.md)

[ER Design a configuration for generating reports in OPENXML format (November 2016)](tasks/er-design-reports-openxml-2016-11.md)

[Design ER configurations to generate reports in Word format](tasks/er-design-configuration-word-2016-11.md)

[Embed images and shapes in documents that you generate by using ER](electronic-reporting-embed-images-shapes.md)

[Configure Electronic reporting (ER) to pull data into Power BI](general-electronic-reporting-report-configuration-get-data-powerbi.md)

