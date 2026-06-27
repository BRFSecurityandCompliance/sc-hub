# Security & Compliance Hub

Central link hub for the BevChain S&C team. Single self-contained `index.html`
(vanilla JS, no build step). Public portal + password-gated admin console (`#admin`).

## Deploy to Azure Static Web Apps (recommended)

### 1. Push to GitHub
    git init
    git add .
    git commit -m "Security & Compliance hub"
    git branch -M main
    git remote add origin https://github.com/brfsecurityandcompliance/sc-hub.git
    git push -u origin main

### 2. Create the Static Web App
1. Azure Portal -> Create a resource -> "Static Web App" -> Create.
2. Subscription + Resource Group (new: `rg-sc-hub`).
3. Name: `sc-hub`. Plan type: **Free**. Region: East Asia (or nearest).
4. Deployment source: **GitHub** -> sign in -> pick org `brfsecurityandcompliance`,
   repo `sc-hub`, branch `main`.
5. Build presets: **Custom**.
   - App location: `/`
   - Api location: (leave blank)
   - Output location: (leave blank)
6. Review + Create.

Azure commits a workflow to `.github/workflows/` and runs it. After ~1-2 min your
site is live at `https://<name>.azurestaticapps.net`. Every `git push` redeploys.

## Admin
Default password: `scadmin2026` (change it in Settings).
Note: this is a client-side soft gate. For real security, protect the admin behind
Entra ID (see "Secure the admin" below).

## Data
Stored per-browser via localStorage. Use Settings -> Export JSON to back up or move
between machines. For shared multi-user data, move to Supabase / SharePoint.
