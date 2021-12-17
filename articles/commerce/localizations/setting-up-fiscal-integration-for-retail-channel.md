---
# required metadata

title: Set up the fiscal integration for Commerce channels
description: This topic provides guidelines for setting up the fiscal integration functionality for Commerce channels. 
author: josaw
ms.date: 08/10/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: RetailFunctionalityProfile, RetailFormLayout, RetailParameters
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: Retail
ms.author: epopov
ms.search.validFrom: 2018-11-1
ms.dyn365.ops.version: 8.1.1

---
# Set up the fiscal integration for Commerce channels

[!include [banner](../includes/banner.md)]

This topic provides guidelines for setting up the fiscal integration functionality for Commerce channels. For more information about the fiscal integration, see [Overview of fiscal integration for Commerce channels](fiscal-integration-for-retail-channel.md).

The process of setting up the fiscal integration includes the following tasks:

- Configure fiscal connectors that represent fiscal devices or services that are used for fiscal registration purposes, such as fiscal printers.
- Configure document providers that generate fiscal documents that will be registered in fiscal devices or services by fiscal connectors.
- Configure the fiscal registration process that defines a sequence of fiscal registration steps and the fiscal connectors and fiscal document providers that are used for each step.
- Assign the fiscal registration process to point of sale (POS) functionality profiles.
- Assign connector technical profiles to hardware profiles.

## Set up a fiscal registration process

Before you use the fiscal integration functionality, you should configure the following settings.

### Update Commerce parameters.

1. On the **Commerce shared parameters** page, on the **General** tab, set the **Enable fiscal integration** option to **Yes**. On the **Number sequences** tab, define the number sequences for the following references:

    - Fiscal technical profile number
    - Fiscal connector group number
    - Registration process number

1. On the **Commerce parameters** page, define the number sequence for the fiscal functional profile number.

    > [!NOTE]
    > Number sequences are optional. Numbers for all fiscal integration entities can be generated either from number sequences or manually.

### Upload configurations of fiscal connectors and fiscal document providers.

A fiscal document provider is responsible for generating fiscal documents that represent transactions and events that are registered on the POS in a format that is also used for the interaction with a fiscal device or service. For example, a fiscal document provider might generate a representation of a fiscal receipt in an XML format.

A fiscal connector is responsible for the communication with a fiscal device or service. For example, a fiscal connector might send a fiscal receipt that a fiscal document provider created in an XML format to a fiscal printer. For more details about fiscal integration components, see [Fiscal registration process and fiscal integration samples for fiscal devices](fiscal-integration-for-retail-channel.md#fiscal-registration-process-and-fiscal-integration-samples-for-fiscal-devices).

1. On the **Fiscal connectors** page (**Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connectors**), upload an XML configuration for each device or service that you plan to use for fiscal integration purposes.

> [!TIP]
> By selecting **View**, you can view all functional and technical profiles that are related to the current fiscal connector.

1. On the **Fiscal document providers** page (**Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal document providers**), upload an XML configuration for each device or service that you plan to use.

> [!TIP]
> By selecting **View**, you can view all functional profiles that are related to the current fiscal document provider.

For examples of configurations of fiscal connectors and fiscal document providers, see [Fiscal integration samples in the Commerce SDK](fiscal-integration-for-retail-channel.md#fiscal-integration-samples-in-the-commerce-sdk).

> [!NOTE]
> Data mapping is considered part of a fiscal document provider. To set up different data mappings for the same connector (for example, state-specific regulations), you should create different fiscal document providers.

### Create connector functional profiles and connector technical profiles.

1. On the **Connector functional profiles** page (**Retail and Commerce \> Channel setup \> Fiscal integration \> Connector functional profiles**), create a connector functional profile for each combination of a fiscal connector and a fiscal document provider that is related to this fiscal connector.
    1. Select a connector name.
    1. Select a document provider.

You can change the data mapping parameters in a connector functional profile. To restore the default parameters that are defined in the fiscal document provider configuration, select **Update**.

**Examples**
| Parameter  | Format | Example |
|---|--------|---------|
| **VAT rates settings** | value : VATrate | 1 : 2000, 2 : 1800 |
| **VAT codes mapping** | VATcode : value | vat20 : 1, vat18 : 2 |
| **Tender types mapping** | TenderType : value | Cash : 1, Card : 2 |

> [!NOTE]
> Connector functional profiles are company-specific. If you plan to use the same combination of a fiscal connector and a fiscal document provider in different companies, you should create a connector functional profile for each company.

2. On the **Connector technical profiles** page (**Retail and Commerce \> Channel setup \> Fiscal integration \> Connector technical profiles**), create a connector technical profile for each fiscal connector.
    1. Select a connector name.
    2. Select a connector type. 
        1. For devices that are connected to a Hardware station or POS registers, select **Local**.
        1. For External services, connected to a Hardware station or POS registers, select **External**.
        1. For Internal signing service, select **Internal**. 
    3. Select a connector location.
        1. Hardware station if connector locates on the Hardware station
        1. Register if connector locates on the POS register



3. Parameters on the **Device** and **Settings** tabs in a connector technical profile can be changed. To restore the default parameters that are defined in the fiscal connector configuration, select **Update**. While a new version of an XML configuration is loaded, you receive a message that states that the current fiscal connector or fiscal document provider is already being used. This procedure doesn't override manual changes that were previously made in connector functional profiles and connector technical profiles. To apply the default set of parameters from a new configuration, on the **Connector functional profiles** page or the **Connector technical profiles** page, select **Update**.

4. If you need to setup unique connection parameters for specific POS register or Store:
    1. Click on Override menu item.
    1. In the override form, create new record.
    1. In the new record select specified store, or POS register. You can override parameters of selected technical profile for specified POS register or store.
    1. In the Device tab you can input special parameters for selected POS register or store.  

### Create fiscal connector groups.

    A fiscal connector group combines functional profiles of fiscal connectors that perform identical functions and are used at the same step of a fiscal registration process. For example, if several fiscal printer models can be used in a store, fiscal connectors for those fiscal printers can be combined in a fiscal connector group.

    1. On the **Fiscal connector group** page (**Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connector groups**), create a new fiscal connector group.
    1. Add functional profiles to the connector group. On the **Functional profiles** tab, select **Add**, and select a profile number. Each fiscal connector in a connector group can have only one functional profile.
    1. To suspend use of the functional profile, set the **Disable** option to **Yes**. This change affects only the current connector group. You can continue to use the same functional profile in other connector groups.

### Create a fiscal registration process.

    A fiscal registration process is defined by the sequence of registration steps and the connector group that is used for each step.

    1. On the **Fiscal registration process** page (**Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal registration processes**), create a new record for each unique process of fiscal registration.
    1. Add registration steps to the process:

        1. Select **Add**.
        1. Select a fiscal connector type.
        1. In the **Group number** field, select an appropriate fiscal connector group.

### Assign entities of the fiscal registration process to POS profiles.

    1. On the **POS functionality profiles** page (**Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**), assign the fiscal registration process to a POS functionality profile. Select **Edit**, and then, on the **Fiscal registration process** tab, in the **Process number** field, select a process.
    1. On the **POS hardware profile** page (**Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Hardware profiles**), assign connector technical profiles to a hardware profile. Select **Edit**, add a line on the **Fiscal peripherals** tab, and then, in the **Profile number** field, select a connector technical profile.

    > [!NOTE]
    > You can add several technical profiles to the same hardware profile. However, a hardware profile or POS functionality profile should have only one intersection with any fiscal connector group.

    The fiscal registration flow is defined by the fiscal registration process and also by some parameters of fiscal integration components: the Commerce runtime extension for the fiscal document provider and the Hardware station extension for the fiscal connector.

    - The subscription of events and transactions to fiscal registration is predefined in the fiscal document provider.
    - The fiscal document provider is also responsible for identifying the fiscal connector that is used for fiscal registration. It matches the connector functional profiles that are included in the fiscal connector group that is specified for the current step of the fiscal registration process with the connector technical profile that is assigned to the hardware profile of the Hardware station that the POS is paired to.
    - The fiscal document provider uses the data mapping settings from the fiscal document provider configuration to transform transaction/event data such as taxes and payments while a fiscal document is generated.
    - When the fiscal document provider generates a fiscal document, the fiscal connector can either send it to the fiscal device as is, or parse it and transform it into a sequence of commands of the device application programming interface (API), depending on how the communication is handled.

1. On the **Fiscal registration process** page (**Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal registration processes**), select **Validate** to validate the fiscal registration process.

    We recommend that you run this type of validation in the following cases:

    - After you've completed all the settings for a new registration process, including when you assign registration processes to POS functionality profiles and hardware profiles.
    - After you make changes to an existing fiscal registration process, and those changes might cause a different fiscal connector to be selected at runtime (for example, if you change the connector group for a fiscal registration process step, enable a connector functional profile in a connector group, or add a new connector functional profile to a connector group).
    - After you make changes in the assignment of connector technical profiles to hardware profiles.

1. On the **Distribution schedule** page, run the **1070** and **1090** jobs to transfer data to the channel database.

## Set up fiscal texts for discounts

In some cases, a special text must be printed on a fiscal receipt if a discount is applied. You can set up fiscal texts for discounts on the **Fiscal connector group** page (**Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connector groups**).

- For manual discounts that are applied at the POS, you should set a fiscal text for the info code or info code group that is specified as the **Product discount** info code in the POS functionality profile.

    1. On the **Fiscal connector group** page, select **Text for fiscal receipt**.
    1. On the **Info codes** tab, select **Add**, and select an info code or info code group.
    1. In the **Info code number** field, select a value.
    1. In the **Subcode number** field, select a value if a subcode is required for the selected info code.
    1. In the **Text for fiscal receipt** field, specify a fiscal text that should be printed on a fiscal receipt.
    1. Set the **Print user input on fiscal receipt** option to **Yes** to override the text on a fiscal receipt with information that a user manually enters at the POS. This option applies only to info codes that have an input type of **Text**.

    > [!NOTE]
    > You can specify a fiscal text for several info codes to support scenarios where info code groups, linked info codes, and triggered info codes are used. In these scenarios, the fiscal receipt will contain the fiscal texts from all info codes that are linked to the transaction line where the discount was applied.

- For channel-specific discounts, you should define a fiscal text for the discount ID.

    1. On the **Fiscal connector group** page, select **Text for fiscal receipt**.
    1. On the **Discounts** tab, select **Add**, and select a discount ID.
    1. In the **Text for fiscal receipt** field, specify a fiscal text that should be printed on a fiscal receipt.

    > [!NOTE]
    > If several discounts are applied to the same transaction line, the fiscal receipt will contain fiscal texts from all discounts that are linked to those transaction line.

## Set error handling settings

The error handling options that are available in the fiscal integration are set in the fiscal registration process. For more information about error handling in the fiscal integration, see [Error handling](fiscal-integration-for-retail-channel.md#error-handling).

1. On the **Fiscal registration process** page (**Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal registration processes**), you can set the following parameters for each step of the fiscal registration process:

    - **Allow skip** – This parameter enables the **Skip** option in the error handling dialog box.
    - **Allow mark as registered** – This parameter enables the **Mark as registered** option in the error handling dialog box.
    - **Continue on error** – If this parameter is enabled, the fiscal registration process can continue on the POS register if the fiscal registration of a transaction or event fails. Otherwise, to run the fiscal registration of the next transaction or event, the operator must retry the failed fiscal registration, skip it, or mark the transaction or event as registered. For more information, see [Optional fiscal registration](fiscal-integration-for-retail-channel.md#optional-fiscal-registration).

    > [!NOTE]
    > If the **Continue on error** parameter is enabled, the **Allow skip** and **Allow mark as registered** parameters are automatically disabled.

1. The **Skip** and **Mark as registered** options in the error handling dialog box require the **Allow skip registration or mark as registered** permission. Therefore, on the **Permission groups** page (**Retail and Commerce \> Employees \> Permission groups**), enable the **Allow skip registration or mark as registered** permission.
1. The **Skip** and **Mark as registered** options let operators enter additional information when fiscal registration fails. To make this functionality available, you should specify the **Skip** and **Mark as registered** info codes on a fiscal connector group. The information that operators enter is then saved as an info code transaction that is linked to the fiscal transaction. For more details about info codes, see [Info codes and info code groups](../info-codes-retail.md).

    > [!NOTE]
    > The **Product** trigger function isn't supported for the info codes that are used for **Skip** and **Mark as registered** in fiscal connector groups.

    - On the **Fiscal connector group** page, on the **Info codes** tab, select info codes or info code groups in the **Skip** and **Mark as registered** fields.

    > [!NOTE]
    > One fiscal document and one non-fiscal document can be generated on any step of a fiscal registration process. A fiscal document provider extension identifies every type of transaction or event as related to fiscal or non-fiscal documents. The error handling feature applies only to fiscal documents.
    >
    > - **Fiscal document** – A mandatory document that should be registered successfully (for example, a fiscal receipt).
    > - **Non-fiscal document** – A supplementary document for the transaction or event (for example, a gift card slip).

1. If the operator must be able to continue to process the current operation (for example, creation or finalization of a transaction) after a health check error occurs, you should enable the **Allow skip health check error** permission on the **Permission groups** page (**Retail and Commerce \> Employees \> Permission groups**). For more information about the health check procedure, see [Fiscal registration health check](fiscal-integration-for-retail-channel.md#fiscal-registration-health-check).

## Set up fiscal X/Z reports from the POS

To enable fiscal X/Z reports to be run from the POS, you should add new buttons to a POS layout.

- On the **Button grids** page, follow the instructions in [Add POS operations to POS layouts by using Button grid designer](../dev-itpro/add-pos-operations.md#add-a-custom-operation-button-to-the-pos-layout-in-retail-headquarters) to install the designer and update a POS layout.

    1. Select the layout to update. 
    1. Add a new button, and set the **Print fiscal X** button property.
    1. Add a new button, and set the **Print fiscal Z** button property.
    1. On the **Distribution schedule** page, run the **1090** job to transfer changes to the channel database.

## Enable manual execution of postponed fiscal registration

To enable manual execution of a postponed fiscal registration, you should add a new button to a POS layout.

- On the **Button grids** page, follow the instructions in [Add POS operations to POS layouts by using Button grid designer](../dev-itpro/add-pos-operations.md#add-a-custom-operation-button-to-the-pos-layout-in-retail-headquarters) to install the designer and update a POS layout.

    1. Select the layout to update.
    1. Add a new button, and set the **Complete fiscal registration process** button property.
    1. On the **Distribution schedule** page, run the **1090** job to transfer your changes to the channel database.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
