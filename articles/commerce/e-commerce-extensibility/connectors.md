---
title: Configure and enable connectors
description: This article describes connectors and explains how to configure and enable them in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 02/03/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.13
ms.custom: 
ms.assetid: 
---

# Configure and enable connectors

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article describes connectors and explains how to configure and enable them in Microsoft Dynamics 365 Commerce.

Connectors let you connect your Dynamics 365 Commerce site to external third-party services to perform tasks such as capturing analytics, logging, and experimenting. Some third-party service providers require a paid license for their service before it can be used. For more information, contact your service provider.

As of Commerce version 10.0.13, the only supported type of connector is the experimentation connector. As of Commerce version 10.0.17, support for the geoLookup connector has been added. As of Commerce version 10.0.21, the segmentation provider connector is supported. In future versions, you'll be able configure and enable other types of connectors.

## Configure and enable connectors

You can add connectors to your Commerce site by adding them as a dependency in your **package.json** file. Alternatively, you can implement them directly in your configuration package code under the **\\src\\connectors** directory.

### Connector settings file

Connectors are configured and enabled in the **connector.settings.json** file under the **\\src\\settings** directory. If no **connector.settings.json** file exists, you can manually create one. In this file, you can specify the experimentation connector that you want to use and configure it as you require. Only one experimentation connector can be used at a time.

The following example shows the contents of the **connector.settings.json** file that defines several connectors.

```json
{
    "experimentation": {
        "name": "msdyn365-exp-test-2",
        "config": {
            "sdkKey": "EXPERIMENTATION_PROVIDER_KEY",
            "key2": "value2"
        },
        "cacheConfig": {
            "ttlInSeconds": {
                "experimentation": 1800,
                "experimentationDataFile": 300
            },
            "ttrInSeconds": {
                "experimentation": 10
            }
        }
    },
    "geoLookup": {
        "name": "GeoLocationTest",
        "config": {
            "apiKey": "GEOLOCATION_SERVICE_PROVIDER_API_KEY"
        },
        "cacheConfig": {
            "ttlInSeconds": {
                "geoLookup": 10
            }
        }
    },
    "segmentation": [
        {
            "id": "100",
            "config": {
                "apiKey": "testApiKey"
            }
        }       
    ]
}
```

#### Connector settings file schema

| Element | Details |
| -- | -- |
| experimentation | This object contains all the information that is required to start and enable your experimentation connector. |
| name | This setting specifies the name of the experimentation connector that is used. You can find the name of the connector in the connector's definition file. The type of the connector must be **experimentationConnector**. |
| config | This section allows for any configuration object that the connector requires for initialization and to start to communicate with the third-party service. To learn what information is required, look in the **configSchema** section of the connector's definition file or in the connector's README file. |
| cacheConfig | You can specify the timings that are used when some experimentation-related entities are cached. In this section, **ttlInSeconds** refers to the amount of time that an entity can remain in the cache before it's considered stale, and **ttrInSeconds** refers to the amount of time before an entity is refreshed. The connector's README file should include a list of recommended cache timings. |
| experimentation | This setting controls the cache timings for getting the list of available experiments that are configured in your third-party provider during **getExperiments()**. The default TTL (time to live) is 1,800 seconds, and the default TTR (time to refresh) is 60 seconds. |
| experimentationDataFile | This setting controls the cache timings for having the configuration passed down to the client during **getConfigForClientSideInit()**. The default TTL is 1,800 seconds, and the default TTR is 60 seconds. |


## Experimentation connector

An experimentation connector lets you connect your application to an external experimentation service provider. By adding this type of connector to your application, configuring it, and enabling it, you can create and run experiments in Commerce site builder, and track outcomes, to provide the best experience for your customers.

An experimentation connector consists of three parts:

- A connector definition file in JSON format
- A provider file
- A listener file

### Connector definition file

A connector definition file is used to register and provide configuration metadata data to your application. This metadata includes the type of connector, the name of the connector, a description of the connector, and the configuration schema. The name of the connector definition file is in the format **\<CONNECTOR\_NAME\>.connector.json**.

The following example shows the contents of a connector definition file.

```json
{
    "$type": "experimentationConnector",
    "name": "msdyn365-exp-test",
    "description": "Test connector implementation",
    "configSchema": {
        "type": "object",
        "properties": {
          "projectId": {
            "type": "string",
            "description": "The project ID to use for experimentation"
          }
        },
        "required": ["projectId"]
    }
}
```

#### Connector definition file schema

| Element | Details |
| -- | -- |
| $type | The type of connector. Because the definition file in the preceding example is for an experimentation connector, the type is **experimentationConnector**. |
| name | The name of the connector. This name must be unique across all connectors. |
| description | The description of the connector. |
| configSchema | The configuration schema. A configuration schema lets you provide a JSON schema that validates the configuration that is given to you at application startup, so that your connector can be initialized correctly. For example, when you initialize your connector, you need the **projectId** value to make an API call that is required for communication with the third-party experimentation service. You can specify this value in the preceding JSON file to ensure that the configuration that is provided matches your connector's requirements. |

### Provider file

An experimentation provider file is required to initialize a connector. It also enables the connector to interact with Commerce site builder to present a list of available experiments that are configured in your third-party experimentation service. The name of the provider file is in the format **\<CONNECTOR\_NAME\>.provider.ts**.

The provider file should implement the following interface.

```typescript
export interface IExperimentationProvider {
    /**
     * Allows the experimentation connector to do any startup related tasks
     * using the config provided by the partner.
     *
     * This method is only called once during server startup.
     * @param config The configuration provided in connector.settings.json
     */
    initialize(config: any): Promise<boolean>;

    /**
     * Returns the configuration that should be passed to the experimentation connector
     * when it is initialized client-side
     */
    getConfigForClientSideInit(): Promise<any>;

    /**
     * Initializes the experimentation provider on the browser (client-side) so that
     * it may activate experiments for a user.
     *
     * @param config The config that is required to initialize the experimentation connector
     * client-side. The result of getConfigForClientSideInit() is passed into this method
     */
    initializeClientSide(config: any): boolean;

    /**
     * Returns a list of all the experiments currently configured whether active or not.
     * This list will be cached and periodically refreshed.
     * @param page Optional argument that specifies the page to return.
     * @param items Optional argument that specifies the maximum number of objects to return per request.
     */
    getExperiments(page?: string, items?: string): Promise<IExperiments[]>;

    /**
     * Returns a list of experiments and variants a user will be a part of based
     * off the userId. Optional attributes can provide the connector with additional criteria
     * to determine which experiments a user should be a part of.
     *
     * @param userId userId unique to a user if signed in or unique to a session if user is anonymous.
     * userId will be generated from hash if user is signed-in to deterministically generate sanitized userIds.
     * @param attributes Optional user related attributes
     */
    getVariantsForUser(userId: string, attributes?: {
        [index: string]: string;
    }): IVariants[];

    /**
     * Activates experiment(s) a user is currently being served. This call will be made
     * client-side after the connector has been initialized client-side
     *
     * @param userId userId unique to a user if signed in or unique to a session if user is anonymous.
     * userId will be generated from hash if user is signed-in to deterministically generate sanitized userIds.
     * @param experiments The experiments the user is participating in.
     * @param attributes Optional user related attributes
     */
    activateExperiment(userId: string, experiments: IVariants[], attributes?: {
        [index: string]: string;
    }): boolean;
}
```

In addition, some of the functions use the following types for their return types and arguments.

```typescript
/**
 * Variations on each experiment
 */
export interface IVariations {
    friendlyName: string;
    id: string;
    status: State;
    weight?: string;
}

/**
 * Experiments
 */
export interface IExperiments {
    friendlyName: string;
    id: string;
    status: State;
    variations: IVariations[];
    createdDate?: string;
    lastModifiedDate?: string;
    lastModifiedBy?: string;
    description?: string;
    type?: string;
    link?: string;
    resultLink?: string;
}

/**
 * Experiments
 */
export interface IVariants {
    variantId: string;
    experimentId: string;
    moduleId?: string;
}
```

### Listener file

An experimentation listener file is required to track user conversion events. The listener file implements a logger interface that hooks into the event logging framework of the software development kit (SDK) to subscribe to specific user actions. The name of the listener file is in the format **\<CONNECTOR\_NAME\>.listener.ts**.

The listener file should implement the following interface.

```typescript
export interface IExperimentationListener {
    /**
     * Initializes the experimentation listener on the browser (client-side) so that
     * it may keep track of any conversion events related to the current experiments.
     *
     * @param config The config that is required to initialize the experimentation connector
     * client-side. The result of the provider file's getConfigForClientSideInit() is passed into this method
     * @param userId The user ID of the current user being served the experiment
     */
    initializeClientSide(config: any, userId: string): boolean;
    /**
     * Tracks a successful user conversion event.
     *
     * @param eventType The name of the event that occurred
     * @param payload Any additional tags or data related to the conversion event
     * @param attributes Optional parameter containing user attributes pertaining to the user that triggered the event
     */
    trackEvent(eventType: string, payload: any, attributes?: any): void;
}
```


## GeoLookup connector

A geoLookup connector lets you connect to an external geolocation service provider. By adding this type of connector to your e-commerce site and configuring it, you can generate geolocation information for e-commerce site users.

A geoLookup connector consists of two parts:

- A connector definition file in JSON format
- A provider file

#### Connector definition file

The connector definition file is used to register and provide configuration metadata data to your application. The name of the provider file is in the format **\<CONNECTOR\_NAME\>.connector.json**. The metadata includes the type of connector, the connector's name, a description of the connector, and the configuration schema, as shown in the following example of a connector definition file.

```json
{
    "$type": "geoLookupConnector",
    "name": "msdyn365-geoLookup-test",
    "description": "Test connector implementation",
    "configSchema": {
        "type": "object",
        "properties": {
          "apiKey": {
            "type": "string",
            "description": "Api key for using the geoLookup API"
          }
        },
        "required": ["apiKey"]
    }
}
```

#### Connector definition file schema

| Element | Details |
| -- | -- |
| $type | The type of connector. Because the definition file in the preceding example is for a geoLookup connector, the type is **geoLookupConnector**. |
| name | The name of the connector. This name must be unique across all connectors. |
| description | The description of the connector. |
| configSchema | The configuration schema. A configuration schema lets you provide a JSON schema that validates the configuration that is given to you at application startup, so that your connector can be initialized correctly. For example, when you initialize your connector, you need the **projectId** value to make an API call that is required for communication with the third-party service. You can specify this value in the preceding JSON file to ensure that the configuration that is provided matches your connector's requirements. |

#### Provider file

A provider file is required to initialize a connector. The name of the provider file is in the format **\<CONNECTOR\_NAME\>.provider.ts**.

The geoLookup provider file should implement the following **IGeoLookupProvider** interface.

```typescript
export interface IGeoLookupProvider  {
    /**
     * Allows the geoLocation connector to do any startup related tasks
     * using the config provided..
     *
     * This method is only called once during server startup.
     * @param config The configuration provided in connector.settings.json
     */
    // tslint:disable:no-any
    initialize(config: any): Promise<boolean>;

    /**
     * Geolocation lookup connector will get location information based on the ip address
     * @param ip The ip address
     */
    getGeoInformation(ip: string): Promise<IGeoLocation>;
}
```

In addition, some of the functions use the following types for their return types and arguments.

```typescript
export interface IGeoLocation {
    country?: string;
    region?: string;
    city?: string;
    zipCode?: string;
    [otherProperty: string]: string | undefined;
}
```
Geolocation information that is generated will be saved in the **requestContext.geoLocation** object.

### Enable and configure a geoLookup connector

Connectors are enabled and configured in the **connector.settings.json** file under the **\\src\\settings** directory of the SDK.

The following example shows a geoLookup connector being enabled in the **connector.settings.json** file.

```json
{
    "geoLookup": {
        "name": "GeoLocationTest",
        "config": {
            "apiKey": "GEOLOCATION_SERVICE_PROVIDER_API_KEY"
        },
        "cacheConfig": {
            "ttlInSeconds": {
                "geoLookup": 10
            }
        }
    }
}
```

#### Connector settings file schema

| Element | Details |
| -- | -- |
| geoLookup | This object contains all the information that is required to start and enable a geoLookup connector. |
| name | This setting specifies the name of the geoLookup connector. You can find the name of the connector in the geoLookup connector's definition file. The connector type must be **geoLookupConnector**. |
| config | This section allows for any configuration object that the connector requires for initialization and communication with the third-party service. To learn what information is required, look in the **configSchema** section of the geoLookup connector's definition file, or in the connector's README file. Change the **apiKey** value to a value that is provided by the service provider. |
| cacheConfig | Here, you can specify the timings that are used when geolocation entities are cached. The **ttlInSeconds** value specifies the amount of time, in seconds, that an entity can remain in the cache before it's considered stale. The **ttrInSeconds** value specifies the amount of time, in seconds, before an entity is refreshed. The geoLookup connector's README file should include a list of recommended cache timings. |
| geoLookup | This setting controls the cache timings for getting geolocation information that is generated by the third-party service provider. The default TTL is 120 seconds. |

> [!NOTE]
> For performance reasons, by default geolocation provider information is not resolved on the initial page request, but is instead resolved during a subsequent callback. To override this behavior and resolve geolocation provider information on the initial page request, file a [support ticket] (https://support.microsoft.com).

## Segmentation provider connector

A segmentation provider contains the business logic to fetch and analyze raw data source attributes (for example age, city, zip code, or country) from third-party sources and reduces them to one or more simple target segments that can be used within your e-commerce site.  Multiple segmentation providers can be registered at the same time.

A segmentation connector consists of two parts:

- A connector definition file in JSON format
- A provider file


#### Connector definition file

The connector definition file is used to register and provide configuration metadata data to your application. The name of the provider file is in the format **\<CONNECTOR\_NAME\>.connector.json**. The metadata includes the type of connector, the connector's name, a description of the connector, and the configuration schema, as shown in the following example of a connector definition file.

```json
{
    "$type": "segmentationConnector",
    "name": "msdyn365-seg-test-1",
    "id": "100",
    "description": "Test connector implementation",
    "configSchema": {
        "type": "object",
        "properties": {
          "apiKey": {
            "type": "string",
            "description": "Api key for using the third party service API"
          }
        },
        "required": ["apiKey"]
    },
    "segmentations": [
        {
            "id": "101",
            "name": "Age",
            "type": "integer",
            "maxValue": 100,
            "minValue": 1
        },
        {
            "id": "102",
            "name": "Gender",
            "type": "enum",
            "enum": ["male", "female"],
            "enumNames": ["Male", "Female"]
        },
        {
            "id": "103",
            "name": "Home type",
            "type": "enum",
            "enum": ["house", "condo", "townhouse", "apartment"],
            "enumNames": ["House", "Condo", "Townhouse", "Apartment"]
        },
    ]
}
```

#### Connector definition file schema

|Element|Details|
|--|--|
|$type|The type of connector. Because the definition file in the preceding example is for a geoLookup connector, the type is **segmentationConnector**.|
|name|The name of the connector. This name must be unique across all connectors.|
|id|The ID of the connector. This ID must be unique across all connectors.|
|description|The description of the connector.|
|configSchema|The configuration schema. A configuration schema lets you provide a JSON schema that validates the configuration that is given to you at application startup, so that your connector can be initialized correctly. For example, when you initialize your connector, you need the **projectId** value to make an API call that is required for communication with the third-party service. You can specify this value in the preceding JSON file to ensure that the configuration that is provided matches your connector's requirements.|

#### Segmentations schema

|Element|Details|
|--|--|
|Id| Unique ID in the scope of current segmentation provider. |
|Name| Segment name that is shown in the user interface. |
|Type| integer, string, enum, bool |
|enum| Only applies to enum type, array of enum values. |
|enumName| Only applies to enum type, array of enum names that will show in the user interface. |
|maxValue| Only applies to integer type, the max value allowed for the integer segment. |
|minValue| Only applies to integer type, the min value allowed for the integer segment. |

#### Provider file

A provider file is required to initialize a connector. The name of the provider file is in the format **\<CONNECTOR\_NAME\>.provider.ts**.

The provider file should implement the following interface.

```typescript
export interface ISegmentationProvider  {
    /**
     * Allows the segmentation connector to do any startup related tasks
     * using the config provided.
     *
     * This method is only called once during server startup.
     * @param config The configuration provided in connector.settings.json
     */
    initialize(config: any): Promise<boolean>;

    /**
     * Geolocation lookup connector will get location information based on the ip address
     * @param ip The ip address
     */
    getSegmentations(userId: string, segmentationIds: string[], requestContext: IRequestContext): Promise<ISegmentations>;
}
```

In addition, some of the functions use the following types for their return types and arguments.

```typescript
declare type ISegmentation = number | string | bool;
export interface ISegmentations {
    [segmentationID: string]: ISegmentation;
}
```
The output of the **getSegmentations()** function will be a key value object, where "key" is the segment ID and "value" is the value resolved for this segment.

### Enable and configure a segmentation provider connector

Connectors are enabled and configured in the **connector.settings.json** file under the **\\src\\settings** directory of the SDK.

The following example shows a segmentation provider connector being enabled in the **connector.settings.json** file.

```json
{
    "geoLookup": {
        "name": "GeoLocationTest",
        "config": {
            "apiKey": "GEOLOCATION_SERVICE_PROVIDER_API_KEY"
        },
        "cacheConfig": {
            "ttlInSeconds": {
                "geoLookup": 10
            }
        }
    },
    "segmentation": [
        {
            "id": "100",
            "config": {
                "apiKey": "testApiKey"
            }
        }       
    ]
}
```

#### Connector.settings.json definition file schema

|Element|Details|
|--|--|
|segmentation|This object contains all the information that is required to start and enable a segmentation connector. |
|id|This setting specifies the ID of the segmentation connector. You can find the ID of the connector in the segmentation connector's definition file. |
|config|This section allows for any configuration object that the connector requires for initialization and communication with the third-party service. To learn what information is required, look in the **configSchema** section of the geoLookup connector's definition file, or in the connector's README file. Change the **apiKey** value to a value that is provided by the service provider. |


## Additional resources

[Online channel extensibility overview](overview.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
