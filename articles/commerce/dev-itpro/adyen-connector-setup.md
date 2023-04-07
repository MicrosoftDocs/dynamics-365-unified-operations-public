---
title: Set up Dynamics 365 Payment Connector for Adyen
description: This article describes how to sign up with Adyen and set up the Microsoft Dynamics 365 Payment Connector for Adyen.
author: Reza-Assadi
ms.date: 04/07/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: rassadi
ms.search.validFrom: 2019-01-01
ms.dyn365.ops.version: AX 7.0.1
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.industry: Retail
---

# Set up Dynamics 365 Payment Connector for Adyen

[!include [banner](../includes/banner.md)]

This article describes how to sign up with Adyen and set up the Microsoft Dynamics 365 Payment Connector for Adyen. For an overview of the Dynamics 365 Payment Connector for Adyen, see [Dynamics 365 Payment Connector for Adyen overview](adyen-connector.md).

## Sign up with Adyen

To use the Dynamics 365 Payment Connector for Adyen, you must have a separate agreement with Adyen. To learn more about Adyen's services, or to create a test merchant account, visit the [Adyen website](https://www.adyen.com/signup).

## Setup and configuration

> [!NOTE]
> These instructions assume that you've already signed up for a merchant account with Adyen, and that you have access to the Adyen merchant dashboard.

> [!IMPORTANT]
> Adyen no longer supports [hosted payment pages](https://docs.adyen.com/online-payments/classic-integrations/hosted-payment-pages) as of October 2022. When configuring the Dynamics 365 Payment Connector for Adyen, version V001 will no longer be supported for call center and e-commerce because it uses hosted payment pages from Adyen. Instead, use version V002 (with origin key) or version V003 (with client key). Version V003 is recommended by Microsoft and is available in Commerce versions 10.0.29 and higher. Also, ensure that you set the **Allowed Origins** in the Adyen configuration by adding the full URL (for example, 'https://www.adventure-works.com') for your site (for e-commerce) or Commerce headquarters (for call center).

### Prerequisites

The following prerequisites must be completed before payments can be configured in any channel.

#### Configure your Adyen account settings for Dynamics 365 Commerce

In addition to the instructions below, you must also configure your Adyen account settings for Dynamics 365 Commerce. For instructions on setting up Adyen for Dynamics 365 Commerce, see [Set up the Adyen payment connector for Dynamics 365](https://docs.adyen.com/plugins/microsoft-dynamics).

#### Set up a processor for new credit cards

To process payments across point of sale (POS) terminals, a call center, or Commerce, you must configure a new default payment processor for new credit cards. Follow these steps to configure a default payment processor.

1. Sign in to Commerce headquarters and go to **Accounts receivable \> Payments setup \> Payment services**.
1. On the Action Pane, select **New**, and then, on the **Setup** tab, enter the following information.

    | Field | Description | Sample value |
    |---|---|---|
    | Payment service | Enter the name of the payment service to configure. | Adyen Payment Service |
    | Payment connector | Select the payment connector to use for new credit card payments. | Dynamics 365 Payment Connector for Adyen |
    | Test mode | For the Adyen connector, in production and test environments you should set this field to **false**. | false |
    | Default processor for credit cards | Specify whether this payment processor should be the default processor that's used for new credit cards. | Yes |
    | Bypass payment processor for zero transactions | Specify whether this payment processor should be skipped for transactions that have a 0 (zero) amount. | Yes |

1. On the **Payment service account** tab, enter the following information.

    | Field | Description | Required | Automatically set | Sample value |
    |---|---|:-:|:-:|---|
    | Assembly Name | Auto populated name of the assembly for the Dynamics 365 Payment Connector for Adyen. | Yes | Yes | *Binary name* |
    | Service account ID | Auto populated unique identifier for the setup of the merchant properties. This identifier is stamped on payment transactions and identifies the merchant properties that downstream processes (such as invoicing) should use. | Yes | Yes | *Guid* |
    | Version | Enter the version of the Dynamics 365 Payment Connector for Adyen to use. Version "V003" should be used for all new implementations. Version "V002" is available while origin key functionality is still supported by Adyen. Version "V001" is no longer supported.  | Yes | Yes | "V002"/"V003" |
    | Gateway environment | Enter the Adyen gateway environment to map to. The possible values are **Test** and **Live**. You should set this field to **Live** only for production devices and transactions. | Yes | Yes | Live |
    | Optional Domain | The optional domain is required for live environments and should be obtained by contacting Adyen. This domain is the unique identifier for your live environment in the form **[random]-[company name]**, and is present as the prefix inside the API URLs under **Account \> API URLs** in your company's live account on the Adyen Customer Area portal. For more information, see [Live endpoints](https://docs.adyen.com/development-resources/live-endpoints). | Live only | No | Contact Adyen |
    | Merchant account ID | Enter the unique Adyen merchant identifier. This value is provided when you sign up with Adyen as described in the [Sign up with Adyen](#sign-up-with-adyen) section. | Yes | No | MerchantIdentifier |
    | Terminal architecture | This field must be set to **Cloud** for the `Payment service account`. | Yes | Yes | Cloud |
    | Local Password phrase | This field is used only for the POS payment terminal integration and should be left blank. | No | Yes | *Leave this field blank.* |
    | Local Key Identifier | This field is used only for the POS payment terminal integration and should be left blank. | No | Yes | *Leave this field blank.* |
    | Local Key Version | This field is used only for the POS payment terminal integration and should be left blank. | No | Yes | *Leave this field blank.* |
    | Local Cryptor Version | Enter the Adyen cryptor version to use when you interact with the Adyen gateway. You should set this field to **1**. | Yes | Yes | 1 |
    | Cloud API Key | Enter the Adyen cloud API key. You can obtain this key by following the instructions on the [Generate an API key](https://docs.adyen.com/development-resources/api-credentials#generate-an-api-key) page on the Adyen website. | Yes | No | abcdefg |
    | Supported Currencies | Enter the currencies that the connector should process. In card-present scenarios, Adyen can support additional currencies through [Dynamic Currency Conversion](https://www.adyen.com/pos-payments/dynamic-currency-conversion) after the transaction request is sent to the payment terminal. Contact Adyen support to get a list of supported currencies. | Yes | Yes | USD;EUR |
    | Supported Tender Types | Enter the tender types that the connector should process. | Yes | Yes | Visa;MasterCard;Amex;Discover;Debit |
    | Gift card provider | Enter the gift card provider that the connector should use to process gift cards. This field is case-sensitive. | No | No | "svs" or "givex" |
    | Terminal gift card entry | (*POS only*) Allows the customer to select between **Manual** or **Swipe**. | Yes | Yes | True/False |
    | Allow saving payment information in e-commerce | (*E-commerce only*) Gives signed-in users the option to save payment details for future online purchases.  | Yes | Yes | True/False |
    | Authorization stale period (days) | (*POS only*) Number of days before an authorization is considered stale and should decline before going to the processor for capture. | Yes | Yes | "7" |
    | Origin Key ("V002") or Client Key ("V003") | An origin key value is required when "V002" is the designated version. For instructions on obtaining this key, see [How to get an origin key](https://docs.adyen.com/development-resources/how-to-get-an-origin-key). A client key value is required when "V003" is the designated version. For instructions on obtaining this key, see [Migrate to Client key](https://docs.adyen.com/development-resources/client-side-authentication/migrate-from-origin-key-to-client-key#switch-to-using-the-client-key).| Yes | No | *The full origin or client key* |
    | EnableRequestProtection | Adds retry logic to "card not present" payment calls, reducing potential for duplicate calls using a correlation ID. When "True", a correlation ID is added to provider requests to prevent duplicates. If "False", calls are sent to the provider without the correlation ID or duplicate protection logic. | No | No | True/False |
    | Non-incremental capture payment methods | Names of the payment method variant or card types used by Adyen to identify card types in authorization responses that don't support incremental capture. Value entered should match the payment method variant/card type string used in Adyen to reference, as noted in [Adyen PaymentMethodVariant](https://docs.adyen.com/development-resources/paymentmethodvariant).  | No | No | "amexcommercial" |
    | Disable terminal line display | Removes the itemized digital receipt lines from the terminal interface used for preview to shoppers before paying. Disabling terminal line display is helpful for smaller, handheld terminal devices. | No | No | True/False |
    | Omitted payment methods | (*E-commerce and call center only*) Use this field to omit a payment method from the configuration where an iFrame element is rendered for payments as configured against the merchant account. Separate multiple values with semicolons. Strings must match the label used in the Adyen portal. Some payment method security criteria may interfere with the iFrame element rendering, so it may be desirable to omit conflicting security criteria from the configuration.  | No | No | "applepay;googlepay" |

1. On the **Card verification value** tab, leave **Prompt for card verification value** and **Allow blank card verification value** set to **No**. 

### POS payment terminal

#### Onboard and configure an Adyen payment terminal

> [!NOTE]
> These instructions assume that you have access to an Adyen payment terminal.

Go to the [In-person payments](https://docs.adyen.com/point-of-sale) page on the Adyen website and follow the instructions to onboard your Adyen payment terminal. Skip any steps that instruct you to download Adyen-specific apps. During the onboarding process, make a note of the following information for each payment terminal. You'll need this information in the [Configure the payment terminal IP address and EFT POS register number](#configure-the-payment-terminal-ip-address-and-eft-pos-register-number) section later in this article.

- IP address of the payment terminal
- POIID (POIID is composed of the serial number and model number of the device. It's used to uniquely identify the device.)

After the payment terminal is onboarded, sign in to the [Adyen Customer Area](https://ca-test.adyen.com/ca/ca/login.shtml), go to the terminal that you want to configure, and make a note of the following information for each payment terminal. You'll need this information in the [EFT service for local network communication](#eft-service-for-local-network-communication) section later in this article.

- Key identifier
- Key passphrase
- Key version

#### Set up a Dynamics 365 POS hardware profile

1. Sign in to Commerce headquarters and go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Hardware profiles**.
1. Select the hardware profile to add the Dynamics 365 Payment Connector for Adyen for.
1. Follow the steps in the [EFT service](#eft-service) and [PIN pad](#configure-the-pin-pad) sections that follow.

#### EFT service

The Adyen payment connector can be configured to communicate with devices via the local network or through Adyen's cloud backend. For environments with unreliable internet service, or where offline mode is required, the **Local** setup should be used. For environments with strong internet connections, or if a static IP address can't be assigned to the payment terminal, the **Cloud** architecture may work best.

##### EFT service for local network communication

1. On the **EFT service** FastTab, in the **EFT Service** field, select **Payment Connector**.
1. On the **Connectors** tab, select **New**, and then, in the **Connector** field, select **Dynamics 365 Payment Connector for Adyen**. Make sure that the value in the **Sequence number** field is lower than the value for all other connectors.
1. In the **Connector properties** section, enter the following information.

    | Field | Description | Required | Automatically set | Sample value |
    |---|---|:-:|:-:|---|
    | Assembly Name | Auto populated name of the assembly for the Dynamics 365 Payment Connector for Adyen. | Yes | Yes | *Binary name* |
    | Service account ID | Auto populated unique identifier for the setup of the merchant properties. This identifier is stamped on payment transactions and identifies the merchant properties that downstream processes (such as invoicing) should use. | Yes | Yes | *Guid* |
    | Version | Set to **V001** for EFT settings in the hardware profile. **V002** is required for call center and storefront only.  | Yes | Yes | "V001" |
    | Gateway environment | Enter the Adyen gateway environment to map to. The possible values are **Test** and **Live**. You should set this field to **Live** only for production devices and transactions. | Yes | Yes | Live |
    | Optional Domain | The optional domain is required for live environments and should be obtained by contacting Adyen. This domain is the unique identifier for your live environment in the format **[random]-[company name]**, and is present as the prefix inside the API URLs under **Account \> API URLs** in your company's live account on the Adyen Customer Area portal. For more information, see [Live endpoints](https://docs.adyen.com/development-resources/live-endpoints).| Live only | No | Contact Adyen |
    | Merchant account ID | Enter the unique Adyen merchant identifier. This value is provided when you sign up with Adyen as described in the [Sign up with Adyen](#sign-up-with-adyen) section. | Yes | No | MerchantIdenfier |
    | Terminal architecture | This field must be set to **Local** for local communications. For more information about the different Terminal API architectures, see the [Introducing the Terminal API](https://www.adyen.com/blog/introducing-the-terminal-api) page on the Adyen website. | Yes | Yes | Local |
    | Local Password phrase | Enter the Adyen key passphrase for the payment terminal. This value is provided when you sign up with Adyen as described in the [Sign up with Adyen](#sign-up-with-adyen) section. | Yes | No | keypassphrase123 |
    | Local Key Identifier | Enter the Adyen key identifier for the payment terminal. This value is provided when you sign up with Adyen as described in the [Sign up with Adyen](#sign-up-with-adyen) section. | Yes | No | mykey |
    | Local Key Version | Enter the Adyen key version for the payment terminal. This value is provided when you sign up with Adyen as described in the [Sign up with Adyen](#sign-up-with-adyen) section. | Yes | No | 0 |
    | Local Cryptor Version | Enter the Adyen cryptor version to use when you interact with the Adyen gateway. You should set this field to **1**. | Yes | Yes | 1 |
    | Cloud API Key | Enter the Adyen cloud API key. You can obtain this key by following the instructions on the [Generate an API key](https://docs.adyen.com/development-resources/api-credentials#generate-an-api-key) page on the Adyen website. This field is required even for local terminal setups. | Yes | No | abcdefg |
    | Supported Currencies | Enter the currencies that the connector should process. In card-present scenarios, Adyen can support additional currencies through [Dynamic Currency Conversion](https://www.adyen.com/pos-payments/dynamic-currency-conversion) after the transaction request is sent to the payment terminal. Contact Adyen support to get a list of supported currencies. | Yes | Yes | USD;EUR |
    | Supported Tender Types | Enter the tender types that the connector should process. These values are case-sensitive. | Yes | Yes | Visa;MasterCard;Amex;Discover;Debit |
    | Gift card provider | Enter the gift card provider that the connector should use to process gift cards. This field is case-sensitive. | No | No | "svs" or "givex" |    
    | Terminal gift card entry | (*POS only*) Allows the customer to select between **Manual** or **Swipe**. | Yes | Yes | True/False |
    | Allow saving payment information in e-commerce | (*E-commerce only*) Gives signed-in users the option to save payment details for future online purchases.  | Yes | Yes | True/False |
    | Authorization stale period (days) | (*POS only*) Number of days before an authorization is considered stale and should decline before going to the processor for capture. | Yes | Yes | "7" |
    | Origin Key | (*Card not present only*)  |
    | EnableRequestProtection | Adds retry logic to "card not present" payment calls, reducing potential for duplicate calls using a correlation ID. When "True", a correlation ID is added to provider requests to prevent duplicates. If "False", calls are sent to the provider without the correlation ID or duplicate protection logic. | No | No | True/False |
    | Non-incremental capture payment methods | Names of the payment method variant or card types used by Adyen to identify card types in authorization responses that don't support incremental capture. Value entered should match the payment method variant/card type string used in Adyen to reference, as noted in [Adyen PaymentMethodVariant](https://docs.adyen.com/development-resources/paymentmethodvariant).  | No | No | "amexcommercial" |
    | Disable terminal line display | Removes the itemized digital receipt lines from the terminal interface used for preview to shoppers before paying. Disabling the terminal line display is helpful for smaller, handheld terminal devices. | No | No | True/False |
    | Omitted payment methods | (*E-commerce and call center only*) |

1. On the Action Pane, select **Save**.

> [!NOTE]
> When setting up a local POS instance, the **Cloud API** key field is still required for "card not present" scenarios to work. Such scenarios include omnichannel payments customer orders created in POS, linked refunds, and payment authorization token references on order pickups.

##### EFT service for cloud communication

1. On the **EFT service** FastTab, in the **EFT Service** field, select **Payment Connector**.
1. On the **Connectors** tab, select **New**, and then in the **Connector** field, select **Dynamics 365 Payment Connector for Adyen**. Make sure that the value in the **Sequence number** field is lower than the value for all other connectors.
1. In the **Connector properties** section, enter the following information.

    | Field | Description | Required | Automatically set | Sample value |
    |---|---|:-:|:-:|---|
    | Assembly Name | Autopopulated name of the assembly for the Dynamics 365 Payment Connector for Adyen. | Yes | Yes | *Binary name* |
    | Service account ID | Autopopulated unique identifier for the setup of the merchant properties. This identifier is stamped on payment transactions and identifies the merchant properties that downstream processes (such as invoicing) should use. | Yes | Yes | *Guid* |
    | Version | Set to **V001** for EFT settings in the hardware profile. **V002** is required for call center and storefront only.  | Yes | Yes | "V001" |
    | Gateway environment | Enter the Adyen gateway environment to map to. The possible values are **Test** and **Live**. You should set this field to **Live** only for production devices and transactions. | Yes | Yes | Live |
    | Optional Domain | The optional domain is required for live environments and should be obtained by contacting Adyen. This domain is the unique identifier for your live environment in the format **[random]-[company name]**, and is present as the prefix inside the API URLs under **Account \> API URLs** in your company's live account on the Adyen Customer Area portal. For more information, see [Live endpoints](https://docs.adyen.com/development-resources/live-endpoints).| Live only | No | Contact Adyen |
    | Merchant account ID | Enter the unique Adyen merchant identifier. This value is provided when you sign up with Adyen as described in the [Sign up with Adyen](#sign-up-with-adyen) section. | Yes | No | MerchantIdenfier |
    | Terminal architecture | This field must be set to **Cloud** for cloud communication with the payment terminal. For more information about the different terminal API architectures, see the [Introducing the Terminal API](https://www.adyen.com/blog/introducing-the-terminal-api) page on the Adyen website. | Yes | Yes | Cloud |
    | Local Password phrase | This setting is used for local payment terminal communication only. | No | No | *leave blank* |
    | Local Key Identifier | This setting is used for local payment terminal communication only. | No | No | *leave blank* |
    | Local Key Version | This setting is used for local payment terminal communication only. | No | No | *leave blank* |
    | Local Cryptor Version | This setting is used for local payment terminal communication only. You can leave the default as-is, set to **1**. | Yes | Yes | 1 |
    | Cloud API Key | Enter the Adyen cloud API key. You can obtain this key by following the instructions on the [Generate an API key](https://docs.adyen.com/development-resources/api-credentials#generate-an-api-key) page on the Adyen website. | Yes | No | abcdefg |
    | Supported Currencies | Enter the currencies that the connector should process. In card-present scenarios, Adyen can support additional currencies through [Dynamic Currency Conversion](https://www.adyen.com/pos-payments/dynamic-currency-conversion) after the transaction request is sent to the payment terminal. Contact Adyen support to get a list of supported currencies. | Yes | Yes | USD;EUR |
    | Supported Tender Types | Enter the tender types that the connector should process. These values are case-sensitive. | Yes | Yes | Visa;MasterCard;Amex;Discover;Debit |
    | Gift card provider | Enter the gift card provider that the connector should use to process gift cards. This field is case-sensitive. | No | No | "svs" or "givex" |    
    | Terminal gift card entry | (*POS only*) Allows the customer to select between **Manual** or **Swipe**. | Yes | Yes | True/False |
    | Allow saving payment information in e-commerce | (*E-commerce only*) Gives signed-in users the option to save payment details for future online purchases.  | Yes | Yes | True/False |
    | Authorization stale period (days) | (*POS only*) Number of days before an authorization is considered stale and should decline before going to the processor for capture. | Yes | Yes | "7" |
    | Origin Key | (*Card not present only*) |
    | EnableRequestProtection | Adds retry logic to "card not present" payment calls, reducing potential for duplicate calls using a correlation ID. When "True", a correlation ID is added to provider requests to prevent duplicates. If "False", calls are sent to the provider without the correlation ID or duplicate protection logic. | No | No | True/False |
    | Non-incremental capture payment methods | Names of the payment method variant or card types used by Adyen to identify card types in authorization responses that don't support incremental capture. Value entered should match the payment method variant/card type string used in Adyen to reference, as noted in [Adyen PaymentMethodVariant](https://docs.adyen.com/development-resources/paymentmethodvariant).  | No | No | "amexcommercial" |
    | Disable terminal line display | Removes the itemized digital receipt lines from the terminal interface used for preview to shoppers before paying. Disabling terminal line display is helpful for smaller, handheld terminal devices. | No | No | True/False |
    | Omitted payment methods | (*E-commerce and call center only*) |

1. On the Action Pane, select **Save**.

##### Configure the PIN pad

1. On the **PIN pad** FastTab, in the **PIN pad** field, select **Network**.
1. In the **Device name** field, enter **MicrosoftAdyenDeviceV001**.

#### Set up a Dynamics 365 register

> [!NOTE]
> These instructions assume that there is a dedicated mapping between a POS register and an Adyen payment terminal. For a hardware station that is based on Microsoft Internet Information Services (IIS), go to **Retail and Commerce \> Channels \> Stores \> All stores**, and select the store that you're setting up. Then, on the page for that store, on the **Hardware Stations** FastTab, follow the same instructions.

Payment terminals may not be used by multiple hardware stations. If a payment terminal must be shared by multiple POS devices, an IIS hardware station must be deployed to manage communications with the payment terminal. 

##### Configure the payment terminal IP address and EFT POS register number

1. In Commerce headquarters, go to **Retail and Commerce \> Channel setup \> POS setup \> Registers**.
1. Select the register to link to the Adyen payment terminal.
1. On the **POS Registers** page, on the **General** FastTab, in the **EFT** section, in the **EFT POS register number** field, enter a unique number. 
1. In the **Profiles** section, in the **Hardware profile** field, select the hardware profile that you configured earlier.
1. Save your changes.
1. On the Action Pane, on the **Register** tab, in the **Hardware** group, select **Configure IP addresses**.
    1. **If using the "Local" architecture:** On the **IP address configuration** page, on the **PIN pad** FastTab, in the **IP address** field, enter the IP address of the terminal in the following format: `https://<IP address>:8443/nexo/<POIID>`. **\<IP address\>** and **\<POIID\>** are the values that you made a note of when you onboarded the Adyen payment terminal (for example, `https://192.168.1.3:8443/nexo/MX925-123456789`). The values in this URL are case-sensitive.
    1. **If using the "Cloud" architecture:** On the **IP address configuration** page, on the **PIN pad** FastTab, in the **IP address** field, enter the **POIID** value that you made a note of when you onboarded the Adyen payment terminal (for example, `MX925-123456789`). The values in this field are case-sensitive.
1. If the payment terminal includes an onboard printer and you want to print receipts from the processor using that printer, enter **123** in the **Port** field that is separate from the **IP address** field in the **PIN pad** FastTab.

#### Update the Store Commerce app or IIS Hardware Station configuration

If you're packaging your own version of the Store Commerce app by using the Commerce SDK, you must follow these steps only one time in the SDK code before the installer is packaged. Otherwise, you must follow these steps after the standard Store Commerce app or IIS Hardware Station is installed.

1. Open the **dllhost.exe.config** file (for Store Commerce app) or the **web.config** file (for IIS Hardware Station).
1. Update the **PreloadedComposition** section as shown here, to switch from the legacy payment device adapter to the standard payment device adapter.

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

The configuration in headquarters at **Accounts receivable \> Payments setup \> Payment service** is the connector configuration used in the call center. 3D Secure (3DS) authentication isn't supported in call center. Digital wallet modern payment methods requiring users to sign in are also not supported in call center, because call center agents are prohibited from collecting or using user passwords on behalf of customers.

### Configure additional information for the connector

To configure additional information for the connector in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Channels \> Online stores**.
1. Select the online store to add the Dynamics 365 Payment Connector for Adyen.
1. On the **Online store** page, on the **Payment accounts** FastTab, select **Add**.
1. In the **Connectors** field, select **Dynamics 365 Payment Connector for Adyen**.
1. Enter the following additional information.

    | Field | Description | Required | Automatically set | Sample value |
    |---|---|:-:|:-:|---|
    | Assembly Name | Auto populated name of the assembly for the Dynamics 365 Payment Connector for Adyen. | Yes | Yes | *Binary name* |
    | Service account ID | Auto populated unique identifier for the setup of the merchant properties. This identifier is stamped on payment transactions and identifies the merchant properties that downstream processes (such as invoicing) should use. | Yes | Yes | *Guid* |
    | Version | Enter the version of the Dynamics 365 Payment Connector for Adyen to use. Version "V003" should be used for all new implementations. Version "V002" is available while origin key functionality is still supported by Adyen. Version "V001" is no longer supported.  | Yes | Yes | "V002"/"V003" |
    | Gateway environment | Enter the Adyen gateway environment to map to. The possible values are **Test** and **Live**. | Yes | Yes | Live |
    | Optional Domain | Enter the domain to use when payment requests are made to Adyen. This domain is the unique identifier for your live environment in the format **[random]-[company name]**, and is present as the prefix inside the API URLs under **Account \> API URLs** in your company's live account on the Adyen Customer Area portal. For more information, see, [Live endpoints](https://docs.adyen.com/development-resources/live-endpoints). | Live only | No | Contact Adyen |
    | Merchant account ID | Enter the unique Adyen merchant identifier. This value is provided when you sign up with Adyen as described in the [Sign up with Adyen](#sign-up-with-adyen) section. | Yes | No | MerchantIdenfier |
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
    | Allow saving payment information in e-commerce | (*E-commerce only*) Gives signed-in users the option to save payment details for future online purchases.  | Yes | Yes | True/False |
    | Authorization stale period (days) | (*POS only*) Number of days before an authorization is considered stale and should decline before going to the processor for capture. | Yes | Yes | "7" |
    | Origin Key ("V002") or Client key ("V003") | (*E-commerce only*) 'An origin key value is required when "V002" is the designated version. For instructions on obtaining this key, see [How to get an origin key](https://docs.adyen.com/development-resources/how-to-get-an-origin-key). A client key value is required when "V003" is the designated version. For instructions on obtaining this key, see [Migrate to Client key](https://docs.adyen.com/development-resources/client-side-authentication/migrate-from-origin-key-to-client-key#switch-to-using-the-client-key). | Yes | No | *The full origin or client key* |
    | EnableRequestProtection | Adds retry logic to "card not present" payment calls, reducing potential for duplicate calls using a correlation ID. When "True", a correlation ID is added to provider requests to prevent duplicates. If "False", calls are sent to the provider without the correlation ID or duplicate protection logic. | No | No | True/False |
    | Non-incremental capture payment methods | Names of the payment method variant or card types used by Adyen to identify card types in authorization responses that don't support incremental capture. Value entered should match the payment method variant/card type string used in Adyen to reference, as noted in [Adyen PaymentMethodVariant](https://docs.adyen.com/development-resources/paymentmethodvariant).  | No | No | "amexcommercial" |
    | Disable terminal line display | Removes the itemized digital receipt lines from the terminal interface used for preview to shoppers before paying. Disabling terminal line display is helpful for smaller, handheld terminal devices. | No | No | True/False |
    | Omitted payment methods | (*E-commerce and call center only*) Use this field to omit a payment method from the configuration where an iFrame element is rendered for payments as configured against the merchant account. Separate multiple values with semicolons. Strings used must match the label used in the Adyen portal. Some payment method's security criteria may interfere with the iFrame rendering, so it may be desirable to omit conflicting security criteria from the configuration.  | No | No | "applepay;googlepay" |

1. On the Action Pane, select **Save**.

## Next steps

For answers to frequently asked questions regarding the Dynamics 365 Payment Connector for Adyen, see [Dynamics 365 Payment Connector for Adyen FAQ](adyen-connector-faq.md).

## Additional resources

[Dynamics 365 Payment Connector for Adyen overview](adyen-connector.md)

[Dynamics 365 Payment Connector for Adyen FAQ](adyen-connector-faq.md)

[Troubleshoot Dynamics 365 Payment Connector for Adyen](adyen-connector-troubleshoot.md)

[Payments FAQ](/dynamics365/unified-operations/retail/dev-itpro/payments-retail)

[!INCLUDE [footer-include](../../includes/footer-banner.md)]
