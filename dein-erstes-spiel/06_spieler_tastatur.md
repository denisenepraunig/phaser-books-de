# Teil 6 - Den Spieler mit der Tastatur steuern

> Dieses Tutorial wurde aus dem Englischen von Denise Nepraunig [@denisenepraunig][twitter_me] übersetzt. Das [originale Tutorial][org_tutorial] stammt von [Alvin Ourrad and Richard Davey][authors] und ist vom 7. Dezember 2013 [@photonstorm][authors]

Kollisionen sind ja schön und gut, aber wir benötigen eine Möglichkeit den Spieler zu bewegen. Vielleicht denkst du jetzt daran direkt in die Dokumentation zu springen und nach so etwas wie dem Hinzufügen von Event Listener zu suchen, aber das ist gar nicht notwendig. Phaser hat einen eingebauten Tastatur-Manger und einer seiner Vorteile ist die Verwendung dieser kleinen, praktischen Funktion:

```javascript
cursors = game.input.keyboard.createCursorKeys();
```

Dies erweitert das `cursor` Objekt mit vier Eigenschaften: up, down, left und right und alle sind Instanzen vom `Phaser.Key-Objekt`. Alles was wir dann tun müssen ist es diese vier Werte in unserer `update` Schleife abzufragen:

```javascript
	//  Die Beschleunigung des Spielers zurücksetzen
    player.body.velocity.x = 0;

    if (cursors.left.isDown)
    {
        //  nach links bewegen
        player.body.velocity.x = -150;

        player.animations.play('left');
    }
    else if (cursors.right.isDown)
    {
        //  nach rechts bewegen
        player.body.velocity.x = 150;

        player.animations.play('right');
    }
    else
    {
        //  still stehen
        player.animations.stop();

        player.frame = 4;
    }

    //  Dem Spieler erlauben zu springen wenn er den Boden berührt
    if (cursors.up.isDown && player.body.touching.down)
    {
        player.body.velocity.y = -350;
    }
```

Obwohl wir hier ziemlich viel Code hinzugefühgt haben, sollte dieser ziemlich verständlich sein. Das Erste was wir tun ist die horizontale Beschelunigung des Spieler-Sprites zurückzusetzen. Danach prüfen wir ob die linke Pfeiltaste gedrückt ist. Wenn dem so ist, dann wenden wir eine negative, horizontale Beschleunigung an und starten die `left` Animation (Laufen). Wenn die rechte Pfeiltaste gedrückt wurde, dann machen wir geanu das Gegenteil. Durch das Zurücksetzen der Beschleunigung in jedem Frame auf diese Art und Weise, erzeugen wir eine `Start-Stop`-ähnliche Bewegung.

Das Sprite des Spielers bewegt sich nur wenn eine Pfeiltaste gedrückt wird und hört sofort wieder auf wenn diese losgelassen wird. Phaser erlaubt es uns auch wesentlich komplexere Bewegungen mit Beschleunigung und Impulsen, aber für unser Spiel reicht uns der aktuelle Effekt. Der finale Teil der Tastenüberprüfungen setzt den Frame auf Nummer 4 wenn keine Taste gedrückt wurde. Dieser Frame ist der sogenannte Ruhemodus (idle) in welchem der Spieler dich ansieht.

## Springen

Der letzte Teil des Codes ermöglicht uns das Springen. Wir überprüfen ob die Nach-Oben-Pfeiltaste gedrückt wurde, denn sie ist die Taste welche wir für das Springen verwenden. Zusätzlich testen wir noch ob der Spieler gerade den Boden berührt, ansonsten könnte er auch springen wenn er sich gerade mitten in der Luft befindet. Wenn beide Bedingungen zutreffen wenden wir eine negative, vertikale Beschleunigung von 350 Pixel/Sekunde an. Der Spieler wird auch automatisch fallen, da wir ihm zuvor auch eine Gravitation zugewiesen haben. Jetzt wo wir die Steuerung aufgesetzt haben, kann man die Spielewelt nun auch erkunden. Starte `part7.html` und probiere es aus. Du kannst mit dem Wert 350 herumspielen um höher oder niedriger zu springen um zu sehen welchen Effekt das hat.

![Spieler springt][img_game]

[twitter_me]: https://twitter.com/denisenepraunig
[org_tutorial]: http://phaser.io/tutorials/making-your-first-phaser-game
[authors]: https://twitter.com/photonstorm 

[img_game]: http://phaser.io/content/tutorials/making-your-first-phaser-game/part7.png