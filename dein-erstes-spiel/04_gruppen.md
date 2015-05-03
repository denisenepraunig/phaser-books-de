# Teil 4 - Gruppen

> Dieses Tutorial wurde aus dem Englischen von Denise Nepraunig [@denisenepraunig][twitter_me] übersetzt. Das [originale Tutorial][org_tutorial] stammt von [Alvin Ourrad and Richard Davey][authors] und ist vom 7. Dezember 2013 [@photonstorm][authors]

Gruppen sind richtig mächtig. Wie ihr Name impliziert erlauben sie dir ähnliche Objekte zu gruppieren und als einzelne Einheit zu kontrollieren. Du kannst auch auf Kollisionen zwischen Gruppen prüfen, und für dieses Spiel werden wir zwei verschiedene Gruppen verwenden. Eine davon ist die Gruppe der Plattformen, welche wir bereits erzeugt haben.

```javascript
platforms = game.add.group();
```

So wie bei den Sprites erzeugt `game.add` unser Gruppenobjekt. Wir weisen es einer lokalen Variable `platforms` zu. Jetzt können wir ihr Objekte hinzufügen - als erstes den Boden. Der ist am Grund des Spiels platziert und verwendet das `ground` bild welches wir vorher geladen haben. Der Boden ist skaliert um die gesamte Breite des Spiels auszufüllen. Am Schluss setzen wir die ìmmovable` Eigenschaft auf true. Hätten wir das nicht getan, würde sich der Grund bewegen sobald der Spieler mit ihm kollidiert (mehr davon in dem Physikabschnitt).

Mit dem Boden an Ort und Stelle erzeugen wir zwei kleinere Platformen zum Draufspringen mit der exakt gleichen Technik wie für den Boden.

## Bereit machen: Spieler 1
Erzeuge eine neue lokale Variable genannt `player` und füge folgenden Code der `create` funktion hinzu. Du kannst dies in `part5.html` sehen:

```javascript
    // Der Spieler und seine Einstellungen
    player = game.add.sprite(32, game.world.height - 150, 'dude');

    //  Auch der Spieler benötigt Physik
    game.physics.arcade.enable(player);

    //  Physikeigenschaften des Spielers. Wir geben dem kleinen Kerl eine leichte Federkraft
    player.body.bounce.y = 0.2;
    player.body.gravity.y = 300;
    player.body.collideWorldBounds = true;

    //  Unsere beiden Animationen, gehen links und rechts.
    player.animations.add('left', [0, 1, 2, 3], 10, true);
    player.animations.add('right', [5, 6, 7, 8], 10, true);
```

Dies erzeugt ein neues Sprite namens `player`, positioniert an 32 x 150 Pixel vom Grund des Spiels aus. Wir weisen Phaser an das `dude` Asset zu verwenden welches wir vorher schon geladen haben. Wenn du zurückschielst auf die `preload` Funktion wirst du erkennen, dass wir `dude` als Spritesheet geladen haben und nicht als Bild. Das haben wir deshalb gemacht weil es Animationsframes enthält. Das vollständige Spritesheet sieht so aus:

![Player][img_game]

Du siehst das es in Summe 9 Frames hat, 4 für laufen rechts, 1 direkt in die Kamera blickend und 4 für nach links laufen. Hinweis: Phaser unterstützt das Spiegeln von Sprites und so kann man sich einige Animationsframes sparen, aber in diesem Tutorial werden wir es richtig 'Old School' machen.

Wir definieren zwei Animationen genannt `left` und `right`. Die `left` Animation verwendet Frames 0, 1, 2 und 3 und läuft mit 10 Frames pro Sekunde. Der `true` Parameter sagt unserer Animation in einer Schleife ausgeführt zu werden (loop). Das ist unser Standard Lauf-Ablauf und wir wiederholen das ganze auch in der entgegengesetzten Richtung. Vor den Animationen haben wir dem Spieler auch ein paar Physikeigenschaften zugewiesen.

[twitter_me]: https://twitter.com/denisenepraunig
[org_tutorial]: http://phaser.io/tutorials/making-your-first-phaser-game
[authors]: https://twitter.com/photonstorm 

[img_game]: http://phaser.io/content/tutorials/making-your-first-phaser-game/dude.png