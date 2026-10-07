# ✂️ Microsoft Teams Link Trimmer & Cleaner

> **Sanitize long Microsoft Teams URLs to prevent broken links in Jira and issue trackers.**

A lightweight, zero-dependency, open-source web tool designed to trim and sanitize **Microsoft Teams message links, chat URLs, and channel links**. It strips away telemetry bloat, tracking IDs, and unnecessary parameters while keeping only essential context so your links paste cleanly without breaking Jira markdown fields or hitting character limits.

## 💡 The Problem It Solves

When pasting raw Microsoft Teams URLs into **Jira** (or other ticketing tools and markdown editors), the links often break or fail because:

1. **Jira URL & Character Limits:** Comments and custom text fields in Jira can truncate extra-long URLs.

2. **Broken Markdown Parsing:** Extremely long query strings with special characters tend to break Jira's automatic link renderer, making the pasted link unclickable or corrupted.

3. **Cluttered Issue Tickets:** Tracking tokens (`trackingId`, `deepLinkVariant`, `createdTime`) add unnecessary clutter to issue tickets, pull requests, and documentation.

**Microsoft Teams Link Trimmer** strips away the tracking payload so the link fits within length constraints and pastes cleanly into Jira.

## 🔍 Key Features

* **Jira-Friendly:** Prevents link corruption when pasting Teams threads into Jira tickets, comments, and documentation.

* **Removes Telemetry & Tracking:** Strips out `trackingId`, `createdTime`, `deepLinkVariant`, and other bloat parameters.

* **100% Privacy-Focused & Offline:** All processing is done client-side in your browser using JavaScript. No links or data are sent to external servers.

* **Fast & Lightweight:** Zero dependencies, instant execution, and copy-to-clipboard support.

## 🛠️ Preserved Query Parameters

Unlike generic link shorteners that redirect through third-party servers, this tool retains the native Microsoft Teams domain while preserving only the parameters required to jump directly to a thread:

| Parameter | Purpose / Function | 
| ----- | ----- | 
| `tenantId` | Identifies your organization or corporate Microsoft 365 tenant. | 
| `groupId` | Identifies the target Microsoft Teams channel or team context. | 
| `parentMessageId` | Points directly to the specific message thread or reply. | 

*All other tracking parameters are automatically safely discarded.*

## ⚡ Example

### ❌ Raw / Bloated Teams URL (Breaks in Jira / Hits Limits)

```
https://teams.microsoft.com/l/message/19%3Axxx@thread.v2/12345?tenantId=abc-123&groupId=def-456&parentMessageId=12345&createdTime=1600000000&trackingId=xyz-789&deepLinkVariant=desktop
```

### ✅ Cleaned / Trimmed Teams URL (Pastes Cleanly into Jira)

```
https://teams.microsoft.com/l/message/19%3Axxx@thread.v2/12345?tenantId=abc-123&groupId=def-456&parentMessageId=12345
```

## 🚀 How to Use

### Method 1: Live Web App (GitHub Pages)

1. Open the hosted web app: `https://zief.github.io/teams-link-trimmer/` *(Replace with your actual GitHub Pages URL)*.

2. Paste your long Microsoft Teams link into the input box.

3. Click **Bersihkan Link** (Clean Link).

4. Click **Salin ke Clipboard** and paste the result into Jira.

### Method 2: Run Locally

1. Clone this repository:

   ```bash
   git clone https://github.com/zief/teams-link-trimmer.git
   ```

2. Open `index.html` in any modern web browser.

## ❓ Frequently Asked Questions (FAQ)

### Why does Jira break long Teams links?

Jira parses raw URLs automatically into markdown or HTML links. When a Teams URL contains long query strings (especially tracking codes and encoded characters), the renderer can cut off the URL midway or fail to format it, resulting in a broken, unclickable link.

### Is it safe to use for internal work links?

Yes. The script runs entirely in your browser (`client-side`). No links, tenant IDs, or message parameters leave your browser or get sent to any server.

## 🏷️ Recommended GitHub Topics

Add these topics in your GitHub repository settings to boost discovery:
`jira` • `jira-fix` • `microsoft-teams` • `teams-link-cleaner` • `url-trimmer` • `url-sanitizer` • `privacy-tool`

## 👤 Credits

Created with ❤️ by **vibecoding \~niam**.
