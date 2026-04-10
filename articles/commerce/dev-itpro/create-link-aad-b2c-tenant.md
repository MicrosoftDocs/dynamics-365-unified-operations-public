---
title: Create or link to an existing Microsoft Entra B2C tenant in the Azure portal
description: Learn how to create or link to an existing Microsoft Entra business-to-consumer (B2C) tenant in the Microsoft Azure portal.
author: BrianShook
ms.date: 02/13/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2020-02-13
ms.custom: 
  - bap-template
---

# Create or link to an existing Microsoft Entra B2C tenant in the Azure portal

[!include [banner](../includes/banner.md)]

This article explains how to create or link to a Microsoft Entra business-to-consumer (B2C) tenant in the Microsoft Azure portal. For more information, see [Tutorial: Create a Microsoft Entra B2C tenant](/azure/active-directory-b2c/tutorial-create-tenant).

> [!NOTE]
> For Commerce tenants created by using the Dynamics 365 Commerce version 10.0.46 general availability (GA) release or later versions, Microsoft Entra ID (formerly Azure AD) business-to-consumer (B2C) integration for Commerce e-commerce site authentication isn't enabled by default. If you need to use Microsoft Entra ID B2C (for example, to continue using an existing Azure AD B2C tenant), submit a Microsoft Support request for explicit enablement.

To create or link to an existing Microsoft Entra B2C tenant in the Azure portal, follow these steps:

1. Sign in to the [Azure portal](https://portal.azure.com/).
1. From the Azure portal menu, select **Create a resource**. Be sure to use the subscription and directory that you connect with your Commerce environment.

    :::image type="content" source="../media/B2CImage_1.png" alt-text="Screenshot of the Create a resource option in the Azure portal.":::

1. Go to **Identity \> Microsoft Entra ID B2C**.
1. Once on the **Create New B2C Tenant or Link to existing Tenant** page, use one of the following options that best suits your company's needs:

    - **Create a new Microsoft Entra B2C Tenant**: Use this option to create a new Microsoft Entra B2C tenant.
        1. Select **Create a new Microsoft Entra B2C Tenant**.
        1. Under **Organization name**, enter the organization name.
        1. Under **Initial domain name**, enter the initial domain name.
        1. For **Country or region**, select the country/region.
        1. Select **Create** to create the tenant.

     :::image type="content" source="../media/B2CImage_2.png" alt-text="Screenshot of creating a new Microsoft Entra B2C tenant in the Azure portal.":::

     - **Link an existing Microsoft Entra B2C Tenant to my Azure subscription**: Use this option if you already have a Microsoft Entra B2C tenant you want to link to.
        1. Select **Link an existing Microsoft Entra B2C Tenant to my Azure subscription**.
        1. For **Microsoft Entra B2C Tenant**, select the appropriate B2C tenant. If the message "No eligible B2C Tenants found" appears in the selection box, you don't have an existing eligible B2C tenant and must create a new one.
        1. For **Resource group**, select **Create new**. Enter a **Name** for the resource group that contains the tenant, select the **Resource group location**, and then select **Create**.

    :::image type="content" source="../media/B2CImage_3.png" alt-text="Screenshot of linking an existing Microsoft Entra B2C tenant to an Azure subscription.":::

1. When you create the new Microsoft Entra B2C directory, a link to the new directory appears on the dashboard. This link directs you to the **Welcome to Microsoft Entra B2C** page.

    :::image type="content" source="../media/B2CImage_4.png" alt-text="Screenshot of the link to the new Microsoft Entra B2C directory on the dashboard.":::

> [!NOTE]
> If you have multiple subscriptions within your Azure account or set up the B2C tenant without linking to an active subscription, a **Troubleshoot** banner directs you to link the tenant to a subscription. To resolve the subscription issue, select the troubleshooting message and follow the instructions.

The following image shows an example of a Microsoft Entra B2C **Troubleshoot** banner.

:::image type="content" source="../media/B2CImage_5.png" alt-text="Screenshot of the Microsoft Entra B2C Troubleshoot banner warning that the directory has no active subscription.":::

## Next steps

To continue setting up a B2C tenant in Commerce, see [Create the B2C application](create-b2c-app.md).

## Additional resources

[Set up a B2C tenant in Commerce](set-up-B2C-tenant.md)

[Create the B2C application](create-b2c-app.md)

[Create user flow policies](create-user-flow-policies.md)

[Add social identity providers (Optional)](add-social-identity-providers.md)

[Update Commerce headquarters with the new Microsoft Entra B2C information](update-hq-aad-b2c-info.md)

[Configure your B2C tenant in Commerce site builder](config-b2c-tenant-site-builder.md)

[Additional B2C information](additional-b2c-info.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
