# Geosi – Basisdokument (gemeinsames Wissen für alle Geosi-Claude-Projekte)

| | |
|---|---|
| **Version** | 4 |
| **Stand** | 28.09.2026 |
| **Maßgebliche Fassung** | `Geosi-Basis.md` im GitHub-Repository **GeosiBasiswissen** |
| **Erstellt von** | Claude, aus dem Projekt „GeosiFORM6“, zur Prüfung durch Martin Ruetz |

---

## 1. Zweck und Regeln für dieses Dokument

### 1.1 Wozu

Die Geosi-Produkte sind zu umfangreich für ein einziges Claude-Projekt. Deshalb gibt es je Programmbereich ein eigenes Projekt (Abschnitt 2). Manches Wissen brauchen aber alle Projekte:

- Architektur und Schnittstellen,
- fachliche Konventionen,
- Pfade,
- Arbeitsweise.

Dieses Dokument hält dieses Querschnittswissen **an genau einer Stelle** fest.

### 1.2 Ablage und Pflege

- **Maßgeblich ist die Fassung im Git-Repository.** Nicht die Kopie in einem Claude-Projekt und nicht eine Datei auf einem einzelnen Rechner.
- Ablageort: `Geosi-Basis.md` im GitHub-Repository **[GeosiBasiswissen](https://github.com/IDC-EDV-GmbH/GeosiBasiswissen.git)** (eigenes Repository, angelegt von Martin Ruetz; Zweck siehe `README.md` dort). Lokaler Klon empfohlen unter `<GEOSI_ROOT>\GeosiBasiswissen`.
- **Änderungen nur im Repository**, versioniert per Commit, bei Bedarf per Pull Request mit Review. Dabei jedes Mal **Version und Stand** oben erhöhen und einen Eintrag in Abschnitt 10 ergänzen.
- **In jedes Claude-Projekt kommt eine unveränderte Kopie.** Die Kopien werden dort **nie bearbeitet**, nur durch die neue Fassung ersetzt.
- **So wird eine Projektkopie ersetzt:** zuerst die alte `Geosi-Basis.md` im Claude-Projekt **löschen**, dann die neue aus dem Repository-Klon einfügen. Nur Einfügen überschreibt nicht, sondern legt eine zweite Datei gleichen Namens daneben an – dann stehen zwei widersprüchliche Fassungen im Projekt. Danach prüfen, dass die Datei nur einmal vorhanden ist und die Version oben stimmt.
- Die Datei immer **aus dem Repository-Klon** (bzw. von GitHub) importieren, nicht aus einer Zwischenablage oder einem Download aus einer Claude-Sitzung.
- Claude-Sitzungen:
  - Findet eine Sitzung Wissen, das hierher gehört, schlägt sie die Änderung für das Repository vor, statt nur die Projektkopie anzupassen.
  - Stimmt die Version in einer Projektkopie nicht mit der im Repository überein, gilt die Fassung im Repository.

### 1.3 Was hier NICHT hineingehört

- Detailwissen eines einzelnen Programmbereichs, z. B. einzelne Bugs, Testfälle, Feldkataloge. Das gehört ins zuständige Projekt (Abschnitt 2).
- Echte Kundendaten, auch keine Beispiele daraus (Abschnitt 8).

---

## 2. Projektlandschaft und Zuständigkeiten

| Claude-Projekt | Programmbereich | Code-Schwerpunkt |
|---|---|---|
| **GeosiFORM6** | GeosiFORM 6 gesamt (Urkunden, Teilung, Gegenüberstellung, Anonymisierung auf Form-Seite, Form5-Import usw.) | `GeosiFORMv6`, `IdcShared_Cpp_GeosiForm` |
| **Geosi Plan STP** | STP-Export in GeosiPLAN | GeosiPLAN (STP-Teil) |
| **Geosi Plan Flächenverwaltung** | Flächenmanager in GeosiPLAN, inkl. Anonymisierung auf Plan-Seite | GeosiPLAN (Flächenverwaltung) |
| **GeosiFORM5** | GeosiFORM 5 (Vorgänger von Form6, VB.NET, bei Kunden noch im Einsatz), zunächst Anonymisierung von Form5-Urkunden (`.eig`) | GeosiFORM5-Quellcode (Pfad noch nicht erhoben, siehe 3.1) |

**Regeln:**

- **Jedes Thema lebt in genau einem Projekt.** Die anderen Projekte verweisen nur darauf („siehe Projekt X“).
- **Faustregel für die Zuordnung:** Ein Thema gehört in das Projekt, in dessen Code die Änderung passiert. Bei Schnittstellen ist jede Seite in ihrem Projekt.
- **Schnittstellen haben zwei Seiten.** Ändert sich ein Austauschformat, ist die Übergabe an das Projekt der anderen Seite ein fester Arbeitsschritt. Übergabe als MD-Datei, die dort importiert wird.
- **Neues Projekt nur, wenn es sich lohnt:** Ein Programmbereich bekommt ein eigenes Projekt erst, wenn er eigenen Code, eigene Testdaten und eigene offene Punkte hat. Sonst reicht ein eigenes Dokument im passenden Projekt.

Bisherige Übergaben:

| Datum | Von → Nach | Übergabedatei |
|---|---|---|
| 24.09.2026 | GeosiFORM6 → Geosi Plan STP | `STP-Export_Wissen_fuer_GeosiPLAN-STP.md` |
| 25.09.2026 | GeosiFORM6 → Geosi Plan Flächenverwaltung | `GeosiPLAN_Flaechenverwaltung_Projektwissen.md` |
| 25.09.2026 | Geosi Plan Flächenverwaltung → GeosiFORM6 | `Uebergabe_Flaechenabgleich_Absturz_fuer_GeosiFORM6.md` (Absturz im Flächenabgleich; behoben 25.09.2026) |
| 25.09.2026 | Geosi Plan Flächenverwaltung → GeosiFORM6 | `Uebergabe_Anonymisierung_ungueltige_KG_fuer_GeosiFORM6.md` (fiktive KGs für ungültige KG-Werte; behoben, getestet 28.09.2026) |
| 28.09.2026 | GeosiFORM6 → GeosiFORM5 | `GeosiFORM5_Anonymisierung_Projektwissen.md` (Regeln, Form5-Datenformat aus dem Form6-Import, Zuordnungsdatei, Fallstricke) |

---

## 3. Pfade

Alle Pfade in den Projektdokumenten sind lokale Pfade auf dem Rechner, auf dem sie erhoben wurden, meist auf Martins Rechner. **Bei Kollegen sind sie teilweise identisch, teilweise anders.** Deshalb werden Pfade in drei Gruppen geführt.

### 3.1 Gruppe 1 – Pfade im Repository: bei allen gleich, relativ angegeben

Ab dem Stammordner der Klone ist die Struktur bei allen gleich. In den Dokumenten steht der Stammordner als Platzhalter **`<GEOSI_ROOT>`**.

| Platzhalter | Bedeutung | Bei Martin |
|---|---|---|
| `<GEOSI_ROOT>` | Ordner, in dem die Geosi-Repositories nebeneinander liegen | `C:\Arbeit_Entw\Geosi` |

| Pfad (relativ) | Inhalt |
|---|---|
| `<GEOSI_ROOT>\GeosiFORMv6\` | Form6-Lösung (`GeosiFormApp.sln`, `GeosiFormArx.sln`, `GeosiFormKernel.sln`) |
| `<GEOSI_ROOT>\GeosiFORMv6\GeosiFormKernel\` | Kernel (C#) |
| `<GEOSI_ROOT>\GeosiFORMv6\GeosiFormApp\`, `...\GeosiFormArx\` | Standalone-App, BricsCAD-Aufsatz (C++/MFC) |
| `<GEOSI_ROOT>\GeosiFORMv6\CmdAreaSyncTestHarness\synthetic_testdata\` | synthetische Testdaten für den Flächenabgleich |
| `<GEOSI_ROOT>\IdcShared_Cpp\Dev\IdcShared_Cpp_GeosiForm\` | gemeinsamer C++-Code von App und Arx |
| `<GEOSI_ROOT>\IdcShared_Cs\` | gemeinsamer C#-Code |
| `<GEOSI_ROOT>\GeosiBasiswissen\` | dieses Basisdokument (empfohlener Ablageort des Klons) |
| GeosiFORM5-Quellcode (VB.NET) | **noch nicht erhoben**, bitte im Projekt GeosiFORM5 ergänzen |
| `<GEOSI_ROOT>\GeosiPLAN\Dev\GeosiPlan\` | GeosiPLAN-Lösung (`GeosiPlan.sln`, `GeosiPlan.vcxproj`), C++/MFC, ObjectARX/BRX. Quelldateien in **Windows-1252** (siehe 7) |

**Fest vorgegeben (Build-Voraussetzung):** `IdcShared_Cpp` muss als **Geschwisterordner** neben `GeosiFORMv6` liegen, nicht darunter. Das Makro `$(IdcSharedRoot)` in `GeosiFormApp.vcxproj` (`..\..\IdcShared_Cpp\Dev`) und die relativen Pfade in `GeosiFormArx.vcxproj` setzen das voraus. Der Stammordner darf abweichen, die Lage zueinander nicht. Dasselbe gilt für GeosiPLAN: `GeosiPlan.vcxproj` bindet gemeinsamen Code über `..\..\..\IdcShared_Cpp\Dev\...` ein, `IdcShared_Cpp` liegt also auch neben `GeosiPLAN`.

### 3.2 Gruppe 2 – Installationspfade: bei Standardinstallation gleich

| Pfad | Inhalt | Hinweis |
|---|---|---|
| `C:\ProgramData\Geosi60\GeosiPLANv3\Cfg\Kg.xcfg` | KG-Verzeichnis von GeosiPLAN (Abschnitt 5.2) | kann je nach Version oder Installation abweichen, z. B. andere Versionsnummer im Ordnernamen |

### 3.3 Gruppe 3 – persönliche Arbeitspfade: bei jedem anders

Stehen in Dokumenten nur als Beispiel („bei Martin: …“), nie als Vorgabe.

| Beispiel bei Martin | Zweck |
|---|---|
| `<GEOSI_ROOT>\GeosiFORMv6\Claude testdata\` | reale, anonymisierte Test-Urkunden (**nicht im Repository**, siehe Abschnitt 8) |
| `<GEOSI_ROOT>\GeosiFORMv6\Claude outputs\` | Ablage für Übergabedateien und Ergebnisse aus Claude-Sitzungen |
| `C:\Temp\` | Debug-Dumps |

### 3.4 Im Code fest hinterlegte Pfade (Stand 25.09.2026)

Diese Pfade stehen nicht nur in Dokumenten, sondern im Quellcode. Bei Kollegen können sie ins Leere zeigen.

| Datei | Fester Pfad | Gruppe | Bewertung |
|---|---|---|---|
| `IdcShared_Cpp_GeosiForm\CmdAnonymSaveAs.cpp` | `C:\ProgramData\Geosi60\GeosiPLANv3\Cfg\Kg.xcfg` | 2 | **Relevant.** Fehlt die Datei, wird der KG-Nachtrag still übersprungen – bei abweichender Installation fällt das nicht auf. **Quelle in GeosiPLAN ermittelt (28.09.2026):** `CParamLocal::GetParamLoc()->GetPathCfgConfig() + KG_MGR_FILE` (`"Kg.xcfg"`, Land AT; sonst `Kg_<land>.xcfg`), siehe `CKgMgrMap::GetFilename` in `GeosiPLAN\Dev\GeosiPlan\KgMgr.cpp`. Das Plan-Werkzeug `Cmd_Area_Mgr_Anonymize` nutzt diesen Weg. Umstellung in Form6 offen. |
| `GeosiFormKernel\FormFlAbgleich.cs` (Region `TEST-ONLY`) | `C:\Arbeit_Entw\Geosi\GeosiFORMv6\CmdAreaSyncTestHarness\synthetic_testdata` | 3 | unkritisch: nur Startordner eines Test-Dialogs, Testcode zum Entfernen |
| `GeosiFormKernel\CmdAreaSync.cs` (TEMP-DEBUG) | `C:\Temp\CmdAreaSync_*.xml` | 3 | unkritisch, soll ohnehin entfernt werden |

Neue feste Pfade im Code sind zu vermeiden. Wo sie nötig sind, werden sie in dieser Tabelle nachgetragen.

### 3.5 Anweisung für Claude-Sitzungen

- Zu Beginn einer Sitzung anhand der **verbundenen Ordner** feststellen, wo `<GEOSI_ROOT>` beim jeweiligen Anwender liegt. Pfade aus Dokumenten nie blind übernehmen.
- Pfade aus Gruppe 2 und 3 vor der Verwendung auf Existenz prüfen oder beim Anwender nachfragen.
- In neuen Dokumenten Repository-Pfade immer mit `<GEOSI_ROOT>` schreiben. Persönliche Pfade nur als Beispiel mit Namensangabe („bei Martin: …“).

---

## 4. Produktarchitektur (Überblick)

Abschnitt 4.1 (einschließlich der Architekturregel Kernel/nativ) gilt **nur für GeosiFORM 6**. GeosiPLAN und GeosiFORM 5 sind anders aufgebaut (4.2, 4.4).

### 4.1 GeosiFORM 6

Fachanwendung für österreichische Vermessungsbüros und Ingenieurkonsulenten, läuft mit **BricsCAD**.

| Komponente | Technik | Rolle |
|---|---|---|
| `GeosiFormApp` | C++/MFC (SDI, Doc/View) | Standalone-App ohne CAD |
| `GeosiFormArx` | C++/MFC, BRX-API (`.arx`) | Aufsatz in BricsCAD |
| `GeosiFormKernel` | .NET Framework 4.7.2, WinForms, **eigener Prozess** | gesamte Fachlogik und Bearbeitungs-UI |

- **Kommunikation nativ ⟷ Kernel:** `KernelInterface` (`IdcShared_Cpp_GeosiForm`). XML-Pakete (`DataXmlCollection`) laufen über eine eigene Shared-Memory-IPC (`IdcShared_Cpp_SharedMem`).
- **Ablauf:**
  1. Nativ: `KernelInterface::Connect()`, dann `SendWaitAnswer()`.
  2. Kernel: `CmdFactory.CreateCommand` findet per Reflection die Klasse `GeosiFormKernel.CmdXxx` zum `Command`-String.
  3. Aufruf von `CmdXxx.Execute(DataXmlCollection)`.

**Verbindliche Architekturregel für Form6 (von Martin festgelegt, gilt für bestehende und neue Funktionen):**

- **Im Kernel** (`CmdXxx : CmdBase`): die gesamte Fachlogik. Ergebnis und Fehler gehen per `DataXmlCollection` zurück (`Command`-String, `ReturnError(msg)`). **Kein** Dateidialog, **kein** Datei-I/O, **keine** Meldungsfenster.
- **Nativ** (`GeosiFormApp`/`GeosiFormArx`): Dateidialoge, Lesen und Schreiben von Dateien, Meldungen und der schlanke Kernel-Aufruf. Grund: Das kann sich zwischen Standalone-App und BricsCAD-Aufsatz unterscheiden.
- **Vorlagen für neue Befehle:** `CmdImportBev`, `CmdAnonymSaveAs`.

**Gemeinsamer nativer Code:**

- Eine Datei in `IdcShared_Cpp_GeosiForm` wird von jedem `.vcxproj` (`GeosiFormApp`, `GeosiFormArx`) **einzeln** mitkompiliert.
- Eine neue Datei muss deshalb in **jedem** `.vcxproj` und `.filters`, das sie braucht, als `ClCompile`/`ClInclude` eingetragen werden. Ein Eintrag nur in `IdcShared_Cpp.vcxproj` reicht nicht.

**Code-Duplikate:**

- `GeosiFormApp`, `GeosiFormArx` und `IdcShared_Cpp_GeosiForm` enthalten teils inhaltsgleiche Kopien derselben Dateien. Das stammt aus der Vault→GitHub-Migration.
- Synchron gehalten wird durch manuelle Disziplin, es gibt keinen automatischen Abgleich.
- Einige Duplikate im App-Ordner sind in keinem `.vcxproj` referenziert und damit unbenutzte Dateileichen.

### 4.2 GeosiPLAN

- Schwesterprodukt, eigenes `.arx` in BricsCAD (GeosiPLANv3).
- **Form-Arx ⟷ Plan:** Laufzeit-Bindung über `GetProcAddress` auf `IdcGetPlanInterface`, mit Versionscheck (`IPlan->IGetVersion() != IPlan->GetVersion()`).
- Plan-Architektur (Aufteilung Logik, UI, Datei-I/O) ist **noch nicht vollständig dokumentiert**. Die Form6-Regel aus 4.1 gilt nicht automatisch für Plan. Bisher erhoben (Projekt „Geosi Plan Flächenverwaltung“, 28.09.2026):
  - **Befehle:** Klassen `Cmd_Xxx : Cmd_Base` mit `DECLARE_SERIAL`/`IMPLEMENT_SERIAL`, erzeugt per Klassenname (`CRuntimeClass`) und ausgeführt über `CommandController`. Aufruf z. B. über `IDCP_CMD Cmd_Xxx;`. Menü-/Toolbar-Einträge in `CommandDefinition::FillRc`; ein Befehl ohne Eintrag dort ist trotzdem über `IDCP_CMD` aufrufbar.
  - **Daten je Zeichnung:** Manager in `CDocData` (z. B. `DataAreaMgr` = Flächenmanager, `DataPointMgr`), gespeichert als XML im DWG-Dictionary; Speichern mit der Zeichnung.
  - **Projekteigenschaften:** `CParamDoc` (pro GZ ein `PlanInfo` mit KG, Datum, Bearbeiter, Form-Dateiname). Änderungen erst mit `CParamDoc::ParamToDoc(doc)` in der Zeichnung.
  - **Form-Anbindung:** `Cmd_Form_Add` / `Cmd_Form_Remove`. Nur den Dateinamen zu setzen reicht nicht.

### 4.3 Datenaustausch Form ⟷ Plan (Überblick)

Die Tabelle beschreibt GeosiFORM 6. Zu GeosiFORM 5 siehe 4.4.

| Richtung | Mechanismus | Details im Projekt |
|---|---|---|
| Plan → Form | Flächenabgleich `CmdAreaSync`: der Flächenmanager kommt als XML („AreaMgr“) | Geosi Plan Flächenverwaltung, GeosiFORM6 |
| Form → Plan | `CmdSendDataToPlan`: Plan fordert per Keys an (`GetTheseXmls: ` + `;`-Liste, z. B. `GstListGdb`, `TrennstueckeList`, `EigentuemerList`, `GfnList`, `V408` …). Dieselben Key-Namen gibt es in Plan als Defines. | Geosi Plan STP, Geosi Plan Flächenverwaltung |

Verknüpfung Plan-Fläche ⟷ Urkunde: Die Plan-Guid (`Guid_S`) steht in der `.fdoc` als `GuidPlanFlaeche`.

### 4.4 GeosiFORM 5

- Vorgängerversion von GeosiFORM 6, geschrieben in **VB.NET**.
- **Bei Kunden noch im Einsatz.** Bugmeldungen von Kunden kommen deshalb oft mit Form5-Testdateien (`.eig`). Diese müssen vor der Weitergabe anonymisiert werden, daher braucht auch Form5 ein Anonymisierungswerkzeug (6).
- Relativ isoliert von den anderen Geosi-Programmen. Einzige bekannte Schnittstelle: eine **Flächenübertragung zu GeosiPLAN** (Details noch nicht dokumentiert).
- **Urkundenformat `.eig`:** Access-Datenbank (MDB). GeosiFORM 6 kann `.eig` importieren („Import FORM...“): externer Konverter `IdcMdbToXmlConverter.exe` → XML → `EigFile` (`GeosiFormKernel\ImportV5.cs`, dort alle Tabellen und Felder) → Umwandlung in die Form6-Urkunde (`ImportV5EigToUrkunde.cs`).
- Eine aus `.eig` importierte Urkunde hat **keine Plan-Verknüpfung** (`GuidPlanFlaeche` leer), weil Form5 keine Plan-Guids kennt.
- Architektur von Form5 (Aufbau, Befehle, Speicherung) ist **noch nicht dokumentiert**. Bitte im Projekt GeosiFORM5 erheben und hier ergänzen.

---

## 5. Gemeinsame fachliche Konventionen

### 5.1 Begriffe und Schreibweisen

- **Teilung** ist der fachliche Begriff. Im Code heißt es teils „Zerlegung“ bzw. `Ze*`.
- **Grundstücksnummer:**
  - Führender Punkt = Bauparzelle: `.1146`.
  - Ohne Punkt = normales Grundstück: `1146`.
  - `.1146` und `1146` sind **verschiedene** Grundstücke.
  - `/Nenner` nur bei Nenner > 0. `1146/0` gibt es als Schreibweise nicht.
  - Neue Unterteilung einer Bauparzelle: `.1146/9`.
  - In der `.fdoc`: `<Nummer><IstBauparzelle>`/`<Zaehler>`/`<Nenner>`.
- **KG-Nummer** im Austausch mit Plan fünfstellig mit führenden Nullen (Format `"00000"`). In der `.fdoc` als Zahl ohne führende Nullen.
- **Restfläche (Plan):**
  - GeosiPLAN garantiert, dass Restfläche plus benannte Benützungsarten die Gesamtfläche ergeben.
  - Die Restfläche heißt „Rest“ und ist ein Benützungsart-Eintrag ohne Banu-Code.
  - Für Plan-Flächen zählt in Form6 die **Summe der Benützungsarten**.
- **Plan-Flächen werden nur in GeosiPLAN gelöscht**, nie aus Form heraus.

### 5.2 KG-Verzeichnis `Kg.xcfg`

- Pfad: siehe 3.2. XML, UTF-8.
- Aufbau:
  - `<KgMgr Version="1"><LastUpdate_T>…</LastUpdate_T><KgMgr_Items>` und darin je KG ein `<KG>`-Block.
  - Felder: `KG_L`/`KG_S` (Nummer/Name) sowie `GB_*`, `VA_*`, `PG_*`, `PB_*`, `BL_*` (Gerichtsbezirk, Vermessungsamt, Gemeinde, Bezirk, Bundesland), jeweils `_L` = Nummer und `_S` = Name.
- **Der STP-Export in GeosiPLAN verarbeitet KG-Nummern nicht korrekt, die in `Kg.xcfg` fehlen.** Beispiel: leere Tabellen im STP-Export.
- **Fiktive KGs** (Anonymisierung):
  - Bereich 90001–90999.
  - Dieser Bereich ist **nicht** frei: z. B. 90001–90019 und 90101–90110 sind echte KGs. Fiktive Nummern müssen deshalb gegen `Kg.xcfg` kollisionsfrei vergeben werden.
  - Eintrag in `Kg.xcfg`: Block der Original-KG klonen, nur `KG_L` ersetzen und `KG_S` = „Test-KG anonymisiert“ setzen.
  - Vorher Backup `Kg.xcfg.bak_JJJJMMTT_hhmmss` anlegen.

---

## 6. Anonymisierung von Testdaten (produktübergreifend)

Ziel: echte Projekte als Testdaten nutzen, ohne echte Personen- oder Grundstücksdaten.

- **Form6:** „Anonymisiert speichern unter...“ (`CmdAnonymSaveAs`). Eingebaut und getestet am 25.09.2026, Details im Projekt GeosiFORM6.
- **GeosiFORM5:** Anonymisierung von `.eig`-Urkunden nach denselben Regeln und mit derselben Zuordnungsdatei. **In Arbeit** (Projekt GeosiFORM5, Stand 28.09.2026).
- **GeosiPLAN:** gleichlautende Anonymisierung des Flächenmanagers und der Projekt-KG, Werkzeug `Cmd_Area_Mgr_Anonymize` (Aufruf `IDCP_CMD Cmd_Area_Mgr_Anonymize;`, Eingabe: `_Zuordnung.xml`). Eingebaut und getestet am 28.09.2026, Details im Projekt Geosi Plan Flächenverwaltung. Die Form-Anbindung an die anonymisierte `.fdoc` stellt der Anwender danach manuell um.

**Gemeinsame Regeln, damit beide Seiten zusammenpassen:**

| Daten | Behandlung |
|---|---|
| Personendaten (Namen, Geburtsdaten, Adressen inkl. roher BEV-Adresszeile `NotParsed`, Firma, Anrede, Titel, Vertretung) | Platzhalter (Mustermann, Musterstraße, 9999 Musterstadt …) oder geleert |
| Stammnummer der Grundstücke | zufällig, pro Dokument und Lauf konsistent, gilt für das ganze Dokument unabhängig von KG und Nenner |
| Nenner, Bauparzellen-Punkt | unverändert |
| KG und GB (gemeinsame Zuordnung) | fiktiv 90001–90999, kollisionsfrei gegen `Kg.xcfg`, dort nachtragen. Gilt auch für die Projekt-KG (Form `Metadata/KgNr`, Plan Projekteigenschaften) |
| KG-Werte `0` (nicht gesetzt) oder außerhalb 1–99999 (z. B. `-842150451` = `0xCDCDCDCD`, nicht initialisiert) | unverändert, nicht in die Zuordnung |
| EZ | zufällig, pro Dokument konsistent |
| Guids (inkl. `GuidPlanFlaeche`), Flächen, Benützungsarten | unverändert |
| GFN (Nummer, Jahr, VA-Nr.) | unverändert (offiziell einsehbar, kaum ausgegeben). Nur die KG darin über die KG-Zuordnung |
| Büro-Angaben (Company, Planverfasser) | unverändert |

Weitere Regeln:

- Kein fester Versatz wie „+5“, weil er rückrechenbar wäre.
- Keine dokumentübergreifende Zuordnung.

**Zuordnungsdatei `<Name>_Zuordnung.xml`:**

- Liegt neben der anonymisierten `.fdoc` bzw. `.eig`.
- Gleiches Format für Form6 und Form5, damit das Plan-Werkzeug beide lesen kann.
- Enthält `KgList`, `StammNrList`, `EzList` und `GrundstList` (Original ↔ Anonym).
- Sie ist die Eingabe für die Plan-Seite.
- Stammnummern oder KGs, die nur in Plan vorkommen, werden dort nach derselben Methode neu vergeben, ohne Kollision mit den Werten aus der Zuordnungsdatei.

**Bekannte Lücken:**

- Texte, Beschriftungen und Blöcke in der `.dwg` außerhalb des Flächenmanagers (z. B. eingefügte Grundstücksnummern) werden **nicht** anonymisiert.
- Die STP-Datendatei `<Zeichnung>_<KG>.xstp` wird nicht anonymisiert und nicht weitergegeben. Nach der Anonymisierung legt der STP-Export eine neue mit der fiktiven KG im Namen an.

---

## 7. Arbeitsweise mit Claude

- **Claude kann nicht kompilieren oder ausführen**: kein Windows, kein BricsCAD, kein Visual Studio. Der Entwickler baut und testet und meldet Compiler-Fehler und Testergebnisse zurück. Reine C#-Logik kann Claude teilweise vorab mit Mono gegen Stubs kompilieren und testen.
- **Übertragene Dateien werden immer byte-genau auf der Platte verifiziert.** Visual Studio hat mehrfach eine gerade geschriebene Datei sofort wieder mit dem alten Stand überschrieben. Deshalb: geänderte Dateien vor dem Bauen in VS schließen bzw. neu laden, **ohne zu speichern**.
- **Maßgeblich ist nur, was nach der Übertragung auf der Platte geprüft wurde.** Die Fassung einer Datei in der Leiste „Ausgaben“ der Claude-App bzw. ein Download daraus kann veraltet sein. Auch die Übertragung selbst hat schon eine ältere Fassung gleichen Namens geliefert, obwohl die Datei in der Sitzung aktuell war. Claude überträgt eine geänderte Datei deshalb im Zweifel unter neuem Namen und prüft das Ergebnis danach auf der Platte. Anwender verwenden die Datei am Zielort (z. B. im Repository-Klon), nicht einen Download aus „Ausgaben“.
- **Datei-Encoding:** GeosiPLAN-Quelldateien (`.cpp`/`.h`) sind **Windows-1252** und dürfen nicht als UTF-8 umgeschrieben werden (Regel im `CLAUDE.md` des Plan-Repositorys). Dateien in `IdcShared_Cpp_GeosiForm` sind UTF-8. Neue Dateien schreibt Claude in reinem ASCII (Umlaute nur als Escape, Kommentare ohne Umlaute), dann passen sie zu beiden.
- **VB.NET-Quellen (GeosiFORM5):** Encoding der Quelldateien vor der ersten Änderung prüfen und beibehalten, analog zur Regel für GeosiPLAN. Erfahrungen dazu gibt es noch keine.
- **Umlaute in C++-String-Literalen** als Escape schreiben: `\u00E4` usw. für ä, ö, ü, Ä, Ö, Ü, ß. Sonst zeigt MSVC nach einer Komplett-Übertragung der Datei alle Umlaute der Datei falsch an (z. B. „ZusÃ¤tzlich“). Kommentare sind nicht betroffen.
- **Transport über `DataXmlCollection`:**
  - Nur einfache Elemente mit Textinhalt, **keine Attribute, keine Self-Closing-Tags**.
  - `CmdFactory` schickt immer einen zusätzlichen Eintrag `IdcWindowId` mit. Nutzdaten deshalb an fester Position (Index 0) erwarten oder gezielt per Key suchen, nie per Ausschlussverfahren.
- **Code-Kommentare** bei Änderungen mit Datum und Urheber („Claude, TT.MM.JJJJ“) und kurzer Begründung.
- **Testcode** klar markieren (`#region TEST-ONLY …`, Schalter wie `TestModeEnabled`) und leicht entfernbar halten.
- **Neue Plan- oder Form-Themen** bekommen eigene Dokumente im zuständigen Projekt. Dokumente vor dem Überschreiben vollständig lesen: Im Form6-Projekt ging einmal ein Dokument durch Überschreiben mit einem Platzhalter verloren.

---

## 8. Datenschutz bei Testdaten

- **Echte Kundendaten gehören nicht ins Repository**, auch nicht in angeblich anonymisierter Form, ohne vorherige Prüfung.
  - Beispiel: Die Datei `9909-temp_Anonym.fdoc` enthielt vor dem `NotParsed`-Fix vom 25.09.2026 trotz Anonymisierung eine echte Adresse.
  - Ältere anonymisierte Dateien können echte Werte enthalten, die damals noch nicht erfasst wurden (`NotParsed`, `NoGuid_KgNach`, `GstBetroffen`). **Im Zweifel mit dem aktuellen Tool neu anonymisieren.**
- **Die Zuordnungsdatei `_Zuordnung.xml` hebt die Anonymisierung auf.** Nie zusammen mit der anonymisierten `.fdoc` oder Plan-Datei weitergeben, hochladen oder einchecken.
- Synthetische Testdaten, z. B. `CmdAreaSyncTestHarness\synthetic_testdata`, sind unbedenklich.

---

## 9. Offene Punkte (projektübergreifend)

1. ~~Endgültigen Ablageort festlegen~~ – erledigt: Repository GeosiBasiswissen (1.2).
2. ~~GeosiPLAN-Quellcode-Pfade ergänzen (3.1)~~ – erledigt 28.09.2026.
3. `Kg.xcfg`-Pfad im Form6-Code nicht fest hinterlegen, sondern von GeosiPLAN beziehen (3.4). Quelle in GeosiPLAN ermittelt (28.09.2026), Umsetzung im Projekt GeosiFORM6 offen.
4. Plan-Architektur vollständig dokumentieren (4.2, teilweise erhoben).
5. Anonymisierung der `.dwg`-Texte und -Blöcke außerhalb des Flächenmanagers (6).
6. GeosiFORM5: Quellcodepfad (3.1), Architektur und Schnittstelle zu GeosiPLAN (4.4) dokumentieren.

---

## 10. Änderungshistorie

| Version | Datum | Änderung | Von |
|---|---|---|---|
| 1 | 25.09.2026 | Erstfassung aus dem Projekt GeosiFORM6 | Claude, zur Prüfung durch Martin |
| 2 | 25.09.2026 | 1.2: Vorgehen beim Ersetzen der Projektkopie (erst löschen, dann einfügen; aus dem Klon importieren). 7: Nur der auf der Platte geprüfte Stand ist maßgeblich, nicht „Ausgaben“ bzw. Download. | Claude, auf Hinweis von Martin |
| 3 | 28.09.2026 | 2: zwei Übergaben Geosi Plan Flächenverwaltung → GeosiFORM6. 3.1: GeosiPLAN-Quellcodepfad. 3.4/9: Quelle des `Kg.xcfg`-Pfads in GeosiPLAN. 4.2: erste Angaben zur Plan-Architektur. 6: Plan-Werkzeug `Cmd_Area_Mgr_Anonymize` eingebaut und getestet, Regel für ungültige KG-Werte, Projekt-KG, `.xstp`. 7: Datei-Encoding GeosiPLAN. | Claude, aus dem Projekt „Geosi Plan Flächenverwaltung“, zur Prüfung durch Martin |
| 4 | 28.09.2026 | 2: Projekt GeosiFORM5 und Übergabe GeosiFORM6 → GeosiFORM5. 3.1: Platzhalter Form5-Quellcode. 4: Hinweis, dass 4.1 nur für Form6 gilt; neuer Abschnitt 4.4 GeosiFORM 5. 6: Form5-Anonymisierung in Arbeit, Zuordnungsdatei auch für `.eig`. 7: Encoding VB.NET. 9: offener Punkt 6. | Claude, aus dem Projekt „GeosiFORM6“, zur Prüfung durch Martin |
