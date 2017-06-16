---
# required metadata

title: Generate Affordable Care Act reports
description: Functionality is available to assist employers that need to track the information reported on forms 1095-B and 1095-C in support of the Employer Mandate portion of the Affordable Care Act. Note this functionality is only enabled for legal entities in the United States.
author: kherr
manager: AnnBe
ms.date: 07/01/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: rschloma
ms.search.scope: AX 7.0.0, Talent, Core
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 3b953d5f-6325-4c9e-8b9b-6ab0458a73f8
ms.search.region: Global
# ms.search.industry: 
ms.author: kherr
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: AX 7.0.0

---
# Generate Affordable Care Act reports
Functionality is available to assist employers that need to track the information reported on forms 1095-B and 1095-C in support of the **Employer Mandate** portion of the Affordable Care Act. Note this functionality is only enabled for legal entities in the United States.

## Getting started
When beginning to track information to report on forms 1095-B and 1095-C, you must first create one or more Affordable Care coverage groups. These Affordable Care coverage groups will be used to indicate the offer of coverage that was provided to an employee, the employee’s share of the lowest cost monthly premium (if the cost is above the federal poverty line) as well as Safe Harbor used by the employer, if applicable. Using Affordable Care Act groups enables you to manage the information for these fields without needing to touch every employee record where the conditions are the same. In addition, Affordable Care coverage groups can easily be assigned to one or more employees using the Mass assign functionality on the page.

## Maintaining multiple versions of a coverage group
You can maintain multiple versions of any coverage group, which allows you to make changes that keep the group’s information current, without having to create a new group and reassign employees to it when something changes in your organization or in the benefits that are offered. 

After you’ve created the Affordable Care coverage groups that you need, you can choose to mass assign the groups to employees using the **Mass assignment** functionality on the page, or you can go to each employee and indicate whether ACA information needs to tracked and reported for that employee as well as assigning the employee to an Affordable Care coverage group.

If affordable care coverage information doesn’t need to be tracked or reported for an employee, for example if they are a part-time employee, the **Report coverage** field could be set to No. Although each employee for which ACA information needs to be tracked needs to be assigned to an Affordable Care coverage group, you can still change the **Offer of coverage**, **Employee share of cost** and **Safe Harbor** options for any month – or months – that may need different values than those entered in the Affordable Care coverage group.

To enter exceptions to any of the Affordable Care coverage group values, click on the Affordable Care Coverage link found on the Worker detail page, which is under the Additional information section on the Employment tab.

## Reporting health care coverage
In addition to tracking what if any health insurance coverage was offered to a full-time employee, if the employer offers employer-sponsored self-insured health coverage for which the employee is enrolled (regardless of whether their employment status is full-time or part-time), additional information needs to be reported on the 1095-C. Each employee (including dependents) covered by the employer-sponsored benefit plans needs to be included on the report for the months they were covered. 

You can indicate whether or not each Benefit plan must be reported by selecting the **ACA reportable** check box.

In addition, if employees have chosen to have any of their dependents covered under a benefit you can indicate the dates the dependent was covered for each employee on the Maintain benefits page. To indicate that the dependent is covered under the benefit, choose the Edit button in the action pane of the Dependents FastTab.

On the **Dependent coverage date manager** page, you can indicate the dates the dependent was covered by the benefit. Entering dates on this page will automatically select the **Covered** checkbox on the **Maintain benefits** page.

## Generate 1095B and 1095C forms
You can also generate 109-B and 1095-C forms from with in the product, and distribute them to each of your employees. Electronically generating 1095-C and the corresponding 1094-C transmittal files which can be used to send to the IRS, can also be generated from the system.  

When generating the 1095-C form enter in the appropriate calendar or tax year as well as if you want to print the two-page or three page form. The three-page form is only needed if the Employer provided self-insured coverage and an employee has more than six covered dependents including themselves. When generating the Two page form the system will automatically detect if an employee has more than 6 covered dependents and will not include that employee when generating the form. Additionally, when generating the three-page form the system will only include those employees that have more than six covered dependents.

## Viewing information
You can use the **Worker Affordable Care coverage** page to see which employees have been assigned to each coverage group, which employees don’t need to be included on a report, and which employees are unassigned.

If any of the default values from the Affordable Care coverage group have been overridden an asterisk will appear next to the value that was changed. If the values for all 12 months are the same and haven’t been overridden, the value will print in the **All 12 months** column.

You can also use the inquiry window to understand which employees have been flagged as not ACA reportable, meaning you don’t need to track whether coverage was offered to them and will not need to issue a 1095-C to them at the end of the year. By selecting **Not ACA reportable** in the **Filter by** field, you can generate a list of all employees that have been flagged to not receive a 1095-C.

In addition to viewing a list of employees that are not ACA reportable, you can also view any employees who are unassigned (the **ACA Report coverage** field is empty) or that have been assigned to an Affordable Care coverage group that is expired for the year selected in the **Year** field.

You can export lists of employees that were generated using any of the filtering options to
Excel.

If you need to report covered individuals because as an employer you provide self-insured coverage you can also view any dependents covered under benefit plans that have been marked as **ACA reportable** by selecting the View Dependent coverage action on the action pane strip.

**Note:** Only benefits whose plan has been marked as **ACA reportable** will display in the inquiry window.
