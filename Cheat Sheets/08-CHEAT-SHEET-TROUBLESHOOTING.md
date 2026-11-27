# MD-102 cheat sheet 5/5 — Troubleshooting and administration

*One page. Facts snapshot 2026-11; verify current behaviour on Microsoft Learn before the exam.*

## Where to look first

| Symptom | First stop |
|---|---|
| Policy not applying | Assignment, exclusion, filter, then device sync |
| Setting shows conflict | Two profiles set the same value |
| App not installing | App install report, then IME logs |
| Update failing | Update compliance report, then Windows Update logs |
| Compliance stale | Device check-in, then manual sync |
| Many users affected | Service health and tenant status |

## Logs and tools

| Tool or log | Contains |
|---|---|
| IntuneManagementExtension.log | Win32 apps, PowerShell scripts, remediations |
| AppWorkload.log | App download, install, and detection detail |
| DeviceManagement-Enterprise-Diagnostics-Provider | MDM policy and CSP events |
| dsregcmd /status | Join state, PRT, tenant details |
| Collect diagnostics | Silent bundle of registry, logs, and system info |
| Company Portal logs | User-side enrolment and app issues |
| Autopilot diagnostics | Profile, ESP, and deployment detail |
| Audit logs | Admin actions with actor and time |

- Order of work: assignment, filter, sync, status report, device logs, escalation.
- Sync is the least invasive action and the right first step for delivery lag.
- Collect diagnostics avoids interrupting the user.

## Error codes

| Code | Meaning |
|---|---|
| 0 | Success |
| 3010 | Success, soft reboot required |
| 1641 | Success, hard reboot initiated |
| 1618 | Another installation in progress, retry |
| 1603 | Fatal MSI error: rights, prerequisite, or existing version |
| 0x87D1xxxx | Intune policy or app enforcement error |

- A non-zero code is not automatically a failure; check the configured return codes.
- 1603 needs the installer log, not a blind retry.

## Remote actions

| Action | What it preserves | Use when |
|---|---|---|
| Sync | Everything | Force a check-in |
| Restart | Everything | Pending reboot |
| Collect diagnostics | Everything | Need logs without disruption |
| Remote lock | Data, needs PIN | Lost device, possible recovery |
| Reset passcode | Data | Forgotten local credential |
| Retire | Personal data | BYOD leaving the organisation |
| Wipe | Nothing | Reissue, compromise, lost beyond recovery |
| Fresh Start | User files | Rebuild Windows, remove OEM apps |
| Autopilot Reset | Enrolment and Autopilot record | Return to OOBE for reprovisioning |
| Delete record | Device untouched | Stale record only |
| Rotate BitLocker key | Data | Key exposure |

- Wipe versus retire is the most tested pair: reissue equals wipe, personal device equals retire.
- Delete is record-keeping, not security; a joined device can re-enrol and reappear.
- Bulk actions scale lifecycle work and produce a monitorable job.
- Lost device playbook: lock, monitor, then wipe at a decision point.

## Reports

| Report | Answers |
|---|---|
| Compliance | Which devices meet policy |
| Configuration profile status | Success, error, and conflict per device |
| App install status | Installed, failed, and pending per device |
| Windows Update compliance | Missing or failed updates |
| Encryption | BitLocker and escrow state |
| Endpoint analytics | Startup score and performance |
| Autopilot deployment | Provisioning success and failures |
| Defender portal | Incidents, alerts, and device risk |

- Export compliance and audit data through reports or the Graph API for evidence.
- Diagnostic settings stream logs to Log Analytics, Event Hubs, or storage.

## Administration hygiene

- Audit logs answer "who changed what"; device telemetry does not.
- Cleanup rules retire inactive devices; review stale records on a schedule.
- Tenant status shows connector health; service health shows incidents.
- Remote Help is attended support; lifecycle actions are separate.
- Scope tags and RBAC limit what an admin can see and do.

## Rapid-fire confusion pairs

| Pair | One-line difference |
|---|---|
| Registered vs joined vs hybrid | Identity only vs cloud management vs both directories |
| Compliance vs configuration | Evaluates vs configures |
| Wipe vs retire vs Fresh Start | Erase all vs remove company data vs rebuild and keep files |
| MDM vs MAM | Device control vs app data protection |
| SCEP vs PKCS | NDES and a challenge vs a certificate connector to the CA |
| Scope tag vs RBAC | Object label vs permission assignment |
| Supersedence vs dependency | Replace a version vs install a prerequisite |
| Deferral vs deadline | Delay vs enforce |
| Report-only vs enforced | Observe vs apply |
| Autopilot Reset vs Fresh Start | Keep enrolment vs keep user files |
