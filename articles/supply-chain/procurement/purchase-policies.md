---
# required metadata

title: Purchasing policies overview
description: This article provides information about purchasing policies. A purchasing policy is a collection of rules that control the requisition process. Purchasing policies help procurement administrators implement their procurement strategy by creating a policy structure that is aligned with the organization’s strategic purchasing requirements.
author: GalynaFedorova
ms.date: 07/25/2019
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: PurchReqSourcingPolicyRule, SysPolicy, SysPolicyListPage, PurchReqControlRule, RequisitionReplenishCatAccessPolicyRule, PurchReApprovalPolicyRule, RequisitionReplenishControlRule, PurchReqControlRFQRule
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: 729a304d-0f3f-4ccb-bd5b-46ee0976c57f
ms.search.region: Global

# ms.search.industry: 
ms.author: gfedorova
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Purchasing policies overview

[!include [banner](../includes/banner.md)]

This article provides information about purchasing policies. A purchasing policy is a collection of rules that control the requisition process. Purchasing policies help procurement administrators implement their procurement strategy by creating a policy structure that is aligned with the organization’s strategic purchasing requirements.

A purchasing policy consists of a set of policy rules. When you define a policy rule, you first select a rule type. You then create a rule for the rule type by defining the settings, the start date, and the end date for the rule.  

For example, an administrator creates a policy, selects the **Catalog policy** rule type, and then adds a catalog policy rule to the policy. This catalog policy rule specifies that the Adventure catalog must be used for internal procurement. After the purchasing policy is associated with a particular organization, employees of that organization see the Adventure catalog when they create requisitions.

## Assigning policies to organizations
Before a policy can take effect, it must be associated with an organization. Purchasing policies are associated with the **Procurement internal control** hierarchy purpose. Therefore, purchasing policies apply only to organizations in hierarchies that have a hierarchy purpose of **Procurement internal control**. You can also select organizations from the flat list of legal entities in the CompanyInfo table. These legal entities are designated in the policy framework as “Companies.”

## Determining which rule to apply
Depending on how you configure your purchasing policies, multiple rules can affect the users in an organization. The following examples illustrate different ways that you can configure purchasing policies and specify how policies are applied when a transaction occurs.

### Example 1: Simple purchasing policy configuration

Organizations that are small and less complex can set up purchasing policies by legal entity, and can use only the Companies organization hierarchy.  

For Fabrikam, a small business, purchasing requirements vary little across the organization. Purchasing rules vary only among the organization's legal entities. For example, employees of Fabrikam Canada and employees of Fabrikam U.S. purchase goods and services from different catalogs and different vendors. Therefore, Fabrikam sets up its purchasing policies at the legal-entity level.  

Fabrikam creates two purchasing policies. Policy A applies to its U.S. legal entity, 1111. Policy B applies to its Canadian legal entity, 2222. When an employee in legal entity 1111 creates a purchase requisition, the policy rules are derived from policy A. For example, the product catalog that the employee sees is specified in the catalog policy rule for policy A.  

When an employee in legal entity 2222 creates a purchase requisition, the policy rules are derived from policy B.  

**Note:** If an employee of legal entity 1111 purchases an item on behalf of an employee of legal entity 2222, the policy rules that are specified for legal entity 2222 (that is, the policy rules from policy B) are applied.

### Example 2: Complex purchasing policy configuration

In the previous example, all purchasing rules were defined in a single organization hierarchy, the Companies organization hierarchy. However, a complex organization might define policies for multiple organization hierarchies.  


Contoso is a large company that requires complex purchasing rules to control the requisition process. Contoso has defined rules for two different organization hierarchies: Department and Global purchasing control.  

Policy 123 is defined for the Department organization hierarchy for the Sales UK – Sales department. In policy 123, the purchase requisition control rule specifies that restrictions must be enforced for minimum order quantities. In this rule, the **Enforce minimum order quantity restrictions** option is selected.  

Policy 456 is defined for the Global purchasing control organization hierarchy for the Sales and Marketing department. In policy 456, the purchase requisition control rule doesn't specify that restrictions must be enforced for minimum order quantities. In this rule, the **Enforce minimum order quantity restrictions** option is de-selected.  

Sam works in the Sales UK – Sales department in Contoso’s United Kingdom office. The policies for both the Department and Global purchasing control organization hierarchies apply to Sam's department. When Sam creates a purchase requisition, the system must determine which policy to apply. The system administrator set up the purchasing policy parameters to specify that purchasing policies must be applied in the following order of precedence:

1.  Global purchasing control
2.  Department
3.  Companies

Therefore, policy 456 is applied to the purchase requisition that Sam creates, and no minimum order quantity is required for the purchase requisition.

## Policy rules
### Catalog policy rule

The catalog policy rule determines which procurement catalog users see when they create purchase requisitions. If a user has been granted permission to order products on behalf of another user, the requisition uses the catalog policy rule that is defined for the requester’s legal entity and operating unit to determine which catalog to display. Before you can define a catalog policy rule, you must create and publish a procurement catalog.

### Category access policy rule

The category access policy rule determines which categories users have access to when they create purchase requisitions. If no rule is specified, all the procurement categories can be added to the purchase requisition.

1.  Select the **Include parent rule** option to apply the category access policy rule of the parent organization to the category.
2.  In the **Available categories** pane, select the categories that the rule applies to. When you select a category, all categories that are higher in the hierarchy are also added to the **Selected categories** list.
3.  Select the **Include subcategories** option to apply the rule to all subcategories of the selected category.

### Category policy rule

The category policy rule defines how users can select vendors for each category. It also defines requirements for the receiving and invoicing processes.

### Re-approval rule for purchase orders

The re-approval rule is an optional rule that defines the criteria for requiring re-approval when a purchase order is changed. The selected fields are evaluated in the purchase order workflow when the "Requires purchase order re-approval" condition is set up in the workflow.

> [!NOTE]
> Accounting distribution will always be reset when an approved purchase order with change management enabled is changed. So you should be aware that if you want to avoid a re-approval of a purchase order when certain fields are changed, the field Accounting distribution.changed should NOT be included as a selected field for re-approval. 

### Purchase requisition RFQ rule

The purchase requisition RFQ rule defines criteria for requiring a request for quotation (RFQ) for a purchase requisition line. If a line meets the conditions, the "informal RFQ" or "formal RFQ" stamp appears on the requisition line.

### Purchase requisition control rule

The purchase requisition control rule for requisitions of type **consumption** is an optional rule. When you create rules of this type, you can set options on various tabs:

-   On the **Workflow submission** tab, you can configure the fields that must be entered on the requisition line for the requisition to be submitted for approval.
-   On the **Order quantities** tab, you can configure the fields that are required on the purchase requisition under certain conditions. You can also enforce order quantities.
-   On the **Dates** tab, you can configure whether the accounting date is the same as the requested date
-   On the **Address** tab, you can define whether the user is allowed to create new addresses in the system to apply to the purchase requisition.

### Requisition purpose rule

The requisition purpose rule is an optional rule that determines the type of requisition purpose that is allowed for a specific legal entity. Unless another purpose is indicated in this rule, requisitions automatically have a purpose of **Consumption** when they are created.

### Replenishment category access policy rule

The replenishment category access policy rule is an optional rule that determines the products that are available to fulfill requisition demand for a specific legal entity when the requisition purpose is **Replenishment**.

### Replenishment control rule

The replenishment control rule is an optional rule that defines the fields that must be entered on the requisition line for the requisition to be submitted for approval when the requisition purpose is **Replenishment**.

### Purchase order creation and demand consolidation rule

The purchase order creation and demand consolidation rule defines the policy rules to use when a purchase order is generated from an approved purchase requisition. When you create rules of this type, you can set options on various tabs:

-   On the **Purchase order split** tab, you can define criteria for splitting purchase requisition lines onto separate purchase orders.
-   On the **Price/discount transfer** tab, you can define when to recalculate the price agreement when a purchase order is created:
    -   **Only if no trade agreement** – Prices and discounts are transferred from the purchase requisition only if there is no applicable trade agreement or base price. If a trade agreement or base price exists for the item or vendor, the prices and discounts are recalculated based on the trade agreement or the base price, and are applied to the purchase order. Unless otherwise specified, this is the default behavior.
    -   **Always** – Prices and discounts are always transferred from the purchase requisition.

    You can also allow the requester to change the method of price and discount transfer for individual purchase requisition lines, regardless of the price/discount transfer rule that is defined. Select the **Allow manual override per purchase requisition line** option to enable this capability.
-   On the **Item description transfer** tab, you can transfer the item description from the requisition when it originates from an RFQ.
-   On the **Price Tolerance** tab, you can define rules to route approved purchase requisitions back through the review process when the price of a procurement catalog item increases. Set the maximum amount that the net amount on a line item on a purchase requisition can increase between the time when the purchase requisition is approved and the time when the purchase order is created. The net amount is calculated by using the following formula: (\[Quantity × (Unit price – Discount) ÷ Price unit\] + Purchase miscellaneous charges) × (100 – Discount percent) ÷ 100 Purchase requisition lines that exceed the price tolerance that you set are held for manual processing. The rules that you configure on the **Error processing** tab determine how the purchase requisition lines are processed.
-   On the **Error processing** tab, you can configure the processing rule that is applied to a purchase requisition if it fails validation during purchase order creation because of a vendor error or a price tolerance error. Select one of the following options:
    -   **No action** – The purchase requisition lines remain on the **Release approved purchase requisitions** page. The status of the purchase requisition lines remains **Approved**. However, the errors must be resolved before a purchase order can be generated for the purchase requisition lines.
    -   **Cancel the purchase requisition line** – The purchase requisition lines are canceled. The requester can create a new purchase requisition for the canceled lines if they still want to request the line items.
    -   **Create a new purchase requisition line** – The purchase requisition lines are canceled. New purchase requisitions are then generated that contain only the purchase requisition lines that failed validation. The new purchase requisitions that are generated have a status of **Draft**. These purchase requisitions can be resubmitted for review after the validation errors have been resolved. The preparer of the purchase requisition lines is notified that the lines were canceled, and that new purchase requisitions were generated for the purchase requisition lines that failed.
-   On the **Manual purchase order creation** tab, you can define the parameters that determine whether a purchase requisition must be manually processed, or whether it can be automatically converted to a purchase order. The parameters can apply to internal catalog items, external catalog items, or non-catalog items. Select one of the following options:
    -   **Manually create purchase orders** – Manually create purchase orders for all purchase requisitions.
    -   **Automatically create purchase orders** – Automatically create purchase orders for all approved purchase requisitions. No purchase requisitions are held for manual purchase order creation.
    -   **Automatically create purchase orders except under these conditions** – Manually create purchase orders for purchase requisitions that match the criteria that you define. All other purchase requisitions that are approved are automatically converted to purchase orders. If you select **Automatically create purchase orders except under these conditions**, you can add procurement categories and vendors to specify which approved purchase requisition lines are held for manual processing. This option can apply to internal catalog items, external catalog items, and non-catalog items. When you select a procurement category, any subcategories for that procurement category are also selected. Select the **All** option for a specific type of purchase requisition line to hold all lines of that line type for manual processing.

    If you want purchase orders to be generated automatically from approved purchase requisitions when the batch job for purchase order generation runs, select the **Run automatic purchase order creation as a batch job** option. This option applies only to purchase requisitions that don't require manual processing. By running automatic purchase order generation as a batch job, you can schedule this activity at a time when resources are less constrained. If the **Prepayment required** option is selected on the purchase requisition lines, select the **When the requisition is set up for prepayment** option to hold approved purchase requisitions for manual processing. Purchase requisitions that are held for manual processing can be filtered so that you can view only those purchase requisition lines that require prepayment.
-   On the **Demand consolidation** tab, you can define the parameters that determine whether purchase requisitions that are manually processed can be considered for purchase requisition consolidation. The parameters can apply to internal catalog items, external catalog items, or non-catalog items. Select one of the following options:
    -   **Do not allow demand consolidation** – No approved purchase requisition lines are eligible for demand consolidation. This option is selected by default and applies only to purchase requisition lines that require manual processing for purchase order creation.
    -   **Always allow demand consolidation** – All approved purchase requisition lines are eligible for demand consolidation. **Note:** If you select the **Always allow demand consolidation** option on the **Demand consolidation** tab, but you select the **Automatically create purchase orders** option on the **Manual purchase order creation** tab, all purchase requisitions are held for manual processing.
    -   **Allow demand consolidation under these conditions** – Define the criteria that determine whether approved purchase requisition lines are eligible for demand consolidation. For each type of purchase requisition line, you can set the criteria by procurement category and vendor. If you select **Allow demand consolidation under these conditions**, you can set the criteria by procurement category and vendor for each type of purchase requisition line. When you select a procurement category, any subcategories for that procurement category are also selected. If you select the **All** option for a specific line type, all purchase requisition lines of that line type are eligible for demand consolidation.






[!INCLUDE[footer-include](../../includes/footer-banner.md)]
