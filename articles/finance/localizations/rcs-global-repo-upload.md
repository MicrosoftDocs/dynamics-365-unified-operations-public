---
# required metadata

title: Create Electronic reporting configurations in RCS and then upload to Global repository 
description: This topic describes how to create an ER configuration in RCS and upload it to the RCS/Global repository.
author: JaneA07      
manager: AnnBe
ms.date: 05/05/2020
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

# Create Electronic reporting configurations in RCS and then upload to Global repository 

[!include [banner](../includes/banner.md)]

You can use Regulatory Configuration Services (RCS) to design Electronic reporting (ER) configurations and publish them to use within your organization.

The following steps explain how a user in the System Administrator or Electronic Reporting Developer role can create a derived version of an ER configuration that has been configured in an RCS instance and upload it to the Global repository. To complete these steps, you must first complete the following:

- Access an RCS instance
- Create an active configuration provider. For more infofrmation, see [Create configuration providers and mark them as active](../../fin-ops-core/dev-itpro/analytics/tasks/er-configuration-provider-mark-it-active-2016-11.md).

1. In a Dynamics 365 Finance and Operations app, go to **Organization administration** > **Workspaces** > **Electronic reporting**.
2. If you have no RCS environment provisioned to your company, select **Regulatory services – Configuration external** and follow the instructions to provision an RCS environment for your organization.

> [!NOTE]
> If an RCS environment has been already provisioned to your company, use the page URLs to access it by selecting the sign in option.

## Create a derived version of a configuration in RCS

1. Go to the **Electronic reporting** workspace, and verify that you have an active configuration provider for your organization. 
2. Select **Reporting configurations**.
3. Select the configuration from which you want to derive a new version. You can use the filter field above the tree to narrow your search.
4. Select **+Create configuration** > **Derive from Name**.
5. Enter a name and description, and then select **Create configuration** to create a new derived version.
6. Select your newly derived configuration, add a version description, and then select **OK**. This will change the status of the configuration to **Complete**.

![New version of config in RCS](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/Janeaug_RCSdocs/articles/finance/localizations/media/RCS_CompleteConfig.JPG)

> [!NOTE]
> When the configuration status is changed, you might get a validation error related to the **connected applications‘**. You can turn off this validation in the **Configuration/User parameters** by setting **Skip validation at configuration’s status change and rebase** to **Yes**.

## Upload to the Global repository
To share a new or derived configuration that you have created with your organization, you can upload the configuration to the Global repository.

1. Select the completed version of the configuration, and then select **Upload into repository**.
2. Select **Global (Microsoft)**, and then click **Upload**.


![Upload to Global repo options](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/Janeaug_RCSdocs/articles/finance/localizations/media/RCS_Upload_to_GlobalRepo_options.JPG)

3. On the confirmation/action message, select **Yes**. 
4. If needed, update the version description and then select **OK**. 

The configuration is updated to **Share** and the configuration is uploaded to the Global repository where it is available to be:

  - Imported into your Dynamics 365 instance. For more information, see[(ER)Import configurations from RCS](../../fin-ops-core/dev-itpro/analytics/tasks/import-configuration-rcs.md)
  - Shared with a 3rd party or external organization

![Derived Intrastat Contoso version in Global repo](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/Janeaug_RCSdocs/articles/finance/localizations/media/RCS_Config_upload_GlobalRepo.JPG)



