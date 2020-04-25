---
# required metadata

title: RCS Global repository sharing
description: This topic describes how to share configuration in RCS/Global repository direct with external organizations
author: JaneA07      
manager: AnnBe
ms.date: 04/24/2020
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

# Regulatory Configuration Services (RCS): Create Electronic reporting (ER) configurations in RCS and upload to Global repository 

[!include [banner](../includes/banner.md)]

You can use Regulatory Configuration Services (RCS) to share Electronic reporting (ER) configurations and publish them to external organizations.

The following steps explain how a user in Microsoft Regulatory Configuration Services (RCS) can share a version of an Electronic reporting (ER) configuration. 

In this example, you will share a version of an ER configuration that has been configured in an RCS instance with an external organization. To complete these steps, you must first complete the steps related to:

- Access to an RCS instance
- Creation of a configuration provider that is active - see [Create configuration providers and mark them as active](er-configuration-provider-mark-it-active-2016-11.md)
- Create and upload a new version of an Electronic reporting (ER) configuration - see [Create and upload a new version of an Electronic reporting (ER) configuration](rcs-global-repo-upload.md)

**From Dynamics F&O** you can take the following actions:
- Go to **Organization administration > Workspaces > Electronic reporting.**
- If you have no RCS environment provisioned to your company, you can click Regulatory services – Configuration external link and follow the instructions to provision an RCS environment for your organization.

**Note**: If RCS environment has been already provisioned to your company, use the page URLs to access it by selecting the sign in option.

**Check the configuration that you want to share is already uploaded to Global repository**

1.	Click Electronic reporting workspace
2.	Click Repositories for your Configuration provider
3.	Select ‘Global repository’ click Open 
4.	Search for the configuration that you want to share - Tip you can find this by using filter field
If you cannot find the configuration in the global repository than you can follow the steps here - [Create and upload a new version of an Electronic reporting (ER) configuration](rcs-global-repo-upload.md)

**Share created Electronic reporting (ER) configurations with external / 3rd party organization**

Once a configuration has been created under your Configuration provider you can easily share it with external / 3rd party organization directly by utilizing the ‘Share with’ functionality on the Global repository form
1.	Click Electronic reporting workspace
2.	Click Repositories for your Configuration provider
3.	Select ‘Global repository’ click Open 
4.	Select the configuration that you want to share, in this example we will use the format configuration we created previously (Intrastat (DE) Contoso). Tip you can find this by using filter field
5.	Go to ‘Shared with’ and click +Organization
6.	Enter parameters domain name for external organization and click Ok
7.	Configuration is ‘Shared with’ the organization and is available for them in the Global repository where it can be imported for use either into their RCS or F&O instance

**Related screen shots:**

Open the repository for your Configuration provider:

![Open the repository for your Configuration provider](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/Janeaug_RCSdocs/articles/finance/localizations/media/1_RCS_Repo_for_config_provider.JPG)

Go to ‘Share with’ and click +Organization:

![Go to ‘Share with’ and click +Organization](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/Janeaug_RCSdocs/articles/finance/localizations/media/1_RCS_Repo_for_Share_with_org.JPG)

Enter organization domain name and click ‘Share’:

![Enter organization domain name and click ‘Share’](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/Janeaug_RCSdocs/articles/finance/localizations/media/1_RCS_Repo_for_Share_with_form.JPG)

Configuration is ‘shared with’ the organization and is available for them to import and use in the Global repository:

![Configuration is ‘shared with’](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/Janeaug_RCSdocs/articles/finance/localizations/media/1_RCS_Repo_for_Share_with_test.com)


