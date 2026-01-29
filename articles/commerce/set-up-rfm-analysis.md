---
title: Set up Recency, Frequency, and Monetary (RFM) analysis
description: Learn how to set up a Recency, Frequency, and Monetary (RFM) analysis of your customers in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 01/29/2026
ms.topic: how-to
ms.search.form: MCRRFMDefinition
ms.reviewer: v-griffinc
ms.assetid: 8ff9aac3-5ada-4150-85fd-18901c926d53
ms.search.region: global
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.custom: 
  - bap-template
---

# Set up Recency, Frequency, and Monetary (RFM) analysis

[!include [banner](includes/banner.md)]

This article explains how to set up a Recency, Frequency, and Monetary (RFM) analysis of your customers in Microsoft Dynamics 365 Commerce.

Recency, frequency, and monetary (RFM) analysis is a marketing tool that your organization can use to evaluate the data that customer purchases generate. After you set up RFM analysis, customers receive a calculated RFM score as they make purchases. The RFM score can be a three-digit rating or an aggregate number, depending on how your organization configures RFM analysis. Here's how the rating works if your organization uses a three-digit rating for the score:

- The first digit is the customer's recency rating, which is how recently the customer made a purchase from your organization.
- The second digit is the customer's frequency rating, which is how often the customer makes purchases from your organization.
- The third digit is the customer's monetary rating, which is how much the customer spends when the customer makes purchases from your organization.

For example, your organization sets the ratings on a scale of 1 through 5, where 5 is the highest rating. In this case, a customer rating of 535 tells you the following information about the customer:

- **Recency rating of 5** – The customer recently made a purchase.
- **Frequency rating of 3** – The customer purchases products from your organization moderately often.
- **Monetary rating of 5** – When the customer makes a purchase, the customer spends a significant amount of money.

If your organization uses an aggregate number for the score, add the individual ratings together. For the same example, the customer has a rating of 13 (5 + 3 + 5).

## Set up RFM analysis for the customers in your organization

To set up RFM analysis for the customers in your organization, follow these steps:

1. In Commerce headquarters, go to **Call center > Periodic > RFM analysis**.
1. On **RFM analysis**, select **New**. In the **RFM definition** field, enter a name for the RFM definition. For example, you could call the definition RFM-A.
1. Enter a start date and end date for this RFM definition.
1. On the **General** FastTab, do the following:

    - If each section of the RFM score must contain an equal count of customers, select the **Even distribution** check box.
    - Select the **Add scores** check box to aggregate the three scores. For example, this aggregation gives a customer an RFM score of 13 instead of 535.
    - Select the **Save history** check box to require the system to save the statistical data for customers so that the data can be used to calculate the RFM score.

1. On the **Recency** FastTab, do the following:

    - In the **Divisions** field, enter the number of divisions, or groups, which are used to calculate the recency score for customers. For example, if you have 100 customers, a division of five means that there are 20 customers for each score. The 20 customers who made purchases most recently have a recency score of five. The next 20 customers have a recency score of four, and so on. If you have 50 customers, 10 customers have a recency score of five, 10 have a recency score of four, and so on.
    - In the **Priority** field, select how much weight to give the recency parameter in relation to the other parameters when the RFM score is calculated for a customer. For example, you might place more value on the recency score than the monetary score.
    - In the **Multiplier** field, enter the value by which to multiply the recency score. If you don't enter a value, the score isn't multiplied.
    - In the **Period** field, select the time period by which the recency score is calculated. For example, by week or by month.

1. On the **Frequency** FastTab, do the following:

    - In the **Divisions** field, enter the number of divisions, or groups, which are used to calculate the frequency score for customers.
    - In the **Priority** field, select how much weight to give the frequency parameter in relation to the others when the RFM score is calculated for a customer.
    - In the **Multiplier** field, enter the value by which to multiply the frequency score. If you don't enter a value, the score isn't multiplied.

1. On the **Monetary** FastTab, do the following:

    - In the **Divisions** field, enter the number of divisions, or groups, which are used to calculate the monetary score for customers.
    - In the **Priority** field, select how much weight to give the monetary parameter in relation to the others when the RFM score is calculated for a customer.
    - In the **Multiplier** field, enter the value by which to multiply the monetary score. If you don't enter a value, the score isn't multiplied.
    - In the **Gross/net** field, select whether the customer's monetary score should be calculated by using the gross or net invoice amount.
    - If a customer's return amounts should be subtracted from the customer's total invoice calculation, select the **Subtract returns** check box.

## View a customer's RFM score

To view a customer's RFM score, follow these steps:

1. In headquarters, go to **Call center > Journals > Customer service**.
1. On the **Customer service** page, in the **Customer service** pane, select the keyword type to search on in the search fields, and enter the search text.
1. Select **Search**.
1. On the **Customer search** page, select the customer record that you want, and then select **Select customer**.

The RFM score appears in the **Order history** group on the right side of the **Customer service** page.

## View or clear the history of an RFM analysis record

To view or clear the history of an RFM analysis record, follow these steps:

1. In headquarters, go to **Call center > Periodic > RFM analysis**.
1. On the **RFM analysis** page, select the record that you want to view.
1. To view the record history, select the **History** FastTab.
1. To clear the history, select **Clear history**.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
