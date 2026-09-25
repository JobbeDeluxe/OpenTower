# Architekturentwurf

## Grundentscheidung

OpenTower wird als **Hybrid aus Godot 4 und einem C#/.NET-Simulationskern** entwickelt.

Godot ist nicht die Simulation selbst, sondern vor allem Host für:

- Rendering
- UI
- Kamera
- Input
- Audio
- Animation
- Szenen und Editor-Tooling

Die eigentliche Spielsimulation liegt soweit sinnvoll in einem **Godot-unabhängigen C#-Core**.

Dadurch vermeiden wir, dass langfristig tausende Personen, Räume oder Aufzugszustände direkt an Godot-Nodes gekoppelt sind.

## Zielarchitektur

```text
                OpenTower
                    |
       +------------+------------+
       |                         |
  Godot Presentation        OpenTower.Core
       |                         |
 Rendering                    Simulation Clock
 UI                           Agents
 Camera                       Building Model
 Input                        Economy
 Audio                        Transport
 Animation                    Pathfinding
       |                         |
       +---- OpenTower.Godot ----+
              Adapter Layer
```

## Projekte

### OpenTower.Core

C# Class Library ohne direkte Abhängigkeit von Godot.

Verantwortlich für:

- Simulationszeit
- Agenten
- Räume
- Gebäude
- Aufzüge
- Warteschlangen
- Wirtschaft
- Zustandsmaschinen
- Events
- Savegame-Datenmodelle
- langfristig Wegfindung

Vorteil: Dieser Teil kann mit normalen .NET-Tests getestet und bei Bedarf sogar ohne Godot ausgeführt werden.

### OpenTower.Godot

Godot-spezifische C#-Schicht.

Verantwortlich für:

- Übersetzung zwischen Core und Godot
- Erzeugen / Pooling sichtbarer Sprites
- Input-Aktionen
- Bauwerkzeuge
- UI-Bindings
- Kamera
- Darstellung von Debug-Informationen

Diese Schicht soll möglichst wenig eigentliche Spiellogik enthalten.

### OpenTower.Core.Tests

Unit- und Simulationstests für den Core.

Beispiele:

- Aufzug nimmt maximal N Agenten auf
- Agent verlässt Warteschlange korrekt
- Büro erzeugt definierte Einnahmen
- 10.000 Ticks liefern reproduzierbaren Zustand
- Speichern / Laden erhält Simulationszustand

## Simulation Core

Die Simulation arbeitet mit Datenobjekten statt mit einem Godot-Node pro Objekt.

Beispiel:

```text
Agent
- Id
- Position
- CurrentFloor
- Destination
- State
- WaitTime
- Mood
```

Ein Agent kann damit existieren und simuliert werden, auch wenn er gerade nicht gerendert wird.

## Agent Simulation

Agenten verwenden zunächst eine einfache Zustandsmaschine:

```text
ENTER_BUILDING
→ WALK_TO_ELEVATOR
→ WAIT_FOR_ELEVATOR
→ RIDE_ELEVATOR
→ WALK_TO_DESTINATION
→ WORK
→ LEAVE
```

Später kann daraus ein flexibleres Task-/Needs-System werden.

## Building Model

Das Gebäudemodell verwaltet:

- Grundstück
- Etagen
- Zellen / Raster
- Räume
- Zugänge
- vertikale Transportwege

Räume besitzen Daten wie:

- Typ
- Position
- Größe
- Kosten
- Kapazität
- Öffnungsstatus
- Einnahmen
- Betriebskosten

## Transport

Aufzüge sind ein separates Core-System.

Sie verwalten:

- Kabinen
- Etagenstopps
- Rufanforderungen
- Kapazität
- Fahrzeiten
- Ein-/Ausstieg
- Warteschlangen
- spätere Dispatching-Strategien

Agenten stellen Transportanforderungen; das Transportsystem löst sie.

## Rendering

Rendering liest den Core-Zustand und stellt ihn dar.

Wichtig:

- Der Core darf ohne sichtbare Nodes laufen.
- Nicht jede Person bekommt permanent einen komplexen Node.
- Sichtbare Agenten werden gepoolt.
- Rendering-Framerate und Simulationsrate sind getrennt.

## UI

UI verändert die Simulation nur über definierte Commands bzw. Services, zum Beispiel:

```text
BuildRoom(type, position)
BuildFloor(level)
BuildElevator(column, minFloor, maxFloor)
Demolish(objectId)
```

UI soll keine internen Core-Daten direkt manipulieren.

## Tick-System

Simulation und Rendering laufen getrennt.

Beispiel:

- Rendering: je nach Framerate
- Simulation Core: feste Tickrate
- Agentenentscheidungen: nach Bedarf / in Intervallen
- Aufzugsteuerung: feste oder ereignisgesteuerte Intervalle
- Wirtschaft: deutlich seltener
- Langzeitstatistik: sehr selten

Das ermöglicht reproduzierbare Simulationen und verhindert, dass das Spielverhalten von 60 oder 144 FPS abhängt.

## Datengetriebenes Design

Raumtypen, Kosten und Balancing sollen möglichst nicht hart im Code stehen.

Beispiel:

```json
{
  "id": "office_small",
  "build_cost": 5000,
  "capacity": 8,
  "daily_rent": 450
}
```

## Raster

Für den ersten Prototypen verwenden wir ein diskretes 2D-Raster:

- X = horizontale Gebäudeposition
- Y = Stockwerk

Jede Einrichtung belegt eine oder mehrere Rasterzellen.

## Performance-Ziel

Der erste Prototyp muss noch keine 10.000 sichtbaren Figuren darstellen.

Der Core soll aber von Anfang an so strukturiert werden, dass große Simulationsmengen möglich bleiben.

Zwischenziele:

- einige hundert Agenten im ersten Gameplay-Prototyp
- 1.000+ Agenten als früher Performance-Test
- später 5.000–10.000 simulierte Agenten untersuchen

Optimiert wird anhand von Messungen, nicht vorsorglich durch unnötig komplizierten Code.

## Warum nicht alles in Godot-Nodes?

Ein Node pro sichtbarem Objekt ist für Darstellung völlig in Ordnung.

Für eine große Managementsimulation entstehen aber unnötige Abhängigkeiten, wenn jeder logische Agent, jede Warteschlangenposition und jeder Wirtschaftszustand direkt Teil des Szenenbaums wird.

Der getrennte C#-Core bringt:

- bessere Testbarkeit
- klare Zuständigkeiten
- einfacheres Profiling
- geringere Engine-Kopplung
- bessere Möglichkeiten für große Agentenzahlen
- einfachere Headless-Simulation
- später leichter austauschbare Darstellung

## Noch offene Entscheidungen

- genaue Rastergröße
- Pixel-Art vs. höher aufgelöste 2D-Grafik
- eigenes Grid-Pathfinding vs. hybride Navigation
- Savegame-Format
- JSON vs. C#-Definitionen vs. Godot Resources für Content-Daten
- Event-Bus / Commands / Observer-Struktur
- feste Simulations-Tickrate
