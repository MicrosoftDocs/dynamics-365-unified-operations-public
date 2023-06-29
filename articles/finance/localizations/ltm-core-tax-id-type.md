---
title: Tax ID types for Latin America 
description: This article provides information about the tax ID type configuration for Latin America. 
author: Fhernandez0088
ms.date: 01/31/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 
ms.custom: bap-template
---

# Tax ID types for Latin America

[!include [banner](../includes/banner.md)]

Use this configuration to enter valid tax ID types in each country/region and identify the entities that the company operates with. These entities can include customers, vendors, contacts, banks, and employees.

## Prerequisites

Before you can set up a tax ID type with a fiscal codification, the tax application must already be configured.

## Set up a tax ID type

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax ID type**.
2. In the **Overview** section, in the **Tax ID type** field, enter the register code.
3. In the **Description** field, enter a brief description of the tax ID type.
4. In the **Settings** section, in the **Mask validation method** field, select one of the following validation methods.

    | Method   | Description |
    |----------|-------------|
    | Basic    | Use a simplified mask to define the number and types of characters. **A** represents alphabetic characters, **9** represents numeric characters, and **X** represents alphanumeric characters. Symbols such as hyphens (-) and periods (.) can also be added to the mask. |
    | Advanced | Use a complete mask with SQL sentences to define each character. The mask can include alphabetic characters (A–Z), numeric characters (0–9), and alphanumeric characters (A–Z, 0–9). Symbols such as hyphens (-) and slashes (/) can also be added to the mask. |
    | None     | The mask isn't validated, and the **Mask** and **Length** fields can't be edited. |

5. In the **Mask** field, enter the mask format. The **Length** field is automatically set to the number of characters in the **Mask** value.
6. In the **Verification algorithm** field, select one of the following options.

    | Verification algorithm                                                    | Description |
    |---------------------------------------------------------------------------|-------------|
    | No verification                                                           | No verification of the tax ID is done. |
    | CUIT verification - Argentina                                             | The verification algorithm verifies that the tax ID is valid for Argentina. |
    | RUT verification - Chile                                                  | The verification algorithm verifies that the tax ID is valid for Chile. |
    | RUC verification - Peru                                                   | The verification algorithm verifies that the tax ID is valid for Peru. |
    | NIT verification - Colombia                                               | The verification algorithm verifies that the Tax ID is valid for Colombia. |
    | RUC verification - Ecuador - Legal / Foreign person without identity card | The verification algorithm verifies that the tax ID is valid for Ecuador. |
    | Identity card verification - Ecuador                                      | The verification algorithm verifies that the tax ID is valid for Ecuador. |
    | RUC verification – Ecuador – Natural person                               | The verification algorithm verifies that the tax ID is valid for Ecuador. |
    | RUT verification – Uruguay                                                | The verification algorithm verifies that the tax ID is valid for Uruguay. |

7. Set the following options according to the characteristics of the tax ID type.

    | Field                 | Description |
    |-----------------------|-------------|
    | Country document type | Set this option to **Yes** to specify that the tax ID type is at the country/region level, not at the state level. |
    | State document type   | Set this option to **Yes** to specify that the tax ID type is at the state level. |
    | Foreign document type | Set this option to **Yes** to specify that the tax ID type can be selected in the countries/regions' address configurations for all foreign countries/regions. |

9. On the Action Pane, select **Save** to finish the configuration and save the record.

## Add the fiscal codification provided by the fiscal authorities

You can use the **Tax application** option to add the fiscal codification that's provided by the fiscal authorities.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Taxpayer type**.
2. On the Action Pane, select **Tax application**.
3. Select **New** to add a line to the grid.
4. In the **Tax application Id** field, select a value.
5. In the **Tax application code** field, enter the code that the fiscal authority uses to identify the tax ID type.
6. Select **Save**.
