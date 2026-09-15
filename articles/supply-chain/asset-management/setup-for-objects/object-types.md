---
title: Asset types
description: Learn how to create asset types in Asset Management. It also describes the elements that are related to asset types, including a step-by-step process.
author: jodahlMSFT
ms.author: jodahl
ms.reviewer: kamaybac
ms.search.form: EntAssetObjectJobType, EntAssetObjectType, EntAssetObjectTypeDefaultCreateCombinations, EntAssetObjectTypeDefault, EntAssetObjectTypeDefaultCopy, EntAssetObjectTypeDefaultSparePartApprove 
ms.topic: how-to
ms.date: 09/14/2026
ms.custom: 
  - bap-template
---

# Asset types

[!INCLUDE [banner](../../includes/banner.md)]

This article explains how to create asset types. It also describes the elements that are related to asset types. Asset types are used as general categories for assets. Examples include CNC machines, measuring equipment, and truck engines. Use asset types to manage the maintenance job types (maintenance tasks), asset lifecycle states, counters, asset attributes, condition assessment templates, and asset models that you can select for an asset. When you create an asset, you must specify the asset type.

For each asset type, you can create variations of the asset type setup. For example, if you have an asset type named *Trucks*, you can create variations of that asset type for different asset manufacturers and asset models. Add the required spare parts and maintenance plans to each asset type setup.

First, set up the required asset types. Next, create the asset models that should be related to the asset types. Finally, on the **Asset type defaults** page, create all the variations of asset types that are required for your equipment.

## Create an asset type

1. Select **Asset management** > **Setup** > **Asset types** > **Asset types**.
2. Select **New** to create an asset type.
3. In the **Asset type** field, enter an asset type ID.
4. In the **Name** field, enter a name.
5. In the **Asset lifecycle model** field, select an asset lifecycle model. For more information about asset lifecycle states and asset lifecycle models, see [Asset lifecycle states](object-stages.md).
6. Set the **Total** option to *Yes* if you want to calculate summarized key performance indicator (KPI) values for assets that have this asset type.
7. Select **Save**.
8. On the **Maintenance job types** FastTab, select the maintenance job types that you want to relate to the asset type:
    - To select a maintenance job type, select it in the **Maintenance job types remaining** field, and then select the right arrow button ![Right arrow button.](media/29-setup-for-objects.png) to move it to the **Maintenance job types selected** section.
    - To select all available maintenance job types, select the ![Forward all arrow.](media/30-setup-for-objects.png) button. All maintenance job types are transferred from the **Maintenance job types remaining** field to the **Maintenance job types selected** field.
    - To cancel the selection of a maintenance job type, select it in the **Maintenance job types selected** field, and then select the left arrow button ![Left arrow button.](media/31-setup-for-objects.png) to move it to the **Maintenance job types remaining** field.

9. Select the counters that you want to relate to the asset type. On the **Counters** FastTab, make your selections by using the methods that are described for maintenance job types in step 8. For more information about the setup of counters, see [Counters](counters.md).
10. Select the attribute types that you want to relate to the asset type. On the **Attribute types** FastTab, make your selections by using the methods that are described for maintenance job types in step 8. To create the preferred sequence of attribute types, select an attribute type in the **Attribute types selected** field, and use the up arrow and down arrow buttons to move it. The sequence of attribute types appears on assets that use this asset type. Learn more about asset attributes in [Maintenance attribute types](../setup-for-functional-locations/specification-types.md).

    > [!NOTE]
    > When you add new attribute types on the **Attribute types** FastTab, existing assets are automatically updated with that information.

11. Select the condition assessment templates that you want to relate to the asset type. On the **Condition assessments** FastTab, make your selections by using the methods that are described for maintenance job types in step 8. For more information about condition assessment templates and registrations, see [Condition assessment](../setup-for-objects/condition-assessment.md).
12. The **Asset model** FastTab shows all the combinations of asset manufacturers and models that are set up on the selected asset type. To see the combinations divided according to manufacturer, select **Asset model** to open the **Asset model** page.

    On the **Asset model** page, you can add asset model–asset type relations. Also, on the **Asset types** page, you can add asset manufacturer–asset model relations directly to an asset type. Finally, on the **Asset model** page (**Asset management** > **Setup** > **Assets** > **Asset model**), you can create new asset manufacturer–asset model–asset type relations. Therefore, there are three ways to set up and edit asset manufacturer–asset model–asset type relations. All the available combinations appear from different perspectives, and you can select your preferred point of entry when you work with the setup.

> [!NOTE]
>
> - If you select counters on an asset type, the selections automatically update on the **Counters** page (**Asset management** > **Setup** > **Assets** > **Asset types** > **Counters**).
> - The fields in the **Details** section on the **General** FastTab show the number of maintenance job types, counters, attributes, and so on, that are set up on the selected asset type.

Typically, work orders that you create manually relate to corrective maintenance, whereas work orders that you automatically create relate to preventive maintenance. When you manually create work orders, you can use only the maintenance job types that you select on the **maintenance job types** FastTab of the **Asset types** page. However, automatically created work orders can use all the maintenance job types you create on the **Maintenance job types** page (**Asset management** > **Setup** > **Jobs** > **Maintenance job types**).

## Create asset type setup lines

1. Select **Asset management** > **Setup** > **Assets** > **Asset types** > **Asset type defaults**. Alternatively, select **Asset management** > **Setup** > **Assets** > **Asset types** > **Asset types**, select an asset type, and then select **Asset type defaults**.
2. The first time that you use the **Asset type defaults** page, you might find the **Create combinations** button useful. Use this button to quickly create all combinations of an asset model on an asset type. Select **Create combinations**, select the asset type to create combinations for, and then select **OK**.

    > [!NOTE]
    > If you don't use all the asset type setup combinations that were automatically created, you can delete a setup by selecting it and then selecting **Delete**.

3. Select **New** to manually create an asset type setup.
4. Depending on how specific the asset type setup should be, make selections in the **Asset type**, **Manufacturer**, and **Model** fields.
5. If a warranty agreement is related to the asset type, select the agreement in the **Vendor warranty** and **Customer warranty** fields.
6. On the **Spare parts** FastTab, select **Add** to add spare parts to the selected asset type setup.
7. To approve a spare part, select the spare part line, and then select **Approve**. You can select multiple lines for approval.
8. The **Active** and **Approved** check boxes control which spare parts are shown on the FastTab. When the **Active** check box is selected, only the spare parts that are valid on the current date are shown, as defined in the **Valid from** and **Valid to** fields. This check box is selected by default. When the **Approved** check box is selected, only approved spare parts are shown. This check box is cleared by default.
9. To see whether a spare part is used somewhere else in Asset Management (for example, in relation to assets and work orders), select the spare part line, and then select **Item where used** to open the **Item where used** page.
10. On the **Maintenance plans** FastTab, select **Add** to add maintenance plans to the selected asset type setup.
11. To copy an asset type setup to another setup, use the Copy function. Select the asset type setup to copy a setup to, select **Copy setup**, and select the asset type setup to copy the setup from. The settings of the various options determine how much information is included. When you finish, select **OK** to copy the setup.

> [!NOTE]
> If you have many spare part lines and maintenance plan lines that you'll reuse, the **Copy** function lets you quickly and easily set up data for many asset type setup combinations.

## Spare parts on the asset type setup

Spare parts are defined on the asset type setup. Therefore, all assets that match the same setup line share the same spare parts, and you maintain one list for a group of similar assets instead of a separate list for each asset.

Workers can then select from that list when they add items to a work order. To learn more about how spare parts are used, how an asset is matched to a setup line, and how to view the spare parts for a specific asset, go to [Asset spare parts](spare-parts.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
