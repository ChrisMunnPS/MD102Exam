# MD-102 cheat sheet 2/5 — Microsoft Intune

*One page. Facts snapshot 2026-11; verify current behaviour on Microsoft Learn before the exam.*

## Service map

| Area | What lives there |
|---|---|
| Devices | Enrolment, compliance, configuration, scripts, remote actions |
| Apps | App types, app protection, app configuration, install status |
| Endpoint security | Antivirus, firewall, ASR, EDR, disk encryption, baselines, LAPS |
| Reports | Compliance, configuration, apps, updates, encryption, Endpoint analytics |
| Tenant administration | Roles, scope tags, connectors, filters, service health |

## Policy types

| Type | Purpose | Example |
|---|---|---|
| Configuration profile | Deliver settings to devices or users | Wi-Fi, VPN, restrictions, settings catalog |
| Compliance policy | Evaluate and report state | BitLocker required, minimum OS |
| Endpoint security | Security workload policies | Antivirus, firewall, ASR, BitLocker |
| App protection | Protect app data without enrolment | PIN, block copy, selective wipe |
| App configuration | Deliver settings to an app | Server URL, account name |
| Scripts and remediations | Run PowerShell on devices | Detect and fix a registry value |
| Update ring | Control Windows updates | Deferral, deadline, active hours |

## Configuration profile flavours

| Profile | Use when |
|---|---|
| Settings catalog | Granular, searchable settings; the default modern choice |
| Templates | Wi-Fi, VPN, email, kiosk, device restrictions |
| Administrative templates | The setting is an ADMX policy that already exists in Group Policy |
| Custom (OMA-URI) | No catalog or ADMX entry; you supply the CSP path, type, and value |
| Security baseline | Microsoft-recommended security defaults you can customise |

- A setting configured twice with different values reports a conflict; the device applies whichever arrives last.
- Group Policy analytics imports a GPO XML export and reports which settings have Intune equivalents, partial support, or none.

## Assignments and filters

| Control | Applies to | Notes |
|---|---|---|
| Required | Users or devices | Installs automatically; can block in ESP |
| Available | Users | Self-service from Company Portal |
| Uninstall | Users or devices | Removes a required app |
| Include group | Users or devices | The audience that receives the policy |
| Exclude group | Users or devices | Wins over include |
| Assignment filter | Device or user properties | Narrows a group without new groups |
| App intent | Users or devices | Different intents can target different groups |

- Filter properties include device name, manufacturer, model, OS version, ownership, enrolment profile name, and user attributes.
- Effective assignment = include minus exclude, then the filter is evaluated on the device or user.

## Groups and RBAC

| Object | Purpose |
|---|---|
| Assigned group | Static membership, manually maintained |
| Dynamic user group | Rule on user attributes such as department |
| Dynamic device group | Rule on device properties such as OS, model, or ownership |
| Intune role | Set of permissions, built-in or custom |
| Role assignment | Role plus members plus scope groups plus scope tags |
| Scope tag | Labels objects so an admin sees only their slice |

- Scope tags filter objects; scope groups bound which users and devices an admin can act on. Both belong to the role assignment.
- Built-in roles include Help Desk Operator, Policy and Profile Manager, Application Manager, Endpoint Security Manager, Read Only Operator, and Intune Role Administrator.
- Administrative units in Entra ID scope directory objects; they are not a substitute for Intune scope tags.

## Co-management and tenant attach

| Workload | Can move to Intune | Stays in ConfigMgr |
|---|---|---|
| Compliance policies | Yes | — |
| Device configuration | Yes | — |
| Windows Update policies | Yes | — |
| Endpoint protection | Yes | — |
| Resource access policies | Yes | — |
| Client apps | Yes | — |
| Office Click-to-Run apps | Yes | — |

- Co-management needs ConfigMgr, cloud attach, and a pilot collection; switch workloads one at a time.
- Tenant attach shows ConfigMgr devices in Intune without enrolling them and enables some Intune actions.
- Co-management authority can be ConfigMgr or Intune; Intune authority is required for some cloud features.

## Intune Suite

| Component | Solves |
|---|---|
| Remote Help | Attended support with screen share, control, and elevation |
| Endpoint Privilege Management | Just-in-time elevation for specific apps |
| Microsoft Tunnel for MAM | Per-app VPN for unenrolled devices |
| Cloud PKI | Hosted certificate authority for Wi-Fi and VPN |
| Advanced Analytics | Longer retention and custom queries |
| Enterprise App Management | Curated app catalogue and update service |

- Suite features are per-user add-on licences; they are not included with Windows Pro.
- Remote Help capabilities follow RBAC, so elevation must be granted deliberately.

## Health and hygiene

- Device check-in is roughly every 8 hours; Sync forces an immediate check.
- Tenant status shows connector health; service health shows active incidents.
- Audit logs record admin actions with actor and time; stream them with diagnostic settings for retention.
- Device cleanup rules retire devices that have not checked in for a set period.
- Diagnostic settings send logs to Log Analytics, Event Hubs, or a storage account.
