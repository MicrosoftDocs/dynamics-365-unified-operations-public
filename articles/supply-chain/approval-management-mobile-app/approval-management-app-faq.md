---
title: Approvals Management mobile app FAQ and known issues
description: This article answers frequently asked questions about the Approvals Management mobile app. It also describes known issues that affect the app and explains how to work around them.
author: kamaybac
ms.author: akshaykmr
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 07/29/2024
ms.custom: 
  - bap-template
---

# Approvals Management mobile app FAQ and known issues

[!include [banner](../../includes/banner.md)]

This article provides answers to several frequently asked questions (FAQ) about the Approvals Management mobile app. It also describes some known issues that affect the app and explains how to work around them.

## What platforms and mobile devices are supported?

The Approvals Management mobile app runs within the Power Apps mobile app. All platforms that the Power Apps mobile app supports can also run the Approvals Management mobile app. Learn more in [System requirements, limits, and configuration values for Power Apps](/power-apps/limits-and-config).

## Why isn't anything shown when I sign in to the mobile app?

If no features are visible in the Approvals Management mobile app, you probably lack the permissions that are required to access them. Access to each feature is controlled by security roles that are assigned to your user account in Dynamics 365 Supply Chain Management. Learn more in [Onboard the Approvals Management mobile app](developer/onboard-approval-app.md).

## What versions of Supply Chain Management support the mobile app?

The Approvals Management mobile app requires Supply Chain Management version 10.0.41 or later.

## Does the mobile app support Microsoft Intune deployment?

Yes, the Approvals Management mobile app supports deployment through Intune. Learn more in [Manage your mobile app with Microsoft Intune](/power-apps/mobile/intune).

## <a name="customize"></a>Can I customize and extend the mobile app?

No, you can't currently customize or extend the Approvals Management mobile app.

## Does the mobile app support offline mode?

No, the Approvals Management mobile app doesn't currently support offline mode.

## Is there multi-language support?

Yes, the Approvals Management mobile app is available in all the same languages as Supply Chain Management, except right-to-left (RTL) languages. We plan to add RTL support in a future release, after it's added to the canvas app platform.

## Where can I go to discuss the mobile app with the community and submit suggestions to Microsoft?

The [Dynamics 365 Procurement and Sourcing group on Viva Engage](https://www.yammer.com/dynamicsaxfeedbackprograms/#/threads/inGroup?type=in_group&feedId=69010219008&view=all) is a great place to go if you want to exchange tips, ask questions, or submit suggestions for improvement. Viva Engage group participants include Microsoft partners, customers, experts, and employees.

## I receive the following error: "Error when trying to retrieve data from the network." How can I diagnose the issue?

If you receive an error message that states, "Error when trying to retrieve data from the network," follow these steps to diagnose and fix the issue.

1. Run the Approvals Management mobile app in a browser as described in [Run an app in a web browser](/power-apps/user/run-app-browser).
1. If you receive the same error while you run the app in a browser, set up your browser to [capture an HTTP Archive file (HAR) file](/microsoft-edge/devtools-guide-chromium/network/reference#save-all-network-requests-to-a-har-file). Then reload the tab where the app is running.
1. Use a tool such as the [Google HAR analyzer](https://toolbox.googleapps.com/apps/har_analyzer/) to redact all secrets from the HAR file.
1. Contact Microsoft Support, and share the redacted HAR file with them.
1. Microsoft Support will help you diagnose and fix the issue.

The content of the HAR file might reveal an error that resembles the following example:

```text
SecLib::CheckPrivilege failed. User: <EntraObjectID>, PrivilegeName: prvReadRelationship, PrivilegeId: <PrivilegeID>, Required Depth: Basic, BusinessUnitId: <BusinessUnitID>, MetadataCache Privileges Count: <CacheCount>, User Privileges Count: <UserPrivilegeCount>
```

This error can occur because the *Approvals Management app* role doesn't have the privileges that are required to read the `Relationship` table. Instead, that privilege is provided by the *Finance and Operations Basic User* role in Dataverse. To fix this issue, add the *Finance and Operations Basic User* role to each user or team that uses the app.

## When I update the mobile app, I receive the following error: "Could not delete solution...because it has been modified." How can I fix the error?

The Approvals Management mobile app is a canvas app. The update process fails with an error if it detects that the canvas app has been customized. This behavior helps prevent the updater from overwriting your customizations. To fix the error, remove any customization layers by restoring the oldest version of the app. If the oldest version is more than six months old, you must manually delete the `msdyn_ApprovalsManagementAnchor` and `msdyn_ApprovalsManagement` solutions, and then reinstall the app from Dynamics 365 apps or AppSource.

Consider cloning the canvas app before you remove your customizations, just in case you want to copy the customizations to the updated app.

> [!NOTE]
> Microsoft doesn't support [customizing or extending](#customize) the Approvals Management mobile app.

## Are there any known issues that affect the release of the mobile app?

Yes, the Approvals Management mobile app has a few known issues that we expect to correct in an upcoming release. The following subsections describe these issues.

### Limited file type support for attachments

The current release provides only limited support for viewing file attachments on the job details page. We plan to add support for more file types in the final release.

**Supported attachment types:**

- URL (link)
- PNG/JPEG/JPG/BMP/GIF (image)
- PDF (document)

**Unsupported attachment types:**

- Note
- All other file types
