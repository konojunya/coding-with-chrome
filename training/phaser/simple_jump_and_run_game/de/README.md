Einfaches Jump ’n’ Run Spiel
============================
Author: Markus Bordihn

## Inhaltsverzeichnis
* [Einleitung](#einleitung)
* [Anforderungen](#anforderungen)
* [1. Ein Spiel erstellen](#ein-spiel-erstellen)
* [2. Laden benötigter Bilder und Sounds](#laden-benötigter-bilder-und-sounds)

<img src="../../../../static_files/images/cwc_logo.png" align="right" alt="Coding with Chrome">

* [3. Erstellen der Welt](#erstellen-der-welt)
  * [Hintergrundbild einfügen](#hintergrundbild-einfügen)
  * [Text einfügen](#text-einfügen)
  * [Boden hinzufügen](#boden-hinzufügen)
* [4. Erstellen der Spielfigur](#erstellen-der-spielfigur)
* [5. Physikalische Eigenschaften definieren](#physikalische-eigenschaften-definieren)
  * [Schwerkraft / Anziehungskraft](#schwerkraft--anziehungskraft)
  * [Kollision](#kollision)
* [6. Steuerung hinzufügen](#steuerung-hinzufügen)
  * [Eingabe überwachen](#eingabe-überwachen)
  * [Aktion bei Eingabe festlegen](#aktion-bei-eingabe-festlegen)
* [7. Hindernisse hinzufügen](#hindernisse-hinzufügen)
* [8. Highscore hinzufügen](#highscore-hinzufügen)
* [9. Spielende durch Kollision mit den Hindernissen](#spielende-durch-kollision-mit-den-hindernissen)
* [10. Soundeffekte hinzufügen](#soundeffekte-hinzufügen)
* [11. Game verschönern](#game-verschönern)

## Einleitung
Dieser Workshop richtet sich an Anfänger die immer schon mal ein eigenes Spiel entwickeln wollten.
Ihr lernt die Grundlage der Spieleentwicklung und wie eine Spiele Engine grundlegend funktioniert.

Zum programmieren wird eine Block-basierte Programmierung mit vordefinierten Blöcke verwendet. 
Diese Blöcke setzt Ihr einfach für euer Spiel zusammen.

Hierzu wird _Coding with Chrome_ verwendet, welches kostenfrei erhältlich ist.

## Anforderungen
Für diesen Workshop solltet Ihr euch bereits mit dem Spiele Editor in Coding with Chrome beschäftigt haben und eine Übersicht der verschiedenen “Blöcke” haben.

Es werde einige Spiele spezifische Begriffe verwenden, die ausführlich in [Grundlagen Games](../../basic/de/README.md) erklärt werden. 

## Ein Spiel erstellen
Wählt im Anfänger Modus **Ein Spiel erstellen** aus und erstellst ein **Neues Projekt**.

Dies sollte dann in etwa wie folgt aussehen:
![][empty_game]

Anschließend legt du den Namen des Spiels und die Dimension (die Größer der Spielfläche) fest.
Für dieses Tutorial verwenden wir eine Dimension von 400x600.

![][game_name_dimension]

## Laden benötigter Bilder und Sounds
Danach müssen wir uns um das Aussehen (Hintergrund, Spielfigur, Boden, Hindernisse, …) des Spiel Gedanken machen.
Fügt hierzu alle Bilder die Ihr verwenden wollt in eure **Datei Bibliothek** hinzu.

Diese erreicht Ihr über die Sidebar:

![][sidebar_file_library]

Alternative könnt Ihr auch **Öffne Datei Bibliothek** unter **Dateien** verwenden:

![][files_file_library]

Sobald Ihr alle benötigten Bilder und Sound Dateien hochgeladen habt, könnt Ihr das **Datei Bibliothek** Fenster schließen.
Ihr könnt natürlich später jederzeit weitere Dateien hinzufügen oder ändern.

Unter den Punkt **Dateien** findet Ihr eure hochgeladenen Dateien, zusätzlich befinden sich unter **Beispiel Dateien** ein paar allgemeine Beispielbilder.

![][example_files]

Zieht eure Bilder anschließend von dem **Dateien** Bereich in euren **beim Vorausladen …** Block und passt den Namen der Bilder an.

![][preload_image]

![][preload_image_name]

Verwendet hierfür die folgenden vordefinierten Namen damit ihr nachher weniger ändern müsst.
Solltet Ihr andere Namen verwenden, achtet bitte darauf diese in den entsprechenden Blöcken anzupassen.

Vordefinierte Name | wird verwendet als
------------ | -------------
bg_01 | Hintergrundbild
floor | Boden
player | Spielfigur
obstacles | Hindernisse

![][preload_image_example]

## Erstellen der Welt
Nun müssen die Grafiken noch in die Spielwelt hinzugefügt werden, damit diese sichtbar im Spiel sind.
Alle dafür benötigten Blöcke findet Ihr in dem Bereich **Erstellen** und werden in den **beim Erstellen …** Block gezogen.

### Hintergrundbild einfügen
Zuerst fügen wir ein sich bewegendes Hintergrundbild hinzu.
Klickt hierfür auf **Tile Sprite** und zieht den Block **füge Hintergrundbild hinzu …** in den **beim Erstellen …** Block.

![][create_tile_sprite]

### Text einfügen
Um einen Text hinzuzufügen klickt auf **Text Objekt** und benützt den **hinzufügen von Text …** Block den Ihr in den beim **Erstellen …** Block zieht.

![][create_text_object]

### Boden hinzufügen
Für den Boden verwenden wir den Block **definiere … als Boden …** und fügen diesen in den **beim Erstellen …** Block hinzu.

![][create_floor]

Bei den Boden könnt Ihr auch die Geschwindigkeit anpassen oder einfach beide Werte auf 0 setzen damit dieser sich nicht mehr bewegt.

Am Ende solltet Ihr ca. folgendes haben:
![][create_world]


## Erstellen der Spielfigur
Seid Ihr mit eurer Welt zufrieden, fügen wir für Spielfigure als Arcade Sprite hinzu, damit wir diese später auch bewegen können.

![][create_player]

Sollte die Spielfigur zu klein/groß sein, so können wir die Größe mit folgenden Block anpassen:

![][create_player_scale]

## Physikalische Eigenschaften definieren
Um das Spiel interessanter zu machen fügen wir der Spielfigure physikalische Eigenschaften hinzu.

### Schwerkraft / Anziehungskraft
Damit unsere Figure nicht einfach in der Luft schwebt, fügen wir eine Anziehungskraft nach unten gereichte (y-Achse) von ca. 200 hinzu.
Zieht hierfür einfach den Block **setze Physik Sprite…** unter den **beim Erstellen …** Block.

![][create_player_physics]

Wählt anschließend “Anziehungskraft y” aus der Auswahlliste des Blocks aus und verwendet einen Wert von ca. 200.

![][create_player_physics_block]

### Kollision
Derzeit fällt unsere Figure einfach durch den Boden.
Um diese zu verhindern müssen wir eine Kollision zwischen der Spielfigure und unseren Boden definieren.

Klickt hierfür auf **Aktualisieren** und geht dann wieder in den **Physik Sprite** Bereich.
Hier zieht Ihr den Block **… kollidiert mit …** in dem **beim Aktualisieren …** Block.

![][create_player_physics_collide]

## Steuerung hinzufügen
Um unsere Spielfigure steuern zu können müssen wir zuerst festlegen wie wir diese steuern möchten.
Um dies so einfach wie Möglich zu machen verwenden wir hierfür die Leertaste.

### Eingabe überwachen
Klickt auf **Erstellen** und wählt **Eingaben** aus.
Hier zieht ihr den **definiere … erfasse als Tastatur Leertaste** in euren beim **Erstellen Block**.

![][create_input]

### Aktion bei Eingabe festlegen
Damit auch etwas mit unsere Spielfigur passiert sobald die Leertaste gedrückt wird, müssen wir noch die entsprechende Aktion festlegen.

Klickt hierzu auf **Eingabe** und zieht den Block **falls spacebar beim betätigen mache** Block in euren **bei Eingabe …** Block.

![][input_spacebar]

Geht anschließend auf die **Physik Sprite** Blöcke und zieht den Block **setzte Physik Sprite … nach …** in den **mache …** Bereich des vorherigen Blocks.

![][input_spacebar_do]

Wählt anschließend aus der Auswahlbox **Geschwindigkeit y** aus und setzt einen Wert von **-150**.

![][input_spacebar_do_example]

Nun sollte eure Figure beim drücken der Leertaste springen.

## Hindernisse hinzufügen
Für die Hindernisse verwenden wir einen vordefinierten Hindernisse Generator Block.
Da wir aber in bestimmten Abständen Hindernisse erzeugen wollen, verwenden wir den **Wiederhole alle … millisekunden** Block. 
Diesen finden wir unter **Erstellen** und ziehen diesen in den **beim Erstellen …** Block.

![][create_loop]

Danach fügen wir den Generator hinzu, diesen finden wir unter **Erstellen → Generatoren**.
Diesen Block ziehen wir direkt im **Wiederhole alle … millisekunden** Block.

![][create_generator]

Nun solltet Ihr die ersten Hindernisse in eurem Spiel sehen.

## Highscore hinzufügen
Für die Highscore verwenden wir den sogenannten **dynamischen Text**, damit wir den Inhalt einfach ändern können.
Dieser befindet sich unter **Erstellen → Text Objekt**.
Fügt den Block **definiere highscore als dynamischen Text …** in den **beim Erstellen …** Bereich hinzu und passt die Position, Farbe, Größe und Aussehen an.

![][dynamic_text]

Damit die Highscore automatisch erhöht wird, ziehen wir den **ändere highscore Text zu erhalte Text ...** Block in die bereits vorhandene Wiederholungsschleife.

![][dynamic_text_loop]

![][dynamic_text_loop_block]

## Spielende durch Kollision mit den Hindernissen
Die einfachste Möglichkeit um das Ende des Spiel festzulegen, ist eine Kollisionsüberprüfung ob der Spieler die Hindernissen berührt hat.

Wir fügen also in dem **beim Aktualisieren …** Bereich eine Kollisionsüberprüfung zwischen dem Spieler und den Hindernissen hinzu.

![][update_collision_block]

Anschließend sagen wir dem Programm was es bei einer Kollision machen soll.
Hierzu verwenden wir den **Spiel neustarten** Block aus dem **Spiel** Bereich.

![][game_restart]

Diesen Block ziehen wir in die Kollisionsüberprüfung zwischen unsere Spielfigur und den Hindernissen.

![][update_collision_example]

## Soundeffekte hinzufügen
Zusätzlich könnt ihr Soundeffekte hinzufügen die beim drücken einer Taste oder bei einer Kollision abgespielt werden.

Zuerst müsst Ihr die entsprechenden Sounds hochladen und unter **Vorausladen** hinzufügen und den Namen anpassen.

![][preload_sound]

Anschließend wird der Sound unter **Erstellen** als **definiere … als Audio …** hinzugefügt.

![][preload_sound_example]

Nun könnt Ihr mit dem Block **spiele Audio …** an jeder beliebigen Stelle den enstprechenden Sound abspielen.

![][input_play_audio]

## Game verschönern
Zum Schluss verschönern wir das Spiel noch, indem wir zusätzliche Grafiken hinzufügen oder aber einen Start bzw. End Bildschirm.

## Komplettes Spiel
![][full_game]


[empty_game]: images/empty_game.png
[game_name_dimension]: images/game_name_dimension.png

[sidebar_file_library]: images/sidebar_file_library.png
[files_file_library]: images/files_file_library.png
[example_files]: images/example_files.png
[preload_image]: images/preload_image.png
[preload_image_name]: images/preload_image_name.png
[preload_image_example]: images/preload_image_example.png

[create_world]: images/create_world.png
[create_tile_sprite]: images/create_tile_sprite.png
[create_text_object]: images/create_text_object.png
[create_floor]: images/create_floor.png
[create_player]: images/create_player.png
[create_player_scale]: images/create_player_scale.png

[create_player_physics]: images/create_player_physics.png
[create_player_physics_block]: images/create_player_physics_block.png
[create_player_physics_collide]: images/create_player_physics_collide.png

[create_input]: images/create_input.png
[input_spacebar]: images/input_spacebar.png
[input_spacebar_do]: images/input_spacebar_do.png
[input_spacebar_do_example]: images/input_spacebar_do_example.png

[create_loop]: images/create_loop.png
[create_generator]: images/create_generator.png

[dynamic_text]: images/dynamic_text.png
[dynamic_text_loop]: images/dynamic_text_loop.png
[dynamic_text_loop_block]: images/dynamic_text_loop_block.png

[update_collision_block]: images/update_collision_block.png
[game_restart]: images/game_restart.png
[update_collision_example]: images/update_collision_example.png


[preload_sound]: images/preload_sound.png
[preload_sound_example]: images/preload_sound_example.png
[input_play_audio]: images/input_play_audio.png

[full_game]: images/full_game.png
