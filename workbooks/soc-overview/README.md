# SOC Overview Workbook

## Overview

Executive and on-call SOC dashboard providing real-time visibility into security incidents, alerts, and system health.

## Key Metrics

- **Total Incidents**: Count of open and recently closed incidents
- **Critical Alerts**: High-severity alerts from last 24 hours
- **MTTR (Mean Time To Resolution)**: Average incident resolution time
- **Alert Trend**: 7-day trend of alert volume
- **Top Threat Types**: Most common threats detected
- **Analyst Workload**: Incidents per SOC analyst

## Features

### Dashboard Sections

1. **Executive Summary** (Top Row)
   - Total Open Incidents (Card)
   - Critical Alerts (24h) (Card)
   - Average MTTR (Card)
   - System Health Score (Card)

2. **Incident Management** (Middle Row)
   - Incident Status Timeline
   - Incidents by Severity
   - Incidents by Status (Open, In Progress, Closed)
   - Top 10 Open Incidents

3. **Alert Trends** (Bottom Row)
   - 7-Day Alert Volume Trend
   - Alerts by Type (Pie Chart)
   - Alerts by Severity (Bar Chart)
   - Top Alert Rules Triggered

4. **SOC Health** (Right Panel)
   - Alert Queue Backlog
   - On-Call Analyst Assignments
   - Incident Age Distribution
   - Response Time SLA Status

## Data Sources

- `SecurityIncident` (Sentinel Incidents)
- `SecurityAlert` (Sentinel Alerts)
- `SecurityEvent` (Windows Events)

## Parameters

- **TimeRange**: 7 days (default, adjustable)
- **Severity Filter**: All (can filter by Critical, High, Medium, Low)
- **Status Filter**: All incident statuses

## Usage

1. Import `template.json` into Microsoft Sentinel
2. Select your Log Analytics workspace
3. Configure time range (default: Last 7 days)
4. Use filters to drill down into specific incidents
5. Pin key metrics to Azure dashboards

## Dependencies

- Microsoft Sentinel enabled in workspace
- SecurityIncident and SecurityAlert tables populated
- Read permissions on Sentinel data

## Customization Tips

- Adjust time ranges for different SLA thresholds
- Add organization-specific alert rules to filtering
- Modify severity thresholds for your organization
- Add custom KQL queries for specific threat hunting
