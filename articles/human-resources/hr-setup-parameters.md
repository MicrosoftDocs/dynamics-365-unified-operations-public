---
# required metadata

title: Configure Human resources parameters
description: The settings of some Human resources parameters are shared across companies, whereas the settings of other parameters are company-specific. This article explains how to set up company-specific HR parameters.
author: andreabichsel
manager: AnnBe
ms.date: 02/03/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-human-resources
ms.technology: 

# optional metadata

ms.search.form: HRMParameters
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Core, Operations, Human Resources
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

The settings of some Human resources (HR) parameters are shared across companies, whereas the settings of other parameters are company-specific. This article explains how to set up company-specific HR parameters.

Two pages are used to set Human resources (HR) parameters. For parameters that are shared across companies, you use the **Human resources shared parameters** page. For parameters that are company-specific (in other words, the settings apply to a single company), you use the **Human resource parameters** page. On the **Human resources parameters** page, the settings are divided among six tabs:

-   General
-   Recruitment - this is not included in Dynamics 365 Human Resources
-   Compensation
-   Number sequences
-   Family and Medical Leave Act (FMLA)
-   Employee self-service

Each tab contains information that pertains to a single company. The settings on the **General** tab define the appearance of information about absence, injury and illness, and new hires. The settings on this tab also define some default entries that appear as you work. Specifically, this tab lets you select a color to apply to open absence transactions, specify the style sheet to use for reports, enable the integration between training courses and absence registration, and select the absence code that is used to control this integration. You can also indicate how long injury and illness case incidents should be kept, and specify the default identification number that is shown when a new worker is hired. 

The settings on the **Recruitment** tab define the document types that are used for correspondence that is automatically sent to applicants, and the recruitment project that is used for unsolicited applications (applications that aren't for a specific recruitment project). The period that is defined for the recruitment project aging determines the recruitment projects that are included on the **Aging projects** tile in the **Recruitment management** workspace. The period that is defined for the application deadline warning is used to display recruitment projects that are approaching their application deadline on the **Application deadline approaching** tile in the **Recruitment** workspace. 

The settings on the **Compensation** tab define whether users must confirm that they want to save information for a fixed or variable compensation plan. If you select the **Enable save validation** check box, any time that users close a compensation-related page, they receive a message that asks whether they want to save the record. Some pages in compensation management don't let users delete information. Therefore, by prompting users to verify that they want to save information, you might be able to limit the amount of information that is saved but can't be deleted later. If the **Enable save validation** check box is cleared, records are always saved immediately, possibly before the user is ready. If you're using performance management, the **Compensation** tab also lets you select a rating model to use instead of the model that is assigned to compensation plans when performance is rated. 

### Previously released functionality

The settings on the **Number sequence** tab determine the sequences that are used to automatically assign IDs to items in Human resources, such as applications, absence registrations, compensation process results, case numbers, courses, and course agendas. To maintain number sequence references and codes, use the **Number sequences** list page (click **Organization administration** &gt; **Number sequences** &gt; **Number sequences**).

> [!NOTE]
> The number of hours that are worked can't exceed 1,250, and the length of employment can't exceed 12 months. These maximum values are in accordance with federal law in the United States. Finally, the settings on the **Employee self-service** tab determine the information that managers can enter on behalf of their employees.
