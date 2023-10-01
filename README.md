# Microsoft-Sentinel-Lab

# RDP Failures Geolocation Tracking

## YouTube Demo

### Overview

This GitHub repository contains a PowerShell script designed to analyze Windows Event Logs for failed RDP (Remote Desktop Protocol) login attempts. It utilizes a third-party API to retrieve geographic information about the attackers' locations.

In the accompanying YouTube demonstration, I showcase the setup of Azure Sentinel (SIEM) connected to a live virtual machine acting as a honeypot. We monitor real-time RDP brute force attacks from across the globe and use a custom PowerShell script to pinpoint the attackers' geographical details, visualizing them on an Azure Sentinel Map.

![RDP Failures Geolocation Tracking](https://i.imgur.com/TmEMcM5.jpg)

## Technologies Used

- **PowerShell:** Extracts failed RDP login logs from Windows Event Viewer.

## External Services

- **ipgeolocation.io:** Utilized for IP Address to Geolocation mapping.

### Visualizing Attacks from Different Regions

![Attack Dataflow](https://i.imgur.com/2MViSiL.jpg)

### Worldwide Attack Map After 24 Hours

![Worldwide Attack Map](https://i.imgur.com/krRFrK5.png)
