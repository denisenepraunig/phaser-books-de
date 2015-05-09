# Teil 7 - Sternenlicht

> Dieses Tutorial wurde aus dem Englischen von Denise Nepraunig [@denisenepraunig][twitter_me] übersetzt. Das [originale Tutorial][org_tutorial] stammt von [Alvin Ourrad and Richard Davey][authors] und ist vom 7. Dezember 2013 [@photonstorm][authors]

Es wird Zeit unserem kleinen Spiel auch einen Zweck zu geben. Lass uns ein paar Sterne in die Szene streuen und erlauben wir dem Spieler diese einzusammeln. Um dies Umzusetzen werden wir eine neue Gruppe namens `stars` erzeugen und dieser Gruppe die Sterne hinzufügen. Ergänzen wir unsere `create` Funktion um folgenden Code (das siehst du auch in `part8.html`):

```javascript
	stars = game.add.group();

    stars.enableBody = true;

    //  Hier erzeugen wir 12 Sterne mit gleichmäßigem Abstand zwischen ihnen
    for (var i = 0; i < 12; i++)
    {
        //  Einen Stern innheralb der Sternengruppe erzeugen
        var star = stars.create(i * 70, 0, 'star');

        //  Lass die Gravitation ihre Arbeit erledigen
        star.body.gravity.y = 6;

        //  Das gibt jedem Stern eine leicht unterschiedliche Federkraft
        star.body.bounce.y = 0.7 + Math.random() * 0.2;
    }
```

Der Prozess hier ist ganz ähnlich dem vorherigen mit dem wir die Platfrom-Gruppe erzeugt haben. Mit dem JavaScript `for loop` weisen wir an, dass wir gerne 12 Steren in unserem Spiel hätten. Diese haben eine x-Koordinate von `i * 70`, was bedeutet dass sie gleichmäßig in der Spieleszene verteilt sind mit jeweils 70 Pixel Abstand. Genauso wie dem Spieler geben wir ihnen eine Graviation, sodass sie nach unten fallen und etwas von den Platformen abprallen, wenn sie auf diese treffen (Federkraft, bounce). 

Federkraft ist ein Wert zwischen 0 (keine Federung) und 1 (voll gefedert). Unsere Sterene werden mit einem Wert zwischen 0.7 und 0.9 abprallen. Wenn man den Code jetzt so ausführen würde, dann würden die Sterne durch die Platfromen und den Boden durchfallen. Um dies zu verhindern brauchen auch sie eine Kollisionsprüfung gegen die Platformen in unserer `update` Funktion:

```javascript
game.physics.arcade.collide(stars, platforms);
```

Zustätzlich müssen wir noch prüfen ob der Spieler einen Stern überlappt:

```javascript
game.physics.arcade.overlap(player, stars, collectStar, null, this);
```

Diese Codezeile sagt Phaser, dass es die Überlappung zwischen dem Spieler und einem Stern der Sternengruppe überprüfen soll, damit wir einen Stern auch einsammeln können. Wenn sich die beiden überlappen, dann sollte die `collectStar` Funktion ausgeführt werden:

```javascript
function collectStar (player, star) {

    // den Stern vom Bildschirm entfernen
    star.kill();

}
```

Ziemlich einfach oder? Der Stern wird getötet und somit vom Bildschirm entfernt. Wenn wir das Spiel jetzt ausführen haben wir einen Spieler der herumspringen, herumlaufen, abprallen und Sterne einsammeln kann. Nicht schlecht für ein paar Zeilen - hoffentlich ziemlich leserlichem - Code ;-)

![Spieler springt mit Sterne][img_game]

[twitter_me]: https://twitter.com/denisenepraunig
[org_tutorial]: http://phaser.io/tutorials/making-your-first-phaser-game
[authors]: https://twitter.com/photonstorm 

[img_game]: http://phaser.io/content/tutorials/making-your-first-phaser-game/part8.png