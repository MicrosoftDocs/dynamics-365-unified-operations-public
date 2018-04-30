---
title: About integration for service agreements and projects
TOCTitle: About integration for service agreements and projects
ms:assetid: dbd8a31d-5686-4640-b043-850d7ec427b0
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Aa551252(v=AX.60)
ms:contentKeyID: 36059670
ms.date: 05/02/2014
mtps_version: v=AX.60
_tocRel: gg242492(v=ax.60)/toc.json
---

# About integration for service agreements and projects 




When you work with service agreements and service agreement lines, you use data that is set up in the following areas in **Project management and accounting**.

## Project prices

The cost and the sales price for a service agreement transaction are derived from the cost price setup that applies to the project that is attached to the service agreement. Cost and sales prices can be set up by project, employee, and category. For more information about project cost and sales prices, see [Set up cost prices and sales prices for projects](set-up-cost-prices-and-sales-prices-for-projects.md) and [About sales price models](about-sales-price-models.md).

## Project validation

The projects, employees, and categories that are available for selection on a service agreement line can be limited by the validation setup in **Project management and accounting**. By using the validation setup, you can combine employees, projects, and categories for control access. For more information about validation, see [About validation in projects](about-validation-in-projects.md).

## Project line properties

A line property is entered automatically for a service agreement line.

Line properties are created in the **Line properties** form in **Project management and accounting**. The line property that is entered on a service agreement is attached to the project that is selected for the service agreement and inherited subsequently by the service agreement line. For more information about line properties, see [About line property setup](about-line-property-setup.md).

## Default offset accounts

If you enter an expense transaction, a default expense offset account is selected automatically for the transaction. The default expense account is set up for the project that is attached to the current service agreement. For more information about default expense accounts, see [Default offset account for expenses (form)](https://technet.microsoft.com/en-us/library/aa616251\(v=ax.60\)).

## Project categories

The categories that are available for service agreement lines are set up in the **Project categories** form in **Project management and accounting**. For more information about project categories, see [About project category groups](about-project-category-groups.md).


> [!NOTE]
> <P>Categories that have the <STRONG>Active in journals</STRONG> check box selected on the <STRONG>Project</STRONG> tab in the <STRONG>Project categories</STRONG> form are available for selection. However, if the <STRONG>Inactive categories</STRONG> check box is selected on the <STRONG>Journals</STRONG> tab in the <STRONG>Project management and accounting parameters</STRONG> form, all categories are available for selection.</P>



## Project parameters

If the **Terminated workers** field on the **Journals** tab in the **Project management and accounting parameters** form is selected, you can select inactive employees and active employees in the **Service agreements** and **Service orders** forms.

Also, you can enable the **Start time** and **End time** fields on the **Project** tab in the **Service orders** form to enter starting and ending times on service order lines.

## Enable the starting and ending time feature for service orders

1.  Click **Project management and accounting** \> **Setup** \> **Project management and accounting parameters**.

2.  Click the **Journals** tab, and then select the **Show start/end times** check box.

3.  Click **Project management and accounting** \> **Setup** \> **Journals** \> **Journal names**.

4.  Select the journal name that is attached to the service order.

5.  Click the **General** tab, and then select the **Show start/end times** check box.


> [!NOTE]
> <P>Select the journal name for the service order in the <STRONG>Hour</STRONG> field on the <STRONG>Journals</STRONG> tab in the <STRONG>Service management parameters</STRONG> form.</P>



For more information about journal names for projects, see [About journal names](about-journal-names.md).

  


