# Veloci Partners — Launch Guide

From this folder to a live site at **www.velocipartners.com**, via GitHub.

Time: ~60 minutes of work, plus DNS propagation. Hosting cost: **$0**. The domain stays at GoDaddy.

**Folder location:** `Desktop\Tax Ease\TaxEase\velocipartners-site\`

---

## Step 1 — Preview it

Double-click `index.html`. It opens in your browser — no install, no server. Drag the window narrow to check the mobile layout.

---

## Step 2 — Fill in the remaining details

Your logo, email (`clients@velocipartners.com`), both phone numbers and the Lagos / London / Berlin locations are already in the site.

Open `index.html` in any text editor (Notepad works, VS Code is nicer) and Ctrl+F for:

| Find | Replace with |
|---|---|
| `YOUR_FORM_ID` | Your Formspree ID — see Step 3 |
| `Monday – Friday, 9:00am – 5:00pm` | Your actual hours, if different |

Then, in the same file:

- **The quote section** (marked `<!-- ==== QUOTE ==== -->`) — replace with a real client testimonial, or delete the whole `<section>`.
- **"Who We Serve"** — trim the industry list to what you actually serve. A short honest list converts better than a long generic one.
- **Locations** — check the Lagos / London / Berlin descriptions match how you actually operate. If any of the three isn't a real presence, soften the wording to "serving clients in…" rather than implying an office.
- **Claims** — don't add client counts, years in business, or credentials you can't substantiate. Accounting sites get read carefully.

The hero visual is a decorative globe — no figures, no data, nothing that needs verifying.

---

## Step 3 — Turn the contact form on (2 minutes)

GitHub Pages serves static files only — it can't process form submissions. Formspree handles that for free.

1. Sign up at **formspree.io**.
2. **+ New Form** → name it "Veloci Partners website" → set the recipient to `clients@velocipartners.com`.
3. Copy the form ID (looks like `xayzbwqd`).
4. In `index.html`, replace `YOUR_FORM_ID` so the line reads:
   `<form action="https://formspree.io/f/xayzbwqd" method="POST" class="reveal">`
5. After the site is live, submit a test enquiry and confirm the first-time verification email.

Free tier: 50 submissions/month. A honeypot spam trap is already built in.

---

## Step 4 — Push to GitHub

The folder is **already a Git repo** with your first commit made. You just need to publish it.

### Easiest: GitHub Desktop

1. Install **desktop.github.com**, sign in.
2. **File → Add Local Repository** → browse to `velocipartners-site` → Add.
3. Click **Publish repository**. Untick "Keep this code private" if you want it public (GitHub Pages works either way on free accounts now, but public is simpler).

### Or: command line

Create an empty repo at **github.com/new** — name it `velocipartners-site`, and do **not** tick "Add a README". Then in a terminal:

```bash
cd "C:\Users\omoto\OneDrive\Desktop\Tax Ease\TaxEase\velocipartners-site"
git remote add origin https://github.com/YOUR_USERNAME/velocipartners-site.git
git push -u origin main
```

Future changes:

```bash
git add -A
git commit -m "Update services copy"
git push
```

> **A note on OneDrive:** Git repos inside a synced OneDrive folder occasionally hit file-lock conflicts. It works, but if you start seeing odd sync errors, move the folder to `C:\Users\omoto\Projects\velocipartners-site` and re-add it in GitHub Desktop.

---

## Step 5 — Switch on GitHub Pages

In your repo: **Settings → Pages**

- Source: **Deploy from a branch**
- Branch: **main**, folder: **/ (root)** → **Save**

Within a minute it's live at `https://YOUR_USERNAME.github.io/velocipartners-site/`. Open it and check.

The `CNAME` file in the repo already contains `www.velocipartners.com`, so GitHub will pick up the custom domain automatically once DNS points at it.

---

## Step 6 — Point the GoDaddy domain at GitHub

Go to **GoDaddy → My Products → Domains → velocipartners.com → DNS → Manage DNS**.

**First:** delete GoDaddy's default parked records — usually an `A` record on `@` pointing to a GoDaddy IP, and a `CNAME` on `www`. Screenshot the existing records before deleting, in case you have email set up.

**Then add five records:**

| Type | Name | Value | TTL |
|---|---|---|---|
| A | `@` | `185.199.108.153` | 1 hour |
| A | `@` | `185.199.109.153` | 1 hour |
| A | `@` | `185.199.110.153` | 1 hour |
| A | `@` | `185.199.111.153` | 1 hour |
| CNAME | `www` | `YOUR_USERNAME.github.io` | 1 hour |

The CNAME value ends in `.github.io` — it's your GitHub *username*, not the repo name.

Save. Propagation is usually under an hour, occasionally up to 24.

⚠️ If you have email on this domain (Microsoft 365 via GoDaddy, etc.), leave the **MX** records alone. Only touch the A and CNAME records above.

---

## Step 7 — Enforce HTTPS

Back in **repo → Settings → Pages**. Once DNS resolves, GitHub issues a free certificate automatically — the **"Enforce HTTPS"** checkbox becomes clickable. Tick it.

If it stays greyed out, DNS hasn't propagated yet. Wait, then remove and re-enter the custom domain to retrigger the check.

Don't launch without the padlock. Nobody submits financial details to an unsecured page.

---

## Step 8 — Make sure clients@velocipartners.com actually receives mail

The site advertises this address, so it needs a working mailbox before launch.

- **Zoho Mail** — free for one user on your own domain
- **Google Workspace** — ~$7/user/month, best if you already live in Gmail

Both give you MX records to add in GoDaddy DNS alongside the A/CNAME records from Step 6. They don't conflict — just don't delete the MX records while editing.

Send yourself a test message from an outside account and confirm it lands.

---

## Step 9 — Get found

1. **Google Search Console** (search.google.com/search-console) → add `velocipartners.com` → verify with a DNS TXT record in GoDaddy → submit `https://www.velocipartners.com/sitemap.xml`. This is how Google learns the site exists.
2. **Google Business Profile** (google.com/business) → create a listing with service area, hours and phone. For a local firm this usually drives more enquiries than the website itself.
3. Add the link to your LinkedIn company page and email signature.

Adding your city to the page title and H1 ("Accounting & Advisory in [city]") noticeably improves local search later.

---

## Step 10 — Pre-launch checklist

- [ ] Formspree ID pasted in — test submission received
- [ ] `clients@velocipartners.com` receiving mail
- [ ] Both phone numbers dial correctly from the site on a phone
- [ ] Placeholder quote replaced or deleted
- [ ] Industries list trimmed
- [ ] Location wording matches reality
- [ ] No unverifiable claims
- [ ] Padlock showing on `https://www.velocipartners.com`
- [ ] Opened on an actual phone, not just a narrow browser window
- [ ] Every nav link scrolls to the right section
- [ ] Old GoDaddy Website Builder site cancelled once the new one is live

---

## Sources

- [Managing a custom domain for your GitHub Pages site — GitHub Docs](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)
- [Configuring a publishing source for GitHub Pages — GitHub Docs](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)
