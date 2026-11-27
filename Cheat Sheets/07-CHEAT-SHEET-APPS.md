# MD-102 cheat sheet 4/5 — Applications and updates

*One page. Facts snapshot 2026-11; verify current behaviour on Microsoft Learn before the exam.*

## App types

| Type | Use for | Detection |
|---|---|---|
| Windows app (Win32) | EXE or MSI with custom logic | File, registry, MSI product code, script |
| Line-of-business (MSI) | Simple MSI or MSIX | Product code or file |
| Microsoft Store app | Packaged Store apps | Store identity |
| Microsoft 365 Apps | Office | Built in |
| Web link | URL shortcut | None |
| Managed Google Play | Android Enterprise apps | Play approval |

- Win32 content is wrapped with IntuneWinAppUtil.exe into an .intunewin file.
- Win32 needs install and uninstall commands, a detection rule, and optionally requirement rules.
- Store apps update themselves; Win32 apps need a new version or supersedence.

## Win32 mechanics

| Element | Purpose |
|---|---|
| Install command | Runs the installer, for example msiexec /i app.msi /qn |
| Uninstall command | Removes the app |
| Detection rule | Proves the app is already installed |
| Requirement rule | Gates whether the app is offered |
| Install context | System for HKLM and no-user installs, user for per-user |
| Return code | 0 success, 3010 soft reboot, 1641 hard reboot, 1618 retry, 1603 fatal |

- Detection is "is it there?"; requirement is "should it be there?".
- Supersedence replaces an older version and can uninstall it; a dependency installs a prerequisite first.
- ESP can block the desktop until required apps install; only required apps can be tracked.
- Win32 logs: IntuneManagementExtension.log and AppWorkload.log on the device.

## Assignments

| Intent | Behaviour |
|---|---|
| Required | Installs automatically |
| Available | User installs from Company Portal |
| Uninstall | Removes a required app |
| Include and exclude | Exclude wins |
| Filter | Narrows by device or user property |

- To retire an app but keep its history, change the intent to uninstall; delete the object only when reporting is no longer needed.
- Self-service failures are usually targeting or requirement rules.

## Microsoft 365 Apps

| Channel | Feature update cadence |
|---|---|
| Current Channel | Monthly, fastest |
| Monthly Enterprise Channel | Monthly on a predictable schedule |
| Semi-Annual Enterprise Channel | Roughly twice a year |
| Semi-Annual Extended | Extended support for specific builds |

- Use the Microsoft 365 Apps app type, choose architecture and apps, and apply an XML configuration if needed.
- Click-to-Run supports channels and streaming; MSI Office is legacy.
- Office settings can also come from cloud policy.

## MAM versus MDM

| Capability | MAM (app protection) | MDM (enrolment) |
|---|---|---|
| Device enrolment | Not required | Required |
| Protects | Data inside managed apps | Whole-device configuration |
| Wipe | Selective, app data only | Full device wipe |
| Compliance signal | No | Yes |
| Conditional Access grant | App protection | Compliant or hybrid joined |
| Target | Users | Users or devices |

- App protection areas: data protection and access requirements (conditional launch). App configuration is a separate policy.
- Conditional launch handles PIN, jailbreak or root, minimum OS, and threat level.
- Multi-identity lets personal and work accounts coexist with protection on work only.
- Multiple app protection policies combine restrictively, like compliance.
- Selective wipe removes corporate data on BYOD; a full wipe is never the BYOD answer.

## Update types

| Type | What it contains |
|---|---|
| Quality update | Monthly security and reliability fixes |
| Feature update | New Windows version |
| Driver update | Hardware driver fixes, targetable by model |
| Definition update | Defender security intelligence |

## Update rings

| Setting | Effect |
|---|---|
| Deferral | Delays updates by a number of days |
| Deadline | Forces installation by a date |
| Grace period | Postponement allowed before the deadline |
| Active hours | Prevents restarts during working time |
| Pause | Temporarily stops updates |
| Delivery Optimization | Peer caching to save WAN bandwidth |

- One device, one update ring; two rings with different values create a conflict.
- Feature update policies target a version with a rollout date and a deadline.
- Quality deferral delays patches; feature deferral delays versions; active hours only move the restart.
- The Windows Update compliance report shows devices missing updates.

## Servicing and automation

| Option | Use when |
|---|---|
| General Availability Channel | Stay current with annual feature updates |
| LTSC | Fixed feature set for years, appliances and certified apps |
| Windows Autopatch | Microsoft manages rings; needs E3/E5 |
| Hotpatch | No-restart monthly updates on Windows 11 Enterprise 24H2+ with VBS |
| WSUS | On-premises update infrastructure, not cloud-managed |
| WUfB | Cloud-managed updates through Intune |

- Autopatch rings run test, first, fast, broad; the test ring receives updates first.
- Hotpatch still needs a quarterly baseline restart.
- Bandwidth complaints point to Delivery Optimization; timing complaints point to rings.
