# sentinel-workbooks

Custom Azure Monitor Workbooks for Microsoft Sentinel, designed for SOC visibility and threat hunting.

## Objectives

- Provide opinionated SOC dashboards for enterprise environments.
- Accelerate deployment of consistent visualizations across tenants.
- Demonstrate workbook design patterns for security operations teams.

## Workbook categories

- `soc-overview` – Executive and on-call overview (incidents, alerts, health).
- `identity-security` – Risky sign-ins, MFA failures, privilege escalation.
- `cloud-security` – Azure resource changes, policy violations, network insights.
- `threat-hunting` – Hunting pivots across entities and data sources.

## Structure

Each workbook folder should contain:

- `template.json` – exported workbook template.
- `README.md` – screenshot, parameters, and usage guidance.

## Usage

1. In Microsoft Sentinel, go to **Workbooks** → **New**.
2. Switch to the advanced editor and paste the JSON from `template.json`.
3. Adjust resource group, subscription, and workspace parameters.
4. Save and pin to Azure dashboards or Sentinel workbooks as needed.
