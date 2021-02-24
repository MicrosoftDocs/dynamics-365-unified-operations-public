---
# required metadata

title: Refund on return order is declined
description: This topic provides troubleshooting guidance for when a refund on a return order is declined due to invoicing with a credit card that is different from the one used during the original payment authorization. 
author: Reza-Assadi
manager: AnnBe
ms.date: 02/23/2021
ms.topic: Troubleshooting
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Retail
ms.author: rassadi
ms.search.validFrom: 2021-01-31
ms.dyn365.ops.version: 10.0.18

---

# Refund on return order is declined

[!include [banner](../../includes/banner.md)]

This topic provides troubleshooting guidance for when a refund on a return order is declined due to invoicing with a credit card that is different from the one used during the original payment authorization.

## Description

A refund is declined when invoicing a return order with a credit card that's different from the card that was used during the original payment authorization. The following error message shown in the image below is displayed: "Some of the payments are not in the correct status for posting. Please re-validate the status of all payments prior to invoicing."

The payment authorization details will include the following error message: "Adyen gateway SendRequest() failed with status 'InternalServerError'.22144; Empty response returned from Adyen.(22001);"

![Refund on return order is declined error](media/refund-order-decline.jpg)

## Resolution

### Enable blind returns in Adyen

To enable blind refunds, follow the steps in [Troubleshoot Dynamics 365 Payment Connector for Adyen issues](adyen-support.md).

## Additional resources

[Dynamics 365 Payment Connector for Adyen](../dev-itpro/adyen-connector.md)

[Set up the Adyen payment connector for Dynamics 365](https://docs.adyen.com/plugins/microsoft-dynamics)
