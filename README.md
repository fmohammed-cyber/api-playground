# ⚡ API Playground for Jira

> Test any Atlassian REST or GraphQL API directly from Jira — no tokens, no setup

[![Atlassian Labs](https://img.shields.io/badge/Atlassian-Labs-0052CC?style=flat&logo=atlassian&logoColor=white)](https://github.com/atlassian-labs)
[![Forge](https://img.shields.io/badge/Built%20with-Forge-0052CC?style=flat)](https://developer.atlassian.com/platform/forge/)
[![Marketplace](https://img.shields.io/badge/Atlassian-Marketplace-0052CC?style=flat&logo=atlassian&logoColor=white)](https://marketplace.atlassian.com)

---

## 📖 Overview

**API Playground** is a native Postman-like API explorer built directly into Jira using the Atlassian Forge platform.

Stop switching to Postman. Stop manually setting up API tokens. Stop context switching.

API Playground gives you a complete API testing environment inside your Atlassian site — using your live session auth, with zero configuration required.

---

## ✨ Features

### 🔍 Natural Language Search
Describe what you want to do in plain English and the app finds the closest matching endpoint and pre-fills your request automatically.

```
"create an issue" → POST /rest/api/3/issue
"list projects"   → GET /rest/api/3/project
"get page content"→ GET /wiki/api/v2/pages
```

### ⚡ Zero-auth API Testing
Send real API requests to your live Jira site using your current session.
- **As User** — runs requests using your current site permissions
- **As App** — runs requests using the Forge app's configured scopes

### 📚 Full OpenAPI Coverage
Browse and search every endpoint across:
- Jira REST API **v2** & **v3**
- Bitbucket REST API
- Compass API
- Atlassian GraphQL Gateway

### ◈ GraphQL Explorer
Full GraphiQL editor with:
- Atlassian Gateway schema autocomplete
- Docs explorer — browse all available types and queries
- Real query execution through Forge native auth

### 💻 Forge Code Generator
Tested your API? Click **Code Gen** and get a ready-to-paste Forge resolver function in JavaScript or TypeScript.

```javascript
// Generated code example
resolver.define('myGetRequest', async ({ context }) => {
  const response = await api.asUser().requestJira(
    route`/rest/api/...`,
    { method: 'GET', headers: { 'Accept': 'application/json' } }
  );
  return response.json();
});
```

### ⭐ Bookmarks & History
- Save favourite requests as bookmarks with one click (⭐)
- Browse your full request history
- All data stored per-user in Forge Storage

### 📋 Developer Utilities
- **Copy as curl** — share requests with teammates instantly
- **Copy as bug report** — paste formatted markdown into community posts or support tickets
- **Response time indicator** — colour-coded ms indicator (green < 500ms, orange < 2s, red > 2s)
- **API schema panel** — see required/optional parameters inline as you type
- **Endpoint info tooltip** — hover over ℹ️ to see the endpoint description from the spec

### 🎯 Context-Aware
- Installed on Jira → shows Jira APIs by default

---

## 🚀 Installation

### From the Atlassian Marketplace
1. Go to the [Atlassian Marketplace listing](https://marketplace.atlassian.com)
2. Click **Get it now**
3. Select your Atlassian site
4. Click **Install**

The app will appear in your Jira navigation under **Apps → API Playground**.


## 🖥️ Usage

### Testing a REST API
1. Open **Apps → API Playground** in Jira
2. Select your **method** (GET, POST, PUT, PATCH, DELETE) from the dropdown
3. Enter the **API path** (e.g. `/rest/api/3/myself`)
4. Choose **auth mode** (As User or As App)
5. Add any **headers**, **query params** or **request body** as needed
6. Click **Send Request**

### Finding an Endpoint
- Use the **natural language search bar** — type what you want to do
- Browse the **Collections** tab — filter by product and API version
- Use the **schema panel** — see parameters for the current endpoint inline

### Saving & Reusing Requests
- Click the **⭐ star** in the Request panel to bookmark the current request
- View all bookmarks in the **Bookmarks** tab
- Previous requests are automatically saved to **History**

### Generating Forge Code
1. Build and test your request
2. Click the **Code Gen** tab
3. Toggle between **JavaScript** and **TypeScript**
4. Copy the generated resolver function and paste into your Forge app

### Copying as curl
Click the **`$ curl`** button in the Request panel header to copy the current request as a curl command — perfect for sharing with teammates or filing bug reports.

---

## 🏗️ Architecture

Built entirely on the **Atlassian Forge** platform:

| Component | Technology |
|---|---|
| Frontend | React (Custom UI) |
| Backend | Forge Resolvers (Node.js) |
| Storage | Forge Storage (per-user) |
| Auth | Forge native (`asUser` / `asApp`) |
| API Specs | Atlassian DAC OpenAPI specs (cached 24h) |
| GraphQL | GraphiQL + bundled Atlassian Gateway schema |

**No external infrastructure.** All processing happens within Atlassian's managed Forge runtime.

---

## 🔒 Privacy & Security

- **No data leaves your Atlassian site** — all requests are proxied through Forge functions on Atlassian infrastructure
- **No response bodies stored** — only request metadata (method, sanitised path, status code) is persisted
- **PII-safe storage** — query parameters containing personal identifiers (accountId, email, etc.) are automatically stripped before saving to history
- **No credentials collected** — uses Forge native auth; no passwords or API tokens are ever requested from users
- **Forge Storage only** — all persistence uses Atlassian-managed Forge Storage, scoped per user

---

## 📄 License

Copyright (c) 2026 Atlassian. Licensed under the Apache License, Version 2.0.

---

## 🙋 Support

- **Issues**: [GitHub Issues](https://github.com/atlassian-labs/api-playground/issues)
- **Forge Docs**: [developer.atlassian.com/platform/forge](https://developer.atlassian.com/platform/forge/)
