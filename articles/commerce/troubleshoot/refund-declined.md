---
# required metadata

title: Refund on return order is declined
description: This topic provides a resolution when a refund is declined when invoicing a return order with a credit card that is different from the card that was used during the original payment authorization. 
author: Reza-Assadi
manager: AnnBe
ms.date: 02/17/2021
ms.topic: Troubleshooting
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: josaw
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

## Description
When invoicing a return order with a credit card that is different from the card that was used during the original payment authorization, the refund is declined and the following error message is displayed: "Some of the payments are not in the correct status for posting. Please re-validate the status of all payments prior to invoicing."

The payment authorization details will contain the following error message: "Adyen gateway SendRequest() failed with status 'InternalServerError'.22144; Empty reponse returned from Adyen.(22001);"

## Resolution

### Enable blind returns in Adyen
Follow the steps in the [Troubleshoot Adyen Connector issues](adyen-support.md) topic to enable blind refunds.


