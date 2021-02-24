# Übung 3.1 #

> Wie immer, erstellen Sie zuerst einen eigenen Ordner für diese Übung.

> Bitte achten Sie auf die korrekte Benennung des Ordners: `Uebung3-1`.

## SCSS ##

### Was ist SCSS? ###

SCSS ist eine Erweiterung für CSS die es für den Entwickler einfacher macht, komplexen CSS
Code zu schreiben. SCSS unterstützt z.B. Variablen oder die Verschachtelung von CSS Definitionen.

Beim Einsatz von SCSS sind folgende Punkte zu beachten:

- Der Browser selbst versteht kein SCSS. SCSS wird zuerst zu CSS kompiliert.
- SCSS ist eine Erweiterung zu CSS. Jeder valide CSS Code ist auch in SCSS valide.

### SCSS vs SASS ###

Häufig verwenden diese beiden Begriffe austauschbar verwendet. Ursprünglich hiess diese Technik nur
`SASS` und verzichtete auf die geschweiften Klammern. Um die Lesbarkeit zu erhöhen wurde bald `SCSS` als Dialekt
von `SASS` eingeführt (`Sassy CSS`).

Unterdessen ist die SCSS Syntax der Standard für SASS weshalb man oft zu SASS auch SCSS sagt.

### Installation Compiler ###

Installieren Sie Sich nun einen SCSS Compiler. Es gibt diverse welche auf NodeJS basieren, ich
empfehle jedoch die Verwendung eines Visual Studio Code Plugin namens [Live Sass Compiler](https://marketplace.visualstudio.com/items?itemName=ritwickdey.live-sass).

### Testen des Compilers ###

Erstellen Sie zum Testen eine Datei `style.scss` und fügen Sie dort normales CSS ein. Wenn der Compiler
korrekt läuft (Anleitung des gewählten Compilers beachten!) wird ein `style.css` File generiert.

> Dieses (generierte) File muss nun im HTML Code eingebunden werden!

## Aufgaben ##

Wir möchten nun einen Block erstellen, in welchem ein Mitarbeiter dargestellt wird. Der Block sollte in etwa so aussehen:

![Übung 3.1](https://github.com/Andi-Moser/SJ20-21-M152/raw/master/m152/Uebungen/img/Uebung3-1.png)

Sie können für den Block folgendes HTML verwenden:

```html
<div class="person">
    <img src="http://placehold.it/300x300" />
    <div class="title">
        Andi Moser
    </div>
    <div class="text">
        Web Entwickler
    </div>
    <button>Kontaktieren</button>
</div>
```

Hier noch einige Hinweise:

- Damit das `div.person` nicht 100% Breit wird, verwenden Sie `display: inline-block`
- Um das Bild rund darzustellen verwenden Sie `border-radius: 50%`
- Den Schatten können Sie mit `box-shadow: #777279 1px 1px` einfügen

Verwenden Sie dabei die Möglichkeiten welche SCSS uns bietet. Sie müssen keine weiteren Klassen/IDs im HTML Code hinzufügen!