---
# required metadata

title: Payments
description: This topic describes the payment options that are available in Dynamics 365 for Retail.
author: athinesh99
manager: AnnBe
ms.date: 06/16/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 65801
ms.assetid: 99079d81-fde2-4432-8cee-82bbcc3bd57e
ms.search.region: Global
# ms.search.industry: 
ms.author: athinesh
ms.search.validFrom: 2017-06-16
ms.dyn365.ops.version: Dynamics 365 for Retail

---
# Payment frequently asked questions

## What payment scenarios are supported for Dynamics 365 for Retail?
- Setting up a merchant account
- Process a call center order (Dynamics 365 for Finance and Operations)
- Process an online order (e-Commerce)
- Process a POS cash-and-carry transaction by using an accepting page
- Process a POS cash-and-carry return by using an accepting page
- Process a POS cash-and-carry return by using an accepting page
- Process a POS customer order by using an accepting page
- Process a POS cash-and-carry transaction by using Microsoft Dynamics AX 2012 Retail Hardware Station
- Process a POS cash-and-carry return by using Hardware Station
- Process a POS customer order by using Hardware Station
        
## Which payment providers are supported out of the box and in what regions?
- Verifone is supported in the United States for card present transactions (performed using devices) and card not present transactions (e.g., e-commerce or call center transations)
- Mastercard is supported for card not present transactions in the following countries: Australia, Canada, Denmark, France, Germany, Iceland, Ireland, Mexico, Netherlands, New Zealand, South Africa, United Kingdom, United States

## What is a payment connector and in what cases do I need to deploy/implement a payment connector?
Payment connectors are software components that can be set up for Dynamics 365 Unified Operations applications, that enable the applications to process payments for card present transactions and card not present transactions. A system can use Microsoft-provided connectors such as Verifone and MasterCard, or custom connectors can be built by ISV partners. A connector is typically built to meet the business needs of a customer. Custom connectors are often created when there is a scenario that requires a new type of payment type (e.g., linked refunds). Customers doing business in certain geographies may need new connectors if the out of box connectors do not support those regions.
          
## Are other payment connector providers supported?
- Yes, but you must connect them using customization.

## What is the Service level agreement (SLA) for out-of-box payment connectors like Verifone and Mastercard?
The SLA for the out of box connectors like Verifone and Mastercard is owned the Payment connector providers themselves. Please contact Verifone and Mastercard support for information about their respective SLAs.
        
## If a supported payment provider issues an update, will Microsoft automatically update the payment connector or do I need to work with payment provider to get the updated payment connector?
If an update of payment connector is issued by the payment connector provider, the updated version of the payment connector will be included in the next planned release of Dynamics 365 for Retail. However, the customer can also work directly with the payment connector provider to uptake it earlier.
        
## Who are the different personas involved in Payment scenarios?
- Customer (Customer IT, implementation partner, cashier or equivalent, shopper (C2))
- Payment connector provider and payment connector provider partner (out of box connector or external connector)
- Payment acquirer
- Microsoft
        
Related topics: 
- [Implementing a payment connector and payment device for Dynamics AX 2012 white paper](http://download.microsoft.com/download/4/D/7/4D7C6B05-0C23-4C6C-BA13-AB62ED08AA61/The%20Guide%20to%20Implementing%20Payment%20Connector%20and%20Payment%20Device.docx)
- [Deploying a Payment Connector](deploy-payment-connector.md)
- [Create a Windows Installer for Payment Connector](create-windows-installer-payment-connector.md)
- [Verifone Payment Connector](https://dynamics.verifone.com/repo/)
- [MasterCard Payment Connector](https://www.simplify.com/microsoft/) 
