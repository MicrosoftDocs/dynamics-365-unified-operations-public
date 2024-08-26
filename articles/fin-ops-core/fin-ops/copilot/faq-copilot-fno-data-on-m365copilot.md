---
title: Responsible AI FAQ for Chat with finance and operations data on Microsoft 365 Copilot
description: This FAQ provides information about the AI technology used in Chat with finance and operations data on Microsoft 365 Copilot, along with key considerations and details about how AI is used, how it was tested and evaluated, and any specific limitations.
ms.date: 06/13/2024
ms.custom: 
  - responsible-ai-faqs
ms.topic: article
author: RamaKrishnamoorthy
ms.author: ramasri
ms.reviewer: johnmichalak
---

# Responsible AI FAQ for Chat with finance and operations data on Microsoft 365 Copilot

These frequently asked questions (FAQ) describe the AI impact of the *Chat with finance and operations data on Microsoft 365 Copilot* feature in finance and operations apps.

## What is Chat with finance and operations data on Microsoft 365 Copilot?

This feature allows the users to use Microsoft 365 Copilot to chat with finance and operations data through virtual entities in Dataverse. 

## What are capabilities of the Chat with finance and operations data on Microsoft 365 Copilot?

This feature enables users with guided conversation experience to quickly identify the available inventory in Dynamics 365 finance and operation apps without leaving the work context in Microsoft 365.  

## What is the intended use of the Chat with finance and operations data on Microsoft 365 Copilot?

A Microsoft 365 Copilot license enables authorized users to engage in a natural-language conversation with finance and operations data. For example, they can ask the following questions: 

- I need six Southridge Video Laptop16 M1601 in Silver color and 5 Laptop15 M1501 in Red color, can you check the availability? Give me the details by product name, site, warehouse, color, available quantity. 
- Do we have red Laptop15 M1501 model in warehouses other than Chicago within the site Central? Give me the details by product name, site, warehouse, color, available quantity. 

Microsoft 365 Copilot is based on the data that resides inside finance and operation apps and responds to users.  

The interested users are M365 Copilot users, those who also have the necessary security role and privilege to access the related querying data in Dynamics 365 Supply Chain Management, for example the access of the query on-hand inventory.  

## How was Chat with finance and operations data on Microsoft 365 Copilot evaluated? What metrics are used to measure performance?

The feature is evaluated by its usage and accuracy. 

## What are the limitations of Chat with finance and operations data on Microsoft 365 Copilot? How can users minimize the impact of these limitations when using the system?

When the feature does not work as intended, it provides the inaccurate inventory quantity that can bring negative impacts on customer’s business, such as:  

- Lost sales: If Copilot responds with more stock than Dynamics 365 SCM on-hand inventory records, and especially in a stock out scenario, the inaccurate inventory availability may cause sales manager to lose potential customers.   
- Wasted resources: If Copilot responds with inaccurate inventory amount, it may cause the overstock of products.  
- Poor customer satisfactions: If Copilot respond is inaccurate, this may cause the fail to deliver orders on time. This can lead to customer dissatisfaction and lower retention rates.   
- Insufficient inventory management: Copilot’s responses may cause poor inventory management if they are inaccurate. This could cause unnecessary inventory transfers between locations, creating the risks of understocking or overstocking in different warehouses.   

Users can minimize the impact by using only the prompts documented in the documentation.  

## What operational factors and settings allow for effective and responsible use of the feature?

With the understanding of the above potential negative impact, we plan to implement the following mitigations:   

- We are fixing the plugin invocation pipeline to improve the hit ratio which increases the probability of invoking the plugin based on user utterances.
- We are coming up with a more advanced and stable concept called Knowledge. Plugin needs to upgrade to knowledge at some point when it becomes ready to consume. 

## See also

- [Chat with finance and operations data on Microsoft 365 Copilot](../../dev-itpro/m365-copilot/chat-with-fno-data-on-m365copilot.md)
