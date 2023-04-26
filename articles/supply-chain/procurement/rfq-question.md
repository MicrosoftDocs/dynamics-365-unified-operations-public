---
# required metadata

title: Responding to vendor questions on Request for quotations
description: Vendors that have questions related to an RFP can submit their questions and read the answers on **Vendor collaboration** page.
author: GalynaFedorova
ms.date: 01/22/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: PurchRFQVendQuestionAnswer
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: public sector
ms.author: gfedorova
ms.search.validFrom: 2020-1-22
ms.dyn365.ops.version: 10.0.9

---
# Responding to vendor questions on Request for quotations

[!include [banner](../includes/banner.md)]

When your agency has sent a request for quotation (RFQ), vendors sometimes have questions that pertain to the request. Vendors that have questions related to an RFP can submit their questions and read the answers on **Vendor collaboration** page, when you make that page available to them. When vendor questions are accepted, **Questions and answers** is available on the **Request for quotation bid** page on **Vendor collaboration**, and for your agency through the **Request for quotation** page, **Questions and answers**. 

Users can publish answers to vendor questions more than once. Vendors can't no longer post questions after a vendor is selected and the RFQ is awarded, or after the cutoff date for questions is reached.

## Turn this feature on or off

To use this feature, it must be turned on for your system. As of Supply Chain Management version 10.0.21, it's turned on by default. As of Supply Chain Management version 10.0.32, this feature is mandatory and can't be turned off. If you're running a version older than 10.0.32, then admins can turn this functionality on or off by searching for the *RFQ questions and answers* feature in the [**Feature management** workspace](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Allow questions and answers to be used in RFQs

1. Go to **Procurement and sourcing \> Setup \> Procurement and sourcing parameters**.
1. Open the **Request for quotation** tab.
1. Set the following options as needed:
    - **Allow vendor questions**: Enables or disables vendor questions for RFQ cases. You must set this to *Yes* to use the features described in this article.
    - **Default direct response**: When you reply to a question, you can choose to reply to all vendors who received the RFQ or to reply only to the specific vendor who submitted the question. You can make choose this option each time you reply, but this setting controls the default. If you usually reply to all vendors, set this to *No*. If you usually reply to individual vendors, set this to *Yes*.

## Setting up for vendor questions

When creating a request for quotation, you determine whether vendors can ask questions about the RFQ.

1. Navigate to **Procurement and sourcing > Requests for quotations** then click **New > Request for quotation** 
1. In the **New request for quotation** page, **Header** to set the **Vendor question options** fields to allow questions before a certain date.
1. Set the **Allow vendor question** option to **Yes** so the vendors can enter questions. Users can enter and answer questions and designate commonly asked questions to publish for vendors when the RFQ is sent to vendors.
1. Optional: In the **Cutoff date** field, define the final date by which questions must be submitted. If no cutoff date is entered, questions are accepted as long as the RFQ is open and accepting bids.
1. Click **Save** to save the RFQ.
1. Click **Send** to send the RFQ to the vendors for bidding.

## Entering and replying to vendor questions

Vendors enter questions in the **Vendor Collaboration > Request for quotations bid** page, **Vendor questions** FastTab. The question is visible only to the vendor and users.

## Entering a vendor question

1. In Vendor collaboration, in the **Request for quotation bid** page, click **Questions and answers**, and then 
click **+ Ask a question**.

    > [!NOTE]
    > Alternately, a user can enter questions for a vendor on the **Request for quotation** page, by clicking **Manage replies**, **Edit RFQ reply** then clicking **Questions and asnwers**.

2. On the **Question** field, enter the question text.
3. Click the **Submit**. Repeat steps 1-3 to add a question.
4. When done, click **Save** to save your questions.

## Replying to a single vendor

The question and answer are visible only to the vendor and users.

1. On the **Request for quotations** page, click the **Questions and answers** to display the **Questions and answers** page.
1. Click **Edit**.
1. Enter text in the **Answer** field to respond to the vendor's question.
1. Check the **Direct response** box.
1. Click **Save** to save your replies.
1. Click **Send answers** to send the answers to the vendor.

## Replying to all vendors

If you receive the same question from multiple vendors, you can group the questions and respond with one answer. All vendors receive notification when the commonly asked questions and answers are published. The vendors and anyone with access to the request for quotation can view the summary of questions and answers.

1. On the **Request for quotations** page, click the **Questions and answers** to display the **Questions and answers** page.
2. Click **Edit**.
3. Choose a code for the common question, such as the letter 'a.'
4. For each line that asks a similar question, enter the code in the **Group code** field. For example, for each line asking about item color, enter 'a.'
5. Choose one of the lines with the code value, and enter the question and answer the way you want them to read in the summary that will be available when the questions and answers are published (**Group question, Group answer** fields).
6. Optional: You can mark the **Direct response** check box to send the answers only to the selected vendors.
7. Click **Save** to save your answers.
8. Optional: You can revert the questions and answers to the previously published values if you want to undo your changes.
9. Click **Send answers** to send your answers to the vendors.

## Changing RFQ to allow or disallow questions

You can make changes to allow or disallow questions to RFQs until the RFQ is awarded. You can also extend or shorten the time frame in which vendors can submit questions.
For published RFQs, you must modify a request for quotation  to allow or disallow vendor questions or adjust the time frame for questions.

> [!IMPORTANT]
> If you amend an existing RFQ for the purpose of allowing vendor questions, the system will clear all existing responses when you resend the RFQ.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]