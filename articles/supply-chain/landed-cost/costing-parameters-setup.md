---
title: Costing parameter values setup
description: When you set up the Landed cost module, you can define several sets of common values when you select costing parameter values in other parts of the app.
author: lisascholz91
ms.author: lisascholz
ms.topic: how-to
ms.date: 06/07/2024
ms.custom: 
  - bap-template
ms.reviewer: kamaybac
ms.search.form: ITMCostTypeTable, ITMCostTypeGroup, ITMCostTransferGroup, ITMCostTemplateTable, ITMVolumetricDivisorTable
---

# Costing parameter values setup

[!include [banner](../../includes/banner.md)]

When you set up the **Landed cost** module, you can define several sets of common values and related settings per value. These values will then be available when you select specific types of costing parameter values in other parts of the app. This article explains how to set up these sets of values.

## Set up cost type codes

Cost type codes determine the type of cost that is incurred when the goods are landed into the warehouse, or the landed costs of the voyage. Although they usually increase the value of the goods, they can also be used to accrue amounts into the ledger. Ledger adjustments are used when a cost is accrued over time or during a series of voyages and offset in a single transaction.

> [!NOTE]
> If the cost type table is shared across legal entities, the chart of accounts must also be shared across legal entities. Otherwise, the posting transactions won't work correctly.

To set up your cost type codes, go to **Landed cost \> Costing setup \> Cost type codes**. You can use the buttons on the Action Pane to create new cost type codes, edit existing codes, or delete a selected cost type.

The following table describes the fields that are available for each cost type code.

| Field | Description |
|---|---|
| Cost type code | Enter a name for the cost type code. |
| Description | Enter a description of the cost type code. |
| Use shipping rate | Set this option to *Yes* if the voyage exchange rate (sometimes referred to as a management rate) must be used to calculate the value of these costs. In this case, the shipping rate will be used instead of the standard default or spot exchange rate to exchange foreign currency invoices. |
| Reporting category | This field establishes a reporting category for the cost type. Reports can be printed either by reporting categories or by cost type. |
| Debit type | Select whether the cost type should debit the item, the ledger account, or the vendor. |
| Debit posting | If the **Debit type** field is set to *Ledger account*, select the posting description. |
| Debit account | If the **Debit type** field is set to *Ledger account*, select the ledger account to use. |
| Credit type | Select whether this cost type should credit the item, the ledger account, or the vendor. |
| Credit posting | If the **Credit type** field is set to *Ledger account*, select the posting description. |
| Credit account | If the **Credit type** field is set to *Ledger account*, select the ledger account to use. |
| Clearing account | Select the clearing account for the cost type. We recommend that you specify a separate clearing account per cost type to help with reconciliation. |
| Standard cost posting type | If you're using standard costing, select the posting description. |
| Standard cost variance account | <p>If you're using standard costing, the account that is specified here will be used to post any variance. This account uses the landed cost breakdown on the **Item prices** page. This breakdown is created by using the periodic routine to update prices.</p><p>For example, the standard cost of an item is $15.00, the FOB is $13.00, and the freight is $2.00. When the invoice is received for the stock, the item is received at $15.00, but there's a standard price variance of $2.00 for the item, because the actual FOB is $13.00. This variance is posted to the standard price variance account that is set up in the item posting profile. Because the estimated freight is $2.00, there is no variance when the stock invoice is posted. However, when the invoice for freight is received, the freight is $2.50 per unit. Therefore, a $0.50 variance is posted to the specified cost. |
| Moving average variance account | <p>If you're using moving average costing, the account that is specified here will be used to post any variance.</p><p>For example, the estimated freight is $2.00. However, when the invoice for freight is received, the freight is $2.50 per unit. Therefore, a $0.50 variance must be posted.</p><p>When the **Post adjustments as variance** option is set to *Yes* on the **Landed cost parameters** page, all variances between estimated and actual shipment costs will be posted to the moving average variance account that is specified here. When the **Post adjustments as variance** option is set to *No*, standard functionality will be used, and the variance will be applied either to inventory or to the moving average variance account that is specified here, depending on stock on hand.</p> |
| Charge accrual account | Select the account that is used to accrue for cost estimates when the purchase invoice is posted. This field is used only when the **Use cost type charge accrual account** option is set to *Yes* on the **Costing** FastTab on the **General** tab of the **Landed cost parameters** page. |
| Charge account | Select the account that is used to capture the inbound transportation costs that have been invoiced by a supplier. The amount is posted as a debit. The offset account is the stock variation account. This posting is used only when the **Post to charge account in ledger** option is set to *Yes* on the **Accounts payable parameters** page. |
| Variance account | The account that will be used to offset the charge accruals when the purchase invoice is posted. This field is used only when the **Use cost type charge accrual account** option is set to *Yes* on the **Costing** FastTab on the **General** tab of the **Landed cost parameters** page. |

## Vendor cost type groups

Vendor cost type groups help determine how *auto cost* charges are found and applied to a voyage. Vendors that have similar import costs are linked together. For example, all vendors from emerging markets pay the same duty percentage for the same type of product that is purchased from an established market.

You can maintain vendor cost type groups by going to **Landed cost \> Costing setup \> Vendor cost type groups**. The **Vendor cost type groups** page provides a grid that lists all existing vendor cost type groups. You can use the buttons on the Action Pane to add, remove, and edit rows in the grid.

The following table describes the fields that are available on each row in the grid.

| Field | Description |
|---|---|
| Vendor cost type groups | Enter a unique name for the vendor cost type group (such as *Emerging markets*). |
| Description | Enter a description of the vendor cost type group. This description can provide details about the level or type of charge that is associated with the vendor group. |

## Item cost type groups

Item cost type groups help determine how *auto cost* charges are found and applied to a voyage. Similar items are linked together. For example, all items that have a duty rate of 5 percent might belong to a specific cost type group.

You can maintain item cost type groups by going to **Landed cost \> Costing setup \> Item cost type groups**. The **Item cost type groups** page provides a grid that lists all existing item cost type groups. You can use the buttons on the Action Pane to add, remove, and edit rows in the grid.

The following table describes the fields that are available on each row in the grid.

| Field | Description |
|---|---|
| Item cost type groups | Enter a unique name for the item cost type group (such as *Duty 5%*). |
| Description | Enter a description of the item cost type group. This description can provide details about the level or type of charge that is associated with the item group. |

> [!NOTE]
> The item cost type is linked to the item through the **Cost type group** field on the **Purchase** FastTab of the item's **Released product** page.

## Transfer order cost type groups

Transfer order cost type groups help determine how *auto cost* charges are found. Similar items are linked together. For example, all items that have a duty rate of 7 percent might belong to a specific cost type group.

You can maintain transfer order cost type groups by going to **Landed cost \> Costing setup \> Transfer order cost type groups**. The **Transfer order cost type groups** page provides a grid that lists all existing transfer order cost type groups. You can use the buttons on the Action Pane to add, remove, and edit rows in the grid.

The following table describes the settings that are available on each row in the grid.

| Field | Description |
|---|---|
| Transfer order cost type groups | Enter a unique name for the transfer order cost type group (such as *Duty 7%*). |
| Description | Enter a description of the transfer order cost type group. This description can provide details about the level or type of charge that is associated with the transfer order cost type group. |

> [!NOTE]
> The transfer order cost type is linked to the item through the **Transfer order cost group** field on the **Purchase** FastTab of the item's **Released product** page.

## Cost templates

You use cost templates to set default values for settings that users who are getting the cost estimate might not know. Cost templates can help reduce complexity in the estimation process by minimizing the selections that users must make to get an accurate estimate.

To work with cost templates, go to **Landed cost \> Costing setup \> Cost templates**. On the **Cost templates** page, the list pane on the left shows all current cost templates. You can use the buttons on the Action Pane to add, remove, and edit templates.

The following table describes the settings that are available for each template.

| Field | Description |
|---|---|
| Cost template | Enter a unique name for the cost template. The name typically describes the factor or cost multiplier for the template. |
| Description | Enter a description of the cost template. |
| Shipping company | Select the vendor account of the shipping company to associate with the cost template. |
| Mode of delivery | Select the mode of delivery that the cost template should use when the estimated cost of an item is calculated. This field will help determine the auto costs that are associated with the goods on the cost estimate. |
| Shipping container type | Select the type of shipping container type to associate with the cost template. This field will help determine the auto costs that are associated with the goods on the cost estimate. |
| Customs broker | Select the customs broker (vendor) to associate with the cost template. This field will help determine the auto costs that are associated with the cost estimate. |
| Factor | Enter a factor to apply to the final cost estimate of goods. For example, to add 10 percent to the calculated cost estimate, enter *1.10*. |

## Volumetric divisors

Volumetric divisors are used to calculate the volumetric weight. Each shipping/freight company formulates its own volumetric divisors. In addition, a company's divisors typically vary, depending on the mode of delivery. For example, air and sea often have very different divisors. A company can also make its rules more complex, depending on where it ships from. The system uses the following formula to find the volumetric weight: VolumetricWeight = Volume ÷ VolumetricDivisor.

For example, a package that is sent by air has a volume of 3 cubic meters (m³). The company charges by volumetric weight and applies a volumetric divisor of 6. This divisor is divided by the volume to determine the volumetric weight. Therefore, the volumetric weight for this example is 3 ÷ 6 = 0.5 kilograms (kg).

To set up volumetric divisors, go to **Landed cost \> Costing setup \> Volumetric divisors**. The **Volumetric divisors** page provides a grid that lists all existing volumetric divisors. You can use the buttons on the Action Pane to add, remove, and edit rows in the grid.

The following table describes the fields that are available on each row in the grid.

| Field | Description |
|---|---|
| Shipping company | Select the vendor account of the shipping company that is associated with the volumetric divisor. |
| Cost type code | Select the cost type code that is associated with the volumetric divisor. Use this field to put cost types into reporting buckets. Reports can be printed either by reporting categories or by cost type. |
| From port | Select the "from" port that the volumetric divisor applies to. |
| Volumetric divisor | Enter the volumetric divisor value that applies to the row. The volume of each package will be divided by value that you enter here to determine that package's volumetric weight. |

> [!NOTE]
> The system will use the maximum value between **actual weight** and **volumetric weight**.
