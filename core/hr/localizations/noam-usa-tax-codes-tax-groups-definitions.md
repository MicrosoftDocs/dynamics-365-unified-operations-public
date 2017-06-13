---
# required metadata

title: Tax codes, tax groups, and posting definitions FAQ
description: This topic answers frequently asked questions about tax and posting definitions.
author: rschloma
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: JournalizingDefinition, JournalizingDefinitionTrans, PayrollTaxCode, PayrollTaxGroup
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 31
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 221414
ms.assetid: cd8cceb4-0ea3-4770-930b-0869e9bfa3c4
ms.search.region: USA
# ms.search.industry: 
ms.author: brpotter
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Tax codes, tax groups, and posting definitions FAQ

[!include[banner](../includes/banner.md)]


This topic answers frequently asked questions about tax and posting definitions.

This topic describes functionality that is available only if the **Payroll - USA** configuration key is selected.

## Can I mass-update tax codes?
Yes, you can update all the tax codes in a tax group at the same time. The financial information for each tax code is set up separately for each legal entity. If you change the values for one legal entity, the values for other legal entities aren’t affected. When you update a tax code by using the mass-update functionality, the changes are effective immediately. To make date-effective changes to a tax code, use the **Maintain versions** button on the **Tax codes** page.

## Can I mass-create tax groups?
Yes. When you set up Payroll, you automatically create a set of system-defined tax groups the first time that you click the **Update tax data** link on the **Payroll** area page. Each system-defined tax group contains tax codes of a particular type. For example, all tax codes for school districts are included in the SCHL tax group, and all tax codes for state income tax are included in the SIT tax group. These tax groups are updated every time that you run the **Update tax data** process. You can manually create additional tax groups. For more information, see [Tax information tasks](noam-usa-tax-information-tasks.md).

## Why are some tax codes not posted according to the posting definition that is associated with their tax group?
There are two possible reasons for this behavior:

-   The **Employer tax** option for the tax code on the **Tax codes** page is incorrect for the line type on the **Transaction posting definitions** page. If some tax codes in a tax group have the correct employer tax setting for the line type, but other tax codes in the tax group don’t have the correct setting, the tax codes that have the correct setting use the posting definition for the tax group. The other tax codes use the posting definition that is specified for the **All** code for their line type. The following table shows the correct relationships of line types and employer tax settings.

    | Line type          | Required setting for the Employer tax option |
    |--------------------|----------------------------------------------|
    | Tax - contribution | Selected                                     |
    | Tax - deduction    | Cleared                                      |

-   On the **Transaction posting definitions** page, the tax code is entered on a line that uses the **Table** code. Table lines take precedence over group lines. The following table shows that value that you can enter in the **Payroll code** field, based on the value that is entered in the **Code** field. It also shows the result that each combination of a code and a payroll code produces.

    | Code  | Payroll code | Result                                                                                                                                           |
    |-------|--------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
    | Table | A tax code   | The tax code uses the specified transaction posting definition, even if the tax code is in a tax group that uses a different posting definition. |
    | Group | A tax group  | All tax codes in the tax group use the specified transaction posting definition, except any tax codes that are on a table line.                  |
    | All   | \[Blank\]    | Any tax code that isn't posted according to a table line or a group line uses the transaction posting definition that is specified for **All**.  |

## Why can't I delete a tax group?
You can’t delete a tax group that is system-defined, or that is enabled for posting definitions.

## Why can't I remove a tax code from a tax group?
You can’t remove a tax code from a system-defined tax group.

## Why can't I select Group in the Code field? The only options that I see are Table and All.
On the **Transaction posting definitions** page, the **Group** option is available only for the **Tax - contribution** and **Tax - deduction** line types.

## Can I delete a tax code from a tax group that is enabled for posting definitions?
Yes. On the **Tax codes** page, clear the **Enable posting definitions** option, delete the tax code, and then select the option again.

## Can I disable posting definitions for a tax group?
Yes, but you can’t disable posting definitions for a tax group that is used in a transaction posting definition. If you open the **Transaction posting definitions** page and delete the line that uses the tax group, you can then clear the **Enable posting definitions** option on the **Tax codes** page.

## Why can a tax code belong to only one tax group that is enabled for posting definitions?
A tax code can belong to only one tax group that is enabled for posting definitions, because this restriction helps guarantee that the tax is posted to the correct account. If a tax code were included in two groups, the system would use the posting definition for the group that was processed first. For example, you could include the Colorado state income tax in both the state income tax group and the Colorado tax group. If both groups were enabled for posting definitions, the system would not consistently use the same posting definition for the Colorado state income tax. Sometimes, the tax might be posted by using the posting definition for the state income tax group. At other times, the tax might by posted by using the posting definition for the Colorado tax group. You would never know which posting definition was used.

## Don't see your question here?
We're working to include as many questions as we can, so that Microsoft Dynamics AX Help will be more useful to people just like you. Tell us what question you would like to add to this topic. Send email to <adocs@microsoft.com>.


