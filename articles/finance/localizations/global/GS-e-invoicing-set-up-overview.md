---
title: Electronic invoicing setup
description: This article provides an overview of the process for setting up and configuring Electronic invoicing.
author: ilikond
ms.date: 01/29/2024
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: ilikond
ms.search.validFrom: 2024-01-29
ms.dyn365.ops.version: 10.0.39
ms.custom: 
ms.assetid: 
ms.search.form: 
---

# Electronic invoicing setup

[!include [banner](../../includes/banner.md)]

The article provides an overview of the process for setting up and configuring Electronic invoicing. You must complete the setup steps in the order that is specified here. If a step is mandatory, but you skip it, the functionality won't work correctly, and multiple failures will occur during subsequent steps or when you use the functionality. 

## Install the add-in for Electronic invoicing microservices

The Electronic Invoicing service is a set of microservices that is hosted in Microsoft datacenters. By default, customers of Dynamics 365 Finance and Dynamics 365 Supply Chain Management don't have access to the Electronic Invoicing service. You must install it as an add-in in Microsoft Dynamics Lifecycle Services (LCS). When you install the add-in, your Finance or Supply Chain Management environment is registered in the register of applications that are allowed to connect to the Electronic Invoicing service.

To register an environment, follow these steps.

1. Sign in to your LCS account.
2. On the project dashboard, select an LCS project.
2. In the project, on the **Environments** dashboard, select your deployed environment. The environment that you select must be running.
3. On the **Power Platform Integration** tab, in the **Environment add-ins** section, select **Install a new add-in**.
4. Select **Electronic Invoicing**.
5. In the **AAD application ID** field, enter the fixed value **091c98b0-a1c9-4b02-b62c-7753395ccabe**. This value is always fixed. Make sure that you enter only a globally unique identifier (GUID). Don't include any other symbols, such as spaces, commas, periods, or quotation marks.
6. In the **AAD tenant ID** field, enter the Azure Active Directory tenant ID of your Azure subscription account.
7. Review the terms and conditions, and then select the checkbox.
8. Select **Install**. After a few minutes, the status should change from **Installing** to **Installed**. You might have to refresh the page to see this change.

> [!NOTE]
> Companies usually have several Finance or Supply Chain Management environments. These environments include production environments, User Acceptance Test (UAT) environments, and development (sandbox) environments. You must complete the preceding procedure for all environments that you want to connect to Electronic invoicing.

## Configure the Azure resources for Electronic invoicing

Set up the Azure resources that Electronic invoicing requires to do its work. For more information, see [Set up Azure resources for Electronic invoicing](e-invoicing-set-up-azure-resources.md).

## Configure Globalization Studio for Electronic invoicing

Make sure that the Globalization Studio is available in the system. For more information, see [Globalization Studio](globalization-studio-overview.md)

To activate Electronic invoicing within the Globalization Studio, in the **Feature management** workspace, enable the following features. For more information, see [Feature management overview](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

 - *Globalization features*
 
 - *E-invoicing service workspace designer*
 
 - *Enable Globalization feature setup for Tax Calculation Service*
 
 - *Electronic reporting globalization feature Key Vault parameters*
 
 - *Electronic reporting globalization feature JSON import/export*
 
 - *Dataverse repository*

## Configure Globalization features

Different scenarios for processing electronic documents are implemented via Globalization features. A Globalization feature is a set of components that define the rules for data transformation and further processing of electronic documents such as sending them to or receiving them from external channels. You can use Globalization features provided by Microsoft or create your own ones. For more information about how to work with Globalization features, see [Work with Globalization features](GS-e-invoicing-working-globalization-features.md).

> [!NOTE]
> If your scenarios require integration with email or SharePoint to process inbound electronic documents, see [Processing incoming electronic documents](e-invoicing-process-incoming-electronic-documents.md) for information about how to set up and use those channels.

## Configure Dynamics 365 Finance and Dynamics 365 Supply Chain Management

Set up Dynamics 365 Finance and Dynamics 365 Supply Chain Management parameters related to Electronic invoicing. For more information, see [Set up Electronic invoicing parameters](GS-e-invoicing-set-up-parameters.md)

