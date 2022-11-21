---
# required metadata

title: Create an open ended leave of absence 
description: Create an open ended leave of absence in Dynamics 365 Human Resources.
author: twheeloc
ms.date: 11/21/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LeavePlanFormPart, LeaveAbsenceWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Create an open ended leave of absence 

> [!Important]
> The functionality noted in this article will be available as part of a future release on the Finance infrastructure after Finance release 10.0.31.

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

You can submit requests for leave of absence that is open ended and see the status of your leave requests in Dynamics 365 Human Resources.

## Request an open-ended leave of absence prerequisites

1.	Under **Feature management**, the **Open ended leave** feature is turned on.

>[!Note] 
> This feature can't be turned off after it has been turned on.


2.	Create a leave of absence leave type.
3.	Enter the details like **Leave type**, **Description**, **Workflow ID**. 
4.	In the **Request type** field, select **Leave of absence**.
5.	In the details section, for open ended leaves set the **Open ended** option to **Yes**. 
6.	Set the **Return to work notice** as **Yes** or **No**. 
7.	The **Return to work notice** can be optionally required for open end leave of absence leave requests.

>[!Note] 
>After this feature is enabled, the **Attachment required** feature will be enabled.

## Request an open-ended leave of absence

1.	In the **Employee self-service** workspace, select **More (...)** in the **Time off balances** tile.
2.	To submit a leave of absence request, select **Request Leave of absence**.
3.	Enter information for **Leave type**, **Start date** and a tentative **End date**.
4.	If you need to submit any supporting documentation, select **Upload** under **Attachments**.
5.	Select **Submit** if you're ready to submit your request. Otherwise, select **Save draft**.
6.	To update an open ended leave: Select the leave to be updated, enter the **End date**, set **Confirm end date** to **Yes** and upload documentation.
7.	If the **Return to work notice** is set to **Yes**, click **Upload** and select the checkbox to confirm that a valid return to work notice is uploaded.
8.	Select **Submit** when all the details are entered. 
 

