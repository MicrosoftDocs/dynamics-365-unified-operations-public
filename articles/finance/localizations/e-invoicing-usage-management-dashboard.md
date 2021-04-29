# Usage management dashboard

The usage management dashboard helps you monitor the usage of Electronic Invoicing service and keep the compliance over the monthly usage of your organization, by calculating the submission volume and comparing towards the acquired volume of submissions, in order you can identify deviations between acquired volume and used volume.

The dashboard presents 1 cost KPI (Key Process Indicator), from where you can monitor the consumption for licensing compliance purposes:

-   KPI: Usage per month (exporting direction)

And more 3 operational KPI from where you can track the usage of Electronic Invoicing service, for management purposes:

-   KPI: Usage by feature

-   KPI: Usage by environment

-   KPI: Usage per month (importing direction)

## Measurement scope

### Unit of measure

The Usage management dashboard counts business documents or electronic invoices.

### Organization

The counting is consolidated by tenant ID of your organization, no matter how many instances of Finance or Supply Chain Management, or Legal entities are enabled to the Electronic Invoicing service.

## KPI: Usage per month (exporting direction)

This KPI shows details of the usage issuing (exporting) electronic invoices per month by your organization.

### Counting Criteria

-   Submissions of business documents, from Finance and Supply Chain Management to the Electronic Invoicing service, independent of number of lines they might contain.

-   Submissions of business documents successfully processed by the Electronic Invoicing service. Successfully processed means the complete execution of the flow of actions defined in the feature setup:

    -   In the scenarios where the electronic invoice is submitted to an external web services, the counting is independent of the result of the web services processing (accepted, rejected or schema validation error). If the web services received and responded to the Electronic Invoicing service request, then it is considered as a valid counting.

### Counting exception criteria:

-   Resubmissions of business documents, from Finance and Supply Chain Management to the Electronic Invoicing service, required for accomplishing changes in the state/or status of electronic invoice life cycle are not counted:

    -   For example: the issuing of a Brazilian electronic invoice (fiscal document) is counted as valid, but its cancelation request is not counted.

### Direction

Export or issuing of electronic invoices.

## Calculation

The calculation of the KPI results from the following components:

### Free volume

The Free volume is a package of 100 submissions of business documents to the Electronic Invoicing service the customer gets monthly without need of payments.

The Free volume is not cumulative and nor rolled over as balance for the next period.

### Purchased

The Purchased volume is a package of 1K submissions of business documents to the Electronic Invoicing service you must acquire for your organization per month.

The Purchased volume is not cumulative and nor rolled over as balance for the next period.

### Used

The Used volume is the counting of the submissions of business documents to the Electronic Invoicing service as per criteria defined above.

### Balance

The Balance volume is the resulting balance of submissions of business documents to the Electronic Invoicing service.

For a given month, the formula for calculation of the Balance volume is:

Balance volume = Free volume + Purchased volume - Used volume

## Important

-   If your organization is going to exceed the monthly volume of 100 free submissions, then you will need to purchase the peak volume to stay compliant with the Microsoft licensing policy for Electronic Invoicing service.

-   As it is now, the Purchased volume must be entered manually, per date of acquisition, as multiple of packages of 1000 submissions.

## KPI: Usage by feature 

This KPI breaks down the usage of the electronic invoicing features deployed by your organization to the Electronic Invoicing service, showing the used electronic invoicing features for submissions during a defined range period (months).

### Counting Criteria

The same as for KPI Usage per month (exporting direction).

### Direction

The same as for KPI Usage per month (exporting direction).

## Calculation

The Used volume is the counting of the submissions of business documents to the Electronic Invoicing service grouped by processing of electronic invoicing feature.

## KPI: Usage by environment

This KPI breaks down the usage of the electronic invoicing environments deployed by your organization to the Electronic Invoicing service, showing used electronic invoicing environment during a defined range period (months).

### Counting Criteria

The same as for KPI Usage per month (exporting direction).

### Direction

The same as for KPI Usage per month (exporting direction).

## Calculation

The Used volume is the counting of the submissions of business documents to the Electronic Invoicing service grouped by processing from electronic invoicing environments.

## KPI: Usage per month (importing direction)

This KPI shows details of the receiving (importing) electronic invoices per month by your organization.

### Counting Criteria

-   Imported electronic invoices to Finance and Supply Chain Management, independent of number of lines they might contain.

### Direction

Import or receiving of electronic invoices.

## Calculation

The Received volume is the sum of the imported electronic invoices to Finance and Supply Chain Management as per criteria defined above.


Note: The Usage management dashboard does not show monetized amounts, only volume of counted submissions and/or imported documents.
