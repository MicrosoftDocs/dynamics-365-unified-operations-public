---

# required metadata

title: How to avoid text truncation on position hierarchy and export to Visio
description: When the customer views the position hierarchy in Talent, the names of individuals and positions are truncated, making it impossible to capture a screenshot or print the hierarchy.
author: Darinkramer
manager: AnnBe
ms.date: 11/02/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2018-11-02
ms.dyn365.ops.version: Talent

---

# How to avoid text truncation on position hierarchy and export to Visio

[!include [banner](includes/banner.md)]


**Issue:**

When the customer views the position hierarchy in Talent, the names of individuals and positions are truncated, making it difficult to take a screenshot or print the hierarchy and distribute it.

![position hierarchy](media/position-h.png)

**Cause:**

By design.  

**Resolution:**

Unfortunately, the size of the text is not something that is easily modified by
the user. However, you can export out of Talent and an import into Visio. This
article was written for AX 2012, but the process is still applicable for Talent
as well.

[https://docs.microsoft.com/en-us/dynamicsax-2012/appuser-itpro/export-a-position-hierarchy-to-microsoft-visio](https://docs.microsoft.com/en-us/dynamicsax-2012/appuser-itpro/export-a-position-hierarchy-to-microsoft-visio)

Steps to export to Visio:

1.  Open the **Positions** list. (If you want to include more information in
    the Org structure diagram, add fields to the **Position** list to make them
    available during the Wizard phase below.

2.  Click **Export to Excel** in the action pane (Ctrl-T).

![organization administration](media/org-admin.png)

3.  Save the Excel file that has been exported.

![Export to Excel](media/export-excel.png)

4.  Open **Visio - Create New** within Visio and choose the "Business template"
    category.

![new diagram](media/new.png)

5.  Choose the **Organization Chart Wizard** and click **Create**.

![org chart wizard 1](media/orgchart-wizard.png)

6.  Select **Information that's already stored in a file or database** and
    click **Next**.

![org chart wizard 2](media/orgchart-wizard7.png)

7.  Choose **A text, Org Plus (\*.txt), or Excel file** and click **Next**.

![org chart wizard 3](media/orgchart-wizard3.png)

8.  Choose to create from your recently created Excel file containing the hierarchy and click **Next**.

![org chart wizard 4](media/orgchart-wizard2.png)

9.  Set **Name** to "Position" and **Reports to** to "Reports to position" and
    click **Next**.

![org chart wizard 5](media/orgchart-wizard1.png)

10.  Choose the fields to display on each node and click **Next**.

![org chart wizard 6](media/orgchart-wizard5.png)

11.  Choose the "Position" column to appear as **Shape data fields** and click **Next**.

![org chart wizard 7](media/orgchart-wizard6.png)

12.  Click **Next**.

13.  Pictures aren’t currently available.

14.  Select **I want the wizard to automatically break my organization chart across pages**.

![org chart wizard 8](media/orgchart-wizard4.png)

15.  Click **Finish**.

    1.  If there are positions not in the structure you will be asked to include
        those in the diagram.

    2.  The diagram will show each manager on a worksheet within Visio.

    3.  Based on what you included in the diagram, you will see the information
        when you generate the Visio file in each node.

![hierarchy diagram](media/hierarchy.png)

**Additional option:**

In Talent, you may also be able to leverage the **People** workspace as well to view some hierarchy related information.
