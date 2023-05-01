---
# required metadata

title: Purchase agreements
description: This article provides information about purchase agreements. A purchase agreement is a contract that commits an organization to buy a specified quantity or amount by using multiple purchase orders over time. In exchange for this commitment, the buyer receives special prices and discounts. 
author: GalynaFedorova
ms.date: 08/09/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: AgreementClassification, AgreementLine, AgreementLinePrompt, PurchAgreement, PurchAgreementCreate, PurchAgreementGenerateReleaseOrder, PurchAgreementHistory, PurchAgreementInvoiceJournal, PurchLine, AgreementLines
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 11634
ms.assetid: 8ac20adf-7412-4929-be8c-aaedf23a76ad
ms.search.region: Global
# ms.search.industry: 
ms.author: gfedorova
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Purchase agreements

[!include [banner](../includes/banner.md)]

This article provides information about purchase agreements. A purchase agreement is a contract that commits an organization to buy a specified quantity or amount by using multiple purchase orders over time. In exchange for this commitment, the buyer receives special prices and discounts. 

Purchase agreements can apply to a specific quantity of a product, a specific currency amount of a product, or a specific currency amount of the products in a procurement category. The prices and discounts of the purchase agreement override the prices and discounts that are specified in any trade agreements that exist.  

On the **Purchase agreements** page, you can create, apply, and follow up on purchase agreements that exist between your organization and your vendors. For example, after you create a purchase agreement, you can order directly from it. Each purchase agreement has a validity period that is defined by the person who creates the purchase agreement. The delivery date of a purchase must be within the effective dates of this validity period.  

After you create a purchase agreement, you must activate it before it becomes effective. To activate a purchase agreement, set the **Mark agreement as effective** option to **Yes**. 

To prevent your purchase agreement from being used and confirmed, mark the agreement status as **Closed**. You can still update the status to **Effective** any time after making this change.

## Responsible workers on purchase agreements

You can identify a primary responsible worker and secondary responsible worker on the purchase agreement classification. These values will be inherited by the resulting purchase agreement. You're not required to add responsible workers to the purchase agreement, and they can be modified directly on a per case basis on the purchase agreement itself. You can't specify a secondary responsible worker without a primary responsible worker, although you don't have to have a secondary responsible worker. You can't specify the same worker as both the primary and secondary responsible worker.

> [!IMPORTANT]
> To use the responsible party feature, it must be turned on for your system. As of Supply Chain Management version 10.0.25, the feature is turned on by default. As of Supply Chain Management version 10.0.29, the feature is mandatory and can't be turned off. If you're running a version older than 10.0.29, then admins can turn this functionality on or off by searching for the *Purchase agreement responsible party* feature in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

## Commitment types
Each line in a purchase agreement is a commitment to buy something. You can use lines from multiple purchase orders (POs) to fulfill the commitment. There are four types of commitments:

-   **Product quantity commitment** – You purchase a specific quantity of a product.
-   **Product value commitment** – You purchase a specific currency amount of a product.
-   **Product category value commitment** – You purchase a specific currency amount in a procurement category. The amount can be for a catalog item or a non-catalog item.
-   **Value commitment** – You purchase a specific currency amount of any product or products in any procurement category.

## Pricing terms for purchase agreements
Pricing terms can vary, depending on the type of commitment. The pricing terms from purchase agreements override any other pricing terms that are set up for trade agreements. The following table describes the price-related fields that are affected by each commitment type. Fields that contain **Yes** can be updated on an order line.

| Commitment type                   | Unit price | Price unit | Discount percent | Cash discount amount |
|-----------------------------------|------------|------------|------------------|----------------------|
| Product quantity commitment       | Yes        | Yes        | Yes              | Yes                  |
| Product value commitment          |            |            | Yes              |                      |
| Product category value commitment |            |            | Yes              |                      |
| Value commitment                  |            |            | Yes              |                      |

## Policies for purchase agreements
The following policies affect the way that the link between a purchase agreement commitment and the corresponding PO lines works:

-   **Max is enforced** – The total quantity or amount for all order lines can't exceed the quantity or amount that is specified on the related commitment.
-   **Price and discount is fixed** – The price on an order line and the price on the related commitment must be the same. If the price is changed on the order line, the link to the commitment is broken. If the link is broken, the order line doesn't contribute to the fulfillment of the commitment.
-   **Minimum release amount and Maximum release amount** – If an amount is specified, you receive a message if you make any change to an order line that causes the order line to differ from the related commitment.

## Fulfillment calculations for purchase agreements
Fulfillment quantities and amounts are shown on the **Fulfillment** tab on the **Line details** FastTab of the **Purchase agreements** page.  

The **Fulfillment** area shows the remaining amount or quantity that is required to fulfill the commitment.  

The **Agreement** area shows the total quantity or the total amount that the sales agreement line is valid for.  

You can access the PO lines and the invoice lines that contribute to the fulfillment calculation by selecting the **Related information** action on the lines or on the header of a purchase agreement.

## Confirmations and version history for purchase agreements
When you confirm a purchase agreement, the current version of the purchase agreement is stored in a history table. If you change the purchase agreement, you can confirm it again to store another version of the purchase agreement in the history. If you don't confirm a purchase agreement, you can still use it to create POs. However, the history information for the purchase agreement isn't stored. You can preview or print all versions of the agreement. You can then share the revisions with your vendor to obtain approval.

## Applying purchase agreements in the ordering process
When you create a PO, you can apply a purchase agreement to it. Information from the terms for the agreement, such as the payment terms, delivery terms, and delivery address, is then copied to the header of the PO. If the PO contains one or more lines for products or categories that are covered by the agreement, the prices and discounts from the purchase agreement are used for those lines. The amount or quantity on the order line contributes to the fulfillment of the commitment in the purchase agreement. The same PO can include both lines that aren't related to a purchase agreement and lines that have a commitment for a purchase agreement.  

You can select a purchase agreement only when you're creating a PO. You can't select a purchase agreement after the PO has been created.  
In some situations where POs are created indirectly, you can control whetherSupply Chain Management automatically searches for applicable purchase agreements. For example, you might do this when you're automatically firming planned POs or creating POs that are based on sales orders.

## Matching policy on purchase agreements
You can define a line matching policy on the header of the purchase agreement. This line matching policy will respect the accounts payable parameters line matching policy when the **Allow matching policy override** field on the **Accounts payable parameters** page (on the **Price and quantity matching** FastTab) is set to **Higher than company policy**. Documents that reference the purchase agreement will use the line matching policy that's defined on the purchase agreement header unless otherwise defined on the corresponding item, item and vendor, or category purchasing policy.

## Purchase agreements and intercompany trade
Intercompany trading relationships can be created between vendor accounts and customer accounts that are in different legal entities. When a sales order or PO is created for one of the parties, an intercompany order chain is created. In the order chain, the sales order and PO are created in the appropriate legal entities.  

You can create a purchase agreement or sales agreement for one of the intercompany trading parties. You can then generate the corresponding sales agreement or purchase agreement for the other intercompany trading party in the other legal entity.  

If you create an intercompany PO that uses the intercompany purchase agreement in one legal entity, the corresponding intercompany sales order uses the corresponding intercompany sales agreement in the other legal entity. The fulfillment of the sales agreement commitments and the fulfillment of the purchase agreements are synchronized, just as the intercompany sales order and the intercompany PO are synchronized.

## Financial dimensions on purchase agreements
You can copy financial dimensions to document headers or to individual lines of a purchase agreement. If you change the dimensions in the agreement header or on the agreement line, the change doesn't affect any released orders, but it will be reflected on any new orders.

## Additional resources

- [Create a purchase agreement](tasks/create-purchase-agreement.md)
- [Apply a purchase agreement when creating a purchase order](tasks/create-purchase-release-order-purchase-agreement.md)





[!INCLUDE[footer-include](../../includes/footer-banner.md)]