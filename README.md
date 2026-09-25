# GeosiBasiswissen

Gemeinsames Grundlagenwissen für die Entwicklung der Geosi-Produkte (GeosiFORM, GeosiPLAN).

Angelegt von Martin Ruetz, IDC EDV, im September 2026.

## Wozu dieses Repository da ist

Bei der Entwicklung von GeosiFORM und GeosiPLAN entsteht laufend Wissen, das nicht im Code steht, aber für die Arbeit daran wichtig ist:

- wie die Programme und Prozesse zusammenspielen,
- welche Schnittstellen es zwischen Form und Plan gibt,
- welche fachlichen Schreibweisen und Regeln gelten,
- welche Pfade und Build-Voraussetzungen nötig sind,
- welche Fallstricke es gibt.

Dieses Wissen war bisher über einzelne Köpfe, Rechner und Notizen verteilt. Dieses Repository hält den **produktübergreifenden Teil** davon an einer zentralen, versionierten Stelle fest, für alle Kollegen erreichbar.

Anlass war die Arbeit mit dem KI-Assistenten Claude. Er wird in mehreren getrennten Projekten eingesetzt, je Programmbereich eines, z. B. GeosiFORM6, Geosi Plan STP und Geosi Plan Flächenverwaltung. Diese Projekte können sich gegenseitig nicht sehen. Wissen, das alle brauchen, würde sonst in jedes Projekt einzeln kopiert und dort auseinanderlaufen. Deshalb gibt es hier **eine maßgebliche Fassung**, von der die Projekte ihre Kopien beziehen.

Der Inhalt ist aber **nicht nur für die KI gedacht**. Er ist genauso als Einstieg und Nachschlagewerk für Kollegen geschrieben, die an Geosi-Code arbeiten.

## Inhalt

| Datei | Inhalt |
|---|---|
| `Geosi-Basis.md` | Das Basisdokument: Projektlandschaft und Zuständigkeiten, Pfade (was bei allen gleich ist und was nicht), Architektur von GeosiFORM 6, Schnittstelle Form ⟷ Plan, fachliche Konventionen, KG-Verzeichnis, Regeln zur Anonymisierung von Testdaten, Arbeitsweise mit Claude, Datenschutz, offene Punkte |
| `README.md` | diese Erklärung |

## Was hier nicht hineingehört

- **Detailwissen eines einzelnen Programmbereichs**, z. B. einzelne Bugs, Testfälle oder Feldkataloge. Das gehört in das jeweils zuständige Claude-Projekt bzw. dessen Dokumentation.
- **Echte Kundendaten**, auch nicht in angeblich anonymisierter Form ohne Prüfung.
- **Zuordnungsdateien `*_Zuordnung.xml`** aus der Anonymisierung. Sie enthalten die echten Grundstücksdaten und heben die Anonymisierung auf.
- Quellcode. Der liegt in den jeweiligen Produkt-Repositories.

## Verwendung

**Als Entwickler:**

- Repository klonen, am besten neben die übrigen Geosi-Repositories, z. B. `<GEOSI_ROOT>\GeosiBasiswissen`.
- `Geosi-Basis.md` lesen. Pfade darin sind relativ zu `<GEOSI_ROOT>` angegeben. Das ist der Ordner, in dem die Geosi-Repositories nebeneinander liegen und der bei jedem Kollegen anders heißen kann (Abschnitt 3 des Basisdokuments).

**In Claude-Projekten:**

- In jedes Geosi-Claude-Projekt kommt eine **unveränderte Kopie** von `Geosi-Basis.md`.
- Wird das Dokument hier geändert, wird die Kopie in den Projekten durch die neue Fassung **ersetzt**, nicht dort von Hand nachgebessert.
- Maßgeblich ist immer die Fassung in diesem Repository. Welche Fassung eine Kopie hat, steht oben im Dokument unter Version und Stand.

## Änderungen

- Änderungen nur über dieses Repository, per Commit, bei größeren Änderungen per Pull Request mit Review.
- Bei jeder inhaltlichen Änderung im Basisdokument **Version und Stand** oben erhöhen und einen Eintrag in der **Änderungshistorie** (letzter Abschnitt) ergänzen.
- Neue Erkenntnisse aus Claude-Sitzungen, die produktübergreifend sind, werden als Änderungsvorschlag für dieses Repository formuliert und hier eingepflegt.

## Ansprechpartner

Martin Ruetz, IDC EDV
