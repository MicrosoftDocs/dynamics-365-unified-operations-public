--- 
title: Evaluate all actions for Multi SKU location directives 
description: A new feature has been added to evaluate all actions for multiple SKU location directives. This page guides you to information on how to turn it on.
author: perlynne 
ms.date: 06/24/2021 
ms.topic: troubleshooting 
# ms.search.form:  
audience: Application User 
ms.reviewer: kamaybac 
ms.search.region: Global 
ms.author: perlynne 
ms.search.validFrom: 2021-06-24 
ms.dyn365.ops.version: 10.0.20 
--- 
 
# Multiple SKU option doesn't evaluate multiple location directive actions

## Symptoms

Location directives of the *Sales orders* work order type and the *Put* work type don't evaluate multiple location directive actions when the **Multiple SKU** option is selected. Only the first location directive action is evaluated.

## Resolution

A new feature, *Evaluate all actions for Multi SKU location directives*, has been added in version 10.0.15 (see [KB 4579866](https://fix.lcs.dynamics.com/Issue/Details?kb=4579866&bugId=475946&dbType=3&qc=1bc41a56de7a3ee419fa76397a6bf282fce5be9b93e427c08a6d916d1dfa3091)). This feature evaluates all actions for multi-SKU location directives. As of Supply Chain Management version 10.0.21, this feature is turned on by default.  As of Supply Chain Management 10.0.25, this feature is mandatory and can't be turned off. Administrators can use the [Feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) page to check the feature status and enable or disable it if needed.
