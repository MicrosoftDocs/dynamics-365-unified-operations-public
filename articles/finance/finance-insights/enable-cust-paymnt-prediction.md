---
# required metadata

title: Enable customer payment predictions
description: This article explains how to turn on and configure the Customer payment predictions feature in Finance insights.
author: ShivamPandey-msft
ms.date: 02/11/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.assetid: 3d43ba40-780c-459a-a66f-9a01d556e674
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2020-05-29
ms.dyn365.ops.version: AX 10.0.12

---

# Enable customer payment predictions

[!include [banner](../includes/banner.md)]

This article explains how to turn on and configure the Customer payment predictions feature in Finance insights. You turn on the feature in the **Feature management** workspace and enter configuration settings on the **Finance insights configuration** page. This article also includes information that can help you effectively use the feature.

> [!NOTE]
> Before you complete the following steps, be sure to complete the prerequisite steps in the [Configure for Finance insights](configure-for-fin-insites.md) article.

1. Turn on the Customer payment predictions feature:

    1. Open the **Feature management** workspace.
    2. Select **Check for updates**.
    3. On the **All** tab, search for **Customer payment predictions**. If you don't find that feature, search for **(Preview) Customer payment predictions**. 
    4. Turn on the feature.

    The Customer payment predictions feature is now turned on and ready to be configured.

2. Configure the Customer payment insights feature:

    1. Go to **Credit and collections \> Setup \> Finance insights \> Customer payment predictions**.
    2. On the **Finance insights configuration** page, on the **Customer payment predictions** tab, select **View the data fields used in the prediction model** to open the **Data fields for prediction model** page. There, you can view the default list of fields that are used to create the artificial intelligence (AI) prediction model for customer payment predictions.

        To use the default list of fields to create the prediction model, close the **Data fields for prediction model** page, and then, on the **Finance insights configuration** page, set the **Enable feature** option to **Yes**.
        
   > [!NOTE]
   > The **Customer payment predictions** feature requires more than 100 transactions in the previous six to nine months. The transactions can include free text invoices, sales orders, and customer payments. This data must be spread across the **On-time**, **Late**, and **Very late** settings.    
     

    3. Specify the "very late" transaction period to define what the **Very late** prediction bucket means for your business.

        For each open invoice, the system predicts the probability of payment in three buckets: **On time**, **Late**, and **Very late**.

        - **On time** – This bucket includes payments that are predicted to be paid on or before the transaction due date.
        - **Late** – This bucket includes payments that are predicted to be paid after the transaction due date but before the start of the "very late" transaction period.
        - **Very late** – This bucket includes payments that are predicted to be paid after the start of the "very late" transaction period.

        > [!NOTE]
        > If you change the "very late" transaction period and select **Change late threshold** after the AI prediction model for customer payments has been created, the existing prediction model is deleted, and a new model is created. The new prediction model will move transactions into the "very late" period, based on the settings that were entered to define it.

    4. After you've finished defining the "very late" transaction period, select **Create prediction model** to create the prediction model. The **Prediction model** section on the **Finance insights configuration** page shows the status of the prediction model.

        > [!NOTE]
        > At any time while the prediction model is being created, you can select **Reset model creation** to restart the process.

    The feature has now been configured and is ready to be used.

After the feature has been turned on and configured, and the prediction model has been created and is working, the **Prediction model** section of the **Finance insights parameters** page shows the accuracy of the model.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
