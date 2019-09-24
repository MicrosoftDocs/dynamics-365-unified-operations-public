# Preview environment provisioning guide
This guide provides you step-by-step instructions on how to provision and configure the Microsoft Dynamics 365 Commerce Preview environment.
## Summary
In order to provision the Preview environment successfully, the project needs to be created with a specific product name and type. Environment and Retail Cloud Scale Unit also have some specific parameters you need to use when provisioning them, in order to be able to start the e-Commerce provisioning later. These instructions contain all the required steps you need to take and parameters you need to use.

After successful provisioning, there are few post-provisioning steps you need to take in order to prepare your Preview environment for use. There are few steps which are optional, depending on which aspects of the system are you expecting to evaluate. Should you later change your mind, you can always run the optional steps later.
## Prerequisites
In order to complete the provisioning successfully, the following prerequisites must be met
* You have LCS access
* You have been accepted to the Commerce public preview program
* You have the required permissions to create **Prospective presales**-projects
* You have **Environment manager** or **Project Owner** role in the project where you will be provisioning the environment
* You either need to have admin access to your Azure subscription or request Subscription admin to help you with the two steps that require admin permissions
* You have your AAD tenant ID available
* You have created AAD security group to be used as e-Commerce system admins group and you have its ID available
* You have created AAD security group to be used as Ratings and reviews moderator group and you have its ID available (can be the same SG as the system admin group above)
## Optional prerequisites
If you want to evaluate transactional email features, the following prerequisites must be met
* You have email server available for your use (SMTP server) which can be used from the Azure subscription where you provision the preview environment to - have the server FQDN/IP, SMTP port number and authentication details available
## Provisioning preview environment
These instructions cover the provisioning of Microsoft Dynamics 365 Commerce Preview environment. After successfully completing these steps, you will have a Preview environment ready to be configured. All the activities described here take place in the LCS portal.
### Before starting
Log in to the LCS portal at https://lcs.dynamics.com

Make sure that you are logged in with the LCS account that was used to request the preview access.
### Create project
1. Click "+" to create a new project
1. Choose "Prospective presales"
1. Enter name, description and industry as you see fit
1. For "Product name", select "Microsoft Dynamics 365 for Retail"
1. For "Product version", select "Microsoft Dynamics 365 for Retail"
1. For "Methodology", select "Dynamics AX implementation methodology"
1. You may import roles and users from existing project if that is desired
1. Proceed with "Create"
1. You are sent to the project view
### Create environment
##### Adding Azure Connector
1. From the menu, select "Project settings"
1. Select "Azure connectors"
1. Click "+ Add" to add Azure Connector
1. Enter name as you see fit
1. Enter your Azure Subscription details. Consult your Azure subscription admin if required.
1. Proceed with "Next"
1. Follow the instructions on the screen to grant required application(s) access to your subscription. Consult your Azure subscription admin if required.
1. Proceed with "Next"
1. Follow the instructions on the screen to grant required application(s) access to your subscription. Consult your Azure subscription admin if required.
1. Proceed with "Next"
1. For "Azure region", choose either "East US", "East US 2", "West US" or "West US 2"
1. Proceed with "Connect"
1. Your Azure Connector should appear in the list
##### Creating the environment
1. From the menu, select "Cloud-hosted environments"
1. Click "+ Add" to add an environment
1. For "Application version", select "10.0.6" or higher from the list
1. Leave "Platform version" as is
1. Proceed with "Next"
1. For environment topology, choose "DEMO"
1. If you configured a single Azure Connector earlier, that will be used for this environment. In case you configured multiple Azure Connectors, you have the option to select which connector you would like to use. "East US", "East US 2", "West US" or "West US 2" is recommended for best end-to-end performance.
1. Enter "Environment name" as appropriate
1. Adjust VM size as you see fit
1. Leave "Advanced settings" as they are
1. After studying the pricing and licensing terms on the screen, tick the checkbox to indicate agreement
1. Proceed with "Next"
1. In the deployment confirmation screen, after verifying that the details are correct click "Deploy"
1. You are sent back to "Cloud-hosted environments"-view and your environment should appear in the list
1. Wait until your environment status is "Deployed" before proceeding
### Provision RCSU
1. While in the "Cloud-hosted environments"-view, select your environment from the list
1. From the environment view on the right side of the screen, click "Full details" - you are sent to environment details-view
1. Under "ENVIRONMENT FEATURES", click "Manage"
1. From "Retail"-tab, press "Initialize" - you will be sent to the RCSU initialization parameters view
1. For region, select "East US", "East US 2", "West US" or "West US 2"
1. For version, specify "9.16.19260.7"
1. Enable "Apply extension"
1. From the list of extensions, choose "Mock Recommendations for Dynamics 365 Commerce"
1. Proceed with "Initialize"
1. In the deployment confirmation screen, after verifying that the details are correct click "Yes"
1. You are sent back to the "Retail management"-view with "Retail"-tab activated. Your RCSU has been queued for provisioning.
1. Wait until your RCSU status is "SUCCESS" before proceeding
### Provision e-Commerce
##### Configure AAD consent
**(AAD STEPS HERE)**
##### Provision e-Commerce
1. Switch to the "e-Commerce (Preview)"-tab
1. After reviewing the Preview consent proceed with clicking "Setup"
1. Enter "e-Commerce tenant name" as you see fit - However, note that this will be visible in some of the URLs pointing to your e-Commerce instance
1. For "Retail cloud scale unit name", select your RCSU from the list (list should only have one option)
1. "e-Commerce geography" is automatically populated and cannot be changed.
1. Proceed to the next page with "Next"
1. For "Supported host names", enter any valid domain (e.g. www.fabrikam.com)
1. For "AAD security group for system admin" enter the AAD SG ID that you wish to use as e-Commerce system admin group
1. For "AAD security group for ratings and review moderator" enter the AAD SG ID that you wish to use as Ratings and reviews moderator group
1. Leave the B2C values empty (7 fields that start with B2C)
1. Proceed with "Initialize"
1. You are sent back to the "Retail management"-view with "e-Commerce (Preview)"-tab activated. Your e-Commerce initialization has started.
1. Wait until your e-Commerce initialization status is "INITIALIZATION SUCCESSFUL" before proceeding
## Post-provisioning steps
At this stage the environment has been provisioned end-to-end, but there are still few configuration steps that need to be taken care of before you can start evaluating the environment.
### Before starting
Log in to the environment
### Configure email server (optional)

### Configure email templates (optional)

### Configure payment connector

### Configure POS

### Configure image backend

### Site setup
