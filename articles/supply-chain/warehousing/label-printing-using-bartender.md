---
title: Print labels using the Seagull Scientific BarTender® label service solution
description: This article describes how to set up and print labels by using the Seagull Scientific BarTender® label service solution.
author: GalynaFedorova
ms.author: gfedorova
ms.reviewer: kamaybac
ms.search.form: WHSLabelLayout, WHSLabelLayoutDataSource
ms.topic: how-to
ms.date: 01/05/2023
ms.custom: bap-template
---

# Print labels using the Seagull Scientific BarTender® label service solution

[!include [banner](../includes/banner.md)]

This article describes how to set up and print labels in Microsoft Dynamics 365 Supply Chain Management by using the BarTender® labeling solution by Seagull Scientific. It's one example that shows how to use the Supply Chain Management external service label printing feature. For general information about how this feature works, see [Print labels using an external service](label-printing-using-external-label-service.md).

The BarTender labeling solution is available both as on-premises software and as a cloud-based software-as-a-service (SaaS) offering that's named BarTender Cloud™. Currently, only BarTender Cloud can be used together with the external label printing service for Supply Chain Management.

This article describes how to integrate Supply Chain Management with BarTender Cloud. It includes information about how to communicate with BarTender Cloud by exchanging documents in YAML format though the BarTender Cloud REST API. For more information about BarTender Cloud, see [BarTender Cloud](https://www.seagullscientific.com/software/cloud/).

> [!IMPORTANT]
> By enabling the external service integration, you affirm that you understand that the data handling, privacy, and compliance standards of the external service might not be the same as the standards that are provided by Dynamics 365 Supply Chain Management. To learn whether the external service meets your organization's security and privacy requirements, including requirements for the handling of personal data and geo-residency, consult the external service's documentation and terms. Your privacy is important to us. To learn more, read the [Microsoft Privacy Statement](https://privacy.microsoft.com/privacystatement).
>
> The information in this article is for general informational purposes only. Although we try to keep the information up to date and correct, Microsoft makes no representation or warranties of any kind, express or implied, about accuracy, reliability, or completeness with respect to the BarTender product. Seagull Scientific might change the functionality of the BarTender product at any time without notice. If you have any additional questions about the BarTender product, contact [Seagull Scientific](https://www.seagullscientific.com/support/microsoft-dynamics-365-scm/).

## Prerequisites

To use the features that are described in this article, you must be running Supply Chain Management version 10.0.34 or later.

## <a name="prepare-integration"></a>Get a copy of your personal access token from BarTender Cloud

Before you can access BarTender Cloud through its REST API, you must get a copy of your personal access token from BarTender Cloud. Supply Chain Management will use this token to authenticate with BarTender Cloud. For more information about how to get this token, see [BarTender Cloud REST API](https://support.seagullscientific.com/hc/en-us/articles/9756611024535) in the BarTender help center. Be sure to make a note of the token, because you'll have to enter it later.

> [!NOTE]
> Personal access tokens expire after 30 days. You'll have to enter a new token before the old one expires. You can manually refresh the token to obtain a new one.

## Configure Supply Chain Management to print to printers managed by BarTender Cloud

For the scripts that the BarTender Cloud service must run, the BarTender Cloud Actions REST API accepts several formats, including YAML-based and JSON-based action scripts and scripts that use the older BarTender XML (BTXML) format. In this article, the label that's printed is based on a design that's saved in your BarTender Cloud account. The article describes how to use the `PrintBTWAction` action to print the label to a printer that's accessed through a BarTender Cloud Print Gateway that's installed on your local network.

### Set up an external service definition for printing through the Actions API

Follow these steps to set up an external service definition.

1. Go to **Warehouse management \> Setup \> External services \> External service definitions**.
1. On the Action Pane, select **New** to create an external service definition.
1. Set the following fields for the new service definition:

    - **External service definition** – Enter a name for the service definition (for example, *BTCloud*).
    - **Description** – Enter a short description of the service definition (for example, *BarTender Cloud*).

1. On the Action Pane, select **Save**.
1. On the **External service operations** FastTab, select **Edit operations** on the toolbar.
1. On the **External service operations** page, on the Action Pane, select **New** to add an operation for printing variable-based layouts. Then follow these steps for the new record:

    - On the header, set the following fields:

        - **External service operation** – Enter a name for the operation (for example, *Actions*).
        - **Description** – Enter a short description of the operation (for example, *Actions API*).

    - On the **General** FastTab, set the following fields:

        - **HTTP method** – Select *POST*.
        - **Operation timeout** – Enter a time-out period for the operation, in milliseconds (for example, *500*).
        - **Request body type** – Select *Raw*.
        - **Relative URL** – Enter */api/actions*.

        > [!NOTE]
        > Cloud Print is a synchronous API. Therefore, it will wait until the label has been printed and will then provide immediate feedback about whether printing was successful. However, because this process can take several seconds, the system might provide a bad user experience for mobile device users. Additionally, the result isn't currently used. Therefore, we recommend that you set a time-out period of 500 milliseconds. Even though Supply Chain Management stops waiting after this time-out expires, printing will continue in the background.

    - On the **Request HTTP headers** FastTab, add a row, and set the following fields for it:

        - **Key** – Enter *Authorization*.
        - **Value** – Enter *Bearer \$auth.secret\$*. Be sure to enter the value exactly as it appears here.

    - On the **Request body** FastTab, set the following fields:

        - **Content type** – Enter *text/yaml*.
        - **Body** – Enter the content of the request body. Here's an example.

            ```YAML
            - SetVariableAction:
                VariableName: D365PrinterName
                VariableValue: $label.printer$
            $label.body$
            ```

            > [!IMPORTANT]
            > Paste the body text exactly as it appears here. Indentation is important. Be sure to use four spaces to indent. Don't use tabs.

1. On the Action Pane, select **Save**.
1. Select the **Close** button to return to the **External service definition** page.
1. In the list pane, select the record that you were working on at the beginning of this procedure.
1. On the **Label print service** FastTab, set the following fields:

    - **Print operation** – Leave this field blank.
    - **Variables print operation** – Select the name of the operation that you created for printing variable-based layouts (for example, *Actions*).
    - **Variable label layout template** – Enter the content for your variable-based layout template. Here's an example.

        ```YAML
        - PrintBTWAction:
            DocumentFile: librarian://Main/$SystemVariables.LabelFile$
            Printer: "%D365PrinterName%"
            Copies: $SystemVariables.Quantity$
            NamedDataSources:
        {{Row Table=LabelLayoutVariable
              $LabelLayoutVariable.Variable$: $LabelLayoutVariable.Value$
        }}

        ```

        > [!IMPORTANT]
        > Paste the body text exactly as it appears here. Indentation is important. Be sure to use four spaces to indent. For the NamedDataSources variables be sure to use six spaces to indent. Don't use tabs.

### Set up an external service instance for printing through the Actions API

For this procedure, you'll need the personal access token that you previously [obtained from BarTender Cloud](#prepare-integration).

Follow these steps to set up an external service instance for printing through the Actions API.

1. Go to **Warehouse Management \> Setup \> External services \> External service instances**.
1. On the Action Pane, select **New** to create an external service instance.
1. Set the following fields for the new service instance:

    - **External service instance** – Enter a name for the instance (for example, *BTCloud*).
    - **Description** – Enter a short description of the instance (for example, *BTCloud*).
    - **External service definition** – Select the service definition to use with the instance. The example service definition value that was suggested earlier in this article was *BTCloud*.

1. On the **General** tab, set the following fields:

    - **Base URL** – Enter one of the following instance URLs, depending on the region:

        - **For the AMER region:** `https://am1.bartendercloud.com`
        - **For the EMEA region:** `https://eu1.bartendercloud.com`
        - **For the APAC region:** `https://ap1.bartendercloud.com`

    - **Authentication secret** – Enter the personal access token that you obtained from BarTender Cloud. You should have made a note of this token earlier, when you were [preparing for BarTender integration](#prepare-integration).
    - **Logging level** – Select *Successes and errors*.
    - **Log request bodies** – Select *Successes and errors*.

You can now create label printers and label layouts.

> [!NOTE]
>
> - When you create label printers on the **Label printers** page in Supply Chain Management, in the **Label print service printer name** field, enter the name of the printer as it appears in the **Print** dialog box in BarTender Cloud, or as it's retrieved from the Printer API. Use the following format: *printer:workstation/printer*.
> - When you create a variable-based label layout on the **Label layout** page of Supply Chain Management, in the **System Variables** grid, include a row where the **Variable name** field is set to *LabelFile* and the **Value** field is set to the full path and file name of the label (including any folders, if the label file is stored in a folder). The BarTender Cloud REST API uses a Librarian path, but the beginning of the full Librarian name has already been coded in the variable label template.
> - When you create a variable-based label layout, **Variable name** in the **Data variables** grid cannot be the same as **Variable name** in the **System variables** grid.

## Additional resources

- [Print labels using an external service](label-printing-using-external-label-service.md)
- [Label Layouts](print-license-plate-labels-using-label-layouts.md)
- [Document routing label layouts](document-routing-layout-for-license-plates.md)
