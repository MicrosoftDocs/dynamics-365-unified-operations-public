---
# required metadata

title: Tax code cannot be determined
description: This topic explains how to troubleshoot error "tax code cannot be determined" in Tax Calcualtion service.
author: hangwan
ms.date: 03/23/2022
ms.topic: business-process
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: TaxIntegrationTaxServiceParameters
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: hangwan
ms.search.validFrom: 03/23/2022
ms.dyn365.ops.version: Version 10.0.21
---

# Tax code cannot be determined

This topic explains how to troubleshoot error "tax code cannot be determined" in Tax Calcualtion service.

## Symptom 
Facing the error like - "Header/Lines - 1, tax code cannot be determined.", or the find the error in troubleshooting file, [Enable debug mode for troubleshooting](./Enable-debug-mode-for-troubleshooting.md)
```json
    ======================Tax service calculation result JSON:===========================
    {
      "taxDocument": {
        "Header": [
          {
            "Lines": [
              {
                ...
                "Errors": [
                  {
                     "Code": "TaxSetup20001",
                     "Message": "Header/Lines - 1, tax code cannot be determined."
                  }
                ],
                "Adjustment": null
              }
            ],
            "Measures": {
              ...
            },
            ...
          }
        ]
      },
      ...
    }
```

## Cause
The issue probably casing `Tax group` and `Item tax group` do not have any intersection

## Troubleshoot
1. Check if `Tax group` and `Item tax group` are determined in troubleshooting file. if they are empty means do not determine. e.g.
```json
    ======================Tax service calculation result JSON:===========================
    {
      "taxDocument": {
        "Header": [
          {
            "Lines": [
              {
               "Tax Codes": {},
               "Measures": {
                  "Tax Group": "Group A",
                  "Item Tax Group": "Group B"
               },
               "Adjustment": null
              }
            ],
            "Measures": {
              ...
            },
            ...
          }
        ]
      },
      ...
    }
```
2. If `Tax group` and `Item tax group` are determined, but determined with an incorrect result.
   - Check if `Override sales tax` on sales order line details setup tab is enabled or not, if enabled. means tax codes will determine by the `Tax group` and `Item tax group` which you input in the transaction line, make sure they are filled correctly.

   - If `Override sales tax` is not enabled. please follow the [No matching result be found](./tcs-troubleshooting-no-matching-result.md) to check if `Tax group applicability` and `Item tax group applicability` have been determined with the correct value.
3. If `Tax group` and `Item tax group` are determined correctly, then check if they any intersection.
   - Go to RCS > Tax features, Tax codes and groups > Tax Group
   
      | Line.Tax Group | Tax Codes |
      |----------------|:----------|
      |   Group A      |     A     |

   - Tax codes and groups > Item Tax Group
      | Line.Item Tax Group | Tax Codes |
      |---------------------|:----------|
      |   Group B           |     B     |

   Result: No intersection, tax code will not be determined.

## Mitigation
1. Check each step in `troubleshoot` and then fix the step up. if `Tax Group` and `Item Tax Group` is not determined correctly, check [No matching result be found](./tcs-troubleshooting-no-matching-result.md).
2. If no intersection for `Tax Group` and `Item Tax Group`, go to RCS, create a new feature version, fix the setup.
   - Tax codes and groups > Item Tax Group
      | Line.Item Tax Group | Tax Codes |
      |---------------------|:----------|
      |   Group B           |     A;B   |
3. Then `Tax Code` will be determined with `A`
