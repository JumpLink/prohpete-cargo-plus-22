# Programmierung & Kalibrierung

Mit einem Bafang CAN-BUS-Programmierkabel und passender Software lassen sich am Controller u. a. **Radumfang, Geschwindigkeitsbegrenzung, Strombegrenzung und Unterstützungsstufen** anpassen – also auch eine Kalibrierung durchführen.

## Kompatibilität mit AEG ComfortDrive

- Das gezeigte **Varstrom-Programmierkabel** (5-Pin, CAN-BUS, 110 cm) ist für **Bafang BBS-HD, BBS01B, BBS02B** ausgewiesen – **nicht** für M200, M400, Ultra oder Nicht-CAN-Systeme.
- **Am Rad identifiziert:** Das Datenkabel Display ↔ Controller ist ein **Bafang DP C211**-Kabel mit **5-Pin rundem Stecker, grüner Innenstecker**. Siehe [Spezifikation → Datenkabel](spezifikation.md#datenkabel-display--controller-identifiziert).
- **AEG ComfortDrive:** Ist Bafang-basiert (u. a. Error 21); ob **BBS-** oder **M/G-Serie** ist öffentlich **nicht eindeutig** dokumentiert. AEG/Prophete nutzen mehrere Bafang-Mittelmotor-Systeme – ohne Herstellerangabe bleibt die genaue Plattform unsicher.
- **Stecker:** Am Rad **rund** (grün), Varstrom-Kabel **Dreikant** (dreieckig) – **nicht automatisch baugleich**. Vor Kauf/Anschluss **Steckerform und Pin-Anordnung am Rad prüfen**; nur bei Übereinstimmung passt das Kabel. Programmier-Port: typischerweise dort, wo das Display angeschlossen ist (Display abziehen, Kabel einstecken).
- **Vor Nutzung:** Anschluss am Rad prüfen; nur Kalibrierung, keine Grenzwert-Änderung (Garantie/Recht).

### Zwei Kabel-Familien (BBS vs. M/G)

| Kabel | Ziel-Motoren | Stecker |
|-------|----------------|--------|
| **Varstrom (BBS)** | BBS-HD, BBS01B, BBS02B | 5-Pin **Dreikant** (dreieckig), **männlich**, wasserdicht, grüner Ring (CAN) |
| **M/G-Serie-Kabel** | M400, G330, M500, G521, M620, M510, G522, M420, G332 | USB → schwarz + **grün** (rund, wasserdicht; teils beide Geschlechter im Set) |

**Stecker-Geschlecht:** Am Rad sitzt in der Regel eine **Buchse (weiblich)**; ein Programmierkabel mit **männlichem** Stecker passt dort hinein (Display abziehen, Kabel einstecken). Das Varstrom-Kabel hat **5-Pin männlich** (Dreikant). **Wichtig:** Am Rad ist der Stecker **rund** (DP C211), beim Varstrom-Kabel **Dreikant** – das können unterschiedliche HIGO-Varianten sein. Nur wenn Form und Pin-Anordnung übereinstimmen, passt es; sonst ggf. Adapter oder anderes Kabel nötig.

Das **M/G-Serie-Programmierkabel** („Parameter Einstellwerkzeug“) ist für **M400, M500, M620, G330, G521** usw. ausgewiesen – **nicht** für die BBS-Serie. Es bietet u. a. **Raddurchmesser-Anpassung** (z. B. 50,8–73,7 cm) und Korrektur von Geschwindigkeitsabweichungen. Ein Ende hat einen **grünen** runden Stecker – optisch wie das DP-C211-Datenkabel. **Unklar:** Ob der AEG ComfortDrive zur **BBS-** oder zur **M/G-Familie** gehört. Passt der Stecker (grün, rund, 5-Pin), kann es das richtige Kabel sein, **wenn** dein Motor M/G-basiert ist; bei BBS-Basis wäre das Varstrom-Kabel die passende Familie. **Hinweis:** Dieses M/G-Kabel war zum Doku-Stand teils als „derzeit nicht verfügbar“ gelistet – Verfügbarkeit prüfen.

## Zusätzliches Kabel: 1T4-Splitter (BBS CAN)

In manchen Varstrom-/BBS-CAN-Anleitungen wird ein **1T4-Kabel** (Splitter) gezeigt:

- **Was ist 1T4?** Ein **Bordverkabelungs-Kabel** („1 zu 4“): ein Stecker zum Motor (z. B. 8-Pin), vier Abgänge – typisch für **Display** (5-Pin grün), **2× Bremshebel** (3-Pin gelb, Motorabschaltung beim Bremsen), **Throttle** (5-Pin orange). Wird bei BBS-Umbauten bzw. -Nachrüstungen genutzt.
- **Für Programmierung:** Bei BBS-CAN kann das Programmierkabel oft **direkt** an die Display-Buchse (Display abziehen, Kabel einstecken). Dann ist **kein** 1T4 nötig. 1T4 brauchst du nur, wenn du bewusst zwischen Motor und Harness einsteckst (z. B. bei speziellen Diagnose-Setups).
- **Am fertigen Rad (z. B. Cargo Plus):** Dein Rad hat **bereits** eine Bordverkabelung (Motor ↔ Display, ggf. ohne Bremsen-Anschluss). Die Bremsen sind bei vielen OEM-Pedelecs **nicht** mit dem Motor verbunden (kein Brems-Signal an den Controller). Mit einem **zusätzlichen** 1T4-Kabel würdest du die bestehende Verkabelung ersetzen – nur nötig bei Defekt oder Umbau, **nicht** für Kalibrierung oder normalen Betrieb. Du brauchst das Zeekpowa-1T4 o. Ä. also **nicht**, solange alles funktioniert und du nur programmieren willst.

## Software und Anleitung (BBS CAN)

Für das Bafang USB-Programmierkabel „For CAN protocol BBS series motor“ sind oft **zwei QR-Codes** angegeben:

| QR-Code | Inhalt | Link (Beispiel) |
|---------|--------|------------------|
| **USER MANUAL** | Bedienungsanleitung | z. B. https://bit.ly/yracan-m |
| **SOFTWARE** | Software + Treiber | z. B. https://bit.ly/yracan-s |

**Hinweis:** Die genauen Links sind anbieterabhängig und können sich ändern. **Maßgeblich ist der QR-Code auf der Verpackung des gekauften Kabels** – nicht eine allgemeine URL.

**Software-Paket (typisch):**

- **Can bus Debugger Pro for ebike V1.6** (Archiv, z. B. `.rar`) enthält:
  - `Can bus Debugger Pro for ebike V1.6.exe` – Konfigurationstool
  - `Ebike CAN Debugger Reference.pdf` – Referenz/Anleitung
  - `USB_uart_Drive_for_Windows.exe` – USB-Treiber für das Kabel
- **Ablauf:** QR-Code scannen → Software herunterladen → Archiv entpacken → Dateien auf PC kopieren → **zuerst USB-Treiber installieren** → dann „Can bus Debugger Pro“ starten → Port öffnen → **„Read All“** (Werte vom Controller lesen) → Parameter anpassen (z. B. Wheel Diameter, Speed Limit) → **„Write All“** nur bei Bedarf und mit Vorsicht.

**Relevante Parameter für Kalibrierung:** Wheel Diameter, Speed Limit, Speed Meter, ggf. Current Limiting; Basic/Advance Settings je nach Software.

## Software (Übersicht)

| Option | Beschreibung |
|--------|--------------|
| **Mit Kabel (z. B. Varstrom/BBS CAN):** | **Can bus Debugger Pro for ebike** V1.6 – per QR-Code (s. o.); inkl. Referenz-PDF und USB-Treiber. Parameter z. B.: Wheel Diameter, Speed Limit, Current Limit, Assist Levels. |
| **Bafang offiziell:** | **BESST / BESST Pro** – [bafang-e.com → Service → Downloads](https://www.bafang-e.com/en/service/downloads/). Für CAN-Systeme; oft mit eigenem **BESST-Tool** (Hardware). Zielgruppe teils Händler/Service. |
| **Open Source:** | **OpenBafangTool** ([GitHub](https://github.com/andrey-pr/OpenBafangTool)) – unterstützt u. a. BBS01, BBS02, BBSHD und teils CAN-BUS (M500, M600). Prüfen, ob dein Anschluss/Kabel unterstützt wird. |

Für das Varstrom-Kabel ist die **mitgelieferte Software** (QR-Code) die naheliegende Wahl; BESST ist eher für offizielle Werkstatt/Diagnose.

## Wichtige Hinweise

- **Garantie:** Reprogrammierung kann zum **Verlust der Herstellergarantie** führen. Vor Änderungen Händler/Servicepartner fragen.
- **Rechtlich:** Änderung der **Geschwindigkeitsbegrenzung** (Tuning) führt dazu, dass das Rad rechtlich **kein Pedelec** mehr ist (Versicherung, StVZO). Diese Doku bezieht sich auf **Kalibrierung/Reparatur** (z. B. Radumfang, korrekte Anzeige), nicht auf Tuning.
- **Risiko:** Falsche Einstellungen können Controller/Motor schädigen. Nur Parameter ändern, die du kennst; Backups/Screenshots der Ausgangswerte machen.
