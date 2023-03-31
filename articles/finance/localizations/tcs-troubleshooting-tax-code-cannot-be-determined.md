---
# required metadata

title: Tax code cannot be determined
description: This article explains how to troubleshoot the "Tax code cannot be determined" error in the Tax Calculation service.
author: hangwan
ms.date: 03/25/2022
ms.topic: how-to
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

This article explains the troubleshooting steps that you can take if you receive a "Tax code cannot be determined" error in the Tax Calculation service.

## Symptom

You receive the following error message: "Header/Lines - 1, tax code cannot be determined." Alternatively, you find the error in the troubleshooting file, as shown in the following example. For more information, see [Enable debug mode for troubleshooting](tcs-troubleshooting-enable-debug-mode.md).

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

The issue is probably occurring because the tax group and the item tax group don't intersect.

## Troubleshoot

Follow these steps to troubleshoot the issue.

1. In the troubleshooting file, verify that tax group and item tax group have been determined. If the values for **Tax Group** and **Item Tax Group** are blank, the tax group and item tax group haven't been determined. If they have been determined, the results might be incorrect.

    Here is an example of a troubleshooting file.

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

2. Verify that the **Override sales tax** option on the **Setup** tab of the sales order line details is enabled.

    - If it's enabled, tax codes are determined by the **Tax group** and **Item tax group** values that you enter on the transaction line. Verify that these values are entered correctly.
    - If it isn't enabled, verify that correct values have been set for the **Tax group applicability** and **Item tax group applicability** fields. For more information, see [No matching result be found](tcs-troubleshooting-no-matching-result.md) to.

3. If the tax group and item tax group have been determined correctly, determine whether there is any intersection for them.

    1. In RCS, go to **Tax features** \> **Tax codes and groups** \> **Tax group**.

        | Line.Tax Group | Tax Codes |
        |----------------|-----------|
        | Group A        | A         |

    2. Go to **Tax features** \> **Tax codes and groups** \> **Item tax group**.

        | Line.Item Tax Group | Tax Codes |
        |---------------------|-----------|
        | Group B             | B         |

    If there is no intersection for the tax group and the item tax group, the tax code won't be determined.

## Mitigation

1. Go through each step in the [Troubleshoot](#troubleshoot) section of this article, and fix the setup as required. If the tax group and item tax group haven't been determined correctly, see [No matching result be found](tcs-troubleshooting-no-matching-result.md).
2. If there is no intersection for the tax group and the item tax group, create a new feature version in RCS, and fix the setup.

    - Go to **Tax features** \> **Tax codes and groups** > **Item tax group**.

        | Line.Item Tax Group | Tax codes |
        |---------------------|-----------|
        | Group B             | A;B       |

    The tax code will be determined as **A**.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
