# MD-102 cheat sheet 3/5 — Device compliance and security

*One page. Facts snapshot 2026-11; verify current behaviour on Microsoft Learn before the exam.*

## Compliance versus configuration

| Question | Compliance policy | Configuration profile |
|---|---|---|
| What does it do? | Evaluates and reports state | Delivers and enforces settings |
| Typical settings | BitLocker on, minimum OS, Defender on | BitLocker cipher, update ring, firewall rule |
| Result | Compliant or not compliant | Applied, error, or conflict |
| Feeds Conditional Access | Yes, through the Entra device object | No |
| Multiple policies | Cumulative; the device must meet all | Conflicts when values differ |

- Compliance answers "is it allowed?"; configuration answers "what is set?".
- Devices with no compliance policy follow the tenant setting, which defaults to compliant. Change it to not compliant before enforcing Conditional Access.

## Compliance rules by platform

| Control | Windows | iOS and Android |
|---|---|---|
| Encryption | Require BitLocker | Require encryption |
| Health | Secure Boot, code integrity, TPM | Jailbroken or rooted block |
| Defender | Antivirus, firewall, machine risk score | Device threat level |
| OS level | Minimum and maximum OS version | Minimum and maximum OS version |
| Access | Password and lock screen rules | Password, inactivity, biometrics |
| Platform | Windows 10/11 with Defender integration | Android Enterprise, iOS, platform security |

- Machine risk score needs Defender for Endpoint onboarding; without it the signal is missing.
- Mobile threat defence settings come from a connected MTD connector.

## Compliance actions and timing

| Action | Effect |
|---|---|
| Send email to end users | Guidance before enforcement |
| Mark device noncompliant | Changes state after the schedule; this is the grace period |
| Remote lock | Locks the device immediately |
| Retire | Removes company data and management |

- Actions run on a schedule; a one-day delay on Mark noncompliant is a one-day grace period.
- State reaches Entra ID at check-in, so a recent fix may not show for a while. Sync first.
- Retire is for BYOD departure; wipe is for reissue or compromise.

## Conditional Access

| Building block | Examples |
|---|---|
| Assignments | Users, groups, workload identities, directory roles |
| Conditions | User risk, sign-in risk, device platform, location, client apps, device state |
| Grant | Block, MFA, compliant device, hybrid joined, app protection, approved client app, terms of use, authentication strength |
| Session | Sign-in frequency, persistent browser, app enforced restrictions, continuous access evaluation |

- Grants in one policy combine with AND; use separate policies for OR.
- Report-only evaluates and logs without enforcing; pilot there, then turn on.
- Every design needs a cloud-only break-glass account excluded from all policies and monitored.
- The app protection grant is the BYOD answer; compliant and hybrid joined grants need management.
- Sign-in frequency is the fixed reauthentication interval.
- Intune writes compliance to the Entra device object; Conditional Access reads it at sign-in.

## Defender stack

| Control | What it does |
|---|---|
| Onboarding (EDR policy) | Sends device signals to Defender for Endpoint |
| Antivirus policy | Scan schedule, exclusions, cloud protection, intelligence updates |
| ASR rules | Audit, warn, or block risky behaviours |
| EDR block mode | Blocks malicious behaviour when third-party AV is primary |
| Tamper protection | Stops local changes to Defender settings |
| Live response | Remote shell for investigation and containment |
| Security baseline | Recommended configuration across many controls |

- Pilot ASR in audit, review events, then block; scope an exception to the affected group.
- Defender portal visibility is Defender RBAC plus device groups, not Intune RBAC.
- Plan 2 adds EDR, automated investigation, advanced hunting, and live response.

## BitLocker

- Silent enablement needs a disk encryption policy plus a ready TPM 2.0.
- TPM plus PIN adds a pre-boot secret; TPM-only is transparent to the user.
- Escrow recovery keys to Entra ID or AD before encryption runs.
- Rotate the recovery key after exposure; retrieval needs the narrow Intune permission.
- The Encryption report shows encryption and escrow state across devices.

## LAPS and local privilege

| Control | Scope |
|---|---|
| Windows LAPS | Built-in local administrator password, rotation, Entra or AD backup |
| Legacy LAPS | MSI client-side extension, being retired |
| Local user group membership | Adds or removes members from Administrators and other groups |
| Endpoint Privilege Management | Just-in-time elevation for a specific app |

- LAPS needs a supported Windows build and an existing local admin account named in the policy.
- EPM keeps users standard and elevates the app, not the person.

## Confusion pairs

| Pair | Difference |
|---|---|
| Compliance vs configuration | Evaluates vs sets |
| Baseline vs endpoint security policy | Recommended posture vs operational settings |
| ASR audit vs block | Measure vs prevent |
| BitLocker vs LAPS | Disk key vs local account password |
| Retire vs wipe | Keep personal data vs erase the device |
