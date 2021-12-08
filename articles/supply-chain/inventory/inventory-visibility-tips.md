<!--
 * @Author: your name
 * @Date: 2021-12-08 17:50:36
 * @LastEditTime: 2021-12-08 18:02:26
 * @LastEditors: Please set LastEditors
 * @Description: 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
 * @FilePath: \undefinedc:\Users\qiwzhou\Desktop\InventoryServicePowerApps\Dynamics365Doc\Dynamics-365-Operations\articles\supply-chain\inventory\inventory-visibility-tips.md
-->

# Inventory Visibility Tips

[!include [banner](../includes/banner.md)]

1. Currently, only Dataverse environments that were created by using LCS are supported. If your Dataverse environment was created in some other way (for example, by using the Power Apps admin center), and if it's linked to your Supply Chain Management environment, you must first contact the Inventory Visibility product team at [inventvisibilitysupp@microsoft.com](mailto:inventvisibilitysupp@microsoft.com) to fix the mapping issue. You can then install Inventory Visibility.

1. If you have more than one LCS environment, create a different Azure AD application for each environment. If you use same application ID and tenant ID to install the Inventory Visibility Add-in for different environments, a token issue will occur for older environments. Only the last one that was installed will be valid.

1. Currently the inventory visibility is not supported for cloud-hosted environment, it is supported for Tier-2+ environments.

1. Currently the API supports querying 100 individual items (ProductID). As for sites and locations, multiple SiteIDs and LocationIDs can be specified in a query and the maximum limit is that **NumOf(SiteID) * NumOf(LocationID) <= 100**.

1. The `fno` data source is reserved for Dynamics 365 Supply Chain Management. If your Inventory Visibility Add-in is integrated with Finance and Operations environment, we recommend not to delete fno related configurations in [Data Source](inventory-visibility-configuration.md#data-source-configuration).

1. Currently, the [partition configuration](inventory-visibility-configuration.md#partition-configuration) consists of 2 base dimensions, SiteId and LocationId, which indicate how the data is distributed. Operations under the same partition can have higher performance with lower cost. This default partition configuration has already been pre-set implicitly. **You do not have to define it by yourself**. Delete or change the default partition configuration may lead to unexpected error. Please do not customize partition configuration.

1. Base dimensions that are defined in the partition configuration should not be defined in [Product index hierarchy configuration](inventory-visibility-configuration.md##index-configuration)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
