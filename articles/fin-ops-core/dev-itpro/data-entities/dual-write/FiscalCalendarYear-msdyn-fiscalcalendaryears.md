## Fiscal calendar year integration entity to msdyn_fiscalcalendaryears

This template synchronizes data between Finance and Operations and Common Data Service.

Source field | Map type | Destination field
---|---|---
FISCALCALENDAR_CALENDARID | = | msdyn_fiscalcalendarname
NAME | = | msdyn_name
STARTDATE | = | msdyn_startdate
ENDDATE | = | msdyn_enddate
FISCALCALENDAR_CALENDARID | = | msdyn_calendar.msdyn_calendar
