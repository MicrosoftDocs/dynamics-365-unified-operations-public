---
title: Access application metadata by using connected applications
description: The steps in this article explain how a Regulatory configuration service user can design a new Electronic reporting model mapping by using metadata.
author: kfend
ms.date: 04/10/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2019-06-28
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: 
---

# Access application metadata by using connected applications

[!include [banner](../../includes/banner.md)]

The following steps explain how a Regulatory configuration service (RCS) user in the System Administrator or Electronic Reporting Developer role can design a new Electronic reporting (ER) model mapping by using metadata in finance and operations. The RCS connected application accesses application metadata online. You configure a sample ER model mapping to access foreign trade transactions. To complete these steps, in RCS you must first complete the steps in the article, [Create configuration providers and mark them as active](er-configuration-provider-mark-it-active-2016-11.md). If you didn't complete the steps in the article, [Access application metadata by using ER configuration](access-application-metadata-er-configuration.md), download the [Electronic reporting examples](https://download.microsoft.com/download/0/4/e/04e13839-e423-442b-a6c2-dd35b1045c2d/Dynamics%20365%20for%20Finance%20and%20Operations%208.1%20Electronic%20reporting%20task%20guides.zip) and save the following ER configurations: Foreign trade metadata.xml, Foreign trade model.xml, and Foreign trade mapping.xml, and then complete the steps in the procedure.

## Prerequisites

1. Go to **All workspaces** > **Electronic reporting**.
1. Make sure that the configuration provider for the sample company, Litware, Inc., is available and marked as **Active**. If you don't see this configuration provider, complete the steps in the procedure [Create configuration providers and mark them as active](er-configuration-provider-mark-it-active-2016-11.md).

## Get required ER configurations

1. Select **Reporting configurations**.
1. If you already completed the steps in the [Access application metadata by using ER configuration](access-application-metadata-er-configuration.md) procedure, you already have all necessary ER configurations (foreign trade metadata, model, and mapping configurations) in the current RCS instance. You can skip all the remaining steps of this sub-task.
1. Select **Exchange**.
1. Select **Load from XML file**.
1. Select **Browse** and select the **Foreign trade metadata.xml** file.
1. Select **OK**.
1. Select **Exchange**.
1. Select **Load from XML file**.
1. Select **Browse** and select the **Foreign trade model.xml** file.
1. Select **OK**.
1. Select **Exchange**.
1. Select **Load from XML file**.
1. Select **Browse** and select the **Foreign trade mapping.xml** file.
1. Select **OK**.

## Register a connected application

1. Close the page.
1. Close the page.
1. Go to **All workspaces** > **Electronic reporting**.
1. Select **Connected applications**.
1. Make sure that the configured application is Azure based and accessible for the current RCS user. The current RCS user must also have access to the selected application and be registered as a user of this application with a role that gives them privileges to access the application's metadata.
1. Select **New**.
1. In the **Name** field, type `MyConnectedApp`.
1. In the **Application** field, type `https:// mycompany.operations.dynamics.com`.
1. In the **Tenant** field, type `mycompany.onmicrosoft.com`.
1. Select **Save**.
1. When you check connection to configured application, on the **Connect to remote application** page select **Click here to connect to selected remote application** link.
1. Select **Check connection**.
1. Select **Close**.
1. When the connection validation succeeds, version and tenant details are updated for the configured application in the current grid.

## Review existing model mapping configuration

1. Close the page.
1. Select **Reporting configurations**.
1. In the tree, expand **Foreign trade model**.
1. In the tree, select **Foreign trade model\Foreign trade mapping**.
1. Expand the **Prerequisites** section.

    > [!NOTE]
    > Currently, this mapping refers to the metadata configuration. Application metadata from this configuration is offered while you design this model mapping.

1. Select **Designer**.
1. Select **Designer**.
1. In the tree, select **Dynamics 365 for Operations\Table records**.
1. Select **Add root**.
1. In the **Table** field, enter or select a value.

    > [!NOTE]
    > Currently, this mapping refers to the metadata configuration. Application metadata from this configuration is offered while you design this model mapping.

1. Select **Cancel**.
1. Close the page.
1. Close the page.

## Assign connected application to model mapping

1. Select **Edit**.
1. Select **MyConnectedApp** application.

    > [!NOTE]
    > Currently, this mapping refers to the metadata of the selected connected application. When the same mapping refers to metadata configuration and connected application at the same time, the metadata of the connected application is used.

1. Select **Designer**.
1. Select **Designer**.
1. In the tree, select **Dynamics 365 for Operations\Table records**.
1. Select **Add root**.
1. In the **Table** field, enter or select a value.

    > [!NOTE]
    > You see more than two application tables because this mapping uses all the metadata of the connected application that you assigned to it.

1. Select **Cancel**.
1. Select **Validate**.

    > [!NOTE]
    > You successfully bound elements of data model with items of data sources that are described by using details of metadata of the connected application that you assigned to this mapping.

1. Close the page.
1. Close the page.

To evaluate this model mapping by using metadata of a different version application, register another connected application, assign it to this model mapping, and validate it against new metadata.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
