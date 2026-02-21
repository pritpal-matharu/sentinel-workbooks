# Cloud Security Workbook

## Overview

Cloud infrastructure security dashboard monitoring Azure resource changes, policy violations, network configuration anomalies, and access control issues.

## Key Metrics

- **Policy Violations**: Compliance violations detected
- **Resource Changes**: Unauthorized or unusual modifications
- **Network Misconfigurations**: Insecure network configurations
- **Access Control Changes**: Role assignments and permission escalations
- **Publicly Exposed Resources**: Storage accounts/databases exposed
- **Failed Deployments**: Deployment errors and blocked operations

## Features

### Dashboard Sections

1. **Compliance Metrics** (Top Row)
   - Policy Violations (Card)
   - Network Misconfigurations (Card)
   - Publicly Exposed Resources (Card)
   - Failed Deployments (Card)

2. **Azure Activity Analysis** (Middle Row)
   - Resource Changes Timeline
   - Changes by Resource Type
   - Failed Operations by Service
   - Access Control Changes Log

3. **Security Posture** (Bottom Row)
   - Network Security Group (NSG) Violations
   - Key Vault Access Patterns
   - Storage Account Configurations
   - Subscription-level Changes

## Data Sources

- `AzureActivity` (Azure control-plane activity)
- `AzureAdministrativeActivityLogs` (Administrative actions)
- `AzureSecurityStatusSnapshot` (Compliance status)
- `CommonSecurityLog` (Network device logs)

## Alert Conditions

- Resource deletion or major modification
- Policy violations detected
- Unauthorized access control changes
- Network security group changes
- Public exposure of sensitive resources

## Usage

1. Import `template.json` into Microsoft Sentinel
2. Connect Azure Activity/Administrative logs
3. Monitor for policy violations
4. Investigate resource changes and access modifications
5. Review network configuration changes

## Customization Tips

- Add resource group filters
- Integrate with Azure Policy for compliance
- Add cost analysis metrics
- Create resource inventory baseline
