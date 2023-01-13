---
title: Sales point prefixes for Latin America 
description: This topic provides information about the sales point prefix configuration for Latin America. 
author: Fhernandez0088
ms.date: 01/13/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 
ms.custom: bap-template
---
# Sales point prefixes for Latin America
You can configure the sales point prefixes that some fiscal authorities require for the emission of legal documents, and that can be used to identify treasury documents and checkbooks.
## Prerequisites
Warehouses can be added to the sales point prefix configuration so they should be previously created.
## Set up a Sales point prefix for Latin America
1. Go to **Organization administration > Setup > LATAM > Sales Point Prefix**
2. Select **New** from the action pane.
3. In the **General** section complete the configuration of the following fields:

| Field              | Description                                                                                                             |
|--------------------|-------------------------------------------------------------------------------------------------------------------------|
| Sales point prefix | Enter the sales point code that identifies the record.                                                                  |
| Description        | Enter a description for the record.                                                                                    |
| Validate CA        | Activate this slider to make mandatory the usage of a CA number when using this sales point prefix in a transaction.    |
| Sales point type   | Define the sales point type for the record.                                                                             |
| Prefix             | Complete this field with the prefix that will appear in a document number when using this sales point in a transaction. |
| Report/Service Id. | Select the report/service configuration.                                                                                |

4. In the **Warehouse** section add the desired warehouses.
> [!NOTE]
> The warehouses added here will be the ones that the user can use when posting a packing slip with the sales point created.
You can use **Tax application** option to add this codification.

1.	Go to **Navigation pane > Organization administration > Setup > LATAM > Sales point Prefix**.
2.	Select the **Tax application** button on the action pane.
3.	Select **New** to add a line to the grid.
4.	In the **Tax application Id.** field select a value from the list.
5.	In the **Tax application code field** type the code with which the fiscal authority identifies the document class type.
6.	Select **Save**.
