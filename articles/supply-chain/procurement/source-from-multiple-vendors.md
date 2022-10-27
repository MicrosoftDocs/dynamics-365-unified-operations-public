---
title: Source products and materials from multiple vendors
description: With this feature, the system automatically suggests a vendor for each planned purchase order so that, over time, the percentages specified are respected.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 10/27/2022
ms.custom: bap-template
---

# Source products and materials from multiple vendors

Diversifying the supply network helps businesses be agile and responsive to changes. One of the most common ways to diversify supply is to balance (split) the supply of a certain product into different vendors according to some percentages. That is the case for having a main vendor and a secondary one, where the usual split is 80%/20% or 70%/30%. Or other strategies such as dividing equally into 3 different vendors 33/33/33.

With this feature, the system automatically suggests the vendor for a planned purchase order so that over time the percentages specified are respected. It assigns a vendor for a certain planned order that, over time, matches the percentages set. However, it won't split an existing planned order into several smaller orders.

A simple example can be seen here on how the whole planned order quantity is assigned to a single vendor balancing both (and the order quantity is NOT split):

| Demand | Vendor A quantity (target: 50%) | Vendor B quantity (target: 50%) |
|---|---|---|
| 100 | 100 | 0 |
| 100 | 0 | 100 |
| 200 | 200 | 0 |
| 100 | 0 | 100 |
| 100 | 0 | 100 |

The automatic vendor selection based on predefined splits secures improved supplier resilience, without needing to keep outside track of the purchases to the vendors outside the system as you are also able to keep track of the actual purchases and percentages versus the targeted ones.

## Turn on multisource for your system

This feature is available for Planning Optimization.

Before you can Source products and materials from multiple vendors, it is a prerequisite that the following feature is turned on for your system. Admins can use feature management settings to check the status of these features and turn them on. The feature that must be enabled is:

- Source products and materials from multiple vendors using Planning Optimization

## Setup the split policy for a product

### Define the multisource policy

To define what split should be kept between vendors, a multisource policy must be created.

Go to **Procurement and sourcing \> Setup \> Policies \> Multisource policies** to define a policy.

Create a policy:

- Click on New
- Enter a name for the policy
- You can optionally enter a description for the same
- Define the **balance period (days):** it is the number of periods in days that Planning Optimization should look into the past when allocating orders for a vendor. In other words, when master planning is choosing a vendor for a planned purchase order, it will look this number of days in the past and choose the vendor that will result in an actual allocation that is closest to the preferred allocation established in the multisource policy. We recommend that you choose a balance period that will include purchases from the relevant vendors but without going too far back. By default, it is 180 days.
- Define the vendors and the percentages to be targeted (**Target allocation (%)**). The sum of the percent
- Then, activate the policy.

Only active policies can be assigned to products to help you manage the policies that are in use and the ones that may be obsolete or you are working on defining.

### Assign the multisource policy to a product

To specify which product or set of products the policy is valid for you can associate the policy with the product in the form Multisource policy assignments that can be found under **Procurement and sourcing \> Setup \> Policies \> Multisource policy assignments**.

You can define the item it applies to, or to which item in site and warehouse. Additionally, you can set up a period for which the multisource policy is valid.

### Define minimum order quantities per vendor

In many cases, there are some vendors that require that a minimum number of units of the product are bought from them.

For these cases, it is possible to setup the minimum order quantity per vendor by clicking on **Order quantity per vendor** button on the action pane of the **Multisource policy** form.

These minimum order settings apply to all multisource policies and only to multisource policies. This implies that when purchase orders are manually created, these minimum order quantities per vendor are not respected.

## Review the current vendor allocation versus the targeted

For each of the multisource policy assignments it is possible to review which is the actual purchased quantities and vendor percentages split versus what were the targeted. From the **Multisource policy assignment** form, click on **Current allocation** from the top panel.

When Planning Optimization suggests the vendor for a planned purchase order it will do so such that the vendor that makes it closer to the targeted percentages is selected.

This is useful to see if your purchasing department is just firming the orders as they are and then the target percentages are filled or if any changes are being made to the suggested.

When showing the balance, it also takes into account firmed orders for the period when the policy assignment is valid and they start counting since the beginning of the assigned policy.

## Manage multisource policies

Managing policies can be cumbersome when you are negotiating with vendors, and you may have some policies that do not apply anymore. For this reason, you can inactivate policies.

When a policy is inactive, it cannot be assigned to a product, and it is not shown when policies are assigned to the product.

## How Planning Optimization will suggest the vendor

**When a multisource policy will be applied (when the different vendors will be considered):**

- A multisource policy has been assigned for the product.

- Matching its dimensions (site, warehouse, or product dimensions) if specified.

- The demand falls during the multisource assignment period.

- The most specific policy assignment is used. For example, if there is demand for the item A0001 site 1 warehouse 11 and the two below policies exist, then policy X will be used as it is the most specific one:

| Item | Site | Warehouse | From date | To date | Policy |
|---|---|---|---|---|---|
| A0001 | 1 | | 24/10/2022 | | X |
| A0001 | 1 | 11 | 24/10/2022 | | Y |

- Classic vendor selection based on cost/price is not performed with trade agreements. If a multisource policy is established, it is understood that the percentages are targeted.
- If a vendor lead time is specified in a trade agreement, it is respected.
- Approved vendor list is respected if setup.
  - If the system is set up to not allow other vendors than the approved vendors (**Approved vendor check method** setup to **Not allowed**), the system will respect it. A vendor specified in the multisource policy will not be selected if not approved. For context the Approved vendor check method is defaulted on the item model group and can also be overwritten at the released product level.
- Default order settings are respected
  - When master planning creates planned purchase orders for the item, the minimum, the multiple and maximum values established in default order settings are respected (if specified)
  - Then, if a minimum order quantity value per vendor has been specified then it will be applied. This means that the highest of the minimum in default order settings and the vendor minimum is applied.

**Example of how the vendor is selected with a multisource policy:**

- Targeted percentages on the top of the grid
- X if the vendor was selected for supplying the given demand
- On the right side of the grid, it is represented how planning chooses the vendor: trying to target the percentages, so it can be seen how the quantities (accumulated) would be over A and B if the vendor was chosen, as well as its percentages. The vendor that makes the percentage closer to the targeted is selected.
- Accumulated quantity column is shown (accumulated demand)
- If vendor A is selected
  - qty A= accumulated quantity for vendor A
  - %A = qty A/accumulated quantity (total)
  - Deviation = (%A +%B)/2 taking %A and %B in absolute value
- Dates for demand within the policy assignment dates

And on a more complex example to showcase how the vendor is selecting according to the one that has the lowest deviation towards the targeted percentages:

| Demand | Vendor A quantity (target:&nbsp;80%) | Vendor B quantity (target:&nbsp;20%) | If vendor A is selected:</br>Qty&nbsp;A&nbsp;\|&nbsp;Qty&nbsp;B</br>A%&nbsp;\|&nbsp;B%</br>Deviation | If vendor B is selected:</br>Qty&nbsp;A&nbsp;\|&nbsp;Qty&nbsp;B</br>A%&nbsp;\|&nbsp;B%</br>Deviation | Accumulated quantity (total) |
|---|---|---|---|---|---|
| 100 | 100 | 0 | 100 \| 0</br>100% \| 0%</br>20% | 0 \| 100</br>0% \| 100%</br>80% | 100 |
| 100 | 100 | 0 | 200* \| 0</br>100% \| 0%</br>20%** | 100 \| 100</br>50% \| 50%</br>25% | 200 |
| 100 | 0 | 100 | 300 \| 0</br>100% \| 0%</br>20% | 200 \| 100</br>66% \| 33%</br>13% | 300 |

\* 100 accumulated + current demand</br>\*\* Average of (100-80), (20-0) = average (20,20) = 20
