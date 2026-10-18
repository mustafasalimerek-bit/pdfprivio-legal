> Build 70 / 2026-10-18 supersedes the analytics/privacy statements in this earlier ad-free change log. The current privacy/support sources disclose optional Firebase Analytics, separate Firebase Installations technical diagnostics and Android ML Kit diagnostics. Apply the current sources and app repo's `docs/release/firebase_analytics_declarations_2026-10-18.md`; do not reapply the historical “no analytics / receives no data / nothing to opt out of” replacements below. No publishing action has occurred.

# PDF Privio legal pages — ad-free rewrite for 1.1.4

Branch `ad-free-2026-10`, cut from `main` @ 4a5c19e. **Not committed, not pushed.**
These pages are the live policy for 1.1.1–1.1.3, which still show ads. Publish them
on the day 1.1.4 goes live.

> ⚠️ Do **not** commit this file to `main`. GitHub Pages (Jekyll, no `.nojekyll`)
> would serve it publicly as `/CHANGES_AD_FREE.html`.

On release day, replace every `2026-10-XX` (4 occurrences: privacy ×2, terms ×2).

Sources used:
- Pre-ads wording: `~/development/pdfprivio` → `git show main:docs/{privacy,terms,support}/index.html`.
- 1.1.4 behaviour, checked in the **uncommitted** `remove-ads` working tree of
  `~/development/pdfprivio` (1.1.4+68):
  - `google_mobile_ads` is gone.
  - `AD_ID` is stripped with `tools:node="remove"`.
  - The AdMob app IDs, `NSUserTrackingUsageDescription` and `SKAdNetworkItems` are removed.
  - `ExportGate` now goes straight to the paywall.
  - `ToolGate` entry-locked tools = `batch`, `receipt`.
  - ML Kit runs only on Android: `OcrService` / `DocumentScannerService` branch on `Platform.isIOS`.
- Kept from the July rewrite because they are not about ads: store-neutral billing and
  refund wording, the `pdfprivio-legal` canonical URLs, "Erek Studio holds no data" wording,
  the narrowed "product analytics" bullet, "no free trial", and the Families-programme
  sentence.

---

## privacy/index.html

### `<meta name="description">`
- OLD: "…your documents never leave your device. Erek Studio operates no servers and receives no data. The free version shows Google AdMob ads, which never receive your documents; Privio Pro removes ads entirely."
- NEW: "…your documents never leave your device. No ads, no tracking, no account. Erek Studio operates no servers and receives no data."

### Meta box
- OLD: "Last updated: 2026-07-28" / "Effective date: 2026-05-18"
- NEW: "Last updated: 2026-10-XX" / "Effective date: 2026-10-XX"
- This version takes effect on release day, so the effective date moves too. The July
  rewrite had left it at 2026-05-18. Put 2026-05-18 back if you prefer the original date.

### TL;DR (paragraphs 2 and 3; paragraph 1 "Your documents never leave your device" unchanged)
- OLD P2: "**The free version of Privio shows ads.** Ads are served by Google AdMob, which collects advertising and device identifiers, approximate (IP-derived) location, and app- and ad-interaction data… Privio Pro removes ads entirely…"
- NEW P2: "**Privio shows no ads and does no tracking.** There is no advertising SDK in the app, no ad-consent form and no App Tracking Transparency prompt, and Privio never accesses your device's advertising identifier (the IDFA on iOS, the Advertising ID on Android). Privio has no analytics of its own and no crash-reporting SDK."
- OLD P3: "Apart from ads, the only outbound activity is what *you* explicitly tap: the system share sheet… or an in-app purchase…"
- NEW P3: "On Android, text recognition (OCR) and the document scanner use Google's ML Kit library, which runs on your device but may send Google its own diagnostic and usage data about the library — never your documents (see section 2.3). Apart from that, the only outbound activity is what *you* explicitly tap: …" (rest unchanged)
- Why the ML Kit sentence: the pre-ads TL;DR said "Privio collects nothing… no server to send anything to". That is not true on Android because of ML Kit, so it was not restored.

### §1 What Privio does not collect
- "Product analytics" bullet:
  - OLD last sentence: "The advertising SDK described in section 2.3 measures ads, not your use of the tools."
  - NEW last sentence: "On Android, the ML Kit usage data described in section 2.3 goes to Google, not to us."
- "Crash reports sent to us" bullet:
  - OLD: "…the diagnostic data the platform and the ad SDK handle."
  - NEW: "…the diagnostic data the platform and, on Android, Google's ML Kit library handle."
- **Added** the "Advertising identifiers" bullet back. The July rewrite had removed it; the new text is adapted from the pre-ads one:
  - NEW: "**Advertising identifiers.** Privio shows no ads and contains no advertising SDK. On iOS it never accesses your IDFA, so it shows no App Tracking Transparency dialog — there is nothing to track. On Android it never reads or uses your Advertising ID."
- Closing paragraph:
  - OLD: "…The advertising described in section 2.3 talks to Google's servers, never to ours, and never carries your documents."
  - NEW: "…On Android, the ML Kit diagnostics described in section 2.3 go to Google's servers, never to ours, and never carry your documents."

### §2 intro (wording fix, not about ads)
- OLD: "Strictly limited to what is unavoidable for the app to function on Apple's platform:"
- NEW: "…on Apple's and Google's platforms:"
- Why: 2.1 and 2.2 already covered Google Play and Android, and the new 2.3 is Android-only.

### §2.3: was "Advertising (free version only)", now "Google ML Kit (Android only)"
- OLD (removed in full):
  - The AdMob + UMP description.
  - The list of data Google collects: identifiers, IP-derived location, ad interactions, SDK diagnostics.
  - "What the ad system never receives".
  - "Your controls": ATT, Android Ads settings, the EEA/UK/CH/US consent form, buying Pro.
  - "Google acts as an independent controller…", including the partner-sites link.
- NEW: "On Android, Privio's text recognition (OCR) and document scanner are powered by **Google ML Kit**, which runs on your device: your pages are processed locally and your documents are never uploaded. ML Kit may, however, send Google its own diagnostic and usage data about the ML Kit library. Erek Studio never receives this data; Google's handling of it is governed by Google's privacy policy: policies.google.com/privacy." + "This section does not apply on iOS, where scanning and text recognition use Apple's own on-device frameworks (VisionKit and Vision)."
- Unchanged: "That is the entire list. There is nothing else."
- The section number was kept, so every "section 2.3" cross-reference still resolves.

### §5 Children's privacy
- OLD: "…Privio is not enrolled in Google Play's Designed for Families programme and is not intended for child-directed use; the advertising described in section 2.3 is therefore not configured for a child audience."
- NEW: "…Privio contains no advertising and does no tracking. It is not enrolled in Google Play's Designed for Families programme and is not intended for child-directed use."

### §6 Your rights
- Delete:
  - OLD: "…There is nothing on our side to delete. For the advertising data held by Google, use Google's own controls, linked in section 2.3."
  - NEW: "…There is nothing on our side to delete. The ML Kit diagnostic data described in section 2.3 (Android only) is held by Google under Google's privacy policy."
- Consent:
  - OLD: "Withdraw consent for advertising. In the EEA, UK, Switzerland and certain US states, reopen the Google consent form… revoke tracking… reset or delete your Advertising ID… Buying Privio Pro stops all ad requests permanently."
  - NEW: "Withdraw consent. **Privio never asks for advertising or tracking consent, because it shows no ads and does no tracking.** Camera and Photos access, if you granted it, can be turned off at any time in your device settings."

### §7 Sale and sharing of data
- Unchanged P1: "Erek Studio does not sell personal information, and never has. We hold none to sell."
- OLD P2+P3: "However, under the California CCPA/CPRA… showing personalised ads can count as "sharing"… for cross-context behavioural advertising… made available to Google… To opt out: …consent form… ATT… Opt out of Ads Personalisation… Buying Privio Pro…"
- NEW: "Privio also does not "share" personal information for cross-context behavioural advertising, as the California CCPA/CPRA and comparable US state laws use that term: the app shows no ads, accesses no advertising identifier, and does no tracking. There is nothing to opt out of."

### §8 International transfers
- OLD: "…The advertising described in section 2.3 is processed by Google on its own global infrastructure, under Google's privacy policy and transfer safeguards…"
- NEW: "…On Android, the ML Kit diagnostic and usage data described in section 2.3 is processed by Google on its own infrastructure, under Google's privacy policy…"

### Changelog
None added: the page has no changelog section. §10 only describes the update process.

## terms/index.html

### Meta box
- OLD: "Last updated: 2026-07-16" / "Effective date: 2026-07-16"
- NEW: "Last updated: 2026-10-XX" / "Effective date: 2026-10-XX"
- The July ad commit changed §4 without updating these dates.

### §4 Free tier and Pro tier
- P1:
  - OLD: "…Every tool opens and runs on your own document for free — releasing the result (save, share, export) is where the free tier asks you to watch a short ad. Two power features (batch processing and the receipt scanner) also ask for an ad, or Pro, from the start…"
  - NEW: "…Every tool opens and runs on your own document for free — Pro is what lets you save, share, or export the result. Two power features (batch processing and the receipt scanner) require Pro from the start…"
  - This is the pre-ads (`main`) wording. The rest of the paragraph is unchanged, including "Privio does not currently offer a free trial."
- P2:
  - OLD: "**The free tier is supported by advertising**, served by Google AdMob: a rewarded ad… or an interstitial… the action is granted anyway… **Privio Pro removes ads entirely**… The advertising system never receives your documents. See our Privacy Policy for the full data statement."
  - NEW: "Privio contains **no advertising of any kind** in any tier. There are no banner ads, interstitial ads, rewarded ads, or sponsored content, and there is no advertising SDK in the app. See our Privacy Policy for the full data statement."

## support/index.html

### FAQ "Does Privio upload my PDFs anywhere?"
- OLD: "…there is no Erek Studio server, no analytics SDK, and no crash-reporting SDK. The free version does show ads (Google AdMob), and the ad system talks to Google — but it never receives your documents… Privio Pro removes ads entirely…"
- NEW: "…there is no Erek Studio server, no account, no analytics of our own, no crash-reporting SDK, and no ads or tracking of any kind. On Android, Google's ML Kit library (used for on-device OCR and the document scanner) may send Google its own diagnostic and usage data about the library — never your documents…"
- "no analytics SDK" became "no analytics of our own". On Android, Google's ML Kit sends usage data to Google, so a flat "no analytics SDK" would overclaim.

### "Legal" list
- OLD: "Privacy Policy — what stays on your device (your documents), and what the ads collect."
- NEW: "Privacy Policy — what stays on your device (your documents); no ads, no tracking, no account."

## Not changed
- `index.html` (landing page): it contains no ad, consent or tracking text. Its free-tier line, "Pro is what lets you save, share, or export the result", already matches 1.1.4.
- `README.md`: it has no ad text.

## Checks
- Tag balance and relative links (`html.parser` script): all 4 pages OK.
- `xmllint --html`: same findings before and after the edits. The only findings are HTML4-parser complaints about HTML5 `header`/`footer`/`section`/`details`/`summary`.

## Final grep
Pattern, case-insensitive, `.git` and this file excluded:
`admob|advertis|\bads?\b|idfa|aaid|\batt\b|app tracking|\bump\b|consent|reklam|personali[sz]|cross-context|tracking|\btrack\b|izleme`

All 10 hits are deliberate "no ads / no tracking" sentences, except `terms:247`, which is the ESIGN "withdraw consent to … sign documents electronically" clause and is not about ads. There are 0 hits for AdMob, UMP, AAID, personalised or partner-sites.

```
terms/index.html:220:    <p>Privio contains <strong>no advertising of any kind</strong> in any tier. There are no banner ads, interstitial ads, rewarded ads, or sponsored content, and there is no advertising SDK in the app. See...
terms/index.html:247:      <li>You may withdraw consent to receive or sign documents electronically by not using the Sign tool.</li>
privacy/index.html:9:  <meta name="description" content="Privio Privacy Policy — your documents never leave your device. No ads, no tracking, no account. Erek Studio operates no servers and receives no data." />
privacy/index.html:218:      <p><strong>Privio shows no ads and does no tracking.</strong> There is no advertising SDK in the app, no ad-consent form and no App Tracking Transparency prompt, and Privio never accesses your devic...
privacy/index.html:232:      <li><strong>Advertising identifiers.</strong> Privio shows no ads and contains no advertising SDK. On iOS it never accesses your IDFA, so it shows no App Tracking Transparency dialog — there is no...
privacy/index.html:291:    <p>Privio is a document utility for adults and is not directed at children under 13. We do not knowingly collect personal information from children, and Erek Studio itself holds no user data at all. P...
privacy/index.html:298:      <li>Withdraw consent. <strong>Privio never asks for advertising or tracking consent, because it shows no ads and does no tracking.</strong> Camera and Photos access, if you granted it, can be turned...
privacy/index.html:305:    <p>Privio also does not "share" personal information for cross-context behavioural advertising, as the California CCPA/CPRA and comparable US state laws use that term: the app shows no ads, accesses n...
support/index.html:257:      <p>No. Every operation — scan, OCR, redact, sign, summarise — runs on your device's own hardware. Your documents are never uploaded: there is no Erek Studio server, no account, no analytics of o...
support/index.html:290:      <li><a href="../privacy/">Privacy Policy</a> — what stays on your device (your documents); no ads, no tracking, no account.</li>
```

## Open points (for review)
1. **ML Kit on iOS.** The iOS binary still links the `MLKitCommon`, `MLKitTextRecognition` and `GoogleDataTransport` pods (`ios/Podfile.lock`), as a plugin stub. The code never calls ML Kit on iOS, which is why the page says 2.3 "does not apply on iOS". That is true at runtime. However, Google's own `MLKitCommon` privacy manifest inside the IPA still declares analytics-purpose data types. The iOS App Privacy label is a separate decision.
2. **Universal claims.** "Apart from that, the only outbound activity is what you explicitly tap" and "That is the entire list" are older claims, now made with the ML Kit exception. The app also has a store rating prompt (`in_app_review` on Android, the native bridge on iOS). That prompt goes through the stores and was not added to the list.
3. **Free-tier wording in Terms §4.** It comes from the uncommitted 1.1.4 working tree. If the gates change before release, check it again.
