# 🔐 Google Cloud CLI — Switch to Application Default Credentials (ADC)

This guide outlines the steps to **authenticate**, **configure**, and **use ADC** for your CLI and app environments.

---

## 🔁 Step 1: Reset any previous `gcloud` state (optional clean slate)

```bash
gcloud auth revoke
gcloud auth application-default revoke
gcloud config unset account
gcloud config unset project
```

---

## ✅ Step 2: Authenticate using ADC

```bash
gcloud auth application-default login
```

- This opens a browser window to authenticate.
- It creates/refreshes the file:  
  `~/.config/gcloud/application_default_credentials.json`

---

## 📁 Step 3: Set project for CLI and SDKs

```bash
gcloud config set project PROJECT_ID
```

> This ensures all your SDK/API calls know which GCP project to operate on.

---

## 👤 Optional: Verify and switch user account

```bash
gcloud auth list
gcloud auth application-default print-access-token
```

To explicitly switch:
```bash
gcloud auth application-default login --scopes=https://www.googleapis.com/auth/cloud-platform
```

---

## 🔁 Step 4: Confirm environment is using ADC

```bash
echo $GOOGLE_APPLICATION_CREDENTIALS
```

- If not set, Google SDKs will fallback to:
  `~/.config/gcloud/application_default_credentials.json`

✅ Test with:
```bash
gcloud auth application-default print-access-token
```

---

## 🧪 Test authenticated API access

```bash
gcloud storage buckets list
gcloud compute instances list
```

If ADC is working, these will return results under your project.

---

## 🛠️ CLI Reconfiguration

You can always reconfigure `gcloud`:

```bash
gcloud init
```

To re-authenticate or change projects.

---

## 🔁 Switch between service account and user ADC (advanced)

### Use Service Account JSON (permanent server-side)
```bash
export GOOGLE_APPLICATION_CREDENTIALS="/path/to/your-sa-key.json"
```

To switch back to browser-based ADC:
```bash
unset GOOGLE_APPLICATION_CREDENTIALS
gcloud auth application-default login
```

---

## 📚 Documentation

- [Application Default Credentials (Google Docs)](https://cloud.google.com/docs/authentication/application-default-credentials)
- [gcloud CLI Auth](https://cloud.google.com/sdk/docs/authorizing)
