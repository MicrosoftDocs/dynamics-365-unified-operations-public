---

# required metadata

title: Avoid text truncation on the position hierarchy and export to Visio
description: This topic explains how to fix the issue of truncated names of individuals and positions in the position hierarchy in Microsoft Dynamics 365 Human Resources. 
author: twheeloc
ms.date: 08/19/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: HcmPositionHierarchyView, HcmPosition
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Avoid text truncation on the position hierarchy and export to Visio


[!INCLUDE [PEAP](../includes/peap-2.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

**Issue**

When a customer views the position hierarchy in Microsoft Dynamics 365 Human Resources, the names of individuals and positions are truncated. Therefore, it can be difficult to take a screenshot, or to print and distribute the hierarchy.

![Position hierarchy.](media/position-h.png)

**Cause**

This behavior is by design.

**Resolution**

Unfortunately, users can't easily change the size of the text. However, you can export the position hierarchy out of Human Resources and then import it into Microsoft Visio. Although the following article was written for Microsoft Dynamics AX 2012, the process still applies to Human Resources: [Export a position hierarchy to Microsoft Visio](/dynamicsax-2012/appuser-itpro/export-a-position-hierarchy-to-microsoft-visio).

Follow these steps to export to Visio.

1. In Human Resources, open the **Positions** list page.

    To include more information in the organization structure diagram, add fields to the **Positions** list, so that they are available when you use the **Organization chart wizard** later in this procedure.

2. On the Action Pane, select the **Open in Microsoft Office** button, and then, under **Export to Excel**, select **Positions**. Alternatively, press Ctrl+T.

    ![Export the Positions list page to Excel.](media/org-admin.png)

3. Save the Excel file that is exported.

    ![Export to Excel dialog box.](media/export-excel.png)

4. In Visio, select **Visio - Create New**, and select the **Business** template category.

    ![New diagram.](media/new.png)

5. Select **Organization Chart Wizard**, and then select **Create**.

    ![Organization Chart Wizard dialog box.](media/orgchart-wizard.png)

6. Select **Information that's already stored in a file or database**, and then select **Next**.

    ![Organization Chart Wizard 1.](media/orgchart-wizard7.png)

7. Choose **A text, Org Plus (\*.txt), or Excel file**, and then select **Next**.

    ![Organization chart wizard 2.](media/orgchart-wizard3.png)

8. Browse to select the exported Excel file that contains the position hierarchy, and then select **Next**.

    ![Organization Chart Wizard 3.](media/orgchart-wizard2.png)

9. Set the **Name** field to **Position**, set the **Reports to** field to **Reports to position**, and then select **Next**.

    ![Organization Chart Wizard 4.](media/orgchart-wizard1.png)

10. Select the fields that should be shown on each node, and then select **Next**.

    ![Organization Chart Wizard 5.](media/orgchart-wizard5.png)

11. Add the **Position** column to the **Shape Data fields** list, and then select **Next**.

    ![Organization Chart Wizard 6.](media/orgchart-wizard6.png)

12. Pictures aren't currently available. Therefore, on the next page, select **Next**.
13. Select **I want the wizard to automatically break my organization chart across pages**.

    ![Organization Chart Wizard 7.](media/orgchart-wizard4.png)

14. Select **Finish**.

    If there are any positions that aren't in the structure, you're asked to include them in the diagram.

The diagram that is generated in Visio shows each manager on a separate worksheet.

Based on the fields that you selected to include in the diagram, each node shows the appropriate information when the Visio file is generated.

![Hierarchy diagram.](media/hierarchy.png)

**Additional option**

In Human Resources, you might also be able to use the **People** workspace to view some hierarchy-related information.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
