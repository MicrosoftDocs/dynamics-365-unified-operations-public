---
# required metadata

title: Create an open-ended leave of absence
description: This article explains how to create an open-ended leave of absence in Microsoft Dynamics 365 Human Resources.
author: twheeloc
ms.date: 07/02/2024
ms.topic: article
# optional metadata

ms.search.form: LeavePlanFormPart, LeaveAbsenceWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anisagrawal
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Create an open-ended leave of absence


[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

You can submit requests for a leave of absence that is open-ended and view the status of your leave requests in Dynamics 365 Human Resources.

## Prerequisites

1. Under **Feature management**, confirm the **Open ended leave** feature is turned on.

    > [!IMPORTANT]
    > This feature can't be turned off after it has been turned on.

2. Create a leave of absence leave type.
3. Enter the details such as the leave type, description, and workflow ID.
4. In the **Request type** field, select **Leave of absence**.
5. In the details section, for open-ended leaves, set the **Open Ended** option to **Yes**.
6. Set the **Return to work notice** option to **Yes** or **No**.
7. A return-to-work notice can optionally be required for open-ended leave of absence requests.

> [!NOTE]
> After this feature is enabled, the **Attachment required** feature is enabled.

## Request an open-ended leave of absence

1. In the **Employee self-service** workspace, on the **Time off balances** tile, select **More (...)**.
2. To submit a leave of absence request, select **Request Leave of absence**.
3. Enter information in the **Leave type** and **Start date** fields. In the **End date** field, enter a tentative end date.
4. If you must submit supporting documentation, under **Attachments**, select **Upload**.
5. If you're ready to submit your request, select **Submit**. Otherwise, select **Save draft**.
6. To update an open-ended leave request, select the request, enter an end date in the **End date** field, set the **Confirm end date** option to **Yes**, and upload documentation.
7. If the **Return to work notice** option is set to **Yes**, select **Upload**, and then select the checkbox to confirm that a valid return-to-work notice has been uploaded.
8. When all the details have been entered, select **Submit**.
