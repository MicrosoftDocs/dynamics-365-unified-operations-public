---
# required metadata

title: Generate Affordable Care Act (ACA) reports
description: Affordable Care Act (ACA) reporting generates forms 1095-B and 1095-C in support of the **Employer Mandate** portion of the Affordable Care Act.
author: twheeloc
ms.date: 02/03/2020
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

# Generate ACA reports


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

Affordable Care Act (ACA) reporting generates forms 1095-B and 1095-C in support of the **Employer Mandate** portion of the Affordable Care Act.

> [!NOTE]
> ACA reporting is only enabled for legal entities in the United States.

## Getting started

To track information for forms 1095-B and 1095-C, you must first create one or more Affordable care coverage groups. Affordable Care coverage groups indicate:

- The offer of coverage for an employee
- The employee’s share of the lowest cost monthly premium, if the cost is above the federal poverty line
- Safe Harbor used by the employer, if applicable

Affordable Care coverage groups allow you to manage the information for these fields without changing every employee record where the conditions are the same. You can easily assign Affordable Care coverage groups to one or more employees by using the **Mass assign** option on the page.

## Maintaining multiple versions of a coverage group

You can maintain multiple versions of any coverage group. This functionality allows you to make changes without having to create a new group and reassign employees to it. 

After you’ve created ACA coverage groups, you can mass assign the groups to employees with the **Mass assignment** option. You can also individually indicate whether to track and report ACA information, and assign an employee to an Affordable Care coverage group.

You don't need to track some ACA coverage information, such as for part-time employees. In this case, set the **Report coverage** field to **No**. Although you must assign each employee with trackable ACA information to an Affordable Care coverage group, you can still change the following options for months with different values:

- **Offer of coverage**
- **Employee share of cost**
- **Safe Harbor**

To enter exceptions for Affordable Care coverage group values, select the **Affordable Care Coverage** link on the **Worker detail** page under the **Additional information** section on the **Employment tab**.

## Reporting health care coverage

In addition to tracking health insurance coverage offered to full-time employees, if the employer offers employer-sponsored self-insured health coverage for which the employee is enrolled (regardless of whether their employment status is full-time or part-time), additional information needs to be reported on the 1095-C. Each employee (including dependents) covered by the employer-sponsored benefit plans needs to be included on the report for the months they were covered. 

You can indicate whether or not each benefit plan must be reported by selecting the **ACA reportable** check box.

In addition, if employees have chosen to have any of their dependents covered under a benefit, you can indicate the dates the dependent was covered for each employee on the **Maintain benefits** page. To indicate that the dependent is covered under the benefit, select the **Edit** button in the action pane of the **Dependents** fast tab.

On the **Dependent coverage date manager** page, you can indicate the dates the dependent was covered by the benefit. Entering dates on this page will automatically select the **Covered** checkbox on the **Maintain benefits** page.

## Generate 1095-B and 1095-C forms

You can also generate 1095-B and 1095-C forms from within the product, and distribute them to each of your employees. The system can also electronically generate 1095-C forms and the 1094-C IRS transmittal files.  

When generating the 1095-C form, enter the appropriate tax year and indicate if social security numbers should be masked. If you're printing 1095-C forms for more than 500 employees, you'll receive more than one PDF file. It’s recommended that you increase the **Maximum file size** in the **Document management parameters** window to 150 MB.

## Viewing information

You can use the **Worker Affordable Care coverage** page to see which employees have been assigned to each coverage group, which employees don’t need to be included on a report, and which employees are unassigned.

If any of the default values from the Affordable Care coverage group have been overridden, an asterisk will appear next to the value that was changed. If the values for all 12 months are the same and haven’t been overridden, the value will print in the **All 12 months** column.

You can also use the inquiry window to understand which employees have been flagged as not ACA reportable. You don’t need to track whether coverage was offered to them and won't need to issue a 1095-C to them at the end of the year. Select **Not ACA reportable** in the **Filter by** field to generate a list of all employees who won't receive a 1095-C.

In addition, you can view any employees who are unassigned (the **ACA Report coverage** field is empty) or who have been assigned to an Affordable Care coverage group that is expired for the year selected in the **Year** field.

You can export lists of employees that were generated using any of the filtering options to Excel.

If you need to report covered individuals because you provide self-insured coverage, you can view any dependents covered under benefit plans marked as **ACA reportable**. Select **View Dependent coverage** on the action pane.

> [!NOTE]
> Only benefit plans marked as **ACA reportable** display in the inquiry window.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
