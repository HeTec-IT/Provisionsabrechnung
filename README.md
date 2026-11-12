# HeTec Provisionsabrechnung

PWA für die monatliche Provisionsabrechnung (o2).

1. Performance-Excel ablegen
2. Telefonie-Excel (WOBIS) ablegen
3. DNE-Excel (Werbeversprechen, Spalte A „Nachname Vorname“, Spalte D %) ablegen – ersetzt den Werbeversprechen-Wert
4. Prüfen, Sonderprovision / Shopleiter / Gutschriften eintragen
5. „Provision generieren“ (ZIP) oder „Provisionen per E-Mail senden“ (Outlook-Entwurf)

## Unterschrift am Handy

Button „Unterschrift (QR)“ je Mitarbeiter: Der Mitarbeiter scannt den QR-Code, sieht seine Abrechnung, unterschreibt mit dem Finger und schickt das signierte PDF per Teilen-Menü zurück.

- Kein Server: Die Abrechnungsdaten stehen komprimiert im Link (Teil nach `#`, wird nie an einen Server gesendet). Interne Notizen sind nicht enthalten.
- Das signierte PDF entsteht auf dem Handy (Unterschrift auf Seite 2, Datum, Uhrzeit, Prüfcode).
- Der Prüfcode wird aus den Abrechnungsdaten berechnet und steht im Dialog und im PDF. Stimmen sie nicht überein, wurde der Link verändert.
- „Unterschrift erhalten ✓“ markiert den Mitarbeiter in der Übersicht.
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
