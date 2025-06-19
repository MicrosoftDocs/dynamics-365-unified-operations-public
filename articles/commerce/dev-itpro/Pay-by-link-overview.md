---
title: Enable Pay by Link in point of sale using Adyen connector 
description: Learn how to set up and enable Pay by Link payment method to capture payments in stores.
author: shajain
ms.date: 06/19/2025
ms.topic: how-to
ms.custom: 
  - bap-template
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2025-06-15
---

# Enable Pay by Link payment method to capture payments using point of sale

[!include [banner](../includes/banner.md)]

The document details how administrators can enable Pay by Link (PBL) for their stores. PBL allows merchants to offer modern payment methods, providing customers with the flexibility to choose their preferred payment method. This payment method also eliminates the need for a payment terminal, facilitating store associates to be mobile and accept various types of payments. Additionally, as explained later in this document, PBL can serve as an effective tool for reducing checkout lines by enabling customers to pay from their current location, thereby expediting the checkout process. PBL is a controlled release, so please contact your Adyen account manager to check availability for participation in the pilot release. 

## Prerequisites

### Enable OAuth authentical from Adyen
The payment notification for pay by link payment method leverages OAuth based authentication and hence before proceeding with setting up, it is required that OAuth authentication is enabled by both Dynamics 365 Commerce team and Adyen. To enable OAuth from D365 Commerce, a flight needs to be enabled. Contact Microsoft support to enable this in your Commerce environments. Similarly, contact your Adyen representative to enable OAuth authentication for webhooks for your Merchant account. Additionally, please request Adyen to set the “Time to Live” (TTL) for the OAuth token to be defined as 3599 seconds i.e., 1 second less than an hour, which is the default TTL value for OAuth token in Azure. 

> [!NOTE]
> If the OAuth TTL cannot be set to 3599 from Adyen, then contact Microsoft support for instructions to override the default TTL value in the Microsoft Azure portal.

### Link Commerce environment to Dataverse environment
Another requirement to receive payment notifications is to link your Commerce environment to a corresponding Dataverse environment. This is because the payment notification service leverages Dataverse and thus it is required to link the two environments. Refer to the following documents if the two environments are not already connected.
https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/power-platform/environment-lifecycle-connect-finops-new-dv 

https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/power-platform/environment-lifecycle-connect-finops-existing-dv 

### Minimum required versions
The Pay by Link (PBL) feature is available starting 10.0.44 release and the minimum required versions for various components are mentioned below:
1.	Store Commerce App/ Cloud Point of Sale: 9.54.25148.1
2.	Commerce Scale Unit: 9.54.25137.4
3.	Commerce HQ: Any 10.0.44 version

### Required role to complete the setup
Some of the steps require a Commerce HQ user who should be either an administrator or have 'Commerce Payment Administrator' role assigned in Power platform.

## Setup
### Step 1: Enable the features required for Pay by Link. 

To enable the payment notifications for pay by link, enable the following features from the Feature management workspace:
1.	Enhanced wallet support and payment improvements (learn more: https://learn.microsoft.com/en-us/dynamics365/commerce/dev-itpro/wallets)
2.	Enable unified payments experience in POS (learn more: https://learn.microsoft.com/en-us/dynamics365/commerce/dev-itpro/faster-checkout-pos)
3.	Enable Payments Notification Feature (new feature flag)
4.	Enable Pay By Link Payment Feature (new feature flag)

### Step 2: Create a webhook to receive payment notification from Adyen
The following information is required to create a webhook in the Adyen portal:
a.	Payment notification service URL
b.	OAuth credentials to authenticate against the payment notification service
Payment notification service URL is the URL where the notifications will be sent by Adyen. It can be retrieved from Commerce HQ. To do so, navigate to the Commerce Shared Parameters -> Payment notifications. Copy the value shown in the field named "Payment notifications end point URL". If this field does not show any value, then it means that the Commerce environment is not linked to Dataverse environment. Please contact your Commerce administrator or contact Microsoft support for help.
To create the OAuth credentials, you need to register a new application using Azure portal. Payment notifications from Adyen will use this application credentials to securely communicate with the Payment notification service. Here are the detailed steps to register a new application.

#### Register a new application by using the Azure portal
- Sign in to the Microsoft Azure portal (https://portal.azure.com/) with a work or school account.
- If your account gives you access to more than one tenant, select your account in the upper-right corner, and set your portal session to the Microsoft Entra tenant that you want.
- In the left pane, select the Microsoft Entra ID service, and then select App registrations > New registration.
- When the Register an application page appears, enter your application's registration information:
  - Name: Enter a meaningful application name that will be shown to users of the app.
  - Supported account types: Select the types of accounts that your app should support. Any of these options should work



