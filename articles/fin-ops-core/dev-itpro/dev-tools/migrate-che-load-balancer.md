---
title: Migrate a CHE load balancer 
description: Learn how to migrate a CHE load balancer for existing CHE environments.
author: pranavjani
ms.author: pranavjani
ms.topic: how-to 
ms.date: 03/21/2025
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
---

# Migrate a CHE load balancer

[!INCLUDE[banner](../includes/banner.md)]

Microsoft Azure announced the retirement of classic load balancers. To ensure that CHE environments can continue to be provisioned, Microsoft implemented provisioning for new CHE environments and migration for existing CHE environments.

## Provision new CHE environments

As of March 28, 2025, all new CHE environments are configured with a load balancer and a public IP address that uses the standard stock-keeping unit (SKU). This transition helps enhance the performance and reliability of our cloud infrastructure.

## Migrate existing CHE environments

Before you migrate, it's crucial to ensure that you have the necessary permissions and contributor access to the subscription. This access allows you to upgrade the load balancer without encountering any permission-related issues. After you verify your access, you can set the required variables and run the migration commands.

To migrate existing CHE environments, follow these steps.

1. Set the variables for the subscription ID, resource group name, and load balancer name.

   ```powershell
   $resourceGroupName = "<resourcegroup-name>"
   $loadBalancerName = "<loadbalancer-name>"
   $subscriptionId = "<subscription-id>"
   $outboundRuleName= "http-outbound-rule"
   $backendPoolName = "vm-backend-pool"
   ```

1. Run the following command to ensure that you specified the correct subscription ID that is associated with the basic load balancer.

   ```powershell
   Select-AzSubscription -Subscription $subscriptionId
   ```

1. Run the following commands to initiate the load balancer migration. This command installs the load balancer upgrade module. It also upgrades the basic load balancer and IP address to the standard SKU.

   ```powershell
   Install-Module -Name AzureBasicLoadBalancerUpgrade -Scope CurrentUser -Repository PSGallery -Force
   Start-AzBasicLoadBalancerUpgrade -ResourceGroupName $resourceGroupName -BasicLoadBalancerName $loadBalancerName
   ```

   > [!NOTE]
   > The basic load balancer supports outbound traffic by default. Therefore, it enables seamless internet access for your virtual machines (VMs). However, the standard SKU load balancers don't automatically permit outbound access for backend pool members. To enable this critical functionality, you must complete the remaining steps of this procedure. In this way, you ensure that your VMs can communicate with the internet for updates, data transfers, and other essential operations.

1. Create the backend pool.

   ```powershell
   $loadBalancer = Get-AzLoadBalancer -ResourceGroupName $resourceGroupName -Name $loadBalancerName
   $backendPool = New-AzLoadBalancerBackendAddressPoolConfig -Name $backendPoolName
   ```

1. Link all VMs to the standard load balancer, and connect the network interface card (NIC) with the backend pool.

   ```powershell
   $nic = Get-AzNetworkInterface -ResourceGroupName $resourceGroupName
   $ipConfig = $nic.IpConfigurations | Where-Object { $_.PrivateIpAddress -ne $null }
   $ipConfig.LoadBalancerBackendAddressPools.Add($backendPool)
   ```

1. Add the backend pool to the load balancer.

   ```powershell
   $loadBalancer.BackendAddressPools.Add($backendPool)
   $frontendIPConfig = $loadBalancer.FrontendIpConfigurations
   $outboundRule = New-AzLoadBalancerOutboundRuleConfig -Name $outboundRuleName -BackendAddressPool $backendPool -FrontendIpConfiguration $frontendIPConfig -Protocol All - 
   IdleTimeoutInMinutes 4 -AllocatedOutboundPort 1000
   $loadBalancer.OutboundRules.Add($outboundRule)
   Set-AzLoadBalancer -LoadBalancer $loadBalancer
   Set-AzNetworkInterface -NetworkInterface $nic
   ```

The backend pool that is created should have following configuration:

- **BackendPoolConfiguration** should be of the **NIC** type.
- **IP configurations** should list all VMs that need outbound connectivity.
- The **Used by** section should contain **http-outbound-rule** in the list.

## More information

- If any of the preceding commands fails or encounters an issue, refer to the comprehensive guide, [Upgrade a basic load balancer with PowerShell](/azure/load-balancer/upgrade-basic-standard-with-powershell).
- If you have multiple CHE environments, ensure the successful migration of *one* of them before you move on to bulk migrations.
- Learn about pricing for the standard SKU load balancers in [Load Balancer pricing](https://azure.microsoft.com/pricing/details/load-balancer).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
