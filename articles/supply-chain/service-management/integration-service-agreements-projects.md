---
title: Integration for service agreements and projects 
description: When you work with service agreements and service agreement lines, you use data that is set up in the areas in Project management and accounting.
author: ChristianRytt
ms.author: crytt
ms.topic: article
ms.date: 05/01/2018
ms.custom:
ms.reviewer: kamaybac
ms.search.form: ProjParameters
---

# Integration for service agreements and projects 

[!include [banner](../includes/banner.md)]


When you work with service agreements and service agreement lines, you use data that is set up in the following areas in **Project management and accounting**.

## Project prices

The cost and the sales price for a service agreement transaction are derived from the cost price setup that applies to the project that is attached to the service agreement. Cost and sales prices can be set up by project, employee, and category. 

## Project validation

The projects, employees, and categories that are available for selection on a service agreement line can be limited by the validation setup in **Project management and accounting**. By using the validation setup, you can combine employees, projects, and categories for control access. 

## Project line properties

A line property is entered automatically for a service agreement line.

Line properties are created in the **Line properties** form in **Project management and accounting**. The line property that is entered on a service agreement is attached to the project that is selected for the service agreement and inherited subsequently by the service agreement line. 

## Default offset accounts

If you enter an expense transaction, a default expense offset account is selected automatically for the transaction. The default expense account is set up for the project that is attached to the current service agreement.

## Project categories

The categories that are available for service agreement lines are set up in the **Project categories** form in **Project management and accounting**. 

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







[!INCLUDE[footer-include](../../includes/footer-banner.md)]