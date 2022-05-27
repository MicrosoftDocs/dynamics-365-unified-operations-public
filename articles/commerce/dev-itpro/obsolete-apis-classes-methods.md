---

title: Obsolete and removed APIs, classes, and methods
description: This topic lists the obsolete and removed APIs, classes, and methods in Microsoft Dynamics 365 Commerce.
author: mugunthanm
ms.date: 05/27/2022
ms.topic: overview
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: mumani
ms.search.validFrom: 05-24-2022
ms.dyn365.ops.version: AX 10.0.25
---
# Obsolete and removed APIs, classes, and methods

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic lists the obsolete and removed APIs, classes, and methods in Microsoft Dynamics 365 Commerce.

Several APIs, classes, and methods have either been removed or marked as obsolete in Dynamics 365 Commerce. As Dynamics 365 Commerce changes over time, each new version adds new APIs, classes, and methods that provide new functionality. Existing APIs, classes, and methods also change over time. For example, some APIs become less important as the functionality they support is replaced by new functionality, and some methods are superseded by newer methods that are superior in some way or use different underlying technologies to provide better performance and reliability.

Dynamics 365 Commerce strives to support backward compatibility, which allows extensions that were developed with one version of Commerce to run on the next version of Commerce. However, backward compatibility makes it difficult to simply remove APIs, classes, or methods. Instead, Dynamics 365 Commerce indicates that an API, class, or method should no longer be used by marking it as obsolete or deprecated. Deprecating an API, class, or method entails marking it so that developers are aware that it will go away and have time to respond to its removal. The terms *obsolete* and *deprecated* have the same meaning when applied to .NET types and members.

## Obsolete attribute

In Dynamic 365 Commerce, an API, class, or method is made obsolete by marking it with the **Obsolete** attribute. Applying the attribute to an API, class, or method indicates that the API, class, or method will be removed in a future version of Dynamic 365 Commerce. 

## How to handle obsolete types and members

When you upgrade and recompile existing code, using an obsolete API, class, or method that generates a compiler warning in your extension is acceptable until the API, class or method is removed. However, you should review the compiler warning message to determine whether you should change your extension code. If the warning message doesn't point to a suitable alternative, you should do one of the following:

- If possible, change your code by removing the use of the API, class, or method.
- Review the documentation for this area to determine how to respond to the deprecation.

## Obsolete and removed APIs, classes, and methods for Hardware Station (HWS)

| Obsoleted and removed APIs, classes, and methods |Version made obsolete | Reason for change |Recommended action | Version the APIs, classes, and methods will be removed from source code| Sample code |
| ------ | ------ |------ |------- |------ |------ |
GenericWarningEvent |	10.0.14	| Extension must use Application insights to log events.	| 	Change your code by removing the use of the API, class, or method and then use your own Application Insights instance to log events.	| 	10.0.33	| [Log extension events to Application Insights](commerce-application-insights.md)	| 
GenericInformationEvent |	10.0.14	| Extension must use Application insights to log events.	| 	Change your code by removing the use of the API, class, or method and then use your own Application Insights instance to log events.	| 	10.0.33	| [Log extension events to Application Insights](commerce-application-insights.md)	|
GenericDebugEvent |	10.0.14	| Extension must use Application insights to log events.	| 	Change your code by removing the use of the API, class, or method and then use your own Application Insights instance to log events.	| 	10.0.33	| [Log extension events to Application Insights](commerce-application-insights.md)	|
ExtendedCriticalEvent |	10.0.14	| Extension must use Application insights to log events.	| 	Change your code by removing the use of the API, class, or method and then use your own Application Insights instance to log events.	| 	10.0.33	| [Log extension events to Application Insights](commerce-application-insights.md)	|
ExtendedErrorEvent |	10.0.14	| Extension must use Application insights to log events.	| 	Change your code by removing the use of the API, class, or method and then use your own Application Insights instance to log events.	| 	10.0.33	| [Log extension events to Application Insights](commerce-application-insights.md)	|
ExtendedWarningEvent |	10.0.14	| Extension must use Application insights to log events.	| 	Change your code by removing the use of the API, class, or method and then use your own Application Insights instance to log events.	| 	10.0.33	| [Log extension events to Application Insights](commerce-application-insights.md)	|
ExtendedInformationalEvent |	10.0.14	| Extension must use Application insights to log events.	| 	Change your code by removing the use of the API, class, or method and then use your own Application Insights instance to log events.	| 	10.0.33	| [Log extension events to Application Insights](commerce-application-insights.md)	|
ExtendedVerboseEvent |	10.0.14	| Extension must use Application insights to log events.	| 	Change your code by removing the use of the API, class, or method and then use your own Application Insights instance to log events.	| 	10.0.33	| [Log extension events to Application Insights](commerce-application-insights.md)	|
