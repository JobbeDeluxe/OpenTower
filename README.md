# OpenTower

OpenTower ist eine eigenständige Tower-Management-Simulation, inspiriert von klassischen Aufbau- und Hochhaus-Simulationen der 1990er Jahre.

Ziel ist **kein 1:1-Klon mit übernommenen Originaldateien**, sondern eine moderne, neu entwickelte Simulation mit eigenem Code, eigenen Assets und eigener technischer Architektur.

## Projektstatus

**Phase 0 – Projektaufbau**

Aktuell entsteht die technische Grundlage. Der erste spielbare Prototyp soll einen sehr kleinen, aber vollständigen Gameplay-Loop abbilden:

1. Grundstück / Baufläche anzeigen
2. Etage bauen
3. Lobby platzieren
4. Aufzug bauen
5. Büro platzieren
6. Besucher erscheinen lassen
7. Besucher warten auf den Aufzug
8. Besucher fahren zum Ziel
9. Büro erzeugt Einnahmen

Wenn dieser Loop funktioniert, wird die Simulation schrittweise erweitert.

## Geplanter Tech-Stack

- **Engine:** Godot 4.x
- **Sprache:** GDScript
- **Plattform zuerst:** Windows
- **Repository:** GitHub
- **Grafik:** eigene Pixel-/2D-Assets
- **Simulation:** datengetrieben, möglichst unabhängig von Darstellung und UI

Die Engine-Entscheidung ist für den Start gesetzt, kann bei guten technischen Gründen später geändert werden.

## Kernsysteme

OpenTower soll langfristig unter anderem folgende Systeme enthalten:

- mehrstöckiges Gebäuderaster
- Räume und Einrichtungen
- Personen / Besucher / Bewohner / Angestellte
- Wegfindung
- Aufzüge und Warteschlangen
- Tageszeit
- Wirtschaftssystem
- Mieten, Einnahmen und Betriebskosten
- Zufriedenheit / Nachfrage
- Gebäudestatus und Progression
- Events und Störungen
- Speichern / Laden
- Debug- und Simulationswerkzeuge

## Projektstruktur

Geplant:

```text
/
├─ assets/             Eigene Grafiken, Audio und Fonts
├─ data/               Daten für Räume, Preise, Balancing usw.
├─ scenes/             Godot-Szenen
├─ scripts/
│  ├─ building/        Gebäude, Etagen, Räume
│  ├─ simulation/      Zeit, Wirtschaft, globale Simulation
│  ├─ agents/          Personen und Verhalten
│  ├─ transport/       Aufzüge, Treppen, Wegfindung
│  └─ ui/              Benutzeroberfläche
├─ docs/               Architektur, Forschung, rechtliche Hinweise
└─ tests/              Tests für Simulationslogik
```

Die Ordner werden angelegt, sobald dort die ersten Dateien benötigt werden.

## Roadmap

Die aktuelle Aufgabenliste steht in [TODO.md](TODO.md).

Technische Grundentscheidungen stehen in [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md).

Hinweise zur Abgrenzung gegenüber SimTower und anderen älteren Spielen stehen in [docs/LEGAL.md](docs/LEGAL.md).

## Umgang mit SimTower

SimTower dient ausschließlich als **Referenz für Spielmechaniken und Forschungszwecke**.

In diesem Repository sollen insbesondere **nicht** eingecheckt werden:

- Originalprogrammdateien
- Originalcode
- Originalgrafiken oder Sprites
- Originalmusik oder Sounds
- kopierte Texte oder Handbuchinhalte
- ROM-/Disk-/Installationsabbilder
- sonstige urheberrechtlich geschützte Originalressourcen

Spielmechaniken können untersucht und anschließend eigenständig implementiert werden.

## Name

**OpenTower** ist derzeit ein Arbeitstitel.

## Lizenz

Derzeit wurde bewusst **keine Open-Source-Lizenz** vergeben. Bis wir uns dafür entscheiden, gelten die normalen urheberrechtlichen Regeln für den hier entwickelten Code und die Assets.

---

OpenTower ist ein unabhängiges Fan-/Hobbyprojekt und steht in keiner Verbindung zu Maxis, Electronic Arts oder den ursprünglichen Entwicklern von SimTower.
