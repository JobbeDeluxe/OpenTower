# Rechtliche Leitlinien für OpenTower

Diese Datei ist eine interne Projektleitlinie und keine Rechtsberatung.

## Ziel

OpenTower soll eine eigenständige Tower-Management-Simulation werden.

SimTower kann als Referenz für Spielmechaniken, Bedienkonzepte und historische Recherche dienen. Geschützte Originalinhalte sollen jedoch nicht Bestandteil dieses Repositorys werden.

## Nicht ins Repository

Insbesondere keine:

- Original-EXE oder Installationsdateien
- Original-DAT-/Ressourcendateien
- Original-Sprites oder Grafiken
- Originalmusik
- Originalsounds
- kopierten Texte
- Handbuchscans
- Logos
- ROM-/ISO-/Disk-/Installationsabbilder
- sonstigen extrahierten Originalressourcen

Das gilt auch dann, wenn solche Dateien in einem fremden öffentlichen Repository zu finden sind.

## Eigene Implementierung

Mechaniken werden durch Beobachtung beschrieben und anschließend eigenständig implementiert.

Beispiel:

Erlaubter Entwicklungsansatz:

```text
Beobachtung:
Ein Büro erzeugt morgens Besucher und diese fahren per Aufzug zum Ziel.

Eigene Implementierung:
Wir entwickeln dafür selbst Agenten-, Zeit-, Wege- und Aufzugslogik.
```

Nicht der gewünschte Ansatz:

```text
Originalcode oder extrahierte Ressourcendaten übernehmen und direkt weiterverwenden.
```

## Fremde Open-Source-Projekte

Auch öffentlich sichtbarer Quellcode darf nicht automatisch beliebig übernommen werden.

Vor jeder Codeübernahme prüfen wir:

- konkrete Lizenz
- Lizenzversion
- Copyleft-Pflichten
- notwendige Attribution
- Kompatibilität mit der späteren OpenTower-Lizenz
- Herkunft eingebundener Assets und Binärdateien

### OpenSkyscraper

OpenSkyscraper ist GPL-2.0-lizenziert.

Solange die endgültige OpenTower-Lizenz nicht feststeht, verwenden wir OpenSkyscraper primär als Forschungs- und Architektur-Referenz und kopieren keinen Source Code daraus in OpenTower.

### ConciliaTower

Zum Zeitpunkt unserer Prüfung am 2026-09-26 war keine eindeutige Root-Lizenzdatei für den eigenen Projektcode sichtbar. Interne Projektunterlagen nennen GPL als beabsichtigte Lizenz.

Bis eine klare Lizenz veröffentlicht ist, wird daraus kein Code übernommen.

### YootTower / historische Originalquellen

Das öffentliche YootTower-Repository dokumentiert einen historischen Source-Code-Drop von Yoot Saito und nennt ausdrücklich alte Maxis-SimTower-Quellen. Der vollständige historische Source ist im sichtbaren Repository jedoch noch nicht veröffentlicht; laut README soll dies erst nach Prüfung, Freigabe und Relizenzierung erfolgen.

Unveröffentlichter Originalcode wird daher nicht als frei nutzbar betrachtet.

Details und Links stehen in [REFERENCE_PROJECTS.md](REFERENCE_PROJECTS.md).

## Forschungsnotizen

Bei der Untersuchung älterer Spiele sollten wir Fakten und Verhalten beschreiben, ohne geschützte Inhalte unnötig zu kopieren.

Gut:

- Raum kostet ungefähr X
- Gebäude erreicht Stufe Y unter Bedingung Z
- Aufzug hat beobachtetes Verhalten A
- Dateifeld X scheint Funktion Y zu besitzen

Vermeiden:

- große Originaltabellen vollständig übernehmen
- Texte oder Beschreibungen 1:1 kopieren
- extrahierte Assets committen
- fremden Source Code ohne vorherige Lizenzentscheidung übertragen

## Originaldateien auf Entwicklerrechnern

Eigene lokal vorhandene Originaldateien können für Forschung und Kompatibilitätstests getrennt vom Repository gehalten werden.

Regeln:

- nicht committen
- nicht in Releases aufnehmen
- Pfade in `.gitignore` berücksichtigen
- Originaldateien nicht als Test-Fixtures veröffentlichen
- Tools möglichst so bauen, dass der Nutzer seine eigenen lokalen Dateien auswählen muss

Eine mögliche spätere Architektur ist ein optionaler Legacy-Importer, der eine vom Nutzer bereitgestellte `SIMTOWER.EXE` oder `.TWR`/`.TDT`-Datei liest.

Das bedeutet jedoch nicht automatisch, dass Originalgrafiken oder Sounds in einem öffentlichen OpenTower-Release genutzt oder weiterverteilt werden dürfen. Die rechtliche Bewertung eines solchen optionalen Runtime-Imports wird vor einer Veröffentlichung separat geprüft.

## Projektname und Marken

OpenTower ist derzeit nur ein Arbeitstitel.

Vor einer öffentlichen Veröffentlichung oder Vermarktung müssen Name, Logo und mögliche Markenrisiken gesondert geprüft werden.

## Lizenz

Aktuell ist keine Open-Source-Lizenz festgelegt.

Ohne ausdrückliche Lizenz entsteht dadurch keine automatische Erlaubnis für Dritte, den Code beliebig zu kopieren oder weiterzuverbreiten.

Eine Lizenzentscheidung treffen wir später bewusst.
