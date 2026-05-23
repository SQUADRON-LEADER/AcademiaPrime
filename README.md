# 🎓 AcademiaPrime

[![Version](https://img.shields.io/badge/version-1.1.0-0f766e?style=for-the-badge)](manifest.json)
[![License](https://img.shields.io/github/license/SQUADRON-LEADER/AcademiaPrime?style=for-the-badge)](LICENSE)
[![Issues](https://img.shields.io/github/issues/SQUADRON-LEADER/AcademiaPrime?style=for-the-badge)](https://github.com/SQUADRON-LEADER/AcademiaPrime/issues)
[![Pull Requests](https://img.shields.io/github/issues-pr/SQUADRON-LEADER/AcademiaPrime?style=for-the-badge)](https://github.com/SQUADRON-LEADER/AcademiaPrime/pulls)
[![License](https://img.shields.io/badge/license-MIT-green?style=for-the-badge)](LICENSE)
[![Platform](https://img.shields.io/badge/platform-Chrome%20%7C%20Edge-blue?style=for-the-badge)](#installation)

> 🚀 Skip the Feedback. Track the Margin.

AcademiaPrime is a focused browser extension for SRM Academia that removes repetitive portal work and turns the most important academic information into something easier to act on. It is built for students who want a faster way to submit course feedback, inspect attendance margin, estimate marks, review grade outcomes, and read timetable information without bouncing between spreadsheets or manual calculations.

The extension is designed to run inside your existing SRM Academia session. There is no separate login screen, no external data pipeline, and no background analytics. All core logic executes locally in the browser, using the page the student already opened. That makes the experience predictable, fast, and privacy-conscious.

## 🎯 Why It Exists

SRM Academia contains a lot of useful information, but the workflow is scattered across multiple pages and repeated manual steps. AcademiaPrime exists to reduce that friction. Instead of forcing students to re-enter the same feedback choices, calculate attendance margins by hand, or decode timetable slots every time, the extension keeps the important actions close to the portal and removes the repetitive parts.

This is especially useful near deadlines, when time matters and small errors become expensive. A narrow tool that handles the repetitive steps cleanly is more valuable here than a broad dashboard that tries to do everything at once.

## ✨ What It Does

AcademiaPrime is not a general-purpose automation tool. It is intentionally narrow in scope and built around the SRM Academia portal workflow. The current release focuses on four core areas:

1. Feedback automation for the course feedback page.
2. Academic insight overlays for grades, marks, and attendance margin.
3. Timetable enhancement that maps slot codes to course names.
4. Local preference storage so repeated tasks do not need to be reconfigured every time.

The user experience is intentionally minimal. You open the relevant SRM Academia page, use the popup when needed, and let the content scripts enhance the page in place. When the page is not relevant to the current feature, the extension stays out of the way.

## 🌟 Highlights

- ⚡ Faster course feedback submission with a visible progress flow and a manual STOP action.
- 💾 Local storage for a default rating and default comment so repeated feedback runs stay consistent.
- 📊 Attendance margin calculation directly inside the attendance page.
- 🧾 Grade detail enhancements that show estimated grades and marks-related context.
- 🧮 A live CGPA calculator that can be populated from the marks table and updated interactively.
- 🗓️ Timetable enrichment that resolves batch timetable slots into clearer course labels.
- 🎨 A polished popup UI that gives the extension a clean, lightweight control surface.

## Feature Breakdown

### ⚙️ Feedback Automation

The popup lets you choose a course rating and a short comment, then triggers the feedback-filling flow on the SRM Academia feedback page. The extension validates that you are on the correct host and section before it tries to fill anything. During the run, a progress bar and status panel show what is happening, and you can cancel the process if needed.

### 📈 Attendance Margin

On the attendance page, AcademiaPrime calculates how many classes you can miss or still need to attend to stay at the threshold. The margin is displayed directly inside the table so you do not have to calculate it by hand. Positive, zero, and negative states are visually differentiated.

### 🧠 Grade and Marks Helpers

The extension adds richer grade context to the marks and results pages. It can estimate grades, display marks lost, and show the approximate marks required to target a higher outcome. This is meant to reduce guesswork before assessments and make the numbers easier to compare at a glance.

### 🧮 CGPA Calculator

AcademiaPrime includes a live CGPA calculator that can be filled from the page’s subject and marks data. It is designed to be interactive, so you can adjust grade assumptions and see the effect immediately instead of recomputing everything by hand.

### 🗓️ Timetable Enhancement

When you open the timetable page, the extension builds a local course catalog from the page’s course table and uses it to decorate timetable cells with course names and clearer labels. That makes batch timetables easier to scan and reduces the need to decode slot tokens repeatedly.

## 🛠️ Installation

### Chrome or Chromium-based browsers

1. Download or clone this repository.
2. Open your browser’s extensions page.
3. Enable Developer mode.
4. Choose Load unpacked.
5. Select the repository root folder, not a nested subfolder.

### Microsoft Edge

1. Download or clone this repository.
2. Open `edge://extensions`.
3. Enable Developer mode.
4. Choose Load unpacked.
5. Select the repository root folder.

No package installation step is required. The extension is a plain browser extension project with its runtime behavior defined by the manifest and source files in this repository.

## 🧭 Compatibility

AcademiaPrime is built for Chromium-based browsers that support Manifest V3, including Google Chrome and Microsoft Edge. The extension is scoped to the SRM Academia portal at `https://academia.srmist.edu.in/*`, and its content scripts are written around that site’s structure.

If the portal markup changes, some page-specific enhancements may need a small update. That is intentional: the project is optimized for a single academic workflow rather than a generic browser-wide automation layer.

## 📘 How To Use

### ✍️ Feedback Page

1. Open the SRM Academia feedback page.
2. Click the extension icon.
3. Select a rating and set a comment if you want something different from the saved default.
4. Click Autofill.
5. Watch the progress bar until the form is completed.
6. Use Stop if you need to cancel the automation mid-run.

### 🪪 Attendance Page

Open the attendance page and let the content script enhance the table. The margin column is added automatically, so the key attendance numbers are visible without manual calculations.

### 📚 Grades and Marks Pages

Open the relevant results or marks page inside SRM Academia. AcademiaPrime enhances the tables with grade context, marks-loss information, and CGPA calculation helpers where the portal data is available.

### 🗓️ Timetable Page

Visit the timetable page and let the extension resolve slot codes into course titles. It stores a local catalog in browser storage so the timetable remains easier to read across sessions.

## ⚙️ Configuration

The popup stores the last selected feedback rating and comment in browser storage so the next run can reuse them. On install, the extension starts with an `Excellent` rating and a `Good` comment as the default values.

If you want a different baseline, simply change the values in the popup once and the extension will remember them locally for future runs.

## 🔒 Privacy And Permissions

AcademiaPrime is built to stay narrow and local.

- `storage` is used to remember user preferences such as the saved rating and comment.
- `activeTab` and `scripting` are used so the extension can run its own scripts on the page the user already opened.
- Host access is limited to `https://academia.srmist.edu.in/*`.
- The extension does not rely on remote JavaScript, does not use analytics, and does not send portal data to external servers.

The privacy policy is included in the repository and published here: [Privacy Policy](privacy-policy.html).

## 🧱 Project Structure

```text
.
├── manifest.json
├── privacy-policy.html
├── src/
│   ├── background.js
│   ├── content/
│   │   ├── content.js
│   │   └── main.js
│   ├── injected/
│   │   └── automator.js
│   └── popup/
│       ├── popup.html
│       ├── popup.css
│       └── popup.js
└── icons/
```

## 🧰 Development Notes

The architecture is split into three layers:

- `src/popup/` contains the popup UI and its interaction logic.
- `src/content/` contains the content scripts that run on the SRM Academia pages.
- `src/injected/` contains page-world helpers used when the extension needs direct access to the portal’s page context.
- `src/background.js` acts as the service worker that coordinates messaging and injection.

If you are changing behavior, update the popup and content logic together so the UI and the page behavior stay aligned. If you are changing permissions or host access, update the manifest and the documentation together so the store-facing story remains accurate.

## ✅ Verification Checklist

Before shipping an update, it is worth checking the following on a live SRM Academia session:

- The popup opens and stores the selected feedback defaults.
- Autofill only activates on the correct feedback page.
- The STOP button cancels a fill in progress.
- The attendance margin column appears on the attendance page.
- The timetable page resolves slots into readable course names.

## 📝 Certification Notes

This extension is intended for SRM Academia users only. Its scope is intentionally narrow, and the code in this repository is designed to run locally in the browser on the declared host. It does not request unrelated site access and does not depend on remotely loaded executable code.

## 🙌 Credits

Created by Aayush Kumar.

## 📄 License

This project is licensed under the MIT License. You are free to use, modify, and distribute this software under the terms of the MIT License.

See [LICENSE](LICENSE) for the full license text.

## 🛟 Troubleshooting

If something does not work as expected, start with the page and host:

- Make sure you are on the SRM Academia portal and not a mirrored or cached page.
- Reload the page after installing or updating the extension so the content scripts can attach cleanly.
- If Autofill looks inactive, check that you are on the course feedback page before opening the popup.
- If the timetable or attendance enhancements are missing, refresh the page and give the extension a moment to rebuild its local state.

Most issues come from being on the wrong page, using an outdated tab, or loading the extension before refreshing the portal session.

## ❓ FAQ

**Does AcademiaPrime require a separate login?**
No. It works inside your existing SRM Academia session.

**Does it send data to a server?**
No. The extension processes its logic locally in the browser.

**Can I change the feedback defaults?**
Yes. Update them in the popup and the extension will remember them for later use.
