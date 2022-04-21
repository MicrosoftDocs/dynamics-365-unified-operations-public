---
# required metadata

title: Configure leave and absence parameters
description: This topic describe how to define human resources parameters for leave and absence in Dynamics 365 Human Resources.
author: twheeloc
ms.date: 10/28/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LeavePlanFormPart, LeaveAbsenceWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Configure leave and absence parameters

>[!Important]
>The functionality noted in this topic is currently available for customers on the stand-alone Dynamics 365 Human Resources. Some or all of the functionality will be available as part of a future release on the Finance infrastructure after Finance release 10.0.26.


[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

Before you set up leave and absence plans in Dynamics 365 Human Resources, it's a good idea to verify the settings for all related **Human resources parameters**, including:

- Number sequence for leave requests
- Family Medical and Leave Act (FMLA) settings
- Employee self service settings for leave and absence requests
- Leave and absence parameters

## View and change human resources parameters

1. On the **Leave and absence** page, select the **Links** tab.

2. Under **Setup**, select **Human resources parameters**.

3. On the **Number sequences** tab, verify the **Number sequence code** for **Leave request ID** and change as necessary. This setting determines the sequence used for automatically assigning IDs to leave requests.

4. On the **FMLA** tab, verify the FMLA settings and change as necessary.

5. On the **Employee self service** tab, indicate whether managers can enter leave and absence requests on behalf of their employees.

7. Select **Save**.

>[!IMPORTANT]
>Viewing leave and absence across companies is currently in preview. You'll need to enable it in your **Sandbox** environment to display the option for leave and absence. For more information about enabling preview features, see [Manage features](hr-admin-manage-features.md).

## View and change Human resources shared parameters

1. On the **Personnel management** page, select the **Links** tab.

2. Under **Setup**, select **Human resources shared parameters**.

3. On the **Advance access** tab, select **Yes** for **Enable cross company leave view** to allow leave to be viewed across company.

4. Select **Save**.

## View and change leave and absence parameters

1. On the **Leave and absence** page, select the **Links** tab.

2. Under **Setup**, select **Leave and absence parameters**.

3. On the **General** tab, set the following parameters:
 
    - Set **Unit for leave and absence** to either hours or days. If days, you can select **Enable half day definition** to allow employees to choose either first or second half of day in their time-off requests. 

    - Select **Months of service effective date** to set when the accrual rates take effect for leave plans using months of service.

    - Select **Balance calculation** to display balances as of today or as of the accrual period. If you select **Balance as of today**, the balance displays the total of all accruals, adjustments, and requests as of today. If you select **Balance as of accrual period**, the balance displays the total of all accruals, adjustments, and requests as of the accrual period defined by the frequency in the leave plan. 

    - Set the **Start time** for the **Carry forward expiration** batch job.  
    
    - Select **Yes** for **Allow employees to buy leave** and **Allow employees to sell leave**. If you select **Yes** for these options, you can create buy and sell leave policies and enable employees to submit buy and sell leave requests.

## Configure calendar parameters

1. On the **Leave and absence** page, select the **Links** tab.

2. Under **Setup**, select **Leave and absence parameters**.

3. On the **Calendar** tab, change calendar settings as necessary.

4. Select **Save**.

## See also

- [Leave and absence overview](hr-leave-and-absence-overview.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
