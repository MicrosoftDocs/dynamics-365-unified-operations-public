---
# required metadata

title: No matching result could be found
description: This topic explains how to troubleshoot the Tax Calculation serivce error, No matching result could be found.
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


# No matching result could be found

[!include [banner](../includes/banner.md)]

This topic explains the troubleshooting steps you can take when you receive the error, **No matching result could be found** in the Tax Calcualtion service.

## Symptom 
You might receive the following error, **Header/Lines - 1, Tax group, no matching result could be found.**

```json
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
The issue occurs when the feature setup is incorrect in the Regulatory Configuration Service (RCS).

## Troubleshoot
1. Download the troubleshooting file. For more information, see [Enable debug mode for troubleshooting](tcs-troubleshooting-enable-debug-mode.md)
2. Compare the tax service calculation input with the feature setup to fix the setup issue, The following example uses Tax calculation input.

    ```json

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
The following table lists the Tax group applicability in RCS.

    | Header.Bussiness process | Lines.Business Unit | Header.Ship From Zip Code| Tax Group |
    |--------------------------|---------------------|--------------------------|-----------|
    |        Journal           |                     |                          | Group A   |
    |        Sales             |                     |     30160                | Group B   |

The tax service calculation input indicates that the **Business process** on the **Header** is **Sales**, and **Ship From Zip Code** on the **Header** is **30159**. This is based on the applicability rule setup in RCS. Because there is no matching line the error occurs. 

> [!NOTE]
> If the value in the applicability rule is set as **empty**, the rule is applicable for any value.

## Mitigation
Complete the following steps to mitigate this error.

1. Go to **RCS** > **Globalization features** > **Tax Calculation**. 
2. Create a new version of the feature.
2. Add a line for the corresponding information.

    | Header.Bussiness process | Lines.Business Unit | Header.Ship From Zip Code| Tax Group |
    |--------------------------|:--------------------|:-------------------------|:----------|
    |        Journal           |                     |                          | Group A   |
    |        Sales             |                     |     30160                | Group B   |
    |        Sales             |                     |     30159                | Group B   |

3. Publish the feature setup version.
4. In Finance, go to **Tax** > **Setup** > **Tax Configuration** > **Tax calculation parameters** and select the new version.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
