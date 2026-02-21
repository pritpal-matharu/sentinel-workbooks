# Identity Security Workbook

## Overview

Comprehensive identity and access security dashboard for monitoring Entra ID authentication threats, risky sign-ins, and privilege escalation attempts.

## Key Metrics

- **Risky Sign-ins**: Count of flagged risky authentications
- **MFA Failures**: Failed multi-factor authentication attempts
- **Privilege Escalations**: Suspicious privilege elevation events
- **Failed Logins**: Failed authentication attempts (24h)
- **Risk Detection Rate**: Percentage of sign-ins flagged as risky
- **User Lockouts**: Accounts locked due to failed attempts

## Features

### Dashboard Sections

1. **Risk Metrics** (Top Row)
   - Risky Sign-ins (24h) (Card)
   - MFA Failures (24h) (Card)
   - Failed Logins (24h) (Card)
   - User Lockouts (24h) (Card)

2. **Risk Indicators** (Middle Row)
   - Risky Sign-ins by Risk Level (Pie Chart)
   - Sign-in Risk Trend (7d) (Time Chart)
   - Top Users with Risky Sign-ins (Table)
   - Risk Detections by Type (Bar Chart)

3. **Authentication Analysis** (Bottom Row)
   - Failed Logins by Country/Region
   - MFA Enforcement Status
   - Privilege Escalation Events
   - Conditional Access Policy Blocks

## Data Sources

- `SigninLogs` (Azure AD sign-in activity)
- `AADNonInteractiveUserSignInLogs` (Service principal sign-ins)
- `AADServicePrincipalSignInLogs` (Service principal activity)
- `AuditLogs` (Privilege escalation and access changes)

## Alert Thresholds

- **Risky**: RiskLevel >= "medium"
- **High**: Multiple failed logins from same IP
- **Critical**: Privilege escalation detected

## Usage

1. Import `template.json` into Microsoft Sentinel
2. Ensure Azure AD/Entra ID connector is enabled
3. Adjust time range for your investigation needs
4. Use filters to investigate specific users or risk types
5. Set alerts on critical threshold violations

## Customization Tips

- Adjust MFA enforcement policies based on your organization
- Add IP reputation lookups for risky sign-ins
- Integrate with Conditional Access policies
- Add country/region-based filters for compliance
