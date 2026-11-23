---
title: Commerce MCP tools for assisted returns (preview)
description: Learn how to use Dynamics 365 Commerce MCP tools to find purchases, prepare returns, refund original cards, and hand off returns to POS.
author: anush6121
ms.topic: article
ms.date: 11/24/2026
ms.author: anvenkat
ms.reviewer: mirao
ms.search.region: Global
ai-usage: ai-generated
ms.custom:
  - bap-template
ms.collection:
  - bap-ai-copilot
---

# Commerce MCP tools for assisted returns (preview)

> [!IMPORTANT]
> Some or all of the functionality noted in this article is available as part of a [preview release](../fin-ops-core/dev-itpro/get-started/supplemental-terms-previews.md). The content and the functionality are subject to change.

**Applies to:** Dynamics 365 Commerce version 10.0.50 and later

The Dynamics 365 Commerce Model Context Protocol (MCP) server provides tools that help an AI agent assist store associates with returns. The agent can find the original purchase, show returnable quantities, collect return reasons, and prepare a priced return cart. After the associate reviews the return with the customer, the agent can refund the original cards or suspend the cart for completion in point of sale (POS).

These tools use existing Commerce return and payment logic. They don't replace the associate's review, grant extra permissions, or provide an unattended self-service return workflow.

## Prerequisites

Before you use the return tools, confirm the following prerequisites:

- A cloud-hosted Commerce Scale Unit (CSU) has Commerce MCP enabled and meets the version requirement in this article. For server enablement, see [Dynamics 365 Commerce MCP server](commerce-mcp.md).
- The agent connects to the store MCP endpoint, `/mcp/store`, with an authenticated Commerce employee identity and activated-register context. Include the `DeviceToken` header for the activated device. A shopper token or an anonymous session doesn't authorize these tools.
- The associate has the required Commerce operation permissions. Purchase lookup checks **Return transaction**, **Suspend transaction**, and **Pay card** permissions before returning purchase details. Cart preparation and refund processing require return permission, and suspension requires suspend permission.
- The associate has an open shift on the calling register before the agent creates a return cart, processes a refund, or suspends an active cart. The tools don't open or reassign shifts.
- The store has the applicable return reasons and receipt number sequences configured. Customer-order returns require configured return-order reasons. Cash-and-carry returns use the register's refund reason configuration.
- The original purchase and payment records are available. The original card payments must support linked refunds, and the channel's tender and return-policy configuration must allow the refund.

> [!IMPORTANT]
> Assign the agent a dedicated register, and serialize operations that allocate receipt numbers on that register. Don't use the same register concurrently from a POS client and an agent, or from multiple agent calls. Receipt number sequences aren't reserved across these callers, so concurrent use can generate duplicate receipt IDs.

The channel, register, and associate context come from the authenticated session. Tool arguments can't select a different channel, register, associate, or shift. Shopper authentication examples in the Commerce MCP server overview aren't a substitute for employee and device authentication.

## Supported scenarios

The tools support receipt-based cash-and-carry returns and invoiced customer-order returns, including an eligible online order returned in store. An associate can return all eligible lines or selected lines and quantities from one original transaction.

In this article, *cash-and-carry* describes the purchase type, not the refund payment method. Refunds through these tools are limited to the original linked card or cards.

| Supported | Not supported through these tools |
| --------- | --------------------------------- |
| Purchase lookup by receipt ID, confirmation number, sales order ID, or invoice ID | Receiptless returns or lookup by an internal transaction ID |
| Full or partial quantities, with configured reasons and subreasons | Combining multiple original transactions in one return |
| Refunds to eligible original cards, including multiple-card purchases | Cash, gift card, store credit, a different card, manually selected tenders, or hardware-station payments |
| Preparing a return and handing it off to POS before refunding | Exchanges that mix sale and return lines |
| Associate-assisted review and confirmation | Manager overrides or unattended self-service returns |

Eligibility results describe the supported Commerce checks. Don't infer an additional return window or a policy exception from the agent's response. If the supported workflow can't handle a return, use the store's POS process and applicable approval procedures.

## Tools at a glance

| Tool | Purpose | Effect |
| ---- | ------- | ------ |
| `find_purchase_for_return` | Find the purchase, returnable quantities, and configured reasons. | Read-only. |
| `create_return_cart` | Validate selected lines and prepare a priced return cart. | Creates or extends a cart. Doesn't refund or post the return. |
| `process_return_refund` | Refund the confirmed amount to the original linked cards and complete checkout. | Moves money and posts the return. Requires confirmation before calling it. |
| `suspend_return_cart` | Suspend a prepared return for POS completion. | Saves a suspended transaction. Doesn't refund or post the return. |

## Associate-assisted workflow

1. Ask the associate for a receipt ID, confirmation number, sales order ID, or invoice ID.
1. Call `find_purchase_for_return`. Show the returned lines, available quantities, and any reasons that a line can't be returned.
1. Collect the selected lines, positive quantities, and applicable reasons. Offer return subreason choices when available. Ask for supplemental input only when the return reason requires it.
1. Call `create_return_cart`. Use its calculated totals rather than estimating a refund from the original purchase.
1. Show the associate the prepared lines, quantities, reasons, currency, refund total, and destination cards. The associate reviews the return with the customer.
1. Select a completion path:
   - **Complete through the agent**: After confirmation, call `process_return_refund` with the returned cart ID and the confirmed refund amount.
   - **Continue in POS**: Before any refund begins, call `suspend_return_cart`. An associate then recalls the transaction from the POS suspended-transactions list and completes it.
1. Report completion only when the tool confirms it. For refund errors, follow the recovery guidance in this article rather than starting a replacement return.

## Find the purchase

Use `find_purchase_for_return` to identify a purchase and discover what can be returned.

### Input

| Parameter | Required | Description |
| --- | --- | --- |
| `orderReference` | Yes | A non-blank receipt ID, confirmation number, sales order ID, or invoice ID, up to 50 characters. It doesn't accept internal transaction IDs. |

The tool checks identifiers in the following order: receipt ID, confirmation number, sales order ID, and invoice ID. If a reference matches multiple receipts or confirmation numbers, ask for a more specific reference. If a sales order has multiple applicable invoices, ask for an invoice ID and search again.

### Result

The result contains `lines` and `reasonCodes`.

| Line field | Description |
| ---------- | ----------- |
| `lineNumber` | Original order line number. Pass this value to `create_return_cart`. Don't use an array position or product ID instead. |
| `name`, `product` | Product identification, with available item, name, and variant information. |
| `returnableQuantity` | Quantity currently eligible for return. A zero means the line isn't returnable. |
| `totalAmount` | Original line total, not a quote for the selected return quantity. This result doesn't include a currency field. |
| `notReturnableReason` | When applicable, `ReturnBlocked`, `Voided`, `NotInvoiced`, or `FullyReturned`. |

Customer-order eligibility is based on invoiced quantities that remain returnable. An invoice-ID lookup returns only lines from that invoice.

Each reason includes `reasonCodeId`, `description`, and `subReasonCodes`. Each subreason has a `subReasonCodeId` and description. A reason that requires supplemental input instead of a subreason can include `inputPrompt`. Use these values to collect the required information; don't invent a reason ID or subreason.

Cash-and-carry lookup can return an empty reason list when no refund reason group is configured. Customer-order lookup fails if return-order reasons aren't configured.

## Prepare the return cart

Use `create_return_cart` after the associate selects the items and reasons. The tool resolves the purchase again and validates the current quantities, reasons, permissions, and payment eligibility.

### Inputs

| Parameter | Required | Description |
| --------- | -------- | ----------- |
| `orderReference` | Yes | The purchase reference used for lookup, up to 50 characters. |
| `lines` | Yes | Between 1 and 100 selected lines, with unique positive `lineNumber` values. |
| `cartId` | No | An existing cash-and-carry return cart ID, up to 100 characters, to add more original lines. Omit it for a new cart or a customer-order return. |

Each entry in `lines` has the following fields:

| Field | Required | Description |
| ----- | -------- | ----------- |
| `lineNumber` | Yes | Original line number returned by purchase lookup. |
| `quantity` | Yes | Positive quantity, no greater than the freshly validated returnable quantity. |
| `reasonCodeId` | When configured | A returned reason ID. Always required for customer-order returns. |
| `subReasonCodeId` | When the reason has subreasons | One of the subreason IDs returned for the selected reason. |
| `reasonCodeInput` | When the reason has an input prompt | Supplemental input, up to 100 characters. |

For example, the following arguments prepare one selected line. The identifiers are illustrative; replace them with values from the actual lookup result.

```json
{
  "orderReference": "RECEIPT-001",
  "lines": [
    {
      "lineNumber": 1,
      "quantity": 1,
      "reasonCodeId": "DAMAGED"
    }
  ]
}
```

### Result and review

The result includes:

- `cartId` and `returnTransactionId`, which identify the prepared cart and original transaction.
- `currencyCode`, which specifies the channel currency used for the calculated return.
- `lines`, including original line numbers, product details, reasons, and positive quantities and amounts.
- `subtotalAmount`, `taxAmount`, and `refundDue`.
- `refundToCards`, which identifies eligible original cards by tender name, card type, and last four digits when available.

Use `refundDue` and `currencyCode` for confirmation. Don't calculate the refund from the lookup result or assume the original order currency is the return currency.

For a cash-and-carry purchase, the tool checks the associate's configured per-line and transaction return amount limits. These amount-limit checks don't apply to customer-order returns.

An existing cash-and-carry cart must be active, unsuspended, owned by the calling register, and free of active tender or sale lines. It must reference the same original transaction, and the requested original lines can't already be present. The tool doesn't change or remove existing return lines. For a customer-order return, submit all selected lines in one new-cart call.

> [!IMPORTANT]
> A cart preparation failure doesn't always mean that no cart was created. For example, `RefundNotCoveredByOriginalPayment` is checked after the cart is written and returns the retained cart ID, refund due, and original-card coverage. Preserve that cart ID and have an associate review the cart in POS. Don't repeatedly create replacement carts.

## Confirm and process the refund

Call `process_return_refund` only after the associate has reviewed the prepared return with the customer and confirmed the amount and original destination cards. This tool can move money.

### Inputs

| Parameter | Required | Description |
| --------- | -------- | ----------- |
| `cartId` | Yes | Prepared return cart ID, up to 100 characters. |
| `expectedRefundAmount` | Yes | Positive, customer-confirmed refund amount. It must match the cart's current total refund amount. |
| `receiptEmail` | No | Valid email address for a receipt, up to 80 characters. |

Use the cart ID and `refundDue` from the successful preparation result. For example, if that result contains `cartId` equal to `RETURN-CART-001` and `refundDue` equal to `49.95`, the arguments are:

```json
{
  "cartId": "RETURN-CART-001",
  "expectedRefundAmount": 49.95
}
```

If `RefundAmountChanged` is returned, review the changed amount and obtain confirmation again before resubmitting. The expected amount is a confirmation guard, not a way to override the refund.

The tool validates the calling register, open shift, return permission, return-only cart contents, required reasons, receipt prerequisites, and original-card coverage before submitting refunds. For eligible multiple-card payments, it distributes the refund across the original refundable cards. The caller doesn't select a replacement tender.

### Result

| Field | Description |
| ----- | ----------- |
| `cartId` | Prepared cart identifier. |
| `isCompleted` | Whether the return checkout completed. |
| `alreadyCompleted` | Whether the tool recognized a previously completed, validated return instead of processing it again. |
| `refundedAmount` | Positive total recorded as refunded. |
| `remainingRefundDue` | Zero for a completed return. |
| `refunds` | Recorded refund details, including tender name, card type, last four digits when available, and positive amount. |
| `returnTransactionId`, `receiptId` | Completed return transaction and receipt identifiers. |

The tool recognizes a validated completed return on a repeated call without issuing another refund. This behavior doesn't make every failed payment call safe to retry. Handle uncertain outcomes as explained in [Handle errors and recovery](#handle-errors-and-recovery).

## Hand off a prepared return to POS

Use `suspend_return_cart` when the associate wants to complete a prepared return in POS instead of refunding through the agent.

The only argument is the prepared `cartId`, a non-blank string up to 100 characters.

```json
{
  "cartId": "RETURN-CART-001"
}
```

An active cart must belong to the calling register, contain only return lines, have an open shift, and have no active tender lines. The associate must have suspend permission.

The result contains `cartId`, `isSuspended`, `suspendedReceiptId`, `refundDue`, and `lineCount`. A successful new suspension confirms the saved suspended state and its journal receipt. An already-suspended cart returns its existing summary without another suspension. A legacy suspended cart that has no journal receipt can return a null `suspendedReceiptId`.

After confirmed suspension, the associate can use the POS suspended-transactions list to recall and complete the return. This tool doesn't resume a cart, process a refund, or provide receipt-barcode recall. A suspended transaction receipt isn't a completed-return receipt.

Don't use suspension as recovery after a refund has started. You can't suspend carts with active tender lines through this tool.

## Handle errors and recovery

Error codes use the `Microsoft_Dynamics_Mcp_` prefix. The following tables omit the prefix for readability.

### Lookup, preparation, and handoff

| Error | Recommended action |
| ----- | ------------------ |
| `ReturnRegisterContextRequired` or `AuthenticatedChannelRequired` | Verify employee authentication, channel access, activated-device context, and the device header. Don't substitute a shopper identity. |
| `ReturnPermissionDenied` | Use an authorized associate and the normal POS approval process. The agent can't grant permission or perform a manager override. |
| `ShiftRequired` | Open or resume the appropriate shift in POS before continuing. |
| `ReturnTransactionNotFound` | Check the customer-visible reference. |
| `OrderReferenceAmbiguous` or `MultipleInvoicesForSalesOrder` | Ask for a more specific reference or invoice ID. Don't choose a transaction automatically. |
| `ReturnPaymentMethodNotSupported` or `ReturnPolicyViolation` | Explain that the return can't be completed through the supported original-card workflow. Use POS for further review. |
| `ReturnLineNotReturnable` or `ReturnQuantityExceedsReturnable` | Refresh eligibility and ask the associate to revise the selection. |
| `ReturnReasonCodesNotConfigured` | Have an administrator configure customer-order return reasons before retrying. |
| `ReasonCodeRequired`, `SubReasonCodeRequired`, or `ReasonCodeInputRequired` | Collect the missing value from the returned reason configuration. |
| `RefundNotCoveredByOriginalPayment` | Save the cart ID from the error and have an associate review the retained cart in POS. |
| `CartOnAnotherTerminal` | Suspend from the owning register, or use the POS process to transfer the workflow. Don't override terminal ownership. |
| `CartHasTenderLines` | Review the cart and any payment activity in POS. Don't suspend it or create a replacement refund automatically. |
| `SuspendReturnCartOperationFailed` | Check the saved cart state in POS before another attempt. The failed call didn't confirm a usable suspension. |
| `FindPurchaseForReturnOperationFailed` | Treat the result as an operational failure, not proof that the purchase doesn't exist. Verify connectivity and retry lookup when appropriate. |

Preparation errors after a write can leave an empty or partially modified cart. Preserve any returned cart identifier for review rather than assuming rollback.

### Refund outcomes

> [!WARNING]
> Don't place `process_return_refund` in an unconditional retry loop. A failed or timed-out payment call can have an unknown financial outcome. Don't create a second return cart or issue a replacement refund to work around that outcome.

| Error | Meaning and recommended action |
| ----- | ------------------------------ |
| `RefundStatusUnknown` | The refund might have reached the payment processor, but its result couldn't be confirmed. Stop automated refund attempts. Have an associate reconcile payment status through the store's payment-support process before taking further financial action. |
| `ReturnCheckoutFailedAfterRefund` | A refund is recorded, but checkout didn't complete. Keep the same cart. A controlled retry on that cart can finish checkout without repeating recorded refunds; don't create another return. |
| `RefundIncompleteAfterPartialRefund` | Part of the refund is recorded, and a later refund was rejected. Show the recorded amount and have an associate finish the remaining work in POS. Repeating the same rejected request isn't the recovery path. |
| `ReturnCheckoutStatusUnknownAfterRefund` | A refund is recorded, but checkout status couldn't be confirmed. A single controlled retry on the same cart can recognize a completed return or finish checkout without repeating recorded refunds. If the result remains unresolved, stop and investigate. |

For a `DownstreamOperationFailed` response, follow the returned Commerce validation message. Don't treat an error as successful completion or hide it from the associate.

## Validate the integration

Before you deploy the agent to stores, validate the workflow in a test environment with your configured payment connector:

1. Find and prepare both a cash-and-carry return and an invoiced customer-order return. Include an eligible online order returned in store.
1. Verify partial quantities, already-returned items, configured reasons and subreasons, permissions, and cash-and-carry amount limits.
1. Confirm that the agent displays the calculated currency, amount, and destination cards before requesting refund approval.
1. Complete single-card and multiple-card refunds. Verify the persisted return receipt, payment records, and channel and headquarters reporting.
1. Suspend a tender-free prepared return, recall it through POS, and verify that the lines, reasons, and original-card refund information are retained.
1. Verify that uncertain payment responses stop automated refund attempts and that recovery preserves the original cart.
1. Verify receipt numbering with the dedicated agent register and check whether refund and suspension activity appears as expected in X/Z reports.

## Version history

| Version | Enhancements |
| ------- | ------------ |
| 10.0.50 | Purchase lookup, return-cart preparation, original-card refund processing, and return-cart suspension for associate-assisted workflows. |

## Related information

- [Dynamics 365 Commerce MCP server](commerce-mcp.md)
- [POS returns](POS-returns.md)
