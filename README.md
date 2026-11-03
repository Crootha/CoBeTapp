# Bilance soukromí / Privacy Balance (PWA)

**CZ:** Offline PWA pro cost-benefit analýzu soukromí a anonymity. Průvodce pro nováčky, expertní režim s váhami a simulací Monte Carlo, 21 šablon, čeština i angličtina. Bez serveru, nic neopustí prohlížeč.

**EN:** Offline PWA for privacy and anonymity cost-benefit analysis. Guided mode for beginners, expert mode with weights and Monte Carlo simulation, 21 templates, Czech and English. No server, nothing leaves your browser.

## Soubory / Files

| Soubor / File | Účel / Purpose |
|---|---|
| `index.html` | celá aplikace / the whole app |
| `manifest.webmanifest` | PWA manifest |
| `sw.js` | service worker, offline cache |
| `icon*.png`, `icon.svg` | ikony / icons |
| `vercel.json` | nastavení pro Vercel / Vercel config |
| `LICENSE` | GPL-3.0-or-later |

Všechny soubory musí ležet **v kořeni** repozitáře nebo nasazované složky. / All files must sit **at the root** of the repo or deployed folder.

## Nasazení / Deploy

Aplikace je statická: žádný build, žádný `package.json`, žádný server. / The app is static: no build, no `package.json`, no server.

### Vercel

**CZ – proč to nemusí fungovat:**
1. **`index.html` není v kořeni.** Nahraný ZIP nebo podsložka (např. `bilance-soukromi-pwa/index.html`) vede k chybě 404. Soubory rozbalte do kořene repozitáře, nebo ve Vercelu nastavte *Root Directory* na tu podsložku.
2. **Špatně rozpoznaný framework.** Když Vercel nastaví *Framework Preset* na Vite, Next.js apod. nebo *Output Directory* na `dist`/`public`, hledá výstup buildu, který neexistuje („No Output Directory named … found“). U projektu bez frameworku („Other“) Vercel navíc dává přednost složce `public`, pokud existuje. Řešení: *Framework Preset* **Other**, *Build Command* a *Output Directory* nechte prázdné (bez override). Přiložený `vercel.json` nastavuje `"framework": null`.
3. **Ochrana nasazení.** Preview URL (`…-git-…vercel.app`) jsou ve výchozím stavu za přihlášením do Vercelu. Otevřete produkční doménu, nebo vypněte *Settings → Deployment Protection → Vercel Authentication*.
4. **Stará verze z cache.** Service worker drží starou verzi. Po každé změně `index.html` zvyšte `CACHE` v `sw.js` (`bilance-v5` → `bilance-v6`) a stránku dvakrát obnovte.

**CZ – postup přes GitHub:**
1. Nahrajte všechny soubory do kořene nového repozitáře na GitHubu.
2. Na vercel.com → *Add New… → Project* → importujte repozitář.
3. *Framework Preset*: **Other**. *Root Directory*: `./`. Build ani Output Directory nevyplňujte.
4. *Deploy*. Hotová adresa je `https://<projekt>.vercel.app`.

**CZ – postup přes příkazovou řádku:**
```bash
npm i -g vercel
cd slozka-s-index-html
vercel          # první nasazení, odpovězte na otázky (bez build příkazu)
vercel --prod   # produkce
```

**EN – why it may fail:**
1. **`index.html` is not at the root.** Uploading the ZIP itself or a subfolder causes a 404. Put the files at the repo root or set *Root Directory* to that subfolder.
2. **Wrong framework detection.** If Vercel picks Vite/Next.js or an output directory like `dist`/`public`, it looks for build output that doesn’t exist. For “Other” projects Vercel prefers a `public` folder when one exists. Use *Framework Preset* **Other** with no build command and no output-directory override. The included `vercel.json` sets `"framework": null`.
3. **Deployment Protection.** Preview URLs require a Vercel login by default. Use the production domain or turn off *Vercel Authentication* under *Settings → Deployment Protection*.
4. **Stale cache.** The service worker keeps serving the old version. Bump `CACHE` in `sw.js` after every change and reload twice.

**EN – via GitHub:** push the files to the repo root → *Add New… → Project* → import → Preset **Other**, Root `./`, no build/output → *Deploy*.

**EN – via CLI:** `npm i -g vercel`, then `vercel` and `vercel --prod` inside the folder with `index.html`.

### GitHub Pages
*Settings → Pages →* branch `main`, folder `/ (root)`.

### Netlify / Cloudflare Pages
Přetáhněte složku, build nevyplňujte. / Drag the folder in, leave build empty.

### Lokálně / Locally
`python3 -m http.server 8000` → http://localhost:8000

Instalace (PWA) a offline fungují jen přes HTTPS nebo `localhost`. / Install and offline need HTTPS or `localhost`.
- Android (Chrome, Vanadium): menu → Nainstalovat aplikaci / Install app
- iPhone (Safari): Sdílet → Přidat na plochu / Share → Add to Home Screen

## Soukromí aplikace / App privacy
Žádný server, analytika, cookies ani externí písma; CSP povoluje jen vlastní zdroje; data jsou v `localStorage`; zálohy přes „Zálohovat vše“.
No server, analytics, cookies or external fonts; CSP allows only own origin; data lives in `localStorage`; back up via “Back up all”.

## Licence / License
GNU General Public License v3.0 or later (`GPL-3.0-or-later`), viz / see [LICENSE](LICENSE).
Můžete aplikaci používat, upravovat a šířit, i komerčně. Pokud upravenou verzi zveřejníte, musí zůstat pod GPL se zdrojovým kódem.
You may use, modify and share it, commercially too. Published modified versions must stay GPL with source available.

Licence se vztahuje na kód a texty aplikace, ne na citované knihy. / The license covers the app’s code and text, not the referenced books.

## Zdroje / Sources
Juraj Bednár (Chain Camp talk on privacy cost-benefit analysis) · Max Hillebrand, *The Praxeology of Privacy* · Michael Bazzell, *Extreme Privacy* (5th ed.), *Mobile Devices*, *Linux Devices*, *VPNs and Firewalls*.
