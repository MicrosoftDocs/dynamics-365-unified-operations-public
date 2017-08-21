---
# required metadata

title: Vendor rebates examples
description: Vendor rebates help companies better manage their supplier rebate programs by automating tasks that are involved in administering, 
tracking, and claiming rebates that are earned.
author: [author's GitHub alias]
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: [Pick one: Application User/Developer/IT Pro]
# ms.devlang: 
# ms.reviewer: [Content Strategist microsoft alias]
ms.search.scope: [Which Operations client to show this topic as help for, to be set by content strategist, see list here: https://microsoft.sharepoint.com/teams/DynDoc/_layouts/15/WopiFrame.aspx?sourcedoc={23419e1c-eb64-42e9-aa9b-79875b428718}&action=edit&wd=target%28Core%20Dynamics%20AX%20CP%20requirements%2Eone%7C4CC185C0%2DEFAA%2D42CD%2D94B9%2D8F2A45E7F61A%2FVersions%20list%20for%20docs%20topics%7CC14BE630%2D5151%2D49D6%2D8305%2D554B5084593C%2F%29]
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: [Global for most topics. Set Country/Region name for localizations]
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: [author's Microsoft alias]
ms.search.validFrom: [month/year of release that feature was introduced in, in format yyyy-mm-dd]
ms.dyn365.ops.version: [name of release that feature was introduced in, see list here: https://microsoft.sharepoint.com/teams/DynDoc/_layouts/15/WopiFrame.aspx?sourcedoc={23419e1c-eb64-42e9-aa9b-79875b428718}&action=edit&wd=target%28Core%20Dynamics%20AX%20CP%20requirements%2Eone%7C4CC185C0%2DEFAA%2D42CD%2D94B9%2D8F2A45E7F61A%2FVersions%20list%20for%20docs%20topics%7CC14BE630%2D5151%2D49D6%2D8305%2D554B5084593C%2F%29]
---

# Vendor rebates
[!include[banner](../includes/banner.md)]

Vendor rebates help companies better manage their supplier rebate programs by automating tasks that are involved in administering, tracking, and claiming rebates that are earned.

This article provides a broad overview of the most common tasks that you’d want to accomplish when working with vendor rebates. The overview includes the following tasks:

● Review details of a rebate agreement

●	Identify orders that qualify for rebates and generate rebate claims

●	Review and approve claims

### Audience and purpose

The information provided in this article is intended for business decision makers in enterprise companies, in capacities such as purchase manager, chief financial officer (CFO), and accounting manager, who have the following responsibilities:

-   Negotiating vendor price, discount, and rebate agreements 
-   Managing staff that processes rebate claims and collects payments 
-   Ordering inventory at the best possible pricesOn the **Prices** tab, the **Enable price details** option is set to **Yes**.

People in these positions are looking for ways to achieve goals such as these: 

-   Flexibly accommodate different types of vendor promotion programs and rebate conditions. 
-   Reduce the administrative burden and errors that are associated with monitoring promotion performance and processing claims. 
-   Improve cash flow forecasts by accruing for future receivables. 
-   Have a quantified basis for ongoing and future negotiations with the vendor about rebates. 

## Review details of a vendor rebate agreement
A vendor rebate agreement is a record of a contract with a vendor that specifies the negotiated terms and conditions under which the company qualifies for a monetary reward in return for achieving preset purchase targets. Vendor rebate agreements are recorded on the Rebate agreements page.

To open the **Vendor rebate agreements** page, click **Procurement and sourcing** \> **Vendor rebates** \> **Rebate agreements**.

![Purchase agreement](media/purchase-agreement.PNG)

On the **Vendor rebate agreements** page, you can view details about the negotiated conditions of a vendor agreement.

The agreement's header specifies the general conditions that qualify a company for rebates. For example, the header information might specify that vendor A grants a rebate when product X is bought in a quantity of Y.

-   In the **Cumulate purchase by** field, you can set the calculation of the rebate claim. The amount can be set to depend on a period (of week, month, year, lifetime or a customized period). **Invoice** indicates that a rebate claim will be determined every time that a purchase order line is invoiced.

-   The **Rebate program accrual account** and **Rebate program expense account** fields specify account numbers that will receive accrued rebate amounts during the intermediate stage between approval and processing.

-   In the **Rebate line break type** field, the options **Quantity** and **Amount** indicate that the rebates are either volume-based or amount-based.

-   On the **Lines** FastTab, you can see how different quantity tiers can be set up to grant different rebates. For example, in the illustration, the **From value** and the **To value** fields indicate that a product quantity between 10 and 19 units will qualify for a rebate of USD 15 per unit.

-   In the **Workflow approval status** field, the value **Approved** indicates that the agreement can be applied to purchase orders that meet the agreement’s conditions.

-   In the **Unit of measure rebate option** field, you can define if a unit of measure should be a condition for the purchase order line to qualify for a rebate claim. **Convert** indicates that you are entitled to a rebate regardless of the unit of measure on the purchase order line. **Exact match** indicates that a purchase line must have exactly the same unit of measure as is specified on the rebate agreement to qualify for a rebate.

> [!NOTE]
> If items are bought in a different purchase unit than the inventory unit and rebate agreements have have been set up for both the inventory unit and the purchasing unit, you must select **Exact match** in the **Unit of measure rebate option** field to ensure that the rebate claim is only generated once. 

## Identify orders that qualify for rebates and generate rebate claims
 
When purchase orders are placed with a vendor that the company has a rebate agreement with, the program identifies any future vendor credit payments. If the purchase orders qualify for a rebate, a rebte claim will be generated for every order line as soon as a purchase invoice has been posted. This is an automatic process. Subsequently, you can review the expected rebates and see the impact of those rebates on the product’s cost and profit margin. 

### View details of rebates applied to a purchase order line by the vendor rebate agreement:
1.  On the **Purchase order** page, select an order line, and then click **Purchase order line** \> **View** \> **Price details** \>.
2.  On the **Price details** page, click the **Rebates** FastTab.

The rebate information is also shown in the **Vendor rebate** field in the **Margin estimation** section of the **Price details** page.

> [!NOTE]
> To be able to view the rebates, verify that the **Enable price details** option is set to **Yes** on the **Prices** tab on the **Procurement and sourcing parameters** page.

## Review and approve claims 
Generated rebate claims represent the future payments that can be expected from the vendor. Before a credit note is issued to the vendor, the agreement owner typically wants to review the claims and approve them. Note, however, that the status of a claim will determine if it is ready to go through the approval process.

### The status of claims and the effect on the approval process 
When a claim is generated, its status is set to either **To be calculated** or **Calculated**. This status depends on whether the rebate is granted on a cumulative basis or per invoice, respectively. If the status of the claims is **To be calculated**, they need to go through a calculation process which is handled by the Cumulate function. Only claims with the status **Calculated** can be included in the approval process. 

> [!NOTE] 
> If the **Approval required** check box on a vendor rebate agreement is not selected, the claims will be generated with the status **Approved**. The approval is mandatory for claims granted on a cumulative basis.

### Approve claims and view postings and invoice details
When claims have been approved, they can be processed by the Accounts payable and a credit memo (vendor invoice) for the rebate claim amount is automatically created. The credit can then be added to the vendor balance, and the Accounts payable team can include it in the regular settlement process.

1. Click **Procurement and sourcing** > **Vendor Rebates** > **Rebate claims** to open a rebate claim. 
2. Close the rebate claim.
3. Mark the claim, and then, on the Action Pane, click **Approve**.
4. On the request page, in the **Vendor** field, select the vendor from whom you are authorized to receive a rebate, and then click **OK**.

A Rebate accrual journal is posted for the claim amount. This posting debits the Accrued Vendor Rebates Receivable account for the expected vendor credit and credits the interim Accrued Vendor Rebates Received account for the expected gain.

![Message](media/message.png)

5. In the rebate list, select the line, and then, on the Action Pane, click **Rebate transactions** to see and navigate to the journal batch number for this rebate accrual posting. 

To move the claims to the regular A/P process, the A/P clerk must now complete the rebate claim handling by running the Process function.

6. On the Action Pane, click **Process**, click **Filter**.  In the **Criteria** field for the **Vendor account** field, select the vendor whose rebate claims you want to process, click other relevant filters, and then click **OK**.

The message bars and the fact that the status has changed to **Completed** indicate that the following events have occurred:

-   A Rebate accrual journal posting has reversed the previous interim amounts on the accrual receivable and expense accounts.

-   A vendor invoice (credit note) for the rebate amount has been created.

> [!NOTE] 
> The setting of the **Manual invoice posting** option on the **Rebate program** tab of the **Procurement and sourcing parameters** page determines whether a vendor invoice is posted automatically as part of claim processing or manually.

-   When the vendor invoice is posted, automatically or manually, the vendor’s Payable account has been debited, and the Discounts and Allowances Received account has been credited.

> [!NOTE] 
> The Discounts and Allowances Received account number is specified for the procurement category that is used on the purchase invoice line for the rebate. The procurement category, in turn, is set on the **Rebate program** tab of the **Procurement and sourcing parameters** page.

7. In the rebate list, select the line, and then, on the Action Pane, click **Rebate transactions** to see and navigate to the journal batch number for this rebate accrual posting and also the vendor invoice number.

8. Select the line for the vendor invoice transaction, and then, on the Action Pane, click **Vendor invoice**. If the vendor invoice has been posted, you will see the Invoice journal. Otherwise, you will see the vendor invoice as a pending vendor invoice, that requires manual posting.

The invoice line specifies the details of the vendor invoice for the **Commissions and Rebates** procurement category. 

9. On the **All vendors** page, select the vendor from whom you receive a rebate, and then, on the Action Pane, click **Transactions** and find the line for the invoice. The rebate amount has now been added to the vendor balance.

## Summary
The process for handling vendor rebates involves multiple manual tracking tasks that are often tedious. By automating these tasks, the vendor rebate management feature can help you move through the following processes: 
-   Generating accurate rebate claims 
-   Accruing the expected receivable and interim gain in the general ledger 
-   Updating the vendor balance and the income statement with the allowance that is due 
