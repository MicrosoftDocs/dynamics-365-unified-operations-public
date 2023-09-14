---
title: Field list configuration for Latin America
description: This article provides information about configuring field lists for a Latin America. 
author: Fhernandez0088
ms.date: 09/05/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe
ms.custom: bap-template
---
# Field list configuration for Latin America
You can create up to 10 lists that contains elements with a code and description to be used in the LATAM section of transaction posting forms (invoice posting,  packing slip posting and any journal posting). Whrn creating a list you can select which one you are using among the 10 preestablished lists. These lists are used to comply with required information for transactions when that information consists of a list of options that the user must select. For each transaction up to one option of each list can be selected according to what is configured for the document class used in that transaction.

## Prerequisites
Before you complete the procedures in this article, enable the **LATAM Globalization** feature for the country that the legal entity you are working in is located.

## Set up a field list for Latin America
This procedure explains how to create a field list and customize its elements:
1. Go to **Organization administration** > **Setup** > **LATAM** > **Fields master List**.
2. Select **New** to create a new list. The lists are limited to ten that appear sequentially when created, and one must be selected.
3. In the **General** section complete the **Name** field with the description of the list.
4. In the **Reference code** section select **New** to create an element on the list.
5. Complete the **Reference code** field with the code provided by the fiscal authority.
6. Complete the **Description** field with an explanation of the element.

## Add the fiscal codification provided by the fiscal authorities
1. Go to **Organization administration > Setup > LATAM > Fields master List**.
2. Select an element from a list.
3. Select the **Tax application** button on the action pane.
4. Select **New** to add a line to the grid.
5. In the **Tax application Id.** field select a value from the list.
6. In the **Tax application code field** type the code with which the fiscal authority identifies the document class type.
7. Select **Save**.
