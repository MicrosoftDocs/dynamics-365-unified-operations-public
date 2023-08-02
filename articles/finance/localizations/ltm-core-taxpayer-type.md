---
title: Taxpayer types for Latin America 
description: This article provides information about the taxpayer type configuration for Latin America. 
author: Fhernandez0088
ms.date: 01/31/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 
ms.custom: bap-template
---

# Taxpayer types for Latin America 

[!include [banner](../includes/banner.md)]

You can set up the types of tax-responsible entities that the company operates with. These entities can include customers, vendors, employees, and even the company itself.
 
## Prerequisites

The following prerequisites must be met before you can set up taxpayer types for organizations in Latin America:

- Tax ID types must be configured.
- Document class letters must be configured.

## Set up a taxpayer type for Latin America

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Taxpayer type**.
2. In the **General** section, in the **Taxpayer type** field, enter the register's code.
3. In the **Description** field, enter an explanation of the taxpayer type.

    > [!NOTE]
    > The **Taxpayer type** and **Description** fields are required.

4. In the **Settings** section, set the options as required to complete the configuration according to the characteristics of the taxpayer type.

    | Option                                  | Description |
    |-----------------------------------------|-------------|
    | Foreign taxpayer                        | Set this option to **Yes** if the registered entity is foreign. |
    | Validate vendor AC                      | Set this option to **Yes** if the authorization code that the vendor issues must be validated. |
    | Internal taxpayer                       | Set this option to **Yes** if the taxpayer is internal and doesn't represent a real entity. No transactions that are made by entities of this taxpayer type will be entered on tax reports. |
    | Mandatory country of residence          | Set this option to **Yes** to make the **Country of residence** field required in the entity configuration. |
    | Mandatory registered jurisdiction       | Set this option to **Yes** to make the **Registered jurisdiction** field required in the entity configuration. |
    | Mandatory country identification number | Set this option to **Yes** to make the **Country identification number** field required in the entity configuration. |
    | Mandatory state identification number   | Set this option to **Yes** to make the **State identification number** field required in the entity configuration. |

5. In the **Document types** grid, add the tax Id types that are associated with the taxpayer type according to the country/regions's legislation.

    > [!NOTE]
    > This configuration and the tax ID type configuration in the country/region address book will let you filter or directly assign the tax ID type in the customer or vendor record.

6. In the **Document class letter** grid, select the IDs that the taxpayer type uses in transactions.
7. Select **Save**.

## Add the fiscal codification provided by the fiscal authorities

You can use the **Tax application** option to add the fiscal codification that's provided by the fiscal authorities.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Taxpayer type**.
2. On the Action Pane, select **Tax application**.
3. Select **New** to add a line to the grid.
4. In the **Tax application Id** field, select a value.
5. In the **Tax application code** field, enter the code that the fiscal authority uses to identify the taxpayer type.
6. Select **Save**.
