---
# required metadata

title: Audit synchronization of customer operations in headquarters
description: This article explains how to audit synchronization of customer operations in Microsoft Dynamics 365 Commercen headquarters to help resolve any site user issues.
author: gvrmohanreddy
ms.date: 10/12/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: gmohanv
ms.search.validFrom: 2022-09-28

---
# Audit synchronization of customer operations in headquarters

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This article explains how to audit synchronization of customer operations in Microsoft Dynamics 365 Commercen headquarters to help resolve any site user issues.

As organizations start adopting create customer asynchronously and edit customers asynchronously, businesses want a way to view all the operations and troubleshoot any operations based on end user requests or process failures. In those scenarios C1 should be able audit customer creation/edit operations and fix any failures in a self-serve model. 

## Customer synchronization status

When you opt-in for asynchronous mode of customer management and its corresponding features, refer to [Asynchronous customer creation mode](async-customer-mode.md) and schedule a recurring batch job for the P-job, the Synchronize customers and business partners from async mode job, and the 1010 job, synchronization of customer management operations happen.

To view a list of all synchronization operations, go to **Commerce & Retail \> Customers** under the **Customer synchronization status** section.  

As a business owner, you can do the following operations:

- Ability to view all create/edit operations of C2’s, status along with time stamp.   
- Ability to filter operations using any of the Cust table fields and values to narrow down the audit log. 
- View a brief description of the change along with the status to understand the operation at high-level.   
- For any failures, ability to edit and fix the problematic fields and save and synchronize specific customer operation. 
	
Customer synchronization operations list will the following columns showing by default. 

- Channel name
- Customer account
- Async customer account
- Operations timestamp
- Customer sync status

Customer synchronization status page will have the following sections

| Section| Description  | 
| ------------- |:--------------:|
| General | Customer account details  |
| Change description | Type of customer management operation (for example, customer creation, update to an account, or failure of synchronization with detail). |
| Customer attributes | Section that shows table of all customer attributes name, old and new values. This is the section you can edit if you want to change your customer attribute values to fix and then synchronize again.  | 

 ![Dynamics 365 Commerce Headquarters - Customer synchronization status report](media/D365-Commerce-Customer-Mgmt-Audi-Async-Operations.png)
