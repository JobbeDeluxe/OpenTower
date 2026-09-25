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
- sonstigen extrahierten Originalressourcen

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

## Forschungsnotizen

Bei der Untersuchung älterer Spiele sollten wir Fakten und Verhalten beschreiben, ohne geschützte Inhalte unnötig zu kopieren.

Gut:

- Raum kostet ungefähr X
- Gebäude erreicht Stufe Y unter Bedingung Z
- Aufzug hat beobachtetes Verhalten A

Vermeiden:

- große Originaltabellen vollständig übernehmen
- Texte oder Beschreibungen 1:1 kopieren
- extrahierte Assets committen

## Originaldateien auf Entwicklerrechnern

Falls später für Forschung ein lokal installiertes Originalspiel verwendet wird:

- nicht committen
- nicht in Releases aufnehmen
- Pfade in `.gitignore` berücksichtigen
- Tools möglichst so bauen, dass der Nutzer eigene Dateien auswählen muss

## Projektname und Marken

OpenTower ist derzeit nur ein Arbeitstitel.

Vor einer öffentlichen Veröffentlichung oder Vermarktung müssen Name, Logo und mögliche Markenrisiken gesondert geprüft werden.

## Lizenz

Aktuell ist keine Open-Source-Lizenz festgelegt.

Ohne ausdrückliche Lizenz entsteht dadurch keine automatische Erlaubnis für Dritte, den Code beliebig zu kopieren oder weiterzuverbreiten.

Eine Lizenzentscheidung treffen wir später bewusst.
