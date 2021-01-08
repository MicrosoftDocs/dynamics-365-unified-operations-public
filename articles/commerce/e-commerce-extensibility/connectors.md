---
# required metadata

title: Configure and enable connectors
description: This topic describes connectors and explains how to configure and enable them in Microsoft Dynamics 365 Commerce.
author: samjarawan
manager: annbe
ms.date: 09/28/2020
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
ms.dyn365.ops.version: Release 10.0.13

---

# Configure and enable connectors

[!include [banner](../includes/banner.md)]

This topic describes connectors and explains how to configure and enable them in Microsoft Dynamics 365 Commerce.

## Overview

Connectors let you connect your Dynamics 365 Commerce site to external third parties to perform tasks such as capturing analytics, logging, and experimenting. Some third-party service providers require a paid license for their service before it can be used. For more information, contact your service provider.

In Commerce version 10.0.13, the only supported type of connector is the experimentation connector. In future versions, you will be able configure and enable other types of connectors.

## Configure and enable connectors

You can add connectors to your Commerce site by adding them as a dependency in your **package.json** file. Alternatively, you can implement them directly in your configuration package code under the **\\src\\connectors** directory.

### Connector settings file

Connectors are configured and enabled in the **connector.settings.json** file under the **\\src\\settings** directory. If no **connector.settings.json** file exists, you can manually create one. In this file, you can specify the experimentation connector that you want to use and configure it as you require. Only one experimentation connector can be used at a time.

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

- **experimentation** – This object contains all the information that is required to start and enable your experimentation connector.
- **name** – This setting specifies the name of the experimentation connector that is used. You can find the name of the connector in the connector's definition file. The type of the connector must be **experimentationConnector**.
- **config** – This section allows for any configuration object that the connector requires for initialization and to start to communicate with the third-party service. To learn what information is required, look in the **configSchema** section of the connector's definition file or in the connector's README file.
- **cacheConfig** – You can specify the timings that are used when some experimentation-related entities are cached. In this section, **ttlInSeconds** refers to the amount of time that an entity can remain in the cache before it's considered stale, and **ttrInSeconds** refers to the amount of time before an entity is refreshed. The connector's README file should include a list of recommended cache timings.
- **experimentation** – This setting controls the cache timings for getting the list of available experiments that are configured in your third-party provider during **getExperiments()**. The default TTL (time to live) is 1,800 seconds, and the default TTR (time to refresh) is 60 seconds.
- **experimentationDataFile** – This setting controls the cache timings for having the configuration passed down to the client during **getConfigForClientSideInit()**. The default TTL is 1,800 seconds, and the default TTR is 60 seconds.

## Experimentation connector

An experimentation connector lets you connect your application to an external experimentation service provider. By adding this type of connector to your application, configuring it, and enabling it, you can create and run experiments in Commerce site builder, and track outcomes, to provide the best experience for your customers.

An experimentation connector consists of three parts:

- A connector definition file (in JavaScript Object Notation \[JSON\] format)
- A provider file
- A listener file

### Connector definition file

A connector definition file is used to register and provide configuration metadata data to your application. This metadata includes the type of connector, the name of the connector, a description of the connector, and the configuration schema. The name of the connector definition file is in the format **&lt;CONNECTOR\_NAME&gt;.connector.json**.

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

- **$type** – The type of connector. Because the definition file in the preceding example is for an experimentation connector, the type is **experimentationConnector**.
- **name** – The name of the connector. This name must be unique across all connectors.
- **description** – The description of the connector.
- **configSchema** – The configuration schema. A configuration schema lets you provide a JSON schema that validates the configuration that is given to you at application startup, so that your connector can be initialized correctly. For example, when you initialize your connector, you need the **projectId** value to make an API call that is required for communication with the third-party experimentation service. You can specify this value in the preceding JSON file to ensure that the configuration that is provided matches your connector's requirements.

### Provider file

An experimentation provider file is required to initialize a connector. It also enables the connector to interact with Commerce site builder to present a list of available experiments that are configured in your third-party experimentation service. The name of the provider file is in the format **&lt;CONNECTOR\_NAME&gt;.provider.ts**.

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

An experimentation listener file is required to track user conversion events. The listener file implements a logger interface that hooks into the event logging framework of the software development kit (SDK) to subscribe to specific user actions. The name of the listener file is in the format **&lt;CONNECTOR\_NAME&gt;.listener.ts**.

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

## Additional resources

[Online channel extensibility overview](overview.md)
