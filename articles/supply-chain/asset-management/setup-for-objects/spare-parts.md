---
title: Asset spare parts
description: Learn how spare parts are defined on asset-type setup lines in Asset Management, how workers use them on work orders, and how to view the spare parts that apply to a specific asset.
author: jodahlMSFT
ms.author: jodahl
ms.reviewer: kamaybac
ms.search.form: EntAssetObjectTypeDefaultSparePart, EntAssetObjectTypeDefaultSparePartApprove, EntAssetObjectTypeDefault, EntAssetItemWhereUsed
ms.topic: concept-article
ms.date: 09/14/2026
ms.custom: 
  - bap-template
---

# Asset spare parts

[!INCLUDE [banner](../../includes/banner.md)]

A spare part is an item that's typically used to maintain or repair assets. In Asset Management, you define spare parts on an asset-type setup line, which is a combination of an asset type, an asset manufacturer, and an asset model. You can't define spare parts on individual assets.

Because you define spare parts on the asset-type setup line, all assets that match the same line share the same spare parts. Therefore, you maintain one list for a group of similar assets, instead of a separate list for each asset. For example, if you have 20 pumps of the same model, you define the spare parts for that model one time, and the list applies to all 20 pumps.

To add spare parts to an asset-type setup line, see [Asset types](object-types.md).

## How spare parts are used on work orders

Spare parts help workers add the correct items to a work order. Instead of searching the full item catalog, a worker can select from a short list that shows only the spare parts that apply to the asset on the work order job. A spare part appears in the filtered list only if it meets both of the following conditions:

- The spare part is approved.
- The current date falls within the period that's defined in the **Valid from** and **Valid to** fields on the spare part line.

This filtered list is available both when the work is planned and when the consumption is registered. Workers can use it on the following pages:

- Open the **Work order maintenance forecast** page for a work order. On the **Items** FastTab toolbar, select **Add spare parts**. Learn more in [Maintenance forecasts](../work-orders/maintenance-forecasts.md).
- Open the **Work order journals** page for a work order. On the **Items** FastTab, find the line you want to edit and open the dropdown list for the **Item number** field. Then select the **Spare parts** tab. Learn more in [Register consumption](../consumption/register-consumption.md).

Workers aren't limited to the spare parts list. On both pages, they can also select any other item, or select an item from the asset bill of materials (BOM). Learn more in [Asset BOMs](../objects/object-bom.md).

## Where spare parts are created and shown

You can view and create spare parts on the **Asset type defaults** and **Spare parts** pages. The **Asset type defaults** page shows the data for one combination at a time, whereas the **Spare parts** page shows all spare part records across all asset-type setup lines. If the **Spare parts** page contains many records, the **Asset type defaults** page might give you a better overview. You can decide which page you prefer to use.

### Manage spare parts on the Asset type defaults page

To open the **Asset type defaults** page, go to**Asset management** > **Setup** > **Asset type defaults**. When you open the **Asset type defaults** page, you see only the spare parts for the selected combination of asset type, asset manufacturer, and asset model.

To see whether a spare part is used anywhere else in Asset Management (for example, in relation to assets and work orders), select the line on the **Spare parts** FastTab and then select **Item where used** from the FastTab toolbar to open the **Item where used** dialog. Set filtering options in this dialog as required and then select **OK** to view the items.

### Manage spare parts on the Spare parts page

To open the **Spare parts** page, go to **Asset management** > **Inquiries** > **Spare parts**. On this page, you can view all spare part records across all asset-type setup lines. You can also create new spare parts for existing combinations of an asset type, asset manufacturer, and asset model.

To see whether a spare part is used anywhere else in Asset Management (for example, in relation to assets and work orders), select the spare parts line and then select **Item where used** from the Action Pane to open the **Item where used** dialog. Set filtering options in this dialog as required and then select **OK** to view the items.

## How an asset matches to an asset-type setup

Each asset matches exactly one asset-type setup line, based on the asset type, manufacturer, and model of the asset.

If you leave the **Manufacturer** or **Model** field blank on a setup line, that line applies to all manufacturers or all models. Therefore, an asset can match several setup lines. In this situation, the most specific line is used: a line that specifies a model takes precedence over a line that specifies only a manufacturer, and a line that specifies a manufacturer takes precedence over a line that specifies only the asset type.

For example, suppose the following asset-type setup lines exist.

| Asset type | Manufacturer | Model | Applies to |
|------------|--------------|-------|------------|
| Pumps | Blank | Blank | All pumps |
| Pumps | Contoso | Blank | All Contoso pumps |
| Pumps | Contoso | P-100 | Contoso P-100 pumps only |

An asset that has the *Pumps* asset type, the *Contoso* manufacturer, and the *P-100* model matches all three lines. Because the third line is the most specific line, the system uses this line for the asset.

> [!IMPORTANT]
> Only the spare parts on the matched setup line apply to an asset. Spare parts that you define on a more general line don't appear for the asset, and they aren't available in the filtered list on a work order. To make those spare parts available, add them to the matched setup line.

## View the spare parts for a specific asset

You can view the spare parts that apply to one asset.

1. Go to **Asset management** > **Assets** > **All assets**.
1. Select the asset in the list.
1. On the Action Pane, open the **General** tab and, in the **Related information** group, select **Spare parts**.

The page shows only the spare parts of the asset-type setup line that the asset matches. The filter is applied automatically and it doesn't appear in the filter pane.

The following check boxes control which spare parts are shown:

- **Active** – Show only the spare parts that are valid on the current date, as defined in the **Valid from** and **Valid to** fields. This check box is selected by default.
- **Approved** – Show only the spare parts that are approved. This check box is cleared by default.

> [!TIP]
> If you expect to see spare parts for an asset, but the page is empty, clear the **Active** check box. If spare parts then appear, their validity period doesn't include the current date. If the page is still empty, the spare parts are probably defined on an asset-type setup line other than the line that the asset matches. To see all spare part records and the setup line that each record belongs to, go to **Asset management** > **Inquiries** > **Spare parts**.
