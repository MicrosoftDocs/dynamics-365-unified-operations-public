---
# required metadata

title: India GST configuration
description: [Full description that appears in the search results. Often the first paragraph of your topic.]
author: ShylaThompson
manager: AnnBe
ms.date: 05/09/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form:  
audience: IT Pro
# ms.devlang: 
# ms.reviewer: shylaw
# ms.search.scope: 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.assetid: d3426cb4-476a-46ae-9a86-4f68173a2dd6
ms.search.region: India
# ms.search.industry: 
ms.author: shylaw
# ms.search.validFrom: 
# ms.dyn365.ops.version: 
---

# India GST configuration

[!include[banner](../includes/banner.md)]

Before you can use India GST for Microsoft Dynamics AX, you must complete the prerequisite steps covered in this topic.

> ![NOTE]
> If you don’t plan to review or extend the Microsoft India GST configurations, you can skip to...

## Get a Dynamics 365 for Operations Trial License

For more information, see [Sign up for a preview subscription](../dynamics365/operations/dev-itpro/dev-tools/sign-up-preview-subscription).

## Deploy the GST configuration environment 
You can deploy the configuration environment on Azure, or you can deploy it on a local box.

### Option 1: Deploy the configuration environment on Azure

1. Procure a Microsoft Azure subscription. For more information, visit [Microsoft Azure](https://azure.microsoft.com/).
2. Create the Lifecycle Services project for Dynamics 365 for Finance and Operations, Enterprise Edition. 
    1. Go to the Office 365 admin center. For more information, see [About the Office 365 admin center](https://support.office.com/en-us/article/About-the-Office-365-admin-center-758befc4-0888-4009-9f14-0d147402fd23). 
    2. Click **Admin centers** /> **Dynamics 365 for operations** to open LCS.
3. Create a new project in LCS using the following information.
    - Project purpose: Migrate, create solutions, and learn Dynamics 365 for Operations
    - Name: /<any name/>
    - Product name: Microsoft Dynamics 365 for Operations
    - Product version: Microsoft Dynamcis 365 for Operations
    - Industry: Other
    - Methodology: Learn Development in the New Dynamics AX
    - Import roles and users from existing LCS project: No
 4. Create an Azure connector when you are prompted to. You'll be asked to enter your Name, Azure subscription ID, and Azure subscription AAD Tenant Domain (or ID). Be sure to select "yes" for the **Configure to use Azure Resource Manager (ARM)** option and follow the [ARM onboarding instructions](../dynamics365/operations/dev-itpro/deployment/arm-onboarding) to add the required Access control (IAM) to your Azure subscription.
 5. Back in LCS, Download the management certificate for LCS and then click **Next**.
 6. Go to the [Azure portal](https://manage.windowsazure.com) and upload the management certificate that you downloaded in the previous step. 
    > ![NOTE]
    > This is a different website from Azure Portal which you usually used to manage your Azure Subscription. The “settings” is in the bottom of the left list pane of the page.
 7. Choose a data center near you.
 8. On your LCS dashboard, scroll until you see the **Environments** section and then click **+** to set up a new environment.
 9. Select **Azure** to create your configuration environment on Azure.
 10. Select **DevTest** for the topology to deploy.
 11. Select the environment with **Release 1611** in the name.
 12. Enter a name for the environment.
 13. Set the Virtual machine Build instance to be **0**. The GST configuration environment doesn't require a build machine.
 14. 
 
  

  
### Option 2: Download the GST Configuration VHD to run on a local server.
