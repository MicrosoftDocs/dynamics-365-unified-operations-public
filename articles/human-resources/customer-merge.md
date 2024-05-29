---
# required metadata

title: Human Resources customer merge FAQ
description: This article answers frequently asked questions about the merge of Microsoft Dynamics 365 Human Resources to the finance and operations merged infrastructure.
author: Edison-MS
ms.date: 05/10/2024
ms.topic: article
# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 

ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: edilai
ms.search.validFrom: 2024-04-29
ms.dyn365.ops.version: Human Resources

---
# Human Resources customer merge FAQ

## What is customer merge?

Customer merge refers to the process that customers use to migrate their Human Resources (HR) environments from the standalone infrastructure to the finance and operations infrastructure as part of an infrastructure merge. Customers who have an existing finance and operations system can choose whether they want to maintain two separate environments or consolidate them into one system.

Customer merge involves the following elements:

- An optional step
- A customer-driven decision and timeline
- A manual process that the customer initiates
- Data integration with an existing finance and operations environment

## General questions about customer merge

### What is the recommendation from Microsoft?

The decision to proceed with customer merge post-migration is discretionary and lies with the customer and business stakeholders. No strict timeline is imposed for this process. Microsoft recommends that customers do a thorough assessment before they make a decision, and that they consider organizational objectives and weigh the pros and cons.

### Is there any cost benefit if we consolidate HR into finance and operations apps and operate them as a unified system?

Integration of HR functions into finance and operations apps can lead to streamlined processes and improved efficiency. For example, consider the integration between Microsoft Dynamics 365 Finance and HR systems that some customers currently maintain. After the merge, this integration can be eliminated to simplify management.

Here are some other benefits: 

- Easier control over Application Lifecycle Management (ALM)
- A single Microsoft Dynamics Lifecycle Services project
- Elimination of separate versioning and branches for different environments
- Reduced overhead in the management of updates and deployments for two separate systems
- Seamless data integration across platforms

### We have one sandbox in the HR project and two sandboxes in the Finance project. Will we end up with three sandboxes after customer merge?

No. In this scenario, you can have only two sandboxes at the conclusion of the single Lifecycle Services project. The sandbox from the HR environment can't be carried over to the Finance project.

### How can Microsoft support the customer merge process?

If you encounter any obstacles during customer merge, the best course of action is to initiate a support ticket to request help from Microsoft. Our support engineers will provide professional assistance for your issue.

### What tools does Microsoft offer for customer merge?

Microsoft offers extra data entities to facilitate customer merge. The Data Management Framework (DMF) serves as the primary standard tool for data migration. To initiate the process, identify and compile a list of applicable data entities. In cases where the out-of-box (OOB) data entities are inadequate, you might have to explore customized data entities.

### Can the application URL be modified after the merge?

No. The target environment's name and link remain unchanged unless you redeploy the instance.

### After the merge, what changes occur in the HR environment? Is it automatically deleted?

After customer merge is completed, you're responsible for deprovisioning both the sandbox and production environments from source environment, and the related Dataverse environment. For information, see [Delete a production finance and operations apps environment](../fin-ops-core/dev-itpro/deployment/delete-production-environment.md). You can proceed with the Lifecycle Services project.

### Do I have to reinstall the Expense mobile app after the merge to the Finance environment?

Yes. If the target environment lacks required mobile apps, such as the Dynamics 365 Expense Management app, you must install those apps in the merged environment after customer merge.

### Can I limit system administration access after a merge, so that only HR administrators can access HR data?

No. Individuals who have the System Administrator security role maintain unrestricted access to the whole system. There are no module-specific limitations.

### How should attachments for employee data be managed in a merged infrastructure to ensure data security, especially given the security protocols that were previously applied to separate infrastructures?

Security is paramount in this scenario. It's essential that you meticulously configure access roles, so that you grant permissions for employee-related forms only to necessary individuals. However, it's crucial to note that system administrators retain access to all data. If there are concerns about data security, a merge of infrastructures might not be advisable.

### How should we approach the merge of HR data into existing finance and operations data that already contains basic worker records? How do we handle the merge of workers and other elements, such as positions?

This consideration is key. If HR master data is already established, there's typically no need to duplicate efforts. However, it's crucial that you do a thorough analysis to determine which data sets must be merged and which incremental updates are necessary.

### What are the challenges and considerations during the customer merge process?

Several significant challenges and considerations emerge during the customer merge process. Here are some examples:

- Global Address Book (GAB)
- Number sequences
- Custom fields
- Security configuration
- Batch jobs/periodic tasks
- Custom code (X++ or addon)
- Personalization/saved views
- Integrations
- Extended solutions

We address and provide recommendations for these key challenges and considerations in [Dynamics 365 Human Resources Infrastructure Customer merge](https://community.dynamics.com/blogs/post/?postid=d9decee4-8b06-ef11-9f89-7c1e5216c747).
