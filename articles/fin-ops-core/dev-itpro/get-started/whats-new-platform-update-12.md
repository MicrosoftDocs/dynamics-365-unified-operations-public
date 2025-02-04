---
title: What's new or changed in Dynamics 365 Finance and Operations, Enterprise edition platform update 12 (November 2017)
description: Learn about new or changed features in Dynamics 365 Finance and Operations, Enterprise edition platform update 12. This version was released in November 2017.
author: sericks007
ms.author: sericks
ms.topic: whats-new
ms.date: 07/12/2024
ms.custom: 
  - bap-template
  - evergreen
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2017-09-30
ms.dyn365.ops.version: Platform update 12 
ms.assetid: e577d51d-42d2-47c5-b388-93c8219c692a
ROBOTS: NOINDEX, NOFOLLOW
---

# What's new or changed in Dynamics 365 Finance and Operations, Enterprise edition platform update 12 (November 2017)

[!include [banner](../../../finance/includes/banner.md)]

This article describes features that are either new or changed in Dynamics 365 Finance and Operations, Enterprise edition platform update 12. This version was released in November 2017 and has a build number of 7.0.4709.

Go to the [Dynamics 365 Roadmap](https://roadmap.dynamics.com/) to find supplemental information about new features and learn more about what new features are in development. For information about the bug fixes included in Platform update 12, log in to Lifecycle Services (LCS) and view this [KB article](https://go.microsoft.com/fwlink/?linkid=863949).

## Browser client – Discover and learn currently available keyboard shortcuts

You no longer need to search through documentation to learn keyboard shortcuts. Instead, you can now discover currently available keyboard shortcuts directly from the user interface. Simply right-click on a control and select **View shortcuts**. This will open a dialog box listing the shortcuts that you can use based on where you are on the page. 

For more information, see [Keyboard shortcuts](../../fin-ops/get-started/shortcut-keys.md).

## Development and build environments in a customer LCS implementation project are monitored and managed by Microsoft

If you're a customer operating or implementing Finance and Operations, you are provided with a set of environments to enable development, testing, and production. Sandbox (Tier-2) and production environments are managed by Microsoft, while your IT staff is responsible for managing developer and build environments. With this feature, all environments in a Lifecycle Services (LCS) implementation project that are running in the Microsoft subscription, including developer and build environments, are monitored and managed by Microsoft. This relieves your IT staff from having to monitor and manage security, including applying security patches and updates for these environments. This does not affect development and build environments running on-premises or in the customer's or partner's own Microsoft Azure subscription.

Development and application management tasks performed by developers can be done without requiring local administrator rights on the development virtual machine (VM). Customers will not have access to the VM admin account of development and build environments running in the Microsoft subscription.

For more information, refer to this LCS blog article, [Restricted Admin Access](https://blogs.msdn.microsoft.com/lcs/2017/10/31/restricted-admin-access-with-platform-12-updates/).

## Enabling SQL triggers in 'bring your own database' (BYOD)

The 'bring your own database' feature, also called BYOD, enables incrementally exporting data entities from Dynamics 365 Finance and Operations into your own SQL Azure database. If your destination database contains SQL database triggers, at present, the BYOD process bypasses triggers to enable efficient bulk data transfer.

You can now use SQL database triggers in your own database, for data that is exported or BYOD. This allows for downstream processes to easily integrate with the BYOD processes.

## Export B2B users to Microsoft Entra ID

You can automatically export business-to-business (B2B) users to Microsoft Entra ID.

In the past, B2B users were exported manually to a .csv file. Then the Microsoft Entra tenant administrator had to use this file to manually add the users to Microsoft Entra using the Azure portal.

To enable the automatic export feature, a one-time setup and configuration process must be completed. When the process is completed, you can use the Provision new user workflow task to automatically export B2B users to Microsoft Entra ID.

The one-time set up and configuration means that you'll need to:

- Set up a B2B invitation service application in Microsoft Entra ID.
- Configure the B2B invitation service settings in finance and Operations.

For more information, see [Export business-to-business (B2B) users to Microsoft Entra ID](../sysadmin/implement-b2b.md).

## Personalizations can easily be shared with one or more roles in your organization

Personalization capabilities enable a user to make changes to the user interface, such as renaming labels, adding, moving or hiding controls, resizing, adding or re-ordering grid columns on forms across the application. Personalization also makes it possible for an end user to create new workspaces showing content from within the application as well as from Power BI. These features reduce the need to make customizations to the application and instead allow a user to potentially create the required user interface, either starting from scratch or by modifying ready-made content.

Administrators already have the ability to export a personalization done by a user and apply that to other users or roles within the organization through an import process. This will be simplified by allowing an administrator to share personalizations with others from the personalization administration form, without having to import the personalization.

Additionally, this feature gives the administrator more control over how to apply a personalization. Instead of replacing existing personalizations, an administrator can optionally choose to add the new personalizations to any existing ones.

## Reporting: Document Routing Agent scale improvements

The Document Routing Agent has been enhanced to offer support for more network printer devices. With the ability to support up to 50 network printers, clients are better prepared to handle common printing workloads. Simply upgrade the Document Routing Agent after deploying the latest platform update to take advantage of the intelligent document queue management.

> [!NOTE]
> Refer to the following installation instructions to deploy the latest version of the Document Routing Agent onto local print servers hosted on the corporate domain, [Install the Document Routing Agent to enable network printing](../analytics/install-document-routing-agent.md).

## Table extension – PreviewPartRef property

This release includes the ability to change the value of the **PreviewPartRef** property via a table extension. This feature provides an enhanced preview to existing fields, such as an enhanced preview for TMSRoute.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
