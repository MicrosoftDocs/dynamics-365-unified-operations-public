---
# required metadata

title: Collections coordinator workspace
description: This article describes the Collections coordinator workspace, including the aged balances and customer timeline summary.
author: JodiChristiansen
ms.date: 06/04/2023
ms.topic: conceptual
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 539093
ms.search.region: Global
# ms.search.industry: 
ms.author: jchrist
ms.search.validFrom: 2023-06-05
ms.dyn365.ops.version: 10.0.34

---

# Collections coordinator workspace

> [!NOTE]
> Some or all of the functionality that's mentioned in this article is available as part of a preview release. The content and the functionality are subject to change.

Collections coordinators (collections agents) have the daily task of contacting customers who have overdue balances. Before they contact a customer, they must know the customer's aged balances, the last payment that was received, outstanding invoice amounts, and many other data points. In the past, collections coordinators (collections agents) had to navigate multiple pages and lookups to find all this information. However, the **Collections coordinator** workspace helps save them time by showing much of this information on one page.

## Enable the Collections coordinator workspace

To enable the **Collections coordinator** workspace, in the **Feature management** workspace, search for and select **(Preview) Collections coordinator workspace**. Then select **Enable**.

## Overview of the Collections coordinator workspace

The **Collections coordinator** workspace shows collections coordinators (collections agents) relevant collection information for their customers. If a collections coordinator is set up as a collections agent who has a default collection pool, the collection pool is automatically entered in the **Pool** field.

The **Customer account** list is restricted to customers in the collections coordinator's (collections agent's) assigned collection pool. If you aren't using pools, all customers are available for selection in the **Customer account** list. After a customer is selected, the header of the workspace shows the customer's name together with their credit rating in Microsoft Dynamics 365 Finance, a summary of their payment history, and their overdue balance as of 60 days ago. If this information isn't available in Finance, the header doesn't show it.

The **Overview** tab shows the customer account details. Details include the aged balances and other customer data points in Finance that are relevant to the customer's credit and open transactions. The aged balances chart shows the aging bucket summaries of current and overdue amounts.

The following data points are shown for the selected customer:

- **Open contracts** – The number of active project contracts from the **Project management and accounting** module.
- **Open invoices** – The total number of invoices that haven't been fully settled.
- **Months as a customer** – The number of months that the customer has been a customer. The value is calculated from the **Customer since** field on the **Credit and collections** tab of the customer record.
- **Credit limit** – The customer's credit limit.
- **Credit remaining** – The customer's remaining credit amount. The value is calculated during the **Age customer balances** periodic process.
- **Account status** – The account status. The value is taken from the **Account status** field on the **Credit and collections** tab of the customer record.

The **Open transactions** tab shows the customer transactions that haven't been fully settled. Collections options on this page include **Change status**, **NSF payment**, **Write-off**, **Settle**, **Reprint**, and **View collections history**. These options are the same options that are available on the [View customer collections details](tasks/review-collections-information.md#view-aged-customer-balances) page. For clarity, the **Due date** column has been added for transactions.

## Customer timeline

The **Customer timeline** section shows posted invoices, payments that have been received, collection letters that have been sent, and activities. The most recent transactions are shown first and are limited to the last year (365 days) of transactions. The information that's shown depends on the type of transaction. Hover over any transaction to view more details about it.

- For invoices, the posted date, invoice number, transaction currency amount, and due date are shown. Hover to use the invoice number to drill back to the invoice journal.
- For received payments, the posted date, voucher number, and transaction currency amount are shown. Hover to use the voucher number to drill back to the customer transactions.
- For collection letters, the posted date, collection letter number, collection letter sequence, and collection letter amount together with the currency are shown. Hover to use the collection letter number to drill back to the collection letter journal and view the fee amount.
- For activities (tasks, appointments, events, and actions) the category, end date/time, type, and person who's responsible are shown. If a note was entered, **User memo included** is shown. Hover over the entry to view the complete note, use the activity number to link back to the activity, and view the start date, purpose, and closed status.

## Contact details

To quickly contact a customer, use the **Contact details** information at the bottom of the page. The **Collections contact** value is taken from the **Credit and collections** tab of the customer record and is the first contact for the customer when contacts are viewed. Use the **Email** button to start a blank email directly to the customer contact. Use the phone symbol to call the customer in Microsoft Teams, for example.

The customer's organization contact information is listed for easy reference. The **Internal team** information includes the primary contact and the person who's specified in the **Employee responsible** field on the **Sales demographics** tab of the customer record.
