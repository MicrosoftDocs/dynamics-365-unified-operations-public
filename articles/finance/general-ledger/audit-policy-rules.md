---
# required metadata

title: Audit policy rules
description: You can use audit policies to evaluate expense reports, vendor invoices, and purchase orders to make sure that they comply with policy rules that you create. All of the rules that are associated with an audit policy are run in batch mode, according to a schedule that you specify.  Each policy rule is an instance of a policy rule type. For each policy rule type, only one policy rule can be active at a time. 
author: panolte
ms.date: 08/01/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: AuditPolicyAdditionalOption, AuditPolicyRule
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.assetid: 8d787017-71dc-418f-b8c2-4ea9763d9978
ms.search.region: Global
# ms.search.industry: 
ms.author: panolte
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Audit policy rules

[!include [banner](../includes/banner.md)]

You can use audit policies to evaluate expense reports, vendor invoices, and purchase orders to make sure that they comply with policy rules that you create. All of the rules that are associated with an audit policy are run in batch mode, according to a schedule that you specify.  Each policy rule is an instance of a policy rule type. For each policy rule type, only one policy rule can be active at a time. 

## Queries and query types

When you create an audit policy rule, you first select a policy rule type. The policy rule type specifies the Application Object Tree (AOT) query to use as the starting point for creating the policy rule. It also specifies the query type to use for the policy rule. The query determines the source document that the policy rule evaluates. It also specifies the fields in the source document that identify both the legal entity and the date to use when documents are selected for audit. The query type controls the default fields in the query page and in the Audit policy rule page. The following table shows the query types that are available for audit policy rules.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Query type</th>
<th>Purpose</th>
<th>More information</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Conditional</td>
<td>Evaluate source document attributes against specified values.</td>
<td></td>
</tr>
<tr class="even">
<td>Aggregate</td>
<td>Evaluate multiple source documents or source document lines against a policy rule by aggregating numeric values.</td>
<td></td>
</tr>
<tr class="odd">
<td>Sampling</td>
<td>Randomly select a specified percentage of the source documents to evaluate for policy violations.</td>
<td>When you select this option, use the Audit policy rule page to specify the percentage of documents to randomly select for audit.</td>
</tr>
<tr class="even">
<td>Duplicate</td>
<td>Evaluate source documents to determine whether they contain duplicate entries in specified fields.</td>
<td>When you select this option, use the Audit policy rule page to specify the number of days to add to the start of the document selection date range when documents are evaluated for duplicate entries.</td>
</tr>
<tr class="odd">
<td>List search</td>
<td>Evaluate source documents for specific entities.</td>
<td>The root document of the query defines the document that is being audited. The query must be a list query that includes a reference to the dirpartytable table. This option can be used only with the following AOT queries:
<ul>
<li><span class="ui">AuditPolicyExpenseList</span> (Expense report monitored employees)</li>
<li><span class="ui">AuditPolicyPurchList</span> (Purchase order monitored vendors)</li>
<li><span class="ui">AuditPolicyVendInvoiceList</span> (Vendor invoice monitored vendors)</li>
</ul>
When you select this option, specify the monitored entities in the Audit policy rule page.</td>
</tr>
<tr class="even">
<td>Keyword search</td>
<td>Evaluate source documents to determine whether they contain certain words.</td>
<td>When you select this option, enter the words to look for in the Audit policy rule page. The Audit policy rule page also includes options that let you specify the tables and fields to evaluate for the words you entered.</td>
</tr>
</tbody>
</table>

## Common parameters
All of the policy rules for a particular audit policy share the same batch parameters and the same document selection date range. These parameters are specified for the policy in the Additional options page.



## Additional resources

[Audit policy violations and cases](audit-policy-violations-cases.md)
[Define audit policies for source documents](tasks/define-audit-policies-source-documents.md)




[!INCLUDE[footer-include](../../includes/footer-banner.md)]
