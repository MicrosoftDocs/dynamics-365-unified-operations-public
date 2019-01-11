---
# required metadata

title: What's new or changed in Dynamics 365 for Talent Core HR (January 11, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 for Talent Core HR.
author: Darinkramer
manager: AnnBe
ms.date: 1/11/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2019-01-11
ms.dyn365.ops.version: Talent

---
# "What's new or changed in Dynamics 365 for Talent Core HR (January 11, 2019)"

[!include [banner](includes/banner.md)]

**Build 8.1.2100**

This topic describes features that are either new or changed in Core HR.

## Changes

### Validate leave requests by forecasting available balance
Changes made in this release allow employees to book future time without subtracting from current balance. Standard workflows will be used for any future requests made. 

### View forecasted leave balance in ESS and People
This feature enables viewing of balances for future leave periods by HR and employees. Employees can view future balances in Employee Self-Service and HR will have access to the same information through the People workspace.

### Notifications for changing leave balances
With these changes leave balances will display the employees current balance. Future balances are available via ESS and People workspaces by entering an “as of date” to calculate the forecasted balance.

Navigation has been added to view forecasted balances in the following areas:
	•Time off card on the ESS workspace
	•Leave and absence card on the MSS workspace
	•Leave and absence page on the People workspace

### Allow decimals for Variable Compensation plans (Cash Plans)
With these changes, variable cash awards and plans have the additional flexibility for amounts and overrides for values with decimal amounts.

### Unable to change the dates on Variable Comp Enrollments after the plan is saved
This change allows for the plans end date to be updated (extended/expired) once the plan has been saved. You can still activate or inactivate plans independent of start and end dates.

### Payroll information available when assigned the Payroll admin security role
The Payroll Administrator role has been updated to have access to the Payroll information during the request process.

### Employee self-service | Position Hierarchy drill-down from tile fails to get parent node
Changes have been made to allow to eliminate an error that occurred when adding the position hierarchy to new workspaces and navigating within the organizational structure.

### New validation message when personnel number sequence is in use
A change has been made to clarify what the issue is when you hire an employee and the next personnel number is in use.

### ESS Workspace selected as the initial startup page
When the ESS Workspace is selected as the Initial Startup Page for a user and that user is not assigned the employee role, the system will redirect to the default dashboard.

### Termination reason code updates position assignment record
With this change the termination reason code will update the position assignment when terminating an employee and ending the position. 


