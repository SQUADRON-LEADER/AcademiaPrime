Edge Add-ons Submission Notes for AcademiaPrime
=============================================

Single purpose description
--------------------------
Automates common workflows on the SRM IST Academia student portal (https://academia.srmist.edu.in) to make it faster and easier for students to view grades, attendance, and course info. The extension only targets that site and provides UI in a popup to run the automation.

Permission justifications
------------------------
- `storage`: Used to save user preferences (UI settings, last-used options). No personal data is stored by default. If the user opts in to store credentials, they are stored only in extension storage (optional and clearly disclosed).
- `activeTab`: Used when the user clicks the extension action to operate on the page currently open in their browser; allows running a single interaction without broad host-level access.
- `scripting`: Used to inject and execute the extension's own JavaScript (bundled in the package) into pages on the allowed host so the automation can run. Injection is performed only for the declared host match pattern below.

Host permission justification
---------------------------
Host pattern: `https://academia.srmist.edu.in/*`

Reason: The extension's functionality is specific to the SRM IST Academia web application. Content scripts and injected helpers must run on pages within this origin to read DOM elements and perform the automation tasks. No other hosts are requested.

Remote code
-----------
- Are you using remote code (JS or Wasm)?: No

Justification: All JavaScript and Wasm used by the extension is packaged in the extension. The only external resources referenced are non-executable assets (Google Fonts for UI typography and links/images hosted on GitHub). There are no `<script src="https://...">` tags loading remote JS, no dynamic `eval()` usage, and no remote module imports of executable code.

Data usage (public disclosure text for store listing)
---------------------------------------------------
What user data do you plan to collect from users now or in the future?

- The extension does not collect analytics or personally-identifiable information by default.
- It reads the currently-open page's DOM on the allowed host to extract academic information requested by the user (grades, attendance, course names) solely to present that information in the extension popup or to automate navigation. That data is processed locally in the browser and is not transmitted to any external server.
- Optional local storage: If the user opts in, the extension may store non-sensitive preferences (display settings) or session identifiers required to simplify repeated automation. Credentials are not collected by default; if the user chooses to save credentials locally this will be clearly presented in the UI and stored only in extension `storage` (not transmitted).

Privacy policy URL
------------------
The extension's privacy policy is available at: https://github.com/SQUADRON-LEADER/AcademiaPrime/blob/main/privacy-policy.html

Certification statements (for the Microsoft form)
-------------------------------------------------
I certify that:
1. The extension has a single, narrow purpose as described above.
2. The permissions requested are necessary and narrowly scoped to that purpose.
3. The extension does not load or execute remote JavaScript/Wasm; all code is bundled inside the package.

Notes for the reviewer / Developer actions
----------------------------------------
- The manifest `permissions`, `host_permissions`, and `content_scripts` already limit runtime to `https://academia.srmist.edu.in/*`. See [manifest.json](manifest.json).
- Non-executable external resources: fonts referenced in `src/popup/popup.html` and `src/content/content.js` use Google Fonts; if you prefer zero external network requests during review, replace local fonts or vendor-font files and update the markup.
- If you want, I can update `manifest.json` to remove `activeTab` and use only host permissions, or vice versa depending on how the extension UI operates — tell me which behaviour you prefer and I'll apply the change.

Prepared by: Developer (repository: SQUADRON-LEADER/AcademiaPrime)
Date: 2026-05-21
