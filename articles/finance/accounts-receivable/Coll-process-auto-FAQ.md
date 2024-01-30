---
# required metadata

title: Collections coordinator summary
description: This article describes how the Collections coordinator summary feature shows AI-generated text in the Collections coordinator workspace.
author: JodiChristiansen
ms.date: 08/02/2023
ms.topic: conceptual
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jchrist
ms.search.validFrom: 2023-06-05
ms.dyn365.ops.version: 10.0.24
ms.collection: bap-ai-copilot   

---
# Collections process automation FAQ

## Example 1: Interest by range = Amount
You set up an interest code that assesses interest one time for every three months that the invoice payment exceeds the transaction due date. You want to base the calculation on a percentage interest value, according to stepped amount intervals. The interest value will be 1 percent for invoice amounts up to 1,000.00, 2 percent for amounts from 1,001.00 to 5,000.00, and 3 percent for amounts larger than 5,000.00. You set up the interest code field values as follows.

| **Field name**                  | **Field value** |
|---------------------------------|-----------------|
| **Interest code**               | 3M%ByAmt        |
| **Calculate interest every**    | 3/Month         |
| **Interest by range**           | Amount          |
| **Calculate interest based on** | Percentage      |

You set up the range information as follows.

| **From value** | **Interest value** |
|----------------|--------------------|
| 0              | 1                  |
| 1,001          | 2                  |
| 5,001          | 3                  |
