# Technische Spezifikation

## Motor

| Spezifikation | Wert |
|---------------|------|
| Typ | AEG ComfortDrive Mittelmotor |
| Leistung | 250 W |
| Max. Drehmoment | 100 Nm |
| Unterstützung | bis 25 km/h (Pedelec) |

**Hinweis:** Äußerlich „AEG“, technisch Bafang-basiert (u. a. Fehlercode Error 21 = Bafang „Speed sensor Error“). OEM-typisch: gleiche Technik, anderes Branding.

## Sensoren

- **Drehmomentsensor:** Hauptsensor, regelt Unterstützung nach Trittkraft.
- **Geschwindigkeitssensor (Speed Sensor):** Hall-Sensor am Hinterrad (Rahmen, Kettenstrebe/Ausfallende). Magnet an Speiche/Bremsscheibe/Ritzelträger. Liefert Impulse für Anzeige und 25-km/h-Abschaltung. Kritisch für Sicherheit und Fehlercode Error 21.
- **Drehzahlsensor (Cadence):** Vermutlich Hall-Sensor am Tretlager/ im Motor. Erkennt Pedalumdrehungen, Motor nur bei Tritt.

## Display & Steuerung

- AEG LCD-Display
- 5 Unterstützungsstufen, Schiebehilfe, ProKey (Akku-Entnahme), USB-Anschluss

### Datenkabel Display ↔ Controller (identifiziert)

Am verbauten **Datenkabel** (Display zum Controller) steht:

- **Aufkleber/QR-Code:** `DPC211CQ10101.0  PD051215  DP  C211.C  1.0  707Q1U9160097`
- **Hersteller:** BAFANG (auf dem Aufkleber)
- **Typ:** **DP C211** – Bafang-Display-Serie, Revision 1.0; **C211 erscheint nicht** in Bafangs aktueller öffentlicher Modellliste (dort z. B. C171, C221, C231). Wahrscheinlich **OEM-/Variantenbezeichnung** (z. B. für Prophete/AEG), technisch C-Serie CAN.
- **Stecker:** **5-Pin, rund, grüner Innenstecker** – typisch Bafang/HIGO für Display–Controller (CAN). Pin-Anordnung: 1 Mittelpin, 4 Pins im Quadrat; Kerbe zur Orientierung.

**Schlussfolgerung:** Das System nutzt ein **Bafang CAN-BUS Display-Kabel**. Ob ein Programmierkabel passt, hängt von der **Steckerform** ab: Am Rad ist der Stecker **rund** (grün). Manche BBS-CAN-Programmierkabel haben einen **Dreikant-** (dreieckigen) Stecker – **nicht zwingend baugleich**. Vor dem Kauf oder Anschluss **Steckerform und Pin-Anordnung vergleichen**; bei Abweichung passt es ggf. nicht oder nur mit Adapter.

## Übersicht

| Komponente | Details |
|------------|---------|
| Motor | AEG ComfortDrive, 250 W, 100 Nm |
| Geschwindigkeitssensor | Hall-Sensor am Hinterrad |
| Drehzahlsensor | Am Tretlager / im Motor |
| Display | AEG LCD, 5 Stufen, Schiebehilfe, ProKey, USB |
| Limit | 25 km/h (Pedelec) |
