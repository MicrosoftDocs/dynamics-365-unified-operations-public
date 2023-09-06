---
title: Extend export control rules functionality
description: This article provides information that's useful for developers who are extending rules functionality for implementing export controls.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: overview
ms.date: 08/29/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Extend export control rules functionality

This article provides information that's useful for developers who are extending rules functionality for implementing export controls.

Rules are defined primarily as data in the `msdyn_exportcontroljurisdiction`, `msdyn_exportcontrolrule`, and `msdyn_exportcontrollicense` tables.

## High-level flow

Evaluations are performed per document line. The result is a set of matching restrictions, exceptions, and applicable licenses for each line. If no restrictions are found, the set of exceptions and licenses is empty.

No document-level checks are performed. Instead, the document is considered blocked if there are any restrictions that don't have a matching exception. The following pseudo-code shows how the restrictions, exceptions, and licenses are considered.

```plaintext
foreach (Line in Request)
{
    Line.MatchingRestrictions = FindAnyMatchingRestrictions(Line);

    foreach (MatchingRestriction in Line.MatchingRestrictions)
    {
        Line.MatchingExceptions = FindAnyMatchingExceptions(Line);

        foreach (MatchingException in Line.MatchingExceptions)
        {
            if (MatchingException.RequireLicense)
            {
                Line.ApplicableLincenses = FindApplicableLicenses(Line);
            }
        }
    }
}
```

## Evaluation of an individual rule

The `msdyn_exportcontrolrule` table has fields for information such as the sell-to country/region, ship-to country/region, *de minimis* threshold, and transaction purpose. If a field isn't set, it has no impact on rule evaluation. The values from the line must match *all* rules where a value is set. Otherwise, the rule doesn't apply.

For example, a line has the following values:

- **Sell to country/region:** *France*
- **Ship to country/region:** *Mexico*
- **Transaction purpose:** *Return*
- **De minimis threshold:** *28%*

**Rule example 1**

A rule has the following values:

- **Sell to country/region:** Blank
- **Ship to country/region:** *Mexico, Canada*
- **Transaction purpose:** Blank
- **De minimis threshold:** *25%*

In this case, only the ship-to country/region and *de minimis* values are evaluated. Because the ship-to country/region, Mexico, is in the list of values that's provided by the rule, and 28 percent is more than the 25 percent threshold that's provided by the rule, the rule is evaluated to *true*.

**Rule example 2**

A rule has the following values:

- **Sell to country/region:** *Italy*
- **Ship to country/region:** *Mexico, Canada*
- **Transaction purpose:** Blank
- **De minimis threshold:** blank

In this case, only the sell-to country/region and ship-to country/region values are evaluated. Because the sell-to country/region, France, isn't in the list of values that's provided by the rule, the rule is evaluated to *false* .

A rule applies only if the Export Control Classification Number (ECCN) from the line is one of the codes that are explicitly listed for the rule, or if the ECCN is part of one of the categories for the rule. A rule that's marked as *Apply to All Codes* is automatically evaluated to *true*, regardless of the ECCN that's included on the line.

An exception rule that's marked as *Require License* is evaluated to *true* only if one or more licenses are found that match the line.

License evaluation works in the same way. Fields that are left blank are ignored during validation. If a field has a value (that is, it isn't blank), the item that's being tested must match one of the values in the field. The overall evaluation is *true* only if all fields are evaluated to *true*.

## Power Fx formulas

[Microsoft Power Fx formulas](/power-platform/power-fx/overview) enable complex rules to be expressed for scenarios that aren't simple references to countries/regions or purposes. As is the case for other fields of rules, if a Power Fx formula isn't provided, it has no impact on the rule evaluation. The document object that's being evaluated is passed to the rule and can be used in formulas for comparison.

Here are some examples of Power Fx formulas for export control. For more information, see the [Formula reference](/power-platform/power-fx/formula-reference).

- Documents that are being shipped to one of three countries/regions:

    `CountRows(Filter(["NOR","SWE","FIN"], Value=Document.SellToCountryRegion)) > 0`

- Documents that are being shipped to one of three countries/regions and contain at least one 6A994 product in the US Export Administration Regulations (EAR) jurisdiction:

    `And(CountRows(Filter(["NOR","SWE","FIN"], Value=Document.SellToCountryRegion)) > 0, CountIf(Document.Lines, CountIf(Codes, And(Jurisdiction="EAR",Code="6A994")) > 0) > 0)`

- Documents that are after a specific date and contain no more than five items on any line:

    `And(Document.DocumentDate > Date(2023, 12, 1), CountIf(Document.Lines, Quantity > 5) = 0)`

## Overrides

Export control checks can be overridden at the line code level. Therefore, you can override a failing export control check for one jurisdiction on one line of a document but still enforce checks on other lines. To override an export control check, pass `"msdyn_overridden": true` as a property of one of the line codes in the `msdyn_CheckExportControlLineCodes` collection. The export checks are still evaluated, and any informational or warning messages are still shown. However, any error messages are downgraded to warning messages and don't block the activity.
