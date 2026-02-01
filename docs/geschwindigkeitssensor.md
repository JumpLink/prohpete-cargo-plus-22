# Geschwindigkeitssensor (Speed Sensor)

Der Sensor am **Hinterrad** ist der Geschwindigkeitssensor (nicht der Drehzahlsensor). Hall-Sensor, typisch 3-Draht oder 4-polig CAN-BUS.

## Error 21 (Bafang: Speed sensor Error)

- **Bedeutung:** Controller erhält kein oder fehlerhaftes Signal vom Geschwindigkeitssensor.
- **Typische Ursachen:** Magnet fehlt/lockert/falsch ausgerichtet; Sensor defekt; Kabelbruch (besonders direkt am Sensor); Abstand Magnet–Sensor zu groß (> ca. 10 mm); Stecker korrodiert/lose.
- **Abstand:** Magnet innerhalb 15 mm, optimal 2–5 mm vom Sensor.

### Schnellprüfung

1. Magnet vorhanden? (Speiche, Bremsscheibe, Ritzelträger)
2. Abstand Magnet ↔ Sensor (2–5 mm ideal)
3. Kabel/Knick besonders am Sensorgehäuse prüfen (Kabelbruch)
4. Stecker (am Hinterbau/Motor) trennen, auf Korrosion prüfen
5. Multimeter: Versorgung ~5 V; Signal beim Raddrehen 0 V / ~5 V wechselnd

## Ersatzteil-Beschaffung

Öffentliche Pinouts/Ersatzteillisten für den AEG-Sensor gibt es praktisch nicht. Sinnvoll:

1. **Prophete / autorisierte Werkstatt:** Kundendienst (z. B. obi@prophete.de), MOT-Nr. vom Typenschild angeben. Ersatzteilversorgung laut Prophete bis 5 Jahre nach Kauf.
2. **Bafang-Kompatibilität:** Wegen Bafang-Basis des Controllers (u. a. Error 21) sind Bafang Speed Sensoren oft kompatibel. Entscheidend: **Stecker** (und ggf. Kabellänge). Protokoll CAN-BUS vs. UART prüfen.

### Zwei getestete/bestellte Alternativen

| | Zeekpowa (bereits bestellt) | windmeile Bafang SR SD021.01 |
|--|-----------------------------|------------------------------|
| **Modell** | Kein Modellname | **SR SD021.01** (Bafang-Typ) |
| **Anschluss** | 4-Pin CAN-BUS, Kabel zum Motor | 4-Pin CAN, **Indirect** – 20 cm Kabel, Anschluss über Kabelbaum |
| **Optik** | Standard Bafang | **Äußerlich wie Original** (zylindrisch, schwarz) |
| **Schutz** | – | IP65 |
| **Magnet-Abstand (Hersteller)** | 2–5 mm (allg. Empfehlung) | 15–20 mm (Bafang-Logo zum Laufrad) |
| **Preis (Stand Doku)** | ca. 20 € | ca. 17 € |

**Technisch kompatibel:** Beide sind Bafang CAN-BUS Speed-Sensoren mit 4-Pin-Stecker und gleichem Protokoll – sie sind untereinander austauschbar. Der Unterschied ist nur mechanisch (Kabellänge, „Indirect“ = kurzes Kabel in den Kabelbaum, „Direct“ = langes Kabel bis zum Motor).

**Empfehlung:** Der **windmeile SR SD021.01** sieht wie dein Original aus und hat eine klare Bafang-Typnummer – damit ist die Chance hoch, dass es derselbe oder ein baugleicher OEM-Sensor ist. „Indirect“ heißt nur: kurzes Kabel (20 cm), Stecker in den vorhandenen Kabelbaum (wie beim Original). Wenn du den Zeekpowa-Sensor noch nicht verbaut hast, ist der SR SD021.01 die sinnvollere Wahl. Funktioniert der Zeekpowa-Sensor bereits, musst du nicht wechseln.

### Erstes bestelltes Ersatzteil (Zeekpowa)

- **Bezeichnung:** Geschwindigkeitssensor für Bafang CAN-BUS (Zeekpowa/Amazon).
- **Kompatibel mit:** BBS01, BBS02, BBS-HD, M-Serie. 4-poliger Stecker (blau-tipped), 5 V, CAN-BUS.
- **Lieferumfang:** Sensor, Kabel, 2 Kabelbinder, Magnet-Halter für Speiche.
- **Montage:** Sensor am Rahmen (Kettenstrebe/Ausfallende), Magnet an Speiche, Abstand 2–5 mm. Stecker wie am Original – bei Problemen Protokoll (CAN vs. UART) prüfen.

### Alternative: windmeile Bafang SR SD021.01 (CAN Indirect)

- **Bezeichnung:** Bafang Geschwindigkeitssensor und Magnet SR SD021.01 (windmeile/Amazon), „CAN Indirect“.
- **Kompatibel mit:** Bafang CAN-Mittelmotoren, 4-Pin CAN. Anschluss **indirekt über Kabelbaum**, Kabel 20 cm.
- **Lieferumfang:** CAN Indirect Geschwindigkeitssensor, Magnet, Montagezubehör. IP65.
- **Montage:** Sensor an Kettenstrebe (Schraube oder Kabelbinder), Magnet an Speiche (Bafang-Logo zu den Speichen), Abstand 15–20 mm, Magnet mit Torx-Schraube (20 mm) mit Stift befestigen.
- **Hinweis:** In der Produktbeschreibung steht teils „3-Pin Stecker am Motor“ – gemeint ist der Anschluss über den Kabelbaum; das System ist 4-Pin CAN.

**Rechtlich:** Nur Reparatur/Ersatz. Manipulation an der 25-km/h-Begrenzung führt dazu, dass das Rad rechtlich kein Pedelec mehr ist.

## Kabelbruch

- **Sehr häufig:** Bruch direkt vor dem Sensorgehäuse.
- **Wenn genug Kabelstumpf (> 5–10 cm):** Bruchstelle entfernen, Adern (Plus, Minus, Signal) einzeln löten, jede Ader mit Schrumpfschlauch, danach Kabelmantel – wasserdicht ausführen (Außenbereich).
- **Wenn Bruch direkt am Sensor (< 5 cm):** Sensor tauschen (Ersatzteil siehe oben).

## Suchbegriffe für Ersatzteile

- Bafang Speed Sensor, E-Bike Hall Speed Sensor, Julet/Higo Speed Sensor
- Auf Steckertyp, Kabellänge (z. B. 40–60 cm Standard), 3-Draht bzw. 4-polig CAN achten; Magnet oft mit dabei.
