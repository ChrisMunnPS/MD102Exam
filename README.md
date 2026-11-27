<div align="center">

# 🖥️ MD-102 Exam Simulator

### Microsoft Endpoint Administrator · 251 questions · 3 case studies · runs entirely in the browser

[![Live site](https://img.shields.io/badge/%E2%96%B6%20Take%20the%20exam-chrismunnps.github.io-0e7490?style=for-the-badge)](https://chrismunnps.github.io/exam-sim/md-102/)
[![Questions](https://img.shields.io/badge/questions-251-2563eb?style=for-the-badge)](#-question-bank)
[![Pass mark](https://img.shields.io/badge/pass%20mark-700%20%2F%201000-7c3aed?style=for-the-badge)](#-scoring-and-review)
[![No account](https://img.shields.io/badge/signup-not%20required-16a34a?style=for-the-badge)](#-privacy)

**▶ Live exam: https://chrismunnps.github.io/exam-sim/md-102/**

</div>

---

## 🚀 Executive summary

A free, full-length practice exam for **Exam MD-102: Endpoint Administrator**, built from the Microsoft Learn MD-102 learning paths. It recreates the real sitting closely enough to be useful: a weighted 50-question draw, a 100-minute clock, scaled scoring against the 700 pass mark, three multi-question case studies, and eight architecture diagrams used by twenty-five items.

The bank is **251 questions** split across the four skills-measured domains: deploying the Windows client, managing identity and compliance, managing and protecting devices, and managing applications and resources. It deliberately over-covers the pairs candidates mix up — registered versus joined versus hybrid joined, compliance versus configuration, wipe versus retire versus Fresh Start, MDM versus MAM, SCEP versus PKCS, scope tags versus RBAC.

Everything runs client-side. There is no account, no install, no server, no analytics, and no network call after the page loads — scores and review history stay in the visitor's own browser.

The same seven files power both the repository and the live site, so what you test locally is exactly what is published:

> **🌐 Live site: https://chrismunnps.github.io/exam-sim/md-102/**
> Served by GitHub Pages from the portfolio repo's `exam-sim/md-102/` folder — the same seven runtime files in this repository are the deployed build.

It is an independent study tool. It is not affiliated with, endorsed by, or connected to Microsoft.

---

## ✨ Why this one is different

🧭 **It behaves like the real exam.** Fifty questions drawn by domain weight (13 / 12 / 17 / 8), 120 seconds each, a running clock, flag-for-review, a question palette, and submit-on-timeout. No practice-mode shortcuts unless you ask for them.

🧠 **Explanations teach, not just score.** Every item carries a rationale, a note on why each distractor fails, an exam tip, and the Microsoft Learn module and unit it came from.

🧩 **Three case studies.** Twenty-one questions hang off shared scenarios — Contoso's Autopilot and hybrid-identity modernisation, Fabrikam's no-enrolment BYOD programme, and Tailwind Retail's shared-device security hardening — so you practise holding context across a case, the way the real exam does.

🖼️ **Architecture you can actually see.** Eight inline SVG diagrams cover the Autopilot flow, Conditional Access evaluation, Intune policy processing, the device lifecycle, BYOD MAM and MDM paths, Windows update rings, the remote-actions matrix, and compliance evaluation. Every diagram item also restates the figure in prose, so it survives a broken image or a screen reader.

✅ **Multi-answer items are all-or-nothing.** Twenty-eight "select two/three" questions are graded exactly as strictly as the exam grades them.

🎯 **Eight ways to drill.** Full 50, one drill per domain, four cross-domain focus drills (Intune, security, device management, troubleshooting), Quick 10, and a seven-question drill for each case.

🔁 **A spaced-review queue.** Wrong answers come back on a schedule instead of disappearing, so weak areas get revisited without re-running whole exams.

🌓 **Light and dark themes.** A top-bar switch, remembered per browser, following the OS until you choose. Printing always forces black-on-white.

⌨️ **Keyboard-first.** `A`–`D` to answer, arrows to navigate, `F` to flag, plus a visible focus ring and a skip link.

📴 **Genuinely offline.** Double-click the page and it works with the network unplugged. No bundler, no local server, no runtime dependencies.

---

## 🎯 Exam at a glance

| | |
|---|---|
| **Certification** | Microsoft 365 Certified: Endpoint Administrator Associate |
| **Exam** | MD-102 — Endpoint Administrator |
| **Questions in bank** | 251 (230 standalone + 21 case-study) |
| **Default attempt** | 50 questions, weighted by domain |
| **Time limit** | 120 seconds per question — 100 minutes for the default draw |
| **Passing score** | 700 / 1,000 (scaled from percentage correct) |
| **Review** | Every question after submission, with explanations and sources |
| **Prerequisites** | A browser. That is the whole list. |

---

## 📚 Question bank

| Domain | Bank | Standalone | Case items | Weight | 50-question draw | IDs |
|---|---:|---:|---:|---|---:|---|
| Deploy Windows client | 67 | 60 | 7 | 25–30% | 13 | Q1–Q60, Q231–Q237 |
| Manage identity and compliance | 62 | 55 | 7 | 25–30% | 12 | Q61–Q115, Q238–Q244 |
| Manage, maintain, and protect devices | 82 | 75 | 7 | 35–40% | 17 | Q116–Q190, Q245–Q251 |
| Manage applications and resources | 40 | 40 | 0 | 15–20% | 8 | Q191–Q230 |
| **Total** | **251** | **230** | **21** | | **50** | |

The official ranges overlap and sum to 120%, so the kit uses the midpoints normalised to 100. The draw is deterministic per domain, so every full attempt contains 13 / 12 / 17 / 8 questions and no domain can be starved by chance. Case-study items are counted inside their primary domain.

**Question mix:** 45 easy (17.9%) · 128 medium (51.0%) · 78 hard (31.1%) · 28 multi-answer (11.2%) · 25 diagram-based (10.0%) · 28 troubleshooting-tagged.

### 🗂️ Case studies

| Case | Questions | Scenario |
|---|---|---|
| Contoso Global Device Modernisation | Q231–Q237 | 4,000 domain-joined Windows devices moving to Autopilot, hybrid identity for Kerberos and ERP, Cloud PCs for contractors, staged rollout |
| Fabrikam BYOD Initiative | Q238–Q244 | Personal phones with no enrolment, app protection, Conditional Access app-protection grant, selective wipe on departure |
| Tailwind Retail Security Hardening | Q245–Q251 | Shared POS kiosks, removing standing admin rights, BitLocker escrow, 14-day update deadline, lost-laptop response |

---

## 📄 Cheat sheets

Five one-page A4 sheets, written from the same course snapshot as the bank:

| Sheet | Covers |
|---|---|
| `04-CHEAT-SHEET-DEPLOY.md` | Join types, enrolment methods, Autopilot modes, Windows 365, AVD, upgrade and activation |
| `05-CHEAT-SHEET-INTUNE.md` | Service map, policy types, profile flavours, assignments, groups, RBAC, co-management, Intune Suite |
| `06-CHEAT-SHEET-SECURITY.md` | Compliance versus configuration, compliance actions, Conditional Access, Defender, BitLocker, LAPS |
| `07-CHEAT-SHEET-APPS.md` | App types, Win32 mechanics, MAM versus MDM, Microsoft 365 Apps, update rings, Autopatch, Hotpatch |
| `08-CHEAT-SHEET-TROUBLESHOOTING.md` | Logs, error codes, remote actions, wipe/retire decisions, reports, rapid-fire confusion pairs |

`09-CHEAT-SHEETS.html` bundles all five into a print pack — open it, press **Print all five sheets**, and each sheet lands on its own page with no reflow.

---

## 🖥️ Run it locally

**The short version:** download the repository and double-click `index.html`.

```text
index.html        – page shell, theme bootstrap
exam.config.js    – pass mark, domains, weights, timer, focus drills
questions.js      – 251 compiled questions (the whole bank)
diagrams.js       – 8 inline SVG diagrams
app.js            – exam engine
styles.css        – shared theme, light + dark
md-loader.js      – data bootstrap and zero-setup fallback
```

No `npm install`. No build step. No web server. The page opens from `file://`, reads the compiled bank through a plain `<script>` tag, and starts.

> 💡 **Why not Markdown at runtime?** A double-clicked page is not allowed to `fetch` other local files — that rule applies to every `file://` URL. Compiling the Markdown into `questions.js` once is what makes the offline copy work with no setup prompt.

If you only want to check the bank without opening the UI, run `node tools\build-questions.mjs --check` from the authoring kit (not included in this repository).

---

## 🧮 Scoring and review

📊 **Scaled score.** `round(correct / total * 1000)` — the same shape Microsoft uses in the score report. Thirty-five out of fifty is a pass.

🎆 **Passing feels like passing.** Clearing 700 adds a five-second fireworks overlay to the score report. It is skipped automatically when the operating system asks for reduced motion, and never appears in print.

🔍 **Review everything.** After submitting, filter by all / incorrect / flagged / unanswered. Each item shows your answer, the correct answer, the full explanation, the distractor notes, the exam tip, and the source module.

📈 **Section breakdown.** The score report charts all four domains, marks the 700 line on each bar, and links straight into the filtered review for that section.

📄 **Print or save.** "Print full review" and "Print score report" produce clean paper layouts with the light palette forced, so a dark-mode session still prints readable black text.

💾 **Resume safe.** An in-progress attempt is saved on every change. Close the tab, come back, and the clock and answers are where you left them.

---

## 🔐 Privacy

Everything is local. The simulator writes four keys to `localStorage` and nothing else:

| Key | Holds |
|---|---|
| `md102-sim:attempt` | The in-progress attempt, for resume |
| `md102-sim:settings` | Draw size, timer, instant-feedback preference |
| `md102-sim:srs` | Spaced-review scheduling data |
| `md102-sim:theme` | Light or dark choice |

No cookies, no requests to third parties, no telemetry. Clearing site data for the page resets the simulator completely.

---

## ♿ Accessibility

- Full keyboard operation, including `A`–`D` answer keys and arrow navigation.
- Semantic landmarks, a skip link, and a polite live region for toasts.
- Visible focus rings and readable contrast in both themes.
- `prefers-reduced-motion` disables the fireworks and shortens transitions.
- Diagrams are hidden from assistive technology; every diagram question restates the figure in prose.

---

## ⚠️ Disclaimer

Unofficial study material built from publicly available Microsoft Learn content. Not affiliated with or endorsed by Microsoft. Exam objectives and product behaviour change; verify the current skills measured on Microsoft Learn before sitting the exam. Facts snapshot: **November 2026**.

<div align="center">

**[▶ Start practising](https://chrismunnps.github.io/exam-sim/md-102/)** · [Microsoft Learn MD-102](https://learn.microsoft.com/en-us/credentials/certifications/endpoint-administrator/)

</div>
