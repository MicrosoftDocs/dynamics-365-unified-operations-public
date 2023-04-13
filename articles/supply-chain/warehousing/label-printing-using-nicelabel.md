---
title: Print labels using the Loftware NiceLabel label service solution
description: This article describes how to set up and print labels using Loftware NiceLabel label service solution.
author: GalynaFedorova
ms.author: gfedorova
ms.reviewer: kamaybac
ms.search.form: WHSLabelLayout, WHSLabelLayoutDataSource
ms.topic: how-to
ms.date: 04/04/2023
ms.custom: bap-template
---

# Print labels using the Loftware NiceLabel label service solution

[!include [banner](../includes/banner.md)]

<!-- KFM: I used the term "NiceLabel Automation Service" almost everywhere where "NiceLabel Automation" was mentioned, except where NiceLabel Automation Manager was mentioned specifically. This should probably be verified (search and check) -->

This article describes how to use the print labels in Microsoft Dynamics 365 Supply Chain Management using the Loftware NiceLabel solution.

Loftware NiceLabel lets you create, manage, and print standardized, compliant barcode labels. In addition, it lets you print labels to supported cloud-connected printers or a wide variety of classic on-premises printers. NiceLabel has several products available that can be used together with the external label printing service, including their cloud solution (NiceLabel Cloud) and several versions of their on-premises products. This article focuses on how to integrate Supply Chain Management with the NiceLabel Cloud solution, but parts of the article that use NiceLabel automation can also be used with other products. <!-- KFM: I'm not sure what we mean by this second phrase. Recommend to just remove it. -->

For more information about Loftware NiceLabel Cloud, see [Loftware NiceLabel Cloud & Label Management System](https://www.loftware.com/products/labeling/nicelabel-cloud).

> [!IMPORTANT]
> By enabling the external service integration, you are affirming that you understand that the data handling, privacy, and compliance standards of the external service may not be the same as those provided by Dynamics 365 Supply Chain Management. Please consult the external service's documentation and terms to learn whether your organization's security and privacy requirements are met by the external service, including the handling of personal data and geo-residency. Your privacy is important to us. To learn more, read the [Microsoft Privacy Statement](https://privacy.microsoft.com/privacystatement).

*NiceLabel Cloud* supports two integration approaches for other cloud applications:

- **Cloud Print API** – NiceLabel Cloud generates the labels and sends print jobs to the printer. This can be either a so-called *cloud printer* (a printer connected directly to the NiceLabel Cloud instance, without using any locally installed software or printer driver), or any printer that is connected to a workstation with a print gateway component installed. For the current list of supported cloud printers, see the [Loftware web site](https://www.loftware.com/).
- **Cloud Trigger API** – NiceLabel Cloud sends messages to an on-premises NiceLabel Automation Service instance, which generates the labels and sends them to the printer. You must install a Windows printer driver for each of your printers.

If you don't want any local software footprint, then Cloud Print API with supported printers is the preferred option. Otherwise, we suggest using the Cloud Trigger API as the preferred option, but both options are available.

Here are some of the pros and cons of each integration option:

- Cloud Trigger API lets you use use an out-of-the-box cloud integration pack or completely customize the processing of print requests.
- Cloud Print API is synchronous (the server waits for the print engine to print the label) and reports the outcome of the print job, but Supply Chain Management doesn't use this result. You must therefore wait a bit longer when printing labels or set a timeout on the external service operation. If a timeout occurs, the Cloud Print API will continue printing, but the request will be logged as a timeout.
- On-premises printer naming is simpler in the Cloud Trigger API because you can use the names of the printers as configured on the server(s) running the NiceLabel Automation Service. To use the Cloud Print API, you must specify a workstation ID to identify which workstation to print to.
- For Cloud Trigger API, you can install multiple instances of the NiceLabel Automation Service on the local network to achieve load balancing and high availability. As noted in the previous point, you must specify which workstation the printing request will be routed to, and if that workstation isn't available, the label won't print. Conversely, multiple NiceLabel Automation Service instances can handle requests to the same cloud trigger.
- Cloud Print API has a smaller installation footprint.

## <a name="prepare-integration"></a>Prepare for NiceLabel Cloud integration

Before you can access NiceLabel Cloud using either Cloud Print API or the Cloud Trigger API, you must register on the NiceLabel Developer Portal and then link your developer portal subscription with your NiceLabel Cloud instance. For instructions, see [Cloud Integrations](https://help.nicelabel.com/hc/en-001/articles/4402966072209-Cloud-Integrations#cloud-integrations-1-0) on the NiceLabel Help Center.

> [!IMPORTANT]
> As you are registering on the NiceLabel Developer Portal, be sure to make a copy of your primary or secondary subscription key (use primary by default). You will need this key later to configure the external service definition. <!-- KFM: I think this belongs here. Please confirm. -->

If you wish to use printers enabled for internet of things (IoT), you must connect them to your NiceLabel Cloud instance. For instructions, see [Cloud Printers](https://help.nicelabel.com/hc/en-001/articles/4407466158737-Cloud-Printers) on the NiceLabel Help Center.

## Configure Supply Chain Management to print to cloud printers using the Cloud Print API

Using the Cloud Print API, you can print labels that are generated by NiceLabel Cloud based on variables sent from Supply Chain Management or send a ZPL (Zebra Programming Language) label (such as an existing label layout or a shipping label provided by a shipping carrier for small parcel shipping (SPS) integration). The external service definition will contain two operations, one for printing variables-based layouts and the second for printing ZPL-based label layouts. <!-- KFM: we refer to the concepts of "variables-based layouts" and "ZPL-based label layouts" several times, but using different terms. Are these the preferred terms? -->

### Set up an external service definition

Follow these steps to set up an external service definition.

1. Go to **Warehouse management \> Setup \> External services \> External service definitions**.
1. On the Action Pane, select **New** to create an external service definition.
1. Set the following values for the new service definition:
    - **External service definition** – Enter a name for the service definition (for example, *NLPrint*).
    - **Description** – Enter a short description of the service definition (for example, *NiceLabel Cloud Print API*).
1. Select **Save** on the Action Pane.
1. From the **External service operations** FastTab toolbar, select **Edit operations**.
1. The **External service operations** page opens. Select **New** on the Action Pane to add a new operation, which is for the *Print* service operation <!-- KFM: Is this the "variables-based layout" operation we mention earlier? -->. Make the following settings for the new record:

    - Make the following settings in the header:
        - **External service operation** – Enter a name for the operation (for example, *Print*).
        - **Description** – Enter a short description of the operation (for example, *Print to cloud printer*).

    - Make the following settings on the **General** FastTab.
        - **HTTP method** – Select *POST*.
        - **Operation timeout** – Enter a timeout period, in milliseconds (for example, *500*).
        - **Request body type** – Select *Raw*.
        - **Relative URL** – Enter */Print/v2/Print*.

        > [!NOTE]
        >  Cloud Print is a synchronous API, which means that it will wait until the label has been printed and will then provide immediate feedback about whether the printing was successful or not. However, because this might take several seconds, the system could provide a bad user experience for mobile device users. Additionally, the result is currently not used. Therefore we have suggested a quick timeout setting of 500 ms. Even though Supply Chain Management stops waiting after this timeout expires, the print will continue in the background. <!-- KFM: I'd like to clarify this a bit more. Let's discuss it. -->

    - On the **HTTP request headers** FastTab, add a row with the following settings:
        - **Key** – Enter *Ocp-Apim-Subscription-Key*.
        - **Value** – Enter *$auth.secret$*.

    - On the **Request body** FastTab, make the following settings:
        - **Content type** – Enter *application/json*
        - **Body** – Enter the following code: <!-- KFM: Is this always the value we want here, or just an example? Also, is there an error in the last line? -->

            ```JSON
            {
                "deviceType": "CloudPrinter",
                "deviceId": {
                    "printerName": "$label.printer$",
                    "workstation": null
                },
                $label.body$
            }
            ```

1. Select **Save** on the Action Pane.
1. Select **New** on the Action Pane to create a second new operation, this time for sending data <!-- KFM: Is this the "printing ZPL-based label layouts" operation we mention earlier? -->. This time, make the following settings for the new record:
    - Make the following settings in the header:
        - **External service operation** – Enter a name for the operation (for example, *SendData*).
        - **Description** – Enter a short description of the operation (for example, *Send ZPL to cloud printer*).
    - Make the following settings on the **General** FastTab.
        - **HTTP method** – Select *POST*.
        - **Operation timeout** – Set the operation timeout (for example, *500*).
        - **Request body type** – Select *Raw*.
        - **Relative URL** – Enter */Print/v2/SendData*.
    - On the **HTTP request headers** FastTab, add a row with the following settings:
        - **Key** – Enter *Ocp-Apim-Subscription-Key*.
        - **Value** – Enter *$auth.secret$*.
    - On the **Request body** FastTab, make the following settings:
        - **Content type** – Enter *application/json*
        - **Body** – Enter the following code: <!-- KFM: Is this always the value we want here, or just an example? -->

            ```JSON
            {
                "deviceType": "CloudPrinter",
                "deviceId": {
                    "printerName": "$label.printer$",
                    "workstation": null
                },
                "data": "$label.body:base64$"
            }
            ```

1. Select **Save** on the Action Pane.
1. Select the **Close** button to go back to the **External service definition** page.
1. On the list pane, select the record you were working on at the start of this procedure.
1. Expand the **Label print service** FastTab and make the following settings:
    - **Print operation** – Select the send-data operation that you created in this procedure (for example, *SendData*).
    - **Variables print operation** – Select the print operation that you created in this procedure (for example, *Print*).
    - **Variable label layout template** – Enter the following code: <!-- KFM: Is this always the value we want here, or just an example? Also, is this JSON too? Also, do we have too many "{" here? } -->

        ```JSON
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

### Set up an external service instance

<!-- KFM: Add intro: what is an "external service instance", what does it do, and why do we need one? -->

Follow these steps to set up an external service instance.

1. Go to **Warehouse Management \> Setup \> External services \> External service instances**.
1. On the Action Pane, select **New** to create an external service instance.
1. Set the following values for the new service instance:
    - **External service instance** – Enter a name for the instance (for example, *NLPrintProd*).
    - **Description** – Enter a short description of the instance (for example, *NiceLabel Cloud Print API Production*).
    - **External service definition** – Select the service definition to use. The example service definition value that was suggested earlier in this article was *NLPrint*.
1. Expand the **General** tab and set the following values:
    - **Base URL** – Enter *https:\/\/labelcloudapi.onnicelabel.com*.
    - **Authentication secret** – Enter your primary or secondary subscription key from the NiceLabel Developer Portal. You should have made a note of this earlier when you were [preparing for NiceLabel integration](#prepare-integration).
    - **Logging level** – Select *Successes and errors*.
    - **Log request bodies** – Select *Successes and errors*.

You can now proceed to create label printers and label layouts using either variables or ZPL.

> [!NOTE]
>
> - When creating label printers, use the name of the printer from the **Cloud printers** tab in NiceLabel Cloud Control Center for the **Label print service printer name** field. <!-- KFM: Not sure what we mean by "creating label printers"-->
> - When creating label layouts using variables, use the full path and file name of the label (as seen in the **Path** field in **File Properties**) for the `LabelFile` system variable.

## Configure Supply Chain Management to print to local network printers using the Cloud Trigger API

Using the Cloud Trigger API, you can call an on-premise installation of the NiceLabel Automation Service, which then processes the request and performs preprogrammed actions. Before proceeding with the following steps, install NiceLabel on the computers that will run the NiceLabel Automation Service and also set up the required printers for those computers. For guidance on how to install and set up printers, see the NiceLabel documentation. <!-- KFM: Can we give a link? -->

To simplify the configuration of the NiceLabel Automation Service, use the NiceLabel Cloud Data Integration pack and follow the instructions provided in [Appendix A: Integration bundle](https://help.nicelabel.com/hc/en-001/articles/7361192275217-Appendix-A-Integration-bundle) on the NiceLabel Help Center. The following procedure summarizes the required steps (more details are provided on the NiceLabel Help Center).

1. Use the link provDownload the integration pack from the URL in the document.
1. Sign in to your NiceLabel Control Center.
1. In Documents, create a new folder `/Demo/LabelCloudDataIntegration`.
1. Open the integration pack ZIP file and extract the files.
1. Upload your Document Storage folder contents into your `CloudIntegration` folder in your DMS (Document Management System).
1. On the computer where the NiceLabel Automation Service is installed, open the NiceLabel Automation Manager.
1. If not activated yet, connect the NiceLabel Automation Service to your NiceLabel Cloud.
1. In the NiceLabel Automation Manager, select **Add** and browse to the `LabelCloudDataIntegration` folder on the NiceLabel Cloud.
1. Open the `CloudIntegration-CloudTrigger.misx` file.
1. Start only the Print trigger (verify that it is using the Unique identifier Api-CloudIntegrationDemo-Print); other triggers are not currently used by Supply Chain Management.

After you have installed and started the Print trigger, we can configure the External Service Definition and External Service Instance required to access the NiceLabel Automation Service using the Cloud Trigger API. Without customizing the demo automation configuration, we can only print labels defined using variables, therefore we will be only configuring one operation on the External Service Definition. Use the following steps to create the definition and instance:

### Configure external service definition

Follow these steps to set up external service definition.

1. Go to **Warehouse management \> Setup \> External services \> External service definitions**.
1. On the Action Pane, select **New** to create an external service definition.
1. Set the following values for the new service definition:
    - **External service definition** – Enter *NLTrigger*.
    - **Description** – Enter *NiceLabel Label Cloud Trigger API*.
1. Select **Edit operations** to define the *Print* service operation. Set the following values for the new service operation:
    - **External service operation** – Enter *Print*.
    - **Description** – Enter *Print to local printer*.
    - **HTTP method** – Select *POST* method.
    - **Operation timeout** – Select the operation timeout (for example, , *500*).
    - **Request body type** – Select *Raw*.
    - **Relative URL** – Enter */Trigger/v1/CloudTrigger/Api-CloudIntegrationDemo-Print*.
    - Expand **HTTP request headers** and create the following record:
        - **Key**: Ocp-Apim-Subscription-Key
        - **Value**: $auth.secret$ (exactly as written)
    - Expand **Request body** and create the following record:
        - **Content type**: Enter *application/json*
        - **Body**: Enter the following code: <!-- KFM: What code language are we showing here? -->

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
1. In the **Variable label layout template** field set the following: <!-- KFM: What code language are we showing here? -->

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
<!-- KFM: How is this section different from the previous one with the same name? -->

Follow these steps to set up external service instance.

1. Go to **Warehouse Management \> Setup \> External services \> External service instances**.
1. On the Action Pane, select **New** to create an external service instance.
1. Set the following values for the new service instance:
    - **External service instance** – Enter a name for the instance (for example, *NLTriggerProd*).
    - **Description** – Enter a short description of the instance (for example, *NiceLabel Cloud Trigger API Production*).
    - **External service definition** – Select the service definition to use. The example service definition value that was suggested earlier in this article was *NLTrigger*.
1. Expand **General** tab and set the following values:
    - **Base URL** – Set *https:\/\/labelcloudapi.onnicelabel.com*.
    - **Authentication secret** – Enter the subscription key from the NiceLabel developer portal.
    - **Logging level** – Select *Successes and errors*.
    - **Log request bodies** – Select *Successes and errors*.

You can now proceed with creating label printers and label layouts using variables.

> [!NOTE]
> When creating label printers, use the name of the printer installed on the computer(s) running the NiceLabel Automation Service.

> [!NOTE]
> When creating label layouts using variables, use the full path and file name of the label (as seen in the Path field in File Properties) or the label file's URL (also seen File Properties) for the LabelFile system variable.

> [!IMPORTANT]
> The information contained in this article is for general information purposes only. While we attempt to keep the information up to date and correct, Microsoft makes no representation or warranties of any kind, express or implied, about accuracy, reliability, or completeness with the respect to the NiceLabel product. We are not under control of the NiceLabel changes and if you experience any issues or have any additional questions about NiceLabel product, please reach out to the Loftware company. 

## Additional resources

- [Print labels using external label service solutions](label-printing-using-external-label-service.md)
- [Label Layouts](print-license-plate-labels-using-label-layouts.md)
- [Document routing label layouts](document-routing-layout-for-license-plates.md)
