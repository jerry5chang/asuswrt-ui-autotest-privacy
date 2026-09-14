# ASUSWRT UI Autotest Privacy Policy

Effective date: September 14, 2026

Applies to: ASUSWRT UI Autotest v3.2

Maintainer: [jerry5chang](https://github.com/jerry5chang)

## 1. Purpose and scope

ASUSWRT UI Autotest is a browser extension for testing an ASUSWRT router web
interface or a mock server selected by the user. It reads device information,
runs selected UI checks, and produces reports. It is not a general browsing
history collector. Data handling depends on the selected tests and settings.
Processing data locally is still data handling, as described below.

## 2. Data the extension handles

- **Account and authentication information:** a device username and password
  entered in the extension's settings, plus authentication challenges and
  responses used to log in to the selected device. Authenticated requests may
  use that device's browser session cookies.
- **Device and network information:** device URLs and IP addresses, model,
  firmware, UI version, territory code, language, available pages, capabilities,
  and information returned by the selected API checks. Device responses or
  diagnostics may include identifiers such as hostnames, client names, or MAC
  addresses. The extension does not request GPS/browser geolocation access.
- **Website content and test activity:** page URLs, inspected text, DOM and
  accessibility properties, styles, links, JavaScript/console errors, UI logs,
  API request metadata and parameters inspected during testing, test actions,
  timestamps, durations, and results. Only information relevant to the selected
  checks is included in their results; not every inspected value is retained.
- **Preferences and reports:** test selection, language/territory selections,
  tool settings, timing estimates, current run state, and saved reports.

The extension has no feature designed to collect health records, payment or
financial details, or personal messages. However, a tested page, API parameter,
or diagnostic log may itself contain sensitive information. Do not assume that
reports or logs are fully anonymized or that every secret is automatically
removed. Inspect and redact reports before sharing them.

## 3. Uses, storage, and security

Data is used to authenticate to the selected device, execute and diagnose tests,
display progress, preserve settings and results, estimate test duration, and
generate user-requested report exports. The extension has no developer-operated
analytics, advertising, or automatic report-upload service.

Settings, including a password supplied in settings, are stored in the browser
profile using `chrome.storage.local`. Current run state uses
`chrome.storage.session`; history and timing information use local extension
storage. Exported reports are saved to a location chosen through the browser's
download flow. The extension does not use `chrome.storage.sync` for these data.

The extension does not add its own encryption to locally stored settings and
reports. Protect the browser profile and downloaded files, and use dedicated
test credentials rather than credentials for production systems. Device
connections use the HTTP or HTTPS address selected by the user; HTTP does not
provide transport encryption. Prefer HTTPS where supported and trusted test
networks. This policy does not promise that every device connection is encrypted.

## 4. Network requests and sharing

- **Selected device or mock server:** receives requests necessary for probing,
  authentication and testing. Depending on the enabled test mode, UI actions
  can send settings requests. On a positively identified writable mock server,
  the device-read check can temporarily test territory-code writes, and selected
  SKU scenarios can change territory/language with readback and recovery checks.
  The extension does not change a real DUT's territory code for SKU scenarios.
- **External-link checks:** when selected, the extension requests external URLs
  found in the tested UI and may follow redirects and check each host's home
  page. Its external-link checker omits browser credentials. Destination
  servers still receive normal request information, including the requesting
  network's IP address and the requested URL, which may contain query parameters.
- **Connectivity check:** the external-link check may also request the configured
  connectivity endpoint. The default is
  `http://connectivitycheck.gstatic.com/generate_204`. The endpoint is configurable;
  leaving it empty skips this connectivity probe, not other external requests.
- **Resources loaded by the DUT UI:** navigating the tested pages may cause those
  pages to request their own external scripts, images, support links, or services.
  Those requests and any associated cookies follow the page's behavior and
  browser settings, not the credential-omission rule of the extension's link checker.
- **User-directed sharing:** exports stay on the user's computer unless the user
  shares them or another application uploads/synchronizes them. Information a
  user voluntarily submits to project support is handled through GitHub under
  GitHub's policies. Public issues and attachments are publicly visible.

The extension does not automatically send device credentials or complete test
reports to its developer. Operators of the selected device, external destinations,
and services the user chooses to use may retain their own logs under their own
policies; this extension cannot delete those remote copies.

We use data only for the extension's stated testing features and user-requested
support. We do not sell user data, use or transfer it for advertising, use it for
unrelated purposes, or use it to determine creditworthiness or lending eligibility.
Our use of data accessed through Chrome APIs follows the Chrome Web Store User
Data Policy, including its Limited Use requirements.

## 5. Isolated SKU source checks

Some SKU checks read the selected device's deployed frontend functions or
bounded source fragments and execute fixed test cases in a short-lived sandboxed
iframe. This environment has no extension API or same-origin access; its content
security policy blocks network connections and form submissions. Test control
logic and expected results are included in the extension package. Results return
to the local test runner. This is a device-code test, not a remote extension
update mechanism.

## 6. Retention and user controls

- Settings and timing information remain in the browser profile until changed
  or removed. Clear a saved password in the settings and allow the change to save
  if it is no longer needed. This does not erase copies in earlier run state,
  reports, or exports.
- Report history keeps the most recent three runs by default. The retention
  count can be adjusted up to twenty; it is a count limit, not a time-based
  expiry. Older records are removed when the limit is enforced.
- Use **Clear history** in report history to delete saved report history, and
  **Clear** in the run controls to reset the current run. Clearing history does
  not delete settings or downloaded reports. Browser session storage is temporary;
  do not rely on it as the only place a run's information may have been saved.
- To remove all extension-local data, remove the extension from the relevant
  Chrome profile. Downloaded files, OS/cloud backups, router login cookies and
  sessions, and copies already shared with others must be removed separately
  using the relevant application or service.
- You can stop a test, deselect external-link checking, or remove the extension
  to prevent further extension-initiated testing. Stopping does not undo device
  changes already made by UI interactions; mock recovery failures are reported.

## 7. Contact and policy changes

For privacy questions, contact the maintainer through
[GitHub Issues](https://github.com/jerry5chang/asuswrt-ui-autotest-privacy/issues).
Do not post passwords, authentication tokens, private network information, or
unredacted reports in a public issue. You may first ask how to discuss a privacy
concern without including sensitive information. The developer does not have a
remote copy of your local data merely because you installed the extension.

Updates to this policy will be published on this page with a revised effective
date. Material changes to data handling will also be reflected in the extension's
disclosures and Chrome Web Store declarations, with consent obtained where required.

## 繁體中文摘要

本政策適用於 ASUSWRT UI Autotest v3.2。工具處理使用者指定之路由器或 mock
的登入設定、設備及網路資訊、待測頁面內容、API／錯誤／互動紀錄與測試報告。
這些資料主要在本機瀏覽器處理；即使未傳給開發者，仍屬資料處理。

登入密碼會隨設定保存在瀏覽器本機儲存區，工具未另外加密本機設定或報告。
請使用測試用帳號、保護瀏覽器設定檔，並優先使用 HTTPS。報告不保證已完整
去識別化或移除所有敏感資訊，分享前務必檢查。

工具沒有開發者營運的分析、廣告或自動報告上傳服務。但選取對外連結檢測時，
會連線到頁面中的網址、重新導向目的地、主機首頁及設定的連線檢查端點；
待測 UI 本身也可能載入第三方資源。對方可取得一般請求資訊，例如來源 IP
及 URL。使用者自行分享報告、雲端同步檔案或在 GitHub 留言不屬於僅限本機。

歷史報告預設保留最近 3 輪，可調整至 20 輪。清除報告紀錄不會清除登入設定、
目前執行狀態或已下載檔案；移除擴充功能可移除該 Chrome 設定檔內的擴充功能
資料，下載檔、備份、設備登入工作階段及外部副本需另外處理。
資料僅用於上述測試功能及使用者要求的支援，不販售、不用於廣告、無關用途
或信用／貸款判斷。隱私問題請透過上方 GitHub Issues 聯絡，勿公開敏感資料。
