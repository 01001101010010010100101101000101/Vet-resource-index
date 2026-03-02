# Veteran Resources Directory

A comprehensive, single-page HTML directory of resources for U.S. military veterans, service members, and their families. Resource cards are populated from a **Google Sheet** — update the sheet to update the site, no code changes needed.

---

## Quick Start

### 1. Copy the Google Sheet template

Create a new Google Sheet with these exact column headers in row 1:

| Column | Description |
|---|---|
| `section` | Which section the card belongs to (see values below) |
| `title` | Card heading (e.g. `Veterans Crisis Line`) |
| `tag_type` | Badge color: `urgent`, `federal`, `nonprofit`, `state`, or blank |
| `description` | 1–2 sentence description shown on the card |
| `phone1_label` | Label for first phone (e.g. `Call`) |
| `phone1_number` | First phone number (e.g. `988`) |
| `phone2_label` | Label for second phone (optional) |
| `phone2_number` | Second phone number (optional) |
| `link1_label` | Text for first link button (e.g. `Website`) |
| `link1_url` | Full URL for first link |
| `link2_label` | Text for second link (optional) |
| `link2_url` | URL for second link (optional) |
| `link3_label` | Text for third link (optional) |
| `link3_url` | URL for third link (optional) |
| `tags` | Space-separated search keywords (e.g. `crisis hotline ptsd`) |

**Valid `section` values:**

| Value | Page section |
|---|---|
| `crisis` | Crisis & Emergency |
| `mental-health` | Mental Health |
| `va-benefits` | VA Benefits & Claims |
| `healthcare` | Healthcare |
| `housing` | Housing & Homelessness |
| `employment` | Employment & Career |
| `education` | Education & Training |
| `legal` | Legal Resources |
| `state` | Resources by State |

### 2. Publish the sheet as CSV

1. In Google Sheets: **File → Share → Publish to web**
2. Select **Sheet1** (or your sheet tab name)
3. Change format to **Comma-separated values (.csv)**
4. Click **Publish** and copy the URL

It looks like:
```
https://docs.google.com/spreadsheets/d/e/XXXXXXXXXXXXXXXX/pub?gid=0&single=true&output=csv
```

### 3. Paste the URL into index.html

Open `index.html` and find this line near the bottom:

```js
var SHEET_URL = '';
```

Replace it with your URL:

```js
var SHEET_URL = 'https://docs.google.com/spreadsheets/d/e/XXXXXXX/pub?output=csv';
```

### 4. Done

Open `index.html` in a browser. Cards load automatically from the sheet. To update a resource, edit the sheet — visitors see changes on their next page load (no deployment needed).

---

## Example Data Row

| section | title | tag_type | description | phone1_label | phone1_number | link1_label | link1_url | tags |
|---|---|---|---|---|---|---|---|---|
| crisis | Veterans Crisis Line | urgent | Free, confidential support 24/7 | Call | 988 | Website | https://www.veteranscrisisline.net/ | crisis hotline suicide |

---

## Features

- **Google Sheets backend** — edit a spreadsheet to update all cards
- **Live search** — filters cards instantly by keyword or tag
- **No build step** — pure HTML/CSS/JS, open directly in any browser
- **Accessible** — skip link, ARIA labels, semantic HTML, keyboard navigable
- **Responsive** — works on mobile, tablet, and desktop
- **Crisis-first design** — persistent 988 banner, urgent-tagged cards

---

## Local Development

```bash
# Python
python3 -m http.server 8080

# Node
npx serve .
```

Then open `http://localhost:8080`.

> **Note:** Fetching the Google Sheet requires a web server (even a local one). Opening `index.html` as a `file://` URL will fail due to browser CORS restrictions.

---

## Crisis Resources (Always Hardcoded)

These are hardcoded in the page header and footer regardless of the sheet:

| Resource | Contact |
|---|---|
| Veterans Crisis Line | Call/text **988**, press 1 |
| Safe Helpline (MST) | 1-877-995-5247 |
| National Domestic Violence Hotline | 1-800-799-7233 |
| Homeless Veterans Hotline | 1-877-424-2365 |
| SAMHSA Helpline | 1-800-662-4357 |

---

*Not affiliated with or endorsed by the U.S. Department of Veterans Affairs or any government agency. Always verify benefit details directly with the relevant agency.*
