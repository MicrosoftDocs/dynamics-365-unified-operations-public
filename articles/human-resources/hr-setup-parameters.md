---
# required metadata

title: Configure Human resources parameters
description: The settings of some Human resources parameters are shared across companies, whereas the settings of other parameters are company-specific. This article explains how to set up company-specific HR parameters.
author: andreabichsel
manager: tfehr
ms.date: 02/03/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-human-resources
ms.technology: 

# optional metadata

ms.search.form: HRMParameters, HcmPersonnelManagementWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 51941
ms.assetid: 2cfb061a-a616-4bf9-9d98-9cde00039eec
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Configure Human resources parameters

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

The settings of some Human resources (HR) parameters are shared across companies, whereas the settings of other parameters are company-specific. This article explains how to set up company-specific HR parameters.

Two pages are used to set Human resources (HR) parameters. For parameters that are shared across companies, you use the **Human resources shared parameters** page. For parameters that are company-specific (in other words, the settings apply to a single company), you use the **Human resource parameters** page. On the **Human resources parameters** page, the settings are divided among six tabs:

- General
- Recruitment - this is not included in Dynamics 365 Human Resources
- Compensation
- Number sequences
- Family and Medical Leave Act (FMLA)
- Employee self-service

Each tab contains information that pertains to a single company. 

## General

The settings on the **General** tab define the appearance of information about absence, injury and illness, and new hires. The settings on this tab also define some default entries that appear as you work. Specifically, this tab lets you:

- Select a color to apply to open absence transactions
- Specify the style sheet to use for reports
- Enable the integration between training courses and absence registration
- Select the absence code that is used to control this integration.

You can also indicate how long injury and illness case incidents should be kept, and specify the default identification number that is shown when a new worker is hired.

## Recruitment

The settings on the **Recruitment** tab define the document types used for correspondence that is automatically sent to applicants, and the recruitment project used for unsolicited applications (applications that aren't for a specific recruitment project).

The period defined for the recruitment project aging determines the recruitment projects that are included on the **Aging projects** tile in the **Recruitment management** workspace. The period defined for the application deadline warning is used to display recruitment projects that are approaching their application deadline on the **Application deadline approaching** tile in the **Recruitment** workspace.

For more information about recruiting, see [Recruit job candidates](hr-personnel-recruit.md).

## Compensation

The settings on the **Compensation** tab define whether users must confirm that they want to save information for a fixed or variable compensation plan. If you select the **Enable save validation** check box, any time that users close a compensation-related page, they receive a message that asks whether they want to save the record. Some pages in compensation management don't let users delete information. Therefore, by prompting users to verify that they want to save information, you might be able to limit the amount of information that is saved but can't be deleted later. If the **Enable save validation** check box is cleared, records are always saved immediately, possibly before the user is ready.

If you're using performance management, the **Compensation** tab also lets you select a rating model to use instead of the model that is assigned to compensation plans when performance is rated.

For more information about compensation, see [Compensation plans overview](hr-compensation-overview.md).

## Number sequences

The settings on the **Number sequence** tab determine the sequences that are used to automatically assign IDs to items in Human Resources, such as applications, absence registrations, compensation process results, case numbers, courses, and course agendas.

To maintain number sequence references and codes, use the **Number sequences** list page (select **Organization administration > Number sequences > Number sequences**).

For more information, see [Number sequences overview](https://docs.microsoft.com/dynamics365/fin-ops-core/fin-ops/organization-administration/number-sequence-overview?toc=/dynamics365/human-resources/toc.json).

> [!NOTE]
> The number of hours that are worked can't exceed 1,250, and the length of employment can't exceed 12 months. These maximum values are in accordance with federal law in the United States. 

## Employee self service

The settings on the **Employee self service** tab affect how Employee self service appears to employees. On this tab, you can:

- Enter a name for the Employee self service workspace
- Select which information a manager can enter on behalf of employees
- Add useful links for employees
- Restrict employees from adding or editing business contact details. For more information about restricting employees from editing business contact details, see [Restrict editing of contact details](hr-employee-self-service-restrict-editing.md).

For more information about setting up Employee self service, see [Employee and Manager self service overview](hr-employee-manager-self-service-overview.md).


[!INCLUDE[footer-include](../includes/footer-banner.md)]