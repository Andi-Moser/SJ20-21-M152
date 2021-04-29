# Übung 5.1 #

> Diese Übung benötigt keine Abgabe!

## Responsive Web Design (RWD) ##

CSS ist bekanntliche keine Programmiersprache im eigentlichen Sinne (zumindest zurzeit noch nicht - CSS entwickelt sich
stetig weiter). Was CSS fehlt sind Elemente wie `if` Abfragen oder `while` Loops.

Mit dem Aufkommen von Mobilen Geräten wurde nach Lösungen gesucht, Websiten auf allen Geräten möglichst optimal darzustellen.
Eine weit verbreitete Lösung war damals eine Kopie der Seite zu erstellen und diese unter einer anderen Domain (z.B. `m.exambple.com`)
online zu stellen.

Dies bringt jedoch einige offensichtliche Probleme. Am mühstamsten war es, zwei komplett getrennte Layouts pflegen zu müssen.
Anpassungen musste immer an beiden Seiten gemacht werden.

So wurde das Verlangen immer stärker, eine Möglichkeit zu haben dasselbe Layout (die `CSS` Files) für die Desktop- und Mobileseite
zu verwenden. Als Antwort darauf wurden die sogenannten `CSS Media Queries` eingeführt.

## Media Queries ##

Media Queries sind eine Art der `if` Abfrage. Der Unterschied ist zu anderen Programmiersprachen ist jedoch, dass ich mit
Media Queries nicht jede beliebige Variable abfragen kann.

Ein Media Query sieht wie folgt aus:

```css
@media only screen and (max-width: 600px) {
  body {
    background-color: orange;
  }
}
```

> Bei diesem Beispiel werden alle CSS Regeln im Media Query nur angewandt, wenn das Ausgabeformat ein Bildschirm ist und maximal 600px breit ist.

Die allgemeine Definition der Media Queries sieht wie folgt aus:

```css
@media not|only mediatype and (mediafeature and|or|not mediafeature) {
  CSS-Code;
}
``` 

### Medientypen ###

Der erste Teil (`not|only mediatype`) kann verwendet werden um den Darstellungstyp abzufragen. Die folgende Liste zeigt die
meistgenutzen Mediatypen:

|Mediatype|Beschreibung|
|---|---|
|`all`|Alle Typen|
|`screen`|Bildschirm|
|`print`|Drucker (wird verwendet um Websiten schön auszudrucken)|

Der Medientyp `print` wurde früher noch häufiger gebraucht - vielleicht haben Sie auch schon ein Print-Icon auf einer Website gesehen.
Heutzutage ist dies aus der Mode gefallen und es wird nur noch für den Typ `screen`, also den Bildschirm, optimiert.

### Mediafeature ###

Der zweite Teil (`and (mediafeature and|or|not mediafeature)` oder `and (max-width: 600px)`) ist der für uns interessante Teil.
Hier können, Features des Medientypen abgefragt werden. Die komplette Tabelle aller Features finden sie [hier](https://developer.mozilla.org/de/docs/Web/CSS/Media_Queries/Using_media_queries#media_features),
wir benötigen jedoch hauptsächlich folgende Eigenschaften:

|Mediafeature|Wert|
|---|---|
|`min-width`|Die Breite des Browsers|
|`max-width`|Die Breite des Browsers|

> Halt, Stopp!
> Beide Features haben ja denselben Wert? Wie kann das funktionieren?
>
> Da Media Queries nicht eine `if` Abfrage im eigentlichen Sinne ist, ist der Operator (`=`, `<`, `>`) gleich im Feature enthalten!
>
> `min-width: 1200px` ist alles immer dann WAHR, wenn das Browserfenster 1200px oder Breiter ist.

## Der Viewport ##

Weiter oben wurde die historische Entwicklung von CSS und Media Queries erwähnt. Hersteller von Browser für Mobilgeräte warteten
nämlich nicht auf die Einführung und Implementierung von Responsive Websites (Auch heute sind viele Websiten noch nicht optimiert).
Um ihren Benutzern ein möglichst gutes Interneterlebnis zu bieten, griffen die Hersteller zu einem Trick:

Die (unoptimierte) Seite wird dargestellt als wäre man an einem Desktop Gerät und wird dann verkleinert dass sie auf dem schmalen
Bildschirm platz hat. Der Benutzer kann über den Touchscreen zoomen und sieht so dieselbe Seite wir ein Desktop Benutzer.

Leider (bzw. aufgrund der vielen nicht-optimierten Seiten) ist dieses Verhalten immer noch in vielen Mobilgeräten vorhanden. Sie können
es auch erzwingen, wenn Sie in den Einstellungen des Browsers die Option "Desktop Seite anzeigen" auswählen.

Um sicherzustellen, dass der Mobile Browser die Seite nicht als skalierte Desktopversion darstellen will, müssen wir folgendes HTML Tag im `<head>` angeben:

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

Dieses Tag zwingt den Browser dazu, als (virtuelle) Breite die effektive Breite des Gerätes zu nehmen (`width=device-width`).
`initial-scale=1.0` setzt den Zoomfaktor auf 1.

Man kann auch das Zoomen auf der Seite verbieten, mit folgendem Tag:

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
```

Die beiden weiteren Angaben (`maximum-scale=1.0, user-scalable=no`) verbieten das Zoomen. Dies ist jedoch eine schlechte Angewohnheit
und sollte nicht verwendet werden.

## Vorgehen für RWD ##

Nun haben wir das Vorwissen um anzufangen, Layouts für Desktop und Mobilgeräte umzusetzen. Doch wo startet man am besten?
Es gibt zwei Ansätze hierfür, wobei der eine sehr stark verbreitet ist:

> Bei beiden Ansätzen geht man davon aus, dass man mit einer Grösse des Browserfenster startet und ihn dann entweder stetig verbreitert oder verschmälert. 

### Mobile First ###

Mobile First bedeutet, dass man das Layout zuerst für kleine Bildschirme entwirft und dann anpasst sobald der Bildschirm
zu gross wird.

Der Vorteil ist, dass man sich bei einem kleinen Bildschirm mehr überlegen muss, welche Elemente man wohin platziert - die
komplexe Aufgabe ist also schon zu Beginn erledigt.

Mobile First ist sehr stark verbreitet. Besonders bei Applikationen (Eine Website dient zum Marketing, mit einer Applikation wird gearbeitet)
ist dieser Ansatz zwingend.

> Ein Online-Shop gilt in diesem Zusammenhang auch als Applikation. Sobald viel Input vom Benutzer erwartet wird kann man von einer Applikation sprechen.

### Desktop First ###

Beim Desktop First Ansatz wird das Layout zuerst für grosse Bildschirme erstellt und dann angepasst sobald der Browser zu klein ist.
Der Vorteil ist, dass auf dem grossen Desktop mehr Platz für schön und aufwändig gestaltete Elemente vorhanden ist.

Auf Mobilgeräten wird der Inhalt meistens einfach "von oben nach unten" aufgelistet. Beim Desktopgerät muss man sich jedoch überlegen
ob man Inhalte in Sidebars auslagern möchte.

Wir werden im Unterricht mit dem Desktop First Ansatz arbeiten. Unsere Aufgabe ist es nicht, komplexe Applikationen schön auf dem Smartphone darzustellen.
Uns geht es hautpsächlich darum, Informationen möglichst ansprechend an den Benutzer zu vermitteln.

## Media Queries in der Anwendung ##

Wir werden den Desktop First ansatz verwendet. Das Vorgehen um ein responsives Layout zu erstellen ist also folgendes:

1. Layout für den Desktop erstellen
1. Browser so lange kleiner machen, bis das Layout nicht mehr gut aussieht
1. Anpassungen vornehmen für die aktuelle Browsergrösse
1. Punkt 2 und 3 solange wiederholen, bis die kleinste Grösse erreicht wird.

> Dieses Vorgehen kann bedeuten, dass man 20 verschiedene Abstufungen hat. Meistens ist dies jedoch nicht benötigt.
> In der Praxis unterscheidet man häufig zwischen 3 Grössen: Desktop, Tablet und Mobile
>
> Eine Website für jede erdenkliche "Zwischengrösse" zu optimieren ist wirtschaftlich untragbar und wird daher auch nicht gemacht.

Sobald ein Punkt erreicht wird, müssen die Elemente für die kleinere Breite angepasst werden.
Dafür notiert man sich die Bildschirmbreite (z.B. 900px) und überschreibt die bestehenden CSS Angaben
in einem Media Query mit `max-width: 900px`.

> Diese CSS Angaben gelten dann für alle Fenstergrösser < 900px. Es werden nicht alle CSS Eigenschaften wiederholt,
> sondern nur jene überschrieben welche angepasst werden müssen.

```css
.person {
    width: 25%;

    @media screen and (min-width: 900px) {
        width: 50%;
    }
}
```

In diesem Beispiel ist das Person-Element auf Desktopgrösse 25% breit (also 4 Personen pro Zeile). Ab 900px wird das Element neu
50% breit dargestellt (also 2 pro Zeile)

> Das oben verwendete Beispiel ist in SCSS geschrieben. Ohne SCSS darf man keine Media Queries in anderen Selektoren verschateln:

```css
.person {
    width: 25%;
}

@media screen and (min-width: 900px) {
    .person {
        width: 50%;
    }
}
```