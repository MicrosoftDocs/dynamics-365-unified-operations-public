---
title: Reuse product configurations
description: Learn about reusing product configurations, including outlines on requirements for reusing configurations and resetting configuration reuse.
author: sgmsft
ms.author: shwgarg
ms.topic: article
ms.date: 06/20/2017
ms.reviewer: kamaybac
ms.search.form: PCProductConfigurationModelDetails
ms.assetid: 4985e308-7824-41fc-83fd-fd0bdae888e3
---

# Reuse product configurations

[!include [banner](../includes/banner.md)]

You can specify that you want to automatically reuse an existing configuration for a product. Then, when a user has completed a configuration session, the system verifies whether a configuration that matches the user’s selections already exists. If a matching configuration is found, the configuration ID, corresponding bill of materials (BOM), and route are reused.

## Requirements for reusing configurations

To enable configurations to be reused, you must specify the following information for the components and attributes on the **Product configuration model details** page:

-   **Components and subcomponents** – On the **General** FastTab, in the **Reuse configurations** field, select **Yes**.
-   **Attributes** – On the **Attributes** FastTab, select the **Include in reuse** option. This option appears only when the related component is enabled for reuse. If you don't select any attributes for reuse, the configuration is always reused, regardless of the user’s selections during a configuration session. The attribute values in the existing configuration must match the user’s selections. For example, if the user selects **Blue** as the color during a configuration session, the system verifies whether an existing configuration of the component has the color blue.

## Resetting configuration reuse
When you reset configuration reuse, previously created configurations are no longer considered. You might want to reset configuration reuse if the BOM or route was changed, but no related attributes were changed. You reset configuration reuse on the **General** FastTab for the component.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]