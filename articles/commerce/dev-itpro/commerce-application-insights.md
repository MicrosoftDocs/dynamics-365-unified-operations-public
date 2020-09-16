---
# required metadata

title: Log extension events to Application Insights
description: This topic explains how to log events to Customer Application Insights from Commerce runtime (CRT) extensions.
author: mugunthanm
manager: AnnBe
ms.date: 05/15/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 28021
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 2019-08-2019
ms.dyn365.ops.version: AX 10.0.7

---

# Log extension events to Application Insights

[!include [banner](../includes/banner.md)]

This topic explains how to log events to [Customer Application Insights](https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview) from Commerce runtime (CRT) and POS extensions.

## Log an event to Application Insights

1. Set up Application Insights in the [Microsoft Azure portal](https://portal.azure.com), and generate the instrumentation key.
2. Extend CRT to log events to Application Insights by using the instrumentation key that you generated.

> [!NOTE]
> The **RetailLogger** class is no longer supported. Existing extensions that use this class must be migrated to the new model.

## Set up and configure Application Insights in Azure

1. Open the [Azure portal](https://portal.azure.com), and sign in by using your Azure subscription credentials.
2. Select **Create a resource**.

    > [!div class="mx-imgBorder"]
    > ![Create a resource button](media/NewResource.png)

3. Search for **Application Insights**.

    > [!div class="mx-imgBorder"]
    > ![Search field](media/Search.png)

4. Click **Create** in the Application Insights page.

5. On the **Basic** tab, set the **Subscription**, **Resource group**, **Name**, and **Region** fields.

    > [!div class="mx-imgBorder"]
    > ![Basic tab](media/CreateNew.png)

6. On the **Review + create** tab, select **Create**.

    > [!div class="mx-imgBorder"]
    > ![Create button](media/CreateConf.png)

7. Wait for the deployment to be completed.

    > [!div class="mx-imgBorder"]
    > ![Resource created](media/Completed.png)

8. Go to the resource, and copy the **Instrumentation Key** value. You will use this value in the CRT code or CRT extension configuration file.

    > [!div class="mx-imgBorder"]
    > ![Instrumentation Key field](media/Resource.png)

## Extend the CRT extension project to log events to Application Insights

1. Create a new C\# class library project, and name it **Contoso.Diagnostic**.

    > [!div class="mx-imgBorder"]
    > ![New Contoso.Diagnostic project](media/VSProject.png)

2. Add references to the following libraries:

    + Microsoft.ApplicationInsights
    + Netstandard
    + Microsoft.Dynamics.Commerce.Runtime.Framework

    > [!NOTE]
    > To install the **Microsoft.ApplicationInsights** assembly reference, install the [Application Insights SDK for ASP.NET Core](https://nuget.org/packages/Microsoft.ApplicationInsights.AspNetCore). The reference to **Microsoft.Dynamics.Commerce.Runtime.Framework** can be added from the **..\\RetailSDK\\Reference** folder.

3. Add a new class file that is named **ContosoLogger**, and copy the following code into it.

    ```C#
    using Microsoft.ApplicationInsights;
    using Microsoft.ApplicationInsights.Extensibility;
    using Microsoft.Dynamics.Commerce.Runtime;
    using Microsoft.Dynamics.Commerce.Runtime.Extensions;
    namespace Contoso.Diagnostic
    {
        public static class ContosoLogger
        {
            private static readonly object lockObject = new object();
            private static TelemetryClient client = null;
            public static TelemetryClient GetLogger(RequestContext context)
            {
                if (client == null)
                {
                    lock (lockObject)
                    {
                        if (client == null)
                        {
                            string key = context.Runtime.Configuration.GetSettingValue("ext.AppInsightsKey") ?? string.Empty;
                            client = new TelemetryClient(new TelemetryConfiguration(key));
                        }
                    }
                }
                return client;
            }
        }
    }
    ```

4. Build the project, and copy the output library and the **Microsoft.ApplicationInsights.dll** file to the **..\\RetailServer\\webroot\\bin\\Ext** folder for manual deployment and testing.
5. In the **..\\RetailServer\\webroot\\bin\\Ext** folder, open the **CommerceRuntime.Ext.config** file, and update the **\<settings\>** section with the Applications Insights instrumentation key that you generated earlier. Here is an example.

    ```xml
    <add name="ext.AppInsightsKey" value="xxxxxxx"/>
    ```

6. Restart your Commerce Scale Unit.

## Consume the logger in the CRT extension

1. To consume the **ContosoLogger** in the extension, add the **ContosoDiagnostic** and **Microsoft.ApplicationInsights** assembly references to the extension project.
2. To log events, use the **TraceTelemetry** class, and create the traces. Here is an example.

    ```C#
    using Contoso.Diagnostic;
    using Microsoft.ApplicationInsights.DataContracts;
    var trace = new TraceTelemetry("CRT executing request", SeverityLevel.Information);
    trace.Properties.Add("CustomDimensionColumn1", request.RequestContext.GetTerminalId().ToString());
    trace.Properties.Add("CustomDimensionColumn2", "CRT demo - Save Cart request");
    ContosoLogger.GetLogger(request.RequestContext).TrackTrace(trace);
    ```

    > [!NOTE]
    > Trace properties are custom dimensions that you can easily add to query the traces.

## Validate the trace events

1. Open the [Azure portal](https://portal.azure.com), and sign in by using your Azure subscription credentials.
2. Go to the Application Insights instance, and then, under **Monitoring**, select **Logs (Analytics)** to open a new query editor.

    > [!div class="mx-imgBorder"]
    > ![Log Analytics option](media/AppInsightQuery.png)

3. On the **Schema** tab, double-click **traces** to add it to the query editor. The default time range is **Last 24 hours**.

    > [!div class="mx-imgBorder"]
    > ![Traces added to the query editor](media/Trace.png)

4. Select **Run** to run the query. The logged event will appear in the results.

    > [!div class="mx-imgBorder"]
    > ![Log details](media/TraceDetails.png)

## Build the deployable package

For detailed information about how to build deployable packages, see [Create deployable packages](retail-sdk/retail-sdk-packaging.md).

1. Copy the **Contoso.Diagnostic** and **Microsoft.ApplicationInsights** assemblies to the **\\RetailSDK\\References** folder.
2. Update the **BuildTools\\Customization.settings** file, and add the following entries in the **\<ItemGroup\>** section.

    ```xml
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\\Contoso.Diagnostic.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\\Microsoft.ApplicationInsights.dll" />;
    ```

3. Open an MSBuild **Command Prompt** window for Microsoft Visual Studio 2015, and run the **build** command in the root of your Retail SDK folder.
4. Enter the following command to generate the deployable package.

    ```Console
    msbuild /t:rebuild
    ```

5. In the **RetailSDK\\Packages\\RetailDeployablePackage** folder, find the deployable package. Go to the **content.folder** folder, and make sure that your three files are in the package (**Packages\\RetailDeployablePackage\\content.folder\\RetailServer\\Code\\bin\\ext**).
6. Upload the deployable package to your Shared asset library in Microsoft Dynamics Lifecycle Services (LCS).
7. In LCS, open your environment's main page, and select **Environment Features** \> **Retail and Commerce** \> **Manage**.
8. Select **Apply Extension**, and select the extension from your library.
9. After the extension has been successfully deployed, open an instance of Modern POS (MPOS) or POS (CPOS) that has been activated against the Commerce Scale Unit.
10. Run the extension scenario that that uses custom Application Insights logging.
11. Refresh the query in Application Insights to verify that the traces from the extension are logged correctly.

## Log events to Application Insights in the POS extension projects

1. Open the ModernPOS.sln or CloudPos.sln from RetailSDK\POS.
2. Create a 'Libraries' folder in Pos.Extensions project.
3. Navigate to the 'Libraries' folder using Command prompt and run the 'npm i --save @microsoft/applicationinsights-web' command to install the npm package for java script App insights package. Once the package is installed the 'POS/Extensions/Libraries' folder should contain 'node_modules' folder containing the Application Insights library files.

npm package must be installed before running the command. [npm package can be downloaded and installed from here](https://nodejs.org/en/).

4. Check that the path 'POS/Extensions/Libraries/node_modules/@microsoft/applicationinsights-web/dist/applicationinsights-web.js' exists in the library (this may change if the Application Insights library updates this path in the future versions).
If the path is changed, update the library path in step 5, 6, and 7 to one that points to the main Application Insights library.

5. Open the tsconfig.json form the POS.Extensions project and under the exclude section add an entry to the Libraries folder:

```typescript
"exclude": [
    "Libraries"
  ],
```

6. Open the tsconfig.json form the POS.Extensions project and under the 'compilerOptions' section add the following properties :

```typescript
"baseUrl": ".",
"moduleResolution": "node",
"paths": {
    "applicationinsights-web": [ "Libraries/node_modules/@microsoft/applicationinsights-web/dist/applicationinsights-web" ]
}
```

7. Edit the Pos.Extensions.csproj under the 'CopyPosExtensionsFiles' add the below targets to have the Application Insights library be copied over to the POS application and be ready for consumption by the extension code:

```typescript
<JavaScriptFileList Include="Libraries\\**\\*.js">
    <InProject>false</InProject>
    <Visible>false</Visible>
</JavaScriptFileList>
```

8. Include the following in the 'manifest.json' file of the POS extension folder(package) that is consuming the Application Insights library:

```typescript
{
  "dependencies": [
    {
      "alias": "applicationinsights-web",
      "format": "amd",
      "modulePath": "../Libraries/node_modules/@microsoft/applicationinsights-web/dist/applicationinsights-web"
    }
  ]
}
```
Now the Application Insights library is now ready to be consumed and used in POS.

## Consume the library and log events

1. Create a new typescript file inside the POS extension folder(package) and name it as AppInsights.ts
2. Copy the below code to used by the extensions in order to track events using Application Insights (update the instrumentation key created in the Azure App insights).

```typescript
import { ApplicationInsights } from "applicationinsights-web";

/**
 * Example implementation of an Application Insights singleton that can be used to log events and metrics on Application Insights.
 */
export class AppInsights {
    private static _instance: AppInsights = null;
    private _applicationInsights: ApplicationInsights = null;

    /**
     * Gets a global reference to an application insights reference that may be used by other extension code.
     * @returns {ApplicationInsights} The ApplicationInsights instance that may be used to log events.
     */
    public static get instance(): ApplicationInsights {
        if (AppInsights._instance === null) {
            AppInsights._instance = new AppInsights();
        }

        return AppInsights._instance._applicationInsights;
    }

    /**
     * Initializes a new instance of AppInsights.
     */
    constructor() {
        this._applicationInsights = new ApplicationInsights({
            config: {
                instrumentationKey: 'YOUR_INSTRUMENTATION_KEY_GOES_HERE'
                /* ...Other Configuration Options... */
            }
        });
        this._applicationInsights.loadAppInsights();
    }
}
```
3. In the desired extension code log the events by calling the AppInsights class like below:

```typescript
AppInsights.instance.trackEvent({
    name: "extensionTest",
    properties: {
        "property1": "value1",
        "property2": "value2",
    },
    measurements: {
        "measurement1": 1,
        "measurement2": 2,
    },
});
```




