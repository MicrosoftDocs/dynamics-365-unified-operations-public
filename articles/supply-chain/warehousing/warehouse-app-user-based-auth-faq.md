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

## When do I have to switch to user-based authentication?

Support for service-based authentication (client secret and certificate) will be removed from the Warehouse Management mobile app on July 15, 2024. After that date, you'll have to use user-based authentication (such as device code flow) to connect the Warehouse Management mobile app to Microsoft Dynamics 365 Supply Chain Management. For more information, see [Removed or deprecated features in Dynamics 365 Supply Chain Management](../get-started/removed-deprecated-features-scm-updates.md).

## Where can I learn more about user-based authentication?

More information about user-based authentication and the deprecation of service-based authentication methods is available in the following articles:

- [User-based authentication](warehouse-app-authenticate-user-based.md)
- [Mass deploy the mobile app for user-based authentication](warehouse-app-intune-user-based.md)
- [Install the Warehouse Management mobile app](install-configure-warehouse-management-app.md)
- [Removed or deprecated features in Dynamics 365 Supply Chain Management](../get-started/removed-deprecated-features-scm-updates.md)

## Why is Microsoft deprecating service-based authentication for the Warehouse Management mobile app?

User-based authentication offers the following advantages over service-based authentication for the Warehouse Management mobile app:

- User-based authentication is easier to configure and use.
- User-based authentication is more secure in contexts where the Warehouse Management mobile app is used.
- User-based authentication provides more robust security and more configuration options in Microsoft Entra ID.
- User-based authentication establishes a foundation for adding support for single sign-on (SSO) authentication across devices and apps in a future release.

## Is service-based authentication being deprecated everywhere?

No. Service-based authentication is being deprecated only for the Warehouse Management mobile app. Other applications will continue to support it.

## Which version of the mobile app will service-based authentication be removed in?

As of version 3.0, the Warehouse Management mobile app will no longer support service-based authentication. Therefore, existing certificates and client secrets will no longer work.

Older versions of the mobile app will continue to work and will continue to support service-based authentication, even after version 3.0 is released. However, we strongly recommend that you switch to user-based authentication as soon as possible. Devices that are set to automatically update apps from app stores (such as Microsoft Store, Google Play, or Apple App Store) will automatically get the latest version of the mobile app. Therefore, service-based authentication will stop working on these devices soon after version 3.0 is released.

## What if I forget that service-based authentication is being removed?

You won't forget. Soon before the scheduled release of Warehouse Management mobile app version 3.0, we plan to add prominent, nonblocking warnings that all app users will receive. Microsoft Support might even contact you soon before the release of Warehouse Management mobile app version 3.0.

## How and when will the app show pop-up warnings about the authentication method?

Any time that a user changes or adds a connection that uses a certificate or client secret, the app will show a pop-up message to warn the user that the connection method will soon be discontinued. Workers won't receive the message unless they edit the connections.

To prevent the pop-up warning from appearing, you must delete all connections that use a certificate or client secret.

## What is device code flow?

Device code flow provides a two-step process that authenticates users on devices or operating systems that don't necessarily provide a web browser. For example, a media streaming app might use device code flow to allow users to sign in on smart TVs, game consoles, and other devices. For devices and operating systems that don't provide a web browser, device code flow lets you sign in by using another device (such as a computer or mobile phone).

Device code flow is a user-based authentication method that lets you enter a Microsoft Entra ID user name and password to sign in from a device. After the app is signed in, individual workers still sign in by entering their Supply Chain Management worker ID.

For more information, see [User-based authentication](warehouse-app-authenticate-user-based.md). 

## How many Microsoft Entra ID app registrations do I have to set up in Azure?

You only have to create one Microsoft Entra ID app registration. All your devices can then connect through it. For more information, see [User-based authentication](warehouse-app-authenticate-user-based.md).

## How many Microsoft Entra ID users do I need?

We recommend that you set up one Microsoft Entra ID user for each device. This approach makes it easy to block the Microsoft Entra ID user for just one device if that device is stolen or damaged. (For more information, see [Remove access for a device that authenticates by using the device code flow](warehouse-app-authenticate-user-based.md#revoke).) However, you can use a single Microsoft Entra ID user for all your devices if you prefer. Your choice depends on your licensing strategy and risk tolerance.

## Do I have to map users on the Microsoft Entra ID applications page in Supply Chain Management when I use user-based authentication?

No, you don't have to map users on the **Microsoft Entra ID applications** page in Supply Chain Management when you use user-based authentication. That approach is required only when you use [service-based authentication](warehouse-app-authenticate-service-based.md#user-azure-ad).

## How often will the Warehouse Management mobile app have to be signed in?

The session time-out period depends on your Microsoft Entra ID policies. By default, the session lasts for 90 days after each sign in. Therefore, at least 91 days will pass between sign-ins.

## Can I set the session time-out period to more than 90 days?

No. The maximum session time-out period is 90 days.

## Will the current worker sign-in page change or be removed?

No, the current worker sign-in page will remain in place.

## So, I first have to sign the app in by using a Microsoft Entra ID, and then I sign a worker in by using a worker ID?

Yes, but the device code (Microsoft Entra ID) sign-in is required only once every 90 days (by default). Workers will probably sign in and out every day.

## How can I sign out a device?

Follow these steps to sign out the Microsoft Entra ID account that's signed in on a device:

1. Open the Warehouse Management mobile app.
1. Select **Select a connection**.
1. Select **Sign out**.

## Can I just use the Microsoft Entra ID as a worker and skip the worker sign-in page?

You can't currently use this approach. However, we plan to add a feature to support it. In a future release, you'll be able to map Microsoft Entra ID users to worker IDs in Supply Chain Management. Workers will then be able to authenticate the app with Supply Chain Management and sign in as a worker at the same time.

## Can I mass deploy the mobile app for user-based authentication?

Microsoft doesn't currently support mass deployment of the Warehouse Management mobile app when you're using user-based authentication (such as device code flow) to sign in to Supply Chain Management. We expect to add support for this scenario some time in early 2024. For the latest news and more information, see [Mass deploy the mobile app for user-based authentication](warehouse-app-intune-user-based.md).

## Which mass deployment solutions will be supported?

Initially, we'll support Microsoft Intune for mass deployment. We're also investigating adding support for other mass deployment solutions. For the latest news and more information, see [Mass deploy the mobile app for user-based authentication](warehouse-app-intune-user-based.md).

## What about single sign-on? Will I be able to use the mobile app alongside Microsoft Teams to chat with my coworkers?

We're investigating adding support for single sign-on (SSO) in a future release. Among other capabilities, SSO will let you chat with coworkers over Microsoft Teams while you use the same account to sign in to the Warehouse Management mobile app.

If you're using SSO and sign out from one SSO app (such as Microsoft Teams), you'll also be signed out of all other apps that use that same account (including the Warehouse Management mobile app).

## Will user-based authentication work with Dynamics 365 Finance + Operations (on-premises)?

The Warehouse Management mobile app will continue to work with Dynamics 365 Finance + Operations (on-premises), even after service-based authentication is removed. On-premises installations use Active Directory Federation Service (AD&nbsp;FS) instead of Azure. However, the settings are similar, including the settings for user-based authentication methods such as device code flow. For more information, see [Configure the Warehousing app for on-premises deployments](../../fin-ops-core/dev-itpro/deployment/warehousing-for-on-premise-deployments.md).
