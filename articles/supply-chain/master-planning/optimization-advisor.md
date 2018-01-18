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

# Writing rules for the Optimization advisor

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

The **SelfHealingRule** abstract class has some abstract methods that must be implemented in inheriting classes. The core is the **evaluate** method, which returns a List of the opportunities detected by the rule. Opportunities can be per legal entity or can apply to the whole system.

```
protected List evaluate() 
{ 
    List results = new List(Types::Record); 
    
    DataArea dataArea; 

    while select id from dataArea 
        where !dataArea.isVirtual 
    { 
        changecompany(dataArea.id) 
        { 
            container result = this.findRFQCasesWithEmptyTitle(); 

            if (conLen(result) > 0) 
            { 
                SelfHealingOpportunity opportunity = this.getOpportunityForCompany(dataArea.Id); 
                opportunity.EvaluationState = SelfHealingEvaluationState::Evaluated; 
                opportunity.Data = result; 
                opportunity.OpportunityDate = DateTimeUtil::utcNow(); 
                
                results.addEnd(opportunity); 
            } 
        } 
    } 
    
    return results; 
} 
```

The method above is looping over companies and selecting RFQ Cases with empty titles, in the **findRFQCasesWithEmptyTitle** method. If at least one such case is found, then a company specific opportunity is created with the **getOpportunityForCompany** method. Notice that the field **Data** in the **SelfHealingOpportunity** table is of type **container**, and can therefore contain any data relevant to the logic specific to this rule. Setting **OpportunityDate** with the current timestamp registers the time of the latest evaluation of the opportunity.  

Opportunities can also be cross company. In that case, the loop over companies is not necessary and the opportunity must be created with the **getOpportunityAcrossCompanies** method. 

Below is the code for **findRFQCasesWithEmptyTitle** method, which returns the IDs of the RFQ cases that have empty titles.

```
private container findRFQCasesWithEmptyTitle() 
{ 
    container result; 

    PurchRFQCaseTable rfqCase; 
    while select RFQCaseId from rfqCase 
        where rfqCase.Name == '' 
    { 
        result += rfqCase.RFQCaseId; 
    } 
    
    return result; 
} 
```

Two more methods that must be implemented are **opportunityTitle** and **opportunityDetails**. The former returns a short title for the opportunity, the latter returns a detailed description of the opportunity, which can also include data.

The title returned by **opportunityTitle** appears under the **Optimization opportunity** column on the **Optimization advisor** workspace. It also appears as header of the side pane showing more information on the opportunity. By convention, this method is decorated with the **DiagnosticRuleSubscription** attribute, which takes the following arguments: 

* **Diagnostic area** – an enum of type **DiagnosticArea** describing what area of the application the rule belongs to (e.g. **DiagnosticArea::SCM**) 

* **Rule name** – a string with the rule name; it will appear under the **Rule name** column in the **Dianostics validation rule** form (**DiagnosticsValidationRuleMaintain**) 

* **Run frequency** – an enum of type **DiagnosticRunFrequency** describing how often the rule should be run (e.g. **DiagnosticRunFrequency::Daily**). 

* **Rule description** – a string with a more detailed description of the rule; it will appear under the **Rule description** column in the **Dianostics validation rule** form (**DiagnosticsValidationRuleMaintain**) 

> [!NOTE]
> The attribute is required for the rule to work. It is conventionally used on opportunityTitle, but it can decorate any method of the class.

Below is an example implementation. Raw strings are used for simplicity, but a correct implementation requires labels. 

```
[DiagnosticsRuleSubscription(DiagnosticsArea::SCM, 
                             'Assign titles to Request for Quotation cases', 
                             DiagnosticsRunFrequency::Daily,  
                             'This rule detects Requests for Quotation with empty titles.')] 
public str opportunityTitle() 
{ 
    return 'Assign titles to Request for Quotation cases'; 
} 
```
