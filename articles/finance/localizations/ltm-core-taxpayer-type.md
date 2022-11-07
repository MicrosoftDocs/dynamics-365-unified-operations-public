---
title: Taxpayer types for Latin America 
description: This article provides information about the taxpayer type configuration for Latin America. 
author: Fhernandez0088
ms.date: 11/07/2022
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 
ms.custom: bap-template
---

# Taxpayer types for Latin America 

You can set up types of tax responsible entities with which the company operates. Entities can include customers, vendors, employees, and even the company itself.
 
## Prerequisites

The following prerequisites must be met before you can set up taxpayer types for organizations in Latin America:

- Tax ID types must be configured.
- Document class letters must be configured.

## Set up a taxpayer type for Latin America

1. Go to **Organization administration** > **Setup** > **LATAM** > **Taxpayer type**.
2. In the **General** section, in the **Taxpayer type** field, enter the register's code.
3. In the **Description** field, enter an explanation of the taxpayer type.  

   > [!NOTE]
   > These fields are required.

4. In the **Settings** section, complete the configuration according to the taxpayer type characteristics:

Enable the sliders as required:

| Slider                                  | Description                                                                                                                                                                                                                                  |
|-----------------------------------------|----------------------------------------------------------------------|
| Foreign taxpayer                        | Select this field if the registered entity is foreign. |
| Validate vendor AC                      | Select this field if the authorization code issued by the vendor must be validated. |
| Internal taxpayer                       | Select this field if the taxpayer is internal and doesn't represent a real entity. All transactions made by entities that are possessing this taxpayer type won't be informed in tax reports. |
| Mandatory country of residence          | Select **Yes** to make the **Country of residence** field required in the entity configuration. |
| Mandatory registered jurisdiction       | Select **Yes**, to make the **Registered jurisdiction** field required in the entity configuration. |
| Mandatory country identification number | Select **Yes**, to make the **Country identification number** field required in the entity configuration.  |
| Mandatory state identification number   | Select **Yes**, to make the **State identification number** field required in the entity configuration. |

5. In the **Document types** grid, add the **Tax Id types** associated to the taxpayer type according to the country legislation.

   > [!NOTE]
   > With this configuration and the tax ID type configuration in the country address book, you can filter or directly assign the tax ID type in the customer or vendor record.

6. In the **Document class letter** grid, select the IDs that the taxpayer type uses in transactions.
7. Select **Save**.

## Add the fiscal codification provided by the fiscal authorities

You can use **Tax application** option to add this codification.

1.	Go to **Organization administration** > **Setup** > **LATAM** > **Taxpayer type**.
2.	On the Action Pane, select **Tax application**.
3.	Select **New** to add a new line, and in the **Tax application Id** field, select a value from the list.
4.	In the **Tax application code** field, enter the code with wich the fiscal authority identifies the tax payer type.
5.	Select **Save**.


