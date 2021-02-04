# Übung 2.1 #

> Wie immer, erstellen Sie zuerst einen eigenen Ordner für diese Übung.

## CSS Selektoren ##

Es gibt verschiedenste CSS Selektoren - doch nicht jeder Selektor ergibt in jedem
Kontext Sinn.

Im Folgenden sind die wichtigsten Selektoren aufgelistet. Eine komplette Liste aller Selektoren finden
Sie [hier](https://www.w3schools.com/cssref/css_selectors.asp).

**Standard Selektoren**

| Name | Selektor | Anwendung |
| --- | --- | --- |
| Verschachtelung | `div ul` | Wählt alle `ul` Elemente welche sich in einem `div` Element befinden |
| Element | div | Wählt alle `div` Elemente |
| Klasse | .myClass | Wählt alle Elemente welche die `myClass` Klasse besitzen (`class='myClass'`) |
| Mehrere Klassen | .myClass.red | Wählt alle Elemente welche die Klassen `myClass` und `red` besitzen (`class='myClass red'`) |
| ID | #myElement | Wählt das Element mit der ID `myElement` (`id='myElement'`)<br />Achtung, keine zwei Elemente dürfen dieselbe ID besitzen |
| Direkt unterhalb | ul > li | Wählt alle `li` Elemente welche direkt unterhalb eines `ul` Element stehen (`<ul><li>Element</li></ul>`) |
| Direkter nachfolger | li + li | Wählt alle `li` Elemente welche direkt nach einem `li` Element stehen (`<li></li><li></li>`) |

**Pseudo Selektoren**

| Name | Selektor | Anwendung |
| --- | --- | --- |
| Hover | :hover | Spricht Elemente an über welchen sich der Mauszeiger befindet |
| Focus | :focus | Spricht Elemente an welche den Fokus haben (z.B. wenn der Benutzer mit `Tab` die Elemente durchgeht) |
| Positionen | :last-child<br />:first-child<br />:first-of-type<br />:last-of-type | Werden verwendet um Elemente aufgrund ihrer Position im Elternelement auszuwählen |
| Formulare | :required<br />:optional<br />:invalid<br />:valid | Werden verwendet um Formularelemente aufgrund ihres Status auszuwählen |


## Aufgabestellung ##

Erstellen Sie ein HTML File mit folgendem Inhalt:

```html
<html lang="de">
    <head>
        <title>Übung 2.1</title>
    </head>

    <body>

        <h1>Dieses Tag ist ein: h1</h1>

        <p class="lead">p-Tag mit Klasse 'lead'</p>

        <p class="text">p-Tag mit Klasse 'text'</p>

        <div>
            List innerhalb eines div Tags
            <ul>
                <li>Listeneintrag 1</li>
                <li>Listeneintrag 2</li>
                <li>Listeneintrag 3</li>
            </ul>
        </div>

        <ul>
            <li>Liste</li>
            <li>ausserhalb</li>
            <li>eines div-Tags</li>
        </ul>

        <ul class="long">
            <li>Eine</li>
            <li>lange</li>
            <li>Liste</li>
            <li>mit</li>
            <li>vielen</li>
            <li>Punkten</li>
        </ul>

        <form>
            <input type="text" id="name" value="Input mit id 'name'" />
            <input type="text" value="Normales Textfeld" />
            <input type="number" value="1234" />
        </form>

    </body>

    <style type="text/css">
        // Styles hier einfügen
    </style>
</html>
```

Formattieren Sie das bestehende HTML nun so dass es wie auf folgendem Bild aussieht:


![Übung 2.1](https://github.com/Andi-Moser/SJ20-21-M152/raw/master/m152/Uebungen/img/Uebung2-1.png)