---
title: Set up electronic Tax declaration for Germany
description: Learn about how to set up electronic tax declaration for Germany, including a step-by-step procedure that outlines the process.
author: kfend
ms.author: filatovm
ms.topic: how-to
ms.date: 03/12/2026
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Germany
ms.search.validFrom: 2016-06-30
ms.search.form: TaxElectronicDeclarationSetup, TaxElectronicCertificates, TaxElectronicHTTPServer
ms.dyn365.ops.version: Version 7.0.0
---
# Set up electronic tax declaration for Germany

[!include [banner](../../../finance/includes/banner.md)]

This procedure walks you through setting up an electronic tax declaration.

This procedure uses the demo data company DEMF. 

This functionality is available for legal entities whose primary address is in Germany.

You need a valid user certificate (like test-soft-pse.pfx) and a tax authority certificate (Coala2019.pem.cer) before you can complete this procedure.

1. Go to **Tax** > **Setup** > **Sales tax** > **Electronic tax declaration setup**.
1. Select **Edit**.
1. Select **Yes** in the **Authentication** field.
1. Enter or select a value in the **Format mapping** field.
    * As a prerequisite, you should upload from LCS Elster configuration (model and format) for Generic electronic reporting.  
1. Select **Electronic tax certificates**.
1. Select **New**.
1. Enter or select a value in the **User ID** field.
    * First, install certificates through Microsoft Management Console and assign friendly names that you use in these steps.  
    * In MMC for private certificate, go to **Certificates** > **Personal** > **Certificates**, and then select **Certificates**. 
    * In the context menu, click All Tasks > Import. Grant read permissions to the certificate for the user who is doing the submission.     * In MMC, right click the certificate and use All Tasks/Manage Private Keys. 
    * Select the user and add read permission.  
    * For tax authority certificate in MMC, right-click **Trusted Root Certificate Authorities**.  
    * Import **Coala2019.pem.cer**.  
1. Enter a value in the **Certificates reference** field.
1. Select **Save**.
1. Close the page.
1. Select **HTTP servers**.
    * The authority provides HTTP URL addresses and can change them. Microsoft provides default addresses that the system uses randomly.  
1. Select **Save**.
1. Close the page.
1. Select **Save**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
