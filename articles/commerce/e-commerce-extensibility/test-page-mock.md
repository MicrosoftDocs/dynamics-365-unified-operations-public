---
# required metadata

title: Test modules by using page mocks
description: This topic describes how to test modules by using page mocks.
author: samjarawan
manager: annbe
ms.date: 09/15/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
#ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Test modules by using page mocks

[!include [banner](../includes/banner.md)]

This topic describes how to test modules by using page mocks.

## Overview

Some modules are built to interact with other modules. You can use page mocks to test those modules together in a local development environment.

Page mock files are stored under the /src/pageMocks directory. They can be loaded by using the URL `https://localhost:4000/page?mock=PAGE_MOCK`, where **PAGE\_MOCK** is the file name of the mock file, but without the **.json** file name extension.

## Create a new page mock

To create a new page mock, create a blank .json file under the /src/pageMocks directory, such as **/src/pageMocks/campaign-page.json**.

## Example

The following example shows a page mock that adds two instances of the same module to a page but uses different mock data for each instance.

```json
{
    "exception": null,
    "pageRoot": {
        "id": "core-root_0",
        "typeName": "core-root",
        "modules": {
            "body": [
                {
                    "id": "default-page_0",
                    "typeName": "default-page",
                    "modules": {
                        "primary": [
                            {
                                "id": "ProductFeature__0",
                                "typeName": "product-feature",
                                "config": {
                                    "imageAlignment": "left",
                                    "buttonText": "Buy Now",
                                    "productIds": "68719490621"
                                }
                            },
                            {
                                "id": "ProductFeature__1",
                                "typeName": "product-feature",
                                "config": {
                                    "imageAlignment": "right",
                                    "productIds": "68719498121",
                                    "buttonText": "Buy Now"
                                }
                            }
                        ]
                    }
                }
            ]
        }
    },
    "renderingContext": {
        "gridSettings": {
            "xs": {
                "w": 767
            },
            "sm": {
                "w": 991
            },
            "md": {
                "w": 1199
            },
            "lg": {
                "w": 1599
            },
            "xl": {
                "w": 1600
            }
        },
        "staticContext": {
            "staticCdnUrl": "/_scnr/"
        },
        "locale": "en-us"
    },
    "statusCode": 200
}
```

Every page defines a root (**core-root** in the example above) that controls the page HTML structure with slots for "HTML Head", "Body Begin", "Body" and "Body End". The **body** then must have a page container module. In this example, the **default-page** page container is used.

The **modules** section lists the modules that are included inside the page arranged by named slots. The **default-page** page container has a slot that is named **primary**. This container is responsible for laying out the modules that are included inside it. In this example, the **productFeature** module is rendered two times in a row with the mock data defined in the **config** section for each.

The preceding example can be accessed by using the following URL: `https://localhost:4000/page?mock=campaign-page`.

## Rendering context mocks

The **renderingContext** node provides additional mock data that modules can access via the **this.props.context.request** object. This mock data can include the bootstrap grid breakpoints, the locale, and the user context. For more information, see [Request properties object](request-properties-object.md).

### Simulate the signed-in state

Some modules might have logic that must check the signed-in state of the user before they take the appropriate action. Typically, a module gets the state from the **this.props.context.request.user** object. Because business-to-consumer (B2C) sign-in isn't supported in a development environment, the user object can be mocked by using the **user** node, as shown in the following example.

```json
{
    "exception": null,
    "pageRoot": {
        "id": "core-root_0",
        "typeName": "core-root",
        "modules": {
            "body": [
                {
                    "id": "default-page_0",
                    "typeName": "default-page",
                    "modules": {
                        "primary": [
                            {
                                "id": "ProductFeature__0",
                                "typeName": "product-feature",
                                "config": {
                                    "imageAlignment": "left",
                                    "buttonText": "Buy Now",
                                    "productIds": "68719490621"
                                }
                            }
                        ]
                    }
                }
            ]
        }
    },
    "renderingContext": {
        "gridSettings": {
            "xs": {
                "w": 767
            },
            "sm": {
                "w": 991
            },
            "md": {
                "w": 1199
            },
            "lg": {
                "w": 1599
            },
            "xl": {
                "w": 1600
            }
        },
        "staticContext": {
            "staticCdnUrl": "/_scnr/"
        },

        "user": {
            "token": "<TOKEN>",
            "isAuthenticated": true,
            "signInUrl": "https://dev.fabrikam.com/fedev/_msdyn365/signin",
            "signOutUrl": "https://dev.fabrikam.com/fedev/_msdyn365/signout",
            "signUpUrl": "https://dev.fabrikam.com/fedev/_msdyn365/signup",
            "editProfileUrl": "https://dev.fabrikam.com/fedev/_msdyn365/editprofile",
            "signinName": "<User Name>",
            "firstName": "<User First Name>",
            "lastName": "<User Last Name>",
            "tenantId": "",
            "customerAccountNumber": "<User Account Number(HQ)>",
            "name": "<User Name>",
            "emailAddress": "<User Email Address>"
        },
        "locale": "en-us"
    },
    "statusCode": 200
}
```

If you must simulate real data or the token that is returned from Commerce Server after a user signs in, sign in to your production e-Commerce site, and use the F12 browser tools to copy the data. The user information is available in the **\_\_\_initialData\_\_\_.requestContext.user** global JavaScript variable. While the F12 browser tools are open and a user is signed in, open a console window, and enter **\_\_\_initialData\_\_\_.requestContext.user** to see the object. You can then update the **userContext** properties in the preceding example as required. Those properties include **token**, **signinName**, **firstName**, **lastName**, **customerAccountNumber**, **name**, and **emailAddress**.

## Create a dynamic page mock from a production e-Commerce page

You can create dynamic page mocks that mimic live e-Commerce site pages and can be used locally to test module interaction. For example, these page mocks can mock the signed-in state and other page contextual properties as required. Therefore, they can be helpful when you locally test pages such as account pages and wishlist pages, or interactions such as order checkout flow.

### Save a live e-Commerce page's raw JSON structure

The raw JavaScript Object Notation (JSON) structure of any live e-Commerce page can be captured and saved so that it can be used as a page mock. Open the e-Commerce site page that you want to capture, and sign in if the signed-in state is desired. Next, append the query string parameter `?item=nodeserviceproxy:true` to the page URL, and then reload the page to obtain the JSON of the raw page context.

> [!NOTE]
> For this operation to work, you must have secure Azure Active Directory (Azure AD) access to your production site, and you might be prompted to sign in if you aren't already signed. Use the same Azure AD account that you use to sign in to Commerce site builder.

Next, in your development environment, create a new page mock JSON file under the **src/pageMocks** directory. Paste in the JSON file that you obtained from the capture and save operation. 

The structure of the JSON file should have sections that resemble the sections in the following example. These sections should include the **pageRoot** section that defines the set of modules for the page and the **renderingContext** section that includes the **user** context for signed-in user information.

```
{
    "exception": null,
    "pageRoot": {
        "id": "core-root_0",
        "typeName": "core-root",
        "modules": {
        }
    },
    "renderingContext": {
    …
        "user": {
        ...
        }
    },
    "statusCode": 200
    …
}
```

To test the page mock locally, start your Node server by using **yarn start** command. Access the page mock by using the URL format `https://localhost:4000/page?mock=PAGE_MOCK`, where **PAGE\_MOCK** is the file name of the mock file without the **.json** file name extension.

You can now modify the page mock as desired.

## Additional resources

[Create a new module](create-new-module.md)

[Clone a module library module](clone-starter-module.md)

[Add module configuration fields](add-module-config-fields.md)

[Preview and debug a module](test-module.md)

[Test modules by using module mocks](test-module-mock.md)

[Container modules](container-modules.md)

[Create a layout container module](create-layout-container.md)

[Create a page container module](create-page-containers.md)

[Localize a module](localize-module.md)
