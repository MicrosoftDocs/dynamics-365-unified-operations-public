---
title: Platform updates for version 10.0.48 of finance and operations apps (April 2026)
description: This article lists the features and enhancements that are included in the platform updates for version 10.0.48 of finance and operations apps.
author: johnmichalak
ms.author: johnmichalak
ms.reviewer: johnmichalak
ms.date: 04/24/2026
ms.update-cycle: 1095-days
ms.topic: whats-new
ms.custom: 
  - bap-template
  - evergreen
ms.search.region: Global
---

# Platform updates for version 10.0.48 of finance and operations apps (January 2026)

[!include [banner](../includes/banner.md)]

This article lists the features in the platform updates for version 10.0.48 of finance and operations apps. This version uses build number nnnnnn and is available on the following schedule:

- **Preview of release:** April 2026
- **General availability of release (self-update):** June 2026
- **General availability of release (auto-update):** July 2026

## Features included in this release

This section lists the features included in this release when available. The article might be updated to add features that are added to the build after it's published.

| Module or feature area | Feature name | More information | Enabled by |
| --- | --- | --- | --- |
| Agent foundation | Deep links for Dynamics 365 ERP MCP | This feature enables responses generated from agent experiences to include direct navigation links to the corresponding records in the ERP application. When an MCP request retrieves or modifies record data, the MCP response includes a deep link URL that opens the application context used to generate that response. | Administrator |
| Agent foundation | Attachment support for Dynamics 365 ERP MCP | The feature enables the Dynamics 365 ERP MCP server to read, create, modify, and delete attachment records in the Dynamics 365 ERP applications. Learn more in [Enable agents to work with attachments through Dynamics 365 ERP MCP server](/dynamics365/release-plan/2026wave1/enterprise-resource-planning/finance-operations-crossapp-capabilities/enable-agents-work-file-attachments-through-dynamics-365-erp-mcp-server). | Administrator |



## Feature enhancements included in this release

This section has a table that lists enhancements included in this release when available. The article might be updated to include features added to the build after it's published.

| Module or feature area | Feature name | More information | Enabled by |
| --- | --- | --- | --- |
| Developer tools | Struct.remove | Fixed a bug in the implementation of the `remove` method on the struct class. This class is used to create name and value pairs in X++. Using the `remove` method didn't completely remove the element in the struct: It only cleared the key (the field name) but left the value in place. This bug is fixed. If you relied on the erroneous behavior, you need to revisit your code. | &nbsp; |
| Developer tools | X++ | The `client` and `server` keywords that you can apply to X++ methods are now flagged as warnings. Remove these keywords in existing code and don't use them in new code. These keywords were useful in Ax 2012 when developers could choose to run methods on the client or the server tier. Currently, all methods execute on the server tier and these keywords don't make sense and might be confusing to new users. | &nbsp; |
| Developer tools | X++ | Introduced a new option for the X++ compiler executable, xppc.exe. You can now apply the `-notodos` option which causes `todo` comments, where developers state a desire to finish something, to not make it into the output logs. | &nbsp; |
| Developer tools | X++ | The SysDict class that provides reflection over X++ classes is augmented with the ability to determine if a class is internal and whether a method is internal or protected internal. Similarly, the AccessSpecifier enum is updated accordingly. | &nbsp; |
| Agent foundation | Enhanced data tools for read operations | The data tools for read operations in the Dynamics 365 ERP MCP server moved from OData to SQL, enabling additional operators in data retrieval for agent scenarios. In this release, the `data_find_entities` tool in the MCP server is replaced with a new `data_find_entities_sql` tool. Learn more in [Data tools](../../dev-itpro/copilot/copilot-mcp.md#data-tools). | On by default |

### Bug fixes

To see bug fixes in this update, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=nnnnnn).

### Dynamics 365: 2026 release wave 1 plan

Want to know about upcoming and recently released capabilities in our business apps or platform?

Check out the [Dynamics 365: 2026 release wave 1 plan](/dynamics365/release-plan/2026wave1/). This document has all the details you need for planning.

### Removed and deprecated platform features

The [Removed or deprecated platform features](../../fin-ops/get-started/removed-deprecated-features-platform-updates.md) article describes features that are removed or planned for removal in platform updates for finance and operations apps.

- A *removed* feature isn't available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

Deprecation notices appear in the [Removed or deprecated platform features](../../fin-ops/get-started/removed-deprecated-features-platform-updates.md) article 12 months before any feature is removed.

For breaking changes that affect only compilation time but are binary-compatible with sandbox and production environments, the deprecation time is less than 12 months. These changes are functional updates that you must make to the compiler.
](https://successhub.crm.dynamics.com/main.aspx?appid=0fe9f79a-a1f6-4064-af95-ded6c5e7bd5c&pagetype=entityrecord&etn=rn_releasenote&id=ee25d2dc-5946-f011-877a-7c1e52585ca6)
