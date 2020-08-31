Performance issues with resource scheduling can occur when dealing with projects that number in the thousands.  The reasons for the performance issues are the resource capacity roll-up synchronization process and added ResProjectResource table.  The new feature below will remove teh roll-up synchronization process and deformalize ResProjectResource table.  Please note, if there is a dependency on either the resource capacity roll-up synchronization process or added ResProjectResource table then this feature should not be used.

To enable resource scheduling performance enhancement feature
1.       Feature management > All > look for 'Enable project resource scheduling performance enhancement feature' > Clicks 'Enable now'
o    Note: If you can't find this feature, clicks 'Check for updates' button first
2.       Reload the web browser
3.       Project management and accounting > Periodic > Project resources > Synchronize resource calendars capacity across all companies
o    Remove existing capacity records - Set yes to remove previous data. If you want generate incremental data, set it to No.
o    Period code - Generate data according to the selected period range. If this option is selected, then start date and end date will not needed to be defined specification.
o    Start date - specific start date for the data generation
o    End date - specific end date for the data generation
o    Clicks OK
o    Note: This will general data to the ResCalendarCapacity table across all companies. So this batch job is only needed to execute in one LE. The data is needed to calculate resource capacity through the associated calendar.
4.       Project management and accounting > Periodic > Project resources > Populate project resources across all companies
o    Just clicks OK
o    Note: This is the data upgrade script to general data for ResProjectResource, ResCalendarDateTimeRange, ResEffectiveDateTimeRange tables. Also it updates values for PSAPRojSchedRole.RootActivity table field. If this was not executed, then your will get warning when executing many resource scheduling operations that this batch job is not executed yet.
 
To disable resource scheduling performance enhancement feature
1.       Feature management > All > look for 'Enable project resource scheduling performance enhancement feature' > Clicks 'Disable'
2.       Reload the web browser
3.       Project management and accounting > Periodic > Capacity synchronization > Synchronize resource capacity roll-ups
o    Remove existing capacity records - Set yes to remove previous data. If you want generate incremental data, set it to No.
o    Period code - Generate data according to the selected period range. If this option is selected, then start date and end date will not needed to be defined specification.
o    Start date - specific start date for the data generation
o    End date - specific end date for the data generation
o    Clicks OK
o    Note: This will general data to the ResRollup table across all companies. So this batch job is only needed to execute in one LE. This is needed for all Resource Availability View control. If this is not executed, then ResRollup data will be generated on the fly which can take times.
