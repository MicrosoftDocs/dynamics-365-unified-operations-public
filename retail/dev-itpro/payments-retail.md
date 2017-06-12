---
# required metadata

title: Payments FAQ
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
# Payments FAQ

## What payment scenarios are supported?
- Setting up a merchant account.
- Process a call center order.
- Process an online order.
- Process a POS cash-and-carry transaction by using an accepting page.
- Process a POS cash-and-carry return by using an accepting page.
- Process a POS cash-and-carry return by using an accepting page.
- Process a POS customer order by using an accepting page.
- Process a POS cash-and-carry transaction by using Microsoft Dynamics AX 2012 Retail Hardware Station.
- Process a POS cash-and-carry return by using Hardware Station.
- Process a POS customer order by using Hardware Station.

        
## Which payment providers are supported and in what regions?
- Verifone is supported in the United States for transactions where the card is present (performed using devices), and for transactions where the card is not present (for example, e-commerce or call center transactions).
- Mastercard is supported for transactions where the card is not present in the following countries: Australia, Canada, Denmark, France, Germany, Iceland, Ireland, Mexico, Netherlands, New Zealand, South Africa, United Kingdom, and United States.


## What is a payment connector and in what cases do I need to deploy and implement a payment connector?
Payment connectors are software components that can be set up for Dynamics 365 Unified Operations applications, which enable the applications to process payments for transactions where the card is not present and transactions where the card is present.

Microsoft-provided connectors such as Verifone and MasterCard can be used, or custom connectors can be built by ISV partners. A connector is typically built to meet the business needs of a customer. Custom connectors are often created when there is a scenario that requires a new type of payment type (for example, linked refunds). Customers doing business in certain geographies may need new connectors if the out-of-box connectors do not support those regions.
          
## Are other payment connector providers supported?
Yes, but you must connect them using customization.

## What is the Service level agreement (SLA) for out-of-box payment connectors like Verifone and Mastercard?
The SLA for the out-of-box connectors like Verifone and Mastercard is owned by the payment connector providers themselves. Please contact Verifone or Mastercard support for information about their SLAs.
        
## If a supported payment provider issues an update, will Microsoft automatically update the payment connector or do I need to work with the payment provider to get the updated payment connector?
If a payment connector update is issued by the payment connector provider, the updated version of the payment connector will be included in the next planned release of Dynamics 365 for Retail. However, the customer can also work directly with the payment connector provider to uptake it earlier.
        

        
Related topics: 
- [Implementing a payment connector and payment device for Dynamics AX 2012 white paper](http://download.microsoft.com/download/4/D/7/4D7C6B05-0C23-4C6C-BA13-AB62ED08AA61/The%20Guide%20to%20Implementing%20Payment%20Connector%20and%20Payment%20Device.docx)
- [Deploying a Payment Connector](deploy-payment-connector.md)
- [Create a Windows Installer for Payment Connector](create-windows-installer-payment-connector.md)
- [Verifone Payment Connector](https://dynamics.verifone.com/repo/)
- [MasterCard Payment Connector](https://www.simplify.com/microsoft/) 
