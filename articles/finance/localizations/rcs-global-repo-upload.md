---
# required metadata

title: RCS Global repository upload
description: This topic describes creation of ER configuration in RCS and how to upload to the RCS/Global repository
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

You can use Regulatory Configuration Services (RCS) to design Electronic reporting (ER) configurations and publish them to use within your organization

The following steps explain how a user in the System Administrator or Electronic Reporting Developer role can create and upload a new version of an Electronic reporting (ER) configuration from Microsoft Regulatory Configuration Services (RCS). 
In this example, you will create a derived version of an ER configuration that has been configured in an RCS instance and upload it to Global repository. To complete these steps, you must first complete the steps related to:
- Access to an RCS instance
- Creation of a configuration provider that is active - see [Create configuration providers and mark them as active](er-configuration-provider-mark-it-active-2016-11.md)

**From Dynamics F&O** you can take the following actions:
- Go to **Organization administration > Workspaces > Electronic reporting.**
- If you have no RCS environment provisioned to your company, you can click Regulatory services – Configuration external link and follow the instructions to provision an RCS environment for your organization.

**Note**: If RCS environment has been already provisioned to your company, use the page URLs to access it by selecting the sign in option.

**Create derived version of configuration in RCS**
1.	Click Electronic reporting workspace
2.	Check that you have that you have a Configuration provider for your organization, for e.g. here we will use Contoso and make sure the provider is marked as Active
3.	Click Reporting configurations 
4.	Select configuration that you want to derive a new version of, for this example we will use Intrastat (DE). 
**Tip** you can find this by using filter field above the Configuration tree
5.	Select +Create configuration, check ‘Derive from Name’ radio button, complete fields Name (for e.g. Intrastat (DE) Contoso) and Description, then click ‘Create configuration’ to create a new derived version
6.	Select your newly derived configuration and Change status to complete by adding version description and clicking ok

**Note** you might get a validation error related ‘connected applications‘ on changing configuration status. You can turn off this validation in Configuration/User parameters – Skip validation at configuration’s status change and rebase. Slide to parameter to ‘Yes’ and click Ok

**Upload to Global repository**
To share configuration that you have created (either new or derived) with your organization you can upload the configuration to the Global repository

1.	Selected Completed version of the configuration
2.	Click Upload into repository
3.	Select Configuration repository – Global (Microsoft), click select
4.	Click Yes on the confirmation/action message 
5.	Update description for the version (if needed), click Ok
6.	Configuration status is updated to ‘Share’ and has been uploaded to the Global repository where it is available to be:
i.	Imported into Dynamics F&O (see topic (ER) Import configurations from RCS), or
ii.	Shared with 3rd party/external organizations

**Related screen shots:**

Create new version of format configuration by deriving from an existing format and complete:

![New version of config in RCS](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/Janeaug_RCSdocs/articles/finance/localizations/media/RCS_CompleteConfig.JPG)

Upload to Global repository:

![Upload to Global repo](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/Janeaug_RCSdocs/articles/finance/localizations/media/RCS_Upload_to_GlobalRepo.JPG)

![Upload to Global repo options](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/Janeaug_RCSdocs/articles/finance/localizations/media/RCS_Upload_to_GlobalRepo_options.JPG)

Derived Intrastat Contoso version successfully uploaded to Global repository:

![Derived Intrastat Contoso version in Global repo](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/Janeaug_RCSdocs/articles/finance/localizations/media/RCS_Config_upload_GlobalRepo.JPG)



