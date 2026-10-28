---
title: IS (Imposto Seletivo, selective tax) in Brazil Reformed Tax (Preview)
description: Learn how to set up and validate the calculation of the IS (Imposto Seletivo) selective tax for Brazil tax reform in Microsoft Dynamics 365 Finance.
author: yananSong
ms.author: yanansong
ms.topic: how-to
ms.date: 10/27/2026
ms.custom: bap-template
ms.service: dynamics-365-finance
---

# IS (Imposto Seletivo, selective tax) in Brazil Reformed Tax (Preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

> [!IMPORTANT]
> This feature is in preview. Preview features aren't meant for production use and might have restricted functionality. These features are available before an official release so that customers can get early access and provide feedback.

IS (Imposto Seletivo, selective tax) is a tax in Brazil tax reform. This article explains how to set up the IS tax code in the Tax Calculation service and validate the calculation on a sales order. It covers the following tasks:

- Build the tax calculation feature version, and define the IS tax code, rate, and applicability rule.
- Complete the reference data and the tax calculation parameters.
- Validate the IS calculation on a sales order.

## Prerequisites

Before you begin, ensure that you meet the following prerequisites:

- The tax calculation configuration is imported, because the feature version is built on an existing configuration version. For more information, see [Import the configuration files for tax calculation](brazil-reform-setup.md#import-the-configuration-files-for-tax-calculation).
- You have access to **Globalization Studio** (**Tax calculation features**) and the Brazil localization **cClassTrib** reference data. For more information, see [CST and cClasstrib in Brazil Reformed Tax](brazil-reform-cst-cclasstrib.md).
- You have an editable sales order in a Brazilian legal entity.

## Set up the IS tax code in the tax calculation feature

You define the IS tax code in a tax calculation feature version. The setup doesn't take effect until you change the status of the version to **Completed**.

### Create a feature version

To create a feature version, follow these steps:

1. Go to **Tax** > **Setup** > **Tax configuration** > **Tax calculation features**. You can also open **Globalization Studio** and select the **Tax calculation features** tile.
1. Select the tax calculation feature that's used for Brazil tax reform.
1. In the **Versions** section, select **New** to add a feature version, and then select **Edit** to open it.

> [!NOTE]
> You can edit only a version that has a **Draft** status. A version that has a **Completed** status is read-only. To change a completed version, create a new version.

### Set the configuration version and source legal entity

On the feature version header, set the following fields.

| Field | Value |
| --- | --- |
| Configuration version | **Tax Calculation Configuration (Brazil)** |
| Enable lookups in applicability rules | **Yes** |
| Source legal entity | Your Brazilian legal entity, for example, **BRMF** |

When **Enable lookups in applicability rules** is set to **Yes**, the applicability rules offer real values instead of free text.

### Add the IS tax code

To add the IS tax code, follow these steps:

1. On the **Tax codes** tab, select **Add**.
1. Enter the tax code and calculation origin, and then complete the **General** section.

    | Field | Example value | Description |
    | --- | --- | --- |
    | Tax code | **IS** | The tax code for the selective tax. |
    | Calculation origin | **By Net Amount Brazil For IS** | The formula that builds the tax base. Use the IS-specific calculation origin, not the generic net amount origin that other Brazilian taxes use. |
    | cClassTrib code | **000001** | The tax classification code. |
    | Tax type | **IS** | The reformed tax type. |
    | Fiscal indicator | **With Credit/Debit** | |
    | Unit | **ea** | The unit that the specific unit rate is measured against. |

1. Select **Save**.

> [!NOTE]
> Save after you create the tax code line. The **cClassTrib code**, **Tax type**, and **Fiscal indicator** lookups populate only after the line exists.

### Define the IS rate

To define the IS rate, follow these steps:

1. In the **Rate** grid, select **Add**.
1. Enter both the ad valorem rate and the specific unit rate on the same line.

    | Field | Example value | Description |
    | --- | --- | --- |
    | Tax Rate | **10.00** | The ad valorem percentage that's applied to the tax base. |
    | Specific Unit Rate | **1.00** | The specific rate per unit. |
    | Unit | **ea** | The unit that the specific unit rate is measured against. |

The two components aren't alternatives. The tax calculation service applies both components and adds them together. In this example, IS is charged at 10% plus 1% per unit, which is an effective rate of 11% of the tax base.

#### Example

A sales order line has a tax base of 78.75.

| Component | Calculation | Amount |
| --- | --- | --- |
| Ad valorem (Tax Rate) | 10% × 78.75 | 7.8750 |
| Specific (Specific Unit Rate) | 1% × 78.75 | 0.7875 |
| **Total IS** | | **8.6625** (shown as 8.66) |

#### Define unit conversions

The specific component is tied to the unit on the rate line, for example, **ea**. If a sales order line is sold in a different unit, such as **dz**, its quantity must be converted into the setup unit before the rate can be applied. Define the conversion in advance. Without it, the specific component is measured against a quantity in the wrong unit, and the IS amount is incorrect.

To define the conversion, go to **Product information management** > **Setup** > **Units** > **Unit conversions**.

Verify that the rate line shows a Tax Rate and a Specific Unit Rate that aren't zero, and that the unit either matches the sales line unit or has a conversion defined.

### Set the tax code applicability for the IS tax type

The applicability rule determines when IS is calculated. If the fiscal classification code of the line doesn't match the rule, no IS line is created.

To set up the applicability rule, follow these steps.

1. Open the **Tax code applicability (IS tax type)** tab, and select **Add**.
1. Set the following fields.

    | Field | Example value |
    | --- | --- |
    | Lines.Fiscal classification code | **8518.22.00** |
    | Tax codes | **IS** |

> [!TIP]
> The **Tax group** and **Item tax group** tabs drive the sales tax group matching. Review them together with the IS applicability tab so that the item that you test with is covered by both.

### Complete the feature version

To complete the feature version, follow these steps:

1. Select **Save**, and then close the page.
1. Select **Change status** > **Complete**, and then select **Yes** to confirm.

Completing the version publishes the setup to the tax calculation service. Verify that the status of the version changes from **Draft** to **Completed** and that the message **Tax feature setup synchronization completed** appears.

## Set up reference data and tax calculation parameters

The feature version alone isn't enough. The cClassTrib reference data must recognize the IS tax type, and the tax calculation parameters must refer to the completed feature version.

### Set the cClassTrib code category

The **Code category** tells the localization which tax family the classification belongs to. This classification determines how the IS tax type resolves at calculation time.

To set the cClassTrib code category, follow these steps:

1. Go to **Tax** > **Setup** > **Sales tax** > **cClassTrib**.
1. Select the row that the IS tax code uses, such as **000001**.
1. Switch to edit mode, and set the **Code category**.
1. Save the change before you confirm the tax calculation parameters.

### Assign the feature version to the tax calculation parameters

To assign the feature version to the tax calculation parameters, follow these steps:

1. Go to **Tax** > **Setup** > **Tax configuration** > **Tax calculation parameters**.
1. On the **General** tab, in the **Name** field, select the completed feature setup, such as **BR-tax-calculation-feature-demo-data**.

This setting links the legal entity to the feature version that you completed.

### Complete mandatory fields for new tax codes

When you confirm the parameters, the **Maintain mandatory fields for new tax codes** dialog box opens. You can't continue until you set the **Settlement period**, **Ledger posting group**, and **Currency** fields for every new tax code.

To complete mandatory fields for new tax codes, follow these steps:

1. Complete the row for the **IS** tax code.
1. Select **Confirm**.

The dialog box shows the following message until you set all the fields: "The fields Settlement period, Ledger posting profile and Currency must be filled in for all new tax codes." Verify that the dialog box closes without a warning. If a warning is still displayed, a mandatory field is still empty on one of the tax code rows.

## Validate the IS calculation

Validate the result on a sales order. The order line must use an item whose fiscal classification code matches the applicability rule that you defined.

### Check the sales order line setup

To check the sales order line setup, follow these steps:

1. Go to **Accounts receivable** > **Orders** > **All sales orders**, and open or create a sales order.
1. Add a line for the item.
1. Expand **Line details**, and select the **Setup** tab.
1. Confirm that the **Sales tax** and **Tax reform** groups are set.
1. Enter the **Unit price** that you want to test, such as **100.00**.
1. Check the line **Unit**. If it differs from the unit on the IS rate line, ensure that a unit conversion exists.

For more information, see [Calculation in Sales order in Brazil Reformed Tax](brazil-reform-calculation-sales-order.md).

### Review the sales tax transactions

To review the sales tax transactions, follow these steps:

1. Select the order line, and then select **Sales tax** to open the **Sales tax transactions** page.
1. Verify that an **IS** row appears together with the other Brazilian taxes. The row shows the cClassTrib code, the fiscal indicator, and the calculated amount.

The **Percent** column shows only the ad valorem rate, such as **10.00000**. The **Actual sales tax amount** column includes the full 11%. That's why a tax base of 78.75 produces an IS amount of 8.66.

> [!TIP]
> If no IS row appears, the fiscal classification code of the item probably isn't covered by the IS applicability rule.

## Related information

- [Brazil tax reform overview](brazil-reform-overview.md)
- [Brazil tax reform setup](brazil-reform-setup.md)
- [CST and cClasstrib in Brazil Reformed Tax](brazil-reform-cst-cclasstrib.md)
- [Calculation in Sales order in Brazil Reformed Tax](brazil-reform-calculation-sales-order.md)
