# Architekturentwurf

## Grundprinzip

Die Simulation soll von Anfang an möglichst klar von Darstellung und Benutzeroberfläche getrennt sein.

Das verhindert, dass tausende Agenten direkt als vollwertige Godot-Nodes simuliert werden müssen und erleichtert spätere Optimierungen.

## Vorgeschlagene Schichten

### 1. Simulation Core

Verantwortlich für:

- Spielzeit
- Geld
- globale Zustände
- Agentenzustände
- Raumzustände
- Nachfrage
- Events

Die Simulationslogik sollte möglichst unabhängig von Rendering und UI funktionieren.

### 2. Building Model

Datenmodell für:

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

### 3. Agent Simulation

Agenten sollten zunächst einfache Zustandsmaschinen verwenden.

Beispiel:

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

### 4. Transport

Aufzüge sind ein eigenes Simulationssystem.

Sie verwalten unter anderem:

- Kabinen
- Etagenstopps
- Rufanforderungen
- Kapazität
- Fahrzeiten
- Ein-/Ausstieg
- Warteschlangen

Die Aufzugslogik sollte nicht direkt in Agenten implementiert werden.

### 5. Rendering

Rendering liest den Simulationszustand und stellt ihn dar.

Wichtig:

- Simulation darf ohne sichtbare Nodes weiterlaufen können.
- Nicht jede Person muss permanent einen eigenen komplexen Node besitzen.
- Sichtbare Agenten können aus einem Pool erzeugt werden.

### 6. UI

UI verändert den Simulationszustand nur über definierte Aktionen, zum Beispiel:

```text
build_room(type, position)
build_floor(level)
build_elevator(column, min_floor, max_floor)
demolish(object_id)
```

So bleiben UI und Simulation entkoppelt.

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

Das erleichtert:

- Balancing
- Mods
- Tests
- spätere Erweiterungen

## Raster

Für den ersten Prototypen empfiehlt sich ein diskretes 2D-Raster:

- X = horizontale Gebäudeposition
- Y = Stockwerk

Jede Einrichtung belegt eine oder mehrere Rasterzellen.

## Tick-System

Nicht jedes System muss jedes gerenderte Frame aktualisiert werden.

Geplant:

- Rendering: pro Frame
- Agentenbewegung: häufig
- Aufzugsteuerung: regelmäßig
- Wirtschaft: seltener
- Langzeitstatistik: deutlich seltener

Dadurch bleibt die Simulation auch bei vielen Personen performant.

## Erste technische Zielgröße

Der erste Prototyp soll problemlos mindestens einige hundert simulierte Personen verwalten können.

Später wird optimiert, bevor die Zielgröße auf mehrere tausend Agenten erhöht wird.

## Noch offene Entscheidungen

- genaue Rastergröße
- Pixel-Art vs. höher aufgelöste 2D-Grafik
- Navigation: eigenes Grid-Pathfinding oder Godot-Navigation
- Savegame-Format
- Ressourcenformat: JSON vs. Godot Resources
- Event-/Signals-Architektur
