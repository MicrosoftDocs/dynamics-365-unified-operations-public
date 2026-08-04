---
title: Manage unmanaged customizations on the supplier portal (preview)
description: Learn how unmanaged layers affect portal components and how to correctly delete components or solutions in the supplier portal.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 07/27/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Manage unmanaged customizations on the supplier portal (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

When you modify portal components such as site settings, content snippets, web files, web templates, or pages, you create unmanaged layers on those components in Microsoft Dataverse. Understanding how unmanaged layers work is essential when you plan to delete individual components or remove an entire solution.

## Why unmanaged layers matter

When you include a component in a managed solution and you make changes directly in the environment, you create an unmanaged layer on top of the managed layer. This layer overrides the managed solution configuration.

The presence of unmanaged layers can prevent:

- Deleting individual components
- Deleting the managed solution

If you don't remove unmanaged layers first, deletion might fail due to dependency or layering conflicts.

The following screenshot shows the solution dependencies view in Power Apps. It lists the components that prevent a solution from being uninstalled.

:::image type="content" source="media/portal-solution-layers.png" alt-text="Screenshot of the Power Apps solution dependencies view showing components that prevent uninstalling the Vendor Relationship Management Power Pages Solution." lightbox="media/portal-solution-layers.png":::

## Delete a component

To delete a portal component, first remove any unmanaged layers. To delete a component correctly, follow these steps:

1. Go to the [Power Apps maker portal](https://make.powerapps.com).
1. Locate the component in the appropriate solution.
1. Right-click the component, and then select **Advanced** \> **See Solution Layers**.
1. Select and remove the unmanaged layer.
1. After you remove the unmanaged layer, delete the component.

This process ensures the managed solution can properly release the component.

## Delete a solution

When deleting a solution that contains Power Pages components, first disable the associated site.

### Shut down the site

To shut down the Power Pages site, follow these steps:

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. Select **Power Pages**.
1. Select your site.
1. Select **Site Actions** \> **Shut down the site**.

The following screenshot shows the Site Actions menu with the **Shut down the site** option.

:::image type="content" source="media/portal-shut-down-site.png" alt-text="Screenshot of the Power Platform Admin Center showing the Site Actions menu with the Shut down the site option." lightbox="media/portal-shut-down-site.png":::

When you shut down the site, you disable active portal interactions, remove runtime dependencies, prevent additional unmanaged changes, and help ensure unmanaged layers are properly handled.

### Delete the solution

After you clear unmanaged layers and shut down the site, you can delete the managed solution. Make sure no dependency errors exist before you complete the deletion.

## Best practices

- Avoid making direct changes in production environments. Use development environments for customizations.
- Track solution layering carefully when working with managed solutions.
- Always shut down the Power Pages site before you attempt large-scale deletions.
- Validate dependencies before removing components.

## Related information

- [Personalize the supplier portal](personalize-portal-overview.md)
- [Supplier Engagement overview](supplier-engagement-overview.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
