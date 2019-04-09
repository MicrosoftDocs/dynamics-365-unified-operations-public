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
+	[Compatibility]()
    - [Runtime compatibility]()
    - [Design time compatibility]()
+	[Developing new releases]()
    - [Design for Extensibility]()
    - [Data Upgrade]()
    - [Feature exposure]()
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

