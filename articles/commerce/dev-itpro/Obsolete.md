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

Several APIs, Classes, and Methods have been either removed or marked as obsolete in Dynamics 365 Commerce. Dynamics 365 Commerce changes over time, each new version adds new APIs and Classes, and Methods that provide new functionality. Existing APIs and Classes, and Methods also change over time. For example, some APIs become less important as the functionality they support is replaced by a new functionality, and some methods are superseded by newer methods that are superior in some way or the underlying technologies changed to provide better performance, reliability etc.
Dynamics 365 Commerce strives to support backward compatibility (allowing extensions that were developed with one version of Dynamics 365 Commerce to run on the next version of Dynamics 365 Commerce). This makes it difficult to simply remove APIs, Classes, or Methods. Instead, Dynamics 365 Commerce indicates that an API, Class, or a Method should no longer be used by marking it as obsolete or deprecated. Deprecating an API, Class or a method involves marking it so that developers are aware it will go away and have time to respond to its removal. The terms obsolete and deprecated have the same meaning when applied to .NET types and members.

## Obsolete Attribute

In Dynamic 365 Commerce an API, Class or Method is made obsolete by marking it with the Obsolete attribute. Applying the attribute to an API, Class or Method indicates that API, Class, or Method will be removed in some future version of the Dynamic 365 Commerce. 

## How to handle obsolete types and members

When you upgrade and recompile existing code, using an obsolete API, Class, or Method that produces a compiler warning in your extension is perfectly acceptable till the API, Class or Method is removed. However, you should review the compiler warning message to determine whether you should change your extension code. If the message does not point to a suitable alternative, you should do either of the following:
- Change your code by removing the use of the API, Class, or Method, if possible.
            -or-
-   Review the documentation for this area to determine how to respond to the deprecation.

## Obsolete and removed APIs, classes, and methods for Hardware Station (HWS)

| Obsoleted and removed APIs, Classes, and Methods |Version made Obsolete | Reason for change |Recommended action | Version the APIs, Classes, and Methods will be removed from source | Sample code |
| ------ | ------ |------ |------- |------ |------ |
GenericWarningEvent |	10.0.14	| Extension must use their own Application insights to log the events	| 	Change your code by removing the use of the API, Class, or Method and use your own Application insights to log the events	| 	10.0.33	| [Log extension events to Application Insights](commerce-application-insights.md)	| 
GenericInformationEvent |	10.0.14	| Extension must use their own Application insights to log the events	| 	Change your code by removing the use of the API, Class, or Method and use your own Application insights to log the events	| 	10.0.33	| [Log extension events to Application Insights](commerce-application-insights.md)	|
GenericDebugEvent |	10.0.14	| Extension must use their own Application insights to log the events	| 	Change your code by removing the use of the API, Class, or Method and use your own Application insights to log the events	| 	10.0.33	| [Log extension events to Application Insights](commerce-application-insights.md)	|
ExtendedCriticalEvent |	10.0.14	| Extension must use their own Application insights to log the events	| 	Change your code by removing the use of the API, Class, or Method and use your own Application insights to log the events	| 	10.0.33	| [Log extension events to Application Insights](commerce-application-insights.md)	|
ExtendedErrorEvent |	10.0.14	| Extension must use their own Application insights to log the events	| 	Change your code by removing the use of the API, Class, or Method and use your own Application insights to log the events	| 	10.0.33	| [Log extension events to Application Insights](commerce-application-insights.md)	|
ExtendedWarningEvent |	10.0.14	| Extension must use their own Application insights to log the events	| 	Change your code by removing the use of the API, Class, or Method and use your own Application insights to log the events	| 	10.0.33	| [Log extension events to Application Insights](commerce-application-insights.md)	|
ExtendedInformationalEvent |	10.0.14	| Extension must use their own Application insights to log the events	| 	Change your code by removing the use of the API, Class, or Method and use your own Application insights to log the events	| 	10.0.33	| [Log extension events to Application Insights](commerce-application-insights.md)	|
ExtendedVerboseEvent |	10.0.14	| Extension must use their own Application insights to log the events	| 	Change your code by removing the use of the API, Class, or Method and use your own Application insights to log the events	| 	10.0.33	| [Log extension events to Application Insights](commerce-application-insights.md)	|
