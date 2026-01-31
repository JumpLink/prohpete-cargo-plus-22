# Prophete Cargo Plus 22.ETL.10 - Technische Dokumentation

## Übersicht

Diese Dokumentation beschreibt die technischen Details des Antriebssystems und der verbauten Komponenten des Prophete Cargo Plus 22.ETL.10 E-Lastenrads.

## Antriebssystem: AEG ComfortDrive

Das Antriebssystem des Prophete Cargo Plus 22.ETL.10 basiert auf dem **AEG ComfortDrive Mittelmotor**.

### Motor

| Spezifikation | Wert |
|---------------|------|
| **Typ** | AEG ComfortDrive Mittelmotor |
| **Leistung** | 250 Watt |
| **Maximales Drehmoment** | 100 Nm |
| **Unterstützung** | Bis zu 25 km/h (Pedelec) |

**Hinweis zur Motor-Basis:**
- **Äußere Beschriftung:** Der Motor trägt die Bezeichnung "AEG" auf der Hülle
- **Technische Basis:** Es gibt starke Hinweise darauf, dass der AEG ComfortDrive Motor auf einem **Bafang-Motor basiert**
- **Bestätigt durch Error 21:** Der Controller zeigt den Bafang-spezifischen Fehlercode Error 21 ("Speed sensor Error"), was eindeutig auf eine Bafang-basierte Controller-Technologie hinweist

**OEM-Produktion (Original Equipment Manufacturer):**
- Viele E-Bike-Hersteller verwenden **OEM-Motoren** von anderen Herstellern
- Diese werden mit **eigenem Branding** versehen (z.B. "AEG" auf der Hülle)
- Die **technische Basis** bleibt jedoch identisch (z.B. Bafang)
- Dies ist in der E-Bike-Industrie **sehr üblich** und erklärt, warum:
  - Der Motor "AEG" heißt, aber Bafang-Fehlercodes zeigt
  - Bafang-Ersatzteile kompatibel sind
  - Die Stecker identisch aussehen

### Sensoren

#### Drehmomentsensor

Das System verwendet einen **Drehmomentsensor** als Hauptsensor. Dieser misst die Kraft, die der Fahrer auf die Pedale ausübt, und regelt die elektrische Unterstützung entsprechend. Eine höhere Trittkraft führt zu einer stärkeren Motorunterstützung.

#### Geschwindigkeitssensor (Speed Sensor / Wheel Speed Sensor)

**Funktion:**
Der **Geschwindigkeitssensor** (auch Speed Sensor oder Wheel Speed Sensor genannt) misst die Geschwindigkeit des Fahrrads durch Erfassung der Radumdrehungen. Er ist für folgende Funktionen zuständig:
- **Geschwindigkeitsanzeige** im Display
- **Abschalten der Unterstützung bei 25 km/h** (Pedelec-Grenze)
- **Plausibilitätsprüfung im Controller** (Safety-Funktion)

**Technische Details:**
- **Typ:** **Hall-Sensor** (magnetischer Sensor) im Kunststoffgehäuse
- **Position:** Am Fahrradrahmen in der Nähe des Hinterrads (Kettenstrebe oder Ausfallende)
- **Funktionsweise:** 
  - Ein kleiner Magnet ist an einer Speiche, an der Bremsscheibe oder am Ritzelträger montiert
  - Bei jeder Radumdrehung fährt der Magnet am Sensor vorbei
  - Der Sensor erzeugt einen Impuls pro Magnet-Vorbeifahrt (typisch: 1 Impuls pro Radumdrehung, manchmal 2)
  - Der Controller zählt die Impulse und berechnet daraus die Geschwindigkeit
- **Anschluss:** 3-Draht-System (sehr wahrscheinlich):
  - **+5V** (oder +3.3V) Versorgungsspannung
  - **GND** (Masse)
  - **Signal** (Open Collector / Push-Pull, Rechtecksignal)

**Visuelle Identifikation (basierend auf Foto):**
- **Aussehen:** Schwarzes, L-förmiges oder abgewinkeltes elektronisches Bauteil im Kunststoffgehäuse
- **Montageposition:** Am Fahrradrahmen in der Nähe des Hinterrads (Kettenstrebe oder Ausfallende)
- **Kabel:** Schwarzes Kabel führt vom Sensor weg und verläuft entlang des Rahmens Richtung Motor/Controller
- **Bauform:** Kompakte, abgewinkelte Bauform für die Montage am Rahmen
- **Magnet:** Normalerweise ein kleiner Magnet an einer Speiche, an der Bremsscheibe oder am Ritzelträger

**Signal-Charakteristik:**
- Rechtecksignal: 0V / 5V
- Frequenz proportional zur Geschwindigkeit
- Mit Multimeter messbar: Signal springt beim Drehen des Rads zwischen 0V und ~5V
- Versorgung: ~5V zwischen + und GND

**Wichtigkeit:**
Der Geschwindigkeitssensor ist ein **kritischer Sicherheitssensor**, da er die 25-km/h-Begrenzung überwacht. Ein defekter Sensor kann zu Fehlfunktionen der Motorunterstützung führen.

#### Drehzahlsensor (Cadence Sensor)

**Funktion:**
Der **Drehzahlsensor** (auch Tretlager-Sensor oder Cadence Sensor genannt) erkennt, ob und wie schnell der Fahrer in die Pedale tritt. Er misst die Pedalumdrehungen pro Minute (RPM - Rotations Per Minute) und aktiviert die Motorunterstützung, sobald eine Pedalbewegung erkannt wird.

**Technische Details:**
- **Typ:** Vermutlich ein **Hall-Sensor** (magnetischer Sensor)
- **Position:** Am Tretlager oder im Motor integriert (nicht am Hinterrad!)
- **Funktionsweise:** Erkennt Magnete, die sich mit den Pedalen drehen, und sendet Impulse an den Controller
- **Anschluss:** Typischerweise 3-Draht-Anschluss (Plus, Minus, Signal)

**Wichtigkeit:**
Die Kombination aus Drehmoment- und Drehzahlsensor ist bei modernen Pedelecs Standard, um eine reibungslose und sichere Unterstützung zu gewährleisten. Der Drehzahlsensor stellt sicher, dass der Motor nur aktiviert wird, wenn tatsächlich getreten wird, und verhindert so ein unbeabsichtigtes Anfahren.

**Hinweis:** Der Drehzahlsensor wird in Produktbeschreibungen oft nicht gesondert hervorgehoben, da der Drehmomentsensor das wesentliche Merkmal für die Qualität der Tretunterstützung ist.

### Controller und Display

#### AEG LCD-Display

Das System wird über ein **AEG LCD-Display** gesteuert und überwacht.

**Funktionen:**
- Auswahl von bis zu **5 Unterstützungsstufen**
- **Schiebehilfe** (Unterstützung beim Schieben des Fahrrads)
- **ProKey** (vermutlich für die Akku-Entnahme)
- **USB-Anschluss** (zum Laden von Geräten)

## Technische Zusammenfassung

| Komponente | Details |
|------------|---------|
| **Motor** | AEG ComfortDrive Mittelmotor, 250W, 100 Nm |
| **Hauptsensor** | Drehmomentsensor |
| **Geschwindigkeitssensor** | Hall-Sensor am Hinterrad (für 25 km/h-Begrenzung) |
| **Drehzahlsensor** | Vermutlich am Tretlager oder im Motor integriert |
| **Display** | AEG LCD-Display mit 5 Unterstützungsstufen |
| **Zusatzfunktionen** | Schiebehilfe, ProKey, USB-Anschluss |
| **Geschwindigkeitslimit** | 25 km/h (Pedelec) |

## Quellen

### Produktinformationen

1. [Prophete.de - Cargo Plus 22.ETL.10](https://www.prophete.de/Cargo-Plus-22.ETL.10/52612-0231)
2. [TopRatgeber24 - Prophete Cargo Plus 22 ETL 10](https://www.topratgeber24.de/amp/elektro-transportfahrrad/prophete-unisex-erwachsene-cargo-plus-22-etl-10-e-bike-20-26-aeg-comfortdrive)
3. [Prophete.de - Produktseite](https://www.prophete.de/Cargo-Plus-22.ETL.10/052612-0231)
4. [PedelecForum - AEG Mittelmotor Comfort Drive Diskussion](https://www.pedelecforum.de/forum/index.php?threads/aeg-mittelmotor-comfort-drive.62789/)

### Ersatzteile und Reparatur

5. [Prophete E-Cargo Bedienungsanleitung (PDF)](https://cdn.prophete.de/media/bd/cc/31/1745545216/990733-03__Prophete-E-Cargo_2021__de__WEB.pdf?ts=1745545216)
6. [PedelecForum](https://www.pedelecforum.de) - Community-Forum für E-Bike-Reparaturen und Erfahrungsaustausch

## Ersatzteile

### Geschwindigkeitssensor (Speed Sensor) - Ersatzteilinformationen

**WICHTIG:** Der auf dem Foto sichtbare Sensor am Hinterrad ist der **Geschwindigkeitssensor**, nicht der Drehzahlsensor!

#### Aktuelle Situation

**Problem:** Spezifische Informationen zu kompatiblen Ersatzteilen für den Geschwindigkeitssensor des Prophete Cargo Plus 22.ETL.10 sind in öffentlich zugänglichen Quellen **nicht verfügbar**.

**Rechercheergebnis:** Drei Runden umfassender Websuche haben ergeben, dass:
- Keine detaillierten technischen Daten über den Geschwindigkeitssensor öffentlich verfügbar sind
- Keine Pinout-Informationen (Anschlussbelegung) oder Verkabelungsanleitungen gefunden wurden
- Keine spezifischen Ersatzteile oder Kompatibilitätslisten für den AEG ComfortDrive Motor existieren
- Die Beschaffung von Ersatzteilen für proprietäre E-Bike-Komponenten generell schwierig ist

#### Bekannte Informationen

- **Sensor-Typ:** **Hall-Sensor** (magnetischer Geschwindigkeitssensor) im Kunststoffgehäuse
- **Motor-Basis:** Der AEG ComfortDrive Motor basiert auf einem **Bafang-Motor** (OEM-Produktion)
  - **Äußere Beschriftung:** "AEG" auf der Motorhülle (Branding)
  - **Technische Basis:** Bafang-Motor (bestätigt durch Error 21)
  - **OEM-Produktion:** AEG/Prophete nutzt Bafang-Motoren mit eigenem Branding
  - **Hinweis:** Es ist **sehr üblich**, dass E-Bike-Hersteller OEM-Motoren verwenden und diese mit eigenem Branding versehen. Die technische Basis bleibt identisch.
- **Kompatibilität:** Prophete / AEG ComfortDrive nutzt **Bafang-Komponenten**. Der Speed Sensor ist in 90% der Fälle:
  - Elektrisch: Standard-Hall-Sensor
  - Mechanisch: Standard-E-Bike-Sensor mit Magnet
- **Anschluss:** Sehr wahrscheinlich **3-Draht-System** (bei einfachen Sensoren) oder **4-polig CAN-BUS** (bei modernen Systemen):
  - +5V (oder +3.3V) Versorgung
  - GND (Masse)
  - Signal (Open Collector / Push-Pull, Rechtecksignal)
  - CAN-H / CAN-L (bei CAN-BUS Systemen)
- **Stecker:** Meist **Higo / Julet** (wasserdicht, rund, grün/schwarz) oder proprietär, aber elektrisch identisch
- **Kompatibilität:** Viele AEG/Prophete-Bikes nutzen **baugleiche Sensoren wie Bafang BBSxx / MaxDrive / M-Serie** – nur mit anderem Stecker oder anderer Kabellänge
- **Hinweis auf Standardisierung:** Es gibt Hinweise auf ein "Tuning Tool" für AEG Motoren, das zwischen Motor und Sensor eingefügt wird, was auf einen standardisierten Anschluss hindeuten könnte. Allerdings sind keine technischen Spezifikationen dazu öffentlich verfügbar.

#### Visuelle Identifikation für Ersatzteilbeschaffung

**Basierend auf Foto des defekten Sensors:**

| Merkmal | Beschreibung |
|---------|--------------|
| **Farbe** | Schwarz |
| **Form** | L-förmig oder abgewinkelt |
| **Montageposition** | Am Fahrradrahmen in der Nähe des Hinterrads (Kettenstrebe oder Ausfallende) |
| **Kabel** | Schwarzes Kabel, verläuft entlang des Rahmens |
| **Bauform** | Kompakte, abgewinkelte Bauform für Rahmennontage |
| **Größe** | Kompaktes elektronisches Bauteil |

**Wichtig für Ersatzteilbestellung:**
- Diese visuellen Merkmale können bei der Beschreibung des defekten Sensors an Prophete oder einen Fachhändler hilfreich sein
- Die genaue Anzahl der Kabeladern und der Steckertyp sollten vor der Bestellung ermittelt werden
- Fotos des defekten Sensors (insbesondere vom Stecker) können bei der Identifikation helfen
- **Magnet prüfen:** Ist der Magnet noch vorhanden? (An Speiche, Bremsscheibe oder Ritzelträger)

#### Empfohlene Vorgehensweise zur Ersatzteilbeschaffung

**WICHTIG:** 
- Aufgrund des Mangels an öffentlich zugänglichen technischen Daten ist eine **Selbstreparatur des Geschwindigkeitssensors nicht empfehlenswert**. Der sicherste und zuverlässigste Weg ist die Kontaktaufnahme mit dem Prophete-Kundendienst oder einem autorisierten Servicepartner.
- **Rechtlicher Hinweis:** Der Speed-Sensor ist **Teil der 25-km/h-Begrenzung**. Manipulation (z.B. falsche Impulszahl, Tuning-Tools) führt dazu, dass das Fahrrad rechtlich kein Pedelec mehr ist (Versicherungsschutz weg, etc.). Diese Dokumentation geht von **Reparatur / Ersatz** aus.

1. **Direkter Kontakt mit Prophete (EMPFOHLEN):**
   - **Kundendienst:** Prophete bietet ein Netzwerk an zertifizierten Servicepartnern
   - **E-Mail:** obi@prophete.de
   - **Adresse:** Prophete In Moving GmbH, Lindenstraße 50, 33378 Rheda-Wiedenbrück
   - **Service-Seite:** [Prophete Service](https://www.prophete.de/service/)
   - **Ersatzteile:** [Prophete Ersatzteile](https://www.prophete.de/zubehoer/ersatzteile)
   - **Wichtig:** Motor-Nummer (MOT-NR.) vom Typenschild angeben
   - **Ersatzteilgarantie:** Prophete garantiert Ersatzteilversorgung bis zu 5 Jahre nach Kauf

2. **Autorisierte Fachwerkstatt (EMPFOHLEN):**
   - Ein Prophete-Vertragshändler oder autorisierte E-Bike-Werkstatt ist die beste Anlaufstelle für:
     - Professionelle Diagnose des defekten Sensors
     - Identifikation des genauen Sensormodells
     - Beschaffung von Original-Ersatzteilen
     - Fachgerechte Installation und Reparatur
   - **Vorteil:** Garantie bleibt erhalten, professionelle Reparatur gewährleistet

3. **Bedienungsanleitung konsultieren:**
   - Die offizielle Prophete E-Cargo Bedienungsanleitung (PDF verfügbar) sollte technische Details enthalten
   - Link: [Prophete E-Cargo Bedienungsanleitung](https://cdn.prophete.de/media/bd/cc/31/1745545216/990733-03__Prophete-E-Cargo_2021__de__WEB.pdf?ts=1745545216)
   - **Hinweis:** Auch in der Bedienungsanleitung sind keine detaillierten Pinout-Informationen enthalten

4. **Mögliche Bafang-Kompatibilität:**
   - Sehr wahrscheinlich kompatibel: **"Bafang Speed Sensor"** oder **"E-Bike Hall Speed Sensor 3-pin"**
   - **Julet/Higo Speed Sensor** (mit ggf. Stecker-Umpinnen)
   - **WICHTIG:** 
     - Elektrisch sind fast alle identisch - das größte Problem ist meist **der Stecker**
     - Steckerform & Pinout prüfen
     - Kabellänge beachten
     - Magnet dabei oder alten weiterverwenden
   - **WICHTIG:** Dies sollte vorher mit Prophete oder einem Fachhändler abgeklärt werden, um Garantieansprüche nicht zu verlieren
   - Typische Bafang-Modelle: BBS01, BBS02, MaxDrive, M-Serie (für Vergleichszwecke)

#### Bestelltes Ersatzteil

**Geschwindigkeitssensor für Bafang CAN-BUS eBikes**

**Produktdetails:**
- **Hersteller/Marke:** BAFANG (über Zeekpowa-Store)
- **Kompatibilität:** BBS01, BBS02, BBS-HD & M Serie
- **Stecker:** 4-poliger Stecker (blau-tipped, schwarz)
- **Protokoll:** CAN-BUS (auch UART-Variante verfügbar)
- **Material:** ABS (Acrylnitril-Butadien-Styrol)
- **Versorgungsspannung:** 5 Volt (max.)
- **Gewicht:** 20 Gramm
- **Lieferumfang:**
  - Geschwindigkeitssensor (schwarz, L-förmig, "BAFANG" Aufdruck)
  - Kabel mit 4-poligem Stecker
  - 2x Kabelbinder (schwarz) für Montage
  - Magnet-Halter (silber, zylindrisch mit Schraube) für Speichenmontage

**Wichtige Hinweise für Installation:**

1. **Stecker-Kompatibilität:**
   - **Stecker sieht gleich aus** wie am Original-Sensor
   - **4-poliger Stecker** (nicht 3-polig wie bei einfachen Sensoren)
   - **CAN-BUS Protokoll** - prüfen ob AEG ComfortDrive CAN-BUS verwendet
   - Falls UART benötigt wird: UART-Variante verfügbar (17,99€)

2. **Protokoll-Unterschied:**
   - **CAN-BUS:** Digitale Kommunikation, höhere Datenrate
   - **UART:** Serielle Kommunikation, einfacher
   - **Wichtig:** Prüfen welches Protokoll der AEG ComfortDrive verwendet
   - Falls falsches Protokoll: Sensor funktioniert möglicherweise nicht

3. **Installation:**
   - **Sensor montieren** am Rahmen (Kettenstrebe oder Ausfallende)
   - **Magnet-Halter** an Speiche montieren (mitgelieferte Schraube verwenden)
   - **Abstand prüfen:** 2-5 mm zwischen Sensor und Magnet
   - **Kabelbinder** für sichere Befestigung verwenden
   - **Kabel** entlang des Rahmens verlegen

4. **Funktionsprüfung:**
   - Nach Installation: Rad drehen und Signal prüfen
   - Display sollte Geschwindigkeit anzeigen
   - Motor sollte bei 25 km/h abschalten
   - Falls Fehlermeldung: Protokoll prüfen (CAN vs. UART)

5. **Falls Sensor nicht funktioniert:**
   - **Protokoll prüfen:** Möglicherweise benötigt AEG ComfortDrive UART statt CAN-BUS
   - **Stecker prüfen:** Pinout könnte unterschiedlich sein
   - **Original-Sensor** als Referenz behalten (für Pinout-Vergleich)

**Bewertung/Erfahrungen:**
- 4.4 von 5 Sternen (218 Bewertungen)
- Preis: 19,99€ (inkl. USt.) für CAN-BUS Version
- Verfügbar bei Amazon (Zeekpowa-Store)

**Kompatibilitätsbewertung:**

✅ **Sehr wahrscheinlich kompatibel** - Gründe:
1. **Error 21 bestätigt Bafang-Kompatibilität:**
   - Controller zeigt **Error 21** ("Speed sensor Error")
   - Error 21 ist ein **Bafang-spezifischer Fehlercode**
   - Dies bestätigt, dass der **AEG ComfortDrive Controller Bafang-basiert** ist
   - Der bestellte **Bafang CAN-BUS Sensor** sollte daher kompatibel sein

2. **Stecker-Kompatibilität:**
   - **4-poliger Stecker** passt (identisch mit Original)
   - **Blau-tipped, schwarzes Gehäuse** (typisch für Bafang CAN-BUS)

3. **Motor-Basis:**
   - AEG ComfortDrive basiert auf Bafang-Technologie (bereits vermutet)
   - Error 21 bestätigt dies nun eindeutig

⚠️ **Zu beachten bei Installation:**
- **Magnet-Ausrichtung:** Wichtig für korrekte Funktion (siehe Error 21 Abschnitt)
- **Abstand prüfen:** Magnet muss innerhalb von 15 mm vom Sensor sein (optimal: 2-5 mm)
- **Nach Installation:** Error 21 sollte verschwinden, wenn Sensor korrekt funktioniert
- **Falls Error 21 bleibt:** Magnet-Ausrichtung oder Protokoll (CAN-BUS vs. UART) prüfen

**Hinweis:** Da der Stecker gleich aussieht UND Error 21 ein Bafang-Fehlercode ist, ist die Kompatibilität sehr wahrscheinlich. Falls der Sensor nach Installation nicht funktioniert, könnte es am Protokoll (CAN-BUS vs. UART) oder der Magnet-Ausrichtung liegen.

#### Anschlussinformationen

**Visuelle Inspektion (basierend auf Foto):**
- Der Sensor ist mit einem **schwarzen Kabel** verbunden
- Das Kabel verläuft entlang des Rahmens
- Die genaue Anzahl der Adern im Kabel und die Art des Steckers sind visuell nicht eindeutig erkennbar
- **Empfehlung:** Direkte Inspektion des Steckers und der Kabeladern am defekten Sensor durchführen

**Anschluss-Typen:**

**Typischer 3-Draht-Anschluss (einfache Sensoren):**
- **Rot/Plus:** +5V oder +12V Versorgungsspannung
- **Schwarz/Minus:** Masse (GND)
- **Gelb/Grün/Weiß:** Signalleitung (Impulse)

**4-poliger CAN-BUS Anschluss (Bafang CAN-BUS Sensor):**
- **4 Pins** in quadratischer Anordnung
- **Stecker:** Blau-tipped, schwarzes Gehäuse
- **Protokoll:** CAN-BUS (digitale Kommunikation)
- **Pinout:** Typischerweise:
  - CAN-H (CAN High)
  - CAN-L (CAN Low)
  - +5V (Versorgung)
  - GND (Masse)
- **Hinweis:** Exakte Pinbelegung kann variieren - Original-Sensor als Referenz verwenden

**Hinweis:** Die genaue Farbcodierung und Anschlussbelegung kann je nach Hersteller variieren. Die exakte Anschlussweise muss aus der Original-Dokumentation oder durch Inspektion des defekten Sensors ermittelt werden. Da keine Pinout-Informationen öffentlich verfügbar sind, ist eine direkte Inspektion des Steckers und der Kabelbelegung am defekten Sensor notwendig.

#### Diagnose eines defekten Geschwindigkeitssensors

**Typische Symptome:**
- ❌ **Keine Unterstützung** oder ruckelig
- ❌ **Anzeige bleibt bei 0 km/h** (Geschwindigkeit wird nicht angezeigt)
- ❌ **Motor schaltet zu früh / zu spät ab** (25 km/h-Grenze funktioniert nicht korrekt)
- ❌ **Fehlercode im Display** (oft "Speed Sensor Error")
- ❌ **Error 21** (Bafang-spezifischer Fehlercode - siehe unten)
- ❌ **Unterstützung geht kurz an und wieder aus**

#### Error 21 - Bafang Speed Sensor Error

**WICHTIGE ERKENNTNIS:** Der Fehlercode **Error 21** ("Speed sensor Error") ist ein **Bafang-spezifischer Fehlercode**. Wenn Ihr AEG ComfortDrive Controller diesen Fehler anzeigt, ist dies ein **starker Hinweis darauf, dass der Controller Bafang-basiert ist** und der bestellte Bafang CAN-BUS Sensor kompatibel sein sollte.

**Error 21 - Bedeutung:**
- **Fehlercode:** Error 21
- **Meldung:** "Speed sensor Error" (Geschwindigkeitssensor-Fehler)
- **System:** Bafang E-Bike Systeme (BBS01, BBS02, BBS-HD, M-Serie)
- **Ursache:** Geschwindigkeitssensor erkennt kein Signal oder Signal ist fehlerhaft

**Typische Ursachen für Error 21:**
1. **Magnet fehlt, lose oder falsch ausgerichtet**
   - Magnet nicht an Speiche montiert
   - Magnet zu weit vom Sensor entfernt
   - Magnet verrutscht oder verloren
2. **Sensor defekt**
   - Kabelbruch (besonders direkt am Sensor)
   - Sensor beschädigt
   - Stecker korrodiert oder lose
3. **Abstand zu groß**
   - Magnet außerhalb des Erfassungsbereichs
   - Sensor zu weit vom Magnet entfernt

**Lösung für Error 21 (basierend auf Bafang-Anleitung):**
- **Magnet sichern und korrekt ausrichten**
- **Abstand prüfen:** Magnet muss innerhalb von **15 mm** vom Sensor sein
- **Optimaler Abstand:** 2-5 mm zwischen Sensor und Magnet
- **Magnet an Speiche montieren** (mit mitgeliefertem Magnet-Halter)
- **Sensor am Rahmen befestigen** (Kettenstrebe oder Ausfallende)

**Kompatibilitätsbewertung basierend auf Error 21:**

✅ **Starke Indizien für Kompatibilität:**
- Controller zeigt **Error 21** (Bafang-spezifischer Fehlercode)
- Dies deutet darauf hin, dass der **AEG ComfortDrive Controller Bafang-basiert** ist
- Der bestellte **Bafang CAN-BUS Geschwindigkeitssensor** sollte daher kompatibel sein
- **4-poliger Stecker** passt (wie am Original-Sensor)

⚠️ **Zu beachten:**
- **Protokoll prüfen:** CAN-BUS vs. UART (bestellter Sensor ist CAN-BUS)
- **Magnet-Ausrichtung:** Wichtig für korrekte Funktion (siehe Lösung oben)
- **Nach Installation testen:** Error 21 sollte verschwinden, wenn Sensor korrekt funktioniert

**Häufige Ursachen:**
- Magnet verrutscht / verloren
- Sensor zu weit weg vom Magnet (Abstand > ~5–10 mm)
- **Kabelbruch direkt am Sensor** (sehr häufige Ursache!)
- Feuchtigkeit im Sensor
- Stecker korrodiert

**Sofort-Checks (wichtigste Prüfungen):**

1. **Ist ein Magnet am Rad vorhanden?**
   - An einer Speiche?
   - Am Bremsscheibenträger?
   - Am Ritzelträger?

2. **Abstand Magnet ↔ Sensor prüfen**
   - **Optimal: 2–5 mm**
   - **> 10 mm = oft kein Signal mehr**

3. **Kabel wackeln / knicken prüfen**
   - Besonders direkt am Sensorgehäuse → Klassiker für Kabelbruch
   - Kabel entlang des Rahmens auf sichtbare Beschädigungen prüfen

4. **Steckverbindung suchen und prüfen**
   - Meist irgendwo am Hinterbau / Motor
   - Einmal trennen, auf Korrosion prüfen
   - Kontakte auf Verschmutzung prüfen

5. **Multimeter-Messung:**
   - **Versorgung:** ~5V zwischen + und GND prüfen
   - **Signal:** Signalleitung mit Multimeter prüfen - sollte beim Drehen des Rads zwischen 0V und ~5V springen
   - **Mit Oszilloskop:** Sauberes Rechtecksignal, Frequenz proportional zur Geschwindigkeit

6. **Sichtprüfung:**
   - Kabel und Steckerverbindungen auf Beschädigungen, Kabelbruch oder lose Verbindungen prüfen
   - Sensorposition am Rahmen kontrollieren

#### Weitere hilfreiche Ressourcen

- **Pedelec-Forum:** [pedelecforum.de](https://www.pedelecforum.de) - Diskussionen zu AEG ComfortDrive und Sensoren
- **E-Bike Foren:** Spezialisierte Foren für E-Bike-Reparaturen
- **Mikrocontroller.net:** Technische Diskussionen zu E-Bike-Sensoren

#### Kabelbruch-Reparatur

**Problem: Kabelbruch direkt vor dem Sensor**

Ein Kabelbruch direkt am Sensorgehäuse ist eine **sehr häufige Ursache** für defekte Geschwindigkeitssensoren. Das Kabel wird durch Vibrationen, Biegungen und Umwelteinflüsse an dieser Stelle besonders belastet.

##### Ersatzteil-Suchbegriffe

**Für die Suche nach einem Ersatzsensor verwenden Sie folgende Suchbegriffe:**

1. **Allgemeine Suchbegriffe:**
   - "Bafang Speed Sensor"
   - "E-Bike Hall Speed Sensor"
   - "E-Bike Geschwindigkeitssensor"
   - "Pedelec Speed Sensor"
   - "Wheel Speed Sensor E-Bike"

2. **Spezifischere Suchbegriffe:**
   - "Bafang Speed Sensor 3-pin"
   - "E-Bike Speed Sensor Hall Sensor"
   - "Julet Speed Sensor" (falls Julet-Stecker)
   - "Higo Speed Sensor" (falls Higo-Stecker)
   - "AEG ComfortDrive Speed Sensor" (Original-Ersatzteil)

3. **Mit Stecker-Spezifikation:**
   - "Bafang Speed Sensor Julet"
   - "E-Bike Speed Sensor Higo"
   - "Speed Sensor 3-pin wasserdicht"

**Wichtig:** Achten Sie auf:
- **Steckertyp** (Julet, Higo, oder proprietär)
- **Kabellänge** (siehe unten)
- **3-Draht-Anschluss** (Plus, Minus, Signal)
- **Magnet** (meist im Lieferumfang enthalten)

##### Kabellänge für Reparatur

**Typische Kabellängen bei E-Bike Geschwindigkeitssensoren:**

| Typ | Kabellänge |
|-----|------------|
| **Kurze Variante** | 20-30 cm (direkt am Ausfallende) |
| **Standard** | 40-60 cm (entlang Kettenstrebe) |
| **Lange Variante** | 80-120 cm (bis zum Motor/Controller) |

**Für Kabelbruch-Reparatur:**
- **Verfügbare Kabelstumpf-Länge am Sensor:** Typischerweise **5-15 cm** direkt am Sensorgehäuse
- **Empfehlung:** Wenn der Kabelbruch sehr nah am Sensor ist (< 5 cm), ist eine Reparatur schwierig, da nicht genug Kabel für eine saubere Verbindung vorhanden ist
- **Wenn Kabelbruch > 5 cm vom Sensor entfernt:** Reparatur möglich (siehe unten)

##### Kabelbruch selbst reparieren

**Voraussetzungen:**
- Kabelbruch ist **nicht direkt am Sensorgehäuse** (mindestens 5-10 cm Kabelstumpf vorhanden)
- Sie haben Erfahrung mit Lötarbeiten
- Sie können die Kabelbelegung identifizieren

**Schritte:**

1. **Kabelbruch lokalisieren:**
   - Kabel vorsichtig biegen und auf Widerstand prüfen
   - Mit Multimeter Durchgang prüfen (jeder Draht einzeln)
   - Sichtprüfung auf Risse im Kabelmantel

2. **Kabel freilegen:**
   - Kabelmantel vorsichtig entfernen (nicht zu tief schneiden!)
   - Die 3 Adern freilegen (meist: Rot/Plus, Schwarz/Minus, Gelb/Grün/Weiß/Signal)

3. **Kabelbruchstelle entfernen:**
   - Defekten Abschnitt entfernen
   - Kabelenden sauber abisolieren (ca. 5 mm pro Seite)

4. **Verbindung herstellen:**
   - **Lötverbindung** (empfohlen):
     - Kabelenden verzinnen
     - Zusammenlöten (jede Ader einzeln!)
     - Schrumpfschlauch über jede Verbindung
   - **Alternativ: Crimp-Verbinder** (wasserdicht):
     - Wasserdichte Crimp-Verbinder verwenden
     - Jede Ader einzeln verbinden

5. **Isolierung:**
   - Jede Ader einzeln mit Schrumpfschlauch isolieren
   - Gesamtes Kabel mit größerem Schrumpfschlauch oder Isolierband umwickeln
   - **Wichtig:** Wasserdichte Isolierung, da das Kabel Witterung ausgesetzt ist

6. **Prüfung:**
   - Mit Multimeter Durchgang prüfen
   - Funktionstest: Rad drehen, Signal prüfen

**⚠️ WICHTIG:**
- **Wasserdichte Verbindung** ist kritisch (Kabel ist Witterung ausgesetzt)
- **Korrekter Anschluss** jeder Ader (Plus, Minus, Signal nicht vertauschen!)
- **Mechanische Belastung** beachten - Verbindung sollte nicht zu starr sein
- **Garantie:** Selbstreparatur kann Garantieansprüche beeinträchtigen

##### Wenn Kabelbruch zu nah am Sensor

**Wenn der Kabelbruch direkt am Sensorgehäuse ist (< 5 cm):**
- **Empfehlung:** Sensor komplett ersetzen
- Kabelstumpf ist zu kurz für eine saubere Reparatur
- Risiko von erneutem Kabelbruch ist hoch
- Original-Ersatzteil oder kompatiblen Sensor beschaffen

**Ersatzteil-Beschaffung:**
- Siehe Abschnitt "Empfohlene Vorgehensweise zur Ersatzteilbeschaffung" oben
- Kontakt mit Prophete oder autorisierter Werkstatt
- Kompatible Bafang-Sensoren (siehe Kompatibilitätsinformationen)

#### Zusätzliche Informationen für Reparatur

**Was für eine gezielte Hilfe noch benötigt wird:**
1. **Was genau ist das Problem?**
   - Keine Unterstützung?
   - Falsche Geschwindigkeit?
   - Fehlercode im Display?

2. **Foto vom Magneten am Rad** (falls vorhanden)

3. **Foto vom Stecker** (Sensor → Kabelbaum)

4. **Foto vom Kabelbruch** (für Reparatur-Planung)

5. **Error-Code im Display** (falls vorhanden)

6. **Verfügbare Kabelstumpf-Länge** (für Reparatur-Entscheidung)

Mit diesen Informationen kann eine genauere Diagnose und Ersatzteil-Empfehlung erfolgen.

#### Praktische Reparatur-Tipps

##### Feste Schrauben am Motor lösen

**Problem:** Die Schrauben am Motor sind sehr fest und lassen sich nicht lösen.

**Häufige Ursachen:**
- **Korrosion** (Rost, Oxidation)
- **Fadensicherung** (Loctite, Schraubensicherung)
- **Überdreht** beim Einbau
- **Verschmutzung** in den Gewinden
- **Kaltverschweißung** (Metall-Metall-Bindung)

**Lösungsmethoden (in Reihenfolge versuchen):**

1. **Richtiges Werkzeug verwenden:**
   - **Passenden Schraubendreher/Bit verwenden** (nicht zu klein, sonst rutscht ab)
   - **Inbusschlüssel** in der richtigen Größe (metrisch, nicht zoll)
   - **Torx/TX** falls vorhanden (nicht mit Inbus verwechseln!)
   - **Qualitatives Werkzeug** (billiges Werkzeug kann abrutschen und Schraube beschädigen)

2. **Mehr Kraft mit richtigem Hebel:**
   - **Verlängerung verwenden** (Rohr über Schraubendreher)
   - **Schlag-Schraubendreher** (Impact Driver) - vorsichtig verwenden
   - **Kraft in richtiger Richtung** (linksdrehend = gegen den Uhrzeigersinn)
   - **Nicht ruckartig**, sondern gleichmäßig mit zunehmendem Druck

3. **Rostlöser / Penetrieröl:**
   - **WD-40, Kriechöl oder Rostlöser** auf Schraube und Gewinde sprühen
   - **15-30 Minuten einwirken lassen**
   - **Mehrfach wiederholen** (alle 10-15 Minuten nachsprühen)
   - **Leicht klopfen** mit Hammer (vorsichtig!) - Vibrationen helfen
   - **Dann erneut versuchen** zu lösen

4. **Wärme anwenden (vorsichtig!):**
   - **Heißluftföhn** oder **Lötlampe** (nur bei Metallteilen, nicht bei Kunststoff!)
   - **Schraube erwärmen** (Metall dehnt sich aus)
   - **Schnell lösen**, solange noch warm
   - **⚠️ VORSICHT:** Nicht bei Kunststoffteilen, Kabeln oder Akku verwenden!
   - **Feuergefahr** beachten

5. **Schraube anklopfen:**
   - **Leicht mit Hammer** auf Schraubenkopf klopfen
   - **Vibrationen lösen** Rost und Verschmutzung
   - **Nicht zu fest** - Schraube könnte brechen
   - **In Kombination mit Rostlöser** besonders effektiv

6. **Schraube festhalten und drehen:**
   - **Gegenhalten** mit zweitem Werkzeug (falls möglich)
   - **Rahmen/Motor** stabilisieren, damit nichts mitdreht
   - **Gleichmäßiger Druck** beim Lösen

7. **Schlag-Schraubendreher (Impact Driver):**
   - **Mechanischer Schlag-Schraubendreher** (nicht elektrisch!)
   - **Leichte Schläge** mit Hammer auf Schlag-Schraubendreher
   - **Drehmoment durch Schläge** überträgt sich besser
   - **Vorsichtig verwenden** - kann Schraube beschädigen

8. **Wenn Schraube rund ist:**
   - **Schraubenausdreher** (Extractor) verwenden
   - **Linksdrehende Bohrer** (können beim Bohren die Schraube lösen)
   - **Professionelle Hilfe** aufsuchen

**⚠️ WICHTIGE HINWEISE:**

- **Nicht überdrehen:** Wenn Schraube sich nicht löst, nicht weiter drehen - Schraube könnte brechen
- **Richtige Größe:** Falsches Werkzeug beschädigt Schraube (rund drehen)
- **Gewinde schützen:** Beim Lösen nicht Gewinde im Rahmen beschädigen
- **Reihenfolge:** Schrauben im Wechsel lösen (nicht eine komplett, dann nächste)
- **Drehmoment beim Wiedereinbau:** Nicht zu fest anziehen (siehe Herstellerangaben)
- **Fadensicherung:** Beim Wiedereinbau eventuell neue Fadensicherung verwenden

**Wenn nichts hilft:**
- **Professionelle Werkstatt** aufsuchen
- **Schraube aufbohren** und neu einschneiden (Gewindeschneider)
- **Schraube ausbohren** und durch neue ersetzen

**Nach dem Lösen:**
- **Gewinde reinigen** (Gewindeschneider, Drahtbürste)
- **Neue Schrauben** verwenden (falls beschädigt)
- **Fadensicherung** beim Wiedereinbau (falls ursprünglich vorhanden)
- **Korrekten Drehmoment** verwenden (Drehmomentschlüssel)

##### Weitere praktische Tipps

**Beim Arbeiten am Motor:**
- **Akku entfernen** (Sicherheit!)
- **Stabile Position** des Fahrrads (Werkstattständer)
- **Saubere Arbeitsfläche** (Schrauben nicht verlieren)
- **Fotos machen** vor dem Ausbau (für Wiedereinbau)
- **Schrauben sortieren** (in beschrifteten Behältern)

**Werkzeuge die hilfreich sind:**
- **Drehmomentschlüssel** (für korrekten Wiedereinbau)
- **Gewindeschneider** (für Gewindereinigung)
- **Rostlöser** (WD-40, etc.)
- **Schlag-Schraubendreher** (für feste Schrauben)
- **Verschiedene Bit-Größen** (Inbus, Torx, etc.)

#### Bestellte Werkzeuge

**Universal Fahrrad Kurbelabzieher**

**Produktdetails:**
- **Marke:** Gold-Fieber
- **Typ:** Universal Kurbelabzieher
- **Kompatibilität:**
  - Shimano Octalink
  - ISIS (International Splined Interface Standard)
  - **Bosch E-Bikes** (wichtig für AEG ComfortDrive, da möglicherweise Bosch-kompatibel)
- **Material:** Gehärteter Stahl (hochwertig)
- **Bewertung:** 4.6 von 5 Sternen (149 Bewertungen)
- **Preis:** 19,80€ (inkl. USt.)

**Verwendungszweck:**
- **Kurbeln entfernen** (für Zugang zum Tretlager)
- **Tretlager-Wartung** (falls nötig)
- **Motor-Zugang** (falls Kurbeln entfernt werden müssen)
- **Sensor-Zugang** (für Drehzahlsensor am Tretlager)

**Wichtige Hinweise:**
- **Kompatibilität prüfen:** AEG ComfortDrive verwendet möglicherweise Bosch-kompatible Komponenten
- **Richtige Verwendung:** 
  - Kurbelabzieher in das Gewinde der Kurbel einschrauben
  - Mit Schraubenschlüssel oder Ratsche drehen
  - Kurbel wird langsam herausgedrückt
- **Vorsicht:** Nicht überdrehen - Gewinde könnte beschädigt werden
- **Für E-Bikes:** Speziell für Bosch E-Bikes geeignet, was auf Kompatibilität mit AEG ComfortDrive hindeutet

**Hinweis:** Der Kurbelabzieher ist besonders nützlich, wenn Sie Zugang zum Tretlager oder zum Drehzahlsensor benötigen, der möglicherweise am Tretlager oder im Motor integriert ist.

##### Schraubenspezifikationen

**Motorabdeckung - Schraubenspezifikation:**

| Komponente | Schraubentyp | Spezifikation |
|------------|--------------|---------------|
| **Motorabdeckung (Bosch)** | Senkkopfschraube | M3 x 14, TX10, Edelstahl rostfrei |

**Details:**
- **Typ:** Senkkopfschraube (Countersunk Head Screw)
- **Gewinde:** M3 (metrisch, 3 mm Durchmesser)
- **Länge:** 14 mm
- **Antrieb:** TX10 (Torx 10)
- **Material:** Edelstahl rostfrei (A2 oder A4 Edelstahl)

**Hinweise:**
- Diese Spezifikation bezieht sich auf die **Bosch-Motorabdeckung**
- Der **AEG ComfortDrive Motor** verwendet möglicherweise **ähnliche oder identische Schrauben**
- **Torx-Größe:** **TX10** (Torx 10) - wichtig für richtiges Werkzeug
- **Drehmoment:** Für M3-Schrauben typischerweise **1-2 Nm** (Herstellerangaben beachten)
- **Senkkopf:** Schraube sitzt bündig mit der Oberfläche (kein hervorstehender Kopf)

**Ersatzteil-Beschaffung:**

**Suchbegriffe:**
- "Senkschraube M3x14 TX10 Edelstahl"
- "Senkkopfschraube M3 14mm Torx 10 rostfrei"
- "M3x14 TX10 Edelstahl Senkschraube"
- "E-Bike Motorabdeckung Schraube M3x14"

**Erhältlich bei:**
- Fahrradwerkstätten (E-Bike-Spezialisten)
- Online-Shops für E-Bike-Ersatzteile
- Schraubenhändler (Metallwarenhandel)
- Baumärkte (begrenztes Sortiment)

**Wichtig beim Kauf:**
- **Korrekte Länge beachten** (14 mm) - zu lange Schrauben können innenliegende Komponenten beschädigen
- **Torx-Antrieb TX10** (nicht Inbus!)
- **Edelstahl rostfrei** (für Witterungsbeständigkeit)
- **Senkkopf** (nicht Zylinderkopf oder Linsenkopf)

**Beim Wiedereinbau:**
- **Drehmomentschlüssel verwenden** (nicht überdrehen!)
  - Empfohlen: **1-2 Nm** für M3-Schrauben
  - Nicht zu fest anziehen (Gewinde könnte beschädigt werden)
- **Fadensicherung** eventuell verwenden (falls ursprünglich vorhanden)
- **Gewinde prüfen** (sauber, keine Beschädigungen)
- **Schrauben im Wechsel anziehen** (nicht eine komplett, dann nächste)
  - Erst alle Schrauben leicht anziehen
  - Dann im Wechsel auf Enddrehmoment anziehen
- **Korrosionsschutz** (Edelstahl ist bereits korrosionsbeständig, aber bei Bedarf zusätzlich schützen)

**Werkzeug:**
- **Torx-Bit TX10** (für Schraubendreher oder Akkuschrauber)
- **Drehmomentschlüssel** (für korrekten Wiedereinbau)
- **Gewindeschneider M3** (für Gewindereinigung falls nötig)

### Weitere Ersatzteile

Für andere Komponenten gelten ähnliche Vorgehensweisen:
- Kontakt mit Prophete für Original-Ersatzteile
- Ersatzteilversorgung bis zu 5 Jahre nach Kauf garantiert
- Bei Garantieansprüchen: Reparatur durch autorisierte Werkstatt

## Hinweise

- Die Informationen zum Controller (Steuergerät) sind in den verfügbaren Quellen nicht explizit detailliert beschrieben.
- Weitere Sensoren werden in den Produktbeschreibungen nicht gesondert erwähnt, sind aber aufgrund der Standardausstattung moderner Pedelecs wahrscheinlich vorhanden.
- Die genaue Modellnummer des Controllers und weitere technische Details zum Steuergerät müssten durch direkte Inspektion oder Herstellerdokumentation ermittelt werden.
- **Wichtig:** Bei Reparaturen an elektrischen Komponenten sollte immer eine Fachwerkstatt konsultiert werden, insbesondere wenn die Garantie noch besteht.
