---
title: Taxpayer types for Latin America 
description: Learn about the taxpayer type configuration for Latin America, including prerequisites and a process for setting up a taxpayer type.
author: SandraYamamoto0602
ms.author: v-sandraya
ms.topic: how-to
ms.date: 01/05/2026
ms.custom: bap-template
ms.reviewer: johnmichalak 
---

# Taxpayer types for Latin America 

[!include [banner](../../includes/banner.md)]

[!include [does not apply to](includes/does-not-apply-to.md)]

You can set up the types of tax-responsible entities that the company operates with. These entities can include customers, vendors, employees, and even the company itself.
 
## Prerequisites

The following prerequisites must be met before you can set up taxpayer types for organizations in Latin America:

- The legal entity must have an address in a country or region within the LATAM localization.
- Both the region-specific LATAM feature and the general feature must be enabled.
- Tax ID types must be configured.
- Document class letters must be configured.

## Set up a taxpayer type for Latin America

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Taxpayer type**.
1. In the **General** section, in the **Taxpayer type** field, enter the register's code.
1. In the **Description** field, enter an explanation of the taxpayer type.

    > [!NOTE]
    > The **Taxpayer type** and **Description** fields are required.

1. In the **Settings** section, set the options as required to complete the configuration according to the characteristics of the taxpayer type.

    | Option                                  | Description |
    |-----------------------------------------|-------------|
    | Foreign taxpayer                        | Set this option to **Yes** if the registered entity is foreign. |
    | Validate vendor AC                      | Set this option to **Yes** if the authorization code that the vendor issues must be validated. |
    | Internal taxpayer                       | Set this option to **Yes** if the taxpayer is internal and doesn't represent a real entity. No transactions that are made by entities of this taxpayer type will be entered on tax reports. |
    | Mandatory country of residence          | Set this option to **Yes** to make the **Country of residence** field required in the entity configuration. |
    | Mandatory registered jurisdiction       | Set this option to **Yes** to make the **Registered jurisdiction** field required in the entity configuration. |
    | Mandatory country identification number | Set this option to **Yes** to make the **Country identification number** field required in the entity configuration. |
    | Mandatory state identification number   | Set this option to **Yes** to make the **State identification number** field required in the entity configuration. |

1. In the **Document types** section, complete the grid with  **Tax Id types** that are associated with the taxpayer type according to the country/region's legislation.

    > [!NOTE]
    > This configuration and the tax ID type configuration in the country/region address book will let you filter or directly assign the tax ID type in the customer or vendor record.

1. In the **Document class letter** section,  complete the grid with **Document class letter IDs** that the taxpayer type uses in transactions.
1. Select **Save**.

## Add the fiscal codification provided by the fiscal authorities

You can use the **Tax application** option to add the fiscal codification that's provided by the fiscal authorities.

1.  For each **Taxpayer type** that requires fiscal codification:
1.  Select the record, then go to **Tax application** in the top menu.
1. Create a new record.
1. In the **Tax application Id** field, select a value.
1. In the **Tax application code** field, enter the code that the fiscal authority uses to identify the taxpayer type.
1. Select **Save**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
