---
title: Use financial tags in procurement documents
description: Learn how financial tags work across procurement documents, including purchase requisitions, purchase orders, purchase agreements, and requests for quotation.
author: Neeraj-Gandhi
ms.author: neerajgandhi
ms.reviewer: kamaybac
ms.search.form: FinTagConfiguration, PurchReqTable, InventJournalOwnershipChange, PurchTable, PurchAgreement, PurchRFQCaseTableListPage, InventJournalOwnershipChange
ms.topic: how-to
ms.date: 07/29/2026
ms.custom:
  - bap-template
---

# Use financial tags in procurement documents

[!include [banner](../includes/banner.md)]

[Financial tags](../../finance/general-ledger/financial-tag.md) let you attach reporting context to procurement transactions. They help you track the business purpose behind purchases throughout the procurement lifecycle. For example, a company could tag all purchases related to an employee onboarding initiative, making it easy to find and analyze the associated spending later—without relying on document descriptions or manual tracking.

You can use financial tags across procurement documents, including purchase requisitions, purchase orders, purchase agreements, requests for quotation (RFQs), and inventory ownership change journals. Because financial tag values flow through the process from one document to the next (for example, from a purchase requisition to a purchase order), you can maintain consistent reporting context across the entire procurement lifecycle.

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.49 or later.
- The feature named *Enable financial tags for purchase order invoicing* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## How financial tags work in procurement

Financial tags in procurement follow the same general principles across all document types. Understanding these common behaviors helps you use tags consistently.

### Header and line behavior

You can enter financial tag values on both document headers and document lines. The following rules apply across all procurement document types:

- Line-level tag values are the source of truth. A line-level change doesn't flow back to the header.
- When you add new lines, the header tag value can default to the line. However, a blank header value doesn't overwrite an existing line value—only populated header fields cascade to lines.
- Users can override financial tag values directly on individual lines, which allows different lines within the same document to carry different reporting context.

### Tag propagation between documents

When one procurement document creates another document (for example, when you release a purchase requisition to a purchase order), financial tag values flow from the source document's lines to the target document's lines. The following rules apply:

- Tag propagation is always line-to-line. The source document's line-level tags are the primary source.
- If the source document has a single line, the target document's header can also receive the same tag value. If the source has multiple lines with different tag values, the target document's header remains blank to avoid ambiguity.
- Changing financial tags on a source document doesn't change documents that you already created from it. Earlier documents preserve the tag values that existed when they were created.

### Editability

The following rules determine when you can edit financial tag values on procurement documents:

- You can edit financial tags while a document is in a draft or editable state.
- When a document enters a workflow for approval, the system typically locks the tags. Depending on the workflow configuration, the approver might be able to update them during review.
- After you post a document, its financial tag values are read-only.
- On purchase orders that you received but didn't post yet, you can edit financial tags in the same way that you can edit financial dimensions.

## Create financial tags

You can create up to 20 financial tags as needed to meet your business needs. Set up each tag by assigning a name and a value type. The value type might ask users to select from a list of predefined values or allow them to enter free text. When you're working with a relevant procurement document, you can see the available financial tag names and enter values for them as needed. The system stores the tag values with the document and uses them for reporting and analysis.

To create, edit, and activate financial tags, go to **General ledger** > **Chart of accounts** > **Financial tags** > **Financial tags**. Learn more about financial tags and how to set them up in [Financial tags](/dynamics365/finance/general-ledger/financial-tag).

## Financial tags on purchase requisitions

Procurement professionals use financial tags on purchase requisitions to capture the reporting context for each requisition line. When you enter tags here, they flow downstream into purchase orders when you release the requisition.

### Set financial tag values on purchase requisitions

To set financial tag values for a purchase requisition, follow these steps:

1. Go to **Procurement and sourcing** > **Purchase requisitions** > **All purchase requisitions**.
1. Create or open a purchase requisition.
1. On the **Lines** tab of the requisition details page, select or create a line that you want to assign a financial tag to.
1. On the **Line details** FastTab, open the **Financial tags** tab and set the desired financial tag values.

### How financial tags behave on purchase requisitions

The following table describes how financial tags behave in purchase requisition scenarios.

| Scenario | Behavior |
|---|---|
| Entry point | Enter and maintain financial tags on requisition lines. Both item-number lines and procurement-category lines can carry financial tag values. |
| Line-level override | Users can update or add financial tag values directly on requisition lines. A line-level change doesn't update the requisition header and doesn't affect other lines. This behavior allows different requisition lines to carry different reporting context. |
| Workflow and approval | During review, an approver might be able to update the financial tags. After a requisition is recalled to draft, financial tags become editable again. After final approval, they aren't editable. |
| Release to purchase order | When you release an approved requisition (manually or automatically), the purchase order lines receive the financial tag values from the originating requisition lines. |
| Purchase order header outcome | If the requisition has a single line, the purchase order header can receive the same tag value as the requisition line. If the requisition has multiple lines with different tag values, the purchase order header remains blank. |
| Copying requisitions | When you copy a requisition or selected requisition lines, the new requisition lines retain the financial tag values from the source lines. |
| RFQ creation from requisition | When you create an RFQ from a requisition, financial tags are copied to the RFQ header and lines. However, changes made to the RFQ tags don't propagate back to the originating requisition. |

## Financial tags on purchase orders

Financial tags on purchase orders help you track the business purpose of each purchase throughout the order lifecycle, from creation through receipt and invoicing.

### Set financial tag values on purchase orders

To set financial tag values for a purchase order, follow these steps:

1. Go to **Procurement and sourcing** > **Purchase orders** > **All purchase orders**.
1. Create or open a purchase order.
1. To assign financial tags to the purchase order header, open the **Header** tab of the purchase order details page. Then expand the **Financial tags** FastTab and set the desired financial tag values.
1. To assign financial tags to a purchase order line, open the **Lines** tab of the purchase order details page. Then select or create the line that you want to assign a financial tag to. On the **Line details** FastTab, open the **Financial tags** tab and set the desired financial tag values.

### How financial tags behave on purchase orders

The following table describes how financial tags behave in purchase order scenarios.

| Scenario | Behavior |
|---|---|
| Entry point | You can maintain financial tags on both the purchase order header and on purchase order lines. |
| Header-to-line defaulting | Line-level tag values can differ from the header. A line change doesn't flow back to the header. A blank header value doesn't overwrite an existing line value—only populated header fields cascade. |
| Existing lines | For existing purchase order lines, header-to-line updates are controlled by defaulting behavior. A blank header value doesn't overwrite an existing line value—only populated header fields cascade. |
| Line-level override | Users can update or add financial tag values directly on purchase order lines. A line-level change doesn't update the purchase order header and doesn't affect other lines. This behavior allows different purchase order lines to carry different reporting context. |
| From purchase requisition | Purchase order lines inherit financial tags from the linked purchase requisition lines. The purchase order header is populated from the requisition line only when the source requisition has a single line. For multi-line requisitions, the purchase order header remains blank. |
| Copying purchase orders | Copy behavior depends on the copy options. With precise line copy, line tags are copied line by line. With header copy, the purchase order header tag can be copied or overwritten. Without precise or header copy, tags can remain blank. |
| Copying from journals | When copying from confirmation journals, product receipts, or invoices, financial tags follow the same copy-option pattern: precise copy retains line tags, and non-precise header copy can apply header tags to new lines. |
| Version and history views | A confirmed purchase order version shows the tag values that existed at confirmation. Distribution views show the current financial tag values, which might differ if the purchase order was changed after confirmation. |
| Editability after receipt | You can edit tags on a received purchase order before posting, in the same way that you can edit financial dimensions at that stage. Tags on posted journals are read-only. Pending vendor invoice line tags are read-only, consistent with financial dimension behavior. |

## Financial tags on purchase agreements

Financial tags on purchase agreements let you capture agreement-specific reporting context that carries into release orders.

### Set financial tag values on purchase agreements

To set financial tag values for a purchase agreement, follow these steps:

1. Go to **Procurement and sourcing** > **Purchase agreements** > **Purchase agreements**.
1. Create or open a purchase agreement.
1. To assign financial tags to the purchase agreement header, open the **Header** tab of the purchase agreement details page. Then expand the **Financial tags** FastTab and set the desired financial tag values.
1. To assign financial tags to a purchase agreement line, open the **Lines** tab of the purchase agreement details page. Then select or create the line that you want to assign a financial tag to. On the **Line details** FastTab, open the **Financial tags** tab and set the desired financial tag values.

### How financial tags behave on purchase agreements

The following table describes how financial tags behave in purchase agreement scenarios.

| Scenario | Behavior |
|---|---|
| Entry point | You can enter financial tags on purchase agreement headers and lines for different agreement classifications, including bulk purchase, employee purchases, and general purchases. |
| Header-to-line defaulting | Line-level tag values can differ from the header. A line change doesn't flow back to the header. A blank header value doesn't overwrite an existing line value—only populated header fields cascade. |
| Existing lines | For existing agreement lines, header-to-line updates are controlled by defaulting behavior. A blank header value doesn't overwrite an existing line value—only populated header fields cascade. |
| Line-level override | Users can update or add financial tag values directly on agreement lines. A line-level change doesn't update the agreement header and doesn't affect other lines. This behavior allows different agreement lines to carry different reporting context. |
| Release to purchase order | When a release order creates a purchase order, the purchase order receives the financial tag values from the purchase agreement. The line value must be updated on the agreement line for the released purchase order to reflect it. |
| Historical purchase orders | Changing financial tags on a purchase agreement doesn't change purchase orders that you already created from that agreement. Earlier purchase orders preserve the tags that existed when they were created. |

## Financial tags on requests for quotation

Financial tags on requests for quotation (RFQs) help you maintain reporting context while soliciting bids from vendors. Tags flow into the resulting purchase order or purchase agreement when the RFQ is accepted.

### Set financial tag values on RFQs

To set financial tag values for an RFQ, follow these steps:

1. Go to **Procurement and sourcing** > **Requests for quotation** > **All requests for quotation**.
1. Create or open an RFQ.
1. To assign financial tags to the RFQ header, open the **Header** tab of the RFQ details page. Then expand the **Financial tags** FastTab and set the desired financial tag values.
1. To assign financial tags to an RFQ line, open the **Lines** tab of the RFQ details page. Then select or create the line that you want to assign a financial tag to. On the **Line details** FastTab, open the **Financial tags** tab and set the desired financial tag values.

### How financial tags behave on RFQs

The following table describes how financial tags behave in RFQ scenarios.

| Scenario | Behavior |
|---|---|
| Entry point | You can add financial tags on RFQ headers and lines for RFQs created with purchase type *Purchase order* or *Purchase agreement*. Header values can default to lines when you add them. |
| Header-to-line defaulting | Line-level tag values can differ from the header. A line change doesn't flow back to the header. |
| Line-level override | Buyers can change or add financial tag values directly on RFQ lines before the RFQ outcome is accepted. Line changes don't flow back to the RFQ header. |
| Vendor response | Vendors can't edit financial tag values when submitting RFQ responses. Financial tags are buyer-controlled context. |
| After vendor response | The buyer can continue to update financial tags after the vendor submits a response and before the RFQ is accepted. |
| RFQ to purchase order | When an RFQ for a purchase order is accepted, the generated purchase order receives the RFQ financial tag values at both header and line level. After creation, the purchase order follows standard purchase order financial tag rules. |
| RFQ to purchase agreement | When an RFQ for a purchase agreement is accepted, the generated purchase agreement receives the RFQ tag values. |

## Financial tags on inventory ownership change journals

Use financial tags on inventory ownership change journals to capture reporting context for consignment ownership transfers.

### Set financial tag values on inventory ownership change journals

To set financial tag values for an inventory ownership change journal, follow these steps:

1. Go to **Procurement and sourcing** > **Consignment** > **Inventory ownership change**.
1. Create or open an inventory ownership change journal.
1. On the **Lines** tab of the inventory ownership change journal details page, select or create a line that you want to assign a financial tag to.
1. On the **Line details** FastTab, open the **Financial tags** tab and set the desired financial tag values.

### How financial tags behave on inventory ownership change journals

The following table describes how financial tags behave in ownership change journal scenarios.

| Scenario | Behavior |
|---|---|
| Consignment replenishment | Financial tags aren't required when creating a consignment replenishment order or generating the product receipt for that replenishment order. |
| Ownership change journal | Enter financial tags on inventory ownership change journal lines. You can update saved journal lines before posting. |
| After posting | After the inventory ownership change journal is posted, its financial tag values aren't editable. |
| Auto-created purchase order | Posting the ownership change journal can generate a purchase order. The generated purchase order line receives the financial tag values from the journal line. The purchase order header doesn't receive those tags. |
| Purchase order editability | On the generated purchase order, users can add or edit financial tag values on fields that weren't populated by the ownership change journal, subject to normal purchase order editability rules. |
| Product receipt and invoice | Product receipt journal reporting is voucher-oriented rather than requiring editable line-level tags. Invoice line tags are read-only before posting, consistent with financial dimension behavior. |

## General financial tag behaviors

The following table summarizes a few financial tag behaviors that you might not expect, but that are based on intentional design decisions.

| Area | Behavior |
|---|---|
| Product receipt | Product receipt journal carries tags at the voucher level, not per line. |
| Purchase agreements | On header-to-line cascade, a blank header never overwrites an existing line value—only populated fields cascade. |
| Purchase agreements | Editing a purchase agreement's tags doesn't change purchase orders that were already created from it (historical values are preserved). |
| Purchase agreements and RFQs | A line-level tag change never flows back up to the header. |
| Purchase order copy | Copy behavior depends on the `copyHeader` and `copyPrecisely` options (header-only vs. line-precise). |
| Purchase order versions | A confirmed purchase order version shows the tag as of confirmation. View distributions shows the current value. |
| Purchase orders and consignment | Editing tags on a received (pre-posting) purchase order is allowed (same as financial dimensions). Posted-journal tags are read-only. |
| Purchase Requisition | Financial tags are supported for purchase requisition lines but not for purchase requisition headers. |
| Purchase requisition to purchase order | The created purchase order header tag equals the purchase requisition line tag, but only when the requisition has a single line. A multiline requisition leaves the purchase order header tag blank. |
| Purchase requisitions, purchase orders, and purchase agreements | Financial tag header and line behavior mirrors financial dimensions (header cascades to lines; line values are the source of truth). |
| RFQ to purchase requisition | Updated RFQ tags aren't propagated back to the originating purchase requisition. |
| RFQs | Vendors can't edit tags. The buyer can edit tags until the bid is accepted. |

## Related information

- [Financial tags](/dynamics365/finance/general-ledger/financial-tag)
- [Purchase requisition overview](purchase-requisitions-overview.md)
- [Purchase order overview](purchase-order-overview.md)
- [Purchase agreements](purchase-agreements.md)
- [Request for quotations (RFQs) overview](request-quotations.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
