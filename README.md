# Kaylee-Jane Client Intelligence Hub — V1.1

Premium executive portal. No gold. No login gate. Subdomain-ready for GitHub Pages.

## Folder map
```
/
├── index.html
├── CNAME                # ← change to client.kaylee-jane.com
├── robots.txt           # noindex – private engagement
├── /data/
│   ├── client-config.json   # Client name, engagement, ID, dates
│   ├── notes.json           # Advisor Notes – appears on Dashboard
│   ├── documents.json       # Document Vault entries
│   └── resources.json       # Resources Library entries
└── /vault/
    ├── reports/
    ├── governance/
    └── engagement/
```

## How to update — no code
1. **Advisor Notes**  
   Edit `/data/notes.json` – add a new object at the top of the array. Push. It appears on the Dashboard.
   ```json
   {
     "date": "2026-06-19",
     "title": "Your note title",
     "body": "Your note body.",
     "tag": "Diagnosis"
   }
   ```

2. **Document Vault**  
   a. Upload your PDF to `/vault/reports/` (or governance/ or engagement/)  
   b. Add one entry to `/data/documents.json`:
   ```json
   {
     "title": "Report – Week ending 12.06.2026",
     "category": "reports",
     "categoryLabel": "Reports & Findings",
     "date": "2026-06-12",
     "type": "PDF",
     "file": "vault/reports/report-week-ending-12-06-2026.pdf"
   }
   ```
   That's it. No HTML edits.

3. **Resources Library**  
   Edit `/data/resources.json` – same pattern.

4. **Client details**  
   Edit `/data/client-config.json`

## Deploy to GitHub Pages (subdomain)
1. Create a new private repo per client, e.g. `kj-client-acme`
2. Upload this whole folder
3. Settings → Pages → Deploy from main branch, /root
4. Set your subdomain DNS: CNAME `client` → `<your-github-username>.github.io`
5. Update the `CNAME` file in the repo to `client.kaylee-jane.com`
6. Wait for Pages to issue HTTPS

Each client gets their own isolated repo/subdomain. When engagement ends, archive the repo.

Note: `fetch('./data/*.json')` requires http — it won't work opening `index.html` via file:// locally. Use GitHub Pages, or run `python -m http.server` locally for testing.
