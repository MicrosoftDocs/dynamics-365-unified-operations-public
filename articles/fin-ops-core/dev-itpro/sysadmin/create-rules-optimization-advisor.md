---

# required metadata

title: Create rules for Optimization advisor
description: This topic discusses how to add new rules to Optimization advisor. 
author: roxanadiaconu
ms.date: 02/04/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SelfHealingWorkspace
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: sericks
ms.search.validFrom: 2017-12-01
ms.dyn365.ops.version: 7.3 

---

# Create rules for Optimization advisor

[!include [banner](../includes/banner.md)]

This topic explains how to create new rules for **Optimization advisor**. For example, you can create a new rule that identifies which Request for Quotations (RFQ) cases have an empty title. Using titles on cases makes them easily identifiable and searchable. While quite simple, this example shows what can be achieved with optimization rules. 

A *rule* is a check on application data. If the condition that the rule evaluates is met, opportunities to optimize processes or improve data are created. The opportunities can be acted upon and, optionally, the impact of the actions can be measured. 

To create a new rule for the **Optimization advisor**, add a new class that extends the **SelfHealingRule** abstract class, implements the **IDiagnosticsRule** interface, and is decorated by the **DiagnosticRule** attribute. The class must also have a method decorated with the **DiagnosticsRuleSubscription** attribute. By convention, that is done on the **opportunityTitle** method, which will be discussed later. This new class can be added to a custom model with a dependency on the **SelfHealingRules** model. In the following example, the rule being implemented is called **RFQTitleSelfHealingRule**.

```xpp
[DiagnosticsRule] 
public final class RFQTitleSelfHealingRule extends SelfHealingRule implements IDiagnosticsRule 
{ 
… 
} 
```

The **SelfHealingRule** abstract class has abstract methods that must be implemented in inheriting classes. The core is the **evaluate** method, which returns a list of the opportunities identified by the rule. Opportunities can be per legal entity or can apply to the whole system.

```xpp
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

The method shown above loops over companies and selects RFQ cases with empty titles in the **findRFQCasesWithEmptyTitle** method. If at least one such case is found, then a company-specific opportunity is created with the **getOpportunityForCompany** method. Notice that the field **Data** in the **SelfHealingOpportunity** table is of type **Container**, and can therefore contain any data relevant to the logic specific to this rule. Setting **OpportunityDate** with the current timestamp registers the time of the latest evaluation of the opportunity.  

Opportunities can also be cross-company. In this case, the loop over companies is not necessary and the opportunity must be created with the **getOpportunityAcrossCompanies** method. 

The following code shows the **findRFQCasesWithEmptyTitle** method, which returns the IDs of the RFQ cases that have empty titles.

```xpp
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

The title returned by **opportunityTitle** appears under the **Optimization opportunity** column in the **Optimization advisor** workspace. It also appears as the header of the side pane showing more information about the opportunity. By convention, this method is decorated with the **DiagnosticRuleSubscription** attribute, which takes the following arguments: 

* **Diagnostic area** – An enum of type **DiagnosticArea** that describes what area of the application the rule belongs to, such as **DiagnosticArea::SCM**. 

* **Rule name** – A string with the rule name. This will appear under the **Rule name** column in the **Dianostics validation rule** form (**DiagnosticsValidationRuleMaintain**). 

* **Run frequency** – An enum of type **DiagnosticRunFrequency** that describes how often the rule should be run, such as **DiagnosticRunFrequency::Daily**. 

* **Rule description** – A string with a more detailed description of the rule. This will appear under the **Rule description** column in the **Dianostics validation rule** form (**DiagnosticsValidationRuleMaintain**). 

> [!NOTE]
> The **DiagnosticRuleSubscription** attribute is required for the rule to work. Typically, it is used on **opportunityTitle**, but it can decorate any method of the class.

The following is an example implementation. Raw strings are used for simplicity, but a correct implementation requires labels. 

```xpp
[DiagnosticsRuleSubscription(DiagnosticsArea::SCM, 
                             'Assign titles to Request for Quotation cases', 
                             DiagnosticsRunFrequency::Daily,  
                             'This rule detects Requests for Quotation with empty titles.')] 
public str opportunityTitle() 
{ 
    return 'Assign titles to Request for Quotation cases'; 
} 
```

The description returned by **opportunityDetails** appears on the side pane showing more information about the opportunity. This takes the **SelfHealingOpportunity** argument, which is **Data** field that can be used to provide more details about the opportunity. In the example, the method returns the IDs of the RFQ cases with an empty title. 

```xpp
public str opportunityDetails(SelfHealingOpportunity _opportunity) 
{ 
    str details = ''; 
    container opportunityData = _opportunity.Data; 
    int affectedRFQCasesCount = conLen(opportunityData); 

    if (affectedRFQCasesCount != 0) 
    { 
        details = 'The following Request for Quotation cases have an empty title:\n'; 
        for (int i = 1; i <= affectedRFQCasesCount ; i++) 
        { 
            PurchRFQCaseId rfqCaseId = conPeek(opportunityData, i); 
            details += rfqCaseId + '\n'; 
        } 
    } 

    return details; 
}
```

The two remaining abstract methods to implement are **provideHealingAction** and **securityMenuItem**. 

**provideHealingAction** returns true if a healing action is provided, otherwise, it returns false. If true is returned, the method **performAction** must be implemented, or an error will be thrown. The **performAction** method takes a **SelfHealingOpportunity** argument, in which the data can be used for the action. In the example, the action opens the **PurchRFQCaseTableListPage**, for manual correction. 

```xpp
public boolean providesHealingAction() 
{ 
    return true; 
} 

protected void performAction(SelfHealingOpportunity _opportunity) 
{ 
    new MenuFunction(menuItemDisplayStr(PurchRFQCaseTableListPage), MenuItemType::Display).run(); 
} 
```

Depending on the specifics of the rule, it might be possible to take an automatic action using the opportunity data. In this example, the system could generate titles for RFQ cases automatically. 

**securityMenuItem** returns the name of an action menu item such that the rule is only visible to users who can access the action menu item. Security might require that specific rules and opportunities are accessible only to authorized users. In the example, only users with access to **PurchRFQCaseTitleAction** can view the opportunity. Notice that this action menu item was created for this example, and was added as an entry point for the **PurchRFQCaseTableMaintain** security privilege. 

> [!NOTE]
> The menu item must be an action menu item for security to work correctly. Other menu item types, such as **Display menu items** will not work correctly.

```xpp
public MenuName securityMenuItem() 
{ 
    return menuItemActionStr(PurchRFQCaseTitleAction); 
}
```

After the rule has compiled, execute the following job to have it display in the user interface (UI).

```xpp
class ScanNewRulesJob 
{         
    public static void main(Args _args) 
    {         
        SysExtensionCache::clearAllScopes(); 
        var controller = new DiagnosticsRuleController(); 
        controller.runOperation(); 
    } 
} 
```

The rule will display in the **Diagnostics validation rule** form, available from **System administration** > **Periodic tasks** > **Maintain diagnostics validation rule**. To have it evaluated, go to **System administration** > **Periodic tasks** > **Schedule diagnostics validation rule**, select the frequency of the rule, such as **Daily**. Click **OK**. Go to **System administration** > **Optimization advisor** to view the new opportunity. 

The following example is a code snippet with the skeleton of a rule including all the required methods and attributes. It helps you get started with writing new rules. The labels and action menu items that are used in the example are only used for demonstration purpose.

```xpp
[DiagnosticsRuleAttribute]
public final class SkeletonSelfHealingRule extends SelfHealingRule implements IDiagnosticsRule
{
    [DiagnosticsRuleSubscription(DiagnosticsArea::SCM,
                                 "@SkeletonRuleLabels:SkeletonRuleTitle", // Label with the title of the rule
                                 DiagnosticsRunFrequency::Monthly,
                                 "@SkeletonRuleLabels:SkeletonRuleDescription")] // Label with a description of the rule
    public str opportunityTitle()
    {
        // Return a label with the title of the opportunity
        return "@SkeletonRuleLabels:SkeletonOpportunityTitle";
    }

    public str opportunityDetails(SelfHealingOpportunity _opportunity)
    {
        str details = "";

        // Use _opportunity.data to provide details on the opportunity

        return details;
    }

    protected List evaluate()
    {
        List results = new List(Types::Record);

        // Write here the core logic of the rule

        // When creating an opportunity, use:
        //     * this.getOpportunityForCompany() for company specific opportunities
        //     * this.getOpportunityAcrossCompanies() for cross-company opportunities

        return results;
    }

    public boolean providesHealingAction()
    {
        return true;
    }

    protected void performAction(SelfHealingOpportunity _opportunity)
    {
        // Place here the code that performs the healing action

        // To open a form, use the following:
        // new MenuFunction(menuItemDisplayStr(SkeletonRuleDisplayMenuItem), MenuItemType::Display).run();
    }

    public MenuName securityMenuItem()
    {
        return menuItemActionStr(SkeletonRuleActionMenuItem);
    }

}
```

For more information, watch the short YouTube video: [Optimization advisor in Dynamics 365 for Finance and Operations](https://www.youtube.com/watch?v=MRsAzgFCUSQ)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]