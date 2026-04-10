---
title: Manage ER model mapping in separate ER configurations
description: This article describes how to manage Electronic reporting (ER) model mappings in separate ER configurations.
author: kfend
ms.date: 02/25/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: AX 7.0.0
---

# Manage ER model mapping in separate ER configurations

[!include [banner](../../includes/banner.md)]

The following steps explain how a user assigned to the System administrator or Electronic reporting developer role can manage Electronic reporting (ER) model mappings in separate ER configurations. In this task guide, you create required ER configurations for the sample company, Litware, Inc. To complete this task guide, you must first complete the steps in the [Create configuration providers and mark them as active](er-configuration-provider-mark-it-active-2016-11.md) article.

Because ER configurations are shared among companies, you can complete this task guide using the company data set of your choice. The functionality for this task guide is available if you install one of the following hotfixes: https://fix.lcs.dynamics.com/Issue/Resolved?kb=4012872 for the Dynamics AX 7.0 version or https://fix.lcs.dynamics.com/Issue/Resolved?kb=4012871 for the Dynamics 365 for Operations version.

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
    * Verify that the configuration provider for the sample company Litware, Inc. is available and marked as active. If you don't see this configuration provider, you must first complete the steps in the task guide, Create a configuration provider, and mark it as active.   
   
## Add a new ER model configuration

1. Select **Reporting configurations**.
    * Add a new model configuration. The name must be unique in the configurations tree.  
1. Select **Create configuration** to open the form.
1. In the **Name** field, type *Sample data model*.
    * Sample data model  
1. Select **Create configuration**.
1. Select **Designer**.
1. Select **New** to open the form.
1. In the **Name** field, type *Root*.
    * Root  
1. Select **Add**.
1. Select **New** to open the form.
1. In the **Name** field, type *Company*.
    * Company  
1. Select **Add**.
1. In the **Description** field, enter the text, *Description of the legal entity or company in which a user logged at run-time.* 
    * Description of the legal entity or company in which a user logged at run-time.  
1. Select **Root reference**.
1. Select **OK**.
1. Select **Save**.
1. Close the page.
1. Select **Change status**.
1. Select **Complete**.
1. Select **OK**.

## Add a new ER model-mapping configuration

1. Select **Create configuration** to open the form.
1. In the **New** field, enter *Model Mapping based on data model Sample data model*.
1. In the **Name** field, type *Sample mapping*.
    * Sample mapping  
1. Select **Create configuration**.
1. Expand the **Prerequisites** section.
    * The **Implementations prerequisites** group is added automatically. The group contains the prerequisite component that refers to the parent data model configuration and is marked as **Implementation**. This status means that the **Sample mapping** model-mapping configuration is considered the implementation of the data model, **Sample data model**. Therefore, this component forces ER to download the model-mapping configuration, **Sample mapping** from an ER repository when the model configuration, **Sample data model**, is downloaded.   
1. Select **Designer**.
    * The created model-mapping configuration contains a new blank mapping with the same name as the created configuration. When a selected parent model configuration contains model mappings, they are copied to a new model-mapping configuration.   
1. Select **Designer**.
1. In the tree, select *Dynamics 365 for Operations\Table*.
1. Select **Add root**.
1. In the **Name** field, type *Company*.
    * Company  
1. In the **Table** field, type *CompanyInfo*.
    * CompanyInfo  
1. Select **OK**.
1. In the tree, expand *Company*.
1. In the tree, expand *Company\find()*.
1. In the tree, select *Company\find()\Name*.
1. Select **Bind**.
1. Select **Save**.
1. Close the page.
1. Close the page.
1. On the Action Pane, select **Configurations**.
1. Select **User parameters**.
1. Select **Yes** in the **Run settings** field.
1. Select **OK**.
1. Select **Edit**.
1. Select **Yes** in the **Run Draft** field.

## Add a new ER format configuration

1. In the tree, select **Sample data model**.
1. Select **Create configuration** to open the form.
1. In the **New** field, enter `Format based on data model Sample data model`.
1. In the **Name** field, type `Sample format`.
    * Sample format  
1. Select **Create configuration**.
1. Select **Designer**.
1. Select **Add root** to open the **Drop** dialog.
1. In the tree, select `Text\String`.
1. Select **OK**.
1. Select the **Mapping** tab.
1. In the tree, expand `model`.
1. In the tree, select `model\Company`.
1. Select **Bind**.
1. Select **Save**.
1. Close the page.
    * Run the draft version of the created format for testing purposes.  
1. Select **Run**.
    * On the **Versions** FastTab, select **Run**.  
1. Select **OK**.
    * Review the output that contains the name of the company in which the user who is running this format configuration is logged into. The created model-mapping configuration is used by this format configuration because there's only one configuration available that contains required model mappings.   
   
## Add alternative ER model-mapping configuration

1. In the tree, select **Sample data model**.
1. Select **Create configuration** to open the form.
1. In the **New** field, enter *Model Mapping based on data model Sample data model*.
1. In the **Name** field, type *Sample mapping (alternative)*.
    * Sample mapping (alternative)  
1. Select **Create configuration**.
1. Select **Designer**.
1. Select **Designer**.
1. In the tree, select *Dynamics 365 for Operations\Table*.
1. Select **Add root**.
1. In the **Name** field, type *Company*.
    * Company  
1. In the **Table** field, type *CompanyInfo*.
    * CompanyInfo  
1. Select **OK**.
1. Select **Edit**.
1. In the tree, select **String\CONCATENATE**.
1. Select **Add function**.
1. In the tree, expand *Company*.
1. In the tree, expand *Company\find()*.
1. In the tree, select *Company\find()\Name*.
1. Select **Add data source**.
1. In the **Formula** field, type a value.
    * `CONCATENATE(Company.'find()'.Name, ";",`  
1. In the tree, select **Company\find()\Company(DataArea)**.
1. Select **Add data source**.
1. In the **Formula** field, type a value.
    * `CONCATENATE(Company.'find()'.Name, ";", Company.'find()'.DataArea)`  
1. Select **Save**.
1. Close the page.
1. Select **Save**.
1. Close the page.
1. Close the page.
1. Select **Yes** in the **Run Draft** field.

## Use an existing ER model-mapping configuration

1. In the tree, select `Sample data model\Sample format`.
1. Select **Run**.
    * You can't run the selected draft version of the ER format configuration because more than one model-mapping configuration exists for the undefined data model that is selected as the data source of the running ER format.      
    * Next, you need to define the alternative model-mapping configuration as the one from which model mappings are used as data sources for running ER format.   
1. In the tree, select `Sample data model\Sample mapping (alternative)`.
1. Select **Yes** in the **Default for model-mapping** field.
1. In the tree, select `Sample data model\Sample format`.
1. Select **Run**.
1. Select **OK**.
    * This format configuration uses the default model-mapping configuration to generate the electronic document. The created output contains the company code.  



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
