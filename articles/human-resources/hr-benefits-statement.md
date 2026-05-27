---
# required metadata

title: Benefit statement
description: The Benefit statement report explains the benefits that an employee is currently enrolled in.
author: twheeloc
ms.date: 05/14/2026
ms.topic: how-to
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

The **Benefit statement** report provides a statement of the benefits that an employee is currently enrolled in. An employee or the benefit administrator can access the report. The **Benefit statement** provides a list of the employee’s enrolled benefits, coverage options, costs, and any enrolled dependents or beneficiaries. You can print the statement for a single worker or multiple workers.

> [!NOTE]
> An administrator must enable the **Benefit statement** feature in the **Feature management** workspace. To enable this feature, turn on the **Benefit management** feature in **Feature management**.

## Importing the Benefit statement

You must import the **Benefit statement** by using report configuration before the **Benefit statement** is available. To do this, complete the following steps:

1. Go to **System administration** workspace.
1. Select the **Electronic reporting** tile.
1. Go to **Configuration providers** and select **Repositories**.

  ![Repositories selection.](https://user-images.githubusercontent.com/26801678/134203290-7faf7245-ed08-44e9-95a1-a7ba278c42c6.png)

1. Select **HR Resources** from the list, and then select **Open**.

    ![Configuration repositories.](https://user-images.githubusercontent.com/26801678/134203619-b3fd087d-1fe9-45ef-a588-1afedfe38dfd.png)

1. Select the **Benefit statement model** in the left pane and expand it so that **Benefit statement format** displays.
1. Select **Benefit statement format** on the left pane.
1. On the right side of the screen, the **Versions** FastTab appears. Select **Import**.

    ![Versions FastTab.](https://user-images.githubusercontent.com/26801678/134203763-f12ef549-e326-400d-ac69-b25fc94af47b.png)

## Generate the Benefit statement as a PDF file

By default, the **Benefit statement** prints as a Microsoft Word document. To print in a PDF format, you need to configure the PDF option in **Electronic reporting destination**.

1. Go to **System administration workspace** > **Electronic reporting** > **Related links** > **Electronic reporting destination**.
1. Select **New**.
1. In the **Reference** field, select **Benefit statement format**.
1. On the **File destination** FastTab, select **New**.
1. In the **Name** field, enter **Benefits Statement PDF**.
1. In the **File component name** field, select **Benefit statement**.
1. Select the **Convert to PDF** checkbox.
1. Select **Settings** from the menu item.

    ![File destination.](https://user-images.githubusercontent.com/26801678/134203881-a3f1ebc3-d816-485d-a53b-026cc29cae64.png)

1. Select the **File** FastTab, and then select **Enabled**.
1. Select **OK**.

> [!NOTE]
> The benefits management feature is in preview. There's a known issue when you use the email destination setting in the **Electronic reporting destination** report. You might receive an error message and the email fails to send.

You can generate the **Benefit statement** from the following pages:

- **Benefits management workspace** > **Links** > **Reports** > **Benefit statement**
- **Employees (legacy form)** > **Personal information tab** > **Benefit statement**
- **Streamlined employee entry** > **Benefit reports** > **Benefit statement**
- **Employee self service** > **Benefits** > **View Benefit statement**

> [!NOTE]
> Access to the **Benefit statement** in **Employee self-service** is controlled by the privilege **View benefit statement**. This privilege is under the **Employee Self-Service Benefits** duty. Employees are granted this privilege by default.

## Report contents

The **Benefit statement** report shows the confirmed plan selections for the employee, including any waived plans. The following image shows an example of this report.

![Benefit statement report.](https://user-images.githubusercontent.com/26801678/134204058-61baa318-fede-4795-a256-acdf3217f9f9.png)

The report displays the **Plan**, **Coverage option**, **Employee cost**, and **Employer cost**. The report also lists any covered dependents. If the plan has beneficiaries associated with it, the report displays the beneficiaries along with their distribution priority and percentage.

You can print the **Benefit statement** report for multiple employees at the same time by using the **Records to include** FastTab on the **Benefit statement** page.
