# Dynamics 365 Commerce Pricing Migration to Unified Pricing Management

## Version 10.0.46

### Overview
Dynamics 365 Unified Pricing Management (UPM) migration is designed to help Dynamics 365 Commerce customers seamlessly transition from the legacy Commerce Pricing Engine to the new Unified Pricing Management framework — without heavy configuration or disruption.

This enhancement focuses on simplifying adoption, ensuring that customers can quickly experience the benefits of centralized and flexible pricing management. It lays the groundwork for customers to later extend their pricing strategies by incorporating additional pricing attributes for greater precision and control.

The migration is structured into three incremental phases (from version 10.0.46 to 10.0.48), allowing organizations to move at their own pace and address various user scenarios and existing Commerce Pricing Engine configurations.

> **Note:** This provides a clearer overview of the contents included in the 10.0.46 migration script.

---

### Sections

| Feature | Current non-attribute rule | New non-attribute rules | New attribute-based rules |
|----------|-----------------------------|--------------------------|----------------------------|
| Trade agreement price | Support | Can also migrate | Support |
| Discount | Migrate | Not support | Support |
| Shipping discount | Not support Yet | Not support | Support |
| Tender discount | Not support yet | Not support | Not support yet |
| Charges | Support | No migration (In the plan to migrate existing charges rules) | Support |
| Rebate management | Not support yet | Not support yet | Support |
| Trade agreement discount | Support | No migration | Not support | Not support yet |
| Price group | Migrate to attributes | Not support | Support |
| Price adjustments | Migration does not support till 10.0.47 | Not support | Support |

---

## Migration Process

### Step 1: Enable the Feature
In **Feature Management**, enable the feature:

> **Unified pricing management pricing rule performance and enhancement**

This activation unlocks the necessary migration options to migrate from Commerce Pricing Engine to Unified Pricing Management.

---

### Step 2: Set Up Price Group Mapping for Migration
Once the feature is enabled, navigate to:

**Retail and Commerce > Migration > Setup Price group mapping for migration**

- All existing Commerce Price Groups will automatically be converted to Unified Pricing Management Price Groups.  
- Each new group will retain the same price group conditions as its legacy configuration.  
- If duplicate mappings exist, the system will prompt you to resolve them manually.  
- After resolving any duplicates, click **Validate** before proceeding.

---

### Step 3: Migrate Commerce Pricing Setup
Next, open:

**Retail and Commerce > Migration > Migrate Commerce Pricing Setup**

This screen allows you to run the migration job that transitions your current Commerce Pricing Engine data into the Unified Pricing Management framework.

> **Note:** In version 10.0.46, Price Adjustments are not yet included. Their migration support will be added in version 10.0.47.

---

### Step 4: Configure Migration Parameters
When running the migration job:

- Use the **Effective after date** field to select pricing rules that are still active and should be migrated.  
- You can also choose whether to:  
  - Include disabled discounts  
  - Skip trade agreements  

If you want to continue applying existing trade agreements (without attributes), configure the corresponding parameters accordingly.

Once complete, your data and configurations will be successfully migrated to Unified Pricing Management, providing a foundation for future enhancements to flexible pricing strategy.
