---
# required metadata

title: Platform updates for version 10.0.16 of Finance and Operations apps (February 2021)
description: This topic lists the features that are included in the platform updates for version 10.0.16 of Finance and Operations apps.
author: sericks007
ms.date: 11/30/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid:
ms.search.region: Global
# ms.search.industry: 
ms.author: sericks
ms.search.validFrom: 2020-10-31
ms.dyn365.ops.version: 10.0.16

---
# Platform updates for version 10.0.16 of Finance and Operations apps (February 2021)

[!include [banner](../includes/banner.md)]

This topic lists the features that are included in the platform updates for version 10.0.16 of Finance and Operations apps. This version has a build number of 7.0.5860 and is available on the following schedule:

- **Preview of release:** November 2020
- **General availability of release (self-update):** January 2021
- **General availability of release (auto-update):** February 2021

## Features included in this release

The following features are included in this release. Some of the listed features are still in preview, while others may already be generally available. See the [release plan](/dynamics365-release-plan/2020wave2/finance-operations/finance-operations-crossapp-capabilities/planned-features) for official release dates for each feature.

-  User session management<br>- Administrators have the ability to set a maximum session timeout for individual users.  The range of the session can be from 1 hour to 2160 hours.  When this session length expires, the user is required to sign in with their credentials. For more information, see [User session management](../sysadmin/user-session-management.md).

-  Renamed 'Session idle timeout' to 'Session inactivity timeout'<br>- To differentiate the types of session timeouts between maximum user session and inactivity user session, a change in the name was implemented. For more information, see [Set the session inactivity timeout](../sysadmin/session-idle-timeout.md).

-  Removing support for Visual Studio 2015<br>- Version 10.0.16 is the last version to support Visual Studio 2015. For more information, see [
Removing support for Visual Studio 2015](removed-deprecated-features-platform-updates.md#visual-studio-2015).

-  [Email throttling](/dynamics365-release-plan/2020wave2/finance-operations/finance-operations-crossapp-capabilities/email-throttling)<br>- This feature allows non-interactive email providers to adhere to a per-minute email sending limit, which prevents errors that are currently triggered when the system attempts to send more emails than the provider can handle. When email throttling is enabled, sending limits for Microsoft 365 email providers will be set automatically; manual configuration is required for all other email providers. For more information, see 
[Configure and send email](../../fin-ops/organization-administration/configure-email.md).

-  [Document (attachment) history](/dynamics365-release-plan/2020wave2/finance-operations/finance-operations-crossapp-capabilities/document-attachment-history)<br>- This document management feature creates a history mechanism for record attachments. This allows your organization to maintain an audit of actions related to individual attachments. For example, you can see when an attachment was created, marked for pending deletion, restored, deleted, or moved and who performed the action. The default history retention period is 180 days, however this is configurable on the **Document management parameters** page. For more information, see 
[Configure document management](../../fin-ops/organization-administration/configure-document-management.md).

-  [General availability of the Grouping with grids feature](/dynamics365-release-plan/2020wave2/finance-operations/finance-operations-crossapp-capabilities/grouping-subtotals-grids-general-availability)<br>- For more information, see 
[Grid capabilities](../../fin-ops/get-started/grid-capabilities.md#grouping-tabular-data).

-  [New HTML editor control](/dynamics365-release-plan/2020wave2/finance-operations/finance-operations-crossapp-capabilities/new-html-editor-control)<br>

-  Enhanced the Message::AddAction API<br>- The Message::AddAction API now surfaces the action in notifications when messages are routed to the Action center or Message details pane. For more information, see [Messaging APIs](../user-interface/messaging-api-center-bar-details.md#message).

- [Mitigate a SQL injection attack](../dev-ref/query-with-parameters.md)<br>- Use the new **Statement.executeQueryWithParameters** API to mitigate SQL injection attacks.

Most of these features must be enabled using [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md) before you can use them.

## Additional resources

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics Lifecycle Services (LCS), and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=528995&dbType=3&qc=267a545fabd24e111868bedc16716f5713a785ed096cdb6209526f41631e41db).

### Dynamics 365: 2020 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2020 release wave 2 plan](/dynamics365-release-plan/2020wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated platform features

The [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) topic describes features that have been removed, or that are planned for removal in platform updates of Finance and Operations apps.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

A deprecation notice will be added in the [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) topic 12 months before the removal of any feature from the product.

For breaking changes that affect only compilation time, but that are binary-compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these changes are functional updates that must be made to the compiler.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]