# Übergabe vivianglade.de – für Marcel Beriere

Stand: 29.10.2026 · erstellt mit Claude im Auftrag von Vivian Glade

## Was das ist
Eine fertige, statische Startseite (eine HTML-Datei, Bilder, Schriften). Kein PHP, keine Datenbank, keine Cookies,
keine externen Dienste (Schriften liegen lokal unter `fonts/`). Läuft auf jedem Webspace mit HTTPS.

```
index.html          Startseite inkl. Impressum und Datenschutz (aufklappbar im Fuß)
img/                Bilder (Originalarbeiten von Vivian Glade)
fonts/              Shantell Sans, Instrument Sans (SIL Open Font License, via Fontsource)
```

## Ausgangslage (geprüft am 29.10.2026)
- Unter https://vivianglade.de läuft eine **WordPress**-Seite (Theme „Music Star“, WooCommerce 7.1.2), Inhalte von Nov./Dez. 2022.
- Das Lovable-Projekt „Vivian Glade: Anders Denken“ (ID 53daabab-6e4b-46f4-b17d-c8e7f6f179e8) war für mich **nicht einsehbar**:
  es ist mit keinem GitHub-Repo verbunden, auf das ich Zugriff habe. HOSTING_HANDOFF.md, LEGAL_LAUNCH_GATE.md und
  scripts/export-static.mjs konnte ich daher nicht prüfen. Diese Seite ist eigenständig und ersetzt das Projekt nicht automatisch.
- DNS, MX und Mailzustellung für kontakt@vivianglade.de konnte ich von meiner Umgebung aus **nicht prüfen**.

## Vorschlag Livegang (nichts davon ist bisher passiert)
1. **WordPress sichern** (Dateien + Datenbank). Nichts löschen.
2. Diese Dateien in ein **neues Verzeichnis** legen, z. B. `/neu/` oder eine Subdomain `neu.vivianglade.de`, und per HTTPS testen.
3. Test: Seite lädt, Bilder da, Buttons „Projekt anfragen“ und „Arbeiten ansehen“ springen richtig, Formular öffnet E-Mail-Programm
   mit vorausgefüllter Nachricht an kontakt@vivianglade.de. **Eine Testmail an kontakt@vivianglade.de schicken und den Eingang bestätigen.**
4. Danach entweder
   - **a) temporäre 302-Weiterleitung** von `https://vivianglade.de/` auf die neue Seite (schnell, rückgängig zu machen), oder
   - **b) Dokumentenstamm** von vivianglade.de auf das neue Verzeichnis umstellen (WordPress bleibt im alten Ordner erhalten).
5. **DNS und MX-Einträge nicht ändern.** Mailrouting bleibt, wie es ist.
6. Optional später: `vivisview.site` (Squarespace) per Weiterleitung auf `https://vivianglade.de/` (macht Vivian selbst).

Beispiel 302 (Apache, .htaccess im WordPress-Stamm, nur Startseite):
```
RewriteEngine On
RewriteRule ^$ https://vivianglade.de/neu/ [R=302,L]
```

## Vor dem Livegang von Vivian/Marcel zu bestätigen
- [ ] Datenschutz: Hoster ergänzen (Name, Anschrift, ggf. Auftragsverarbeitung) und Server-Log-Speicherdauer. Der Text ist ein
      **Entwurf**, nicht rechtlich geprüft.
- [ ] Impressum: Angaben aus der alten Vivis-View-Seite übernommen (Braunstr. 22a, Kleinunternehmerin § 19 UStG). Aktuell?
- [ ] Musik-Stationen (rund 14 Veröffentlichungen 2002–2016; Radio Bremen, ARD, ZDF; Partnerschaften Indien, Südafrika,
      Italien, Israel) bestätigen.
- Fotos: nur Vivian selbst oder nicht erkennbare Personen; Ausschnitte bewusst so gewählt.
- [ ] Rehabilitations-Sketchnote: Foto fehlt noch.

## Technik
- Anfrage: kein Server-Formular. Das Formular erzeugt einen vorausgefüllten `mailto:`- bzw. `wa.me`-Link.
  Pflichtfelder: Name, Kontakt. Es wird nichts automatisch versendet und nichts gespeichert.
- Keine Cookies, kein Tracking, keine externen Requests beim Laden.
- SEO: Titel, Beschreibung, Canonical, Open-Graph-Bild (echtes Flipchart) gesetzt.
