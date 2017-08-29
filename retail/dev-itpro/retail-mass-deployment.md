---
# required metadata

title: Mass deployment of Retail self-service components
description: [Full description that appears in the search results. Often the first paragraph of your topic.]
author: jashanno
manager: AnnBe
ms.date: 08/29/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
# ms.reviewer: sericks
ms.search.scope: Retail, Operations 
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global 
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: jashanno
ms.search.validFrom: 2017-09-31]
ms.dyn365.ops.version: Application update 3
---

# Mass deployment of Retail self-service components

[!include[banner](../includes/banner.md)]

This topic explains how you can use self-service to configure Retail Store Scale Unit in Retail headquarters, download it, and install it on one or more computers in a brick-and-mortar store. Retail Store Scale Unit combines the Retail channel database, Retail Async Client, Retail Server, and Retail Cloud POS components. A Microsoft Dynamics 365 for Retail environment already provides these components. However, you can now configure them so that they work locally in a store, in either a single-computer setup (the default option) or a multiple-computer setup. This topic also explains how to uninstall and troubleshoot Retail Store Scale Unit.

## Before you begin
> [!IMPORTANT]
> To help maintain a high level of security across the company, we strongly recommend that you create a new application ID (client ID) and secret for each retail store that is created. This step requires a new Web App.

1. Generate a Microsoft Azure Active Directory (Azure AD) app registration to create an application ID (client ID) and secret. For instructions, see [Create an Azure Active Directory Application](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-create-service-principal-portal#create-an-azure-active-directory-application). This article reviews Azure user permissions and requirements, and explains how to generate an app registration.
2. After an application ID (client ID) and secret are created for Retail Store Scale Unit, the client ID must be accepted in Retail. Go to **System administration** &gt; **Setup** &gt; **Azure Active Directory applications**. Enter the application ID (client ID) in the **Client ID** column, enter descriptive text in the **Name** column, and enter **RetailServiceAccount** in the **User ID** column.

## Configure a new Retail Store Scale Unit
To create a functioning Retail Store Scale Unit, complete the procedures in all sections of this topic through the "Running the Retail Store Scale Unit installer" section.

1. Use your Azure AD credentials to sign in to the Retail headquarters or Retail trial.
2. On the **Welcome** page, use the menu in the upper left to go to **Retail** &gt; **Headquarters setup** &gt; **Retail scheduler** &gt; **Channel database**.
3. On the **Channel database** page, on the Action Pane, select **New**.
4. In the **Channel database ID** field, enter a unique value.
5. In the **Channel data group** field, select the **Default** option.

    > [!NOTE]
    > You can select any other option that you've already created.

6. In the **Type** field, leave the default value (**Channel database**) selected.
7. You can leave the **Data sync interval** field blank.
