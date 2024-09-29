<div align="center">
  <a href="https://github.com/github_username/repo_name">
    <img src="images/logo.png" alt="Logo" width="80" height="80">
  </a>

<h3 align="center">:fire: Zabbix Palo Alto Firewall API Monitoring Template :fire:</h3>

  <p align="center">
      This template is designed to monitor Palo Alto firewalls through Zabbix using the API. It allows for comprehensive monitoring of Palo Alto devices from A to Z without the need to write custom scripts.
  </p>
</div>

## Why Monitor with the API?

Traditionally, SNMP has been widely used for monitoring, but certain Palo Alto models and versions encounter compatibility issues. This can result in gaps during monitoring with SNMP. To address this problem, the Palo Alto API interface provides more accurate and stable monitoring.

The API allows for more detailed data collection, enabling better tracking of network security measures and resource performance.

## Key Features :rocket:

- **Comprehensive Monitoring**: Monitor the performance, resources, interfaces, and security measures of Palo Alto firewalls via the API.
- **No Scripts Needed**: This template is easy to install and deploy within Zabbix without the need for custom scripts.
- **High Accuracy**: By directly interacting with the API, more accurate data is gathered.
- **Version and Model Compatibility**: Overcome the compatibility issues often encountered with SNMP by using the API.

## Requirements :page_with_curl:

To use this template, the following requirements must be met:

- Palo Alto device (with API support panos v10 or newer)
- Zabbix Server v6.4 or newer
- Zabbix Agent
- API username and password
- Palo Alto API key

## Installation :lotus_position:

### Step 1: Enabling the API on the Palo Alto Device :point_left:

1. Log in to the Palo Alto firewall management interface.
2. Go to the **Device** section.
3. In the left panel, navigate to **Setup > Management > API Key Lifetime** and ensure it is enabled, if necessary.

### Step 2: Adding the Palo Alto Device in Zabbix :point_left:

1. Log in to the Zabbix Web Interface.
2. Go to **Configuration > Hosts**.
3. Click on **Create Host** and add your Palo Alto device:
   - **Host Name**: PaloAlto_Firewall
   - **Host Interface**: The IP address of your Palo Alto device
   - **Template**: Palo Alto Firewall API Monitoring

### Step 3: Import the Palo Alto API Template :point_left:

1. Navigate to the **Template** section (**Configuration > Templates**).
2. Click **Import** and upload the template file.
3. Apply the template to your device.

### Step 4: Enter the API Key in Zabbix :point_left:

:eight_spoked_asterisk: Obtain the API key from your Palo Alto device:
   ```bash
   curl -k -X POST "https://<firewall-ip>/api/?type=keygen&user=<username>&password=<password>"
   ```
:eight_spoked_asterisk: Add the obtained API key to the Zabbix host:
   - Go to the **Macros** section.
   - **Macro Name**: `{PALO_API_KEY}`
   - **Value**: Enter your API key here.

## Step 5: Start Monitoring :point_left:

Once the host and template are correctly configured, monitoring of your Palo Alto firewall will begin automatically.

## Data and Metrics :warning:

This template can monitor the following data:

- CPU and memory usage
- Interface status and statistics
- Security policy-related statistics
- Session information
- Tracked security events
- Traffic analysis

## Contributing

If you would like to expand the functionality of this template or suggest additional monitoring parameters, feel free to make changes as you see fit. I welcome your feedback and contributions!

## License

This project is distributed under an open-source license. For more information, please refer to the license file.
