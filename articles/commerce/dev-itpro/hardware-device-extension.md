---
# required metadata

title: Integrate POS with a new hardware device
description: This topic explains how to integrate POS with a new hardware device.
author: mugunthanm
manager: AnnBe
ms.date: 07/27/2020
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
ms.dyn365.ops.version: AX 7.3.0, Retail July 2017 update, AX 10.0.11

---

# Integrate POS with a new hardware device

[!include [banner](../../includes/banner.md)]

This topic explains how to integrate POS with a new hardware device. 

To call Hardware station from POS you need to use a request and a response:

+ **HardwareStationDeviceActionRequest** - Request sent from POS to Hardware station.
+ **HardwareStationDeviceActionResponse** - Response received from Hardware station to POS.

The class that you extend depends on which version of the Retail SDK you are using.

+ For Retail SDK version 10.0.11 or later, you extend the **IController** interface.
+ For Retail SDK prior to version 10.0.11, you extend the **HardwareStationController** and **IHardwareStationController** classes.

## HardwareStationDeviceActionRequest

The definition of **HardwareStationDeviceActionRequest** is shown in the following code example.

```TypeScript
class HardwareStationDeviceActionRequest<TResponse extends HardwareStationDeviceActionResponse> extends Request<TResponse> {

  readonly device: string;
  readonly action: string;
  readonly actionData: any;
  constructor(device: string, action: string, actionData: any, correlationId?: string);

}
```

The parameters are described in the following table.

| Parameters | Data type | Description                     |
|------------|-----------|---------------------------------|
| device     | String    | Device name passed to the Hardware station request should be the same as the **Export** attribute added in the Hardware station Device extension controller class.                                          |
| action     | String    | Method to be called in the Hardware station extension. The method name should be passed as string value and the core POS hardware station layer will call the corresponding method from your Hardware station extension code. The method should exactly match the method name in your Hardware station extension. The Hardware station extension should be passed as parameter. |
| actionData | any       | Custom parameter for extension to pass.  |

### Sample code

The following code examples creates a **HardwareStationDeviceActionRequest** object.

```TypeScript
let hardwareStationDeviceActionRequest: HardwareStationDeviceActionRequest<HardwareStationDeviceActionResponse> =
    new HardwareStationDeviceActionRequest("Export attribute in Hardware station controller class",
    "extension method name in Hardware station", "Custom parameters/you can also pass custom object");
return this.extensionContextRuntime.executeAsync(hardwareStationDeviceActionRequest);
```

## HardwareStationDeviceActionResponse

The definition of **HardwareStationDeviceActionResponse** is shown in the following code example.

```TypeScript
class HardwareStationDeviceActionResponse extends Response {
  readonly response: any;
  constructor(response: any);
}
```

The parameters are described in the following table.

| Parameters | Data type | Description                                       |
|------------|-----------|---------------------------------------------------|
| response   | any       | Response sent from the Hardware station extension code to POS. |

## End-to-end flow

The follow diagram shows the flow between POS, Hardware station, and the hardware device.

![POS-HWS-Device Sequence diagram](./media/POSDeviceExtension.png)

## Hardware station extension

To call your new hardware device, you must implement the Hardware station code. From the Hardware station code, call your hardware device.

To implement the Hardware station extension for Retail SDK version 10.0.11 or later, follow these steps:

1. Create a new C# class library project with .NET Framework version 4.6.1 or use one of the samples in the Retail SDK as a template (**...\RetailSDK\SampleExtensions\HardwareStation\\**). Using the sample as a template is recommended.

2. In the extension project add the **Microsoft.Dynamics.Commerce.Hosting.Contracts** package using the NuGet package manager. The NuGet packages can be found in the **RetailSDK\pkgs** folder.

3. Add a new controller class that extends the **IController** interface.

4. Add the **RoutePrefix** attribute to the controller class to expose the controller class to clients.

    ```csharp
    [RoutePrefix("ISVEXTENSIONDEVICE")]  
    ```

5. Add a method in the controller class with **HttpPost** attribute to implement your custom logic to call the hardware device. This method will be passed as the second parameter (action parameter) to the POS **HardwareStationDeviceActionRequest**. From the extension method, the extension can call other requests, like printing and cash drawer, by including the relevant NuGet packages from the Retail SDK.

    ```C#
    [HttpPost]
    public async Task<bool> IsReady(IEndpointContext context)
    {
    }
    ```

6.  Build the project.

To implement the Hardware station extension for Retail SDK prior to version 10.0.11, follow these steps:

1.  Create a new C# class library project.
2.  Add a new controller class that extends **HardwareStationController** and **IHardwareStationController**.
3.  Add the **Export** attribute to the controller class. The **Export** attribute must be in all uppercase letters and you must pass this value as a parameter from POS extension. The device parameter passed from the POS **HardwareStationDeviceActionRequest** must match this value.
4.  Add your method in controller class to implement your custom logic to call the hardware device. This method will be passed as the second parameter (action parameter) to the POS **HardwareStationDeviceActionRequest**.
5.  Build the project.

To deploy the Hardware station extension in MPOS and test it using the local Hardware station:

1. Copy the output library to the **C:\\Program Files (x86)\\Microsoft Dynamics 365\\70\\Retail Modern POS\\ClientBroker\\ext** folder.
2. Open the **HardwareStation.Extension.config**.
3. Add the extension library details under the composition section.

    ```Xml
    <add source="assembly" value="your extension library name" />
    ```
 
4. Save the file.
5. Close Modern POS if running.
6. Open Task Manager and end the **dllhost.exe** task.
7. Launch MPOS and configure it to use local hardware station.
8. Validate your scenario.

To test with Cloud POS, deploy the Hardware station extension dll to the shared Hardware station **ext** folder and update the **HardwareStation.Extension.config** file with the custom library in the shared Hardware station folder.

## Retail SDK samples
Here are some samples in the Retail SDK for reference:

+ **POS**: \RetailSDK\POS\Extensions\FiscalRegisterSample
+ **Hardware station**: \RetailSDK\SampleExtensions\HardwareStation\Extension.FiscalRegisterSample

## Sample code for Retail SDK version 10.0.11 or later

```csharp
namespace Contoso
{
    namespace Commerce.HardwareStation.ISVExtensionDevice
    {

        using Microsoft.Dynamics.Commerce.Runtime.Hosting.Contracts;
        using System;
        using System.Threading.Tasks;

        /// <summary>;
        /// Sample hardware station extension
        /// </summary>

        [RoutePrefix("ISVEXTENSIONDEVICE")]
        public class ISVExtensionDeviceController : IController
        {
            /// <summary>
            /// Sample.
            /// </summary>

            /// <param name="request">Custom request.<param>
            /// <returns>Result of Custom response.</returns>

            [HttpPost]
            public async Task<CustomResponse> Sample(CustomRequest request, IEndpointContext context)
            {
                CustomResponse response;

                try
                {
                    response = new CustomResponse();
                }

                catch (Exception ex)
                {
                    throw ex;
                }
                return await Task.FromResult(response);
            }
        }

        public class CustomResponse
        {
            public string sampleProp { get; set; }

            public CustomResponse()
            {
                this.sampleProp = "sampleValue";
            }
        }
    }
}
```


## Sample code for Retail SDK prior to version 10.0.11

```csharp
namespace Contoso
{
  namespace Commerce.HardwareStation.ISVExtensionDevice
  {

  using System;
  using System.Composition;
  using System.Web.Http;
  using Microsoft.Dynamics.Commerce.HardwareStation;
  /// <summary>;
  /// Fiscal register peripheral web API controller class.
  /// </summary>

  [Export("ISVEXTENSIONDEVICE", typeof(IHardwareStationController))]
  [Authorize]
  public class ISVExtensionDeviceController : HardwareStationController, IHardwareStationController
  {
  /// <summary>
  /// Sample.
  /// </summary>

  /// <param name="request">Custom request.<param>
  /// <returns>Result of Custom response.</returns>

      [HttpPost]
      public CustomResponse Sample(CustomRequest request)
      {
        ThrowIf.Null(request, "request");
        try
        {
          return null;
        }

        catch (Exception ex)
          {
            throw ex;
          }
      }
   }
   }
 }

```

## Sample POS code on how to call the above Hardware station extension

From your POS extension, call the Hardware station by using this pattern.

```TypeScript
let hardwareStationDeviceActionRequest: HardwareStationDeviceActionRequest<HardwareStationDeviceActionResponse> =
    new HardwareStationDeviceActionRequest("ISVEXTENSIONDEVICE",
     "Sample", "Custom parameters or custom object");
 return this.extensionContextRuntime.executeAsync(hardwareStationDeviceActionRequest);
 ```
