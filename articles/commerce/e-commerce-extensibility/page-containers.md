---
# required metadata

title: Request Properties
description: The module react component can access a read only request context object to get request information, which includes properties such as the URL, user, locale and device type information.
author: SamJarawan
manager: annbe
ms.date: 08/30/2019
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: SamJar
ms.search.validFrom: 2019-08-30
ms.dyn365.ops.version: 

---
# Request Properties
The module React component can access a read only request context object to get request information, which includes properties such as the URL, user, locale and device type information.

## Example
Below example shows how to access request properties from within the request context:

```
if (this.props.context.request.user.isAuthenticated) {
    userName = this.props.context.request.user.signinName ? this.props.context.request.user.signinName : '';
    firstName = this.props.context.request.user.firstName ? this.props.context.request.user.firstName : '';
    lastName = this.props.context.request.user.lastName ? this.props.context.request.user.lastName : '';
}      
```

## General Properties
```
{
    "url": {
        "serverUrl": "https://dev.fabrikam.com",
        "serverPageUrl": "https://dev.fabrikam.com/render/",
        "requestUrl": "https://dev.fabrikam.com/fedev",
        "staticCdnUrl": "//dev.fabrikam.com/_msdyn365/_scnr/"
    },
    "urlTokens": {},
    "locale": "en-US",
    "textDirection": "ltr",
    "sitePath": "/fedev",
    "device": { "Type": "Pc" },
    "user": {
        "token": null,
        "isAuthenticated": false,
        "signInUrl": "https://dev.fabrikam.com/fedev/_msdyn365/signin",
        "signOutUrl": "https://dev.fabrikam.com/fedev/_msdyn365/signout",
        "signUpUrl": "https://dev.fabrikam.com/fedev/_msdyn365/signup",
        "editProfileUrl": "https://dev.fabrikam.com/fedev/_msdyn365/editprofile",
        "signinName": null,
        "firstName": null,
        "lastName": null,
        "tenantId": "",
        "customerAccountNumber": null,
        "name": null,
        "emailAddress": null
    },
    "app": {
        "config": {
            "rnrTenantId": "d247ff89-1bb8-42bf-955e-a731fbc57c75",
            "outOfStockThreshold": -1,
            "maxQuantityForCartLineItem": 10,
            "enableStockCheck": false,
            "reviewTextMaxLength": 5000,
            "reviewTitleMaxLength": 5,
            "disableTooltip": false,
            "disableBopis": false
        },
        "routes": {
            "cart": { "destinationUrl": "/fedev/cart", "type": "internalLink" },
            "checkout": { "destinationUrl": "/fedev/checkout", "type": "internalLink" },
            "account": { "destinationUrl": "/fedev/myaccount", "type": "internalLink" },
            "accountProfile": { "destinationUrl": "/fedev/myprofile", "type": "internalLink" },
            "orderDetails": { "destinationUrl": "/fedev/orderdetails", "type": "internalLink" },
            "wishlist": { "destinationUrl": "/fedev/wishlist", "type": "internalLink" },
            "orderConfirmation": { "destinationUrl": "/fedev/order-confirmation", "type": "internalLink" },
            "home": { "destinationUrl": "/fedev/", "type": "internalLink" },
            "loyalty": { "destinationUrl": "/fedev/loyalty", "type": "internalLink" },
            "loyaltyJoin": { "destinationUrl": "/fedev/loyalty-join", "type": "internalLink" }
        },
        "platform": {
            "maintenanceMode": false,
            "imageQuality": 80,
            "pageTitleSuffix": "- Fabrikam",
            "skipToMainText": "Skip to main section"
        }
    },
    "query": {},
    "apiSettings": {
        "baseUrl": "https://rushe2e-tie-sb10cddc845e563b6c8ret.cloudax.test.dynamics.com/",
        "channelId": 5637145359,
        "catalogId": 0,
        "oun": "077",
        "baseImageUrl": "https://cms-ppe-imageresizer-mr.trafficmanager.net/cms/api/fabrikamsb/imageFileData/search?fileName=/",
        "ratingsReviewsEndpoint": "https://pod001.rnr-ppe.ms",
        "retailServerProxyVersion": "9.16.7"
    },
    "operationId": "23be59094df11f4bb5a6f5004bcbfbe5",
    "params": { 
        "mock": "",
        "isDebug": false,
        "isEditor": false
    }   
    "features": { "scnr_blob": true, "disable_cors": true, "action_timeout": true },
    "_debug": { "commerceSDKVersion": "1.7.9", "commerceSSKVersion": "1.32.0-alpha.17925028.0" },
    "requestUrl": "https://dev.fabrikam.com/fedev",
    "clientContext": { "deviceType": "Pc" },
    "staticContext": {
        "staticCdnUrl": "//dev.fabrikam.com/_msdyn365/_scnr/",
        "staticCdnUrlWithLocale": "//dev.fabrikam.com/en-US/_msdyn365/_scnr/"
    },
    "userContext": {
        "token": null,
        "isAuthenticated": false,
        "signInUrl": "https://dev.fabrikam.com/fedev/_msdyn365/signin",
        "signOutUrl": "https://dev.fabrikam.com/fedev/_msdyn365/signout",
        "signUpUrl": "https://dev.fabrikam.com/fedev/_msdyn365/signup",
        "editProfileUrl": "https://dev.fabrikam.com/fedev/_msdyn365/editprofile",
        "signinName": null,
        "firstName": null,
        "lastName": null,
        "tenantId": "",
        "customerAccountNumber": null,
        "name": null,
        "emailAddress": null
    },
    "previewContext": null,
    "gridSettings": { 
        "xs": { "w": 767 },
        "sm": { "w": 991 },
        "md": { "w": 1199 },
        "lg": { "w": 1599 },
        "xl": { "w": 1600 } },
    "debugMode": 0,
    "channel": {
        "RecordId": 5637145359,
        "ChannelNaturalId": "000037",
        "MinimumDepositPercentage": 0,
        "QuoteExpirationDays": 30,
        "PickupDeliveryModeCode": "60",
        "CarryoutDeliveryModeCode": "70",
        "CancellationChargePercentage": 5,
        "InventLocation": "DC-CENTRAL",
        "InventLocationDataAreaId": "usrt",
        "BingMapsApiKey": "AsT9sGxyCe-vqAfUvCYXruaZOjujSb114E4pwCGYX5tWLiUm1Dkoaegz1-r3wWKN",
        "BingMapsEnabled": true,
        "Currency": "USD",
        "CatalogDefaultImageTemplate": "Catalogs/{LanguageId}/{CatalogName}.jpg",
        "CompanyCurrency": "USD",
        "PriceIncludesSalesTax": false,
        "CountryRegionId": "USA",
        "ChannelCountryRegionISOCode": "US",
        "DefaultLanguageId": "en-us",
        "TimeZoneInfoId": "CENTRAL STANDARD TIME",
        "EmailDeliveryModeCode": "12",
        "GiftCardItemId": "9999",
        "EnableProductRecommendations": true,
        "RefundableShippingAmountWithoutApproval": 0,
        "RefundShippingCharges": false,
        "ReceiptSettingsValue": 0,
        "CustomerAttributeGroupId": 68719476773,
        "NotificationRefreshInterval": 0,
        "AllowExchangeOnReturnOrders": false,
        "FiscalRegistrationProcessId": null,
        "ProfileProperties": [
            {
                "Key": 1,
                "Value": "https://rushe2e-tie-sb10cddc845e563b6c8ret.cloudax.test.dynamics.com/Commerce",
                "ExtensionProperties": []
            },
            { "Key": 7, "Value": "https://rushe2e-tie-sb10cddc845e563b6c8pos.cloudax.test.dynamics.com/", "ExtensionProperties": [] },
            {
                "Key": 2,
                "Value": "https://cms-eastus-ppe-imageresizer-mr.cloudapp.net/cms/api/fabrikamsb/imageFileData/search?fileName=",
                "ExtensionProperties": []
            }
        ],
        "Properties": [
            {
                "Name": "SyncAnchor",
                "Value": "...",
                "Channel": 5637145359,
                "ExtensionProperties": []
            }
        ],
        "Languages": [{ "LanguageId": "en-us", "IsDefault": true, "ExtensionProperties": [] }],
        "UseAdvancedAutoCharges": true,
        "UseRTSForOnlineOrderCreation": false,
        "EnableProductRatingsForRetailStores": false,
        "EnableReturnsForMultipleOrderInvoices": false,
        "VoidSuspendedTransactionsOnCloseShift": 0,
        "EnableOmniChannelPayments": false,
        "UseAdvancedCashManagement": false,
        "EnableFiscalRegistrationStorageBackup": false,
        "SalesOrderHeaderAttributeGroups": [],
        "SalesOrderLinesAttributeGroups": [],
        "ExtensionProperties": []
    },
    "cookies": {...},
    "headers": {...}
}
```
