# Geschwindigkeitssensor (Speed Sensor)

Sensor am **Hinterrad** = Geschwindigkeitssensor (nicht Drehzahlsensor). Hall-Sensor, typisch 3-Draht oder 4-polig CAN-BUS.

## Error 21 (Bafang: Speed sensor Error)

- **Bedeutung:** Controller erhält kein oder fehlerhaftes Signal.
- **Ursachen:** Magnet fehlt/lockert/falsch; Sensor defekt; Kabelbruch (oft direkt am Sensor); Abstand Magnet–Sensor > ca. 10 mm; Stecker korrodiert/lose.
- **Abstand:** Magnet innerhalb 15 mm, optimal 2–5 mm.

**Schnellprüfung:** Magnet da? Abstand 2–5 mm? Kabel/Knick am Sensor prüfen. Stecker trennen, auf Korrosion prüfen. Multimeter: Versorgung ~5 V; Signal beim Raddrehen 0 V / ~5 V wechselnd.

## Ersatzteil-Beschaffung

Öffentliche Pinouts für den AEG-Sensor gibt es praktisch nicht. **Prophete** (obi@prophete.de, MOT-Nr. angeben) oder **autorisiertes Service**; Ersatzteilversorgung laut Prophete bis 5 Jahre. Wegen Bafang-Basis (Error 21) sind Bafang Speed Sensoren oft kompatibel – entscheidend: **Stecker** und ggf. Kabellänge.

### Zwei Alternativen (Bafang CAN)

| | Zeekpowa | windmeile SR SD021.01 |
|--|----------|------------------------|
| **Typ** | Bafang CAN-BUS, 4-Pin | Bafang CAN Indirect, 4-Pin, 20 cm Kabel |
| **Optik** | Standard | Äußerlich wie Original (zylindrisch, schwarz) |
| **Schutz** | – | IP65 |
| **Magnet-Abstand** | 2–5 mm | 15–20 mm (Bafang-Logo zum Laufrad) |
| **Preis (Stand Doku)** | ca. 20 € | ca. 17 € |

Beide **technisch austauschbar** (gleiches Protokoll, 4-Pin CAN). **Empfehlung:** windmeile SR SD021.01 sieht wie Original aus, hat Bafang-Typnummer – sinnvoll, wenn Zeekpowa noch nicht verbaut. Lieferumfang: Sensor, Kabel, Magnet, Montagezubehör. Montage: Sensor am Rahmen (Kettenstrebe/Ausfallende), Magnet an Speiche, Abstand wie Hersteller.

**Rechtlich:** Nur Reparatur/Ersatz. Manipulation an der 25-km/h-Begrenzung = rechtlich kein Pedelec mehr.

## Kabelbruch

- **Häufig:** Bruch direkt vor dem Sensorgehäuse.
- **Reparatur möglich** (> 5–10 cm Kabelstumpf): Bruchstelle entfernen, Adern (Plus, Minus, Signal) einzeln löten, Schrumpfschlauch pro Ader, Kabelmantel wasserdicht.
- **Bruch direkt am Sensor (< 5 cm):** Sensor tauschen.

**Suchbegriffe:** Bafang Speed Sensor, E-Bike Hall Speed Sensor, Julet/Higo Speed Sensor; auf Steckertyp, Kabellänge (z. B. 40–60 cm), 3-Draht/4-polig CAN achten.
