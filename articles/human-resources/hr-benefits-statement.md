---
# required metadata

title: Benefits Statement
description: The benefits statement provides a statement of the benefits that an employee i is currrently enrolled in.
author: andreabichsel
ms.date: 09/21/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: HcmACACoverageGroup, BenefitWorkspace, HcmBenefitSummaryPart
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 3b953d5f-6325-4c9e-8b9b-6ab0458a73f8
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: AX 7.0.0, Human Resources

---

# Benefits statement

The benefits statement provides a statement of the benefits that an employee is
currently enrolled in. The report can be accessed by an employee directly or by
the benefit administrator. The benefit statement provides a list of the
employee’s enrolled benefits, coverage options, costs and any enrolled
dependents or beneficiaries. The statement can be printed for a single worker or
multiple workers.

> [!NOTE]
The **Benefits statement** feature is dependent upon the **Benefits management
feature** switch being enabled in Feature management. Once the Benefits
management feature is on, the benefits statement feature can be enabled. The
Benefits Statement feature can be turned off in feature management, once it’s
turned on.


## Importing the Benefits statement 


You must import the **Benefits statement** via report configuration before the
Benefits Statement will be accessible in the product.

1.  Navigate to **System Administration** workspace

2.  Select the **Electronic Reporting** Tile

3.  Navigate to ‘**Configuration providers’** and select **‘Repositories’**

  ![Repositories.](https://user-images.githubusercontent.com/26801678/134203290-7faf7245-ed08-44e9-95a1-a7ba278c42c6.png)

4.  Select **‘HR Resources’** from the list and **‘Open’** from the menu bar

    ![Configuration Repositories](https://user-images.githubusercontent.com/26801678/134203619-b3fd087d-1fe9-45ef-a588-1afedfe38dfd.png)

5.  Select the **Benefits Statement Model** in the left pane and expand it, so
    that ‘**Benefit statement format’** displays below

6.  Select **Benefits statement format** on the left pane.

7.  On the right side of the screen, there will be a ‘**Versions**’ fast tab.
    Select ‘**Import’**

    ![Versions](https://user-images.githubusercontent.com/26801678/134203763-f12ef549-e326-400d-ac69-b25fc94af47b.png)

## Generate the Benefits tatemsent as a PDF File

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

    ![File Destination](https://user-images.githubusercontent.com/26801678/134203881-a3f1ebc3-d816-485d-a53b-026cc29cae64.png)

9.  Select the **‘File’** fast tab and select **‘Enabled’**

![Enabled](https://user-images.githubusercontent.com/26801678/134203994-55d793dd-45fc-458c-a27a-2139b18aff1e.png)

10.  Select ‘**OK’**
  
  
> [!NOTE]
> The benefits management feature is in a Preview state. There
is a known issue when attempting to use the email destination setting in the
Electronic Reporting destination report. The user will receive an error message
and the email will fail to send.

The benefits statement can be accessed in the following areas:

-   Benefits management workspacelinksreportsBenefits Statement

-   Employees (legacy form)Personal information tabBenefits Statement

-   Streamlined employee entryBenefitsReportsBenefits statement

-   Employee self service- Benefits-View benefits statement



> [!NOTE]
>  Access to the benefits statement in employee self-service is
controlled by the privilege ‘View Benefit statement’. This is under the Employee
Self-service Benefits duty. This privileged is granted to employees by default.

## Report contents:


The benefits statement will print the confirmed plan selections of the employee,
including any waived plans.

![Report.](https://user-images.githubusercontent.com/26801678/134204058-61baa318-fede-4795-a256-acdf3217f9f9.png)

The report will print the Plan, Coverage option, Employee Cost, and employer
cost. The statement will also list any covered dependents. If the plan has
beneficiaries associated to it, the beneficiaries and their distribution
priority and percent will display.

The Benefits statement report can be printed for multiple employees at a time
via the**Records to include** fast tab in the **Benefits statement print form**.
