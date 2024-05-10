---
# required metadata

title: Human Resources customer merges FAQ
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
# Human Resources customer merges FAQ

## What is customer merge?

Customer merge refers to the process wherein customers migrate their Human Resources environments from standalone infrastructure to the Finance and operations infrastructure as part of an infrastructure merge. If customers already have an existing Finance and operations system, customers have the flexibility to choose between maintaining two separate environments or consolidating them into one system.
 
Customer merge entails the following:
- An optional step
- Customer-driven decision and timeline
- Manual process initiated by the customer
- Data integration with existing finance and operations environment

### General questions about customer merge

### What is the recommendation from Microsoft?
The decision to proceed with customer merge post-migration is discretionary and lies with the customer and business stakeholders. There is no strict timeline imposed for this process. Microsoft advises customers to conduct a thorough assessment, considering organizational objectives and weighing the pros and cons before making a decision.
  
### Would there be any cost benefit if we consolidate HR into F&O and operate as a unified system?
Integrating HR functions into F&O operations can lead to streamlined processes and improved efficiency, such as streamlined processes and enhanced efficiency. By way of example, consider the integration between Finance and HR systems that some customers currently maintain. Following the merge, this integration could be eliminated, simplifying management. Additionally, benefits include easier control over Application Lifecycle Management, a single LCS project, elimination of separate versioning and branches for different environments, reduced overhead in managing updates and deployments for two separate systems, and seamless data integration across platforms.
 
### We have one Sandbox in the HR project and two Sandboxes in Finance project. Will we end up with three Sandboxes in total after customer merge?
No, in this scenario, you can only have two Sandboxes at the conclusion of the single LCS project. The Sandbox from the HR environment can not be carried over to the Finance project.

### How can Microsoft support the customer merge process?
If you face any obstacles while merging customers, the best course of action is to initiate a support ticket to request assistance from Microsoft. Our support engineers will provide professional assistance for your problem.

### What tool does Microsoft offer for customer merge?
Microsoft offers extra Data entities to facilitate customer merging, with the Data Management Framework (DMF) serving as the primary standard tool for data migration. To initiate the process, identify and compile a list of applicable data entities. In cases where the out-of-the-box (OOB) Data entities are inadequate, customized Data entities may need to be explored.

### Can the application URL be modified after merging?
No, the target environment's name and link remain unchanged unless you redeploy the instance.

### After the merge, what changes occur in the HR environment? Is it automatically deleted?
Upon completing the customer merge, it's your responsibility to deprovision both the Sandbox and Production environments from source environment, and the related Dataverse environment. Refer to [Delete a production finance and operations apps environment](../fin-ops-core/dev-itpro/deployment/delete-production-environment.md), you can proceed it with the LCS project.

### Should I need to reinstall the Expense mobile app after merging into Finance environment?
Yes, if the target environment lacks the relevant mobile apps, such as the Dynamics 365 Expense Management app, it's necessary to install all required apps in the merged environment after the customer merge.
 
### Can I limit system administration access after merging, such that only HR administrators can access HR data?
No, individuals with the System Administrator security role maintain unrestricted access to the entire system, without module-specific limitations.

### How should attachments for employee data be managed in a merged infrastructure while ensuring data security, especially considering the security protocols previously applied to separate infrastructures?
Security is paramount in this scenario. It's essential to configure access roles meticulously, granting permissions only to necessary individuals for employee-related forms. However, it's crucial to note that system administrators retain access to all data. If there are concerns regarding data security, merging infrastructures may not be advisable.

### How should we approach merging HR data into existing FinOps data that already contains basic worker records? How do we handle merging workers and other elements like positions?
This is a key consideration. If HR master data is already established, there's typically no need to duplicate efforts. However, a thorough analysis is crucial to determine which data sets need to merge and any incremental updates that may be necessary.

### What are challenges and considerations during the customer merge process?
Several significant challenges and considerations emerge during the customer merge process, including:
- Global Address Book (GAB)
- Number Sequence
- Custom Field
- Security Configuration
- Batch Jobs/Periodic Tasks
- Custom Code (X++ or addon)
- Personalization/Saved Views
- Integrations
- Extended solutions

We addressed and provided recommendations for these key challenges and considerations in [Dynamics 365 Human Resources Infrastructure Customer merge](https://community.dynamics.com/blogs/post/?postid=d9decee4-8b06-ef11-9f89-7c1e5216c747).


