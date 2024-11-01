---
title: Credit limits for customers
description: Access an overview of how credit limits work in Dynamics 365 Supply Chain Management, including answers to questions about checking credit limits.
author: adpattanaik
ms.author: adpattanaik
ms.topic: article
ms.date: 11/16/2023
ms.custom:
ms.reviewer: kamaybac
ms.search.form: CustParameters
---

# Credit limits for customers

[!include [banner](../includes/banner.md)]

Setting a credit limit lets you specify the maximum amount of credit to extend
to your customers. If a credit limit is specified, it's checked automatically
when a user attempts to update a document. If the credit limit is exceeded, a
message is displayed to the user.

> [!IMPORTANT]
> The credit limit functionality described in this article is only available when the *Credit management* feature is *turned off* in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). *Credit management* is on by default and requires blocking rules to be set up to check customer credit limits. For more information about the *Credit management* feature, see [Credit management parameters setup](../../finance/accounts-receivable/cm-credit-mgmt-setup.md).

This article provides an overview of how credit
limits work and answers the following questions:

- What documents and processes can I check credit limits for?
- Where do I configure the way that the customer’s remaining credit is calculated?
- Where is information about a customer’s remaining credit used?
- Where do I specify whether identification is required for credit to be extended to a customer, and also the credit limit amount that requires identification?
- Where do I specify whether to display a warning or error if the credit limit is exceeded?
- How do I specify the credit limit for a specific customer?
- How do I check credit limits manually on sales orders?

## What documents and processes can I check credit limits for?

Use the **Accounts receivable parameters** page to specify which documents to
check credit limits for. You must be a member of the System administrator
(-SYSADMIN-) security role to make changes in this page. You can check credit
limits for the following documents and processes:

- Invoices for sales orders, when you post the invoices
- Packing slips for sales orders, when you update packing slips
- Sales orders, when you add lines in the **Sales order** page
- Sales orders, when they're created through a service
- Free text invoices, when you post the invoices

Credit limits are automatically checked if either of the following options is
set:

- In the **Accounts receivable parameters** page, the **Credit limit type** field is set to anything other than **None**. Credit limits are checked for all customers.

- In the **Accounts receivable parameters** page, the **Credit limit type** field is set to **None** but **Mandatory credit limit** is selected for a customer in the **Customers** page. Credit limits are checked only for specific customers.

To check credit limits for the following documents, you must specify additional settings.

| Document | Additional setting |
|--|--|
| Free text invoice | On the **Accounts receivable parameters** page, in the **Credit rating** area, select **Check credit limit on free text invoice**. |
| Sales order (manually entered) | On the **Accounts receivable parameters** page, in the **Credit rating** area, select **Check credit limit on sales order**. |
| Sales order (electronically received) | On the **Accounts receivable parameters** page, in the **AIF** area, select **Check credit limit for sales orders**. |

## Where do I configure the way that a customer’s remaining credit is calculated?

You can configure Supply Chain Management to calculate a customer’s remaining credit in any of the following ways:

- Compare the credit limit against the customer balance.
- Compare the credit limit against the customer balance and packing slip amounts.
- Compare the credit limit against the customer balance and all open transaction activity. This includes packing slip amounts and sales order amounts.

Use the **Accounts receivable parameters** page to specify the information to
compare to. You must be a member of the System administrator (-SYSADMIN-)
security role to make changes in this page. In the **Credit limit type** field,
select whether to perform credit limit checks and what transaction information
to include when the credit limit is checked. Select from the following options:

- **None** – Don't check credit limits. You can override this option for a specific customer by selecting the **Mandatory credit limit** check box in the **Customers** page. If you do this, the credit limit is checked against the customer balance.
- **Balance** – The credit limit is checked against the customer balance.
- **Balance + packing slip or product receipt** – The credit limit is checked against the customer balance and deliveries.
- **Balance+All** – The credit limit is checked against the customer balance, deliveries, and open orders.

## Where is information about a customer’s remaining credit used?

Information about a customer’s balance and remaining credit amount is calculated
and stored when you create an aging snapshot, and is displayed in the
**Collections** page. The amounts that are displayed in the **Collections** page
might not include all transaction activity until a new aging snapshot is
created. Learn more in [Collections and credit in Accounts
receivable](/dynamicsax-2012/appuser-itpro/collections-and-credit-in-accounts-receivable).

Depending on the documents that are selected, information about a customer’s
balance and remaining credit amount is calculated when sales orders, packing
slips, and customer invoices are updated. If the amount of the document that you're working with would cause the credit limit to be exceeded, a message is
displayed.

## Where do I specify whether identification is required for credit to be extended to a customer, and also the credit limit that requires identification?

Use the **Accounts receivable parameters** page to specify whether to require
identification and the credit limit amount limit that requires identification.
You must be a member of the System administrator (-SYSADMIN-) security role to
make changes in this page.

| Field | Description |
|--|--|
| Require identification with credit | Select the type of identification that must be entered for customers to whom your legal entity extends credit. The option that you select in this field determines when and what type of information is required in the **Government identification** fields on the **Customers** page: <ul><li>*No* – No government-issued identification is required, regardless of the customer's credit limit.</li><li>*Yes* – A government-issued license number or other government-issued identification is required if the customer's credit limit is higher than or equal to zero.</li><li>*Minimum limit* – A government-issued license number or other government-issued identification is required if the customer's credit limit is higher than or equal to the limit that you enter in the **Limit** field in this page.</li></ul> |
| Limit | Enter the credit limit at which a government-issued license number or other identification is required for customers. For example, type 2000 to require that an identification number, such as a driver's license number, must be entered for customers who have a credit limit of 2,000 or higher. This field is available if you selected Minimum limit in the Require identification with credit field. |

## Where do I specify whether to display a warning or error if the credit limit is exceeded?

Use the **Accounts receivable parameters** page to specify whether to display a
warning or error if the credit limit is exceeded. This warning or error is
displayed when a user is entering or posting information, or it's included in a
log if the documents are being processed by an electronic service. You must be a
member of the System administrator (-SYSADMIN-) security role to make changes on
this page.

| Field | Description |
|--|--|
| Message when exceeding credit limit (in the Credit rating area) | Select how messages about credit limits being exceeded are displayed to users. Select from the following options:<ul><li>*Error* – An error message is displayed. This usually stops the current operation and the conflict must be resolved before the process can continue.</li><li>*Warning* – A warning message is displayed, but the process can continue.</li></ul> |
| Message when exceeding credit limit (in the AIF area) | Select how messages about credit limits being exceeded are delivered in a log. Select from the following options:<ul><li>*Error* – An error message is displayed in the **Exceptions** page, and the document won't be processed until the error is resolved.</li><li>*Warning* – A warning message is displayed in the Exceptions page, but the process can continue.</li></ul> |

## How do I specify the credit limit amount for a specific customer?

Use the **Customers** page to specify the credit limit amount for a specific
customer. You must be a member of a security role that has the Maintain customer
master (CustCustomersMaintain) duty assigned to it to make changes in this page.

1. Go to **Accounts receivable** \> **Customers** \> **All customers** and open a customer account.
1. In the **Customers** page, on the Action Pane, select **Edit**.
1. Enter a currency amount in the **Credit limit** field. This value must be higher than zero (0), and will be used as the credit limit amount.
1. If it's required, enter a license number or other government-issued identification in the **Government identification** field.

> [!NOTE]
> In the **Accounts receivable parameters** page, a credit limit type is typically selected. However, if the credit limit type is set to **None**, you must also select the **Mandatory credit limit** check box in the **Customers** page in order to check the customer’s credit limit against the customer’s balance. For more information about credit limit types, see “What documents and processes can I check credit limits for?” in this article.

## How do I manually check credit limits on sales orders?

Sometimes, you might have to manually check a customer’s credit limit. For
example, you might manually check a customer’s credit limit before you start
entering a sales order. You can use the **Sales order** page to manually check
credit limits. You must be a member of a security role that has the Maintain
sales order (SalesOrderMaintain) duty assigned to it to make changes in this
page.

1. Go to **Sales and marketing** \> **Sales orders** \> **All sales orders** and open a sales order.
1. In the **Sales order** page, on the Action Pane, on the **Manage** tab, select **Check credit limit**.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
