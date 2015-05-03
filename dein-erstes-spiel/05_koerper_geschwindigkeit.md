# Teil 5 - Der Körper und Geschwindigkeit: ein Physikwelt

> Dieses Tutorial wurde aus dem Englischen von Denise Nepraunig [@denisenepraunig][twitter_me] übersetzt. Das [originale Tutorial][org_tutorial] stammt von [Alvin Ourrad and Richard Davey][authors] und ist vom 7. Dezember 2013 [@photonstorm][authors]

Phaser bietet Unterstützung für eine Vielzahl von verschiedenen Physiksystemen. Es wird mit Arcadephysik, Ninjaphysik und P2.JS Full-Body-Physik ausgeliefert. In diesem Tutorial verwenden wir das Arkadephysik-System, welches einfach und leichtgewichtig ist, also optimal für mobile Browser. Du wirst merken, dass wir das Physiksystem manuell anstarten müssen, und dass wir es für jede Gruppe oder Sprite - wo wir physikalische Eigenschaften haben wollen - aktivieren müssen.

Sobald dies erledigt ist erhält das Sprite eine neue Körper-Eigenschaft (body), welche eine Instanz von `ArcadePhysics.Body` ist. Dies repräsentiert das Sprite als einen physikalischen Körper in Phaser's Arkade-Physik-System. Das Körperobjekt hat eine Menge an Eigenschaften mit welchen du herumspielen kannst. Um den Effekt von Anziehung auf ein Sprite zu simulieren braucht man nur die folgenden Zeilen verwenden:

```javascript
player.body.gravity.y = 300;
```

Dies ist ein beliebiger Wert, aber logischerweise, je höher der Wert, desto schwerer fühlt sich dein Objekt an und desto schneller fällt es. Wenn du dies deinem Code hinzufügst oder `part5.html` ausführst siehst du, dass der Spiele unaufhaltsam hinunterfällt und total den Boden ignoriert den wir vorher erzeugt haben:

![Vor dem Kollisionscheck][img_game]

Der Grund dafür ist, dass wir aktuell noch nicht die Kollisionen zwischen dem Boden und dem Spiler überprüfen. Wir haben Phaser aber bereits gesagt, dass unser Boden und die Plattformen sich nicht bewegen sollen (immovable). Hätten wir das nicht gesagt, würde wenn der Spieler mit ihnen kollidiert hätte alles für einen Moment stehen bleiben und dann würde alles kollabieren. Das liegt daran, wenn nicht anders eingestellt, dass der Boden ein bewegtes, physikalisches Objekt ist (bekannt als dynmischer Körper) und wenn der Spieler es berührt, die resultierende Kraft der Kollision auf den Boden angewandt wird, die beiden Körper tauschen ihre Beschleunigungen aus und der Boden fängt dann auch an zu fallen.

Um dem Spieler zu erlauben zu kollidieren und die physikalischen Eigenschaften zun unserem Vorteil zu nutzen müssen wir einen Kollisionscheck in unsere `update` Funktion einbauen:

```javascript
function update() {

    //  Mit dem Spieler und den Platformen kollidieren
    game.physics.arcade.collide(player, platforms);

}
```

Die `update` Funktion wird von dem Haupt-Spiele-Schleife (core game loop) jeden Frame aufgerufen. Die `Physics.collide` Funktion ist diejenige die den ganzen Zauber ermöglicht. Sie nimmt zwei Objekte und überprüft diese auf Kollision und führt auch Separierungen aus. In unserem Fall geben wir ihr die Spieler-Sprite und die Platformgruppe. Sie ist schlau genug um die Kollisionprüfung für alle Gruppenmitglieder auszuführen, sodass wir mit dem Boden und den beiden Platformen kollidieren können. Das Ergebnis ist eine solide Platform:

![Nach dem Kollisionscheck][img_game2]

[twitter_me]: https://twitter.com/denisenepraunig
[org_tutorial]: http://phaser.io/tutorials/making-your-first-phaser-game
[authors]: https://twitter.com/photonstorm 

[img_game]: http://phaser.io/content/tutorials/making-your-first-phaser-game/part5.png
[img_game2]: http://phaser.io/content/tutorials/making-your-first-phaser-game/part6.png