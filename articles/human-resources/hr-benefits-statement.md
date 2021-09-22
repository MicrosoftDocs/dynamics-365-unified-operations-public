---
# required metadata

title: Benefits Statement
description: Benefit statements explain the benefits that an employee is currrently enrolled in.
author: twheeloc
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
ms.author: twheeloc
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: AX 7.0.0, Human Resources

---

# Benefits statement

The benefits statement provides a statement of the benefits that an employee is currently enrolled in. The report can be accessed by an employee directly or by
the benefit administrator. The benefit statement provides a list of the employee’s enrolled benefits, coverage options, costs and any enrolled dependents or beneficiaries. The statement can be printed for a single worker or multiple workers.

> [!NOTE]
The **Benefits statement** feature is dependent upon the **Benefits management** feature switch being enabled in **Feature management**. Once the **Benefits management** feature is on, the **Benefits statement** feature can be enabled. The **Benefits statement** feature can be turned off in feature management, once it’s turned on.


## Importing the Benefits statement 

You must import the **Benefits statement** via report configuration before the **Benefits Statement** will be available.

1.  Navigate to **System Administration** workspace.

2.  Select the **Electronic Reporting** tile.

3.  Go to **Configuration providers** and select **Repositories**.

  ![Repositories.](https://user-images.githubusercontent.com/26801678/134203290-7faf7245-ed08-44e9-95a1-a7ba278c42c6.png)

4.  Select **HR Resources** from the list and **Open** from the menu.

    ![Configuration Repositories](https://user-images.githubusercontent.com/26801678/134203619-b3fd087d-1fe9-45ef-a588-1afedfe38dfd.png)

5.  Select the **Benefit statement model** in the left pane and expand it, so that **Benefit statement format** displays.

6.  Select **Benefit statement format** on the left pane.

7.  On the right side of the screen, there will be a **Versions** FastTab. Select **Import**.

    ![Versions](https://user-images.githubusercontent.com/26801678/134203763-f12ef549-e326-400d-ac69-b25fc94af47b.png)

## Generate the Benefits statement as a PDF File

By default, the **Benefit statement** will print in a **Microsoft Word** document format. To print to a **PDF** format, you will need to configure the PDF option in **Electronic reporting destination** (**System administration workspace** > **Electronic reporting** > **Related links** > **Electronic reporting destination**).

1.  Select **New**.

2.  In the **Reference** field, select **Benefit statement format**.

3.  On the **File destination** FastTab, select **New**.

4.  In the **Name** field, enter **Benefits Statement PDF**.

5.  In the **File component name** field, select **Benefit statement**.

6.  Select the **Convert to PDF** checkbox.

7.  Select **Settings** from the menu item. 

    ![File Destination](https://user-images.githubusercontent.com/26801678/134203881-a3f1ebc3-d816-485d-a53b-026cc29cae64.png)

8.  Select the **File** fast tab and select **Enabled**.

![Enabled](https://user-images.githubusercontent.com/26801678/134203994-55d793dd-45fc-458c-a27a-2139b18aff1e.png)

9.  Select **OK**.
   
> [!NOTE]
> The benefits management feature is in a Preview state. There is a known issue when using the email destination setting in the **Electronic reporting destination** report. The user will receive an error message and the email will fail to send.

The **Benefit statement** can be generated from the following pages:

-   **Benefits management workspace** > **Links** > **Reports** > **Benefit statement**

-   **Employees (legacy form)** > **Personal information tab** > **Benefit statement**

-   **Streamlined employee entry** > **Benefit reports** > **Benefit statement**

-   **Employee self service** > **Benefits** > **View benefit statement**

> [!NOTE]
>  Access to the **Benefit statement** in **Employee self service** is controlled by the privilege **View benefit statement**. This is under the **Employee Self-Service Benefits** duty. This privilege is granted to employees by default.

## Report contents:

The **Benefit statement** will print the confirmed plan selections of the employee, including any waived plans.

![Report.](https://user-images.githubusercontent.com/26801678/134204058-61baa318-fede-4795-a256-acdf3217f9f9.png)

The report will display the **Plan**, **Coverage option**, **Employee cost**, and **Employer cost**. The statement will also list any covered dependents. If the plan has beneficiaries associated to it, the beneficiaries and their distribution priority and percent will display.

The **Benefit statement** report can be printed for multiple employees at a time via the **Records to include** FastTab on the **Benefit statement** print page.
