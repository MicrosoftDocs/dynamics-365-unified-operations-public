---
# required metadata

title: Authorize interoperation with ID-Porten and Altinn web services
description: This topic explains how to authorize your Dynamics 365 Finance environment to interoperate with ID-Porten and Altinn web services. 
author: liza-golub
ms.author: elgolu
ms.date: 11/23/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Norway
# ms.search.industry: 
ms.search.validFrom: 2022-11-18

---

# Authorize interoperation with ID-Porten and Altinn web services

Before you start authorizing your Dynamics 365 Finance environment to interoperate with ID-Porten and Altinn web services, make sure that you [register an integration point in ID-porten](emea-nor-vat-return-integration-point.md) and specify the internet address of the **Web applications** page from the legal entity you are going to interoperate with ID-porten and Altinn in the **Gyldig(e) redirect uri-er** field of your integration point.

To get your Finance environment authorized in ID-Porten and Altinn web services and ready to interoperate with them, complete the following steps.

1. Go to **Tax** > **Setup** > **Electronic messages** > **Web applications** and select the **NO ID-Porten** web application.
2. verify that the internet address of this page is populated in the **Redirect URL** field of this web application. It's the same internet address that you populated in **Gyldig(e) redirect uri-er** field of your integration point in ID-porten web portal.
3. Check that the client ID and client secret of your integration point are populated in **Client ID** and  **Client secret** fields of this web application.
4. On the Action Pane, select **Get authorization code** and in the **Electronic report parameters** dialog box, in the **Requested language in the user interface** field, specify **en**, and then select **OK**.

   You will be redirected to ID-porten for user authorization. The user that is authorized in ID-porten must be granted the necessary rights to fill out and complete the submission of VAT return.
   
5. As a result of successful authorization, you will be redirected back to Finance. You should see the **Success** page on a new browser tab. Close this tab and go back to your browser’s tab with **Web applications** page where the authorization process was started.
6. On the Action Pane, select **Obtain access token**. This must be done immediately after the authorization code was successfully obtained. 
7. On the **Electronic reporting parameters** dialog box, select **OK**.

  If you don't start the process to get an access token immediately after authorization code is obtained, you may see the following error: **`Web service returned error code 400 ({"error":"invalid_grant","error_description":"invalid_grant (correlation id: 08ede4e5-4720-5edb-8fd2-a4f6a1902b74)"}).`** If you see this error, go back to the step 4 and on the Action Pane, select **Obtain access token** immediately after the authorization code was successfully obtained.
  
  As a result of successful obtaining of the access token, you will receive the message, **Access token was successfully obtained.** and the values in the **Granted scope** and **Access token will expire in** fields are updated.

  ![Authorize your Finance environment to interoperate with ID-Porten.](media/emea-nor-vat-return-no-authorization.png)

8. On the **Web applications** page, select the web application, **NO Altinn**.
9. On the Action Pane, select **Obtain access token** and in the **Electronic report parameters** dialog box, select **OK**.

  When you have successfully obtained the access token, you will receive the message, **Access token was successfully obtained.** The values in the **Granted scope** and **Access token will expire in** fieldd are updated.

  ![Access token was successfully obtained.](media/emea-nor-vat-return-access-token-altinn.png)

> [!IMPORTANT]
> Due to parameters of the [integration point](# integration-point), the authorization of your Finance in ID-porten integration point is valid for one calendar year (\“Authorization levetid\” parameter). You must re-authorize your Finance environment in advance before the authorization expires.

