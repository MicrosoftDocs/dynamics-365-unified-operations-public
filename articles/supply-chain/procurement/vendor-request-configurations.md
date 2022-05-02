---
# required metadata

title: Vendor request configurations
description: This topic describes the fields that are required to be populated in a new vendor request.
author: GalynaFedorova
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: VendProspectiveVendorRegistrationConfig 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: gfedorova
ms.search.validFrom: 2017-12-31 
ms.dyn365.ops.version: 7.3
---

# Vendor request configurations
[!include [banner](../includes/banner.md)]

To complete a vendor request, a vendor contact person must complete the prospective vendor registration wizard.

In the **Vendor request configurations** form, you can create profiles that specify required fields and visible fields in the prospective vendor registration wizard.

The vendor registration wizard will start out by asking the prospective vendor user which country/region the vendor is doing business in. This information determines the applicable configuration. If no specific configuration is defined for a country/region, a default configuration will be used.

### Set up a vendor request configuration

By default, there is a vendor configuration available in the Vendor request configurations form.

It is not possible to select country/regions for the default configuration, so the **Countries/regions** section cannot be changed.

1. Click **Procurement and sourcing** > **Setup** > **Vendors**, and then click **Vendor request configurations**.
2. Click the **Fields** tab to set the status of the listed fields.
3. Hidden (Not visible)
4. Displayed (Visible but not mandatory)
5. Required (Visible and mandatory)
6. Click the **Content** tab to specify if text is going to be shown on the wizard and if there should be an acknowledgement that the prospective vendor user must accept this before moving to the next step in the wizard. The acknowledgement will be requested for any terms and conditions that the user must accept to continue.

You can also enter a confirmation message that will be displayed when the wizard is finalized, and you can add one or more questionnaires.

### Create a vendor configuration for a specific country/region
1.	Click **Procurement and sourcing** > **Setup** > **Vendors**, and then click **Vendor request configurations**.
2.	Click **New** to create a new configuration, and provide a name for the configuration.
3.	Click **Save**.
4.	Open the **Country/regions** tab to select the country/region that the configuration should be used for.
5.	Complete the configuration by following the guidelines for the default configuration.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]