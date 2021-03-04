# Übung 4.1 #

## Flexbox Model ##

### 4 Divs nebeneinander ###

1. Erstellen Sie ein `div` Element welche 100% Breit ist. Fügen Sie unterhalb von diesem `div` vier weitere `div` Elemente hinzu.

1. Geben Sie dem obersten `div` die CSS Eigenschaft `display: flex;`

    > Mit dem obersten Element ist jenes gemeint welches die anderen vier Elemente beinhaltet.

1. Die untergeordneten `div`'s brauchen nun noch die Eigenschaft `flex: 1;`

1. Geben Sie allen untergeordneten `div` Elementen ein `border: 1px solid black;` und `height: 100%;`.

1. Sie sehen nun, dass diese vier Elemente nebeneinander dargestellt werden und **dass die Breite gleichmässig verteilt ist**

> `display: flex;` ist die Basis eines Flex-Layouts und muss auf dem übergeordneten Element sein.

> `flex: 1;` bedeutet, dass das Element eine Einheit breit sein soll.
> 
> Die gesamte Breite wird nun zwischen allen Elementen entsprechend ihrer Angabe aufgeteilt. Versuchen Sie
> gewissen Elementen eine Breite von `flex: 2;` zu geben und sehen Sie was passiert.

### Dynamische Breiten ###

1. Kopieren Sie das obere Beispiel als Basis, entfernen Sie jedoch eines der inneren `div` Elemente.

1. Wir möchten nun, dass die beiden Elemente am Rand eine fixe Breite haben und das innere Element den restlichen Platz einnimmt.

1. Geben Sie den beiden Elementen am Rand folgende Eigenschaft: `flex-basis: 200px;`

1. Geben Sie dem Element in der Mitte folgende Eigenschaft: `flex-grow: 1;`

1. Spielen Sie mit der Grösse des Browserfenster und sehen Sie was passiert.

> `flex-basis: 200px;` gibt an, wie breit ein Element initial (d.h. wenn genug Platz vorhanden ist) sein soll.

> `flex-grow: 1;` gibt an, dass das Element breiter werden darf. Ist nur ein Element mit `flex-grow` vorhanden, so nimmt dieses allen verfügbaren Platz ein.
> Sind mehrere Elemente vorhanden so wird der verfügbare Platz dazwischen aufgeteilt.

### Mindestbreite ###

1. Kopieren Sie wieder das letzte Beispiel. Bei diesem Fall wurden die beiden Spalten links und rechts kleiner, falls der Platz nicht ausreichte.

1. Wir möchten nun, dass die erste Spalte nicht kleiner wird. Geben Sie dem Element dazu die Eigenschaft `flex-shrink: 0` und sehen Sie was passiert.

> `flex-shrink` gibt an, dass das Element nicht kleiner werden soll.

### "Zeilenumbrüche" ###

Bisher wurden alle Flex-Elemente immer nebeneinander dargestellt. Wir können jedoch auch angeben, dass die Elemente umbrechen.

Verwenden Sie hierfür folgenden HTML Code:

```html
<div class="container">
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
</div>

<style type="text/css">
    .container {
        display: flex;
    }

    .container div {
        height: 200px;
        border: 1px solid black;
        flex-basis: 200px;
    }
</style>
```

> Sie können das CSS in eine externe CSS oder SCSS Datei auslagern. Es ist nur aus Gründen der Übersichtlichkeit inline angegeben.

Wie Sie sehen werden nun alle Elemente nebeneinander dargestellt. Da der verfügbare Platz nicht ausreicht, wird der Platz im Verhältniss zur `flex-basis` Angabe aufgeteilt.

Fügen Sie nun der Klasse `container` noch die Eigenschaft `flex-wrap: wrap;` hinzu. Nun sehen Sie, dass die Elemente welche nicht mehr Platz auf der aktuellen Zeile haben, umgebrochen werden.

### Reihenfolge ###

Sie können mit Flex auch die Reihenfolge der Elemente ändern.

Schauen Sie Sich hierfür dieses Beispiel im Browser an:

```html
<div class="container">
    <div>1</div>
    <div>2</div>
    <div>3</div>
</div>

<style type="text/css">
    .container {
        width: 100%;
        display: flex;
    }

    .container div {
        border: 1px solid black;
        flex-basis: 300px;
        height: 100px;
        text-align: center;
    }

    div:nth-child(1) {
        order: 2;
    }

    div:nth-child(2) {
        order: 3;
    }

    div:nth-child(3) {
        order: 1;
    }
</style>
``` 

### Vertikale Aufteilung ###

Mit Flex lässt sich der Bildschirm nicht nur in der Horizontalen in beliebige Abschnitte einteilen, sondern auch in der Vertikalen.

Öffnen Sie hierfür dieses HTML Dokument in einem Browser:

```html
<div class="container">
    <div>
        Sehr viel Inhalt<br />
        Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet.
    </div>
    <div>
        Wenig Inhalt
    </div>
    <div>
        Mittlerer Inhalt
        Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat.
    </div>
</div>

<style type="text/css">
    .container {
        width: 100%;
        height: 100%;
        flex-direction: column;
        display: flex;
    }

    .container div {
        border: 1px solid black;
        flex: 1;
    }
</style>
```

Wie Sie sehen ist die volle Höhe immer gleichmässig auf alle 3 `div` Elemente aufgeteilt.

Die Richtung, in welcher Flex die Elemente verteilt wird mit `flex-direction: column;` gesteuert.