---
# required metadata

title: Terminate schedule lines
description: This topic 
author: JodiChristiansen
ms.date: 11/04/2021
ms.topic: article
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
ms.search.validFrom: 2021-11-05
ms.dyn365.ops.version: 10.0.24

---

# Collections coordinator workspace (preview)

Collections coordinators (collections agents) typically need to find various types of information for their customers with overdue invoices. Before they contact their customers, they need to know information like the aging balances, last payment received and outstanding invoice amounts. With the Collections coordinator workspace much of that information is displayed in one page, save you time by not having to search in multiple pages and files. 

The Collections coordinator workspace displays information for a collections coordinator (collections agent) looking for relevant collection information for their customers. If the collections coordinator is assigned a default collection pool it will default in the **Pool** field. The **Customer account** list is restricted to customers in the pool if one is selected. If not using pools then the drop down list for the Customer account displays all customers. Once selected, the workspace displays the customer name along with their credit rating and payment history summary for the last year. 

The Overview tab displays the customer account details including the aging balances and other customer data points in D365 Finance relevant to their credit and open transactions. The aging balances chart displays the aging bucket summaries of the current and overdue amounts. 

The data points displayed include:
Open contracts which is the number of active project contracts from the Project management and accounting module
Open invoices which is the total number of invoices that have not been fully settled
Months as a customer is calculated from the **Customer since** field on the Credit and collections tab on the customer record
Credit limit displays the customer's remaining credit amount calculated during the **Age customer balances** periodic process
Account status displays the **Account status** from the Credit and collections tab on the customer record

The Open transactions tab displays the customers' transactions that have not been fully settled. Collections options on this page include Change status, NSF payment, Write off, Settle, Reprint and View collections history. The Due dat column has been added for clarity on transactions. 

The Customer timeline displays posted invoices, payments received, collection letters sent and closed activities. The most recent transactions are first and is limited to one year's worth of transactions. The information displayed depends on the type of transaction. Posted invoices the posted date, document number, transaction currency amount and due date are displayed. For payments received the posted date, transaction currency amount and document number are shown. Collection letters show the posted date, document number, document amount and collection letter sequence. Activities (tasks, appointments, events and actions) display the end date/time, person responsible and category typ. If a note was entered the words **User memo included** is shown to indicate a note was entered on that activity. Hover over the entry to see the complete note.

To quickly contact a customer, use the Contact details information at the bottom of the page. The **Collections contact** is displayed (from the Credit and collections tab on the customer record) as well as the first contact for the customer when viewing contacts. Use the email button to start a blank email directly with the customer contact. Use the phone icon to call the customer if using Teams, for example. The customer's organization contact information is list for easy reference. The Internal team includes the primary contact and the **Employee responsible** on the Sales demographics tab on the Customer record. 
