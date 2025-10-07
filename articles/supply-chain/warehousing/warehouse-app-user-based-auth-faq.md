---
title: User-based authentication FAQ
description: Access answers to many of the most frequently asked questions about user-based authentication (device code flow) for the Warehouse Management mobile app.
author: Mirzaab
ms.author: mirzaab
ms.topic: faq
ms.date: 11/01/2023
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# User-based authentication FAQ

[!include [banner](../includes/banner.md)]

This article answers many frequently asked questions about user-based authentication (such as device code flow) for the Warehouse Management mobile app.

## When do I have to switch to user-based authentication?

Support for service-based authentication (client secret and certificate) was removed from the Warehouse Management mobile app on July 15, 2024. You must now use user-based authentication (such as device code flow) to connect the Warehouse Management mobile app to Microsoft Dynamics 365 Supply Chain Management. Learn more [Removed or deprecated features in Dynamics 365 Supply Chain Management](../get-started/removed-deprecated-features-scm-updates.md).

## Where can I learn more about user-based authentication?

For more information about user-based authentication and the deprecation of service-based authentication methods, read the following articles:

- [User-based authentication for the Warehouse Management mobile app](warehouse-app-authenticate-user-based.md)
- [Mass deploy the mobile app with user-based authentication](warehouse-app-intune-user-based.md)
- [Install the Warehouse Management mobile app](install-configure-warehouse-management-app.md)
- [Removed or deprecated features in Dynamics 365 Supply Chain Management](../get-started/removed-deprecated-features-scm-updates.md)

## Why is Microsoft deprecating service-based authentication for the Warehouse Management mobile app?

User-based authentication offers the following advantages over service-based authentication for the Warehouse Management mobile app:

- User-based authentication is easier to configure and use.
- User-based authentication is more secure in contexts where the Warehouse Management mobile app is used.
- User-based authentication provides more robust security and more configuration options in Microsoft Entra ID.
- User-based authentication establishes a foundation for adding support for single sign-on (SSO) authentication across devices and apps in a future release.

## Is service-based authentication deprecated everywhere?

No. Service-based authentication is deprecated only for the Warehouse Management mobile app. Other applications continue to support it.

## In which version of the mobile app is service-based authentication removed?

Starting with version 3.0, the Warehouse Management mobile app no longer supports service-based authentication. Therefore, existing certificates and client secrets no longer work.

Older versions of the mobile app continue to work and support service-based authentication, even after the release of version 3.0. However, we strongly recommend that you switch to user-based authentication as soon as possible. Devices that are set to automatically update apps from app stores (such as Microsoft Store, Google Play, or Apple App Store) automatically get the latest version of the mobile app. Therefore, service-based authentication stops working on these devices soon after version 3.0.

## What if I forget that service-based authentication is removed?

You won't forget. Soon before the scheduled release of Warehouse Management mobile app version 3.0, we plan to add prominent, nonblocking warnings that all app users receive. Microsoft Support might even contact you soon before the release of Warehouse Management mobile app version 3.0.

## How and when does the app show pop-up warnings about the authentication method?

Any time that a user changes or adds a connection that uses a certificate or client secret, the app shows a pop-up message to warn the user that the connection method is soon discontinued. Workers don't receive the message unless they edit the connections.

To prevent the pop-up warning from appearing, you must delete all connections that use a certificate or client secret.

## What is device code flow?

Device code flow provides a two-step process that authenticates users on devices or operating systems that don't necessarily provide a web browser. For example, a media streaming app might use device code flow to allow users to sign in on smart TVs, game consoles, and other devices. For devices and operating systems that don't provide a web browser, device code flow lets you sign in by using another device (such as a computer or mobile phone).

Device code flow is a user-based authentication method that lets you enter a Microsoft Entra ID user name and password to sign in from a device. After the app is signed in, individual workers still sign in by entering their Supply Chain Management worker ID.

Learn more in [User-based authentication for the Warehouse Management mobile app](warehouse-app-authenticate-user-based.md).

## How many Microsoft Entra ID apps do I need to register in Azure?

The Warehouse Management mobile app uses a Microsoft Entra ID application to authenticate and connect to your Supply Chain Management environment. You can use a global application that's provided and maintained by Microsoft, or you can register your own application in Microsoft Entra ID.

We recommend that you use the global application, because it's easier to set up, use, and maintain. In this case, you don't need to register any Microsoft Entra ID applications in Azure. All your devices can connect through the global application.

If you have specific requirements that the global application doesn't meet (such as the requirements for some on-premises environments), you can register your own application in Microsoft Entra ID as described in [Register an application in Microsoft Entra ID](warehouse-app-authenticate-user-based.md#create-service). You still need to create just one Microsoft Entra ID app registration. All your devices can then connect through it.

For information about how to configure your devices to connect through either of these methods, see [Install the Warehouse Management mobile app](install-configure-warehouse-management-app.md).

## How many Microsoft Entra ID users do I need?

You can choose any of the scenarios that are described in the following table. Your choice depends on your licensing strategy and risk tolerance.

| Scenario | Notes |
|---|---|
| Use the same Microsoft Entra ID for all devices | <p>*Not recommended.*</p><p>This scenario, where you use a single Microsoft Entra ID user for all your devices, is less secure than other scenarios. It can lead to confusion in Supply Chain Management. For example, all warehouse processes are associated with a single system user, even when multiple warehouse workers use multiple warehouse devices to process work.</p> |
| Use a unique Microsoft Entra ID for each device | <p>Each worker must manually sign in to the app when they start to use the device.</p><p>When you set up one Microsoft Entra ID user for each device, it's easy to block the Microsoft Entra ID user for just one device if that device is stolen or damaged. (Learn more in [Remove access for a device that uses user-based authentication](warehouse-app-authenticate-user-based.md#revoke).) |
| Use a unique Microsoft Entra ID for each worker | [Single sign-on (SSO)](warehouse-app-authenticate-user-based.md#sso) is supported. Therefore, a worker who signs in to a device is automatically signed in to the Warehouse Management mobile app and all other apps that use the same Microsoft Entra ID. |

Learn more in [Scenarios for managing devices, Microsoft Entra ID users, and mobile device users](warehouse-app-authenticate-user-based.md#scenarios).

## Do I need to map users on the Microsoft Entra ID applications page in Supply Chain Management when I use user-based authentication?

No, you don't need to map users on the **Microsoft Entra ID applications** page in Supply Chain Management when you use user-based authentication. That approach is required only when you use [service-based authentication](warehouse-app-authenticate-service-based.md#user-azure-ad).

## How often does the Warehouse Management mobile app need to be signed in?

The session time-out period depends on your Microsoft Entra ID policies. By default, the session lasts for 90 days after each sign in. Therefore, at least 91 days pass between sign-ins.

## Can I set the session timeout period to more than 90 days?

No. The maximum session timeout period is 90 days.

## Will the current worker sign-in page change or be removed?

Although the worker sign-in page is required in some authentication scenarios, it can be skipped in others (for example, when a [default user ID](mobile-device-work-users.md#set-wma-users) is set for the warehouse worker account). For more information, see [Scenarios for managing devices, Microsoft Entra ID users, and mobile device users](warehouse-app-authenticate-user-based.md#scenarios).

## How can I sign out a device?

Follow these steps to sign out the Microsoft Entra ID account that's signed in on a device:

1. Open the Warehouse Management mobile app.
1. Select **Select a connection**.
1. Select **Sign out**.

## Can I just use the Microsoft Entra ID as a worker and skip the worker sign-in page?

Yes. You can map Microsoft Entra ID users to worker IDs in Supply Chain Management. Workers can then authenticate the app with Supply Chain Management and sign in as a worker at the same time. For more information, see [Scenarios for managing devices, Microsoft Entra ID users, and mobile device users](warehouse-app-authenticate-user-based.md#scenarios).

## Can I mass deploy the mobile app with user-based authentication?

Yes. For details and instructions, see [Mass deploy the mobile app with user-based authentication](warehouse-app-intune-user-based.md).

## What about single sign-on? Will I be able to use the mobile app alongside Microsoft Teams to chat with my coworkers?

Yes, [single sign-on (SSO)](warehouse-app-authenticate-user-based.md#sso) is supported. Among other capabilities, SSO lets you chat with coworkers through Microsoft Teams while you use the same account to sign in to the Warehouse Management mobile app.

If you're using SSO and sign out from one SSO app (such as Microsoft Teams), you also sign out of all other apps that use that same account (including the Warehouse Management mobile app).

## Will user-based authentication work with Dynamics 365 Finance + Operations (on-premises)?

The Warehouse Management mobile app continues to work with Dynamics 365 Finance + Operations (on-premises), even after service-based authentication is removed. On-premises installations use Active Directory Federation Service (AD&nbsp;FS) instead of Microsoft Entra ID. However, the settings are similar, including the settings for user-based authentication methods such as device code flow. Learn more in [Configure the Warehousing app for on-premises deployments](../../fin-ops-core/dev-itpro/deployment/warehousing-for-on-premise-deployments.md).

## Can I authenticate using Microsoft Entra Conditional Access?

No. The Warehouse Management mobile app doesn't support Microsoft Entra Conditional Access.

## Can I authenticate using Microsoft Entra Guest User Access?

Yes. You can add an external user as a guest in the Microsoft Entra admin center. Learn how in [Quickstart: Add a guest user and send an invitation](https://learn.microsoft.com/en-us/entra/external-id/b2b-quickstart-add-guest-users-portal).

After sending the invitation, create a [warehouse worker account](warehouse-app-authenticate-user-based.md) in Supply Chain Management and link it to the Microsoft Entra ID guest user account. If the guest user will use the Warehouse Management mobile app, you must assign appropriate roles and permissions to the warehouse worker account.
