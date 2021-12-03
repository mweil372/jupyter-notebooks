# VAPaxAvailSLA

## SLA
Once the upgrade to Linux has been completed it is measured using an automated script on the server measuring the availability of the Passenger Service by checking & logging the availability of the SSID (WLAN) and the software health after the booting phase. The System Uptime and hence the Expected Operation Time starts after the booting phase of the software initiated by power on. Any time the Passenger Service then is not available is considered an Unplanned Downtime.

## Suggested overview
| Event | Timestamp | CWAP status/health | AppCheck Status | Availability |
|-----|-----|-----|-----|-----|
|Power on/off|Nov 26, 2pm| aggregated CWAP status| aggregated AppCheck status| percentage of availability|
|Weight off wheels|Nov 26, 2pm| aggregated CWAP status| aggregated AppCheck status| percentage of availability|
|Inflight|Nov 26, 2pm| aggregated CWAP status| aggregated AppCheck status| percentage of availability|
|Inflight|Nov 26, 2pm| aggregated CWAP status| aggregated AppCheck status| percentage of availability|
|Inflight|Nov 26, 2pm| aggregated CWAP status| aggregated AppCheck status| percentage of availability|
|Weight on wheels|Nov 26, 2pm| aggregated CWAP status| aggregated AppCheck status| percentage of availability|


## Appchecks per component (SLA)
1. sum up all '1' values for a component
2. make max the number of rows with eventId = AppCheck in this powercycle
3. calculacte the availability (=SUM(Q$14:Q15)/SUM(R$14:R15)*100)

## CWAP health
CWAP SerialNumber:"%1"; CWAP Software-Version:"%6"; Configured Radio1 Status:"%2"; Configured Radio2 Status:"%3"; Actual Radio1 Status:"%4"; Actual Radio2 Status:"%5";  

## Windows report
![](./image%20(2).png)

## Requirements
For Windows we had a server boot time report from Stefan Beitlich
On Windows, report shows time in minutes
Aggregation level in the Windows reports is: calendar days; servers are not included but it seems reasonable to have servers added
A downtime of 100 h on a single a/c is the same (in terms of penabilities) as having a downtime of 20 on 5 a/

What is the definition of downtime?
Need to be finally defined

we will ignore appcheck status for DRM Widevine, Fairplay, Moving Map, Analytics Receiver since we don't see them relevant for the overall service availability
For Expected Operation Time we consider 
* first appcheck (timestamp) as the left boundary and power off as the right boundary
* we need to make sure that the report considers CWAP unavailabilities
* the unvailability time of a particular component needs to be summed up
* 
