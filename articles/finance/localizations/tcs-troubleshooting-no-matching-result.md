---
# required metadata

title: No matching result could be found
description: This topic explains how to troubleshoot error "No matching result could be found" in Tax Calcualtion service.
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


# No matching result could be found

This topic explains how to troubleshoot error "No matching result could be found" in Tax Calcualtion service.

## Symptom 
Facing the error like - "Header/Lines - 1, Tax group, no matching result could be found".

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
                    "Code": "TaxSetup20000",
                    "Message": "Header/Lines - 1, Tax group applicability, no matching result could be found."
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
The issue caused by the feature setup in RCS do not have the correct setup.

## Troubleshoot
1. Download the troubleshoot file, refer to [Enable debug mode for troubleshooting](./tcs-troubleshooting-enable-debug-mode.md)
2. Compare the tax service calculation input with the feature setup to fix the setup issue. e.g
   - Tax calculation input:
    ```json
    ===============================Tax service calculation input JSON:=====================================
    {
        "TaxableDocument": {
        "Header": [
            {
            "Lines": [
                {
                ...
                }
            ],
            "Business Process": "Sales",
            "Ship From Zip Code": "30159",

            }
        ]
        },
        "Parameter": {
        ...
        },
        "Adjustment": {
        "Lines": {}
        }
    }
    ```
    - Tax group applicability in RCS

    | Header.Bussiness process | Lines.Business Unit | Header.Ship From Zip Code| Tax Group |
    |--------------------------|:--------------------|:-------------------------|:----------|
    |        Journal           |                     |                          | Group A   |
    |        Sales             |                     |     30160                | Group B   |

    The tax service calculation input indicate `Business process` on `Header` is `Sales`, and `Ship From Zip Code` on `Header` is `30159`, based on the applicability rule setup in RCS, there is no matching line, so the error throw. Note, if the value in applicability rule set as **empty**, it means applicable for **any value**.

## Mitigation

1. Go to RCS -> Globalization features > Tax Calculation. 
2. Create a new version of the feature.
2. Add line for corresponding input.
    | Header.Bussiness process | Lines.Business Unit | Header.Ship From Zip Code| Tax Group |
    |--------------------------|:--------------------|:-------------------------|:----------|
    |        Journal           |                     |                          | Group A   |
    |        Sales             |                     |     30160                | Group B   |
    |        Sales             |                     |     30159                | Group B   |

3. Publish feature setup version.
4. Select the new version in Finance Tax > Setup > Tax Configuration > Tax calculation parameters.
