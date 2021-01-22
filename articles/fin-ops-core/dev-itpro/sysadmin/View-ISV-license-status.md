# View Independent software vendor (ISV) license status

[!include [banner](../includes/banner.md)]

This topic explains how you can view status for ISV licenses for Finance and Operations apps, such as Microsoft Dynamics 365 Finance, Dynamics 365 Supply Chain Management, and Dynamics 365 Commerce.

License codes and configuration keys are part of the ISV licensing model for Microsoft Dynamics Finance and Operations apps.

> [!NOTE]
> Configuration keys that are provided by Microsoft are not part of the licensing model for Microsoft Dynamics Finance and Operations apps. They are used only to enable and disable functionality.

When an ISV license key and code are installed the corresponding configuration key will be available and enabled on the **License configuration** form.

## To view ISV license status
Each ISV solution that is tied to a license runs only when a valid license code exists in the customer's environment. Therefore, if an ISV ties its solution to a license, but the customer doesn't have a valid license code, the solution doesn't run. To prevent loss of functionality it is important to track the expiration dates, if applicable, for license codes. To view go to **System administration > Setup > License configuration** and select the **License codes** tab:

![License codes](media/LicenseCodes.png)

To avoid downtime, it is recommended to review expiration dates of license keys, and if applicable obtain and import new license keys prior to moving to a new version.
The tab will show the license codes that has expired. The corresponding configuration key will not appear in the **Configuration keys** tab.


## Additional resources
For more information about the ISV licensing feature, see [Independent software vendor (ISV) licensing](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/dev-tools/isv-licensing).

For more information about to import ISV licenses into an on-premise deployment, see [Independent software vendor (ISV) licensing (on-premises)](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/dev-tools/isv-licensing-on-prem).

For more information about the related report, see [License codes and configuration keys report](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/sysadmin/license-codes-configuration-keys-report).
