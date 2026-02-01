# Programmierung & Kalibrierung

Mit Bafang CAN-BUS-Hardware und passender Software lassen sich am Controller u. a. **Radumfang, Geschwindigkeitsbegrenzung, Strom und Unterstützungsstufen** anpassen (Kalibrierung).

## Unser Setup & Kompatibilität

- **Rad:** AEG ComfortDrive (Bafang-basiert), Display-Kabel **DP C211** (Bafang CAN-BUS, 5-Pin rund/grün). Siehe [Spezifikation → Datenkabel](spezifikation.md#datenkabel-display--controller-identifiziert).
- **Protokoll:** Nur **CAN-BUS**. Tools nur für **UART/Serial** (z. B. BafangWebConfig, bafang-python, bdac) passen **nicht**.

| Software / Hardware | Passt? | Hinweis |
|---------------------|--------|---------|
| **Can bus Debugger Pro** + günstiges USB-Kabel (Varstrom, TDCuizent) | ✅ Ja, wenn Stecker passt | Stecker am Rad: rund/grün. Viele Kabel: Dreikant – vor Kauf prüfen. Software oft per QR-Code auf der Verpackung. |
| **OpenBafangTool** | ✅ Ja, mit BESST-Tool | Für CAN aktuell **nur** offizielles Bafang BESST-Tool (~100–150 €). Günstige USB-Kabel werden **nicht** unterstützt; Canable geplant. [GitHub](https://github.com/andrey-pr/OpenBafangTool) |
| **BESST / BESST Pro** | ⚠️ Möglicherweise | Offizielles Bafang-Tool, teils Händler-Zugang. [bafang-e.com → Service → Downloads](https://www.bafang-e.com/en/service/downloads/) |

**Kabel-Familien:** BBS-CAN-Kabel (z. B. Varstrom) für BBS01/02/HD; M/G-Kabel für M400, M500, M620 usw. Ob der ComfortDrive BBS- oder M/G-basiert ist, ist öffentlich nicht eindeutig – Steckerform (rund/Dreikant, 5-Pin) vor Nutzung mit dem Rad abgleichen.

## Hardware

| Ziel | Hardware |
|------|----------|
| **Can bus Debugger Pro** (Kalibrierung mit günstigem Kabel) | USB-Programmierkabel für Bafang BBS CAN (5-Pin, z. B. Varstrom, TDCuizent). Display abziehen, Kabel in dieselbe Buchse. |
| **OpenBafangTool** (CAN) | Offizielles **BESST-Tool** (~100–150 €). Günstige Kabel werden für CAN nicht unterstützt. |

**1T4-Kabel:** Bordverkabelung (Motor ↔ Display, ggf. 2× Bremse, Throttle). Am fertigen Rad bereits verbaut; für reine Programmierung nicht nötig (Display abziehen, Programmierkabel einstecken).

## Software

- **Can bus Debugger Pro** (mit Kabel): Oft per **QR-Code** auf der Verpackung (Software + Treiber). Typisch: `.exe`, Referenz-PDF, USB-Treiber. Ablauf: Treiber installieren → Programm starten → Port öffnen → „Read All“ → Parameter anpassen (z. B. Wheel Diameter) → „Write All“ nur bei Bedarf. Links anbieterabhängig – QR-Code auf dem Kabel maßgeblich.
- **OpenBafangTool:** [GitHub – andrey-pr/OpenBafangTool](https://github.com/andrey-pr/OpenBafangTool). Windows/Linux (Executables). Für CAN: BESST-Tool nötig.
- **UART-Tools** (BafangWebConfig, bafang-python, bdac, BBS_config): Nur für UART-BBS, **nicht** für unser CAN-Setup.

## Open-Source-Firmware (Ersatz-Firmware für BBS)

| Projekt | Beschreibung | Link |
|---------|--------------|------|
| **Bafang_BBS02_BBSHB** | Ersatz-Firmware für Bafang **BBS02** und **BBSHD** (UART-Motoren). Ersetzt die Original-Controller-Firmware; keine reine Kalibrierung, sondern vollständiger Firmware-Flash. Von OpenSourceEBike. | [GitHub: OpenSourceEBike/Bafang_BBS02_BBSHB](https://github.com/OpenSourceEBike/Bafang_BBS02_BBSHB) |

**Hinweis:** Unser Rad (AEG ComfortDrive, DP C211) nutzt **CAN-BUS**; die genaue Motorplattform (BBS vs. M/G) ist unklar. Diese Firmware ist nur für **BBS02/BBSHD mit UART** gedacht – nicht für CAN-Motoren (M500, M600 usw.) und nicht für reine Parameter-Anpassung. Nur relevant, wenn du bewusst die Motor-Firmware ersetzen willst und ein BBS-UART-System hast. Flashen kann Garantie voiden und ist mit Risiko verbunden.

## Wichtige Hinweise

- **Garantie:** Reprogrammierung kann Garantieverlust bedeuten. Vor Änderungen Händler/Servicepartner fragen.
- **Rechtlich:** Nur Kalibrierung/Reparatur (z. B. Radumfang). Änderung der 25-km/h-Begrenzung = rechtlich kein Pedelec mehr (Versicherung, StVZO).
- **Risiko:** Falsche Einstellungen können Controller/Motor schädigen. Nur bekannte Parameter ändern; Ausgangswerte sichern (Screenshot/Backup).
