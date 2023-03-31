--- 
# required metadata 
 
title: Review collections information
description: This article explains how to review collections information as well as various setup options and collections transactions. 
author: ShivamPandey-msft
ms.date: 03/28/2023
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: CustCollectionsPool, SysQueryForm, CustCollectionsAgent, OMTeamSelectMemberDialog, CustVendReportInterval, CustParameters, CustAgingSnapshot, CustVendAgingBucketLookUp, CustCollectionsPoolsListPage, CustCollectionsContactPart, CustCollections   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Review collections information

[!include [banner](../../includes/banner.md)]

This article explains how to review collections information as well as various setup options and collections transactions. This procedure uses the USMF demo company.

## Create customer pools
1. Go to **Credit and collections > Setup > Customer pools**.
- Use this page to set up customer pools, which are queries that define a group of customer accounts that can be displayed and managed for collections or aging processes. Use customer pools to filter information on the **Collections** list page and on related list pages. You can also use customer pools to filter the customer accounts that are included when aging snapshots are created.  
- You can use customer pools to filter the customer accounts that are included when aging snapshots are created.  
2. Select **New**.
3. In the **Pool ID** field, type a value.
4. In the **Pool description** field, type a value.
5. Click **Select pool criteria**.
6. In the **Criteria** field, type a value.
7. Select **OK**.
8. Select **Preview customer pool**.

## Create collections agents
1. Go to **Credit and collections > Setup > Collections agents**.  
- Use this page to set up workers as collections agents and optionally assign customer pools to them. A *collections agent* is a person who works with customers to make sure that payments are collected in a timely manner.  
- Collections agents that are set up in this page are automatically added to a collections team. If a team is selected in the **Team** field in the **Accounts receivable parameters** page, collections agents are added to that team. If a team isn't selected, a new team named **Collections** is created automatically and the collections agents are added to that team.  
2. Select the desired agent, then select **Add** in the page.
3. In the **Pool ID** field, select the desired record in the drop-down menu.
4. Select or clear the **Default pool** checkbox.
- Select this option to include all customer pools in filter lists for the selected collections agent. If this option isn't selected, only the customer pools that are assigned to the collections agent are available in filter lists.  

## Create aging period definition
1. In the navigation pane, go to **Credit and collections > Setup > Aging period definitions**.
- You can use aging period definitions to analyze the maturity of customer accounts and vendor accounts, based on a date that you enter. Each aging period that you set up for the aging period definition corresponds to a column on the list page or in the page or report when the analysis is performed.  
2. Select **New**.
3. In the **Aging period definition** field, type a value.
4. In the **Description** field, type a value.
- Specify the period name, unit, and interval for each aging period to include in the aging period definition. The line that has 0 (zero) in the **Unit** field represents the date that the analysis is run. Lines before zero will have -1, and lines after zero will have 1 as a default entry in the **Unit** field, but can be changed. Select **Up** and **Down** to rearrange the lines. The 0 (zero) line cannot be moved.  
- Place the pointer where you want to insert a new line and then select **Add**.  
- Select an indicator to represent the aging period in the **Collections** page and list page. For example, you might select a green indicator for a current period, a yellow indicator for a 30-days-past period, and a red indicator for a 90-days-past period.  
- Select the printing direction for the aging period definition. This selection determines the order in which the columns appear on the **Customer aging** report or the **Vendor aging** report.  
  - **Forward** – Print columns in the same order in which the headings appear in the table, starting with the top row.  
  - **Backward** – Print columns in the reverse order in which the headings appear in the table, starting with the bottom row.    

## Setup collections parameters
1. Go to **Credit and collections > Setup > Accounts receivable parameters**.
2. Select the **Collections** tab.
3. Expand or collapse the **Collections defaults** section.
- Select an aging period definition for the default aging snapshot that will be used in the **Collections** form.  
- Select a team that collections agents are assigned to in the **Collections agent** form. Only teams that have a team type of **Collections** are displayed in the list.  
4. Expand or collapse the **Write-off** section.
- Select the journal name, which is set up for daily ledger journals, to use when a transaction is written off by using the **Collections** page or related list pages. 
- Select the default reason code to use when write-off transactions are created by using the **Collections** page or related list pages.  
- Select this option to create a separate journal line for sales tax amounts when write-off transactions are created by using the **Collections** page or related list pages. If you select this option, you can easily track the sales tax amounts that are involved in write-off transactions. You can track the sales tax amounts separately to help you more easily adjust your sales tax liability for the affected period.  
5. Expand or collapse the **Email template** section.
- Select the email template to use when you send an email message by using the **E-mail > Transactions** to contact action in the **Collections** page.  
- Select the email template to use when you send a customer statement as an attachment to an email message by using the **E-mail > Statement** to contact action in the **Collections** page.  
- Select the email template to use when you send an email message by using the **E-mail > Transactions** to salesperson action in the **Collections** page.  

## Age customer balance
1. Go to **Credit and collections > Periodic tasks > Age customer balances**.
- Select an aging period definition. The aging snapshot process ages transactions according to the aging periods that are defined in the selected aging period definition.  
- Select a customer pool or leave this field blank to create an aging snapshot for all customers. If a customer pool is selected, the aging snapshot process is applied only to the customer accounts that are part of the customer pool. The selected customer pool must be of the Aging snapshot type.  
- Select the type of date to base the aging snapshot on.  
  - **Transaction date** – Age each transaction based on its transaction date.    
  - **Due date** – Age each transaction based on its due date.    
  - **Document date** – Age each transaction based on its document date.  
- Select the date to use as the current date for the aging snapshot. Aging periods are calculated based on this date.    
  - **Today's date** – Use the system date. Use this option if processing is set up to occur in a recurring batch. If you use this date, the recurring batch can be run periodically and the system date at that time is used.    
  - **Selected date** – Use a date that you specify. If you select this option, enter an aging date.  
2. Select **OK**.

## View aged customer balances
1. Go to **Credit and collections > Collections > Aged balances**.
- Use this list page to view customer balances and aged amounts by aging period. This information is stored in an aging snapshot. The aging periods are determined by the aging period definition that is used. The aging period definition is taken from the customer pool, if one was specified for the pool query. If the customer pool doesn't have an aging period definition, the default aging period definition that is specified in the **Accounts receivable parameters** page is used.  
2. Expand the **Contact** FactBox. Here you can view contact information:
- Collection contact for the customer.  
- Default sales person for the customer.  
3. Expand the **Credit limit** FactBox.
- Use the **Credit information** FactBox to view the credit limit and current balance information for the customer.  

## View customer collections details
1. Make sure the desired record is selected.
2. Expand the **Address**, **Contact**, **Aging**, and **Credit limit** FactBoxes to view the given information.
3. On the Action Pane, select **Collect**.
- Update the aging snapshot for the customer, using the current date as the aging date that the transaction dates are compared with. If the aging snapshot contains information for multiple legal entities, the updated aging snapshot contains information for the same set of legal entities. Amounts are stored in the accounting currency of the legal entity that you are logged on to when you update the aging snapshot.  
- Select an aging period definition. By default, the aging period definition that is associated with the aging snapshot for the customer is displayed. The aging period definition controls the aging periods and amounts that are shown in the **Aged balances** and **Credit information** FactBoxes.  
- Open a menu that contains the following items:    
  - **Company** – Display amounts in the **Aged balances** and **Credit information** FactBoxes in the legal entity's accounting currency.  
  - **Customer** – Display amounts in the **Aged balances** and **Credit information** Fact boxes in the customer's currency.  
- Select one or more legal entities in the customer's aging snapshot for which to view information. The legal entities that are shown in the list were selected when the aging snapshot was created.  
- View the customer's statement in Microsoft Excel format. You can select a starting date for the range of transactions to include on the statement and decide whether to include only open transactions, or both open and settled transactions. If the aging snapshot contains information for multiple legal entities, transactions are included for all the legal entities.  
- Open the **Documents** page, in which you can create or edit documents or notes.  
4. On the Action Pane, select **Communicate**.  
- Open Outlook, where you can send an email message to the contact that is specified in the **Contact** field. If a collections contact is not specified, the primary address for the customer is used. If a primary contact is not specified, email messages will be sent to the first address listed in the **Contacts** page. The transactions that are selected are included as an attachment. The attachment is in Excel format and contains three worksheets. An email template for messages to customer contacts can be specified in the **Accounts receivable parameters** page.  
- This button is not available if the contact that is selected in this page does not have an email address set up.  
- Prepare a statement and open Outlook, where you can send an email message that has an attached statement to the address specified in the **Contact** field. If a collections contact is not specified, the primary address for the customer is used. If a primary contact is not specified, email messages will be sent to the first address listed in the **Contacts** page.  
- This button is not available if the contact that is selected in this page doesn't have an email address set up.  
- Open Outlook, where you can send an email message to the employee who is specified as the sales representative for the sales group that is assigned to the customer. If transactions are selected, they are included as an attachment. The attachment is in Excel format and contains two worksheets. An email template for messages to salespeople can be specified in the **Accounts receivable parameters** page.  
- This button is not available if the salesperson that is displayed in this page does not have an email address set up.  
- View and perform actions on transactions for the customer. If you are using centralized payments, information for all legal entities that are included in the customer's aging snapshot is included. You can restrict the legal entity information by selecting **Company** in the **Select** group on the action pane.  
- Change the collections status for the selected transactions.    
  - **Not disputed** – No collections action has occurred for the transaction.    
  - **Disputed** – The customer has notified you that there is a problem with the transaction.    
  - **Promised to pay** – The customer has agreed to pay the transaction amount.    
  - **Resolved** – All problems with the transaction have been solved and no additional collections action is necessary.  
- Open a menu and select one of the following items to specify which transactions to display in this page:    
  - **Open** – Display only transactions that have not been settled.    
  - **Open and closed** – Display all transactions, both settled and not settled.  
- Process the selected payment as a non-sufficient funds (NSF) payment.    
  - This button is available only if the selected transaction is a payment (a credit balance without an invoice) entered in a payment journal, a bank account is assigned to the transaction, and the payment has not been canceled previously.  
- Write off the selected transactions.  
- Mark the selected transactions for settlement with each other.  
- Open the **Original document** page, in which you can view and print the document for the selected transaction.  
- Open a **menu** that contains the following items:    
  - **Collections** – Display only activities that were created in the **Collections** page.    
  - **All** – Display all activities for the customer, regardless of where the activities were created.  
- Open a **menu** that contains the following items:    
  - **Open** – Display only activities that are not closed.    
  - **Open and closed** – Display all activities, regardless of their status.  
- Select a collections case that is assigned to the customer or leave this field blank. If a case is selected, only transactions and activities that are associated with the case are displayed in this page.  
5. Select **Show list**.
- Select a customer account or accept the default entry. By default, this is the selected customer account on the list page or in the page from which you opened this page. If you opened the page from a list page, the customers in the list are the customers who are included in the collections pool that is used on the list page.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
