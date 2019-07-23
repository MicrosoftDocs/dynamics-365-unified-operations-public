# Deploy a new e-Commerce site

Proposed outline
### What is LCS?
	
Lifecycle Services (LCS) is a cloud-based collaborative workspace which allows partners and customers to manage their projects and environments, view latest information on Dynamics products and features  and create, track and browse support incidents. e-Commerce management features are integrated in the LCS portal.

To learn more about Lifecycle Services, please see:  https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/lifecycle-services/lcs-user-guide
	
### How do you get started

Before you can initialize e-Commerce, you need to have a project, environment and RCSU deployed. Person doing the initialization in the LCS portal needs to have either Project Owner or Environment Admin permissions. Supported environment topologies include production and sandbox.

For more information on environments, please see: https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/imp-lifecycle/environment-planning

For more information on RCSU (Retail Cloud Scale Unit), please see: https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/deployment/initialize-retail-channels

### How do you initialize e-Commerce

This procedure walks through the initialization of e-Commerce feature in an existing environment.

Before proceeding with the initialization, please make sure you have all the required information available:
- AAD B2C information (optional, can be added later with service request)
	- Client ID
	- Reply URL
	- SignUp SignIn Policy ID
	- Login Custom Domain
	- Tenant Name
	- Edit Profile Policy ID
	- Reset password Policy ID
- RCSU to be used
- AAD security group to be used for system admins
- Ratings and reviews moderation security group (optional)
- Domains to be associated with the environment

When you have the information available, you can proceed with these steps to initialize the e-Commerce:

1. Log in to the LCS portal
2. Navigate to the project that contains the environment that you are planning to initialize e-Commerce on
3. Open the environment management page for the environment in question
4. Open retail management view (Activate "Manage" under "Environment Features)
5. Activate e-Commerce tab, you should see that e-Commerce components are not initialized yet and the only action on the view is to initialize e-Commerce
6. Activate "Initialize e-Commerce", you will notice a pane opening with input fields. You will be requested to enter information required for provisioning. (Please see list below for details)
7. Fill in the required information and proceed to the next page.
8. Fill in the required information and submit the form.
9. You are returned to the e-Commerce view and you can see that the initialization has started
10. You can refresh the page or return later to this view in order to see the initialization status
	
### What happens in LCS when e-Commerce is enabled

When e-Commerce feature is initialized from the LCS portal, system provisions several components required for e-Commerce and associates them with the environment. After the provisioning e-Commerce tab in the Retail management view will be updated to reflect that. The view shows latest customization deployments and if one is ongoing at that time. View also includes links to the e-Commerce site (the website) and the e-Commerce site management tool (authoring tool).

### Accessing your authoring environment

You can find links to your e-Commerce site and the site management tool from the e-Commerce view in the Retail management view.

