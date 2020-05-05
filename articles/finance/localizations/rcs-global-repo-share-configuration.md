---
# required metadata

title: Create Electronic reporting configurations in RCS and upload to the Global repository
description: This topic describes how to directly share configurations in the RCS/Global repository with external organizations.
author: JaneA07      
manager: AnnBe
ms.date: 05/04/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: ERSolutionTable, ERWorkspace, RCS
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 97423
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: janeaug
ms.search.validFrom: 2020-02-01
ms.dyn365.ops.version: AX 10.0.9

---

# Create Electronic reporting configurations in RCS and upload to Global the repository 

[!include [banner](../includes/banner.md)]

You can use Regulatory Configuration Services (RCS) to share Electronic reporting (ER) configurations and then publish them to external organizations.

The following steps explain how a user in Microsoft RCS can share a version of an ER configuration that has been configured in an RCS instance with an external organization. To complete these steps, you must first complete the following:

- Access an RCS instance
- Create an active configuration provider. For more information, see [Create configuration providers and mark them as active](../../fin-ops-core/dev-itpro/analytics/er-configuration-provider-mark-it-active-2016-11.md)
- Create and upload a new version of an ER configuration. For more information, see [Create and upload a new version of an Electronic reporting (ER) configuration](rcs-global-repo-upload.md)

1. In a Dynamics 365 Finance and Operations app, go to **Organization administration** > **Workspaces** > **Electronic reporting**.
2. If no RCS environment is provisioned to your company, select **Regulatory services – Configuration** and follow the instructions to provision an RCS environment for your organization.

> [!NOTE]
> If an RCS environment has been already provisioned to your company, use the page URL to access it by selecting the sign-in option.

## Check the configuration that you want to share 
Complete the following steps to verify that the configuration that you want to share is already uploaded to Global repository.

1. Open the **Electronic reporting** workspace and select **Repositories** for your configuration provides. 

![Open the repository for your Configuration provider](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/Janeaug_RCSdocs/articles/finance/localizations/media/1_RCS_Repo_for_config_provider.JPG)

2. Select **Global repository** > **Open**.
3. Search for the configuration that you want to share. You can use the filter field to narrow your search.
If you can't find the configuration in the global repository, follow the steps in the topic, [Create and upload a new version of an Electronic reporting (ER) configuration](rcs-global-repo-upload.md)

## Share ER configurations with external organizations

After a configuration has been created under your configuration provider, you can directly share it with external organizations by selecting **Share with** on the **Global repository** page.
1. In the **Electronic reporting** workspace, select **Repositories** for your configuration provider.
2. Select **Global repository** > **Open**. 
3. Select the configuration that you want to share. 
4. Go to **Shared with**, and select **+Organization**.

![Go to ‘Share with’ and click +Organization](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/Janeaug_RCSdocs/articles/finance/localizations/media/1_RCS_Repo_for_Share_with_org.JPG)

5. Enter the parameters domain name for the external organization and then select **OK**.

![Enter organization domain name and click ‘Share’](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/Janeaug_RCSdocs/articles/finance/localizations/media/1_RCS_Repo_for_Share_with_form.JPG)

The configuration is shared with the external organization and is available for them in the Global repository where it can be imported for use into their RCS or the instance of their Finance and Operations apps.

![Configuration is ‘shared with’](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/Janeaug_RCSdocs/articles/finance/localizations/media/1_RCS_Repo_for_Share_with_test.com)


