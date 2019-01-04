---
title: Microsoft Dynamics 365 Project Timesheet mobile application
---

Overview
========

The Microsoft Dynamics 365 Project Timesheet mobile app enables users to submit
and approve timesheet for projects on their mobile device (iPhone or Android),
anywhere and anytime. This mobile app surfaces the timesheet functionality that
resides in the Project management and accounting area of Microsoft Dynamics 365
for Finance and Operations, improving user productivity and efficiency, as well
as enabling timely entry and approval of project timesheets.

Download and install the mobile application
===========================================

Download and install the Microsoft Dynamics 365 Project Timesheet mobile app for
Android or iPhone from the mobile store.

Enable the Microsoft Dynamics 365 Project Timesheet mobile application
======================================================================

In Microsoft Dynamics 365 for Finance and Operations, the project timesheet
mobile application must be enabled. To enable the functionality, go to Project
management and accounting parameters\>Timesheet and mark the “Enable Microsoft
Dynamics 365 Project Timesheet” parameter.

Sign into the mobile application
================================

1.  Start the app on your mobile device.

2.  Enter your Microsoft Dynamics 365 for Finance and Operations URL.

3.  The first time that you sign in, you're prompted for your user name and
    password. Enter your credentials.

4.  You will be signed into your default company.

Submitting a project timesheet
==============================

You can create and submit a project timesheet. You can base a new timesheet on
information from a previous timesheet, saved lines, or project assignments. If
you are designated as a delegate, you can also enter a timesheet for another
worker. To create a timesheet as a delegate, select the Resource name in the
side drawer.

The timesheet form will create a new timesheet for the timesheet period, based
on the current date. The work week will be displayed. If the timesheet period
covers multiple weeks, you can select another work week from the workweek tabs.
If a timesheet exists for the current date, it will be displayed. If you need to
create a new timesheet in a different timesheet period, the side drawer action
**New timesheet** can be used.

You can enter project information by clicking either on the **Add time** action
or the **Copy time from** action. The Copy time from actions will copy project
line information, but not the hours. The Copy time from menu includes the
following options:

>   Copy from existing timesheet – Copy timesheet lines from an existing
>   timesheet.

>   Copy from favorite – Create new timesheet lines by using the timesheet
>   settings that you selected as favorites.

>   Copy from assignment – Create new timesheet lines from assigned projects.

The project information that is displayed is dependent on the mobile parameters
that you have defined in the Project management and accounting parameters form.

In the **Legal entity** field, select the legal entity for which you performed
project work. The Legal entity field is available only if intercompany timesheet
support has been enabled for your legal entity.

Select the **Customer** who is associated with the project for the timesheet.
You can select the project first. If you do, the **Customer** field is filled in
automatically.

In the **Project** field, select the project that you are entering time for. The
Customer field is filled in automatically.

The Customer and Project lookups enable searching across both customers and
projects.

Select information in the **Category**, **Activity**, **Line property**, **Sales
tax group** and **Item sales tax group** fields as required. These fields they
can be overridden.

The **Line property** will be set to a default value, based on Project
management and accounting parameters. When the Project/category and
Category/resource parameters are enabled, the Line property value will be set to
the default value you have defined for this validation. When the
Project/category and Category/resource parameters are not enabled, the Line
property value will be defaulted according to the “Enable default line property”
field on the Project management and accounting parameters page. The Line
property value can be overridden.

Select a day to add time. Enter the number of hours that you worked each day.

To add comments about the hours you are entering, click **Add comments**, and
then enter comments for an internal audience, customer audience, or both.
Internal comments can be viewed by project managers. Customer comments are
included on invoices.

To save the line as a favorite, select the check box, and then click **Save as
favorite**.

Financial dimension and attachment support are not provided in the mobile
application.

Continue adding project lines, as needed, to complete your timesheet.

Click **Submit** to send the timesheet to the approval workflow.

Timesheets to review

A listing of the timesheets that need to be reviewed is available in the side
drawer. This option is only available if the worker has been designated as a
workflow approver. Both header and line approval are supported. Line level
approval offers the ability to mark one or more lines for approval. After
reviewing the timesheet information, click **Approve**, **Delegate** or
**Return** to continue the workflow.
