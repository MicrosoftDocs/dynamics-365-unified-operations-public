---
title: Electronic invoicing configuration
description: Learn about the process for setting up and configuring Electronic invoicing, including an overview on installing the add-in for electronic invoicing microservices.
author: ilikond
ms.author: ikondratenko
ms.topic: overview
ms.date: 12/18/2025
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2024-01-29
ms.dyn365.ops.version: 10.0.39
---

# Electronic invoicing configuration

[!INCLUDE[banner](../../includes/banner.md)]

This article provides an overview of the process for setting up and configuring Electronic invoicing. Complete the setup steps in the order specified here. If you skip a mandatory step, the functionality won't work correctly, and multiple failures occur during subsequent steps or when you use the functionality.

## Install the add-in for Electronic invoicing microservices

The Electronic Invoicing service is a set of microservices that's hosted in Microsoft datacenters. By default, customers of Dynamics 365 Finance and Dynamics 365 Supply Chain Management don't have access to the Electronic Invoicing service. You must install it as an add-in in Microsoft Dynamics Lifecycle Services. When you install the add-in, you register your Finance or Supply Chain Management environment in the register of applications that are allowed to connect to the Electronic Invoicing service.

To register an environment, follow these steps.

1. Sign in to your Lifecycle Services account.
1. On the project dashboard, select a Lifecycle Services project.
1. In the project, on the **Environments** dashboard, select your deployed environment. The environment that you select must be running.
1. On the **Power Platform Integration** tab, in the **Environment add-ins** section, select **Install a new add-in**.
1. Select **Electronic Invoicing**.
1. In the **AAD application ID** field, enter the fixed value **091c98b0-a1c9-4b02-b62c-7753395ccabe**. This value is always fixed. Make sure that you enter only a globally unique identifier (GUID). Don't include any other symbols, such as spaces, commas, periods, or quotation marks.
1. In the **AAD tenant ID** field, enter the Microsoft Entra ID tenant ID of your Azure subscription account.
1. Review the terms and conditions, and then select the checkbox.
1. Select **Install**. After a few minutes, the status changes from **Installing** to **Installed**. You might have to refresh the page to see this change.

> [!NOTE]
> Companies usually have several Finance or Supply Chain Management environments. These environments include production environments, user acceptance testing (UAT) environments, and development (sandbox) environments. You must complete the preceding procedure for all environments that you want to connect to Electronic invoicing.

## Enable Electronic invoicing integration

To enable communication between Electronic invoicing and Finance or Supply Chain Management, you must enable the **Electronic Invoicing integration** feature.

1. In the **Feature management** workspace, on the **All** tab, search for the **Electronic invoicing integration** feature. If this feature doesn't appear on the page, select **Check for updates**.
1. Select the feature, and then select **Enable now**.

> [!NOTE]
> Before you work with Globalization features, the **E-Invoicing designer workspace** feature is enabled by default. However, after the Electronic Invoicing service add-in is installed, there's a delay of 45 minutes before the feature is enabled.

## Service environment configuration

> [!NOTE]
> The following procedure is required if the Regulatory Configuration Service (RCS) experience was previously used to configure the Electronic Invoicing service. If you're doing the initial configuration of the Electronic Invoicing service through Globalization Studio, you can skip this procedure.

1. Identify one of the previously deployed service environments. This environment is the only one that you configure in the Globalization Studio and then use by the Electronic Invoicing service.
1. Go to **Organization administration** \> **Setup** \> **Electronic document parameters**.
1. On the **Electronic invoicing** tab, on the **Service parameters** FastTab, in the **Environment** field, enter the name of the environment that you identified in step 1.

:::image type="content" source="../media/eInvoicing_service_environment_setup.png" alt-text="Screenshot of the Environment field for a service environment unavailable on the Electronic document parameters page.":::

> [!IMPORTANT]
> After the initial configuration of **Electronic document parameters**, the field for the service environment name becomes unavailable. Therefore, you must finalize the name of the relevant service environment in advance.

## Configure the Azure resources for Electronic invoicing

Set up the Azure resources that Electronic invoicing requires to do its work. For more information, see [Set up Azure resources for Electronic invoicing](gs-e-invoicing-set-up-azure-resources.md).

## Configure Globalization features

Implement different scenarios for processing electronic documents by using Globalization features. A Globalization feature is a set of components that define the rules for data transformation and further processing of electronic documents, such as sending them to or receiving them from external channels. You can use Globalization features that Microsoft provides, or you can create your own. For more information about how to work with Globalization features, see [Globalization feature components](gs-e-invoicing-working-globalization-features.md).

> [!NOTE]
> If your scenarios require integration with email or SharePoint to process inbound electronic documents, see [Process incoming electronic documents](e-invoicing-process-incoming-electronic-documents.md) for information about how to set up and use those channels.

## Configure Electronic invoicing parameters

For additional configuration steps related to Electronic invoicing, see [Configure Electronic invoicing parameters](gs-e-invoicing-set-up-parameters.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
