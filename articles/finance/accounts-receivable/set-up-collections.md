---
title: Set up collections
description: Learn how to set up the collections functionality, including an overview on setting up aging period definitions.
author: JodiChristiansen
ms.author: jchrist
ms.topic: article
ms.date: 08/05/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: CustCollectionsActivitiesListPage
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: dcc6da2f-9af5-4f1d-abaa-b72967b66979
---

# Set up collections

[!INCLUDE [banner](../includes/banner.md)]

This article explains how to set up the collections functionality. You must complete some setup steps when using the collections capability. Some optional capabilities include customer pools and collections teams.

- Aging period definitions
- Aging snapshots
- Journal names
- Reason code for writeoff transactions
- Collections agents
- Writeoff account
- NSF (not sufficient funds) information
- Outlook settings for those who use the **Collections** page
- Email addresses

The rest of this article discusses these points in more detail.

## Set up aging period definitions

Set up an aging period definition. An aging period definition defines the columns that appear on the **Aged balances**, **Collections activities**, and **Collections cases** list pages. It also defines the periods that appear on the **Collections** page. If you set up a customer pool, the aging period definition for the pool is used. If you don't set up pools, the default aging period definition that you specify on the **Accounts receivable parameters** page is used. If you don't specify a default aging period definition, the first aging period definition on the **Aging period definitions** page is used.

## Create an aging snapshot

Create aging snapshot records for all customers or for the customers in a customer pool. Aging snapshot information appears on the **Aged balances** list page and on the **Collections** page. You must create an aging snapshot before you can use the list page. The list page shows information only for customers that an aging snapshot is created for.

## Optional: Set up customer pools

Set up customer pools to represent groups of customers. Use customer pools as filters for the customer information that appears on **Collections** list pages, on the **Collections** page, or when you create aging snapshots.

## Optional: Create a collections team

If multiple people in your organization handle collections work, set up a collections team. Select the team on the **Accounts receivable parameters** page. If you don't create a collections team, the system automatically creates a team when you set up collections agents on the **Collections agent** page.

## Set up a collections case category

To use cases to organize your collections work, set up a case category that has the **Collections** category type. Set up this category only if you want to use the case functionality on the **Collections** page.

## Set up journal names (settlement, writeoff, and NSF)

Set up the journal names that the system uses when it processes transactions on the **Collections** page. This processing includes settling a transaction, writing off a transaction, and processing a not sufficient funds (NSF) payment.

| Description | Journal type     |
|-------------|------------------|
| Settlement  | Customer payment |
| Write-off   | Daily            |
| NSF         | Customer payment |

## Set up a reason code for writeoff transactions

Set up the default reason code that the system uses when it writes off transactions on the **Collections** page. You can change the code during the write-off process.

## Set up a folder for email attachments and create email templates

If you send email messages from the **Collections** page that have Microsoft Excel attachments, you can create optional email templates for those messages.

## Set up accounts receivable parameters for collections

Set up the accounts receivable parameters that appear on the **Collections** tab.

## Optional: Set up collections agents

If multiple people in your organization handle collections work, set up collections agents. A collections agent is a worker who you set up as a user on the **User relations** page. Assign customer pools (customer queries) to collections agents to help them organize their work. Add the collections agents to the team that you select on the **Accounts receivable parameters** page. If you don't select a team on that page, the system automatically creates a new team named **Collections** and adds the collections agents to that team.

## Set up a write-off account

Set up the write-off account that the system uses for the general ledger write-off entry when you write off a transaction. Store this account on the customer posting profile.

## Set up NSF information for bank accounts

Update bank accounts so that they have the correct journal when the system identifies NSF payments on the **Collections** page. On the **Currency management** tab, in the **NSF payment journal** field, select a payment journal.

## Set up Outlook settings for users of the Collections page

Before workers can create activities or send email messages by using the **Collections** page, verify that the **Microsoft Outlook synchronization** configuration key is selected, and that Outlook synchronization is set up for those workers.

## Set up email and addresses

Use email to communicate with both customers and salespeople about collections issues. Send email messages from the **Collections** page.

### Set up email and address settings for collections customer contacts

Set up email addresses for customer contacts so you can send email messages to those contacts from the **Collections** page. The collections contact is the default contact on the **Collections** page. Set up a statement address for a customer if statements should use an address other than the primary address.

On the **Credit and Collections** FastTab for a customer, in the **Collections contact** field, select the person in the customer organization who works with your collections agent. This person is the default contact on the **Collections** page, and email messages are sent to them.

> [!NOTE]
> If you don't specify a collections contact for a customer, the primary contact for the customer is used. If you don't specify a primary contact, email messages are sent to the first address that is listed on the **Contacts** page.

### Set up email settings for salespeople

Set up email addresses for salespeople so they can send email messages to salespeople from the **Collections** page. Set up an email address for each sales representative in each commission sales group. The sales representative who has the **Contact** option selected is the default salesperson that email messages are sent to.

If you don't specify a sales representative, the primary salesperson for the customer organization is used. If you don't specify a primary salesperson, email messages go to the first salesperson listed on the page.

For more information, see the following articles:

- [Create a collection letter sequence](tasks/create-collection-letter-sequence.md)

- [Process collection letters](tasks/process-collection-letters.md)

- [Review collections information](tasks/review-collections-information.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
