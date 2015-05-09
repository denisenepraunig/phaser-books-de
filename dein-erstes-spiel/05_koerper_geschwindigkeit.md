# Teil 5 - Der Körper und Geschwindigkeit: eine Physikwelt

> Dieses Tutorial wurde aus dem Englischen von Denise Nepraunig [@denisenepraunig][twitter_me] übersetzt. Das [originale Tutorial][org_tutorial] stammt von [Alvin Ourrad and Richard Davey][authors] und ist vom 7. Dezember 2013 [@photonstorm][authors]

Phaser bietet Unterstützung für eine Vielzahl von verschiedenen Physiksystemen. Es wird mit Arcade-Physik, Ninja-Physik und P2.JS Full-Body-Physik ausgeliefert. In diesem Tutorial verwenden wir das Arkade-Physik-System, welches einfach und leichtgewichtig ist - also optimal für mobile Browser. Du wirst merken, dass wir das Physiksystem manuell aktivieren müssen und dass wir es für jede Gruppe oder Sprite - wo wir physikalische Eigenschaften haben wollen - aktivieren müssen.

Sobald dies erledigt ist erhält das Sprite eine neue Körper-Eigenschaft (body), welche eine Instanz von `ArcadePhysics.Body` ist. Dies repräsentiert das Sprite als einen physikalischen Körper in Phaser's Arkade-Physik-System. Das Körperobjekt hat eine Menge an Eigenschaften mit welchen du herumspielen kannst. Um den Effekt von Anziehung auf ein Sprite zu simulieren braucht man nur die folgende Zeilen zu verwenden:

```javascript
player.body.gravity.y = 300;
```

Dies ist ein beliebiger Wert, aber logischerweise, je höher der Wert, desto schwerer fühlt sich dein Objekt an und desto schneller fällt es. Wenn du dies deinem Code hinzufügst oder `part5.html` ausführst siehst du, dass der Spieler unaufhaltsam hinunterfällt und total den Boden ignoriert den wir vorher erzeugt haben:

![Vor dem Kollisionscheck][img_keine_bodenkollision]

Der Grund dafür ist, dass wir aktuell noch nicht die Kollisionen zwischen dem Boden und dem Spieler überprüfen. Wir haben Phaser aber bereits angewiesen, dass sich unser Boden und die Plattformen nicht bewegen sollen (immovable). Hätten wir das nicht getan, würde wenn der Spieler mit ihnen kollidiert hätte alles zusammenfallen. Das liegt daran - wenn nicht anders eingestellt - dass der Boden ein bewegtes, physikalisches Objekt ist (auch genannt dynmischer Körper) und wenn der Spieler es berührt wird die resultierende Kraft der Kollision auf den Boden angewandt. Die beiden Körper tauschen ihre Beschleunigungen aus und der Boden fängt deshalb an zu fallen.

Um dem Spieler die Kollision zu ermöglichen und die physikalischen Eigenschaften zun unserem Vorteil zu nutzen, müssen wir einen Kollisionscheck in unsere `update` Funktion einbauen:

```javascript
function update() {

    //  Mit dem Spieler und den Platformen kollidieren
    game.physics.arcade.collide(player, platforms);

}
```

Die `update` Funktion wird von dem Haupt-Spiele-Schleife (core game loop) jeden Frame aufgerufen. Die `Physics.collide` Funktion ist diejenige Funktion welche den ganzen Zauber ermöglicht. Sie nimmt zwei Objekte und überprüft diese auf Kollision und führt auch Separierungen aus. In unserem Fall geben wir ihr das Spieler-Sprite und die Platformgruppe zur Überprüfung. Sie ist schlau genug um die Kollisionprüfung für alle Gruppenmitglieder auszuführen, sodass wir mit dem Boden und den beiden Platformen kollidieren können. Das Ergebnis ist eine solide Platform:

![Nach dem Kollisionscheck][img_bodenkollision]

[twitter_me]: https://twitter.com/denisenepraunig
[org_tutorial]: http://phaser.io/tutorials/making-your-first-phaser-game
[authors]: https://twitter.com/photonstorm 

[img_keine_bodenkollision]: http://phaser.io/content/tutorials/making-your-first-phaser-game/part5.png
[img_bodenkollision]: http://phaser.io/content/tutorials/making-your-first-phaser-game/part6.png