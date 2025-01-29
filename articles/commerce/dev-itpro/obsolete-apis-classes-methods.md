---
title: Obsolete and removed APIs, classes, and methods
description: This article lists the obsolete and removed APIs, classes, and methods in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 08/09/2024
ms.topic: overview
audience: Developer
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: anupamar
ms.search.validFrom: 2022-05-24
ms.custom: 
  - bap-template
---
# Obsolete and removed APIs, classes, and methods

[!include [banner](../includes/banner.md)]

This article lists the obsolete and removed APIs, classes, and methods in Microsoft Dynamics 365 Commerce.

Several APIs, classes, and methods have been either removed or marked as obsolete in Dynamics 365 Commerce. As Dynamics 365 Commerce changes over time, each new version adds new APIs, classes, and methods that provide new functionality. Existing APIs, classes, and methods also change over time. For example, some APIs become less important as the functionality that they support is replaced by new functionality, whereas other methods are superseded by newer methods that are superior in some way or use different underlying technologies to provide better performance and reliability.

Dynamics 365 Commerce strives to support backward compatibility, so that extensions that were developed by using one version of Commerce can run on the next version. However, backward compatibility makes it difficult to just remove APIs, classes, or methods. Instead, Dynamics 365 Commerce indicates that an API, class, or method should no longer be used by marking it as obsolete or deprecated. (The terms *obsolete* and *deprecated* have the same meaning when they are applied to .NET types and members.) In this way, developers are aware that the API, class, or method will go away, and they have time to prepare for its removal. 

## Obsolete attribute

In Dynamic 365 Commerce, an API, class, or method is marked as obsolete by applying the **Obsolete** attribute to it. This attribute indicates that the API, class, or method will be removed in a future version of Dynamic 365 Commerce.

## Handling obsolete types and members

When you upgrade and recompile existing code, you might receive a compiler warning message if you use an obsolete API, class, or method in your extension. However, it's acceptable to use the obsolete API, class, or method until it's removed. Nevertheless, you should review the warning message to determine whether you should change your extension code. If the warning message doesn't point to a suitable alternative, you should follow one of these steps:

- If you can, change your code so that the API, class, or method is no longer used.
- Review the documentation for this area to determine how to respond to the deprecation.

## Obsolete and removed APIs, classes, and methods for Hardware Station (HWS)

| Obsolete and removed APIs, classes, and methods | Version where they were made obsolete | Reason for the change | Recommended action | Version where the APIs, classes, and methods will be removed from source code | Sample code |
| ------ | ------ |------ |------- |------ |------ |
GenericWarningEvent | 10.0.14 | Extension must use Application insights to log events. | Change your code so that the API, class, or method is no longer used, and then use your own Application Insights instance to log events. | 10.0.33 | [Log extension events to Application Insights](commerce-application-insights.md) | 
GenericInformationEvent | 10.0.14 | Extension must use Application insights to log events. | Change your code so that the API, class, or method is no longer used, and then use your own Application Insights instance to log events. | 10.0.33 | [Log extension events to Application Insights](commerce-application-insights.md) |
GenericDebugEvent | 10.0.14 | Extension must use Application insights to log events. | Change your code so that the API, class, or method is no longer used, and then use your own Application Insights instance to log events. | 10.0.33 | [Log extension events to Application Insights](commerce-application-insights.md) |
ExtendedCriticalEvent | 10.0.14 | Extension must use Application insights to log events. | Change your code so that the API, class, or method is no longer used, and then use your own Application Insights instance to log events. | 10.0.33 | [Log extension events to Application Insights](commerce-application-insights.md) |
ExtendedErrorEvent | 10.0.14 | Extension must use Application insights to log events. | Change your code so that the API, class, or method is no longer used, and then use your own Application Insights instance to log events. | 10.0.33 | [Log extension events to Application Insights](commerce-application-insights.md) |
ExtendedWarningEvent | 10.0.14 | Extension must use Application insights to log events. | Change your code so that the API, class, or method is no longer used, and then use your own Application Insights instance to log events. | 10.0.33 | [Log extension events to Application Insights](commerce-application-insights.md) |
ExtendedInformationalEvent | 10.0.14 | Extension must use Application insights to log events. | Change your code so that the API, class, or method is no longer used, and then use your own Application Insights instance to log events. | 10.0.33 | [Log extension events to Application Insights](commerce-application-insights.md) |
ExtendedVerboseEvent | 10.0.14 | Extension must use Application insights to log events. | Change your code so that the API, class, or method is no longer used, and then use your own Application Insights instance to log events. | 10.0.33 | [Log extension events to Application Insights](commerce-application-insights.md) |
