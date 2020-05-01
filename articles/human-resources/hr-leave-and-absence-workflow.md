---
# required metadata

title: Create a leave request workflow
description: Create a Leave and absence request workflow to manage leave requests consistently in Dynamics 365 Human Resources.
author: andreabichsel
manager: AnnBe
ms.date: 02/03/2020
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

# Create a leave request workflow

You can create a workflow in Dynamics 365 Human Resources to consistently manage your leave and absence requests. A **Leave and absence** workflow lets you:

- Define tasks
- Determine who must complete the tasks
- Specify who can approve or reject requests

## Create a Leave and absence request workflow

1. On the **Leave and absence** page, select the **Links** tab.

2. Under **Setup**, select **Human resource workflows**.

3. Select **New**, and then select **Leave and absence request**. 

4. When the **Open this file?** message box appears, select **Open** and sign in with your company credentials.

5. Use the workflow editor to create a workflow for your leave requests. For more information about working with workflows, see [Create workflows overview](https://docs.microsoft.com/dynamics365/fin-ops-core/fin-ops/organization-administration/create-workflow?toc=/dynamics365/commerce/toc.json.)

## Leave and absence request workflow data elements
There are mulitple data elements that can be used to create conditional or automatic approvals in workflow for leave and absence requests. 

These data elements include:
- Comment
- Company
- Created by
- Created date and time
- End date
- Leave type
- Modified by
- Modified date and time 
- Reason code
- Request ID
- Start date
- Status 
- Submission date
- Submitted by
- Submitted by Human resources
- Submitted by Manager
- Submitted on behalf
- Worker
- Worker type

Here are some examples of different types of workflow conditions using the data elements above. 

1. Use **Reason code** in a [conditional statement] (https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/organization-administration/configure-conditional-decision-workflow)  to route sick leave requests with the reason code of surgery to HR for approval while all other reason codes go to the manager for approval
2. Use **Submitted by Human resources** and **Submitted by manager** in an [automatic action] (https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/organization-administration/configure-approval-process-workflow) to auto-approve leave requests submitted by these roles for employees
3. Use **Leave type** in a conditional statement or automatic action to control how requests with certain leave types are routed through workflow

## See also

- [Leave and absence overview](hr-leave-and-absence-overview.md)
