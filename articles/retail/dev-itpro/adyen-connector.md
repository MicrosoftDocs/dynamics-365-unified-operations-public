---
# required metadata

title: Configure Adyen connector
description: Configure Adyen connector 
author: aamirallaqaband
manager: AnnBe
ms.date: 07/22/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.search.industry: Retail
ms.author: aamiral
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1

---

# Configure Adyen connector
This topic describes how to configure the Microsoft Adyen payment connector.

## Key terms

## Overview
The Microsoft Adyen payment connector uses the Adyen Terminal API for card present payments and Adyen gateway for card not present payments. Adyen can allow sharing of credit card tokens between Adyen subscriptions and D365 channels.
## Limitations
The following limitations are applied to the Microsoft Adyen connector:
* Maximum EFT POS register number 9999 and each of these must be unique per register per Adyen subscription
* Card not present only supports refunds to the original payment for Call Center and A/R payments.

## D365 Configuration
This section describes how to configure the Microsoft Adyen connector for the different channels
### AX Hardware profile setup
In the EFT service section select the EFT service dropdown and assign it to "Payment Connector". Then click the grid +New button so the "Microsoft Adyen Processor" can be selected from the connector dropdown. Make sure the new Microsoft Adyen connector sequence number is smallest. The connector with the smallest sequence number will be the default connector assigned to the Microsoft Adyen payment terminal. Below is a list of merchant properties supported by the Microsoft Adyen connector:
Property name | Description | Channel
------------- | ----------- | -------
Assembly name | Read only field containing the strong name for the Microsoft Adyen connector. | All
Service account Id | Guid to uniquely identifier the Microsoft Adyen connector for this profile. | All
Version | The connector version to be used. Allows different versions of the connector to co-exist, defaults to latest version. | Gateway
Environment | Environment points to Test/Live/Custom | Gateway and Cloud Terminal
Optional Domain | (Custom live only domain) [Adyen](https://docs.adyen.com/developers/development-resources/live-endpoints#liveendpointsstructure) [random]-[company name] | Gateway and Cloud Terminal
Merchant account Id | The merchant account identifier [Adyen](https://ca-test.adyen.com/ca/ca/accounts/show.shtml?accountTypeCode=MerchantAccount) has assigned to your account | All
Terminal architecture | Local or Cloud based communication to terminals | Terminal
Local password phrase | [Adyen](https://docs.adyen.com/developers/point-of-sale-integration/terminal-api-integration/getting-started-adyen-terminal-api/adyen-terminal-api-architecture/local-communication-to-the-terminal/terminal-api-out-of-band-encryption/encrypting-messages#backofficeconfiguration) supplied password phrase used to encrypt communication between POS and devices | Local Terminal
Local key identifier | Adyen supplied key identifier, use default value | Local Terminal
Local key version | Adyen supplied key version, use default value | Local Terminal
Local cryptor version | Adyen supplied cryptor version, use default value | Local Terminal
Cloud API key | [Adyen](https://docs.adyen.com/developers/user-management/how-to-get-the-checkout-api-key) supplied API gateway key | Gateway and Cloud Terminal
Supported currencies | Currencies supported by channel | All
Supported tender types | Tender types supported by channel | All
Gift card provider | Optional Adyen gift card provider | Terminal
The PIN pad must be set to Network and the Device name MicrosoftAdyenDeviceVXXX where XXX = latest version number

### AX Register setup
If the local hardware station is to be used in MPOS, then carry out the following configuration. Find the required register and click on its link. Make sure the EFT POS register number is unique and only 4 digits in length. Also make sure the registers hardware profile is pointing to one configured to use the Adyen payment connector. In the action panel of the form click on "Configure IP Address" and edit the PIN pad->IP Address. There are two possible IP Addresses
* Cloud based requires just the "POIID"
 * POIID = Adyen terminal ID found by pressing 5 and green button on terminal or Adyen's portal site.
* Local based requires https://"ip address":8443/nexo/"POIID"
 * ip address found on device by pressing 5 and green button on terminal or Adyen's portal site.

### AX All Retail Stores setup
If the shared hardware station is to be used, then carry out the following configuration. Find the required store and click on its link. Scroll down to the hardware station tab and make the same changes you made for the register but this time for a hardware station.

### AX Distribution Schedule
Run the 1070 and 1090 jobs to push the updated profile data down to the stores. If shared hardware station is being used make sure you run the Hardware Station Configuration Utility on each hardware station to make the updated profile avaiable.

### Trouble shooting
Please look for errors and warnings in the windows event viewer, filter the following event ID (7500 - 7599) and (7600 - 7699)
* AX
 * Application and Services Logs->Microsoft->Dynamics->Commerce-LoggingProvider->Operational
* MPOS
 * Application and Services Logs->Microsoft->Dynamics->Commerce-ModernPos->Operational
* Shared hardware station
 * Application and Services Logs->Microsoft->Dynamics->Commerce-HardwareStation->Operational

####Common issues
* AX
 * Connector not displayed in connector dropdown
 * 
* MPOS & Shared Hardware Station
 * Device does not display line items
 * 
