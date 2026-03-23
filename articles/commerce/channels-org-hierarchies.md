---
title: Set up organization hierarchies
description: Learn how to set up organization hierarchies in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 01/20/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2020-01-20
ms.custom: 
  - bap-template
---

# Set up organization hierarchies

[!include [banner](includes/banner.md)]

This article describes how to set up organization hierarchies in Microsoft Dynamics 365 Commerce.

Before creating channels, set up your organization hierarchies.

Use organization hierarchies to view and report on your business from various perspectives. For example, set up one hierarchy for tax, legal, or statutory reporting. Then, set up another hierarchy to report financial information that isn't legally required but is used for internal reporting.

Before you create an organization hierarchy, you must create organizations. For more information, see [Create legal entities](channels-legal-entities.md) or [Create operating units](../fin-ops-core/fin-ops/organization-administration/tasks/create-operating-unit.md?toc=/dynamics365/commerce/toc.json).


For more information, see the following articles.
- [Organizations and organizational hierarchies overview](../fin-ops-core/fin-ops/organization-administration/organizations-organizational-hierarchies.md?toc=/dynamics365/commerce/toc.json)
- [Plan your organization hierarchy](../fin-ops-core/fin-ops/organization-administration/plan-organizational-hierarchy.md?toc=/dynamics365/commerce/toc.json)
- [Create an organization hierarchy](../fin-ops-core/fin-ops/organization-administration/tasks/create-organization-hierarchy.md?toc=/dynamics365/commerce/toc.json)

## Create an organizational hierarchy

To create an organizational hierarchy, follow these steps:

1. In the navigation pane, go to **Modules \> Retail and commerce \> Channel Setup \> Organization hierarchies**.
1. On the action pane, select **New**.
1. In the **Name** field, enter a value.
1. In the **Purpose** section, select **Assign purpose**.
1. In the list, find and select the desired record. Select a purpose to assign to your organization hierarchy.
1. In the **Assigned hierarchies** section, select **Add**.
1. In the list, mark the selected row. Find the hierarchy you created.
1. Select **OK**.

The following image shows an example organizational hierarchy created for a fictitious "Adventure Works" set of stores.

:::image type="content" source="media/organizational-hierarchies.png" alt-text="Screenshot of an example organizational hierarchy.":::

### Add organizations to a hierarchy

To add organizations to a hierarchy, follow these steps:

1. In the list, find and select the desired record. Select your hierarchy.
1. On the action pane, select **View**.
1. Add organizations, as necessary.
1. To add an organization, select **Edit** and then select **Insert**. When you're done making changes, you can save a draft and publish the changes.

> [!NOTE]
> A hierarchy can only be published once per calendar day in a given time zone. Each time you publish, the system records the effective date based on the time zone you select. If you later publish using a different time zone, the resulting dates can overlap or collide, which blocks the publish. To avoid this, always use the same time zone when publishing a hierarchy.

The following image shows an example organization hierarchy. In this example, the legal entity "Contoso Retail" has three cost centers: "Mall," "Online," and "Call Center." The "Mall" cost center has four retail channels: "Atlanta," "Houston," "San Francisco," and "San Jose."

:::image type="content" source="media/hierarchy-valid-combinations.png" alt-text="Screenshot of an example organization hierarchy showing the allowed dimension value combinations for each node.":::

If this hierarchy is linked to an account structure that includes both a **Cost center** dimension and a **Retail channel** dimension, the hierarchy controls which combinations are valid. For example, entering a cost center of "Mall" with a retail channel of "Fabrikam" would produce a validation error, because "Fabrikam" isn't listed under "Mall" in the hierarchy.

## Verify hierarchy relationships in account structures

Organization hierarchies can be linked to account structures to control which dimension value combinations are allowed during transaction entry. To check which hierarchies are linked to an account structure, follow these steps.

1. Navigate to the account structure and select **View** > **Relationships**.

   :::image type="content" source="media/account-structure-relationships.png" alt-text="Screenshot showing the View and Relationships option on an account structure.":::

1. Review which organization hierarchy relationships are included in validation. Any hierarchy that is checked is used to validate dimension value combinations when transactions are entered.

   :::image type="content" source="media/account-structure-hierarchy-included.png" alt-text="Screenshot showing which organization hierarchies are included in account structure validation.":::

To view or edit the hierarchies themselves, go to **Organization administration** > **Organizations** > **Organization hierarchies**.

## Publishing delay for newly published hierarchies

After you publish a new or updated organization hierarchy, it may take up to 24 hours (though typically less) for the changes to take effect in transaction validation. During this period, you may receive validation errors when entering dimension combinations that should be valid under the newly published hierarchy.

If you encounter this issue, you can either:

- Wait for the published hierarchy to take effect.
- Set the transaction date to the next day to work around the delay.

## Importing hierarchy data

You can import organization hierarchy structures using data entities. If you're importing a multi-level hierarchy, import from the top down—start with the highest parent node, then add each level of child nodes in separate import operations. Attempting to import all levels at once can result in the error "The Organization does not exist" because child nodes may be processed before their parent nodes are available.

## Deleting a legal entity after hierarchy publishing

Once a legal entity has been added to an organization hierarchy and that hierarchy has been published, the legal entity can no longer be deleted—even if you later remove it from the hierarchy and republish. The **Delete** button remains unavailable.

This is by design. Publishing a hierarchy creates a permanent historical record of that structure, which is used to support backdated reporting and auditing. Because those records reference the legal entity, the system protects it from deletion to preserve that history.

If you remove a legal entity from an unpublished hierarchy *before* the hierarchy is ever published, the delete option remains available. But once a version of the hierarchy that includes the legal entity has been published, the restriction is permanent.

Leaving an unused legal entity in the system has no negative impact on day-to-day operations.

## Additional resources

[Organizations and organizational hierarchies overview](../fin-ops-core/fin-ops/organization-administration/organizations-organizational-hierarchies.md?toc=/dynamics365/commerce/toc.json)

[Plan your organizational hierarchy](../fin-ops-core/fin-ops/organization-administration/plan-organizational-hierarchy.md?toc=/dynamics365/commerce/toc.json)

[Create legal entities](channels-legal-entities.md)

[Create operating units](../fin-ops-core/fin-ops/organization-administration/tasks/create-operating-unit.md?toc=/dynamics365/commerce/toc.json)

[Channels overview](channels-overview.md)

[Channel setup prerequisites](channels-prerequisites.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
