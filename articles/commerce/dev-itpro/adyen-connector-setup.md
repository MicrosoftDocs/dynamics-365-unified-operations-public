---
title: Set up Dynamics 365 Payment Connector for Adyen
description: Learn how to sign up with Adyen and set up the Microsoft Dynamics 365 Payment Connector for Adyen.
author: Reza-Assadi
ms.date: 09/23/2026
ms.topic: how-to
ms.reviewer: mirao
ms.search.region: Global
ms.author: rassadi
ms.search.validFrom: 2019-01-01
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.custom: 
  - bap-template
---

# Set up Dynamics 365 Payment Connector for Adyen

[!INCLUDE [banner](../includes/banner.md)]

This article describes how to sign up with Adyen and set up the Microsoft Dynamics 365 Payment Connector for Adyen. For an overview of the Dynamics 365 Payment Connector for Adyen, see [Dynamics 365 Payment Connector for Adyen overview](adyen-connector.md).

## Sign up with Adyen

To use the Dynamics 365 Payment Connector for Adyen, you must have a separate agreement with Adyen. To learn more about Adyen's services, or to create a test merchant account, visit the [Adyen website](https://www.adyen.com/signup).

## Setup and configuration

> [!NOTE]
> These instructions assume that you already signed up for a merchant account with Adyen, and that you have access to the Adyen merchant dashboard.

> [!IMPORTANT]
> Adyen no longer supports [hosted payment pages](https://docs.adyen.com/online-payments/classic-integrations/hosted-payment-pages) as of October 2022. When you configure the Dynamics 365 Payment Connector for Adyen, version V001 is no longer supported for call center and Commerce e-commerce because it uses hosted payment pages from Adyen. You should instead use version V002 (with origin key) or version V003 (with client key). Microsoft recommends using version V003, which is available in Commerce versions 10.0.29 and later. Ensure that you set the **Allowed Origins** in the Adyen configuration by adding the full URL (for example, `https://www.adventure-works.com`) for your site (for e-commerce) or Commerce headquarters (for call center). For connecting with Adyen payment terminals, the device name is still "MicrosoftAdyenDeviceV001".

### Prerequisites

Complete the following prerequisites before you configure payments in any channel.

#### Configure your Adyen account settings for Dynamics 365 Commerce

In addition to the following instructions, configure your Adyen account settings for Dynamics 365 Commerce. For instructions on setting up Adyen for Dynamics 365 Commerce, see [Set up the Adyen payment connector for Dynamics 365](https://docs.adyen.com/plugins/microsoft-dynamics).

#### Set up a processor for new credit cards

To process payments in Commerce headquarters via the Adyen connector, configure the Adyen connector and set it up as the default payment processor for new credit cards.

To configure a default payment processor, follow these steps:

1. Sign in to Commerce headquarters and go to **Accounts receivable** > **Payments setup** > **Payment services**.
1. On the **Action** pane, select **New**. On the **Setup** tab, enter the following information.

    | Field | Description | Sample value |
    | ----- | ----------- | ------------ |
    | Payment service | Enter the name of the payment service to configure. | Adyen Payment Service |
    | Payment connector | Select the payment connector to use for new credit card payments. | Dynamics 365 Payment Connector for Adyen |
    | Test mode | For the Adyen connector, in production and test environments, set this field to **false**. | false |
    | Default processor for credit cards | Specify whether this payment processor should be the default processor to use for new credit cards. | Yes |
    | Bypass payment processor for zero transactions | Specify whether to skip this payment processor for transactions that have a zero (0) amount. | Yes |

1. On the **Payment service account** tab, enter the following information.

    | Field | Description | Required | Automatically set | Sample value |
    | ----- | ----------- | :------: | :---------------: | ------------ |
    | Assembly Name | Auto populated name of the assembly for the Dynamics 365 Payment Connector for Adyen. | Yes | Yes | *Binary name* |
    | Service account ID | Auto populated unique identifier for the setup of the merchant properties. This identifier is stamped on payment transactions and identifies the merchant properties that downstream processes (such as invoicing) should use. | Yes | Yes | *Guid* |
    | Version | Enter the version of the Dynamics 365 Payment Connector for Adyen to use. Version "V003" should be used for all new implementations. Version "V002" is still available while Adyen supports origin key functionality. Version "V001" is no longer supported. | Yes | Yes | "V002"/"V003" |
    | Gateway environment | Enter the Adyen gateway environment to which to map. The possible values are **Test** and **Live**. Set this field to **Live** only for production devices and transactions. | Yes | Yes | Live |
    | Optional Domain | The optional domain is required for live environments and you should contact Adyen to obtain it. This domain is the unique identifier for your live environment in the form **[random]-[company name]**, and is present as the prefix inside the API URLs under **Account** > **API URLs** in your company's live account on the Adyen Customer Area portal. For more information, see [Live endpoints](https://docs.adyen.com/development-resources/live-endpoints). | Live only | No | Contact Adyen |
    | Merchant account ID | Enter the unique Adyen merchant identifier. This value is provided when you sign up with Adyen as described in the [Sign up with Adyen](#sign-up-with-adyen) section. | Yes | No | MerchantIdentifier |
    | Terminal architecture | Set this field to **Cloud** for the `Payment service account`. | Yes | Yes | Cloud |
    | Local Password phrase | This field is used only for the POS payment terminal integration and should be left blank. | No | Yes | *Leave this field blank.* |
    | Local Key Identifier | This field is used only for the POS payment terminal integration and should be left blank. | No | Yes | *Leave this field blank.* |
    | Local Key Version | This field is used only for the POS payment terminal integration and should be left blank. | No | Yes | *Leave this field blank.* |
    | Local Cryptor Version | Enter the Adyen cryptor version to use when you interact with the Adyen gateway. Set this field to **1**. | Yes | Yes | 1 |
    | Cloud API Key | Enter the Adyen cloud API key. Obtain this key by following the instructions on the [Generate an API key](https://docs.adyen.com/development-resources/api-credentials#generate-an-api-key) page on the Adyen website. | Yes | No | abcdefg |
    | Supported Currencies | Enter the currencies that the connector should process. In card-present scenarios, Adyen can support additional currencies through [Dynamic Currency Conversion](https://www.adyen.com/pos-payments/dynamic-currency-conversion) after the transaction request is sent to the payment terminal. Contact Adyen support to get a list of supported currencies. | Yes | Yes | USD;EUR |
    | Supported Tender Types | Enter the tender types that the connector should process. | Yes | Yes | Visa;MasterCard;Amex;Discover;Debit |
    | Gift card provider | Enter the gift card provider that the connector should use to process gift cards. This field is case-sensitive. | No | No | "svs" or "givex" |
    | Terminal gift card entry | (*POS only*) Allows the customer to select between **Manual** or **Swipe**. | Yes | Yes | True/False |
    | Allow saving payment information in e-commerce | (*Commerce e-commerce only*) Gives signed-in users the option to save payment details for future online purchases.  | Yes | Yes | True/False |
    | Authorization stale period (days) | (*POS only*) Number of days before an authorization is considered stale and should decline before going to the processor for capture. | Yes | Yes | "7" |
    | Origin Key ("V002") or Client Key ("V003") | An origin key value is required when "V002" is the designated version. For instructions on obtaining this key, see [How to get an origin key](https://docs.adyen.com/development-resources/how-to-get-an-origin-key). A client key value is required when "V003" is the designated version. For instructions on obtaining this key, see [Migrate to Client key](https://docs.adyen.com/development-resources/client-side-authentication/migrate-from-origin-key-to-client-key#switch-to-using-the-client-key).| Yes | No | *The full origin or client key* |
    | EnableRequestProtection | Adds retry logic to "card not present" payment calls, reducing potential for duplicate calls using a correlation ID. If set to **True**, a correlation ID is added to provider requests to prevent duplicates. If set to **False**, calls are sent to the provider without the correlation ID or duplicate protection logic. | No | No | True/False |
    | Nonincremental capture payment methods | Names of the payment method variant or card types used by Adyen to identify card types in authorization responses that don't support incremental capture. Value entered should match the payment method variant/card type string used in Adyen to reference, as noted in [Adyen PaymentMethodVariant](https://docs.adyen.com/development-resources/paymentmethodvariant).  | No | No | "amexcommercial" |
    | Disable terminal line display | Removes the itemized digital receipt lines from the terminal interface used for customer preview before paying. **IMPORTANT:** If the Store Commerce app runs on handheld devices such as the Castles S1F2, then you must set this property to **False** to prevent the devices from getting stuck in line display mode. | No | No | True/False |
    | Omitted payment methods | (*E-commerce and call center only*) Use this field to omit a payment method from the configuration where an iFrame element is rendered for payments as configured against the merchant account. Separate multiple values with semicolons. Strings must match the label used in the Adyen portal. Some payment method security criteria might interfere with the iFrame element rendering, so it might be desirable to omit conflicting security criteria from the configuration.  | No | No | "applepay;googlepay" |

1. On the **Card verification value** tab, leave **Prompt for card verification value** and **Allow blank card verification value** set to **No**.

### POS payment terminal

#### Onboard and configure an Adyen payment terminal

> [!NOTE]
> These instructions assume that you have access to an Adyen payment terminal.

To onboard your Adyen payment terminal, go to [In-person payments | Adyen Docs](https://docs.adyen.com/point-of-sale) and follow the instructions. Skip any steps that instruct you to download Adyen-specific apps. During the onboarding process, make a note of the following information for each payment terminal. You need this information in the [Configure the payment terminal IP address and EFT POS register number](#configure-the-payment-terminal-ip-address-and-eft-pos-register-number) section.

- IP address of the payment terminal.
- POIID (POIID is composed of the serial number and model number of the device, and uniquely identifies the device.)

After the payment terminal is onboarded, sign in to the [Adyen Customer Area](https://ca-test.adyen.com/ca/ca/login.shtml), go to the terminal that you want to configure, and make a note of the following information for each payment terminal. You need this information in the [EFT service for local network communication](#eft-service-for-local-network-communication) section.

- Key identifier
- Key passphrase
- Key version

#### Enable a dedicated or shared hardware station

To enable a dedicated hardware station, follow these steps in Commerce headquarters for each store where you want to configure payment terminals.

1. Go to **Retail and Commerce** > **Channel setup** > **Stores** and select the store where you're configuring payment terminals.
1. On the **Hardware Station** FastTab, select **Add**.
1. For **Hardware Station type**, select **Dedicated**.
1. Save your changes to the store, and then run the **1070 (Channels)** job.

For instructions on enabling a shared hardware station, see [Configure a new Retail hardware station](../retail-hardware-station-configuration-installation.md#configure-a-new-retail-hardware-station). 

#### Set up a Dynamics 365 POS hardware profile

1. Sign in to Commerce headquarters and go to **Retail and Commerce** > **Channel setup** > **POS setup** > **POS profiles** > **Hardware profiles**.
1. Select the hardware profile to add the Dynamics 365 Payment Connector for Adyen for.
1. Follow the steps in the [EFT service](#eft-service) and [PIN pad](#configure-the-pin-pad) sections that follow.

#### EFT service

You can configure the Adyen payment connector to communicate with devices through the local network or through Adyen's cloud backend. For environments with unreliable internet service, or where offline mode is required, use the local architecture configuration. For environments with strong internet connections, or if you can't assign a static IP address to the payment terminal, the cloud architecture configuration might work best.

> [!IMPORTANT]
> The Dynamics 365 Payment Connector for Adyen doesn't currently support Store Commerce for iOS with local network or cloud architecture configurations.

##### EFT service for local network communication

1. On the **EFT service** FastTab, in the **EFT Service** field, select **Payment Connector**.
1. On the **Connectors** tab, select **New**, and then, in the **Connector** field, select **Dynamics 365 Payment Connector for Adyen**. Ensure that the value in the **Sequence number** field is lower than the value for all other connectors.
1. In the **Connector properties** section, enter the following information.

    | Field | Description | Required | Automatically set | Sample value |
    | ----- | ----------- | :------: | :---------------: | ------------ |
    | Assembly Name | Auto populated name of the assembly for the Dynamics 365 Payment Connector for Adyen. | Yes | Yes | *Binary name* |
    | Service account ID | Auto populated unique identifier for the setup of the merchant properties. This identifier is stamped on payment transactions and identifies the merchant properties that downstream processes (such as invoicing) should use. | Yes | Yes | *Guid* |
    | Version | Set to **V003** for EFT settings in the hardware profile. **V002** is required for call center and storefront only. Version **V001** is no longer supported. | Yes | Yes | "V003" |
    | Gateway environment | Enter the Adyen gateway environment to which to map. The possible values are **Test** and **Live**. Set this field to **Live** only for production devices and transactions. | Yes | Yes | Live |
    | Optional Domain | The optional domain is required for live environments and you should contact Adyen to obtain it. This domain is the unique identifier for your live environment in the format **[random]-[company name]**, and appears as the prefix inside the API URLs under **Account** > **API URLs** in your company's live account on the Adyen Customer Area portal. For more information, see [Live endpoints](https://docs.adyen.com/development-resources/live-endpoints).| Live only | No | Contact Adyen |
    | Merchant account ID | Enter the unique Adyen merchant identifier. Adyen provides this value when you sign up, as described in the [Sign up with Adyen](#sign-up-with-adyen) section. | Yes | No | MerchantIdenfier |
    | Terminal architecture | Set this field to **Local** for local communications. | Yes | Yes | Local |
    | Local Password phrase | Enter the Adyen key passphrase for the payment terminal. Adyen provides this value when you sign up, as described in the [Sign up with Adyen](#sign-up-with-adyen) section. | Yes | No | keypassphrase123 |
    | Local Key Identifier | Enter the Adyen key identifier for the payment terminal. Adyen provides this value when you sign up, as described in the [Sign up with Adyen](#sign-up-with-adyen) section. | Yes | No | mykey |
    | Local Key Version | Enter the Adyen key version for the payment terminal. Adyen provides this value when you sign up, as described in the [Sign up with Adyen](#sign-up-with-adyen) section. | Yes | No | 0 |
    | Local Cryptor Version | Enter the Adyen cryptor version to use when you interact with the Adyen gateway. Set this field to **1**. | Yes | Yes | 1 |
    | Cloud API Key | Enter the Adyen cloud API key. Get this key by following the instructions on the [Generate an API key](https://docs.adyen.com/development-resources/api-credentials#generate-an-api-key) page on the Adyen website. This field is required even for local terminal setups. | Yes | No | abcdefg |
    | Supported Currencies | Enter the currencies that the connector should process. In card-present scenarios, Adyen can support additional currencies through [Dynamic Currency Conversion](https://www.adyen.com/pos-payments/dynamic-currency-conversion) after the transaction request is sent to the payment terminal. Contact Adyen support to get a list of supported currencies. | Yes | Yes | USD;EUR |
    | Supported Tender Types | Enter the tender types that the connector should process. These values are case-sensitive. | Yes | Yes | Visa;MasterCard;Amex;Discover;Debit |
    | Gift card provider | Enter the gift card provider that the connector should use to process gift cards. This field is case-sensitive. | No | No | "svs" or "givex" |
    | Terminal gift card entry | (*POS only*) Allows the customer to select between **Manual** or **Swipe**. | Yes | Yes | True/False |
    | Allow saving payment information in e-commerce | (*E-commerce only*) Gives signed-in users the option to save payment details for future online purchases. | Yes | Yes | True/False |
    | Authorization stale period (days) | (*POS only*) Number of days before an authorization is considered stale and should decline before going to the processor for capture. | Yes | Yes | "7" |
    | Origin Key | (*Card not present only*) |
    | EnableRequestProtection | Adds retry logic to "card not present" payment calls, reducing potential for duplicate calls using a correlation ID. If set to **True**, a correlation ID is added to provider requests to prevent duplicates. If set to **False**, calls are sent to the provider without the correlation ID or duplicate protection logic. | No | No | True/False |
    | Nonincremental capture payment methods | Names of the payment method variant or card types used by Adyen to identify card types in authorization responses that don't support incremental capture. Value entered should match the payment method variant/card type string used in Adyen to reference, as noted in [Adyen PaymentMethodVariant](https://docs.adyen.com/development-resources/paymentmethodvariant).  | No | No | "amexcommercial" |
    | Disable terminal line display | Removes the itemized digital receipt lines from the terminal interface used for preview to shoppers before paying. Disabling the terminal line display is helpful for smaller, handheld terminal devices. | No | No | True/False |
    | Omitted payment methods | (*E-commerce and call center only*) |

1. On the Action Pane, select **Save**.

> [!NOTE]
> When setting up a local POS instance, you still need to provide the **Cloud API** key field for "card not present" scenarios to work. Such scenarios include omnichannel payments customer orders created in POS, linked refunds, and payment authorization token references on order pickups.

##### EFT service for cloud communication

1. On the **EFT service** FastTab, in the **EFT Service** field, select **Payment Connector**.
1. On the **Connectors** tab, select **New**, and then in the **Connector** field, select **Dynamics 365 Payment Connector for Adyen**. Ensure that the value in the **Sequence number** field is lower than the value for all other connectors.
1. In the **Connector properties** section, enter the following information.

    | Field | Description | Required | Automatically set | Sample value |
    | ----- | ----------- | :------: | :---------------: | ------------ |
    | Assembly Name | Autopopulated name of the assembly for the Dynamics 365 Payment Connector for Adyen. | Yes | Yes | *Binary name* |
    | Service account ID | Autopopulated unique identifier for the setup of the merchant properties. This identifier is stamped on payment transactions and identifies the merchant properties that downstream processes (such as invoicing) should use. | Yes | Yes | *Guid* |
    | Version | Set to **V003** for EFT settings in the hardware profile. **V002** is required for call center and storefront only. Version **V001** is no longer supported. | Yes | Yes | "V003" |
    | Gateway environment | Enter the Adyen gateway environment to which to map. The possible values are **Test** and **Live**. Set this field to **Live** only for production devices and transactions. | Yes | Yes | Live |
    | Optional Domain | The optional domain is required for live environments and you should contact Adyen to obtain it. This domain is the unique identifier for your live environment in the format **[random]-[company name]**, and appears as the prefix inside the API URLs under **Account** > **API URLs** in your company's live account on the Adyen Customer Area portal. For more information, see [Live endpoints](https://docs.adyen.com/development-resources/live-endpoints).| Live only | No | Contact Adyen |
    | Merchant account ID | Enter the unique Adyen merchant identifier. Adyen provides this value when you sign up, as described in the [Sign up with Adyen](#sign-up-with-adyen) section. | Yes | No | MerchantIdenfier |
    | Terminal architecture | Set this field to **Cloud** for cloud communication with the payment terminal. | Yes | Yes | Cloud |
    | Local Password phrase | This setting is used for local payment terminal communication only. | No | No | *leave blank* |
    | Local Key Identifier | This setting is used for local payment terminal communication only. | No | No | *leave blank* |
    | Local Key Version | This setting is used for local payment terminal communication only. | No | No | *leave blank* |
    | Local Cryptor Version | This setting is used for local payment terminal communication only. You can leave the default as-is, set to **1**. | Yes | Yes | 1 |
    | Cloud API Key | Enter the Adyen cloud API key. Obtain this key by following the instructions on the [Generate an API key](https://docs.adyen.com/development-resources/api-credentials#generate-an-api-key) page on the Adyen website. | Yes | No | abcdefg |
    | Supported Currencies | Enter the currencies that the connector should process. In card-present scenarios, Adyen can support additional currencies through [Dynamic Currency Conversion](https://www.adyen.com/pos-payments/dynamic-currency-conversion) after the transaction request is sent to the payment terminal. Contact Adyen support to get a list of supported currencies. | Yes | Yes | USD;EUR |
    | Supported Tender Types | Enter the tender types that the connector should process. These values are case-sensitive. | Yes | Yes | Visa;MasterCard;Amex;Discover;Debit |
    | Gift card provider | Enter the gift card provider that the connector should use to process gift cards. This field is case-sensitive. | No | No | "svs" or "givex" |
    | Terminal gift card entry | (*POS only*) Allows the customer to select between **Manual** or **Swipe**. | Yes | Yes | True/False |
    | Allow saving payment information in e-commerce | (*E-commerce only*) Gives signed-in users the option to save payment details for future online purchases. | Yes | Yes | True/False |
    | Authorization stale period (days) | (*POS only*) Number of days before an authorization is considered stale and should decline before going to the processor for capture. | Yes | Yes | "7" |
    | Origin Key | (*Card not present only*) |
    | EnableRequestProtection | Adds retry logic to "card not present" payment calls, reducing potential for duplicate calls using a correlation ID. If set to **True**, a correlation ID is added to provider requests to prevent duplicates. If set to **False**, calls are sent to the provider without the correlation ID or duplicate protection logic. | No | No | True/False |
    | Nonincremental capture payment methods | Names of the payment method variant or card types used by Adyen to identify card types in authorization responses that don't support incremental capture. Value entered should match the payment method variant/card type string used in Adyen to reference, as noted in [Adyen PaymentMethodVariant](https://docs.adyen.com/development-resources/paymentmethodvariant).  | No | No | "amexcommercial" |
    | Disable terminal line display | Removes the itemized digital receipt lines from the terminal interface used for preview to shoppers before paying. Disabling the terminal line display is helpful for smaller, handheld terminal devices. | No | No | True/False |
    | Omitted payment methods | (*E-commerce and call center only*) |

1. On the Action Pane, select **Save**.

##### Configure the PIN pad

To configure the PIN pad, follow these steps:

1. On the **PIN pad** FastTab, in the **PIN pad** field, select **Network**.
1. In the **Device name** field, enter **MicrosoftAdyenDeviceV001**.

> [!NOTE]
> To route to region-specific endpoints, see [Route to the region-specific Adyen endpoint](adyen-connector-setup.md#route-to-the-region-specific-adyen-endpoint).

#### Set up a Dynamics 365 register

> [!NOTE]
> These instructions assume that there's a dedicated mapping between a POS register and an Adyen payment terminal. For a hardware station based on Microsoft Internet Information Services (IIS), go to **Retail and Commerce \> Channels \> Stores \> All stores**, and select the store that you're setting up. Then, on the page for that store, on the **Hardware Stations** FastTab, follow the same instructions.

Payment terminals can't be used by multiple hardware stations. If a payment terminal is shared by multiple POS devices, you must deploy an IIS hardware station to manage communications with the payment terminal.

##### Configure the payment terminal IP address and EFT POS register number

1. In Commerce headquarters, go to **Retail and Commerce** > **Channel setup** > **POS setup** > **Registers**.
1. Select the register to link to the Adyen payment terminal.
1. On the **POS Registers** page, on the **General** FastTab, in the **EFT** section, enter a unique number in the **EFT POS register number** field.
1. In the **Profiles** section, select the hardware profile that you configured earlier in the **Hardware profile** field.
1. Save your changes.
1. On the **Register** tab, in the **Hardware** group, select **Configure IP addresses**.
        1. If using the "Local" architecture, on the **IP address configuration** page, on the **PIN pad** FastTab, enter the IP address of the terminal in the **IP address** field in the following format: `https://<IP address>:8443/nexo/<POIID>`. `IP address` and `POIID` are the values that you noted when you onboarded the Adyen payment terminal (for example, `https://192.168.1.3:8443/nexo/MX925-123456789`). The values in this URL are case-sensitive.
        1. If using the "Cloud" architecture, on the **IP address configuration** page, on the **PIN pad** FastTab, enter the **POIID** value that you noted when you onboarded the Adyen payment terminal in the **IP address** field (for example, `MX925-123456789`). The values in this field are case-sensitive.
1. If the payment terminal includes an onboard printer and you want to print receipts from the processor by using that printer, enter **123** in the **Port** field that's separate from the **IP address** field in the **PIN pad** FastTab.

#### Update the Store Commerce app or IIS Hardware Station configuration

If you're packaging your own version of the Store Commerce app by using the Commerce SDK, follow these steps only one time in the SDK code before you package the installer. Otherwise, follow these steps after you install the standard Store Commerce app or IIS Hardware Station.

1. Open the **dllhost.exe.config** file (for Store Commerce app) or the **web.config** file (for IIS Hardware Station).
1. To switch from the legacy payment device adapter to the standard payment device adapter, update the **PreloadedComposition** section as shown here:

    ``` xml
    <PreloadedComposition>
        <composition>
            <add source="assembly" value="Microsoft.Dynamics.Commerce.HardwareStation.Peripherals.PaymentDeviceAdapter" />
            <!-- Switch from legacy to standard Payment Device Adapter.
            <add source="assembly" value="Microsoft.Dynamics.Commerce.HardwareStation.Peripherals.Legacy.PaymentDeviceAdapter" />
            -->
        </composition>
    </PreloadedComposition>
    ```

1. Update the **appSettings** variable **"PrintReceiptsOnCardDeclineOrVoid"** value to **True** to print decline or void responses from the processor.

### Configure the connector for call center payments

To configure the Dynamics 365 Payment Connector for Adyen for call center payments, follow the instructions in the [Set up a processor for new credit cards](#set-up-a-processor-for-new-credit-cards) section earlier in this article.

Use the configuration in headquarters at **Accounts receivable** > **Payments setup** > **Payment service** as the connector configuration in the call center. The call center doesn't support 3D Secure (3DS) authentication. The call center also doesn't support digital wallet modern payment methods that require users to sign in, because call center agents can't collect or use user passwords on behalf of customers.

> [!NOTE]
> Merchants should train call center users to enter credit and debit card information only in the iFrame payment form to reduce the risk of a sensitive data breach.

### Configure the Adyen connector for online stores

To configure the Adyen connector for online stores, follow these steps:

1. Go to **Retail and Commerce** > **Channels** > **Online stores**.
1. Select the online store to add the Dynamics 365 Payment Connector for Adyen.
1. On the **Online store** page, on the **Payment accounts** FastTab, select **Add**.
1. In the **Connectors** field, select **Dynamics 365 Payment Connector for Adyen**.
1. Enter the following information.

    | Field | Description | Required | Automatically set | Sample value |
    | ----- | ----------- | :------: | :---------------: | ------------ |
    | Assembly Name | Auto populated name of the assembly for the Dynamics 365 Payment Connector for Adyen. | Yes | Yes | *Binary name* |
    | Service account ID | Auto populated unique identifier for the setup of the merchant properties. This identifier is stamped on payment transactions and identifies the merchant properties that downstream processes (such as invoicing) should use. | Yes | Yes | *Guid* |
    | Version | Enter the version of the Dynamics 365 Payment Connector for Adyen to use. Version "V003" should be used for all new implementations. Version "V002" is available while origin key functionality is still supported by Adyen. Version "V001" is no longer supported. | Yes | Yes | "V002"/"V003" |
    | Gateway environment | Enter the Adyen gateway environment to which to map. The possible values are **Test** and **Live**. | Yes | Yes | Live |
    | Optional Domain | Enter the domain to use when payment requests are made to Adyen. This domain is the unique identifier for your live environment in the format **[random]-[company name]**, and is present as the prefix inside the API URLs under **Account** > **API URLs** in your company's live account on the Adyen Customer Area portal. For more information, see, [Live endpoints](https://docs.adyen.com/development-resources/live-endpoints). | Live only | No | Contact Adyen |
    | Merchant account ID | Enter the unique Adyen merchant identifier. Adyen provides this value when you sign up, as described in the [Sign up with Adyen](#sign-up-with-adyen) section. | Yes | No | MerchantIdenfier |
    | Terminal architecture | This field is used only for the POS payment terminal integration and should be left blank. | No | Yes | *Leave this field blank.* |
    | Local Password phrase | This field is used only for the POS payment terminal integration and should be left blank. | No | Yes | *Leave this field blank.* |
    | Local Key Identifier | This field is used only for the POS payment terminal integration and should be left blank. | No | Yes | *Leave this field blank.* |
    | Local Key Version | This field is used only for the POS payment terminal integration and should be left blank. | No | Yes | *Leave this field blank.* |
    | Local Cryptor Version | Enter the Adyen cryptor version to use when you interact with the Adyen gateway. You should set this field to **1**. | Yes | No | 1 |
    | Cloud API Key | Enter the Adyen cloud API key. You can obtain this key by following the instructions on the [Generate an API key](https://docs.adyen.com/development-resources/api-credentials#generate-an-api-key) page on the Adyen website. | Yes | No | *The full cloud API key* |
    | Supported Currencies | Enter the currencies that the connector should process. | Yes | Yes | USD;EUR |
    | Supported Tender Types | Enter the tender types that the connector should process. | Yes | Yes | Visa;MasterCard;Amex;Discover;Debit |
    | Gift card provider | Enter the gift card provider that the connector should use to process gift cards. The possible values are **SVS** and **GIVEX**. | No | No | SVS |
    | Terminal gift card entry | (POS only*) Allows the customer to select between **Manual** or **Swipe**. | Yes | Yes | True/False |
    | Allow saving payment information in e-commerce | (*E-commerce only*) Gives signed-in users the option to save payment details for future online purchases. | Yes | Yes | True/False |
    | Authorization stale period (days) | (*POS only*) Number of days before an authorization is considered stale and should decline before going to the processor for capture. | Yes | Yes | "7" |
    | Origin Key ("V002") or Client key ("V003") | (*E-commerce only*) 'An origin key value is required when "V002" is the designated version. For instructions on obtaining this key, see [How to get an origin key](https://docs.adyen.com/development-resources/how-to-get-an-origin-key). A client key value is required when "V003" is the designated version. For instructions on obtaining this key, see [Migrate to Client key](https://docs.adyen.com/development-resources/client-side-authentication/migrate-from-origin-key-to-client-key#switch-to-using-the-client-key). | Yes | No | *The full origin or client key* |
    | EnableRequestProtection | Adds retry logic to "card not present" payment calls, reducing potential for duplicate calls using a correlation ID. If set to **True**, a correlation ID is added to provider requests to prevent duplicates. If set to **False**, calls are sent to the provider without the correlation ID or duplicate protection logic. | No | No | True/False |
    | Nonincremental capture payment methods | Names of the payment method variant or card types used by Adyen to identify card types in authorization responses that don't support incremental capture. Value entered should match the payment method variant/card type string used in Adyen to reference, as noted in [Adyen PaymentMethodVariant](https://docs.adyen.com/development-resources/paymentmethodvariant). | No | No | "amexcommercial" |
    | Disable terminal line display | Removes the itemized digital receipt lines from the terminal interface shown to customers before paying. Disabling the terminal line display can be helpful to users of smaller, handheld terminal devices. | No | No | True/False |
    | Omitted payment methods | (*E-commerce and call center only*) Use this field to omit a payment method from the configuration where an iFrame element is rendered for payments as configured against the merchant account. Separate multiple values with semicolons. Strings used must match the label used in the Adyen portal. Some payment method's security criteria might interfere with the iFrame rendering, so it might be desirable to omit conflicting security criteria from the configuration. | No | No | "applepay;googlepay" |

1. On the Action Pane, select **Save**.

> [!IMPORTANT]
>
> - If 3D Secure (3DS) is enabled with Adyen, you must complete the following required steps if they apply to your setup.
>      1. If you're using Commerce versions 10.0.40, 10.0.41, or 10.0.42, in Commerce headquarters, go to the online channel mapped to your e-commerce website.
>      1. Expand the Adyen payment connector setup section, and in the **Custom settings** property of the payment connector, add the following key value pair: `{"D365PaymentsIsCheckoutThreeDS1AuthorisationBehaviorEnabled": "true"}`.
>      1. Run the **1070** and **1110** distribution schedule jobs. After these jobs finish, you must contact Adyen customer support to set the **checkoutThreeDS1AuthorisationBehavior** parameter to **Manual** for your merchant account.
> - Starting with Commerce version 10.0.43, you don't need to update the **Custom settings** property in Commerce headquarters because it's enabled by default. However, you must still contact Adyen customer support to set the **checkoutThreeDS1AuthorisationBehavior** parameter to **Manual** for your merchant account.

## Route to the region-specific Adyen endpoint

The following table lists the minimum component versions required to use region-specific Adyen endpoints.

| Component | 10.0.44 | 10.0.45 | 10.0.46 |
| --------- | ------- | ------- | ------- |
| Cloud POS | 9.54.25283.4 | 9.55.25283.6 | Enabled by default |
| Store Commerce app | 9.54.25290.2 | 9.55.25283.5 | Enabled by default |
| Hardware Station | 9.54.25283.3 | 9.55.25289.8 | Enabled by default |
| Commerce headquarters | 10.0.2263.95 | 10.0.2345.19 | Enabled by default |

### Set up in-person payments via payment terminals

Starting with Commerce version 10.0.44, you can use region-specific endpoints for Adyen endpoints. Enter the following supported values in the **Gateway environment** property of the payment connector in the hardware profile that the POS register uses.

- test
- live
- live-us
- live-au
- live-apse

> [!NOTE]
> Leave the payment connector **Optional Domain** property value blank for POS use. The system ignores any value you specify.

This functionality is behind a flight named **UseNewGatewayMappingForTerminal**. The following list shows its status for the various versions:  

- **Commerce version 10.0.46**: Enabled by default.
- **Commerce versions 10.0.45 and 10.0.44**: Disabled by default. 

For Commerce versions 10.0.44 and 10.0.45, customers can enable this functionality themselves by adding the string `"UseNewGatewayMappingForTerminal": true, "UseNewGatewayMapping": true` to the **Custom settings** property of the connector.  

### Set up card-not-present payments through call center and online stores

Starting with Commerce version 10.0.44, you can use region-specific endpoints for Adyen endpoints. Enter the following supported values in the **Gateway environment** property of the payment connector on the **Payment services** form (for call center) or **Online store** form (for e-commerce):

- test
- live
- live-us
- live-au
- live-apse

All live gateways, including those that start with **live-**, require a prefix to ensure that all requests route to the correct server. To find the prefix value, go to the Adyen portal under **Developers** > **API URLs**, select the appropriate data center based on your region, and then copy the prefix value. Depending on the channel where you're making this change, paste the prefix into the **Optional Domain** property field of the payment connector under the **Payment services** form or the **Online store** form. Adyen recommends using endpoints that are geographically closest to the region where your infrastructure is deployed. To use location-based live endpoints, contact the Adyen Support team.

> [!IMPORTANT]
> If you don't specify the **Optional Domain** value, payment processing issues occur because the checkout gateway uses the incorrect endpoint.

This change is behind a flight named **UseNewGatewayMapping**, and its status for the various versions is as follows:

- Commerce version 10.0.46: Enabled by default  
- Commerce versions 10.0.45 and 10.0.44: Disabled by default

For Commerce versions 10.0.44 and 10.0.45, customers can enable this functionality themselves by adding the string **"UseNewGatewayMapping": true** to the **Custom settings** property of the connector.  

## Next steps

For answers to frequently asked questions about the Dynamics 365 Payment Connector for Adyen, see [Dynamics 365 Payment Connector for Adyen FAQ](adyen-connector-faq.md).

## Related information

- [Dynamics 365 Payment Connector for Adyen overview](adyen-connector.md)
- [Dynamics 365 Payment Connector for Adyen FAQ](adyen-connector-faq.md)
- [Troubleshoot Dynamics 365 Payment Connector for Adyen](adyen-connector-troubleshoot.md)
- [Payments FAQ](/dynamics365/unified-operations/retail/dev-itpro/payments-retail)

[!INCLUDE [footer-include](../../includes/footer-banner.md)]
