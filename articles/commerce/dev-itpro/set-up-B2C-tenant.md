---
title: Set up a B2C tenant in Commerce
description: This article describes how to set up your Microsoft Entra business-to-consumer (B2C) tenants for user site authentication in Microsoft Dynamics 365 Commerce.
author: BrianShook
ms.date: 07/25/2024
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2020-02-13
ms.custom: 
  - bap-template
---

# Set up a B2C tenant in Commerce

[!include [banner](../includes/banner.md)]

This article describes how to set up your Microsoft Entra business-to-consumer (B2C) tenants for user site authentication in Dynamics 365 Commerce.

Dynamics 365 Commerce uses Microsoft Entra B2C to support user credential and authentication flows. A user can sign up, sign in, and reset their password through these flows. Microsoft Entra B2C stores sensitive user authentication information, such as username and password. The user record in the B2C tenant will store either a B2C local account record or a B2C social identity provider record. These B2C records will link back to the customer record in the Commerce environment.

> [!WARNING] 
> Microsoft Entra ID B2C will retire old (legacy) user flows by August 1, 2021. Therefore, you should plan to migrate your user flows to the new recommended version. The new version provides feature parity and new features. The module library for Commerce version 10.0.15 or higher should be used with the recommended B2C user flows. For more information, see [User flows in Microsoft Entra ID B2C](/azure/active-directory-b2c/user-flow-overview).
 
 > [!NOTE]
 > Commerce evaluation environments come with a pre-loaded Microsoft Entra B2C tenant for demonstration purposes. Loading your own Microsoft Entra B2C tenant using the steps below is not required for evaluation environments.

> [!TIP]
> You can further protect your site users and enhance the security of your Microsoft Entra B2C tenants with Microsoft Entra Identity Protection and Conditional Access. To review the capabilities available to Microsoft Entra B2C Premium P1 and Premium P2 tenants, see [Identity Protection and Conditional Access for Microsoft Entra ID B2C](/azure/active-directory-b2c/conditional-access-identity-protection-overview).

## Dynamics environment prerequisites

Before you begin, ensure that your Dynamics 365 Commerce environment and e-commerce channel are configured appropriately by fulfilling the following prerequisites.

- Set the POS operations **AllowAnonymousAccess** value to "1" in Commerce headquarters:
    1. Go to **POS Operations**.
    1. In the operations grid, right-click and select **Personalize**.
    1. Select **Add a field**.
    1. In the list of available columns, select the **AllowAnonymousAccess** column to add it.
    1. Select **Update**.
    1. For the **612** "Customer add" operation, change **AllowAnonymousAccess** to "1."
    1. Run the **1090 (Registers)** job.
- Set the number sequence customer account **Manual** attribute to **No** in Commerce headquarters:
    1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Accounts receivable parameters**.
    1. Select **Number sequences**.
    1. In the **Customer account** row, double-click the **Number Sequence Code** value.
    1. On the **General** FastTab of the number sequence, set **Manual** to **No**.

After deployment of your Dynamics 365 Commerce environment, it also is recommended to [Initialize seed data](../enable-configure-retail-functionality.md) in the environment.

## Next steps

To continue the process of setting up a B2C tenant in Commerce, proceed to [Create or link to an existing Microsoft Entra B2C tenant in the Azure portal](create-link-aad-b2c-tenant.md).

## Additional resources

[Create or link to an existing Microsoft Entra B2C tenant in the Azure portal](create-link-aad-b2c-tenant.md)

[Create the B2C application](create-b2c-app.md)

[Create user flow policies](create-user-flow-policies.md)

[Add social identity providers (Optional)](add-social-identity-providers.md)

[Update Commerce headquarters with the new Microsoft Entra B2C information](update-hq-aad-b2c-info.md)

[Configure your B2C tenant in Commerce site builder](config-b2c-tenant-site-builder.md)

[Additional B2C information](additional-b2c-info.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
