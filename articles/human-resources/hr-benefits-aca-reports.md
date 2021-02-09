---
# required metadata

title: Generate Affordable Care Act (ACA) reports
description: Affordable Care Act (ACA) reporting assists employers who need to track the information reported on forms 1095-B and 1095-C in support of the **Employer Mandate** portion of the Affordable Care Act.
author: andreabichsel
manager: tfehr
ms.date: 02/03/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-human-resources
ms.technology: 

# optional metadata

# ms.search.form: HcmACACoverageGroup, BenefitWorkspace, HcmBenefitSummaryPart
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
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

# Generate ACA reports

Affordable Care Act (ACA) reporting assists employers who need to track the information reported on forms 1095-B and 1095-C in support of the **Employer Mandate** portion of the Affordable Care Act.

> [!NOTE]
> ACA reporting is only enabled for legal entities in the United States.

## Getting started

When beginning to track information to report on forms 1095-B and 1095-C, you must first create one or more ACA coverage groups. These ACA coverage groups will be used to indicate the offer of coverage that was provided to an employee, the employee’s share of the lowest cost monthly premium (if the cost is above the federal poverty line), and Safe Harbor used by the employer, if applicable. Using ACA groups enables you to manage the information for these fields without needing to touch every employee record where the conditions are the same. You can easily assign Affordable Care coverage groups to one or more employees using the Mass assign option on the page.

## Maintaining multiple versions of a coverage group

You can maintain multiple versions of any coverage group. This functionality allows you to make changes without having to create a new group and reassign employees to it. 

After you’ve created ACA coverage groups, you can mass assign the groups to employees with the **Mass assignment** option. You can also go to each employee and indicate whether ACA information needs to be tracked and reported for that employee, and assign the employee to an ACA coverage group.

Some ACA coverage information doesn’t need to be tracked or reported, such as for part-time employees. In this case, set the **Report coverage** field to **No**. Although each employee for which ACA information needs to be tracked needs to be assigned to an Affordable Care coverage group, you can still change the **Offer of coverage**, **Employee share of cost** and **Safe Harbor** options for any month that may need different values than those entered in the Affordable Care coverage group.

To enter exceptions to any of the Affordable Care coverage group values, select the **Affordable Care Coverage** link on the **Worker detail** page under the **Additional information** section on the **Employment tab**.

## Reporting health care coverage

In addition to tracking what if any health insurance coverage was offered to a full-time employee, if the employer offers employer-sponsored self-insured health coverage for which the employee is enrolled (regardless of whether their employment status is full-time or part-time), additional information needs to be reported on the 1095-C. Each employee (including dependents) covered by the employer-sponsored benefit plans needs to be included on the report for the months they were covered. 

You can indicate whether or not each Benefit plan must be reported by selecting the **ACA reportable** check box.

In addition, if employees have chosen to have any of their dependents covered under a benefit you can indicate the dates the dependent was covered for each employee on the Maintain benefits page. To indicate that the dependent is covered under the benefit, choose the Edit button in the action pane of the Dependents FastTab.

On the **Dependent coverage date manager** page, you can indicate the dates the dependent was covered by the benefit. Entering dates on this page will automatically select the **Covered** checkbox on the **Maintain benefits** page.

## Generate 1095-B and 1095-C forms

You can also generate 1095-B and 1095-C forms from with in the product, and distribute them to each of your employees. Electronically generating 1095-C and the corresponding 1094-C transmittal files which can be used to send to the IRS, can also be generated from the system.  

When generating the 1095-C form, enter in the appropriate tax year and indicate if social security numbers should be masked. If you are printing 1095-C forms for more than 500 employees, you will receive more than one PDF file. It’s recommended that you increase the **Maximum file size** in the **Document management parameters** window to 150 MB.

## Viewing information

You can use the **Worker Affordable Care coverage** page to see which employees have been assigned to each coverage group, which employees don’t need to be included on a report, and which employees are unassigned.

If any of the default values from the Affordable Care coverage group have been overridden an asterisk will appear next to the value that was changed. If the values for all 12 months are the same and haven’t been overridden, the value will print in the **All 12 months** column.

You can also use the inquiry window to understand which employees have been flagged as not ACA reportable, meaning you don’t need to track whether coverage was offered to them and will not need to issue a 1095-C to them at the end of the year. By selecting **Not ACA reportable** in the **Filter by** field, you can generate a list of all employees that have been flagged to not receive a 1095-C.

In addition to viewing a list of employees that are not ACA reportable, you can also view any employees who are unassigned (the **ACA Report coverage** field is empty) or that have been assigned to an Affordable Care coverage group that is expired for the year selected in the **Year** field.

You can export lists of employees that were generated using any of the filtering options to
Excel.

If you need to report covered individuals because as an employer you provide self-insured coverage you can also view any dependents covered under benefit plans that have been marked as **ACA reportable** by selecting the View Dependent coverage action on the action pane strip.

> [!NOTE]
> Only benefit plans marked as **ACA reportable** will display in the inquiry window.
