# Teil 1 - Einführung

Willkoemmen zu unserem ersten Tutorial über Spieleentwicklung mit Phaser. Hier werden wir lernen wi wir ein kleines Spiel erstelllen inklusive einem Spieler der herumrennt und auf Platformen springt und Sterne einfängt. Während wir diesen Prozess durchmachen werden wir einige Hauptfunktionen des Frameworks kennenlernen.

## Was ist Phaser
Phaser ist ein HTML5 Spiele-Framework welches das Ziel hat den Entwicklern zu helfen um mächtige, cross-browser HTML5 Spiele richtig schnell und, im Gegensatz zu anderen, wurde es einzig und allein darum gebaut um auch mit mobielen Browsern zu funktionieren. Die einzige Anforderung an den Browers ist der Support des Canvas Tags. Es leiht sich auch einiges von Flixel aus.

## Vorraussetzungen
[Lade die Quellcode Dateien][sources] und die Ressourcen herunter die zu diesem Tutorial gehören. Wenn du bereits das Phaser Repository von Github ausgecheckt hast, dann hast du diese Daten bereits. Schau einfach in den resources/tutorials Ordner.

Und du brauchst ein sehr, sehr grundlegendes Wissen über JavaScript.

Stell auch sicher, dass du dir den [Getting Started Guide][getting_started] durchliest, er zeigt dir wie du das Framework runterlädst, eine lokale Entwicklungsumgebung aufsetzt und gibt dir einen flüchtigen Eindruck über ein Phaser Projekt und seine Hauptfunktionen.

Wenn du durch den Getting Started Guide durch bist hast du Phaser heruntergeladen und alles ist eingerichtet und bereit fürs Programmieren. Lade die Ressourcen für dieses Tutorial herunter und entpacke sie in das Root-Verzeichnis deines Webservers.

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

Zeile 1 ist die Zeile welche Phaser zum Leben erweckt indem es eine Instanz von einem Phaser.Game Objekt erzeugt und sie einer lokalen Variablen `game` zuweist. Sie `game` zu nennen ist eine gängige Praxis, aber kein Muss, und du wirst es auch so in den Phaser Beispielen vorfinden.

Die ersten zwei Parameter sind die Breite und die Höhe des Canvas Elements welches Phaser erzeugen wird. In unserem Fall 800 x 600 Pixel. Dein Spiel kann jede Größe haben die du willst, aber das ist die Größe in der wir unser Spiel anzeigen werden. Der dritte Parameter kann entweder Phaser.CANVAS, Phaser.WEBGL oder Phaser.AUTO sein. Dies ist der Rendering Context welchen du benutzen willst. Der empfohlene Wert ist Phaser.AUTO welcher automatisch versucht WebGL zu verwenden, aber wenn der Browser oder das Gerät dies nicht unterstützen dann wird auf Canvas umgeschalten.

Der vierte Paramter ist ein leerer String, dies ist die ID des DOM Elements in welchem du gerne den Canvas einfügen würdest den Phaser erzeugt. Da wir ihn leer gelassen haben wird es einfach an den Body angehöngt. Der letzte Parameter ist ein Objekt, welches die Referenzen zu den essenziellen Phaser Funktionen beinhaltet. Ihre Verwendung wird gründlich erklärt werden. Beachte das dieses Objekt nicht zwingend notwendig ist - Phaser unterstützt ein vollkommenes State System mit welchen man den Code in sehr viel sauberere einzelne Objekte aufsplitten kann. Aber für einen einfachen Getting Started Guide wie hier werden wir diesen Ansatz verwenden da er uns sehr viel schnelleres Prototyping erlaubt.

[sources]: https://github.com/photonstorm/phaser/raw/master/resources/tutorials/02%20Making%20your%20first%20game/phaser_tutorial_02.zip
[getting_started]: http://phaser.io/tutorials/getting-started