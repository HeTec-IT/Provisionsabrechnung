# HeTec Provisionsabrechnung

PWA für die monatliche Provisionsabrechnung (o2).

1. Performance-Excel ablegen
2. Telefonie-Excel (WOBIS) ablegen
3. DNE-Excel (Werbeversprechen, Spalte A „Nachname Vorname“, Spalte D %) ablegen – ersetzt den Werbeversprechen-Wert
4. Prüfen, Sonderprovision / Shopleiter / Gutschriften eintragen
5. „Provision generieren“ (ZIP) oder „Per E-Mail senden“ (Outlook-Entwurf). Pro Mitarbeiter: PDF, E-Mail, Unterschrift; „⋯“ öffnet Bearbeiten und Optionen (Azubi/TZ, Einstiegsschwelle, Shopleiter).

## Unterschrift am Handy

Button „Unterschrift (QR)“ je Mitarbeiter: Der Mitarbeiter scannt den QR-Code, sieht seine Abrechnung, unterschreibt mit dem Finger und schickt das unterschriebene PDF per Teilen-Menü zurück.

- Kein Server: Die Abrechnungsdaten stehen komprimiert im Link (Teil nach `#`, wird nie an einen Server gesendet). Interne Notizen sind nicht enthalten.
- Das PDF entsteht auf dem Handy. Die Unterschrift steht im grünen Feld „Auszahlungsbetrag“ (Seite 1) und auf der Zeile „Arbeitnehmer“ (Seite 2), dazu Datum, Uhrzeit und Prüfcode.
- Automatischer Rückweg (optional, nur über dein eigenes GitHub): Privates Repository anlegen und ein Fine-grained Token (nur dieses Repo, „Contents: Read and write“) im QR-Dialog eintragen; beides bleibt nur im Browser. Das Token steckt im QR-Link, das Handy legt die mit AES-256-GCM verschlüsselte Unterschrift (Schlüssel nur im Link nach `#`) als Datei im privaten Repo ab. Das Dashboard holt sie alle 15 Sekunden ab, entschlüsselt sie und löscht die Datei. Es gibt keinen weiteren Dienst.
- Manueller Weg, zurück im Dashboard: „Unterschriften einlesen“ (oben, mehrere PDFs möglich) oder im QR-Dialog „Unterschriebenes PDF einlesen“. Die Unterschrift steckt als Metadaten im PDF und wird dem Mitarbeiter zugeordnet.
- Danach enthält der Button „PDF ✍“ die Unterschrift; sie ist auch im ZIP („Provision generieren“) und in der E-Mail je Mitarbeiter (Haken „Mit Unterschrift“) enthalten.
- Ändert sich der Auszahlungsbetrag nach der Unterschrift, gilt sie nicht mehr (Hinweis in der Übersicht, PDF ohne Unterschrift).
- Der Prüfcode wird aus den Abrechnungsdaten berechnet. Stimmen Dialog und PDF nicht überein, wurde der Link verändert.
- Es handelt sich um eine einfache elektronische Signatur.

## Historie

Button „Historie“ (oben): Tabelle aller Provisionen je Mitarbeiter und Monat, mit Ø je Mitarbeiter, Ø je Monat und Gesamtdurchschnitt. Filter nach Jahr, Excel-Export.

- Einträge entstehen automatisch bei „Provision generieren“, „Provisionen per E-Mail senden“ und dem E-Mail-Entwurf je Mitarbeiter, oder manuell über „In Historie speichern“.
- Bereits versendete Abrechnungen (Versandnachweise) werden einmalig übernommen.
- Zellen anklicken = Betrag ändern oder löschen. Unten können alte Monate nachgetragen werden.
- „Historie importieren“ lädt eine JSON-Datei mit alten Monaten (je Bereich eine Datei, vorhandene Einträge werden nicht überschrieben).
- `historie-seed.enc.json` enthält die bisherigen Monate nur verschlüsselt (AES-256-GCM). Beim ersten Öffnen fragt die App einmal nach dem Passwort und legt die Historie lokal im Browser ab. Das Passwort steht nicht im Repository.
- Die Historie ist Teil der Sicherung (JSON).

Alle Daten bleiben lokal im Browser (localStorage). Keine Daten werden hochgeladen, die Historie liegt nicht im Repository.
