Hier ist eine vollständige README.md inklusive eines erweiterten Beispiels, das alle Funktionen von ShadowCode abdeckt, sowie ein eigenständiges Beispiel-Skript, das du für die Demonstration verwenden kannst.

README.md

# Byte 1.0

**Byte 1.0** ist eine minimalistische 2D-Spiele-Engine, die mit den eigens entwickelten Skriptsprachen **ShadowCode** und **ShadowScript** arbeitet. Diese Engine bietet Entwicklern eine intuitive Möglichkeit, Spiele mit einer einfachen Syntax und umfangreicher Steuerung zu erstellen.

---

## Features

### **ShadowCode und ShadowScript**
- **ShadowCode (`.sdc`):** Führt Code **zeilenweise** aus, ideal für interaktive und sequentielle Prozesse.
- **ShadowScript (`.sdsc`):** Führt Code **auf einmal** aus, geeignet für Events und Module.

Beide Sprachen teilen sich dieselbe Syntax und ermöglichen das einfache Laden von Plugins und externen Skripten.

---

### **Syntax und Funktionen**

1. **Initialisierung:**
   - Jedes Skript startet mit:
     ```shadowcode
     init #ShadowCode
     ```
   - Plugins und Module können geladen werden mit:
     ```shadowcode
     init #url("https://example.com/api.sdc")  $ Laden aus einer URL
     init #file("plugin.sdc")                 $ Laden aus einer lokalen Datei
     ```

2. **Kommentare:**
   - Kommentare werden mit `$` gekennzeichnet:
     ```shadowcode
     $ Dies ist ein Kommentar
     ```

3. **Variablen:**
   - Erstellen und Zuweisen von Variablen:
     ```shadowcode
     var(@score)
     @score = 10
     ```

4. **Funktionen:**
   - Funktionen können definiert und aufgerufen werden:
     ```shadowcode
     func.sayHello() $ Funktion definieren
       show("Hallo, Welt!")
     func.end

     sayHello() $ Funktion aufrufen
     ```

5. **Sprites:**
   - Kontrolle von Sprites:
     ```shadowcode
     Sprite.player.goto(100, 100)   $ Sprite bewegen
     Sprite.player.scale(2, 2)      $ Sprite skalieren
     Sprite.player.show             $ Sprite anzeigen
     Sprite.player.hide             $ Sprite verstecken
     ```

6. **Ereignisse und Eingaben:**
   - Überprüfung auf Berührung:
     ```shadowcode
     if (Sprite.player.touched?() = true [
         show("Sprite berührt!")
     ])
     ```
   - Tastatursteuerung:
     ```shadowcode
     if (button.keyboard.space.pressed?() = true [
         show("Leertaste gedrückt!")
     ])
     ```

7. **Ausgaben in die Konsole:**
   - Verschiedene Nachrichtentypen:
     ```shadowcode
     show("Normale Nachricht")
     debug("Debug-Nachricht")
     error("Fehlermeldung")
     ```

---

## Installation

1. Klone das Repository:
   ```bash
   git clone https://github.com/dein-benutzername/ByteEngine.git
   cd ByteEngine```

	**2.	Installiere Abhängigkeiten:**
	•	Linux (Ubuntu):

```bash
sudo apt-get install libsdl2-dev libsdl2-image-dev```


	•	Windows:
	•	Lade SDL2 von libsdl.org herunter und integriere die Bibliotheken.
	•	MacOS:

```bash
brew install sdl2 sdl2_image
```

	3.	Baue das Projekt:

```bash
mkdir build && cd build
cmake ..
make
```

	4.	Starte das Beispiel:

```Bash
./ByteEngineDemo
```
##Beispiel

Hier ist ein vollständiges Beispiel, das alle Funktionen von ShadowCode demonstriert:

```shadowcode
init #ShadowCode

$ Initialisierung von Variablen
var(@x) 
var(@y)
@x = 50
@y = 50

$ Sprite erstellen und positionieren
Sprite.player.goto(@x, @y)
Sprite.player.show

$ Funktion definieren
func.moveSprite(x, y)
    Sprite.player.goto(x, y)
func.end

$ Spiel-Loop
while (true [
    $ Eingabe: Bewegen des Sprites
    if (button.keyboard.up.pressed?() = true [
        @y = @y - 10
        moveSprite(@x, @y)
    ])

    if (button.keyboard.down.pressed?() = true [
        @y = @y + 10
        moveSprite(@x, @y)
    ])

    if (button.keyboard.left.pressed?() = true [
        @x = @x - 10
        moveSprite(@x, @y)
    ])

    if (button.keyboard.right.pressed?() = true [
        @x = @x + 10
        moveSprite(@x, @y)
    ])

    $ Debug: Position anzeigen
    debug("Position: X=" + @x + ", Y=" + @y)
])
```
Speichere dieses Beispiel in einer Datei namens example.sdc und führe es mit der Byte-Engine aus.

##Geplante Features
	•	Erweiterung der Physik-Engine (Kollisionen, Gravitation).
	•	Unterstützung für erweiterte Animationen.
	•	Einführung von 3D-Rendering in zukünftigen Versionen.

##Mitmachen

Möchtest du mitentwickeln? Folge diesen Schritten:
	1.	Forke das Repository.
	2.	Erstelle einen neuen Branch.
	3.	Reiche einen Pull-Request ein.

##Lizenz

Byte 1.0 ist Open-Source, jedoch mit Einschränkungen für kommerzielle Nutzung. Siehe LICENSE für Details.

---

### **Beispieldatei: example.sdc**

Speichere das folgende Skript als `example.sdc`. Es enthält alle Funktionen, die **ShadowCode** unterstützt:

```shadowcode
init #ShadowCode

$ Variablen initialisieren
var(@score)
@score = 0

$ Sprite erstellen
Sprite.player.goto(100, 100)
Sprite.player.show

$ Funktion: Sprite bewegen
func.moveSprite(dx, dy)
    Sprite.player.goto(dx, dy)
    debug("Sprite bewegt zu X=" + dx + ", Y=" + dy)
func.end

$ Funktion: Score erhöhen
func.increaseScore()
    @score = @score + 1
    show("Score: " + @score)
func.end

$ Spiel-Loop
while (true [
    if (button.keyboard.up.pressed?() = true [
        moveSprite(100, 50)
    ])

    if (Sprite.player.touched?() = true [
        increaseScore()
    ])
])

Zusammenfassung
	•	README.md: Beschreibt die Engine und Syntax.
	•	example.sdc: Eine funktionierende Demonstration aller ShadowCode-Features.
	•	Enthält Tastatureingaben, Sprites, Funktionen, Schleifen, und Debugging.

Diese Dateien kannst du direkt in dein Projekt einfügen!
