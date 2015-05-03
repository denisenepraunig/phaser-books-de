# Teil 2 - Assets laden

> Dieses Tutorial wurde aus dem Englischen von Denise Nepraunig [@denisenepraunig][twitter_me] übersetzt. Das [originale Tutorial][org_tutorial] stammt von [Alvin Ourrad and Richard Davey][authors] und ist vom 7. Dezember 2013 [@photonstorm][authors]

Unter der Haube erzeugt `game.add.sprite` ein neues Phaser.Sprite Objekt und fügt dieses Sprite der `Spielewelt` hinzu. Das ist die Welt wo alle deine Objekte existieren, und kann mit der Stage in ActionScript3 vergleichen werden.

Hinweise: Die Spielewelt had keine fixe Größe und dehnt sich unendlich aus in alle Richtungen und `0, 0` ist ihr Mittelpunkt. Der Einfachheit halber platziert Phaser `0, 0` in der linken, oberen Ecke deines Spieles für dich, aber wenn due die eingebaunte Kamera verwendest, kannst du dich in der Welt bewegen wie du es brauchst.

Auf die Welt-Klasse kann mittels `game.world` zugegriffen werden und sie enthält vielen nützliche Funktionen und Eigenschaften welche dir helfen die Objekte in deiner Welt zu verteilen. Das sind einfache Eigenschaften wie `game.world.height`, aber es gibt auf einige fortgeschrittenere welche wir in einem anderen Tutorial verwenden werden.

Lass uns fürs Erste die Szene mit Hintergrund und Platformen aufbauen. Hier ist die aktualisierte `create` Funktion:

```javascript
var platforms;

function create() {

    //  Wir benötigen ein Physik-System, deshalb lass uns Arcade Physik aktivieren
    game.physics.startSystem(Phaser.Physics.ARCADE);

    //  Ein einfacher Hintergrund für unser Spiel
    game.add.sprite(0, 0, 'sky');

    //  Diese Platform Gruppe enthält den Boden und zwei Platformen auf die wir springen können
    platforms = game.add.group();

    //  Wir werden für jedes Objekt in dieser Gruppe die Physik aktivieren
    platforms.enableBody = true;

    // Hier erzeugen wir den Grund
    var ground = platforms.create(0, game.world.height - 64, 'ground');

    //  Saklieren um der Breite des Spiels zu entsprechen (das originale Sprite hat eine Größe von 400 x 32)
    ground.scale.setTo(2, 2);

    //  Das stoppt es vom Runterfallen wenn du darauf springst
    ground.body.immovable = true;

    //  Lass uns die Platformen erzeugen
    var ledge = platforms.create(400, 400, 'ground');

    ledge.body.immovable = true;

    ledge = platforms.create(-150, 250, 'ground');

    ledge.body.immovable = true;

}
```

Wenn du das ausführst, du findest das in `part4.html` in der Tutorial Zip-Datei, solltest du eine Szene vorfinden welche uns schon mehr an ein Spiel erinnert:

![Platformen][img_game]

Der erste Teil ist der gleiche Teil wie wir im Sternen-Sprite zuvor hatten, nur das wir den Schlüssel zu `sky` geändert haben und nun unseren Himmel Hintergrund stattdessen anzeigen. Das ist eine 800 x 600 PNG-Datei die den ganzen Spieleschirm ausfüllt.

[twitter_me]: https://twitter.com/denisenepraunig
[org_tutorial]: http://phaser.io/tutorials/making-your-first-phaser-game
[authors]: https://twitter.com/photonstorm 

[img_game]: http://phaser.io/content/tutorials/making-your-first-phaser-game/part4.png