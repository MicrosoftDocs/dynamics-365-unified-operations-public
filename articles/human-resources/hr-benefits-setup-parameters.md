---
# required metadata

title: Set Benefits management parameters
description: Configure parameters for Benefits management in Microsoft Dynamics 365 Human Resources.
author: andreabichsel
manager: AnnBe
ms.date: 04/01/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-human-resources
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Set Benefits management parameters

Before you can set up leave plans in Microsoft Dynamics 365 Human Resources, you must configure Benefits management parameters. These parameters set default values, reason codes, and other options.

## Configure general parameters

1. In the **Benefits management** workspace, under **Setup**, select **Parameters**.

2. In the **General** tab, specify values for the following fields:

   | Field | Description |
   | --- | --- |
   | **Country/region** | The **Country/region** field determines the display order of ZIP codes/states. The selected country displays first in the dropdown list. |
   | **Enrollment reason code** | Select a default reason code to use when employee plans are created during open enrollment processing. |
   | **Cancellation reason code** | The reason code to use when an employee benefit plan is canceled. It displays in a dialog during the cancellation process. Users can change it the **Cancellation reason code** if necessary. |
   | **Reopen reason code** | The reason code to use when an employee benefit plan is reopened. It displays in a dialog during the cancellation process. Users can change the **Reopen reason code** if necessary. | 
   | **Life event reason code** | The reason code to use when a life event occurs. |
   | **Rate change reason code** | The reason code to use when canceling and reopening an employee benefit plan during the rate change update process. It indicates which records were changed by the rate change update process. |
   | **New hire eligible** | Specifies whether new hires are eligible. |
   | **New hire enrollment period** | The period of time the new hire enrollment is allowed.</br></br>**Note**: This setting overrides any new hire enrollment period you set on the plan eligibility rule. | 
   | **Life events enabled** | Enables life events. |
   | **Hide legacy benefit forms** | Allows you to hide legacy benefit forms. |

3. Select **Save**.

## Configure Employee self service parameters

1. In the **Benefits management** workspace, under **Setup**, select **Parameters**.

2. In the **Employee self service** tab, specify values for the following fields:

   | Field | Description |
   | --- | --- |
   | **Benefit verification** | The verification text to use during self-service benefits checkout. |
   | **Auto select designees** | Specifies whether to automatically select dependents and beneficiaries based on their eligibility for plan options. |

3. Select **Save**.
