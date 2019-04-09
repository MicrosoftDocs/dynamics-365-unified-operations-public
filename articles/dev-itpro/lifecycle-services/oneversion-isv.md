---
# required metadata

title: Delivering ISV Solutions for Dynamics 365 Finance and Operations using One Version
description: 
author: frandahl
manager: AnnBe
ms.date: 03/15/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: robinarh
ms.search.validFrom: 2019-3-31 
ms.dyn365.ops.version: Platform update 24 

---

# Delivering ISV Solutions for Dynamics 365 Finance and Operations using One Version

[!include [banner](../includes/banner.md)]

We have entered the era of Dynamics 365 Finance and Operations One Version. We now truly run a service with all the benefits that come with this. New updates are automatically broadcast with close to zero downtime, and customers enjoy the benefits of staying current with recent features and fixes without having to go through expensive upgrades. Feature management allows customers to control when new features are applied.

This means that you as partner can innovate together with Microsoft to take advantage of new features without the waiting times that come with long release cycles. When your customers all run on current versions, you have fewer versions to maintain. You can instead focus on building quality into the solutions you bring to your customers.

Servicing current versions is more seamless and safer compared to earlier versions where patching required us to pull together individual fixes and merge them into a customer environment.

Quality is a cornerstone of One Version. Extensibility enables deployment of side-by-side solutions that provide customers more more choices in configuring their solutions.

Under One Version, customer UAT and production environments are updated every month. It is critical we take every step to ensure that updates are done without causing issues. We acknowledge both technical and functional issues may come from updating environments.

+ Technical issues include breaking changes in APIs that are used by customizations in your solutions.
+ Functional issues seen from customers can be due to the untimely introduction of new features. Microsoft will put under feature management any new functionality that may impact existing processes. This lets customers control when new functionality is put into use, leaving time for them to validate, document, and train their users on the new features.
+ Functional issues might also be unintended changes that cause functional regressions.

Preventing technical or functional issues is a difficult proposition and requires a close coordination between Microsoft and you as an ISV partner. Our strategy is that you get to adapt similar practices as we do at Microsoft. Over the next several months we will roll out new practices and tools to help empower you in this. We will update this guidance the tools and practices evolve.

How we do this together is covered in these paragraphs.
+	[Servicing customers](#servicing-customers)
+	[Compatibility](#compatibility)
    - [Runtime compatibility](#runtime-compatibility)
    - [Design time compatibility](#design-time-compatibility)
+	[Developing new releases](developing-new-releases)
    - [Design for Extensibility](design-for-extensibility)
    - [Data Upgrade](data-upgrade)
    - [Feature exposure](feature-exposure)
+	[Branches and builds]()
+	[Testing]()
+	[Deploying updates]()
+	[ISV solutions as part of One Version automated deployment?]()
+	[Do I ship binaries or source code?]()

## Servicing customers

With Dynamics 365 for Finance and Operations on Azure we are running a solution as a service. We service companies 24/7 either proactively from alerts that report abnormal behavior or by request tickets raised by our customers in companies or by their partners. We have a range of tools available that help to support the running services, including usage data that is collected from the services. Much diligence goes around who can access customer systems to safeguard customer data.

When we analyze an issue, we may determine that it is related to your ISV solution. We report such issues to you so that you can follow up offline.

Companies can opt-out of updates for two consecutive service updates before the next service update is applied into their environments. This means we can expect to see companies running on one of the last 3 monthly updates at any time.

When we resolve and issue that requires a code fix, we generally it in the next monthly update. Highly critical reported issues like production outage may however mean a fix is provided for the version the customer is running.

Similar policies apply to your ISV solution, and you might also need provide a code update. For your solution to be binary compatible with all your customers, it needs to be built on the oldest platform release you want to support. New updates from Microsoft promise backward binary compatibility. This compatibility gives you the option of maintaining only one servicing version of your solution that is based on the oldest of the 3 recent updates. This lets you maintain only one released solution, and you can use that solution to update all of your customers customers regardless of which of the most recent 3 updates they are running. As your customers adopt new Microsoft updates, you can choose to rebase your maintained solution to a newer release to keep current with the most recent 3 updates. 

This recommendation applies to servicing and maintaining your released solution. You will use a different approach for development of new releases of your solution. More information is available in the following sections of this document.

## Compatibility

We are diligent in ensuring compatibility with existing customizations. We achieve this by using strict practices in our engineering processes, along with tool and automation support that helps identify API contracts that are unintentionally broken. Telemetry allows our engineers to determine customizations that reference or extend a Microsoft API.

We are making a promise that Microsoft Finance and Operations updates that are applied to customer environments are functionally and binary compatible with existing customizations. The backward compatibility promise does not cover only APIs, it also includes functionality and user experience. All new experiences will be opt-in.

Any deprecation or breaking change in binary or functional compatibility will be announced 12 months in advance to provide ample time for you to align your customizations with an alternative design. You must pay attention to our monthly documentation updates and review the APIs that are marked as obsolete or internal. This allows you to manage changes in a timely fashion.

The following sections defines and describes the aspects of backward compatibility: runtime and design.

### Runtime compatibility

We promise that new updates are runtime backward compatible. This promise covers binary and functional compatibility. Runtime compatibility means customizations that exist on production and sandbox environments will continue to work after a new Finance and Operations update is deployed on the environment. This includes both standard platform and application updates.

This also means that changes to the platform including changes to the compiler will be backward compatible with customizations that were compiled on an earlier platform.

The compatibility is only backwards. It is not possible to compile a customization on a newer platform and deploy this onto a customer environment that has not yet updated to that or a later version.

### Design-time compatibility

Design time backward compatibility means that a developer can apply a Finance and Operation update to their development environment and can successfully compile their code without making any changes.

You must be aware of how APIs in your solution are used in your customers’ implementations, and how you use these API’s without causing breaking changes. This work includes being diligent about what is changed and relying on engineering best practices. Examples of what you should avoid are discussed in [Breaking changes](breaking-changes.md).

You should strive to meet a bar to Microsoft's bar, so that together we avoid creating regressions.

We promise binary compatibility and we also aim for design-time compatibility. However, there is a category of necessary changes that are **not** design time compatible but remain binary compatible. After applying an update, compiling your code may result in new errors or warnings. Some examples are that we make an enumeration extensible, we mark an API as obsolete or internal, or we introduce a new compiler error to avoid unsafe coding practices. These changes might require work on your solution. Design-time breaking changes that are binary compatible do not require a 12-month deprecation notice.

## Developing new releases

One Version together with running the solution as a service provides a great vehicle for collecting feedback. Feedback is useful for choosing which new features should be added to upcoming updates. Historically, we are used to new major releases with many new features, but the new model invites us to rethink this. We have moved to a series of continuous updates, where we gradually build on available capabilities of the system. In many cases one update will contain an initial small feature that we enrich with upcoming updates. There are instances where we need to stage for new features and initially hide or control adaption of new features by use of feature exposure.

We recommend that you follow a similar approach for your ISV solutions. You will benefit from quicker integration and extension of new standard features.

The frequency of your new releases can be independent from Microsoft’s, as shown in the following diagram. Consider a source code branching strategy as described later in this document.

![Branching stategy](./media/oneversion-isv-branch.png)

What is essential is releasing with quality with every update. Testing helps assure quality is there, but quality needs to be built in during the design and implementation phases too. There are some new dimensions to consider under One Version.

### Design for Extensibility

Designing your solution for extensibility means considering both how you customize by extending the standard application and how you enable customization of your ISV solutions by your customers and partners.

Ensure customizations are additive as opposed to intrusive, and follow the guidance found on the [extensibility home page]().

Do not become too creative in building your customization if you end up extending an API that is questionable. This leads to risk that later updates will break your solution. Instead, log an [extensibility request](./extensibility/extensibility-requests.md) for us to create a more explicit API that is more resilient to breakage.

Design solutions that are extensible. Take inspiration from [Write extensible code](./extensibility/writing-extensible-code.md).

Design for backward compatibility to avoid breaking any customer implementation. A good strategy is to be explicit about what you offer for hooking and wrapping extension code. You have great control over what methods you enable extensions for by how you decorate your methods. For more information, read [Attributes that make method extensible](./extensibility/extensibility-attributes.md).

### Data Upgrade

There is no longer support for data upgrade jobs like those that existed with earlier versions of Finance and Operations. This is because we want to provide minimum downtime while updating a production environment.

The database synchronization is still executes during upgrade and supports basics like adding new tables, field, and indexes.

We are introducing new ways of driving data upgrade that execute asynchronously to prevent downtime. This is quite a different paradigm. Data upgrade will at times be triggered when a feature is enabled by a feature flag. This new approach for data upgrade will materialize with upcoming updates, and documentation resources will be available.

### Feature exposure

With One Version, updates are managed by Microsoft and pushed onto customer environments. Pushed updates should not require customers to adjust to functional changes and train their users on a monthly basis because of new or changed features. This should not cause the customer to delay updates to their environment.

Feature management is a new concept that empowers customers to decide when new or changed features are put into effect. This allows customers to review, validate, and document new or changed features before they are adopted. This also allows for training of users before enabling new or changed processes to reduce impact on daily operations. This puts the customer in control.

Feature management will be released in the upcoming monthly updates.

You should consider using feature management with your ISV solution to provide customers control on when new features are put into effect.



