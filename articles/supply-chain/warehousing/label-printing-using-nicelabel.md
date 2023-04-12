---
title: Enable label printing using the external Loftware NiceLabel label service solution
description: This article describes how to set up and print labels using Loftware NiceLabel label service solution.
author: GalynaFedorova
ms.author: gfedorova
ms.reviewer: kamaybac
ms.search.form: WHSLabelLayout, WHSLabelLayoutDataSource
ms.topic: how-to
ms.date: 04/04/2023
ms.custom: bap-template
---

# Enable label printing using the external Loftware NiceLabel label service solution

[!include [banner](../includes/banner.md)]

This article describes how to use the print labels in Microsoft Dynamics 365 Supply Chain Management using the Loftware NiceLabel solution.

Loftware NiceLabel lets you create, manage, and print standardized, compliant barcode labels. In addition, it lets you print labels to supported cloud-connected printers or a wide variety of classic on-premises printers. NiceLabel has several products available that can be used together with the external label printing service, including their cloud solution (NiceLabel Cloud) and several versions of their on-premises products. This article focuses on how to integrate Supply Chain Management with the NiceLabel Cloud solution, but parts of the article that use NiceLabel automation can also be used with other products.

For more information about Loftware NiceLabel Cloud, see [Loftware NiceLabel Cloud & Label Management System](https://www.loftware.com/products/labeling/nicelabel-cloud).

> [!IMPORTANT]
> By enabling the external service integration, you are affirming that you understand that the data handling, privacy, and compliance standards of the external service may not be the same as those provided by Dynamics 365 Supply Chain Management. Please consult the external service's documentation and terms to learn whether your organization's security and privacy requirements are met by the external service, including the handling of personal data and geo-residency. Your privacy is important to us. To learn more, read the [Microsoft Privacy Statement](https://privacy.microsoft.com/privacystatement).

*NiceLabel Cloud* supports two integration approaches for other cloud applications:

- **Cloud Print API** – NiceLabel Cloud generates the labels and sends print jobs to the printer. This can be either a so-called *cloud printer* (a printer connected directly to the NiceLabel Cloud instance, without using any locally installed software or printer driver), or any printer that is connected to a workstation with a print gateway component installed. For the current list of supported cloud printers, see the [Loftware web site](https://www.loftware.com/).
- **Cloud Trigger API** – NiceLabel Cloud sends messages to an on-premises NiceLabel Automation instance, which generates the labels and sends them to the printer. You must install a Windows printer driver for each of your printers.

If you don't want any local software footprint, then Cloud Print API with supported printers is the preferred option. Otherwise, we suggest using the Cloud Trigger API as the preferred option, but both options are available.

Here are some of the pros and cons of each integration option:

- Using Cloud Trigger API, you can use an out-of-the-box cloud integration pack or completely customize the processing of print requests.
- Cloud Print API is synchronous (the server waits for the print engine to print the label) and reports the outcome of the print job, but Supply Chain Management doesn't use this result. You must therefore wait a bit longer when printing labels or set a timeout on the external service operation. If a timeout occurs, the Cloud Print API will continue printing, but the request will be logged as a timeout.
- On-premises printer naming is simpler in the Cloud Trigger API because you can use the names of the printers as configured on the server(s) running the NiceLabel Automation app. To use the Cloud Print API, you must specify a workstation ID to identify which workstation to print to.
- For Cloud Trigger API, you can install multiple instances of the NiceLabel Automation app on the local network to achieve load balancing and high availability. As noted in the previous point, you must specify which workstation the printing request will be routed to, and if that workstation isn't available, the label won't print. Conversely, multiple NiceLabel Automation instances can handle requests to the same cloud trigger.
- The installation footprint is smaller with the Cloud Print API.

## NiceLabel Cloud integration preparation

Before NiceLabel Cloud can be accessed by either the Cloud Print API or the Cloud Trigger API, you must register on the developer portal and then link your developer portal subscription with your NiceLabel Cloud instance. For instructions, see [Cloud Integrations](https://help.nicelabel.com/hc/en-001/articles/4402966072209-Cloud-Integrations#cloud-integrations-1-0) on the NiceLabel Help Center.

If you wish to use internet of things (IoT) enabled printers, you must connect them to your NiceLabel Cloud instance at this point. See also [Cloud Printers](https://help.nicelabel.com/hc/en-001/articles/4407466158737-Cloud-Printers) on the NiceLabel Help Center.

## Configuring Microsoft Dynamics 365 SCM to print to Cloud printers using the Cloud Print API

Using the Cloud Print API, we can print both labels that are generated by the NiceLabel Cloud based on variables sent from Microsoft Dynamics 365 SCM or send a ZPL (Zebra Programming Language) label (perhaps an existing label layout or a shipping label received from the shipping carrier through a SPS integration). The External Service Definition will contain two operations, one for printing variables-based layouts and the second for printing ZPL-based label layouts.

### Configure external service definition

Follow these steps to set up external service definition.

1. Go to **Warehouse management \> Setup \> External services \> External service definitions**.
1. On the Action Pane, select **New** to create an external service definition.
1. Set the following values for the new service definition:
    - **External service definition** – Enter *NLPrint*.
    - **Description** – Enter *NiceLabel Cloud Print API*.
1. Select **Edit operations** to define the *Print* service operation. Set the following values for the new service operation:
    -**External service operation** – Enter *Print*.
    -**Description** – Enter *Print to cloud printer*.
    -**HTTP method** – Select *POST* method.
    - **Operation timeout** - Select the operation timeout (for example, , *500*).
        > [!NOTE]
        > Cloud Print API is a synchronous API, that means that it will wait until the label has been printed and will provide immediate feedback whether the printing was successful or not. However, as this might take several seconds, it could provide a bad user experience for mobile device users. Additionally, the result is currently not used. Therefore the timeout has been set quite low; even though Microsoft Dynamics 365 SCM stops waiting after 500ms, the print is continuing in the background.
    - **Request body type** - Select *Raw*. 
    - **Relative URL** - Enter */Print/v2/Print*.
    - Expand **HTTP request headers** and create the following record:
        - **Key**: Ocp-Apim-Subscription-Key
        - **Value**: $auth.secret$ (exactly as written)
    - Expand **Request body** and create the following record:
        - **Content type**: Enter *application/json*
        - **Body**: Enter the following code:

            ```
            {
                "deviceType": "CloudPrinter",
                "deviceId": {
                    "printerName": "$label.printer$",
                    "workstation": null
                },
                $label.body$
            }
            ```

1. Create *SendData* service operation. Set the following values for the new service operation:
    -**External service operation** – Enter *SendData*.
    -**Description** – Enter *Send ZPL to cloud printer*.
    -**HTTP method** – Select *POST* method.
    - **Operation timeout** - Set the operation timeout (for example, , *500*).
    - **Request body type** - Select *Raw*. 
    - **Relative URL** - Enter */Print/v2/SendData*.
    - Expand **HTTP request headers** and create the following record:
        - **Key**: Ocp-Apim-Subscription-Key
        - **Value**: $auth.secret$ (exactly as written)
    - Expand **Request body** and create the following record:
        - **Content type**: Enter *application/json*
        - **Body**:

            ```
            {
                "deviceType": "CloudPrinter",
                "deviceId": {
                    "printerName": "$label.printer$",
                    "workstation": null
                },
                "data": "$label.body:base64$"
            }
            ```

1. Go back to the **External service definition**.
1. Expand **Label print service** tab.
1. In the **Print operation** field select *SendData* that has been created.  
1. In the **Variables print operation** field select *Print* that has been created.  
1. In the **Variable label layout template** field set the following:
    ```
    "filePath": "$SystemVariables.LabelFile$",
    "quantity": "$SystemVariables.Quantity$",
    "dataSources": [
        {
    {{Row Table=LabelLayoutVariable
            "$LabelLayoutVariable.Variable$": "$LabelLayoutVariable.Value$",
    }}
        }
    ]
    ```

### Configure external service instance

You will need either the Primary or the Secondary key from the subscription you created earlier on the NiceLabel Cloud Development Portal.

Follow these steps to set up external service instance.

1. Go to **Warehouse Management \> Setup \> External services \> External service instances**.
1. On the Action Pane, select **New** to create an external service instance.
1. Set the following values for the new service instance:
    - **External service instance** - Enter a name for the instance (for example, *NLPrintProd*).
    - **Description** - Enter a short description of the instance (for example, *NiceLabel Cloud Print API Production*).
    - **External service definition** – Select the service definition to use. The example service definition value that was suggested earlier in this article was *NLPrint*.
1. Expand **General** tab and set the following values:
    - **Base URL** - Set *https://labelcloudapi.onnicelabel.com*.
    - **Authentication secret** - Enter the subscription key from the NiceLabel developer portal.
    - **Logging level** - Select *Successes and errors*.
    - **Log request bodies** - Select *Successes and errors*.

You can now proceed to create label printers and label layouts using either variables or ZPL.
> [!NOTE]
> When creating label printers, use the name of the printer from the Cloud printers tab in NiceLabel Cloud Control Center for the “Label print service printer name” field.

> [!NOTE]
> When creating label layouts using variables, use the full path and file name of the label (as seen in the Path field in File Properties) for the LabelFile system variable.

## Configuring Microsoft Dynamics 365 SCM to print to local network printers using the Cloud Trigger API

Using the Cloud Trigger API, we can call an on-premise installation of the NiceLabel Automation service, which then processes the request and performs preprogrammed actions. Before proceeding with the following steps, install NiceLabel on one or more computers that will run the NiceLabel Automation. Ensure that you have all the label printers installed on these machines as well. For guidance on installation and printer setup, refer to NiceLabel documentation.

To simplify the configuration of the NiceLabel Automation, we will use the NiceLabel Cloud Data Integration pack and the steps described in [NiceLabel Help Center](https://help.nicelabel.com/hc/en-001/articles/7361192275217-Appendix-A-Integration-bundle). The required steps are summarized below with more details provided in the document:

1. Download the integration pack from the URL in the document.
1. Log in to your NiceLabel Control Center.
1. In Documents, create a new folder /Demo/LabelCloudDataIntegration.
1. Open the integration pack ZIP file and extract the files.
1. Upload your Document Storage folder contents into your CloudIntegration folder in your DMS (Document Management System).
1. On the computer where NiceLabel Automation is installed, open the NiceLabel Automation Manager.
1. If not activated yet, connect the NiceLabel Automation to your NiceLabel Cloud.
1. In NiceLabel Automation Manager, select +Add and browse to the LabelCloudDataIntegration folder on the NiceLabel Cloud.
1. Open the CloudIntegration-CloudTrigger.misx file.
1. Start only the Print trigger (verify that it is using the Unique identifier Api-CloudIntegrationDemo-Print); other triggers are not currently used by Microsoft Dynamics 365 SCM.

After you have installed and started the Print trigger, we can configure the External Service Definition and External Service Instance required to access the NiceLabel Automation using the Cloud Trigger API. Without customizing the demo automation configuration, we can only print labels defined using variables, therefore we will be only configuring one operation on the External Service Definition. Use the following steps to create the definition and instance:

### Configure external service definition

Follow these steps to set up external service definition.

1. Go to **Warehouse management \> Setup \> External services \> External service definitions**.
1. On the Action Pane, select **New** to create an external service definition.
1. Set the following values for the new service definition:
    - **External service definition** – Enter *NLTrigger*.
    - **Description** – Enter *NiceLabel Label Cloud Trigger API*.
1. Select **Edit operations** to define the *Print* service operation. Set the following values for the new service operation:
    -**External service operation** – Enter *Print*.
    -**Description** – Enter *Print to local printer*.
    -**HTTP method** – Select *POST* method.
    - **Operation timeout** - Select the operation timeout (for example, , *500*).
    - **Request body type** - Select *Raw*. 
    - **Relative URL** - Enter */Trigger/v1/CloudTrigger/Api-CloudIntegrationDemo-Print*.
    - Expand **HTTP request headers** and create the following record:
        - **Key**: Ocp-Apim-Subscription-Key
        - **Value**: $auth.secret$ (exactly as written)
     - Expand **Request body** and create the following record:
        - **Content type**: Enter *application/json*
        - **Body**: 
            ```
            {
                "Printer": "$label.printer$",
                $label.body$
            }
            ```
1. Go back to the **External service definition**.
1. Expand **Label print service** tab.
1. In the **Print operation** field do not select anything.  
1. In the **Variables print operation** field select *Print* that has been created.  
1. In the **Variable label layout template** field set the following:
    ```
    "FilePath": "$SystemVariables.LabelFile$",
    "Quantity": "$SystemVariables.Quantity$",
    "Variables": [
    {{Row Table=LabelLayoutVariable
        { 
        "Name": "$LabelLayoutVariable.Variable$",
        "Value": "$LabelLayoutVariable.Value$"
        },
    }}
    ]
    ```

### Configure external service instance

Follow these steps to set up external service instance.

1. Go to **Warehouse Management \> Setup \> External services \> External service instances**.
1. On the Action Pane, select **New** to create an external service instance.
1. Set the following values for the new service instance:
    - **External service instance** - Enter a name for the instance (for example, *NLTriggerProd*).
    - **Description** - Enter a short description of the instance (for example, *NiceLabel Cloud Trigger API Production*).
    - **External service definition** – Select the service definition to use. The example service definition value that was suggested earlier in this article was *NLTrigger*.
1. Expand **General** tab and set the following values:
    - **Base URL** - Set *https://labelcloudapi.onnicelabel.com*.
    - **Authentication secret** - Enter the subscription key from the NiceLabel developer portal.
    - **Logging level** - Select *Successes and errors*.
    - **Log request bodies** - Select *Successes and errors*.

You can now proceed with creating label printers and label layouts using variables.

> [!NOTE]
> When creating label printers, use the name of the printer installed on the computer(s) running the NiceLabel Automation service.

> [!NOTE]
> When creating label layouts using variables, use the full path and file name of the label (as seen in the Path field in File Properties) or the label file's URL (also seen File Properties) for the LabelFile system variable.

> [!IMPORTANT]
> The information contained in this article is for general information purposes only. While we attempt to keep the information up to date and correct, Microsoft makes no representation or warranties of any kind, express or implied, about accuracy, reliability, or completeness with the respect to the NiceLabel product. We are not under control of the NiceLabel changes and if you experience any issues or have any addiitonal questions about NiceLabel product, please reach out to the Loftware company. 

## Additional resources

- [Label Layouts](print-license-plate-labels-using-label-layouts.md)
- [Document routing label layouts](document-routing-layout-for-license-plates.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
