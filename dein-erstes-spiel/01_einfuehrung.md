# Teil 1 - Einführung

> Dieses Tutorial wurde aus dem Englischen von Denise Nepraunig [@denisenepraunig][twitter_me] übersetzt. Das [originale Tutorial][org_tutorial] stammt von [Alvin Ourrad and Richard Davey][authors] und ist vom 7. Dezember 2013 [@photonstorm][authors]

![Unser erstes Spiel][img_erstes_spiel]

Willkommen zu unserem ersten Tutorial über Spieleentwicklung mit Phaser. Wir werden lernen wie wir ein kleines Spiel erstellen inklusive einem Spieler der auf Platformen herumrennt, springt und Sterne einfängt. Während wir diesen Prozess durchmachen, werden wir einige Hauptfunktionen des Frameworks kennenlernen.

## Was ist Phaser
Phaser ist ein HTML5 Spiele-Framework welches das Ziel hat dem Entwicklern dabei zu helfen schnell mächtige, browserübergreifende HTML5 Spiele zu erstellen. Im Gegensatz zu anderen Spieleframeworks wurde es einzig und allein darum gebaut um auch auf mobilen Browsern zu funktionieren. Die einzige Anforderung an den Browers ist der Support des Canvas-Tags. Das Framework selbst leiht sich auch einiges von [http://flixel.org/ Flixel] aus.

## Vorraussetzungen
[Lade die Quellcode Dateien][sources] und die Assets herunter die zu diesem Tutorial gehören. Wenn du bereits das Phaser Repository von Github ausgecheckt hast hast du diese Daten bereits. Schau einfach in den `resources/tutorials` Ordner.

Du brauchst ein grundlegendes Wissen über JavaScript.

Stell auch sicher, dass du dir den [Getting Started Guide][getting_started] durchliest, er zeigt dir wie du das Framework runterlädst, eine lokale Entwicklungsumgebung aufsetzt und gibt dir einen flüchtigen Eindruck darüber wie ein Phaser Projekt aussieht. Dadurch bekommst du auch einen Eindruck über die Hauptfunktionen des Frameworks.

Wenn du den Getting Started Guide durchgelesen hast, dann hast du das Phaser Framework heruntergeladen, alles ist eingerichtet und bist du bereit fürs Programmieren. Lade die [Assets für dieses Tutorial](sources) herunter und entpacke sie in das Root-Verzeichnis deines Webservers.

Öffne die `part1.html` Seite in dem Editor deiner Wahl und lass uns einen genaueren Blick auf den Code werfen. Nach ein bisschen Boilerplate HTML, welches auch Phaser inkludiert, sieht die Codestruktur folgendermaßen aus:

```javascript
var game = new Phaser.Game(800, 600, Phaser.AUTO, '', { preload: preload, create: create, update: update });

function preload() {
}

function create() {
}

function update() {
}
```

Zeile 1 ist die Zeile welche Phaser zum Leben erweckt indem es eine Instanz von einem Phaser.Game Objekt erzeugt und sie einer lokalen Variablen `game` zuweist. Sie `game` zu nennen ist eine gängige Praxis - aber kein Muss - du wirst es so auch in den Phaser Beispielen vorfinden.

Die ersten zwei Parameter sind die Breite und die Höhe des Canvas Elements welches Phaser erzeugen wird. In unserem Fall 800 x 600 Pixel. Dein Spiel kann jede Größe haben die du willst, aber das ist die Größe in der wir unser Spiel anzeigen werden. Der dritte Parameter kann entweder Phaser.CANVAS, Phaser.WEBGL oder Phaser.AUTO sein. Dies ist der Rendering Context welchen du benutzen willst. Der empfohlene Wert ist Phaser.AUTO welcher automatisch versucht WebGL zu verwenden, aber wenn der Browser oder das Gerät dies nicht unterstützen, dann wird auf Canvas umgeschalten.

Der vierte Paramter ist ein leerer String, dies ist die ID des DOM Elements in welchem du gerne den Canvas einfügen möchtest den Phaser erzeugt. Da wir ihn leer gelassen haben, wird es einfach an den Body angehängt. Der letzte Parameter ist ein Objekt, welches die Referenzen zu den essenziellen Phaser Funktionen beinhaltet. Ihre Verwendung wird später noch gründlich erklärt werden. Beachte das dieses Objekt nicht zwingend notwendig ist - Phaser unterstützt ein vollkommenes `State System` mit welchen man den Code in sehr viel sauberere einzelne Objekte aufsplitten kann. In diesem einfachen Getting Started Guide werden wir aber den hier gezeigten Ansatz verwenden, da dieser uns sehr viel schnelleres Prototyping erlaubt.

[twitter_me]: https://twitter.com/denisenepraunig
[org_tutorial]: http://phaser.io/tutorials/making-your-first-phaser-game
[authors]: https://twitter.com/photonstorm 
[img_erstes_spiel]: http://phaser.io/content/tutorials/making-your-first-phaser-game/tutorial_header.png
[sources]: https://github.com/photonstorm/phaser/raw/master/resources/tutorials/02%20Making%20your%20first%20game/phaser_tutorial_02.zip
[getting_started]: http://phaser.io/tutorials/getting-started