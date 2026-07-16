---
title: Audit policy rules
description: You can use audit policies to evaluate expense reports, vendor invoices, and purchase orders to make sure that they comply with policy rules that you create.
author: twheeloc
ms.author: twheeloc
ms.topic: article
ms.date: 06/24/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: AuditPolicyAdditionalOption, AuditPolicyRule
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 8d787017-71dc-418f-b8c2-4ea9763d9978
---

# Audit policy rules

[!include [banner](../includes/banner.md)]

Use audit policies to check expense reports, vendor invoices, and purchase orders. Make sure they follow the policy rules you create. The system runs all the rules for an audit policy in batch mode, following the schedule you set. Each policy rule belongs to a policy rule type. For each policy rule type, only one policy rule can be active at a time. 

## Queries and query types

When you create an audit policy rule, you first select a policy rule type. The policy rule type specifies the Application Object Tree (AOT) query to use as the starting point for creating the policy rule. It also specifies the query type to use for the policy rule. The query determines the source document that the policy rule evaluates. It also specifies the fields in the source document that identify both the legal entity and the date to use when documents are selected for audit. The query type controls the default fields in the query page and in the Audit policy rule page. The following table shows the query types that are available for audit policy rules.

| Query type | Purpose | More information |
|---|---|---|
| Conditional | Evaluate source document attributes against specified values. | |
| Aggregate | Evaluate multiple source documents or source document lines against a policy rule by aggregating numeric values. | |
| Sampling | Randomly select a specified percentage of the source documents to evaluate for policy violations. | When you select this option, use the Audit policy rule page to specify the percentage of documents to randomly select for audit. |
| Duplicate | Evaluate source documents to determine whether they contain duplicate entries in specified fields. | When you select this option, use the Audit policy rule page to specify the number of days to add to the start of the document selection date range when evaluating documents for duplicate entries. |
| List search | Evaluate source documents for specific entities. | The root document of the query defines the document that's being audited. The query must be a list query that includes a reference to the dirpartytable table. You can use this option only with the following AOT queries:<ul><li><span class="ui">AuditPolicyExpenseList</span> (Expense report monitored employees)</li><li><span class="ui">AuditPolicyPurchList</span> (Purchase order monitored vendors)</li><li><span class="ui">AuditPolicyVendInvoiceList</span> (Vendor invoice monitored vendors)</li></ul>When you select this option, specify the monitored entities in the Audit policy rule page. |
| Keyword search | Evaluate source documents to determine whether they contain certain words. | When you select this option, enter the words to look for in the Audit policy rule page. The Audit policy rule page also includes options that you can use to specify the tables and fields to evaluate for the words you entered. |

## Common parameters
All policy rules for a particular audit policy share the same batch parameters and the same document selection date range. Specify these parameters for the policy in the **Additional options** page.



## Additional resources

[Audit policy violations and cases](audit-policy-violations-cases.md)
[Define audit policies for source documents](tasks/define-audit-policies-source-documents.md)




[!INCLUDE[footer-include](../../includes/footer-banner.md)]
