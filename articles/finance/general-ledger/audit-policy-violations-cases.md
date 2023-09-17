---
# required metadata

title: Audit policy violations and cases
description: The article explains how audit cases are generated from violations of audit policy rules. It also includes information about the various ways that audit policies use the document selection date range.
author: panolte
ms.date: 06/20/2017
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
ms.assetid: e0e66c6d-c396-4a9d-b3b6-3641d130fdc0
ms.search.region: Global
# ms.search.industry: 
ms.author: panolte
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Audit policy violations and cases

[!include [banner](../includes/banner.md)]

The article explains how audit cases are generated from violations of audit policy rules. It also includes information about the various ways that audit policies use the document selection date range.

## How audit cases are generated

Audit policies are used to identify expense reports, purchase orders, and vendor invoices that don't comply with business rules that you define and configure as audit policy rules. 

Audit policies are run in batch mode. When you run an audit policy, all the policy rules that are part of that policy are run at the same time.

Each policy rule evaluates a set of documents. The policy rule selects documents that are in the document selection date range and that match the specified criteria. For example, one policy rule might select expense reports that have meals that exceed 50.00. Another policy rule might select vendor invoices that are payable to a specific vendor. For each document that is selected in the set, a violation is generated. That violation is a record that a particular document, such as invoice 12345, doesn't comply with the policy rule. 

Multiple audit violation records are grouped together and associated with audit cases. By default, cases for each audit policy are grouped by audit policy rule. If you prefer, you can select other grouping criteria by using the **Case grouping criteria** page. For example, you can group expense headers by project ID and vendor invoices by vendor account. In this case, all expense header violations that have the same project ID will be grouped in the same case, and all vendor invoices that have the same vendor account will be grouped in the same case. 

> [!NOTE]
> For audit policy rules that are based on a **Duplicate** query type, violations aren't grouped by policy rule or by the criteria that are specified on the **Case grouping criteria** page. Instead, they are grouped by the criteria that are built into the audit policy rule. For example, if a policy rule evaluates expense reports for duplicate expenses of the same amount, merchant ID, and date, all expenses that have the same values in those fields will be one case. Any expenses that have different values will be a separate case.

After the audit cases have been generated, they are handled by using the typical processes for case management.

## Document selection date ranges
When an audit policy is run, each policy rule selects documents of the specified type that have a date that is in the document selection date range. The document selection date range is specified on the **Additional options** page. Many documents have more than one date associated with them. The date field that the audit policy rule uses is specified on the **Policy rule type** page.

Here are some other ways that an audit policy uses the document selection date range:

-   The policy uses the version of each policy rule that is effective on the last day of the document selection date range. You can view the effective dates for each policy rule on the **Audit policies** list page.
-   The policy uses the organization nodes that are associated with the policy on the last day of the document selection date range. Only the organization nodes that are currently associated with the policy appear on the **Audit policies** list page.
-   For policy rules that are based on a **List search** query type, the policy evaluates documents for monitored entities that are effective on the last day of the document selection date range.


For more information, see [Audit policy rules](audit-policy-rules.md)





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
