---
title: Available physical calculation for Negative inventory items
description: Available physical calculation for Negative inventory items
author: perlynne
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: InventOnhandItem
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: perlynne
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---
<!-- KFM: The title should describe an issue -->
# Available physical calculation for negative inventory items

KB Number: 4614020

## Issue description
<!-- KFM: What is the issue? What is the actual vs. the expected behavior? -->
If you enable negative physical inventory on the item level and have reservations, the **Available physical on exact dimensions** quantity will display this quantity per displayed dimension and **Available physical** will be calculated based on the reserved quantity on the highest dimension level (current legal entity). This happens only when the total quantity per legal entity is negative. If total quantity is positive, the availability calculation is done at warehouse level, not at the highest level.

See also [KB number: 4571314](https://fix.lcs.dynamics.com/Issue/Details?bugId=374704&dbType=3&qc=86d62a3c2da9d3023f8df5d0847c0423ff7b65c22f79d2e48fe3de4f5f1c198b)

## Resolution
<!-- KFM: This resolution promises documentation that doesn't exist. Please revise or remove this topic. -->

A documentation work item will get created to explain the design for the calculation of the **Available physical** quantity where the availability will be calculated according to the reservation hierarchy with the availability being the lowest availability in the path up to the highest level.
