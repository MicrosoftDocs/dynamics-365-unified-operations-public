---
title: Extend export control rules functionality
description: This article provides information that is useful for developers who are extending rules functionality for implementing export controls
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: overview
ms.date: 07/31/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Extend export control rules functionality

This article provides information that is useful for developers who are extending rules functionality for implementing export controls.

Rules are defined primarily as data in the `msdyn_exportcontroljurisdiction`, `msdyn_exportcontrolrule`, and `msdyn_exportcontrollicense` tables.

## High level flow

Evaluations are performed per document line. The result is a set of matching restrictions, exceptions, and applicable licenses for each line. If no restrictions were found, then set of exceptions and licenses will be empty.

No document-level checks are performed. Instead, the document is considered blocked if there are any restrictions that don't have a matching exception.  The following pseudo-code illustrates how the restrictions, exceptions and licenses are considered.

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

The `msdyn_exportcontrolrule` table has various fields such as sell to country/region, ship to country/region, de minimis threshold, and transaction purpose. If a field isn't set, then it has no impact on rule evaluation. The values from the line must match *all* rules that have a value set in order for the rule to apply.

Consider a line with the following values:

- Sell to country/region = France
- Ship to country/region = Mexico
- Transaction purpose = Return
- De minimis threshold = 28%

Rule Example 1:

- Sell to country/region = (empty)
- Ship to country/region = Mexico, Canada
- Transaction purpose = (empty)
- De minimis threshold = 25%
- This rule evaluates to *true* because only the ship to country/region and de minimis values are evaluated. Because 28% is greater than the 25% threshold and the ship to country/region is Mexico, the rule evaluates to true.

Rule Example 2:

- Sell to country/region = Italy
- Ship to country/region = Mexico, Canada
- Transaction purpose = (empty)
- De minimis threshold = (empty)
- This rule evaluates to *false* because the sell to country/region of France isn't in the list of values provided by the rule.

A rule only applies if the export control classification number (ECCN) for the line is one of the codes listed for the rule explicitly, or if the ECCN is part of one of the categories for the rule. A rule marked as *Apply to All Codes* will automatically evaluate to true regardless of what ECCN is included on the line.

If an exception rule is marked as *Require License*, then it evaluates to true only if one or more licenses are found that match the line.

License evaluation works in the same way. Fields that are left empty are ignored in validation. If a field isn't empty, then the item being tested must match one of the values in the field. All fields must evaluate to true in order for the overall evaluation to be true.

## Power Fx Formulas

[Power Fx formulas](/power-platform/power-fx/overview) allow complex rules to be expressed for scenarios that aren't simple references to countries/regions or purposes. Like other fields of rules, if a Power Fx formula isn't provided, then it has no impact on the rule evaluation. The document object being evaluated is passed to the rule and can be used in formulas for comparison.

Following are various examples of Power Fx formulas for Export Control. For more information, see the [Formula reference](/power-platform/power-fx/formula-reference)

- Documents being shipped to one of three countries/regions:
    ```CountRows(Filter(["NOR","SWE","FIN"], Value=Document.SellToCountryRegion)) > 0```
- Documents being shipped to one of three countries/regions containing at least one 6A994 product in the EAR jurisdiction:
    ```And(CountRows(Filter(["NOR","SWE","FIN"], Value=Document.SellToCountryRegion)) > 0, CountIf(Document.Lines, CountIf(Codes, And(Jurisdiction="EAR",Code="6A994")) > 0) > 0)```
- Documents after a specific date containing no more than five items on any line:
    ```And(Document.DocumentDate > Date(2023, 12, 1), CountIf(Document.Lines, Quantity > 5) = 0)```

## Overrides

Export control checks may be overridden at a line code level. This allows overriding a failing export control check for one jurisdiction on one line of a document, while still enforcing checks on other lines. To override the export control check, pass `"msdyn_overridden": true` as a property of one of the line codes in the `msdyn_CheckExportControlLineCodes` collection. The export checks will still be evaluated, and any info or warning messages will still be shown. However, any error messages will be downgraded to warning messages and won't block the activity.
