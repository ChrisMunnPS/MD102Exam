# MD-102 cheat sheet 1/5 — Windows deployment

*One page. Facts snapshot 2026-11; verify current behaviour on Microsoft Learn before the exam.*

## Join types: the decision that changes everything

| Join type | What it gives you | Pick it when |
|---|---|---|
| Entra registered | Device identity for SSO and Conditional Access; no MDM | Personal BYOD; app protection only; no device control needed |
| Entra joined | Cloud device identity plus Intune MDM | Corporate device with no on-premises dependency |
| Entra hybrid joined | AD domain membership plus Entra identity and Intune | Kerberos, on-premises shares, legacy apps, or Group Policy still needed |

- Check a device with `dsregcmd /status`: `AzureAdJoined`, `DomainJoined`, `EnterpriseJoined`.
- Registered is identity only; joined is identity plus management; hybrid is both directories.
- Hybrid join needs Entra Connect sync, a service connection point (SCP), and line of sight to a domain controller at join time.

## Enrolment methods

| Method | Best for | Watch out |
|---|---|---|
| Automatic enrolment (MDM user scope) | Entra joined devices at first sign-in | Needs licences and MDM scope set to All or a group |
| Windows Autopilot | New corporate hardware, zero touch | The hardware hash must be registered first |
| Bulk enrolment (provisioning package) | Existing devices with no hash | The package carries a short-lived enrolment token |
| GPO automatic enrolment | Hybrid joined domain devices | Needs the GPO and a domain-joined device |
| Co-management | ConfigMgr estates moving to Intune | Workloads move one at a time |
| Manual (Access work or school) | One-off or lab devices | Not a scale strategy |

- Enrolment restrictions: platform, minimum and maximum OS version, personally owned device block, and a per-user device limit (default 15).
- Corporate identifiers and device categories support ownership reporting; they do not enrol anything.

## Autopilot profiles

| Mode | User at OOBE | Joins | Typical use |
|---|---|---|---|
| User-driven | Yes, signs in | Entra joined or hybrid | Standard knowledge-worker laptop |
| Pre-provisioning (white glove) | Technician first, user later | Entra joined or hybrid | IT prepares the device before shipping |
| Self-deploying | No user | Entra joined only | Kiosk, signage, shared device |
| Device preparation | Yes | Entra joined only | Simpler, newer user-driven flow |

- Every mode needs: registered hash, device in an assigned group, a profile, network, and an Intune licence.
- Self-deploying needs TPM 2.0 and cannot use hybrid join. Pre-provisioning needs TPM 2.0 and wired or wireless network.
- ESP stages: device preparation, device setup, account setup. Track required apps and block until installed.
- Autopilot Reset removes user data and apps, keeps Autopilot registration and Intune enrolment, and returns to OOBE.
- Troubleshoot: normal OOBE with no Autopilot screen means the hash or profile assignment is missing, not a profile setting.

## Windows 365 and Azure Virtual Desktop

| Option | What it is | Key limits |
|---|---|---|
| Windows 365 Business | Cloud PC on a Microsoft-hosted network | No Azure network connection, no hybrid join, small-tenant ceiling |
| Windows 365 Enterprise | Cloud PC with provisioning policies | Supports ANC, hybrid join, custom images |
| Windows 365 Frontline | Shared Cloud PCs for shift workers | One licence covers several users, not concurrent sessions |
| Windows 365 Boot | Device boots straight into the Cloud PC | Windows 11 endpoint, Entra joined |
| Azure Virtual Desktop | Your own host pools in Azure | You manage images, hosts, scaling, and FSLogix |

- A Windows 365 Enterprise provisioning policy = image, network, region, join type, and assignment.
- An ANC needs a virtual network, a subnet, and either domain join credentials or Entra join.
- AVD objects: host pool (pooled or personal), application group, workspace, session hosts, scaling plan.
- Multi-session Windows 11 Enterprise lets several users share a host; FSLogix containers roam profiles.

## Upgrade and activation

- Windows subscription activation: a Microsoft 365 E3/E5 licence steps Windows Pro up to Enterprise with no product key.
- In-place upgrade keeps apps and files; use a feature update policy, or a task sequence when the upgrade needs custom steps.
- Feature update policy targets a Windows version with a rollout date and a deadline.
- Readiness: Endpoint analytics reports app and driver blockers before a Windows 11 rollout.
- Provisioning packages (Windows Configuration Designer) can join, enrol, and apply a small set of settings; they are not a replacement for Autopilot profiles.

## Deployment decision map

| Requirement in the stem | Answer to reach for |
|---|---|
| Zero touch, new hardware, cloud only | Autopilot user-driven, Entra joined |
| Zero touch but Kerberos needed | Autopilot hybrid joined |
| No user at OOBE | Autopilot self-deploying |
| IT prepares before shipping | Autopilot pre-provisioning |
| Contractor desktop, no hardware | Windows 365 Enterprise or AVD |
| On-premises access from a Cloud PC | ANC with hybrid join |
| Existing device with no hash | Provisioning package or GPO enrolment |
| Fixed feature set for years | Windows LTSC |
