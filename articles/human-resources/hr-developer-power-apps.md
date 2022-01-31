---
# required metadata

title: Extend Talent with Power Apps and Power Automate
description: This article describes some examples of extensibility scenarios for Microsoft Dynamics 365 Human Resources that use Microsoft Power Apps and Microsoft Power Automate.
author: negudava
ms.date: 02/06/2020
ms.topic: article
ms.prod: 
ms.technology:
# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom:
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: negudava
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Extend with Power Apps and Power Automate


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]



This article describes some examples of extensibility scenarios for Microsoft Dynamics 365 Human Resources that use Microsoft Power Apps and Microsoft Power Automate. You can import the solution package that is associated with each example into your Power Apps environment. You can then use the packages either as guidance or as starting points to implement scenarios that are applicable to your organization.

> [!IMPORTANT]
> If you want to use the templates and apps that are described in this topic "as is," be sure to test them to make sure that they cover all the scenarios that are specific to your implementation.

## Prerequisites

- To import packages, users must have the **Environment Maker** permission.
- To export or import apps, users must have a Power Apps Plan 2 license or a Power Apps Plan 2 trial license.

## Integration with Microsoft 365, Power Automate

The **Integration with Microsoft 365** app can be used to extract team information for signed-in users from Microsoft 365. It references workers in Human Resources to extract employee identification types. Managers can check expiration dates of employee ID types. They can also send an email reminder if the employee ID type is expiring. Power Automate integrates with Power Apps to send this reminder. Confirmation will be sent back to Power Apps from Power Automate when the reminder is sent. Identification types include driver's license, passport, and other acceptable forms of ID.

You can extend this app for other scenarios. For example, you can use it to show team vacation information, calendar events, and any team-specific events.

To download the **Integration with Microsoft 365, Power Automate** app, go to [Integration with Microsoft 365](https://go.microsoft.com/fwlink/?linkid=2081787) on the Microsoft Download Center.

## Power Automate – SQL Connect and execute

The **Power Automate – SQL Connect and execute** template connects to Microsoft SQL Server and enables SQL queries to be run.

Although this template reads and updates SQL tables, you can extend it and use it for other scenarios. For example, you can use it to fill a staging table in Dataverse with records from SQL Server, and to periodically synchronize the staging table by using an incremental push from SQL Server.

Advanced Query is integrated with Flow to enable Data transformation and incremental push.

To download the **Power Automate – SQL Connect and execute** template, go to [Power Automate – SQL Connect and execute](https://go.microsoft.com/fwlink/?linkid=2081789) on the Microsoft Download Center.

## Additional resources

[The Microsoft Power Platform](/power-platform/admin/admin-documentation)</br>

[!INCLUDE[footer-include](../includes/footer-banner.md)]
