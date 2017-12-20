---
# required metadata

title: Shift depreciation calculation for Indian fixed assets
description: This topic walks you through the process of calculating shift depreciation for India fixed assets in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition.
author: AdamTrukawka
manager: AnnBe
ms.date: 12/01/2017
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang:
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm:
# ms.custom:
ms.search.region: India
# ms.search.industry:
ms.author: atrukawk
ms.search.validFrom: 2017-12-31
ms.dyn365.ops.version: 7.3

---

# Shift depreciation calculation
[!include[banner](../includes/banner.md)]

You can calculate shift depreciation for fixed assets Accordingly to The Indian Companies Act, 1956. You can activate shift depreciation calculation in **Depreciation profiles**. Once **Shift depreciation** option is selected in depreciation profile you can select from Action Pane **Shift depreciation** to define periods of shifted levels depreciation calculation and their percentages.

## Example

The example in this section shows how the number of days that an asset is used is calculated.

An asset is used from December 21, 2012, through March 31, 2013. Here is a breakdown of the days for each period in the fixed asset calendar:

- **December 21, 2011, through December 31, 2011:** 11 days
- **January 1, 2012, through January 31, 2012:** 31 days
- **February 1, 2012, through February 29, 2012:** 29 days
- **March 1, 2012, through March 31, 2012:** 31 days

Therefore, the total number of days that the asset is used is 102 (11 + 31 + 29 + 31).

## Depreciation for non-working days

Depreciation for non-working days is calculated as single-shift depreciation.

- Single-shift depreciation is always calculated on a 365/365 basis. Double-shift and triple-shift depreciation are calculated on regular working days in a year (180 days for seasonal industries or 240 days for non-seasonal industries).
- If the value model that is attached to the depreciation profile uses the Straight line percentage or Reducing balance depreciation method, but a shift depreciation type isn't defined in the value model, no depreciation is calculated for shifts.
- If shift depreciation is defined in the value model, but shift depreciation rates aren't defined in the depreciation profile, the standard depreciation rate applies as single shift. If shift depreciation rates are defined, they have precedence over the standard rate.
- The total number of working days for single shift, double shift, or triple shift in a period can't exceed the number of days that are defined in the ledger period.
- Depreciation for non-working days (calendar days in a period minus the days that are defined in a ledger period) is calculated as single-shift depreciation.

## Shift depreciation formulas

The following table shows the various formulas that are used to calculate shift depreciation.

| Type of depreciation method                         | Type of industry | Number of working days for the industry | Formula |
|-----------------------------------------------------|------------------|-----------------------------------------|---------|
| Straight-line percentage method                     | Seasonal | More than the number of days in the **Min. working days for seasonal industries** field on the **Fixed assets parameters** page | \[(Cost of acquisition – Scrap value) × Percentage that is defined for the type of shift\] × Number of days that the asset is used during the period ÷ Total number of working days in a year |
| Straight-line percentage method                     | Seasonal | Less than the number of days in the **Min. working days for seasonal industries** field on the **Fixed assets parameters** page | \[(Cost of acquisition – Scrap value) × Percentage that is defined for the type of shift\] × Number of days that the asset is used during the period ÷ Minimum number of working days for seasonal industries (180 days) |
| Straight-line percentage method                     | Non-seasonal | More than the number of days in the **Min. working days for non-seasonal industries** field on the **Fixed assets parameters** page | \[(Cost of acquisition – Scrap value) × Percentage that is defined for the type of shift\] × Number of days that the asset is used during the period ÷ Total number of working days in a year |
| Straight-line percentage method                     | Non-seasonal | Less than the number of days in the **Min. working days for non-seasonal industries** field on the **Fixed assets parameters** page | \[(Cost of acquisition – Scrap value) × Percentage that is defined for the type of shift\] × Number of days that the asset is used during the period ÷ Minimum number of working days for non-seasonal industries (240 days) |
| Reducing-balance method                             | Seasonal | More than the number of days in the **Min. working days for seasonal industries** field on the **Fixed assets parameters** page | \[(Written-down value – Scrap value) × Percentage that is defined for the type of shift\] × Number of days that the asset is used during the period ÷ Total number of working days in a year |
| Reducing-balance method                             | Seasonal | Less than the number of days in the **Min. working days for seasonal industries** field on the **Fixed assets parameters** page | \[(Written-down value – Scrap value) × Percentage that is defined for the type of shift\] × Number of days that the asset is used during the period ÷ Minimum number of working days for seasonal industries (180 days) |
| Reducing-balance method                             | Non-seasonal | More than the number of days in the **Min. working days for non-seasonal industries** field on the **Fixed assets parameters** page | \[(Written-down value – Scrap value) × Percentage that is defined for the type of shift\] × Number of days that the asset is used during the period ÷ Total number of working days in a year |
| Reducing-balance method                             | Non-seasonal | Less than the number of days in the **Min. working days for non-seasonal industries** field on the **Fixed assets parameters** page | \[(Written-down value – Scrap value) × Percentage that is defined for the type of shift\] × Number of days that the asset is used during the period ÷ Minimum number of working days for non-seasonal industries (240 days) |
| Straight-line percentage or Reducing-balance method | Seasonal or Non-seasonal | On the **Value models** page, select the **Override fixed asset calendar days?** check box, and specify the number of days in the **Asset working days** field. | \[(Cost of acquisition or Written-down value – Scrap value) × Percentage that is defined for the type of shift\] × Number of days that the asset is used during the period ÷ Asset working days |

Full depreciation is calculated if the value of an asset is less than or equal to the value that is specified in the **Max. acquisition value to avail full depreciation** field on the **Fixed assets parameters** page. In this case, the days that are specified in the **Min. working days for seasonal industries** field or the **Min. working days for non-seasonal industries** field aren't considered when depreciation is calculated.
