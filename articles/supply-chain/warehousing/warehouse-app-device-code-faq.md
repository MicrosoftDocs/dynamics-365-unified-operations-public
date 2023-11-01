---
title: User-based authentication FAQ
description: This article provides answers to many of the most frequently asked questions about user-based authentication (device code flow) for the Warehouse Management mobile app.
author: JTOne123
ms.author: pavlodatsiuk
ms.reviewer: kamaybac
ms.search.form:
ms.topic: faq
ms.date: 11/01/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---


# User-based authentication FAQ

[!include [banner](../includes/banner.md)]

This article provides answers to many of the most frequently asked questions about user-based authentication (such as device code flow) for the Warehouse Management mobile app.

## When do I need to switch to user-based authentication?

Support for service-based authentication (client secret and certificate) will be removed from the Warehouse Management mobile app on July 15, 2024. After that date, you'll need to use user-based authentication (such as device code flow) to connect the Warehouse Management mobile app to Supply Chain Management. For more information, see [Removed or deprecated features in Dynamics 365 Supply Chain Management](../get-started/removed-deprecated-features-scm-updates.md)

## Where can I learn more about user-based authentication?

More information about user-based authentication and the deprecation of service-based authentication methods is available in the following articles:

- [User-based authentication](warehouse-app-authenticate-user-based.md)
- [Mass deploy the mobile app for user-based authentication](warehouse-app-intune-user-based.md)
- [Install the Warehouse Management mobile app](install-configure-warehouse-management-app.md)

## Why is Microsoft deprecating service-based authentication for the Warehouse Management mobile app?

Service-based authentication is less secure than user-based authentication for contexts where the Warehouse Management mobile app is used. User-based authentication provides more robust security and more configuration options in Microsoft Entra ID.

## Is service-based authentication being deprecated everywhere?

No. Service-based authentication only being for the Warehouse Management mobile app. It will continue to be supported for other applications.

## In which version of the mobile app will service-based authentication be removed?

Starting with version 3.0, the Warehouse Management mobile app will no longer support service-based authentication, so existing certificates and client secrets will no longer work.

Older versions of the mobile app will continue to work and will continue support service-based authentication, even after version 3.0 is released. However, we strongly recommend that you switch to user-based authentication as soon as possible. If you use autoupdate from your app stores (such as Microsoft Store, Google Play, or Apple App Store), you'll automatically get the latest version of the mobile app, and service-based authentication will stop working when version 3.0 is released.

## What if I forget about it?

You won't forget about it. We plan to add prominent, nonblocking warnings in new releases of the mobile app. You might even be contacted by Microsoft Support soon before the release of Warehouse Management mobile app version 3.0.

## What is device code flow?

Device code flow is a user-based authentication method that lets you enter a Microsoft Entra ID user name and password to sign in from a device. Once the app is signed in, individual workers will still sign by entering their worker account from Supply Chain Management. For more information, see [User-based authentication](warehouse-app-authenticate-user-based.md).  <!-- KFM: Please double-check this one. -->

## How many Microsoft Entra ID app registrations do I need to set up in Azure?

You only need to create one Microsoft Entra ID app registration, which all of your devices can connect through. For more information, see [User-based authentication](warehouse-app-authenticate-user-based.md).

## How many Microsoft Entra ID users do I need

We recommend setting up one Microsoft Entra ID user for each device. This approach makes it easy to block the Microsoft Entra ID user for just one device if that device is stolen or damaged (see also [Remove access for a device that authenticates by using the device code flow](warehouse-app-authenticate-user-based.md#revoke)). However, you can use a single Microsoft Entra ID user for all of your devices if you prefer; your choice depends on your licensing strategy and risk tolerance.

## How often will the Warehouse Management mobile app need to be signed in?

The session time-out period depends on your Microsoft Entra ID policies. By default, the session lasts for 90 days after each sign in, so at least 91 days will pass between sign ins.

## Can I set the session time-out period to more than 90 days?

No. The maximum session time-out period is 90 days.

## Will the current worker sign-in screen change or be removed?

No, the current worker sign-in screen will remain in place.

## So, I need to first sign the app in using a Microsoft Entra ID and then sign a worker in using a worker ID?

Yes, but the device code (Microsoft Entra ID) sign-in is only required once every 90 days (by default). Workers will probably sign in and out every day.

## Can I just use the Microsoft Entra ID as a worker and skip the worker sign-in screen?

You can't do this now, but we're planning to add this feature. In a future release, you'll be able to map a Microsoft Entra ID user to a worker ID in Supply Chain Management. Then, workers will be able to authenticate the app with Supply Chain Management and sign in as a worker at the same time. <!-- KFM: Please double-check this one. -->

## Can I mass deploy the mobile app for user-based authentication?

Microsoft doesn't currently support mass deployment of the Warehouse Management mobile app when you're using user-based authentication (such as device code flow) to sign in to Supply Chain Management. We expect to add support for this scenario soon. For the latest news and more information, see [Mass deploy the mobile app for user-based authentication](warehouse-app-intune-user-based.md).

## Which mass deployment solutions will be supported?

We'll initially support Microsoft Intune for mass deployment. We're also investigating adding support for other mass deployment solutions, such as those from SOTI. For the latest news and more information, see [Mass deploy the mobile app for user-based authentication](warehouse-app-intune-user-based.md). <!-- KFM: This seems pretty speculative. I suggest removing the mention of SOTI-->

## What about single sign-on? Will I be able to use the mobile app alongside Microsoft Teams to chat with my coworkers?

We're investigating adding support for single sign-on (SSO) in a future release. Among other things, SSO will allow you to chat with coworkers over Microsoft Teams while you're using the Warehouse Management mobile app. <!-- KFM: This seems pretty speculative. I suggest removing this Q/A -->
