---
# required metadata

title: Fiscal calendars, fiscal years, and periods
description: This article discusses fiscal calendars, fiscal years and periods and how to utilize them for legal entities, fixed assets and budgeting.
author: aprilolson
ms.date: 02/23/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: FiscalCalendars
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.assetid: a968a5e5-585e-4389-aa4e-c885a7e23413
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Fiscal calendars, fiscal years, and periods

[!include [banner](../includes/banner.md)]

This article discusses fiscal calendars, fiscal years and periods and how to utilize them for legal entities, fixed assets and budgeting.

Fiscal calendars provide a framework for the financial activity of an organization. Each fiscal calendar contains one or more fiscal years, and each fiscal year contains multiple periods. Fiscal calendars can be based on a January 1 to December 31 calendar year, or on any dates that you select. For example, some organizations select a fiscal calendar that starts on July 1 of one year and ends on June 30 of the following year. 

There is no limit to the number of fiscal calendars that you can create, and no limit to the number of fiscal years that can be created for a fiscal calendar. Each fiscal calendar is independent of your organization, and can be used by multiple legal entities in the organization. For example, an organization has eight departments and each department is a separate legal entity. Five of them share the same fiscal calendar and three use different fiscal calendars. You can create one fiscal calendar for the five legal entities that share the same fiscal calendar, and then create separate fiscal calendars for the other legal entities.

## Create fiscal calendars, fiscal years, and periods
You can create and delete fiscal calendars, fiscal years, and periods on the **Fiscal calendars** page. You can also divide existing periods and create closing periods that can be used to close a fiscal year. 

A closing period is used to separate general ledger transactions that are generated when a fiscal year is closed. When the closing transactions are in one fiscal period, it is easier to create financial statements that either include or exclude different types of closing entries. If a fiscal year is divided into 12 fiscal periods, the closing period is usually the 13th period. However, a closing period can be created from any period that has a status of Open. 

When you create a closing period, select a period that has a status of **Open** and that has the dates that you want to use. The new closing period will copy the starting and ending dates from the existing period. The original period will continue to exist. For example, you select Period 12, which is the last period in the fiscal year, and that has dates of August 1 through August 31. You enter a name for the closing period, such as **Close**. After you create the new closing period, you now have the original period and the closing period. Both have dates that start on August 1 and end on August 31.

## Select fiscal calendars for ledgers, fixed assets, and budget cycles
Fiscal calendars are used with fixed asset depreciation, financial transactions, and budget cycles. When you create a fiscal calendar, you can use it for multiple purposes. You can select a fiscal calendar for a fixed asset book to make it a fixed asset calendar. You can select a fiscal calendar for a ledger to make it a ledger calendar. And you can select a fiscal calendar for a budget cycle to make it a budget calendar. You can use the same fiscal calendar for all of these.

### Select a fiscal calendar for your legal entity

Select the fiscal calendar that you want to use for the ledger for your legal entity in the **Ledger** page. A fiscal calendar must be selected on the **Ledger** page for every legal entity. After a fiscal calendar is selected, you can set up period statuses and permissions on the **Ledger calendar** page for any of the periods that are part of a fiscal year.

### Select a fiscal calendar for fixed assets

You can select a fiscal calendar for a fixed asset book, and that fiscal calendar will be used by the fixed assets that use the selected book. You can select from any fiscal calendar that is defined on the **Fiscal calendars** page.

### Define budget cycle time spans

Budget cycles are the length of time during which a budget is used. Budget cycles can include part of a fiscal year or multiple fiscal years, such as a biennial budget cycle of two years or a triennial budget cycle of three years. The budget cycle time span defines the number of periods that are included in the budget cycle. To specify the budget cycle time span, use the **Budget cycle time spans** page.

## Maintain periods for your organization
You can use the **Ledger calendar** page to view the details of the fiscal calendar, fiscal years, and periods used by your organization. You can also change the status of the periods and select which users can post accounting transactions to periods. For example, at the start of a new period, you might want a group of users to finish posting financial transactions in the previous period, while other groups work only in the new period.







[!INCLUDE[footer-include](../../includes/footer-banner.md)]
