---
title: Vendor request configurations
description: Learn about the fields that are required to be populated in a new vendor request, including a process for setting up a vendor request configuration.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form: VendProspectiveVendorRegistrationConfig 
ms.topic: how-to
ms.date: 06/17/2025
ms.custom: 
  - bap-template
---

# Vendor request configurations

[!include [banner](../includes/banner.md)]

To complete a vendor request, a vendor contact person must complete the prospective vendor registration wizard.

On the **Vendor request configurations** page, you can create profiles that specify required fields and visible fields in the prospective vendor registration wizard.

The vendor registration wizard starts by asking the prospective vendor user which country/region the vendor is doing business in. This information determines the applicable configuration. If no specific configuration is defined for a country/region, a default configuration is used.

## Set up a vendor request configuration

By default, there's a vendor configuration available on the **Vendor request configurations** page.

It isn't possible to select country/regions for the default configuration, so the **Countries/regions** section can't be changed.

1. Go to **Procurement and sourcing** \> **Setup** \> **Vendors** and then select **Vendor request configurations**.
1. Select the **Fields** tab to set the status of the listed fields.
    - *Hidden* (Not visible)
    - *Displayed* (Visible but not mandatory)
    - *Required* (Visible and mandatory)
1. Select the **Content** tab to specify if text is going to be shown on the wizard and if there should be an acknowledgment that the prospective vendor user must accept this before moving to the next step in the wizard. The acknowledgment is requested for any terms and conditions that the user must accept to continue.

You can also enter a confirmation message that is displayed when the wizard is finalized, and you can add one or more questionnaires.

## Create a vendor configuration for a specific country/region

1. Go to **Procurement and sourcing** \> **Setup** \> **Vendors** and then select **Vendor request configurations**.
1. Select **New** to create a new configuration, and provide a name for the configuration.
1. Select **Save**.
1. Open the **Country/regions** tab to select the country/region that the configuration should be used for.
1. Complete the configuration by following the guidelines for the default configuration.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
