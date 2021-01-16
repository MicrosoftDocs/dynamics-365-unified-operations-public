---
# required metadata
title: Configure Benefits management parameters per company
description: Configure parameters for Benefits management per company in Microsoft Dynamics 365 Human Resources.
author: andreabichsel
manager: tfehr
ms.date: 12/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-human-resources
ms.technology: 
# optional metadata
ms.search.form: BenefitWorkspace, HcmBenefitSummaryPart
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2020-12-07
ms.dyn365.ops.version: Human Resources
---

# Configure Benefits management parameters per company

For each organization that offers benefits, you must configure settings for benefits confirmation emails.

## Configure confirmation email settings

1. In the **Benefits management** workspace, under **Setup**, select **Human Resources Parameters**.

2. In the **Benefits management** tab, specify values for the following fields: 

   | Field | Description |
   | --- | --- |
   | **Send confirmation email** | When this feature is on, a confirmation email will be sent to employees when they check out from the benefits enrollment experience in Employee self-service. |
   | **Confirmation email template** | Select the organization email template to use when sending the enrollment confirmation. If you don't select a template, the following generic email will be sent:<br><br>%EmployeeFirstName%,<br><br>Congratulations! You’ve successfully completed benefits enrollment.<br><br>Thank you,<br><Company/Org name> Benefits. |
   | **Default email sender address** | The email address to use when sending the confirmation email. |

3. Select **Save**.