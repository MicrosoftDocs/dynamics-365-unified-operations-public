---
# required metadata

title: Tax code can't be determined
description: This topic explains how to troubleshoot the error, "Tax code cannot be determined" in the Tax Calcualtion service.
author: hangwan
ms.date: 03/25/2022
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

[!include [banner](../includes/banner.md)]

This topic explains how to troubleshoot the error, **Tax code cannot be determined** in the Tax Calcualtion service.

## Symptom 
You might receive the error, **Header/Lines - 1, tax code cannot be determined.** or, you might find find the error in the troubleshooting file, [Enable debug mode for troubleshooting](tcs-troubleshooting-enable-debug-mode.md).

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
The issue is likely occuring because **Tax group** and **Item tax group** are not intersecting.

## Troubleshoot
Complete the following steps to troubleshoot this issue.

1. In the troubleshooting file, verify whether **Tax group** and **Item tax group** have been determined. If they are empty, this means they are not determined. 
For example, 

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

   If **Tax group** and **Item tax group** are determined, it might be with an incorrect result.
   
2. Check whether **Override sales tax**` on the sales order line details **Setup** tab is enabled. 

    - If it is enabled, tax codes are determined by the **Tax group** and **Item tax group** which you enter on the transaction line. Verify that these are entered correctly. 
    - If **Override sales tax** isn't enabled. see [No matching result be found](tcs-troubleshooting-no-matching-result.md) to check if **Tax group applicability** and **Item tax group applicability** have been determined with the correct value.
3. If **Tax group** and **Item tax group** are determined correctly, check if they any intersection.
4. Go to **RCS** > **Tax features**, **Tax codes and groups** > **Tax Group**
   
      | Line.Tax Group | Tax Codes |
      |----------------|:----------|
      |   Group A      |     A     |

   - **Tax codes and groups** > **Item Tax Group**
     
      | Line.Item Tax Group | Tax Codes |
      |---------------------|:----------|
      |   Group B           |     B     |

 If there is no intersection, the tax code will not be determined.

## Mitigation
1. Check each step in `troubleshoot` and then fix the step up. If **Tax Group** and **Item Tax Group** aren't determined correctly, see [No matching result be found](tcs-troubleshooting-no-matching-result.md).
2. If there is no intersection for **Tax Group** and **Item Tax Group**, go to RCS, create a new feature version, and fix the setup.
  
  - **Tax codes and groups** > **Item Tax Group**
      | Line.Item Tax Group | Tax Codes |
      |---------------------|:----------|
      |   Group B           |     A;B   |

   The **Tax Code** will be determined with **A**.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
