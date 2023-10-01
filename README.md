# Microsoft-Sentinel-Lab

# RDP Failures Geolocation Tracking

### Overview

This GitHub repository contains a PowerShell script designed to analyze Windows Event Logs for failed RDP (Remote Desktop Protocol) login attempts. It utilizes a third-party API to retrieve geographic information about the attackers' locations.

In the accompanying YouTube demonstration, I showcase the setup of Azure Sentinel (SIEM) connected to a live virtual machine acting as a honeypot. We monitor real-time RDP brute force attacks from across the globe and use a custom PowerShell script to pinpoint the attackers' geographical details, visualizing them on an Azure Sentinel Map.

![RDP Failures Geolocation Tracking](https://imgur.com/a/L2Hd7Zn)

## Querying Logs with Sentinel in log analytical workspace 

To effectively analyze RDP failure logs from Windows Event Viewer, you can use the following PowerShell command as an example. This command uses the Kusto Query Language (KQL) to extract and summarize relevant information:

FAILED_RDP_WITH_GEO_CL
|extend username = extract(@"username:([^,]+)", 1, RawData),
         timestamp = extract(@"timestamp:([^,]+)", 1, RawData),
         latitude = extract(@"latitude:([^,]+)", 1, RawData),
         longitude = extract(@"longitude:([^,]+)", 1, RawData),
         sourcehost = extract(@"sourcehost:([^,]+)", 1, RawData),
         state = extract(@"state:([^,]+)", 1, RawData),
         label = extract(@"label:([^,]+)", 1, RawData),
         destination = extract(@"destinationhost:([^,]+)", 1, RawData),
         country = extract(@"country:([^,]+)", 1, RawData)
 |where destination != "samplehost"
 |where sourcehost != ""
 |summarize event_count=count() by timestamp, label, country, state, sourcehost, username, destination, longitude, latitude

In this example, we're using Kusto Query Language (KQL) to process logs and extract specific fields like username, timestamp, latitude, longitude, and more. You can adapt this command to suit your log analysis requirements and source data.

Make sure to replace "FAILED_RDP_WITH_GEO_CL" with the actual name of the log or data source you're querying. Users can modify and execute this command in their own environment to analyze logs more effectively.


## Technologies Used

- **PowerShell:** Extracts failed RDP login logs from Windows Event Viewer.

## External Services

- **ipgeolocation.io:** Utilized for IP Address to Geolocation mapping.
![ipgeolocation](https://imgur.com/a/QPIM7Uj)


### Worldwide Attack Map After 24 Hours

![Worldwide Attack Map](https://imgur.com/a/weSpAK8)
