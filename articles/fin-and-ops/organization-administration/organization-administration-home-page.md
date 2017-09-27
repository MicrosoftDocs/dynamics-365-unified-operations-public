---
# required metadata

title: Organization administration home page
description: This topic points to resources that will help you use Microsoft Dynamics 365 for Finance and Operations, Enterprise edition in your organization.
author: sericks007
manager: AnnBe
ms.date: 08/18/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 20421
ms.assetid: 7aa24a03-d172-47e9-81f8-ebd39e80bc60
ms.search.region: Global
# ms.search.industry: 
ms.author: sericks
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Organization administration home page

[!include[banner](../includes/banner.md)]


This topic points to content that will help power users and administrators configure Microsoft Dynamics 365 for Finance and Operations, Enterprise edition. This content will help them configure the system to work smoothly and effectively for your organization and business.

Much of the content listed here applies to features in the **Organizational administration** module. However, there are a couple of tasks, such as creating and using a record template, that can be performed in any module to help your organization run more efficiently. 

Number sequences
----------------
Number sequences are used to generate readable, unique identifiers for master data records and transaction records that require identifiers. A master data record or transaction record that requires an identifier is referred to as a *reference*. Before you can create new records for a reference, you must set up a number sequence and associate it with the reference.

-   [Number sequence overview](number-sequence-overview.md)
-   [Set up number sequences by using a wizard](tasks/set-up-number-sequences-wizard.md) (Task guide)
-   [Set up number sequences on an individual basis](tasks/set-up-number-sequences-individual-basis.md) (Task guide)

## Organizations
An organization is a group of people who are working together to carry out a business process or achieve a goal. Organizational hierarchies represent the relationships between the organizations that make up your business.

Before you set up organizations and organization hierarchies in Finance and Operations, make sure that you plan how your business will be modeled. The organization model has a significant effect on the implementation of Finance and Operations and on business processes.

-   [Organizations and organizational hierarchies](organizations-organizational-hierarchies.md)
-   [Plan your organizational hierarchy](plan-organizational-hierarchy.md)
-   [Create an organization hierarchy](tasks/create-organization-hierarchy.md) (Task guide)
-   [Create a legal entity](tasks/create-legal-entity.md) (Task guide)
-   [Create an operating unit](tasks/create-operating-unit.md) (Task guide)

## Address books
The global address book is a centralized repository for master data that must be stored for all internal and external persons and organizations that the company interacts with. The data that is associated with party records includes the party's name, address, and contact information. 

After you create the global address book, you can create additional address books as you require, such as a separate address book for each company in your organization or for each line of business. 

-   [Global address book](overview-global-address-book.md)
-   [Plan how to configure the global address book and additional address books](plan-configuration-global-address-book-additional-address-books.md)
- [Configure the global address book](tasks/configure-global-address-book.md)
-   [Address books FAQ](qa-address-books.md)


## Workflow
Workflow is a system that is installed with Finance and Operations that you can use to create individual workflows, or business processes. When you create a workflow, you specify how a document flows, or moves, through the system by showing who must complete a task, make a decision, or approve a document. 

-   [Workflow overview](overview-workflow-system.md)
-   [Workflow elements](workflow-elements.md)
-   [Workflow actions](workflow-actions.md)
-   [Create a workflow](create-workflow.md)

## Electronic signatures
An electronic signature confirms the identity of a person who is about to start or approve a computing process. In some industries, an electronic signature is as legally binding as a handwritten signature. Electronic signatures are a regulations compliance requirement for several regulated industries, such as pharmaceuticals, food and beverage, and aerospace and defense.

In Finance and Operations, you can use electronic signatures for critical business processes. Some processes have built-in electronic signature capabilities. You can also create custom signature requirements for any database table and field.

-   [Electronic signature overview](electronic-signature-overview.md)
-   [Set up electronic signatures](tasks/set-up-electronic-signatures.md) (Task guide)

## Case management
By planning, tracking, and analyzing cases, you can develop efficient resolutions that can be used for similar issues. For example, when customer service representatives or Human Resources generalists create cases, they can find information in knowledge articles to help them work with or resolve a case more efficiently. 

-   [Case management overview](cases.md)
-   [Configure case security, processes, and categories](plan-case-management.md)

## Record templates
Record templates can help you to create records more quickly. You can create a record template so that field values that are used often do not have to be entered explicitly for each new record. 

-   [Record templates](record-templates.md)
- [Create a record template to facilitate data entry](../../dev-itpro/data-entities/tasks/create-record-template-facilitate-data-entry.md) (Task guide)
- [Use a record template to create a new record](../../dev-itpro/data-entities/tasks/use-record-template-new-record.md) (Task guide)

## General organization administration
-   [Change the banner or logo](../get-started/tasks/change-banner-or-logo.md) (Task guide)
- [Configure document management](configure-document-management.md)
- [Configure and send email](configure-email.md)
-   [Date/time data and time zones](date-time-zones.md)







