# HeTec Provisionsabrechnung

PWA für die monatliche Provisionsabrechnung (o2).

1. Performance-Excel ablegen
2. Telefonie-Excel (WOBIS) ablegen
3. DNE-Excel (Werbeversprechen, Spalte A „Nachname Vorname“, Spalte D %) ablegen – ersetzt den Werbeversprechen-Wert
4. Prüfen, Sonderprovision / Shopleiter / Gutschriften eintragen
5. „Provision generieren“ (ZIP) oder „Provisionen per E-Mail senden“ (Outlook-Entwurf)

## Historie

Button „Historie“ (oben): Tabelle aller Provisionen je Mitarbeiter und Monat, mit Ø je Mitarbeiter, Ø je Monat und Gesamtdurchschnitt. Filter nach Jahr, Excel-Export.

- Einträge entstehen automatisch bei „Provision generieren“, „Provisionen per E-Mail senden“ und dem E-Mail-Entwurf je Mitarbeiter, oder manuell über „In Historie speichern“.
- Bereits versendete Abrechnungen (Versandnachweise) werden einmalig übernommen.
- Zellen anklicken = Betrag ändern oder löschen. Unten können alte Monate nachgetragen werden.
- Die Historie ist Teil der Sicherung (JSON).

Alle Daten bleiben lokal im Browser (localStorage). Keine Daten werden hochgeladen, die Historie liegt nicht im Repository.
