# OpenTower

OpenTower ist eine eigenständige Tower-Management-Simulation, inspiriert von klassischen Aufbau- und Hochhaus-Simulationen der 1990er Jahre.

Ziel ist **kein 1:1-Klon mit übernommenen Originaldateien**, sondern eine moderne, neu entwickelte Simulation mit eigenem Code, eigenen Assets und eigener technischer Architektur.

## Projektstatus

**Phase 0 – Projektaufbau**

Der erste spielbare Prototyp soll einen kleinen, vollständigen Gameplay-Loop abbilden:

1. Grundstück / Baufläche anzeigen
2. Etage bauen
3. Lobby platzieren
4. Aufzug bauen
5. Büro platzieren
6. Besucher erscheinen lassen
7. Besucher warten auf den Aufzug
8. Besucher fahren zum Ziel
9. Büro erzeugt Einnahmen

## Tech-Stack

OpenTower wird bewusst als **Hybrid aus Godot 4 und C#/.NET** aufgebaut.

- **Engine / Rendering / UI:** Godot 4.x .NET
- **Simulation Core:** C# / .NET
- **Plattform zuerst:** Windows
- **Repository:** GitHub
- **Grafik:** eigene 2D-/Pixel-Assets
- **Simulation:** datengetrieben und möglichst unabhängig von Rendering und UI

Godot übernimmt Rendering, Szenen, Eingabe, UI, Audio und Tooling. Die eigentliche Spielsimulation wird als möglichst eigenständiger C#-Kern entwickelt.

## Architekturprinzip

```text
                OpenTower
                    |
       +------------+------------+
       |                         |
     Godot                  C# Simulation Core
       |                         |
 Rendering                    Agenten
 UI                           Aufzüge
 Kamera                       Wirtschaft
 Input                        Tageszeit
 Audio                        Wegfindung
 Animation                    Gebäudemodell
```

Eine simulierte Person muss nicht automatisch ein vollständiger Godot-Node sein. Der C#-Core kann tausende Agenten als reine Datenobjekte verwalten, während Godot nur die sichtbaren oder relevanten Agenten rendert.

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
├─ OpenTower.sln
├─ project.godot
├─ assets/
├─ data/
├─ scenes/
├─ src/
│  ├─ OpenTower.Core/
│  │  ├─ Agents/
│  │  ├─ Building/
│  │  ├─ Economy/
│  │  ├─ Simulation/
│  │  └─ Transport/
│  └─ OpenTower.Godot/
├─ ui/
├─ docs/
└─ tests/
   └─ OpenTower.Core.Tests/
```

## Roadmap

Die aktuelle Aufgabenliste steht in [TODO.md](TODO.md).

Technische Grundentscheidungen stehen in [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md).

Hinweise zur Abgrenzung gegenüber SimTower stehen in [docs/LEGAL.md](docs/LEGAL.md).

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

## Name

**OpenTower** ist derzeit ein Arbeitstitel.

## Lizenz

Derzeit wurde bewusst **keine Open-Source-Lizenz** vergeben.

---

OpenTower ist ein unabhängiges Fan-/Hobbyprojekt und steht in keiner Verbindung zu Maxis, Electronic Arts oder den ursprünglichen Entwicklern von SimTower.
