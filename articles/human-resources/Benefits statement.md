---
title: Benefits statement overview
---

The benefits statement provides a statement of the benefits that an employee is
currently enrolled in. The report can be accessed by an employee directly or by
the benefit administrator. The benefit statement provides a list of the
employee’s enrolled benefits, coverage options, costs and any enrolled
dependents or beneficiaries. The statement can be printed for a single worker or
multiple workers.

**!Important!**

The **Benefits statement** feature is dependent upon the **Benefits management
feature** switch being enabled in Feature management. Once the Benefits
management feature is on, the benefits statement feature can be enabled. The
Benefits Statement feature can be turned off in feature management, once it’s
turned on.

Importing the benefits statement 
=================================

You must import the **Benefits Statement** via report configuration before the
Benefits Statement will be accessible in the product.

1.  Navigate to **System Administration** workspace

2.  Select the **Electronic Reporting** Tile

3.  Navigate to ‘**Configuration providers’** and select **‘Repositories’**

    ![Graphical user interface, text, application, chat or text message Description automatically generated](media/d5b6d805ff2ca95463372b4bb0a80428.png)

4.  Select **‘HR Resources’** from the list and **‘Open’** from the menu bar

    ![Graphical user interface, text, application, email Description automatically generated](media/acb9a7eea66a53518a9ed50a8ee0f3bb.png)

5.  Select the **Benefits Statement Model** in the left pane and expand it, so
    that ‘**Benefit statement format’** displays below

6.  Select **benefits statement format** on the left pane.

7.  On the right side of the screen, there will be a ‘**Versions**’ fast tab.
    Select ‘**Import’**

    ![](media/aa2461fd5964d7c60d1d5685fbf37513.png)

Generate the Benefits Statement as a PDF File
=============================================

By default the **Benefits statement** will print in a **Microsoft Word**
document format. To print to a **PDF** format, you will need to configure the
PDF option in **Electronic reporting destination** (System admin
workspaceElectronic reporting tileRelated LinksElectronic reporting destination)

1.  Select ‘New’

2.  Reference =‘Benefits Statement Format’

3.  Navigate to **File Destination** fast tab

4.  Select **‘New’**

5.  Name=Benefits Statement PDF

6.  File Component Name = **Benefits Statement**

7.  Select ‘**Convert to PDF**’ checkbox

8.  Select **‘Settings’** from the menu item in the **File destination** fast
    tab

    ![Graphical user interface, text, application Description automatically generated](media/9e49444973ba97e3ab9fdd4cfd85bff4.png)

9.  Select the **‘File’** fast tab and select **‘Enabled’**

![](media/ab5427c273c3859fdefc82f78580ab47.png)

1.  Select ‘**OK’**

**!Important!** – The benefits management feature is in a Preview state. There
is a known issue when attempting to use the email destination setting in the
Electronic Reporting destination report. The user will receive an error message
and the email will fail to send.

The benefits statement can be accessed in the following areas:

-   Benefits management workspacelinksreportsBenefits Statement

-   Employees (legacy form)Personal information tabBenefits Statement

-   Streamlined employee entryBenefitsReportsBenefits statement

-   Employee self service- Benefits-View benefits statement

Important!: Access to the benefits statement in employee self-service is
controlled by the privilege ‘View Benefit statement’. This is under the Employee
Self-service Benefits duty. This privileged is granted to employees by default.

Report contents:
================

The benefits statement will print the confirmed plan selections of the employee,
including any waived plans.

![Graphical user interface, text, application Description automatically generated](media/054ad7bddb4b7a61264183b72bef2436.png)

The report will print the Plan, Coverage option, Employee Cost, and employer
cost. The statement will also list any covered dependents. If the plan has
beneficiaries associated to it, the beneficiaries and their distribution
priority and percent will display.

The Benefits statement report can be printed for multiple employees at a time
via the ‘Records to include’ fast tab in the Benefits statement print form.
