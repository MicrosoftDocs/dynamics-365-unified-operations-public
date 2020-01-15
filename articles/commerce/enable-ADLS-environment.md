---
# required metadata

title: Enable ADLS a in Dynamics 365 Commerce Environment
description: This topic explains how to enable and test Azure Data Lake Storage (ADLS) for a Dynamics 365 Commerce Environment, a pre-requisite for enabling product recommendations.
author: bebeale
manager: AnnBe
ms.date: 01/13/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: 
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail, eCommerce
ms.author: bebeale
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: 10.0.5

---

# Enable ADLS in a Dynamics 365 Commerce Environment

[!include [banner](includes/preview-banner.md)]
[!include [banner](includes/banner.md)]

In the Dynamics 365 Commerce solution, all product and transaction information is tracked in the AX environment’s Entity Store. To make this data accessible to other Dynamics 365 services, such as data analytics, business intelligence, and personalized recommendations, it is necessary to connect the environment to a customer owned Azure Data Lake Storage Gen 2 (ADLS) solution.

As ADLS is configured in an environment, all necessary data is mirrored from the Entity Store, while still being protected and under customer’s control.

If Product Recommendations and/or Personalized Recommendations are also enabled in the environment, then the Product Recommendations stack will be granted access to the dedicated folder in ADLS to retrieve the customer’s data and compute recommendations based on it.


## Prerequisites

Customer needs to have Azure Data Lake Storage Gen 2 (ADLS) configured in an Azure subscription they own. 
This document does not cover the purchase of an Azure subscription or the setup of an ADLS enabled storage account.

More information on how to accomplish this can be found in the [ADLS official documentation](
	https://azure.microsoft.com/en-us/pricing/details/storage/data-lake).
  

## Configuration steps

This section covers the configuration steps necessary for enabling ADLS in an environment.

### Enable ADLS in the environment

1. Login to the environment's HQ back office portal.
1. Search for **System Parameters** and navigate to the **Data connections** tab. 
1. Set the **Enable Data Lake Integration** slider to **Yes**.
1. Set the **Trickle update Data Lake** slider to **Yes**.
1. Next, enter the following required information:
    1. **Application ID** // **Application Secret** // **DNS Name** - needed to connect to KeyVault where the ADLS secret is stored.
    1. **Secret name** - secret stored in KeyVault and used to authenticate with ADLS.
1. Save your changes in the top left corner of the page.

![Example ADLS Configuration](./media/exampleADLSConfig1.png)

### Test the ADLS connection

1. Test the connection to KeyVault via the **Test Azure Key Vault** link.
1. Test the connection to ADLS via the **Test Azure Storage** link.


> [!NOTE]
> If the tests fail, double check all KeyVault information added above is correct, then try again.

Once the connection tests are successful, then automatic refresh for entity store must be enabled: 

1. Search for **Entity Store**.
1. In the list on the left, navigate to the **RetailSales** entry, and select **Edit**.
1. Ensure that **Automatic Refresh Enabled** is set to **Yes**, click **Refresh**, then select **Save**.

![Example Entity Store Refresh](./media/exampleADLSConfig2.png)

Congratulations, ADLS is now configured for the environment. 

If not completed already, follow steps for [enabling product recommendations and personalization](enable-product-recommendations.md) for the environment.



## Additional resources

[Product recommendations overview](product-recommendations.md)

[Enable product recommendations](enable-product-recommendations.md)

[Add product recommendation lists to pages](add-reco-list-to-page.md)

[Add recommendations panel to POS devices](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/add-recommendations-control-pos-screen)


