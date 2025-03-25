Overview
--------
This application integrates two industrial protocols: MTConnect and OPC UA. It fetches real-time machine data from an MTConnect server and exposes it through an OPC UA server, making it accessible to OPC UA clients. The goal is to bridge these protocols, exploring use cases like factory monitoring, legacy system integration, and smart manufacturing.

Features
--------
- Pulls data from MTConnect endpoints (/probe, /current, /sample, /assets)
- Serves data via an OPC UA server with secure authentication
- Updates nodes with machine status, timestamps, and units
- Handles connection failures with retries and status updates
- Runs in demo mode (stops after 1 hour)

Requirements
------------
- Windows 10 or higher (64-bit)
- Internet connection (for fetching MTConnect data)
- OPC UA client (e.g., UaExpert) for testing

Installation
------------
1. Download the provided exe file
2. Install it to a folder on your Windows machine (e.g., C:\MTConnectAdapter).
3. Ensure config.toml is in the same folder as the executable (see Configuration below).

Configuration
-------------
Create or edit config.toml in the same folder as the executable with these settings (defaults shown):
[mtconnect]
baseUrl = "https://demo.mtconnect.org"
pollInterval = 1000  # milliseconds
connectionTimeout = 10  # seconds

[opcua]
port = 4840
username = "admin"
password = "password"

Adjust baseUrl to your MTConnect server, and tweak other settings as needed. A sample config.toml is included.

Running the Application
-----------------------
1. Double-click MTConnect-OPCUA-Adapter.exe in the installed folder, or run it from Command Prompt.
2. The OPC UA server starts at opc.tcp://localhost:4840/MTConnectAdapter.
3. Open an OPC UA client to view data under the "MTConnect" folder.
4. A console window shows connection status and data updates.
5. Press Ctrl+C in the console to stop, or wait 1 hour for demo mode to end.

Usage Notes
-----------
- Data like "Yabs" or "Ztravel" appears under MTConnect.<machineId>.current or .sample.
- If values show "UNAVAILABLE," check your MTConnect server's output.
- Connection failures trigger "Pending Failure" or "Connection Fail" statuses after retries.

Potential Use Cases
-------------------
- Real-Time Monitoring: View machine data in OPC UA dashboards.
- Legacy Integration: Connect MTConnect machines to modern OPC UA systems.
- Predictive Maintenance: Use data for upkeep planning.
- Smart Manufacturing: Feed machine stats into Industry 4.0 platforms.

Troubleshooting
---------------
- "Failed to load config.toml": Ensure config.toml is in the same folder as the executable and is valid.
- "Connection timeout": Verify your network and MTConnect URL.
- "Port in use": Change the opcua.port in config.toml and restart.
- Check the console for error messages and suggestions.

License
-------
This Application is distributed under Bufferstack.IO Shareware License and comes with no warranty.. 
Bufferstack.IO Analytics Technology LLP or its partners or software distributors are not responsible for 
any kind of damage or data loss or unwanted result that might occur due to this application usage

Feedback
--------
Questions or ideas? Reach out on GitHub or LinkedIn. Let’s explore how this integration can grow!
