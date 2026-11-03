# Bilance soukromí / Privacy Balance (PWA)

CZ: Cost-benefit analýza soukromí a anonymity. Průvodce pro nováčky, expertní režim pro profesionály, čeština i angličtina. Offline, nic neodesílá.
EN: Cost-benefit analysis for privacy and anonymity decisions. Guided mode for beginners, expert mode for professionals, Czech and English. Offline, sends nothing.

## Spuštění / Running

Statický web bez buildu / Static site, no build step:
- GitHub Pages, Netlify, Cloudflare Pages: nahrajte obsah složky / upload the folder.
- Lokálně / Locally: `python3 -m http.server 8000` → http://localhost:8000

Instalace (PWA) a offline fungují jen přes HTTPS nebo localhost. / Install and offline need HTTPS or localhost.

- Android (Chrome, Vanadium): menu → Nainstalovat aplikaci / Install app
- iPhone (Safari): Sdílet → Přidat na plochu / Share → Add to Home Screen

Při úpravě `index.html` zvyšte `CACHE` v `sw.js`. / Bump `CACHE` in `sw.js` after editing `index.html`.

Data: `localStorage` v prohlížeči; zálohy přes „Záloha (JSON)“ / „Zálohovat vše“. / Browser `localStorage`; back up with "Backup (JSON)" / "Back up all".

Zdroje / Sources: Juraj Bednár (Chain Camp talk), Max Hillebrand – The Praxeology of Privacy, Michael Bazzell – Extreme Privacy (5th ed.), Mobile Devices, Linux Devices, VPNs and Firewalls.
