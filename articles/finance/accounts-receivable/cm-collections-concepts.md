---
title: Collections management key concepts
description: Learn about key concepts for collections management, including overviews on customer aging snapshots, collections customer pools, and collections pages.
author: JodiChristiansen
ms.author: kweekley
ms.topic: concept-article
ms.date: 07/28/2026
ms.custom:   
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom:
ms.search.form:
ms.dyn365.ops.version: 
---
# Collections management key concepts

[!include [banner](../includes/banner.md)]

Before you start to set up or work with collections, make sure you understand the following concepts:

- Customer aging snapshots contain aged balance information at a specific point in time.
- Collections customer pools help you organize your work.
- Collections agents can have their own customer pools.
- List pages organize collections customers, activities, and cases.
- All collections information for a customer is on one page, and you can take action from that page.
- You can waive, reinstate, or reverse interest and fees in one step.
- You can create write-off transactions in one step.
- You can process not sufficient funds (NSF) payments in one step.

This article describes each concept.

## Customer aging snapshots

An aging snapshot contains the calculated aged balances for a customer at a specific point in time. You see this information on the **Aged balances** list page and the **Collections** page. You must create an aging snapshot before you can view information on the collections list pages (**Aged balances**, **Collections activities**, and **Collections cases**).

For each customer, an aging snapshot has an aging snapshot header and detail records that correspond to each aging period in the aging period definition.

The aging snapshot header contains the total amount that is due, credit limit, packing slip amount, sales order amount, number of disputed transactions, and total amount of the disputed transactions for the customer account. The calculation of these amounts includes all transactions for the customer. The **Credit information** FactBox on the **Collections** page shows the total amount that is due, credit limit, packing slip amount, and sales order amount.

For each aging period in the aging period definition, the aging snapshot includes a detail record. Each detail record contains the ID of the aging period and the total amount of the transactions that have dates in the aging period. You assign transactions to an aging period, such as 30 days past due. The date is relative to the **Aging as of** date value that you specify when you create the aging snapshot. You see this information on the **Aged balances** list page and in the **Aged balances** FactBox on the **Collections** page.

## Collections customer pools

Customer pools are queries that define a group of customer records. Use these grouped records to view information for the customer accounts that are included, and to manage collections or aging processes for them. Use customer pools to filter information on the collections list pages. You can also use them to filter the customer accounts that are included when aging snapshots are created.

## Collections agents

By default, users can view all customer information on the collections list pages. Collections agent records let you determine the customer pools that can be used to filter information on the collections list pages and the **Collections** page.

Collections agents work with customers to make sure that payments are collected in a timely manner. They're workers who are assigned to users on the **User setup** page.

## Collections list pages

The following list pages help you organize collections information:

- **Aged balances** – The columns on this list page show customer balances and aged amounts by aging period. This information is stored in an aging snapshot. The aging periods are determined by the aging period definition that is used. The aging period definition comes from the customer pool, if you specify a customer pool for the pool query. If the pool doesn't have an aging period definition, the default aging period definition that you specify on the **Accounts receivable parameters** page is used. If you don't specify a default aging period definition, the first aging period definition on the **Aging period definitions** page is used.
- **Collections activities** – The columns on this list page show activities that are identified as collections activities. You create these activities on the **Collections** page. Use activities to track the collections-related work that you do.
- **Collections cases** – The columns on this list page show information for cases that belong to a case category that has a case type of **Collections**.

### Aging snapshots

You must create an aging snapshot before you can view information on the collections list pages. The system shows information only for customers that an aging snapshot exists for. You can filter the records that are shown on the list page, as described in the following list:

- By default, users have access to all customers who have an aging snapshot.
- If customer pools exist, set up a user as a collections agent to use the pools to filter information on the collections list pages. Information is limited to the customers who are included in the selected customer pool.
- If you set up a user as a collections agent, only the pools that you select for that collections agent are available on the collections list pages. If you select the **Allow agent to view all customer pools** option on the **Collections agent** page for the collections agent, all pools are available for that agent.

## Collections page

Use the **Collections** page to view, manage, and take action on collections information, activities, and cases for a customer.

The upper section of the page shows cases for the selected customer, the middle section shows transactions for the customer, and the lower section shows activities for the customer. You can create collections cases to track collections information for one or more transactions and activities. You can filter the information in the upper and lower sections by case.

FactBoxes show aged balances and credit limit information for the selected customer. The aging snapshot stores this information. As you require, you can update the aging snapshot with current information.

The Action Pane contains buttons that you use to view related information for the selected customer, case, transaction, or activity. You can also perform common actions, such as changing the collections status of a transaction, sending email through the integration with your email provider, reimbursing customers, processing NSF payments, and writing off uncollectible balances.

## Waiving, reinstating, or reversing interest and fees

You can waive, reinstate, or reverse whole interest notes, or the fees and transaction interest that are part of interest notes. On the **Collect** tab on the Action Pane of the **All customers** list page, select **Interest note**, **Transaction interest**, or **Fee**.

These adjustments affect only interest notes, and the interest and fees that they include. For information about how to write off all the charges that a customer owes, see the [Creating write-off transactions](#creating-write-off-transactions) section of this article.

For more information, see Create an interest code with a range and Process interest.

## Creating write-off transactions

You can write off bad debts by selecting **Write off** on the **Collections** page and the collections list pages.

When you write off transactions for a customer, the system automatically marks all transactions for that customer for settlement. The amount that you write off depends on the net amount of the marked transactions. You create the write-off transaction in a general journal and it can contain up to three types of journal lines:

- The first type of journal line contains the customer write-off entry. If the marked transactions contain multiple combinations of currency codes, dimensions, and posting profiles, you create a separate journal line for each combination.
- The second type of journal line contains the general ledger write-off entry. If the marked transactions contain multiple combinations of currency codes, dimensions, and posting profiles, you create a separate journal line for each combination.
- The third type of journal line contains the general ledger write-off information for sales taxes. You create this journal line only if you select the **Separate sales tax** option on the **Accounts receivable parameters** page. If the marked transactions contain multiple combinations of sales tax payable accounts, dimensions, and sales tax codes, you create a separate journal line for each combination. You create the write-off transaction in the transaction currency. For more information, see Create a write-off journal for a customer.

## Process NSF payments

You can process NSF payments by selecting **NSF payment** on the **Collections** page. When you select this option, the payment is canceled. If an NSF fee applies for the customer, the system creates a charge transaction in a payment journal. The amount of the fee is based on the settings for the automatic charges. The charges group that you select on the **Bank accounts** page for the affected bank account specifies the automatic charges that apply to NSF payments.

## Additional resources

[Customer credit management parameters setup](./cm-credit-mgmt-setup.md)

[Customer credit management setup information](./cm-setup-information.md)

[Add credit management information for a customer](./cm-add-credit-mgmt-information-customer.md)

[Customer credit groups](./cm-customer-credit-groups.md)

[Customer credit limit adjustments](./cm-credit-limit-adjustments.md)

[Credit holds for sales orders](./cm-sales-order-credit-holds.md)

[Customer credit management periodic tasks](./cm-periodic-tasks.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
