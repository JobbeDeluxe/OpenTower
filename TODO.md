# OpenTower – TODO / Roadmap

Diese Liste ist nach Entwicklungsphasen sortiert. Ziel ist zuerst ein funktionierender Kern.

## Phase 0 – Projektbasis

- [x] Repository anlegen
- [x] README erstellen
- [x] `.gitignore` anlegen
- [x] technische Architektur dokumentieren
- [x] rechtliche Leitlinien dokumentieren
- [x] relevante SimTower-Nachbauten und Forschungsquellen dokumentieren
- [x] Architekturentscheidung: Godot 4 + C#/.NET Simulation Core
- [ ] Godot 4 **.NET** Projekt initialisieren
- [ ] C# Solution / Projekte anlegen
- [ ] `OpenTower.Core` als Godot-unabhängige Class Library anlegen
- [ ] `OpenTower.Godot` Integration anlegen
- [ ] `OpenTower.Core.Tests` anlegen
- [ ] Basisordner erstellen
- [ ] Namens- und Lizenzentscheidung später treffen

## Phase 1 – Minimaler spielbarer Prototyp

### C# Simulation Core
- [ ] Simulationsuhr / Tick-System
- [ ] Gebäuderaster als Datenmodell
- [ ] Etagen und belegte Zellen
- [ ] Raum-Basismodell
- [ ] Agent-Basismodell
- [ ] Zustandsmaschine für Agenten
- [ ] Aufzug-Basismodell
- [ ] Warteschlangen
- [ ] einfache Wirtschaft / Kontostand

### Godot Darstellung / UI
- [ ] leere Baufläche darstellen
- [ ] Gebäuderaster visualisieren
- [ ] Etagen platzierbar machen
- [ ] Lobby platzierbar machen
- [ ] Büro platzierbar machen
- [ ] einfachen Aufzug platzierbar machen
- [ ] sichtbare Agenten darstellen
- [ ] Geldanzeige
- [ ] Spielzeit pausieren / fortsetzen
- [ ] Debug-Anzeige für Agenten und Wege

### Erster kompletter Gameplay-Loop
- [ ] Personen erzeugen
- [ ] Personen zu Lobby und Aufzug laufen lassen
- [ ] Warteschlange am Aufzug
- [ ] Aufzug fährt Personen auf Zielstockwerk
- [ ] Personen erreichen Büro
- [ ] Büro erzeugt Einnahmen
- [ ] Core läuft unabhängig von der Framerate
- [ ] Core kann ohne Godot-Oberfläche getestet werden

## Phase 2 – Solide Simulation

- [ ] Tageszeit
- [ ] unterschiedliche Agententypen
- [ ] Büroangestellte
- [ ] Bewohner
- [ ] Besucher
- [ ] Öffnungszeiten
- [ ] Nachfrage
- [ ] Betriebskosten
- [ ] Mieteinnahmen
- [ ] einfache Zufriedenheit
- [ ] Agenten verlassen das Gebäude wieder
- [ ] mehrere Aufzüge
- [ ] Aufzugsgruppen
- [ ] Kapazitätsgrenzen
- [ ] Wartezeiten auswerten
- [ ] Performance-Test mit 1.000+ Agenten
- [ ] Performance-Test mit 5.000+ Agenten

## Phase 3 – Gebäudemanagement

- [ ] Restaurants
- [ ] Geschäfte
- [ ] Wohnungen
- [ ] Hotels
- [ ] Service-Räume
- [ ] Treppen / Rolltreppen
- [ ] Reinigung
- [ ] Wartung
- [ ] Strom / Betriebskosten
- [ ] Raum-Upgrades
- [ ] Abrisswerkzeug
- [ ] Baukosten und Rückerstattungen

## Phase 4 – Progression

- [ ] Fortschritts-/Bewertungssystem
- [ ] Freischaltungen
- [ ] Besucherziele
- [ ] Gebäudeklassen
- [ ] besondere Ereignisse
- [ ] Störungen
- [ ] Sicherheits- und Komfortwerte

## Phase 5 – Savegame & Tools

- [ ] Speichern
- [ ] Laden
- [ ] Savegame-Versionierung
- [ ] Auto-Save
- [ ] Debug-Konsole
- [ ] Simulationsgeschwindigkeit
- [ ] Profiler für Agentenzahlen
- [ ] Balancing-Daten extern halten
- [ ] Headless-Core-Tests
- [ ] optionalen Legacy-Import als getrenntes Modul entwerfen
- [ ] TWR/TDT-Import prüfen
- [ ] Versionserkennung für lokale SIMTOWER.EXE prüfen

## Phase 6 – Recherche SimTower

Nur Beobachtung und Dokumentation, keine ungeprüfte Übernahme geschützter Inhalte oder fremder Quelltexte.

- [ ] OpenSkyscraper Architektur und Ressourcen-Lader untersuchen
- [ ] ConciliaTower Mechanik-/Format-Dokumentation untersuchen
- [ ] YootTower Code Map auswerten
- [ ] tower-docs TDT-Spezifikation auswerten
- [ ] Raumtypen erfassen
- [ ] Progressionslogik untersuchen
- [ ] Aufzugsverhalten dokumentieren
- [ ] Besucherströme beobachten
- [ ] Tagesabläufe dokumentieren
- [ ] Wirtschaftswerte grob vergleichen
- [ ] UI-Konzepte analysieren
- [ ] NE-Ressourcenformat der eigenen Originaldateien untersuchen
- [ ] eigene Designentscheidungen daraus ableiten
- [ ] YootTower-Repository später erneut auf veröffentlichte Originalquellen + Lizenz prüfen

## Später / Ideen

- [ ] Szenario-Modus
- [ ] Sandbox-Modus
- [ ] Mods
- [ ] Steam-Deck/Linux
- [ ] Controller-Unterstützung
- [ ] eigene Karten / Grundstücke
- [ ] modifizierbare Datendateien
- [ ] Statistiken und Heatmaps
- [ ] detaillierte Aufzugsteuerung
- [ ] Brand- und Evakuierungssysteme
- [ ] Multiplayer nur prüfen, nicht priorisieren
