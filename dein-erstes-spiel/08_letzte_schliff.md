# Teil 8 - Der letzte Schliff

> Dieses Tutorial wurde aus dem Englischen von Denise Nepraunig [@denisenepraunig][twitter_me] übersetzt. Das [originale Tutorial][org_tutorial] stammt von [Alvin Ourrad and Richard Davey][authors] und ist vom 7. Dezember 2013 [@photonstorm][authors]

Den letzten Schliff den wir machen werden ist es eine Punkteanzeige hinzuzufügen. Um das zu tun werden wir das `Phaser.Text` Objekt verweden. Wir werden zwei neue Variablen einführen, eine enthält die aktuelle Punktezahl und die andere das Textobjekt:

```javascript
	var score = 0;
	var scoreText;
```

Den Punktezahl-Text erstellen wir in der `create` Funktion:

```javascript
	scoreText = game.add.text(16, 16, 'score: 0', { fontSize: '32px', fill: '#000' });
```

16 x 16 sind die Koordinaten wo wir den Text anzeigen. `score: 0` ist der Standardtext welchen wir anzeigen und das darauffolgende Objekte enthält Einstellungen zur Größe und Füllfarbe des Texts. Wenn wir die Schriftart nicht angeben verwendet der Browser die Standardschrift, in Windows wäre dies Arial. Als nächstes müssen wir die `collectStar` Funktion anpassen, damit sich die Punkteanzahl erhöht wenn der Spieler einen Stern einsammelt. Der Text für die Punkteanzeige muss auch angepasst werden um diese Änderung darzustellen:

```javascript
function collectStar (player, star) {

    // den Stern vom Bildschirm entfernen
    star.kill();

    //  Punkte und Text aktualisieren
    score += 10;
    scoreText.text = 'Score: ' + score;

}
```

Es werden also 10 Punkte hinzugefügt für jeden Stern den wir anzeigen und `scoreText`wird aktualisiert um die neue Punkteanzahl anzuzeigen. Wenn du `part9.html` ausführst kannst du das finale Spiel spielen.

![Spieler sammelt Sterne][img_game]

## Zusammenfassung

Du hast gelernt wie man Sprites mit physikalische Eigenschaften erzeugt, wie man seine Bewegung kontrolliert und wie man sie mit anderen Objekten in unserer kleinen Spielewelt interagieren lässt. Es gibt viele weitere Dinge die du tun kannst um das zu Spiel zu erweitern - zum Beispiel hat das Spiel kein Ende oder Gefahren. Warum nicht ein paar Zacken (spikes) hinzufügen welche du vermeiden musst? Du könntest eine neue `spikes` Gruppe erzeugen und auf Kollision mit dem Spieler überprüfen, und anstatt den Zacken zu töten, könntest du stattdessen den Spieler töten. Oder für ein nicht-gewaltätiges Spiel könntest du ein Spiel gegen die Zeit erstellen wo du die Sterne so schnell wie möglich einsammeln musst. Wir haben ein paar extra Grafiken in der Zip-Datei inkludiert welche dir helfen sollen Inspiration zu finden.

Mit der Hilfe von dem was du jetzt gelernt hast in diesem Tutorial und den 450+ Beispielen die du zur Verfügung hast, solltest du nun eine solide Grundlage habe für ein zukünftiges Projekt. Solltest du Fragen haben, brauchst Hilfe oder du willst teilen was du erstellt hast - dann wende dich einfach and das Phaser Forum.


[twitter_me]: https://twitter.com/denisenepraunig
[org_tutorial]: http://phaser.io/tutorials/making-your-first-phaser-game
[authors]: https://twitter.com/photonstorm 

[img_game]: http://phaser.io/content/tutorials/making-your-first-phaser-game/part9.png