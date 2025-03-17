---
title: Collections coordinator workspace
description: Learn about the Collections coordinator overview and workspace, including the aged balances and customer timeline summary.
author: JodiChristiansen
ms.author: jchrist
ms.topic: conceptual
ms.date: 01/17/2025
ms.reviewer: twheeloc
ms.collection: bap-ai-copilot 
audience: Application User
ms.search.scope: Core, Operations
ms.search.region: Global
ms.search.validFrom: 2023-06-05
ms.search.form:
ms.dyn365.ops.version: 10.0.34  
---

# Collections coordinator workspace


Collections coordinators (collections agents) have the daily task of contacting customers who have overdue balances. Before they contact a customer, they must know the customer's aged balances, the last payment that was received, outstanding invoice amounts, and many other data points. In the past, collections coordinators (collections agents) had to navigate multiple pages and lookups to find all this information. However, the **Collections coordinator** workspace helps save them time by showing much of this information on one page.

## Enable the Collections coordinator workspace

To enable the **Collections coordinator** workspace, in the **Feature management** workspace, search for and select **Collections coordinator workspace**. Then select **Enable**.

## Overview of the Collections coordinator workspace

The **Collections coordinator** workspace shows collections coordinators (collections agents) relevant collection information for their customers. If a collections coordinator is set up as a collections agent who has a default collection pool, the collection pool is automatically entered in the **Pool** field.

The **Customer account** list is restricted to customers in the collections coordinator's (collections agent's) assigned collection pool. If you aren't using pools, all customers are available for selection in the **Customer account** list. After a customer is selected, the page will only display information for that customer. 

In Dynamics 365 Finance version 10.0.39, a new landing page was added for the Collections coordinator workspace called **Collections coordinator overview**. This new landing page is designed to help the collections coordinator focus on the activities that are assigned to them and display the customers that have the highest balances and the most aged balances in the other grids. Depending on what balances are the most important, the collections coordinator can get all relevant details so they can decide which customers need the most attention. Selecting the **Customer name** in any grid brings you to the existing **Collections coordinator workspace** that was updated in this version. Alternatively, when a customer account is selected at the top of the page, select **View customer details**. Select the **Customer account** to drill down the **Customers** page. 

## Collections coordinator overview 

Each grid is independent of the others but will only display customers from the Pool if one is selected. The activities assigned to the collections agent (as the Responsible field shows) are in the top grid sorted by oldest end date. Hover over the Purpose field and select More to open the Activity details. Any activity can be closed by highlighting one or more lines and then selecting the Close activity link above the grid. Enter a new activity using the **New activity** option above the grid. The Highest balances grid displays the top 100 customers with the highest outstanding balances along with the Credit limit, Credit available and Risk score. The grid can be displayed by any column by selecting the column and using the sort and filter options. The Aged balances grid shows the customers that have the oldest aged balance along with the Customer credit group and Account status columns. The grid can be sorted by any column by selecting the column and using the sort and filter options. 

## Collections coordinator workspace 

This page was updated in version 10.0.39 to have separate tabs for Open transactions, Disputed inovices, Promised to pay and Unsettled payments. The **Overview** tab shows the AI-generated text if the **Collections coordinator summary feature** is enabled. The **Create reminder email** button drafts an AI-generated email. For more information, see [Collections coordinator summary](collectionscoordinatorsummary.md) page. The aged balances chart shows the aging bucket summary of current and overdue amounts.

The **Open transactions** tab shows the customer transactions that haven't been fully settled. Collections options on this page include **Change status**, **NSF payment**, **Write-off**, **Settle**, **Reprint**, and **View collections history**. These options are the same options that are available on the [View customer collections details](tasks/review-collections-information.md#view-aged-customer-balances) page. For clarity, the **Due date** column has been added for transactions. The **Disputed invoices** tab shows any open transactions where the collections status has been updated to Disputed. The **Promised to pay** tab shows any open transactions where the collections status has been updated to Promised to pay. The **Unsettled payments** tab shows any payments for the customer that have been posted but not settled against an invoice. 

## Customer timeline

The **Customer timeline** section shows posted invoices, payments that have been received, collection letters that have been sent, and activities.  Use the activity type drop down list to filter the list to specific activity types. The most recent transactions are shown first and are limited to the last year (365 days) of transactions. The information that's shown depends on the type of transaction. Hover over any transaction to view more details about it.

- For invoices, the posted date, invoice number, transaction currency amount, and due date are shown. Hover to use the invoice number to drill back to the invoice journal.
- For received payments, the posted date, voucher number, and transaction currency amount are shown. Hover to use the voucher number to drill back to the customer transactions.
- For collection letters, the posted date, collection letter number, collection letter sequence, and collection letter amount together with the currency are shown. Hover to use the collection letter number to drill back to the collection letter journal and view the fee amount.
- For activities (tasks, appointments, events, and actions) the category, end date/time, type, and person who's responsible are shown. If a note was entered, **User memo included** is shown. Hover over the entry to view the complete note, use the activity number to link back to the activity, and view the start date, purpose, and closed status.

## Contact details

To quickly contact a customer, use the **Contact details** information at the bottom of the page. The **Collections contact** value is taken from the **Credit and collections** tab of the customer record. The **Other contact** displays the first contact for the customer when contacts are viewed. Use the **Email** button to start a blank email directly to the customer contact. Use the phone symbol to call the customer in Microsoft Teams, for example.

The customer's organization contact information is listed for easy reference. The **Internal team** information includes the primary contact and the person who's specified in the **Employee responsible** field on the **Sales demographics** tab of the customer record.
