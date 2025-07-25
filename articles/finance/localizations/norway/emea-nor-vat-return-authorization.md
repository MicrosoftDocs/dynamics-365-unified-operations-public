---
title: Authorize interoperation with ID-porten and Altinn web services
description: Learn how to authorize your Microsoft Dynamics 365 Finance environment to interoperate with ID-porten and Altinn web services in Norway.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.date: 06/12/2025
ms.reviewer: johnmichalak
ms.search.region: Norway
ms.search.validFrom: 2022-11-18
ms.custom:
  - bap-template
  - sfi-image-nochange
---

# Authorize interoperation with ID-porten and Altinn web services

[!include [banner](../../includes/banner.md)]

This article explains how to authorize your Microsoft Dynamics 365 Finance environment to interoperate with ID-porten and Altinn web services in Norway.

Before you start to authorize your Microsoft Dynamics 365 Finance environment to interoperate with ID-porten and Altinn web services, make sure that you've [registered an integration point in ID-porten](emea-nor-vat-return-integration-point.md). Additionally, make sure that the **Gyldig(e) redirect uri-er** field of your integration point is set to the internet address (URL) of the **Web applications** page in the legal entity that you will interoperate with ID-porten and Altinn web services from.

To authorize your Finance environment in ID-porten and Altinn web services, follow these steps.

1. In Dynamics 365 Finance, go to **Tax** \> **Setup** \> **Electronic messages** \> **Web applications**.
1. Select the **NO ID-Porten** web application in the list on the left.
1. Verify that the **Redirect URL** field is set to the URL of the current page (**Web applications**). This URL should match the URL that you specified in the **Gyldig(e) redirect uri-er** field of your integration point in the ID-porten web portal.
1. Verify that the **Client ID** field is set to the client ID of your integration point, and the **Client secret** field is set to the client secret.
1. On the Action Pane, select **Get authorization code**.
1. In the **Electronic report parameters** dialog box, in the **Requested language in the user interface** field, specify **en** for English. ID-porten also supports the following values: **nb**, **nn**, **en**, and **se**.

    > [!NOTE]
    > The list of supported values for the **Requested language in the user interface** field is subject to change by ID-porten. We recommend that you check the official ID-porten documentation for current information.

1. In the **Requested security level** lookup field, select a value that reflects your preference for the security level of your authorization in ID-porten. The following values that are available for the **Requested security level** lookup field can be used as the `acr_values` parameter for authorization requests to ID-porten:

    - **High** – This value is equivalent to the `idporten-loa-high` value, which is equivalent to security level "high" in eIDAS.
    - **Substantial** – This value is equivalent to the `idporten-loa-substantial` value, which is equivalent to security level "substantial" in eIDAS.
    - **Low** – This value is equivalent to the `idporten-loa-low` value.
    - **Not use** – This value is equivalent to the `acr_values` parameter not being used (optional).

    > [!NOTE]
    > The list of supported values for the `acr_values` parameter is subject to change by ID-porten. Check the official ID-porten documentation for current information.

1. Select **OK** to proceed with authorization in ID-porten.

    ![Specify parameters in the Electronic report parameters dialog box.](../media/emea-nor-vat-return-no-authorization-params.png)

    You're redirected to ID-porten for user authorization. The user who is authorized in ID-porten must have the rights that are required to complete and submit VAT returns.

1. When authorization is successful, you're redirected back to Finance, and a new browser tab shows the **Success** page. Close that browser tab, and return to the browser tab that shows the **Web applications** page where you started the authorization process.
1. On the Action Pane, select **Obtain access token**.

    > [!NOTE]
    > You must complete this step immediately after you obtain the authorization code. Otherwise, you might receive the following error message:
    >
    > Web service returned error code 400 ({"error":"invalid_grant","error_description":"invalid_grant (correlation id: aaaa0000-bb11-2222-33cc-444444dddddd)"}).
    >
    > If you receive this error message, go back to step 1. This time, select **Obtain access token** immediately after you obtain the authorization code.

1. In the **Electronic reporting parameters** dialog box, select **OK**.

    When you've successfully obtained an access token, you receive the following message: "Access token was successfully obtained." Additionally, the values in the **Granted scope** and **Access token will expire in** fields are updated.

    ![Granted scope and Access token will expire in fields updated for the NO ID-Porten web application on the Web applications page.](../media/emea-nor-vat-return-no-authorization-2023.png)

1. Select the **NO Altinn** web application in the list on the left.
1. On the Action Pane, select **Obtain access token**.
1. In the **Electronic report parameters** dialog box, select **OK**.

    When you've successfully obtained an access token, you receive the following message: "Access token was successfully obtained." Additionally, the values in the **Granted scope** and **Access token will expire in** fields are updated.

> [!IMPORTANT]
> - The authorization of your Finance environment in your integration point in ID-porten is valid for one calendar year. This period is defined by the **Authorization levetid (sekunder)** field of your [integration point](emea-nor-vat-return-integration-point.md). You must reauthorize your Finance environment before the authorization expires.
> - The authorization of your Finance environment in your integration point in ID-porten is *user-specific*. Because of this, Finance also stores information about which user obtained the authorization code in ID-porten. The submission of VAT return from Finance is allowed for only this user. If another user must submit a VAT return, they must go through the authorization process prior to submitting the VAT return.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
