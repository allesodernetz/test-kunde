# Kunden-Vorlage: Visitenkarten-Website

Statische One-Pager-Vorlage (Jekyll) mit Admin-Bereich über **Pages CMS**.
Läuft auf **GitHub Pages** (baut Jekyll automatisch, keine Build-Pipeline nötig) oder **Netlify**.

## Was drin ist
| Datei | Zweck |
|---|---|
| `_data/site.yml` | **Alle Inhalte** (Texte, Bilder, Öffnungszeiten, Kontakt, Farbe). Das bearbeitet der Kunde. |
| `.pages.yml` | Konfiguration des Admin-Bereichs (welche Felder der Kunde sieht). |
| `index.html`, `_layouts/default.html` | Aufbau der Seite. Pro Kunde nur anfassen, wenn er etwas Besonderes will (= Aufpreis). |
| `impressum.md`, `datenschutz.md` | **Platzhalter.** Kunde erstellt die Texte selbst (Generator/Anwalt). |
| `admin/index.html` | `/admin` leitet zum Login von Pages CMS weiter. |
| `assets/css/style.css` | Design. Systemschriften, kein Google Fonts, Dark Mode inklusive. |
| `netlify.toml` | Nur bei Netlify-Hosting nötig. |

Bewusst **nicht** drin: Cookies, Tracking, Google Fonts, eingebettete Karten/Videos, Cookie-Banner (nicht nötig, solange das so bleibt).

## Neuer Kunde in ca. 60–90 Minuten
1. **Konten des Kunden** (gemeinsam im Termin oder per Anleitung): GitHub-Konto *auf den Kunden*, Domain beim Kunden-Provider. Du wirst als Collaborator auf sein Repo eingeladen.
2. Diese Vorlage ins Kunden-Repo kopieren (GitHub: „Use this template“, wenn du sie als Template-Repo anlegst).
3. `_config.yml`: `title` und `url` eintragen.
4. `_data/site.yml` mit den gelieferten Texten/Fotos füllen, Akzentfarbe setzen, Fotos nach `assets/images/` (vorher auf max. ~1600 px verkleinern).
5. **GitHub Pages aktivieren**: Repo → Settings → Pages → „Deploy from a branch“ → `main` / root.
6. **Domain**: Settings → Pages → Custom domain eintragen, beim Provider DNS setzen (A-Records + CNAME laut GitHub-Doku), „Enforce HTTPS“ anhaken.
7. **Admin-Bereich**: auf app.pagescms.org mit GitHub einloggen, Pages-CMS-GitHub-App für das Repo installieren, Kunden-E-Mail als *Collaborator* einladen. Der Kunde braucht dafür **kein** GitHub-Konto.
8. Kunde liefert **Impressum + Datenschutz** (Generator). Du fügst sie ein. Erst dann live schalten.
9. Abnahme-Check (siehe unten), Video-Einweisung (10 Min.), Restrechnung.

## Relaunch: Kunde hat schon eine Website
1. Vorher prüfen: Google „Branche + Stadt“ (steht er auf Seite 1?) und `site:alte-domain.de` (wie viele Seiten sind bei Google?).
2. **Gleiche Domain behalten.**
3. Alle alten Adressen sammeln (`alte-domain.de/sitemap.xml` oder Menü durchklicken) und in `_redirects` eintragen: alt → neu, `301`.
4. Wichtige Texte übernehmen (Leistungen, Ort, Stadtteile) – nur Füllsätze kürzen.
5. Nach Livegang jede alte Adresse einmal aufrufen: muss auf die neue Seite springen, keine Fehlerseite.
6. Wenn der Kunde Google Search Console hat: Lesezugriff erbitten, nach 2–4 Wochen auf Fehler prüfen.
7. Vertrag: keine Garantie für Google-Platzierungen.

## Abnahme-Check vor Livegang
- [ ] Impressum und Datenschutz echte Texte, keine Platzhalter mehr
- [ ] Alle Links/Telefon/E-Mail getestet (auch am Handy)
- [ ] HTTPS aktiv, Domain mit und ohne `www` funktioniert
- [ ] Bilder komprimiert, Alt-Texte ok
- [ ] Kontaktformular nur mit Web3Forms-Key **und** Web3Forms-Abschnitt in der Datenschutzerklärung; einmal Testnachricht schicken
- [ ] Kunde hat sich einmal selbst im Admin eingeloggt und etwas geändert
- [ ] Bei Relaunch: alle alten Adressen leiten per 301 weiter

## Hinweise
- **GitHub Pages und kommerzielle Nutzung:** GitHub schließt Pages für Online-Shops/kommerzielle Transaktionen aus. Für eine reine Info-Seite ist das verbreitet, aber eine Grauzone. Netlify (Free) ist die saubere Alternative.
- **Kontaktformular:** Läuft über Web3Forms (kostenlos, ohne Branding). Key auf web3forms.com mit der Kunden-E-Mail anlegen, in `_data/site.yml` bei `web3forms_key` eintragen, `kontaktformular: true`.
- **Lokale Vorschau:** `bundle install && bundle exec jekyll serve` (Ruby nötig).
