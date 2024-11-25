---
# required metadata
title: Set Benefits management and Employee self service parameters for all companies
description: Configure parameters for Benefits management and Employee self service in Microsoft Dynamics 365 Human Resources.
author: twheeloc
ms.date: 08/24/2021
ms.topic: article
# optional metadata
ms.search.form: BenefitWorkspace, HcmBenefitSummaryPart
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources
---

# Set Benefits management and Employee self service parameters for all companies



Before you can set up benefit plans in Microsoft Dynamics 365 Human Resources, you must configure Benefits management parameters. These parameters set default values, reason codes, and other options. 

## Configure general parameters

1. In the **Benefits management** workspace, under **Setup**, select **Human Resources Shared Parameters**.

2. In the **Benefits management** tab, specify values for the following fields:

   | Field | Description |
   | --- | --- |
   | **Country/region** | The **Country/region** field determines the display order of ZIP codes/states. The selected country/region displays first in the dropdown list. |
   | **Enrollment reason code** | Select a default reason code to use when employee plans are created during open enrollment processing. |
   | **Cancellation reason code** | The reason code to use when an employee benefit plan is canceled. It displays in a dialog during the cancellation process. Users can change it the **Cancellation reason code** if necessary. |
   | **Reopen reason code** | The reason code to use when an employee benefit plan is reopened. It displays in a dialog during the cancellation process. Users can change the **Reopen reason code** if necessary. | 
   | **Life event reason code** | The reason code to use when a life event occurs. |
   | **Rate change reason code** | The reason code to use when canceling and reopening an employee benefit plan during the rate change update process. It indicates which records were changed by the rate change update process. |
   | **Benefits annual salary** | Enables you to set a **Benefits annual salary** amount for an employee. Human Resources will use the **Benefits annual salary** amount when determining coverage amounts, instead of the fixed compensation annual amount. |
   | **New hire eligible** | Specifies whether new hires are eligible. |
   | **New hire enrollment period** | The period of time the new hire enrollment is allowed.</br></br>**Note**: This setting overrides any new hire enrollment period you set on the plan eligibility rule. |
   | **Default pay frequency** | The default pay frequency to use when new workers are added. |
   | **Life events enabled** | Enables life events. |
   | **Hide legacy benefit forms** | Allows you to hide legacy benefit forms. |
   | **Benefit verification** | The verification text to use during self-service benefits checkout. |
   | **Auto select designees** | Specifies whether to automatically select dependents and beneficiaries, based on their eligibility for plan options. |

3. Select **Save**.

## Configure Employee self service parameters

1. In the **Benefits management** workspace, under **Setup**, select **Human Resources Parameters**.

2. In the **Benefits management** tab, specify values for the following fields:

   | Field | Description |
   | --- | --- |
   | **Benefit verification** | The verification text to use during self service benefits checkout. |
   | **Auto select designees** | Specifies whether to automatically select dependents and beneficiaries based on their eligibility for plan options. |

3. Select **Save**.




[!INCLUDE[footer-include](../includes/footer-banner.md)]
