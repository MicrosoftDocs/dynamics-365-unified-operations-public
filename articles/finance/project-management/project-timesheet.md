---
# required metadata

title: Project timesheet mobile application 
description: This topic provides information about the Microsoft Dynamics 365 Project Timesheet mobile application. The Project Timesheet mobile app enables users to submit and approve timesheets for projects on their mobile device.
author: abruer
manager: AnnBe
ms.date: 04/08/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Service industries
ms.author: josaw
ms.dyn365.ops.version: 10.0
ms.search.validFrom: 2019-01-15

---

# Project timesheet mobile application

[!include [banner](../includes/banner.md)]

## Overview

The Microsoft Dynamics 365 Project Timesheet mobile app enables users to submit
and approve timesheets for projects on their mobile device (iPhone or Android). This mobile app surfaces the timesheet functionality that
resides in the Project management and accounting area of Dynamics 365
Finance, improving user productivity and efficiency, as well
as enabling timely entry and approval of project timesheets.

## Download and install the mobile app

Download and install the Microsoft Dynamics 365 Project Timesheet mobile app for
Android or iPhone from the mobile store for your device.

## Enable the app 

In Finance, the Project Timesheet
mobile app must be enabled. To enable the functionality, go to **Project
management and accounting parameters \> Timesheet** and select the **Enable Microsoft
Dynamics 365 Project Timesheet** parameter.

## Sign in to the app

1.  Start the app on your mobile device.

2.  Enter your Finance URL.

3.  The first time that you sign in, you're prompted for your user name and
    password. Enter your credentials.

4.  You will be signed into your default company.

## Submit a project timesheet

You can create and submit a project timesheet in the app. You can base a new timesheet on
information from a previous timesheet, saved lines, or project assignments. If
you are designated as a delegate, you can also enter a timesheet for another
worker. To create a timesheet as a delegate, select the **Menu** button and then select a resource name..

The timesheet page will create a new timesheet for the timesheet period, based
on the current date. The work week will be displayed. If the timesheet period
covers multiple weeks, you can select another work week from the work week tabs.
If a timesheet exists for the current date, it will be displayed. If you need to
create a new timesheet in a different timesheet period, select the **Menu** button and then select
**New timesheet**.

You can enter project information by clicking the **Add time** action
or the **Copy time from** action. The **Copy time from** action will copy project
line information, but not the hours. The **Copy time from** menu includes the
following options:

- **Copy from existing timesheet** - Copy timesheet lines from an existing timesheet.

- **Copy from favorite** - Create new timesheet lines by using the timesheet settings that you selected as favorites.

- **Copy from assignment** - Create new timesheet lines from assigned projects.

The project information that is displayed is dependent on the mobile parameters
that you defined on the **Project management and accounting parameters** page.

In the **Legal entity** field, select the legal entity for which you performed
project work. The **Legal entity** field is available only if intercompany timesheet
support has been enabled for your legal entity.

Select the customer who is associated with the project for the timesheet. For the initial release on the Android, entry by customer is not supported, as you must select the project first. If you selected the project first, the **Customer** field is filled in automatically.

In the **Project** field, select the project that you are entering time for. The **Customer** field is filled in automatically.

The customer and project lookups enable searching across both customers and projects.

Select information in the **Category**, **Activity**, **Line property**, **Sales tax group**, and **Item sales tax group** fields as required. These fields can be overridden.

The **Line property** field will be set to a default value, based on project
management and accounting parameters. When the project/category and
category/resource parameters are enabled, the **Line property** value will be set to
the default value you have defined for this validation. When the
project/category and category/resource parameters are not enabled, the **Line
property** value will default according to the **Enable default line property**
field on the **Project management and accounting parameters** page. The **Line
property** value can be overridden.

Select a day to add time. Enter the number of hours that you worked each day.

To add comments about the hours you are entering, click **Add comments**, and
then enter comments for an internal audience, customer audience, or both.
Internal comments can be viewed by project managers. Customer comments are
included on invoices.

To save the line as a favorite, select the check box, and then click **Save as
favorite**.

Financial dimension and attachment support are not provided in the mobile
application.

Continue adding project lines as needed to complete your timesheet.

Click **Submit** to send the timesheet to the approval workflow.

## Review timesheets

A list of the timesheets that need to be reviewed is available in the menu. This option is only available if you have been designated as a workflow approver. Both header and line approval are supported. Line level
approval offers the ability to mark one or more lines for approval. After
reviewing the timesheet information, click **Approve**, **Delegate**, or
**Return** to continue the workflow.
