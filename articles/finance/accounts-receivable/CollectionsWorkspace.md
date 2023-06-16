---
# required metadata

title: Collections coordinator workspace
description: This article describes the Collections coordinator workspace including the aged balances and customer timeline summary. 
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
> Some or all of the functionality noted in this article is available as part of a preview release. The content and the functionality are subject to change. 

Collections coordinators (collections agents) have the daily task of contacting customers with overdue balances. Before they contact their customers, they need to know information like the aged balances, last payment received, outstanding invoice amounts and many other data points. Finding this information requires navigating multiple screens and lookups. With the **Collections coordinator** workspace, much of that information is displayed in one page, saving them time by not having to search in multiple places. 

## Enable the Collections coordinator workspace
To enable the **Collections coordinator** workspace, go to **Feature management**. In the **Feature management** workspace, search for **(Preview) Collections coordinator workspace** and select **Enable**.

## Overview
The **Collections coordinator** workspace displays information for a collections coordinator (collections agent) looking for relevant collection information for their customers. If the collections coordinator is set up as a collections agent with a default collection pool, the collection pool will default into the **Pool** field. The **Customer account** list is restricted to customers in their assigned pool. If you're not using pools, then the **Customer account** selection displays all customers. Once selected, the workspace displays the customer name along with their credit rating in Dynamics 365 Finance, payment history summary and overdue balance as of 60 days ago. If this information is not available in Dynamics 365 Finance, the header won't display it. 

The **Overview** tab displays the customer account details including the aged balances and other customer data points in Dynamics 365 Finance relevant to their credit and open transactions. The aged balances chart displays the aging bucket summaries of current and overdue amounts. 

The selected customer data points displayed include:
 - **Open contracts** which are the number of active project contracts from the Project management and accounting module
 - **Open invoices** which is the total number of invoices that have not been fully settled
 - **Months as a customer** is calculated from the **Customer since** field on the **Credit and collections** tab on the customer record
 - **Credit limit** displays the customer's remaining credit amount calculated during the **Age customer balances** periodic process
 - **Credit remaining** displays the customer's remaining credit amount calculated during the **Age customer balances** periodic process
 - **Account status** displays the **Account status** from the Credit and collections tab on the customer record

The **Open transactions** tab displays the customers' transactions that haven't been fully settled. Collections options on this page include **Change status**, **NSF payment**, **Write-off**, **Settle**, **Reprint** and **View collections** history. These are the same options available from the [View customer collections details](tasks/review-collections-information#view-aged-customer-balances) page. The **Due date** column has been added for clarity on transactions. 

## Customer timeline
The **Customer timeline** displays posted invoices, payments received, collection letters sent and activities. The most recent transactions are first and are limited to the last year (365 days) of transactions. The information displayed depends on the type of transaction. Hover over any of the transactions to view more details. 

 - For invoices the posted date, invoice number, transaction currency amount and due date are displayed. Hover to use the invoice number to drill back to the Invoice journal. 
 - For payments received the posted date, voucher number, and transaction currency amount and are displayed. Hover to use the voucher number to drill back to the customer transactions. 
 - Collection letters show the posted date, collection letter number, collection letter sequence, and collection letter amount with currency. Hover to use the collection letter number to drill back to the collection letter journal and view the fee amount.
 - Activities (tasks, appointments, events and actions) display the category, end date/time, type and person responsible. If a note was entered, you see **User memo included** and there's more text available if you hover over the entry. Hover to see the complete note, use the activity number to link back to the activity, view the start date, purpose and closed status.  

## Contact details
To quickly contact a customer, use the **Contact details** information at the bottom of the page. The **Collections contact** is displayed (from the **Credit and collections** tab on the customer record) and the first contact for the customer when viewing contacts. Use the **Email** button to start a blank email directly with the customer contact. Use the phone icon to call the customer if using Microsoft Teams, for example. The customer's organization contact information is listed for easy reference. The **Internal team** includes the primary contact and the **Employee responsible** on the **Sales demographics** tab on the customer. 
