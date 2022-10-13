---
# required metadata

title: Audit synchronization of customer operations in headquarters
description: This article explains how to audit synchronization of customer operations in Microsoft Dynamics 365 Commerce headquarters to help resolve any site user issues.
author: gvrmohanreddy
ms.date: 10/13/2022
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

This article explains how to audit synchronization of customer operations in Microsoft Dynamics 365 Commerce headquarters to help resolve any site user issues.

As organizations start adopting the ability to create and edit customers asynchronously, site administrators need a way to view and troubleshoot operations based on site user requests or process failures. In those scenarios, site administrators should be able audit customer creation and edit operations and fix any failures using a self-serve model. 

## Customer synchronization status

When you opt in for the asynchronous mode of customer management and its corresponding features, Commerce headquarters administrators must create and schedule a recurring batch job for the **P-job**, the **Synchronize customers and business partners from async mode** job, and the **1010** job so that any async customers are converted to sync customers in Commerce headquarters. Synchronization of customer management operations occurs whenever these jobs are run. For more information, see [Asynchronous customer creation mode](async-customer-mode.md).

As a business owner, you have the ability to do the following operations:

- View all create/edit operations of site users. Details include status and time stamp.   
- Filter operations using any of the customer table fields and values to narrow down the audit log. 
- View brief descriptions of changes along with the status details to understand operations at a high level.   
- For failures, edit and fix problematic fields, and then save and synchronize specific customer operations. 

### Customer synchronization status page elements 

To view a list of all synchronization operations, in headquarters go to **Commerce and Retail \> Customers \> Customer synchronization status**. The following illustration shows an example of the **Customer synchronization status** page.

![Customer synchronization status page in headquarters](media/D365-Commerce-Customer-Mgmt-Audi-Async-Operations.png)

The customer synchronization operations list on the left side of the **Customer synchronization status** page displays the following columns by default: 

- **Channel name**
- **Customer account**
- **Async customer account**
- **Operations timestamp**
- **Customer sync status**

The top right side of the **Customer synchronization status** page displays customer account details such as **Customer account**, **Retail async operation**, **Customer sync status**, and **Last known error**.

The **Change description** section contains a description of the type of customer management operation that ran (for example, customer creation, account update, or synchronization failure with detail).

The **Customer attributes** section displays a table of all customer attributes, with columns for old and new values. You can edit this section if you want to change your customer attribute values to fix bugs, and then synchronize again.


