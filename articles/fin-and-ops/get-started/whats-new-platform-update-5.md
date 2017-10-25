---
# required metadata

title: What's new or changed in Dynamics 365 for Operations platform update 5 (March 2017)
description: This topic describes features that are either new or changed in Dynamics 365 for Operations platform update 5. This version was released in March 2017 and has a build number of 7.0.4475.16165.
author: tonyafehr
manager: AnnBe
ms.date: 04/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: Operations, Platform, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 273193
ms.assetid: 025acbbf-7c05-407c-bed2-cde1935e11c9
ms.search.region: Global
# ms.search.industry: 
ms.author: tfehr
ms.dyn365.ops.intro: Platform update 5
ms.search.validFrom: 2017-03-31

---

# What's new or changed in Dynamics 365 for Operations platform update 5 (March 2017)

[!include[banner](../includes/banner.md)]


This topic describes features that are either new or changed in Dynamics 365 for Operations platform update 5. This version was released in March 2017 and has a build number of 7.0.4475.16165.

Development and customization
-----------------------------

| **Feature**                                                 | **Why this is important**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|-------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| EventHandlerResult classes in request or response scenarios | You can now use the EventHandlerResult class for scenarios where the delegate (event) logic requires its subscribers (event handlers) to provide at least one response so that no result is lost when there are multiple subscribers and multiple results.                                                                                                                                                                                                                                                                                                                                                                  |
| Customization Analysis Report (CAR) justification          | When you suppress a best practice warning within a suppression file in the AxIgnoreDiagnosticList folder of your model, and include a justification, the justification text will appear in the CAR report of your model. For an example of a suppression file that includes justifications, see &lt;Packages Local Directory&gt;\\Directory\\Directory\\AxIgnoreDiagnosticList\\Directory\_BPSuppressions.xml.                                                                                                                                                                                                              |
| Telemetry                                                  | When a model is built, the telemetry framework collects information about Microsoft classes and methods that are referenced by customer and ISV code. This provides Microsoft with much needed information regarding what part of the standard application code is included in backward compatibility requirements.                                                                                                                                                                                                                                                                                                         |
| X++ compiler and try catch blocks                          | The X++ compiler now generates code that is slightly different for try catch blocks. Before, the system would catch the DuplicateKey and UpdateConflict exceptions as part of the catch all clause. This introduced some problems that could ultimately lead to data consistency problems if the try catch was used when a transaction is running. Now, the two exceptions mentioned, which are special because they do not roll back a running transaction, are no longer caught in the catch all. For more information, see the blog post [X++, the catch](https://blogs.msdn.microsoft.com/mfp/2016/11/24/x-the-catch/). |

## Personalization
| Feature                                              | **Why this is important**                                                                                                                                                                                                                                                                                                  |
|------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Enhanced administration features for personalization | The personalization administrator can now apply or remove form personalizations for groups of users. Previously personalization administration was only possible one user at a time. For more information, see [Personalize the user experience](personalize-user-experience.md). |






