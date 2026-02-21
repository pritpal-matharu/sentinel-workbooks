# Threat Hunting Workbook

## Overview

Proactive threat hunting dashboard providing pivoting and correlation across entities, log sources, and attack patterns for advanced security investigations.

## Key Metrics & Hunting Capabilities

- **Entity Enrichment**: IP, domain, user, and file hash analysis
- **Lateral Movement Detection**: Cross-system movement patterns
- **Command & Control (C2) Indicators**: Suspicious network communications
- **Process Tree Analysis**: Execution flow and parent-child relationships
- **Data Exfiltration Patterns**: Unusual network traffic and file transfers
- **Living-off-the-Land Binaries (LoLBin) Usage**: Abuse of legitimate tools

## Features

### Hunting Sections

1. **Entity Pivot** (Search & Enrichment)
   - IP/Domain Lookup
   - User Activity Timeline
   - File Hash Intelligence
   - Process Execution Analysis

2. **Attack Patterns** (Detection)
   - Lateral Movement Chains
   - Living-off-the-Land Execution
   - Credential Harvesting Attempts
   - Data Staging Activities

3. **Network Hunting** (Correlation)
   - Unusual Port Activity
   - DNS Query Anomalies
   - External Network Connections
   - Protocol Abuse Detection

4. **Behavioral Analysis** (Investigation)
   - Privilege Escalation Chains
   - Registry Modifications
   - File System Changes
   - Service Installation Patterns

## Data Sources

- `DeviceProcessEvents` (Process execution)
- `DeviceNetworkEvents` (Network connections)
- `DeviceFileEvents` (File modifications)
- `DeviceRegistryEvents` (Registry changes)
- `SecurityEvent` (Windows event logs)
- `CommonSecurityLog` (Network appliance logs)
- `DnsEvents` (DNS query logs)

## Hunting Queries Included

### Command Execution Hunting
```
DeviceProcessEvents
| where InitiatingProcessFileName in~ ("cmd.exe", "powershell.exe")
| where ProcessCommandLine contains_any ("whoami", "net user", "ipconfig")
| project TimeGenerated, DeviceName, ProcessCommandLine
```

### Lateral Movement Detection
```
DeviceNetworkEvents
| where ActionType == "ConnectionSuccess"
| where RemotePort in (445, 3389, 22)  // SMB, RDP, SSH
| summarize Connections=count() by InitiatingProcessName, RemoteIP
| where Connections >= 5
```

### Data Exfiltration Indicators
```
DeviceNetworkEvents
| where Direction == "Outbound"
| where InitiatingProcessFileName not in ("browser.exe", "svchost.exe")
| where RemotePort in (53, 80, 443, 8080)
| summarize TotalBytes=sum(SentBytes) by InitiatingProcessFileName, RemoteIP
| where TotalBytes > 100MB
```

## Usage

1. Import `template.json` into Microsoft Sentinel
2. Connect required data sources (Defender, Windows Events, Network logs)
3. Use entity search for quick lookups
4. Run hunting queries against suspicious patterns
5. Create custom KQL queries for your environment
6. Pin successful hunts as bookmarks for investigation

## Hunting Methodology

This workbook supports:
- **Indicator-based hunting**: Search for known IOCs
- **Behavior-based hunting**: Detect abnormal patterns
- **Threat intel hunting**: Correlate with known attack patterns
- **Rule-based hunting**: Automated detection of TTPs

## Customization Tips

- Add internal IP ranges to baseline exclusions
- Create custom threat intelligence feeds
- Add industry-specific hunting scenarios
- Build organization-specific behavioral baselines
- Create team-specific hunting runbooks
