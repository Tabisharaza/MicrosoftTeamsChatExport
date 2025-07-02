# 📤 Microsoft Teams Chat Export Tool

**Export your Microsoft Teams chat conversations directly into structured JSON with ease and clarity.**
This lightweight, browser-based tool uses Microsoft Graph API with modern authentication via MSAL.js and allows users to browse, view, and export their Teams chat messages securely.

---

## 🛠 Features

* 🔐 Secure login using Microsoft OAuth2 (MSAL.js)
* 📂 Lists all Teams chat threads
* 📥 Exports chat content (with participant names, timestamps, and message bodies) into a clean downloadable `.json` file
* 🧹 Automatically removes system bots like `Fireflies.ai Notetaker`
* 🚫 Skips anonymous or unidentified message authors for cleaner exports
* 🔁 Supports pagination (`@odata.nextLink`) to load all historical messages
* 🎯 Clean UI with loading overlays and friendly prompts

---

## 🚀 Getting Started

### 1. **Clone the Repository**

```bash
git clone https://github.com/Tabisharaza/MicrosoftTeamsChatExport.git
cd teams-chat-export
```

### 2. **Setup Your Azure AD App Registration**

1. Go to [Azure Portal – App Registrations](https://portal.azure.com/#blade/Microsoft_AAD_RegisteredApps)
2. Create a **new registration**
3. Note down:

   * `Client ID`
   * `Tenant ID`
4. Under **Authentication**, add your site as a **Redirect URI**

   * e.g. `http://localhost` or your hosted domain
5. Under **API Permissions**, add:

   * `Chat.Read`
   * `Chat.ReadBasic`
   * `User.Read`
   * (Ensure admin consent is granted)

---

## 🧾 Configuration

Open the HTML file and replace the following lines:

```js
clientId: ADD YOUR CLIENT ID HERE,
authority: 'https://login.microsoftonline.com/ADD YOUR TENET ID HERE',
```

with your actual credentials.

Also ensure your redirect URI matches `window.location.href`.

---

## ✅ Usage

1. Open `index.html` in a browser (or host it securely)
2. Click **"Sign In with Microsoft"**
3. After successful login, your chat list will appear
4. Click any chat to begin exporting
5. JSON download will begin automatically once messages are fetched

---

## 📎 Notes

* This tool uses [Microsoft Graph API](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0)
* This is a **read-only** tool; it does not modify any Teams data
* No server backend – **all data stays in your browser session**
* Ensure your organization’s Microsoft 365 tenant allows third-party Graph access

---

## 📁 Sample Output (JSON)

```json
[
  {
    "displayName": "John Doe",
    "userIdentityType": "aadUser",
    "content": "<p>Hello, team!</p>",
    "createdDateTime": "2025-07-01T08:30:00Z"
  },
  ...
]
```

---

## 🧼 Clean Chat Export Policy

The tool **automatically filters out:**

* Empty or anonymous messages
* Fireflies.ai bot messages
* Non-parseable content blocks

---

## 🙏 Acknowledgements

* Microsoft Graph API Team
* MSAL.js by Microsoft
* The open-source community

---

## ✉️ Support

For feature requests or issues, kindly open a [GitHub Issue](https://github.com/Tabisharaza/MicrosoftTeamsChatExport/issues)
For private consultations or enterprise needs, feel free to connect.

---

Crafted with care for professionals who believe **data should be portable, clean, and respected**.
