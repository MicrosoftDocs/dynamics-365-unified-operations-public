---
title: Globalization features
description: This article explains the features of Globalization Studio workspace
author: filatovm
ms.author: filatovm
ms.topic: conceptual 
ms.date: 01/29/2023
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak

---

# Globalization features

You can use Globalization Studio to create a Globalization feature that can be used in Globalization services: Electronic Invoicing and Tax Calculation. Globalization Studio lets you perform these tasks:

- Define related components of a feature.
- Manage the feature lifecycle through a feature's status.

To use a Globalization feature, you must first import it from Dataverse repository and create your own version of it. There are two ways to add Globalization features:

- Add a derived feature that is based on an existing feature that has been published or shared.
- Add a new feature that you've created from scratch.

## Feature component overview

Globalization features have several components:

- **Version**  – This component supports feature lifecycle management and lets users manage the status for different versions of the feature.
- **Configurations**  – This component lets users manage, view, and edit related ER formats and format mappings.
- **Setups**  – This component lets users of Globalization services, such as an e-invoicing service, manage the setup of the related feature version. Therefore, it supports the flexible construction of communication and responses rules.

See more details on Globalization features setup and usage in Electronic Invoicing and Tax Calculation Service articles.

## Import Electronic reporting (ER) configurations from Dataverse

### Set up integration with Dataverse and import Globalization solution

In order to use this functionality you should have Dataverse environment connected to your Finance environment. To validate this:

- Go to environment in
**Power Platform admin center**
- Click **Settings**
- Go to **Features** under **Product** tab
- Set **Enable Finance and Operations User Impersonation in Dataverse** to **On,** if it is not and click **Save**

After this, you can **import** Globalization Solution by the following steps:

- Navigate to [solution AppSource link](https://appsource.microsoft.com/en-us/product/dynamics-crm/mscrm.d365-globalizationartifacts-preview?flightCodes=a0bc3ba0711a4558bf3a2932a66dc11d)
- Click **Get it now**
- Fill out required data
- Select an environment and click **Install**

### Import configurations from Dataverse

New type of repository for getting ER configurations in Dynamics 365 Finance is added: Dataverse configuration repository. It enables the same user interface as for Global repo, allowing import of single and filtered configurations.

#### Open configurations repository

1. Sign in to the Dynamics 365 Finance application using one of the following roles:

- Electronic reporting developer

- Electronic reporting functional consultant

- System administrator

1. Go to  **Organization administration \> Workspaces \> Globalization studio**.
2. In the  **Configuration providers**  section, select the  **Microsoft**  tile.
3. On the  **Microsoft**  tile, select  **Repositories**.

![](RackMultipart20240123-1-zm1783_html_80bd147c81bdcb31.png)

1. On the  **Configuration repositories**  page, in the grid, select the existing repository of the  **Dataverse**  type. If this repository doesn't appear in the grid, follow these steps:

  1. Select  **Add**  to add a new repository.

  1. Select  **Dataverse**  as the repository type, and then select  **Create repository**.

  1. If prompted, follow the authorization instructions.

  1. Enter a name and description for the repository and then select  **OK**  to confirm the new repository entry.

  1. In the grid, select the new repository of the **Dataverse**  type.

1. Select  **Open**  to view the list of ER configurations for the selected repository.
