---
# required metadata

title: Benefit statement
description: The Benefit statement report explains the benefits that an employee is currently enrolled in.
author: twheeloc
ms.date: 07/02/2024
ms.topic: article
# optional metadata

# ms.search.form: HcmACACoverageGroup, BenefitWorkspace, HcmBenefitSummaryPart
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 3b953d5f-6325-4c9e-8b9b-6ab0458a73f8
ms.search.region: Global
# ms.search.industry: 
ms.author: anisagrawal
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: AX 7.0.0, Human Resources

---

# Benefit statement

The **Benefit statement** report provides a statement of the benefits that an employee is currently enrolled in. The report can be accessed by an employee directly or by the benefit administrator. The **Benefit statement** provides a list of the employee’s enrolled benefits, coverage options, costs, and any enrolled dependents or beneficiaries. The statement can be printed for a single worker or multiple workers.

> [!NOTE]
> The **Benefit statement** feature must be enabled in the **Feature management** workspace. In order to do this, the **Benefit management** feature must be turned on in Feature management. 


## Importing the Benefit statement 

You must import the **Benefit statement** using report configuration before the **Benefit statement** will be available. To do this, complete the following steps:

1.  Go to **System administration** workspace.
2.  Select the **Electronic reporting** tile.
3.  Go to **Configuration providers** and select **Repositories**.

  ![Repositories selection.](https://user-images.githubusercontent.com/26801678/134203290-7faf7245-ed08-44e9-95a1-a7ba278c42c6.png)

4.  Select **HR Resources** from the list, and then select **Open**.

    ![Configuration repositories.](https://user-images.githubusercontent.com/26801678/134203619-b3fd087d-1fe9-45ef-a588-1afedfe38dfd.png)

5.  Select the **Benefit statement model** in the left pane and expand it so that **Benefit statement format** displays.
6.  Select **Benefit statement format** on the left pane.
7.  On the right side of the screen, there will be a **Versions** FastTab. Select **Import**.

    ![Versions FastTab.](https://user-images.githubusercontent.com/26801678/134203763-f12ef549-e326-400d-ac69-b25fc94af47b.png)

## Generate the Benefit statement as a PDF File

By default, the **Benefit statement** will print as a Microsoft Word document. To print in a PDF format, you will need to configure the PDF option in **Electronic reporting destination**. 

1. To do this, go to **System administration workspace** > **Electronic reporting** > **Related links** > **Electronic reporting destination**.
2.  Select **New**.
3.  In the **Reference** field, select **Benefit statement format**.
4.  On the **File destination** FastTab, select **New**.
5.  In the **Name** field, enter **Benefits Statement PDF**.
6.  In the **File component name** field, select **Benefit statement**.
7.  Select the **Convert to PDF** checkbox.
8.  Select **Settings** from the menu item. 

    ![File destination.](https://user-images.githubusercontent.com/26801678/134203881-a3f1ebc3-d816-485d-a53b-026cc29cae64.png)

9.  Select the **File** FastTab, and then select **Enabled**.
10.  Select **OK**.
   
> [!NOTE]
> The benefits management feature is in a Preview state. There is a known issue when using the email destination setting in the **Electronic reporting destination** report. You may receive an error message and the email will fail to send.

The **Benefit statement** can be generated from the following pages:

-   **Benefits management workspace** > **Links** > **Reports** > **Benefit statement**
-   **Employees (legacy form)** > **Personal information tab** > **Benefit statement**
-   **Streamlined employee entry** > **Benefit reports** > **Benefit statement**
-   **Employee self service** > **Benefits** > **View Benefit statement**

> [!NOTE]
>  Access to the **Benefit statement** in **Employee self-service** is controlled by the privilege **View benefit statement**. This is under the **Employee Self-Service Benefits** duty. This privilege is granted to employees by default.

## Report contents

The **Benefit statement** will print the confirmed plan selections of the employee, including any waived plans. The following image shows an example of this report. 

![Benefit statement report.](https://user-images.githubusercontent.com/26801678/134204058-61baa318-fede-4795-a256-acdf3217f9f9.png)

The report displays the **Plan**, **Coverage option**, **Employee cost**, and **Employer cost**. The report will also list any covered dependents. If the plan has beneficiaries associated to it, the beneficiaries and their distribution priority and percent will display.

The **Benefit statement** report can be printed for multiple employees at the same time using the **Records to include** FastTab on the **Benefit statement** page.
