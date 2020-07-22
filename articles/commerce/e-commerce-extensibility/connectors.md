---
# required metadata

title: Connectors overview
description: 
author: samjarawan
manager: annbe
ms.date: 07/31/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Connectors overview

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

Connectors allow you to connect your Dynamics 365 Commerce site to external third parties to accomplish certain tasks including capturing analytics, logging, and experimentation.

Connectors can be added to your Commerce site by adding them as a dependency in your package.json file, or by implementing them directly in your configuration package code under the **\src\connectors** directory. 

As of Commerce version 10.0.13, Dynamics 365 Commerce supports only one type of connector, the experimentation connector. Some service providers require a paid license for the service before they can be used, please check with the service provider for more information.

## Configure and enable a connector

As of Commerce version 10.0.13, the experimentation connector is the only supported type of connector. In future versions you will be able configure and enable other types of connectors. 

### Connector settings file

Connectors are configured and enabled in the **connector.settings.json** file which can be found under the **\src\settings** directory. If no **connector.settings.json** file exists, you can create one manually. In this file, you can specify the experimentation connector to use and configure it as needed. Only one experimentation connector can be used at a time. 

The following example shows the contents of a **connector.settings.json** file.

```json
{
    "experimentation": {
        "name": "msdyn365-exp-test-2",
        "config": {
            "sdkKey": "RhoXz6PsLmjvifyZfTxL2R",
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
    }
}
```
#### Connector settings file schema

- **experimentation** – This object contains all the necessary information to start and enable your experimentation connector.
- **name** – The name of the experimentation connector to use. The name of the connector can be found in the connector’s definition file. The type of the connector must be a **experimentationConnector**.
- **config** – The config section allows any configuration object the connector needs to initialize and start communicating with the third party service. Check the connector’s configSchema in its definition file or README file to understand what information is required.
- **cacheConfig** – You can provide the timings to use when caching certain experimentation related entities. **ttlInSeconds** refers the amount of time an entity should live in the cache before being considered stale and the **ttrInSeconds** refers to when an entity should be refreshed. The connector’s README file should also have a list of recommended cache timings.
- **experimentation** - Controls the cache timings for getting the list of available experiments configured in your third party provider during getExperiments(). Default TTL (time-to-live) is 1800 seconds and default TTR (time-to-refresh) is 60 seconds. 
- **experimentationDataFile** - Controls the cache timings for how often the config that is passed down to the client during getConfigForClientSideInit(). The default TTL (time-to-live) is 1800 seconds and default TTR (time-to-refresh) is 60 seconds.  

## Experimentation connector

An experimentation connector allows you to connect your application to an external experimentation provider. Adding this type of connector to your application and configuring it will allow you to create and run experiments in the site builder experience as well as track their outcomes to provide the best experience for your customers.

An experimentation connector is composed of three parts: A connector definition file (JSON), a provider file. and a listener file.

### Connector definition file

A connector definition file is used to register and provide configuration metadata data to your application. The connector definition file name is in the format **&lt;CONNECTOR_NAME&gt;.connector.json**. The metadata includes the type of connector, the connector name, a description of the connector, and the configuration schema.

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
            "description": "The project id to use for experimentation"
          }
        },
        "required": ["projectId"]
    }
}
```
#### Connector definition file schema

- **$type** – This refers to the type of connector. In this case, because this is an example of experimentation connector’s definition file, the type is “experimentationConnector"
- **name** – This is the name of the connector and must be unique across all connectors
- **description** – The description of the connector
- **configSchema** – A config schema allows you to provide a JSON schema that will validate the configuration given to you at application startup so that your connector can be initialized properly. For example, let's say when you initialize your connector, you need the projectId to make an API call necessary to talk to the third party experimentation service. You can specify the JSON above to ensure that the configuration provided matches your connectors requirements.

### Provider file

An experimentation provider file is necessary to initialize a connector and enable it to interact with Commerce site builder to present a list of available experiments configured in your third party experimentation service. The connector definition file name is in the format **&lt;CONNECTOR_NAME&gt;.provider.ts**. 

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
     * Initailizes the experimentation provider on the browser (client-side) so that
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
     * userId will be generated from hash if user is signed-in to deterministically generate sanatized userIds.
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
     * userId will be generated from hash if user is signed-in to deterministically generate sanatized userIds.
     * @param experiments The experiments the user is participating in.
     * @param attributes Optional user related attributes
     */
    activateExperiment(userId: string, experiments: IVariants[], attributes?: {
        [index: string]: string;
    }): boolean;
}
```

Additionally, here are the types that some of the functions use for their return types and arguments.

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

An experimentation listener file is necessary to track user conversion events. The listener file implements a logger interface that hooks into the SDK's event logging framework and will subscribe to certain user actions. The connector definition file name is in the format **&lt;CONNECTOR_NAME&gt;.listener.ts**.

The listener file should implement the following interface.

```
export interface IExperimentationListener {
    /**
     * Initailizes the experimentation listener on the browser (client-side) so that
     * it may keep track of any conversion events related to the current experiements.
     *
     * @param config The config that is required to initialize the experimentation connector
     * client-side. The result of the provider file’s getConfigForClientSideInit() is passed into this method
     * @param userId The user id of the current user being served the experiment
     */
    initializeClientSide(config: any, userId: string): boolean;
    
    /**
     * Tracks a successful user conversion event.
     *
     * @param eventType The name of the event that occured
     * @param payload Any additional tags or data related to the conversion event
     */
    trackEvent(eventType: string, payload: any): void;
}
```

## Additional resources

[TBD]()
