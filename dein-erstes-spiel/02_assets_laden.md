# Teil 2 - Assets laden

> Dieses Tutorial wurde aus dem Englischen von Denise Nepraunig [@denisenepraunig][twitter_me] übersetzt. Das [originale Tutorial][org_tutorial] stammt von [Alvin Ourrad and Richard Davey][authors] und ist vom 7. Dezember 2013 [@photonstorm][authors]

Lass uns die Spiele Assets (Bilder, Spritesheets, Sounds) laden welche wir für unser Spiel brauchen. Das machst du indem du `game.load` innerhalb der Funktion `preload` aufrufst. Phaser sieht automatisch nach dieser Funktion wenn es startet und fängt and alles zu laden was darin definiert ist.

Aktuell ist die `preload` Funktion leer. Ändere es zu:

```javascript
function preload() {

    game.load.image('sky', 'assets/sky.png');
    game.load.image('ground', 'assets/platform.png');
    game.load.image('star', 'assets/star.png');
    game.load.spritesheet('dude', 'assets/dude.png', 32, 48);

}
```

Dies wird 4 Assets laden: 3 Bilder und ein Spritesheet. Es mag vielleicht für manche offensichtlich sein, aber ich möchte den ersten Parameter hier hervorheben, auch genannt `asset key`. Dieser String ist ein Link zum geladenen Asset und ist das was du in deinem Code verwenden wirst wenn du Sprites erstellst. Du kannst jeden validen JavaScript String als Key verwenden.

## Ein Sprite erstellen
Um unseren Spiel ein Sprite hinzuzufügen platziere folgenden Code in ther `create` Funktion:

```javascript
game.add.sprite(0, 0, 'star');
```

Wenn du die Seite erneut im Browser lädst solltest du einen schwarzen Schirm mit einem einzigen Stern-Sprite in der linken, oberen Ecke sehen:

![Stern-Sprite][img_game]

Die Reihenfolge in der die einzelnen Objekte gerendert werden entsprechen der Reihenfolge in der du sie erstellst. Wenn du also einen Hintergrund hinter das Stern-Sprite haben willst musst du sicher stellen dass du es als Sprite vor dem Stern hinzufügst.


[twitter_me]: https://twitter.com/denisenepraunig
[org_tutorial]: http://phaser.io/tutorials/making-your-first-phaser-game
[authors]: https://twitter.com/photonstorm 

[img_game]: http://phaser.io/content/tutorials/making-your-first-phaser-game/part3.png