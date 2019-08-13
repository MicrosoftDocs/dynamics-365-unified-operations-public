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
The module react component can access a read only request context object to get request information, which includes properties such as the URL, user, locale and device type information.

## Example
Below example shows how to access request properties fromwithin the request context:

```
if (this.props.context.request.user.isAuthenticated) {
    userName = this.props.context.request.user.signinName ? this.props.context.request.user.signinName : '';
    firstName = this.props.context.request.user.firstName ? this.props.context.request.user.firstName : '';
    lastName = this.props.context.request.user.lastName ? this.props.context.request.user.lastName : '';
}      
```

## General Properties
* url - Provided the requested URL
* locale - The locale context (example "en-us")
* market - The market context 
* textDirection - The text direction, possible values "rtl" and "ltr"
* sitePath - The sites full path
* params - List of supported query string parameters includes:
  * mock - Name of mock file specified
  * isDebug - Debug setting
  * isEditor - Editor setting
  * concatJs - ConcatJs value
  * theme - Theme specificed
* device - Device request came from
  * Type - Device type (example: 'pc')
* user - Information about the user including
  * toekn
  * isAuthenticated
  * signinURL
  * signoutURL
  * signUpUrl
  * editProfileUrl
  * signinName
  * name
  * firstName
  * lastName
  * emailAddress
  * customerAccountNumber
* query - List of query string parameters
* cookies - Cookie information

## Interface

```
export interface IRequestContext {
    url: {
        serverUrl: string;
        serverPageUrl: string;
        requestUrl: URL;
        staticCdnUrl: string;
    };
    locale: string;
    market?: string;
    textDirection: string;
    sitePath?: string;
    params: {
        mock?: string;
        isDebug: boolean;
        isEditor: boolean;
        concatJs: IParsedQSP<boolean | string | number | undefined>;
        theme: string;
    };
    device: {
        Type: string;
    };
    user: {
        token: string;
        isAuthenticated: boolean;
        signInUrl?: string;
        signOutUrl?: string;
        signUpUrl?: string;
        editProfileUrl?: string;
        signinName?: string;
        name?: string;
        firstName?: string;
        lastName?: string;
        emailAddress?: string;
        customerAccountNumber?: string;
    };
    app: IGeneric<IAny>;
    query?: IDictionary<string>;
    apiSettings: ICommerceApiSettings;
    gridSettings?: IGridSettings;
    urlTokens: IUrlTokens;
    operationId: string;
    features: {
        [switchName: string]: boolean;
    };
    pageData: IGeneric<IAny>;
    headers: {
        readonly [header: string]: string;
    };
    cookies: ICookieContext;
}
```
