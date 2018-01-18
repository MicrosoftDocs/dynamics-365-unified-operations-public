---
# required metadata

title: Writing Rules for the Optimization Advisor
description: This topic discusses how to add new rules to the Optimization Advisor. 
author: roxanadiaconu
manager: AnnBe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: yuyus
ms.search.scope: Core (Operations, Core)
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: roxanadiaconu
ms.dyn365.ops.intro: 7.3 
ms.search.validFrom: 2017-12-31

---

# Writing Rules for the Optimization Advisor

[!include[banner](../includes/banner.md)]

This article explains how to write a new rule for the Optimization Advisor. To give an example, we will create a new rule that detects what Request for Quotations Cases (RFQ Cases) have an empty title. Having titles on cases makes them clearly identifiable and searchable. While quite simple, this example gives the opportunity to see what can be achieved with optimization rules. 

A rule is a check on application data. If the condition that the rule evaluates is met, opportunities to optimize processes or improve data are created. The opportunities can be acted upon and, optionally, the impact of the actions can be measured. 

To write a new rule for the **Optimization Advisor**, add a new class that extends the **SelfHealingRule** abstract class, implements the **IDiagnosticsRule** interface, and is decorated by the **DiagnosticRule** attribute. The class must also have a method decorated with the **DiagnosticsRuleSubscription** attribute; by convention, that is done on the **opportunityTitle** method, which will be discussed later. This new class can be added to a custom model, with a dependency on the **SelfHealingRules** model. In the following example, the rule being implemented is called **RFQTitleSelfHealingRule**.

```
[DiagnosticsRule] 
public final class RFQTitleSelfHealingRule extends SelfHealingRule implements IDiagnosticsRule 
{ 
… 
} 
```
