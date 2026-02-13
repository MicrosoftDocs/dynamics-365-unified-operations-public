---
title: What's new or changed in Dynamics AX platform update 2 (August 2016)
description: Learn about new or changed features in Microsoft Dynamics AX platform update 2. This version was released in August 2016.
author: johnmichalak
ms.author: johnmichalak
ms.topic: whats-new
ms.date: 10/31/2025
ms.update-cycle: 1095-days
ms.custom: 
  - bap-template
  - evergreen
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2016-08-30
ms.dyn365.ops.version: Platform update 2
ms.assetid: 7ab12871-d7b9-4bf8-9bde-1ab372db421a
ROBOTS: NOINDEX, NOFOLLOW
---

# What's new or changed in Dynamics AX platform update 2 (August 2016)

[!include [banner](../../../finance/includes/banner.md)]

This article describes features that are new or changed in Microsoft Dynamics AX platform update 2. This version was released in August 2016 and has a build number of 7.0.4230.16130.

## Deployment

| What can you do? | Why is this important? |
|------------------|------------------------|
| Enable Azure Resource Manager (ARM) deployments of Dynamics AX. | This feature is now in public preview. With Azure Resource Manager deployments, you can take advantage of the latest features of Azure. For more information, see [Complete the Azure Resource Manager (ARM) onboarding process](../deployment/arm-onboarding.md). |

## Development and customization

| What can you do? | Why is this important? |
|------------------|------------------------|
| Upgrade the Microsoft Dynamics AX platform to a new release without upgrading your application. | The Microsoft Dynamics AX platform is now compatible with previous versions of the Dynamics AX application, starting with the Microsoft Dynamics AX 7.0 (February 2016) version. Therefore, you can stay up to date with the latest improvements to the platform without having to upgrade your whole application. This feature is in preview mode and is available to those who don't overlay the platform models. |
| Extend your code and metadata (additional support). | Additional extensibility features let you do less customization (over-layering) of the standard Microsoft models.<br>• Extend a view.<br>• Add a new mapping to a table extension.<br>• Enable code-behind extension forms. For example, define a run-time class that is associated with an extension form where you write event handlers, write methods, and store a global state for your form extension.<br>• Provide an extension alternative to overrides of the **Lookup**, **LookupReference**, **ResolveReference**, and **jumpRef** methods.<br><br>Extensibility features are key features of the Dynamics AX platform because the **Application Platform** and **Test Essentials** models *can't be customized* (over-layered) in the August 2016 release. Also, if you customize elements in the **Application Foundation** model, you get warnings as this model is scheduled to be locked from customizations in the next Dynamics AX platform update. |

## Cloud operations

| What can you do? | Why is this important? |
|------------------|------------------------|
| Create replicas of production environment databases for testing. | You can submit a request to Microsoft to update your Tier-2 sandbox environment by using a copy of your database from your production environment. |
| Monitor the execution of Microsoft Azure SQL Database queries in real time. | You can troubleshoot SQL issues in real time by viewing the queries that are blocked and the queries that are blocking them. You can also view aggregated lock information for tables that currently have locks on them. |

## User interface

| What can you do? | Why is this important? |
|------------------|------------------------|
| Easily edit task recordings by rearranging steps or inserting new steps without playing back any existing steps. | Task recorder is improved through new tools on the **Edit** menu (currently titled **Change recording text**). The new tools let you change the order of steps in the recording. First select the step to move, and then select the location to move the step to. You can also insert new steps between existing steps. First select the location where you want to insert the new steps, and then just record the new steps. You don't have to play back any existing steps. |
| Extensible controls are guided away from nonpublic application programming interfaces (APIs). | To minimize future breaks in extensible controls, an effort is made to differentiate between the public and nonpublic JavaScript application programming interfaces (APIs) available to extensible controls. As part of this effort, documentation is now available [here](../user-interface/public-javascript-apis.md) for the public JavaScript APIs that extensible control authors can use. Additionally, extensible control authors should start ensuring their controls are only using public APIs, as starting with Platform Update 3 any nonpublic API might be removed or modified as needed. One planned modification for the nonpublic APIs is to prefix the names with underscores to clearly denote their access level. In this release, the only APIs that are undergoing this name change are those for which we have high confidence they aren't being used. |
| Use the updated Gantt control to develop interactive scheduling scenarios. | The updated Gantt control enables the development of new interactive scheduling scenarios and delivers enhanced APIs for customizing the appearance of activities. Here are some of the new APIs:<br>• Vertical drag-and-drop of activities<br>• Add/remove activities<br>• Preview booked periods in summary bar<br>• Change color and style of activity borders<br>• Change color, style, and background of text in grid |

## Microsoft Office integration

| What can you do? | Why is this important? |
|------------------|------------------------|
| View Skype contact cards by hovering over Skype presence indicators. | Skype contact cards are now shown when you hover over Skype presence indicators. This feature provides easy access to contact information and a contact image. |
| Design and generate Microsoft Word documents that have section-style tables. | Word document generation now supports section-style tables in addition to grid-style tables, to improve readability and provide more space. The Word template designer is also updated, so that section-style tables can now be added into templates. |
| Use screen readers together with the Office Add-ins. | Office Add-ins are now more accessible through full support for screen readers. |

## Analytics

| What can you do? | Why is this important? |
|------------------|------------------------|
| Export entities to customer-owned data warehouses. | The entity store that is provisioned with Dynamics AX is configured for integration with Microsoft Power BI and Microsoft Cortana Intelligence Suite. If you require integration with a third-party business intelligence (BI) tool or a preexisting data warehouse, you can now export data entities to your own SQL database. Data can be exported as a full push or as an incremental push. Therefore, this feature enables frequent updates. |
| Run the Document Routing Agent as a Windows service application. | The Document Routing Agent now offers an option to select the mode of execution. While running as a Windows service, the application can be automatically started when the computer boots and configured to run under the security context of a specific user account. This enhancement was added based on direct feedback from customers hosting the Document Routing Agent on shared resources like Network Print Servers. |
| Exported reports use the Yu Gothic font when the target language is Japanese. | Out-of-box reports, or reports that independent software vendors (ISVs) develop by using Dynamics AX tools, generate exported documents in the Yu Gothic font when the target language is Japanese. Previously, by default, reports used the Sego UI font, which doesn't support the full character set for all multibyte languages. Therefore, exported documents appeared malformed when the target language was Japanese. |
| Use controller extensions to establish default file names for exported and archived documents. | Developers can produce documents that have contextual names that they can use to associate those documents with transactional attributes (such as customer name or invoice number). Contextual names enable the creation of friendly names for exported and archived documents. |

## Security

| What can you do? | Why is this important? |
|------------------|------------------------|
| Enable business-to-business scenarios by using the Microsoft Entra Business to Business service. | You can invite external users to Dynamics AX by using an externally managed identity. External users no longer need to be part of an existing Microsoft Entra tenant. |
| Enable service-to-service authentication. | Registered services can connect to Dynamics AX without requiring a user to sign in. |

## Integrations

| What can you do? | Why is this important? |
|------------------|------------------------|
| Enable the export of incremental updates to a data entity. | The setup of recurring data projects now supports incremental updates. In other words, you can set up an export data project that periodically exports any changes to that entity. |

## Additional resources

[What's new or changed in Finance and Operations home page](../../fin-ops/get-started/whats-new-changed.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
