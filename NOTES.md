# Kumar Bajagain — Personal Website Notes

## What Was Built
A clean static HTML/CSS personal academic website, replacing a broken React app (forked from sudip-ghimire) that had a blank white page issue.

**Live site:** https://kumarbajagain.com.np  
**GitHub repo:** https://github.com/kumarbajagain/kumarbajagain.github.io  
**Local folder:** `C:\Users\kumar\Desktop\Kumar_Website\`

---

## Hosting Setup

| Layer | Service | Notes |
|---|---|---|
| Code hosting | GitHub Pages | Repo: kumarbajagain.github.io, branch: master |
| Domain | .com.np (Nepal) | kumarbajagain.com.np |
| DNS + CDN | Cloudflare (free) | Handles DNS, SSL, caching |

**Cloudflare settings to keep:**
- Rocket Loader → **OFF** (was breaking React, keep off)
- Auto Minify JS → **OFF**
- SSL mode → **Full**
- If site breaks after changes → Cloudflare dashboard → Caching → **Purge Everything**

---

## File Structure

```
Kumar_Website/
├── index.html          ← Main website (all sections in one file)
├── style.css           ← All styles
├── CNAME               ← Contains: kumarbajagain.com.np (needed for custom domain)
├── .nojekyll           ← Prevents GitHub from using Jekyll
├── favicon.png         ← Iceberg icon (from icon_iceberg.png)
├── profile.jpg         ← Profile photo
├── intro.jpg           ← Hero background image
├── CV_KUMAR_BAJAGAIN.pdf ← Resume/CV
└── NOTES.md            ← This file
```

---

## Website Sections

1. **Home** — Hero with name, title, Purdue, tagline, buttons, social links
2. **About** — Bio, profile photo, highlight cards
3. **Research** — Research description + interests tags
4. **Projects** — 6 project cards
5. **Education** — Purdue PhD, TU M.Sc. (3.85/4.0), TU B.Sc. (58.1%)
6. **Skills** — Research/Modeling, Data/Programming, Technical Tools
7. **Publications** — Placeholder (add when available)
8. **Experience** — NARERL research, Master's thesis, Bachelor's project, SAMA volunteering
9. **Certifications** — 6 training programs + SAMA Student Champion Award
10. **Blog** — 4 placeholder posts (add content when ready)
11. **Gallery** — Placeholder (add photos when ready)
12. **Contact** — Emails, address, LinkedIn, GitHub, Google Maps (Purdue)

---

## How to Update the Website

### Edit content
1. Open `index.html` or `style.css` in any text editor
2. Make changes
3. Push to GitHub (see below)

### Push changes to GitHub
```bash
cd /c/Users/kumar/Desktop/Kumar_Website
git add index.html style.css
git commit -m "Your description of changes"
git pull origin master --rebase
git push origin main:master
```

### Add new files (images, PDFs etc.)
```bash
git add filename.jpg
git commit -m "Add new file"
git push origin main:master
```

### If push is rejected (non-fast-forward)
```bash
git pull origin master --rebase
git push origin main:master
```

---

## Services & Accounts

### GoatCounter Analytics
- **Dashboard:** https://kumarbajagain.goatcounter.com
- Shows: page views, visitor countries, browsers, referrers
- Script is in index.html before `</body>`
- Free, privacy-friendly, no tracking cookies

### Visitor Counter Widget
- **Service:** counterapi.dev (free, no account needed)
- API endpoint: `https://api.counterapi.dev/v1/kumarbajagain/visits/up`
- Shows as a small dark widget fixed in bottom-right corner
- Counts every page load (+1 per visit)

### Google Search Console
- **URL:** https://search.google.com/search-console
- Verified with HTML meta tag in `<head>` of index.html
- Use to request re-indexing when site changes

---

## Key Contact Info on Site
- **Purdue email:** kbajagai@purdue.edu
- **Alt email:** kumarbajagain@outlook.com
- **LinkedIn:** https://www.linkedin.com/in/kumarbajagain
- **GitHub:** https://github.com/kumarbajagain

---

## Things To Do Later
- [ ] Add real publications when available
- [ ] Add gallery photos (categories: Purdue, Research, Conferences, Community, NEPSAP, Travel)
- [ ] Write blog posts (ERA5 processing, LPJ-STM setup, etc.)
- [ ] Add Google Scholar link when profile is created
- [ ] Update CV PDF when it changes (replace `CV_KUMAR_BAJAGAIN.pdf`)
- [ ] Enable 2FA on GitHub account for security

---

## Troubleshooting

| Problem | Fix |
|---|---|
| Site not updating | Cloudflare → Purge Everything, then Ctrl+Shift+R |
| Favicon not updating | Open in incognito window |
| Push rejected | Run `git pull origin master --rebase` first |
| CSS not updating | Change `?v=3` to `?v=4` in the CSS link in index.html |
| Blank white page | Check Cloudflare: Rocket Loader must be OFF |

---

## Old Site Issue (for reference)
The previous React site (forked from sudip-ghimire) had a blank white page because:
- React was not mounting (`root.innerHTML.length = 0`)
- Webpack bundle used `webpackJsonpsudip-ghimire` name
- CountAPI (old visitor counter) was dead
- The site was compiled React code with no source files available
- Solution: replaced entirely with clean static HTML/CSS
