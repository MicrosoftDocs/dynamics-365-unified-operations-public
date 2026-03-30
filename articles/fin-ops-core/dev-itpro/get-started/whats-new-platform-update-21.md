---
title: What's new or changed in Dynamics 365 for Finance and Operations platform update 21 (November 2018)
description: Learn about new or changed features in Dynamics 365 for Finance and Operation platform update 21. This version was released in November 2018.
author: johnmichalak
ms.author: johnmichalak
ms.topic: whats-new
ms.date: 10/31/2025
ms.update-cycle: 1095-days
ms.custom: 
  - bap-template
  - evergreen
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2017-09-30
ms.dyn365.ops.version: Platform 21 
ms.assetid: a765a61c-52a3-47c5-b579-68b9249c592b
---

# What's new or changed in Dynamics 365 for Finance and Operations platform update 21 (November 2018)

[!include [banner](../../../finance/includes/banner.md)]

This article describes features that are new or changed in Dynamics 365 for Finance and Operations platform update 21. This version was released in November 2018 and has a build number of 7.0.5073.

## Dynamics 365 October '18 release notes

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

[Check out the October '18 release notes](/dynamics365/release-plans/). We captured all the details, end to end, top to bottom, in a single document that you can use for planning.

## Bug fixes

For information about the bug fixes included in each of the updates that are part of Platform update 21, sign in to Lifecycle Services and view the [KB article](https://go.microsoft.com/fwlink/?linkid=2033925).

## Extensibility enhancements

The Release notes contain information about [the second wave of platform extensibility enhancements for the October 2018 release](/business-applications-release-notes/October18/dynamics365-finance-operations/platform-extensibility2), which come with Platform update 21. The document details 11 enhancements. One of the highlights is the new ability to put the next call inside a chain of command method within a try-finally block to facilitate standard exception handling.

## TransientSqlConnectionError X++ exception

During an X++ SQL query execution, a transient SQL connection error on the server side causes a TransientSqlConnectionError X++ exception. Depending on your application requirements, you should catch and handle the exception.

This exception usually occurs during a large transaction or when the database is under heavy processing pressure.

You can't catch the TransientSqlConnectionError exception within the transaction. The X++ transaction that encounters this exception is canceled (calling **ttsAbort**) before the exception occurs. This behavior means that you need to use the catch block to identify the transient SQL connection error instead of a generic X++ error exception, and then retry the outermost transaction or retry application code logic in a new session. This exception allows you to design your application for transient server failures.

If an application transaction takes a long time to process, you can use multiple incremental delays to catch the TransientSqlConnectionError exception. Retrying your application code in a new session is most likely to succeed after you catch the exception.

For more information, see [SQL connection error X++ exception](../dev-ref/sql-connection-error.md).

## Sticky default actions in grids

Many grids in Finance and Operations have a defined *default action*. This action is a single column in the grid where the value in every row always appears as a hyperlink, as opposed to other columns where only the value in the active row appears as a hyperlink. This default action always appears on the first textual column in a grid before any user personalization is applied. For example, consider the **Account** column in the **Customer** list following.

:::image type="content" source="../../fin-ops/get-started/media/customerGrid.png" alt-text="Screenshot of Customer list.":::

The **sticky default action** feature, which is available starting in Platform update 21, controls where the default action column appears in the grid after personalizations that change the order or visibility of columns are applied.

With sticky default actions off, which corresponds to how default actions work prior to Platform update 21, the default action hyperlink changes to whatever column is the first textual column after personalizations are applied. For example, if you move the **Account** column to be fourth column in the grid (or alternatively if you hide the **Account** column), the hyperlink representing the default action moves to the **Name** column.

:::image type="content" source="../../fin-ops/get-started/media/stickyDAOff.png" alt-text="Screenshot of Sticky default actions off.":::

With sticky default actions on, the default action hyperlink is on the same column regardless of any personalizations applied to the form. This behavior means that for this customer list, the **Account** column continues to be the default action column regardless of whether the **Account** column is moved or hidden.

:::image type="content" source="../../fin-ops/get-started/media/stickyDAOn.png" alt-text="Screenshot of Sticky default actions on.":::

With Platform update 21, the sticky default action feature is off, but a system administrator can turn it on for an environment. To turn on this feature, go to the **Client performance options** page under **System administration** and find the **Enable sticky default action** option.

## Batch active periods

With the release of Platform update 21, you get more control over when batch jobs run. Previously, you could only schedule a batch job to run every hour for a set number of hours or until a specific date. Now, administrators can add details for an extra active period, such as in the following scenarios:

- Set time ranges when jobs in a batch group can start running.
- Choose to run batch jobs only outside of office hours.
- Set the recurrence for any time within the active period. For example, your administrator might choose to run the batch jobs every hour, but only between 6:00 PM and 8:00 AM.

For more information, see [Batch active period](../sysadmin/activeperiod.md).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
