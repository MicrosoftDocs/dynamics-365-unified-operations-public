---
title: Asset Management mobile app FAQs and known issues
description: Access answers to several frequently asked questions (FAQs) about the Asset Management mobile app, including questions about supported platforms and devices.
author: jodahl
ms.author: jodahl
ms.topic: overview
ms.date: 09/19/2023
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Asset Management mobile app FAQs and known issues

[!include [banner](../../includes/banner.md)]

This article provides answers to several frequently asked questions (FAQs) about the Asset Management mobile app. It also describes a few known issues that affect the app and how to work around them.

## What platforms and mobile devices are supported?

The Asset Management mobile app runs within the Power Apps mobile app. All platforms supported by the Power Apps mobile app can also run the Asset Management mobile app. For details, see [System requirements, limits, and configuration values for Power Apps](/power-apps/limits-and-config).

## Why don't I see anything when I sign in to the app?

If you don't see any features in the app, you probably lack the permissions required to access them. Access to each feature is controlled by security roles assigned to your user account in Supply Chain Management. Learn more in [Configure users and workers in Supply Chain Management](onboard-app.md#roles-workers)

## What versions of Supply Chain Management support the app?

The Asset Management mobile app requires Supply Chain Management version 10.0.36 or newer.

## <a name="customize"></a>Can I customize and extend the app?

No, it isn't currently possible to customize or extend the app.

## Does the app support offline mode?

No, the Asset Management mobile app doesn't currently support offline mode.

## Is there multi-language support?

Yes, the Asset Management mobile app is available in all the same languages as Supply Chain Management, except for right-to-left (RTL) languages. We're awaiting RTL support from the canvas app platform and plan to add RTL support in a future release.

## Where can I go to discuss the app with the community and submit suggestions to Microsoft?

The [Asset Management Viva Engage (Yammer) group](https://www.yammer.com/dynamicsaxfeedbackprograms/#/threads/inGroup?type=in_group&feedId=17556554&view=all) is a great place to go if you want to exchange tips, ask questions, or submit suggestions for improvement. Yammer group participants include Microsoft partners, customers, experts, and employees.

## How can I diagnose "Error when trying to retrieve data from the network" issues?

If you see the error message "Error when trying to retrieve data from the network", follow these steps to diagnose and solve the issue:

1. Run the Asset Management app in a browser as described in [Run an app in a web browser](/power-apps/user/run-app-browser).
1. If you see the same error while running in a browser, set up your browser to [capture a HAR file](/microsoft-edge/devtools-guide-chromium/network/reference#save-all-network-requests-to-a-har-file) and then reload the tab where the app is running.
1. Use a tool such as the [Google HAR analyzer](https://toolbox.googleapps.com/apps/har_analyzer/) to redact all secrets from the HAR file.
1. Contact Microsoft Support and share the redacted HAR file with them.
1. Microsoft Support will help you diagnose and solve the issue.

The content of the HAR file might reveal an error similar to the following example:

```text
SecLib::CheckPrivilege failed. User: <EntraObjectID>, PrivilegeName: prvReadRelationship, PrivilegeId: <PrivilegeID>, Required Depth: Basic, BusinessUnitId: <BusinessUnitID>, MetadataCache Privileges Count: <CacheCount>, User Privileges Count: <UserPrivilegeCount>
```

This error can occur because the *Asset Management app* role doesn't have the privileges required to read the `Relationship` table. Instead, that privilege is provided by the *Finance and Operations Basic User* role in Dataverse. To resolve this issue, add the *Finance and Operations Basic User* role to each user or team that's using the app.

## When updating the app, how can I solve the error: "Could not delete solution ... because it has been modified"?

The update process fails with an error if it detects that the Asset Management mobile application canvas app has been customized. This helps prevent the updater from overwriting your customizations. To solve this issue, remove any customization layers by restoring the oldest version of the app. If the oldest version is over six months old, you'll need to manually delete the `msdyn_EnterpriseAssetManagementMobileV2` solution and then reinstall the app from *Dynamics 365 apps* or *AppSource*.

Consider cloning the canvas app before removing your customizations, just in case you want to copy the customizations to the updated app.

> [!NOTE]
> Microsoft doesn't support [customizing or extending](#customize) the Asset Management mobile app.

## Are there any known issues affecting the release of the Asset Management mobile app?

Yes, the Asset Management mobile app has a few known issues that we expect to correct in an upcoming release. The following subsections describe them.

### Limited file-type support for attachments

The current release provides only limited support for viewing file attachments on the job details page. We plan to add support for more file types in the final release.

Supported attachment types:

- URL (link)
- PNG/JPEG/JPG/BMP/GIF (image)
- PDF (document)

Unsupported attachment types:

- Note
- All other file types
