# Übung 6.1 - Webpack #

Webpack ist ein "Module Bundler". Er bündlet verschiedenste Javascript Files (und auch CSS Files, Fonts und Bilder)
in einer Art die sicherstellt das 1) die Seite so schnell lädt wie möglich und 2) sicherstellt dass alle Dateien in der
korrekten Reihenfolge geladen werden.

## Geschichte ##

### Web2.0 ###

Zusammen mit dem "Web 2.0" wurden diverse Javascript Frameworks und Libraries gross, wie zum Beispiel:

- jQuery
- MooTools
- ExtJS

Diese Werkzeuge basierten zwar alle auf normalem Javascript, boten einem jedoch Möglichkeiten welche mit reinem JS sehr
aufwändig umzusetzen sind. jQuery bot erstmals eine einfache Möglichkeit auf HTML Elemente per CSS Selektoren zuzugreifen,
ExtJS bot einfache Funktionen um aus Javascript Daten automatisch HTML Tabellen mit Such, Filter und Sortierfunktion zu erstellen.

Beinahe alle dieser Frameworks unterstützen auch Plugins. Für jQuery waren (sind) abertausende Erweiterungen verfügbar.
Diese Plugins wurden jeweils vom Entwickler heruntergeladen und manuell im HTML verlinkt. Meist wurden von einem Plugin gleich
mehrere Files zur Verfügung gestellt:

- plugin.css - Alle Styles welche das Plugin benötigt.
- plugin.js - Der (unkomprimierte) JS Code damit der Entwickler bei Fehlern debuggen konnte.
- plugin.min.js - Der komprimierte Code welcher kleiner war und deshalb schneller geladen wurde.

So konnten, bei einer aufwändigen Website, gut 10 verschiedene solche Plugins im Einsatz sein. Der HTML Code dazu
sah bald mal so aus:

```html
<head>
    <link rel="stylesheet" href="/plugins/plugin1/styles.css" />
    <link rel="stylesheet" href="/plugins/gallery/css.css" />
    <link rel="stylesheet" href="/plugins/swiper/stylesheet.css" />
    <link rel="stylesheet" href="/plugins/contactform/styles.min.css" />
    <link rel="stylesheet" href="/plugins/peters-lightbox/styles.css" />
    <link rel="stylesheet" href="/plugins/peters-lightbox/styles-dark.css" />
    <link rel="stylesheet" href="/plugins/fujikama/utils.css" />
    <link rel="stylesheet" href="/plugins/permans/style-1.0.14.dist.min.css" />
</head>
<body>
    <script type="text/javascript" src="/plugins/plugin1/script.js"></script>
    <script type="text/javascript" src="/plugins/gallery/js.js"></script>
    <script type="text/javascript" src="/plugins/swiper/javascript.js"></script>
    <script type="text/javascript" src="/plugins/contactform/script.min.js"></script>
    <script type="text/javascript" src="/plugins/peters-lightbox/plugin.js"></script>
    <script type="text/javascript" src="/plugins/peters-lightbox/script-themes.js"></script>
    <script type="text/javascript" src="/plugins/fujikama/utils.js"></script>
    <script type="text/javascript" src="/plugins/permans/script.1.0.14.js"></script>
</body>
```

Dies bedeutete für den Entwickler immer mehr Aufwand:

- Die Reihenfolge war wichtig (nur JS): Benötigte ein Plugin Funktionen eines anderen, so musste dies vorher geladen sein
- Das Namensschema: Jeder Entwickler benannte seine Dateien nach einem eigenen Schema.
- Vergessene Abhängigkeiten: Wurde vergessen, dass das Plugin XY das Plugin AB benötigt, ging nichts mehr
- Keine Qualitätskontrolle: Wer stellte sicher, dass ein Plugin auch wirklich dies macht was es soll?
- Ladezeit: Für jedes JS und CSS File musste ein eigener HTTP Request gemacht werden. Die Seite konnte erst schön dargestellt werden,
 wenn alle Plugins fertig geladen waren.
 
### Dependency Management ###

Viele Entwickler hatten bald genug vom mühsamen Plugin hin und her kopieren. Zusammen mit der Entstehung von NodeJs entstand deshalb
`npm`, der Node Package Manager.

Das Ziel von NPM ist es, die Abhängigkeiten zwischen Plugins zu automatisieren. NPM verfügbt über eine öffentliche Quelle in
welcher alle Entwickler Plugins (ab jetzt Pakete genannt) zur Verfügung stellen können. Zusammen mit dem Paketinhalt können die
Entwickler dort angeben, welche weiteren Pakete benötigt werden.

Fügt man als "Endverbraucher" nun ein Paket mit NPM hinzu, so werden automatisch alle nötigen Abhängigkeiten installiert.

Entwickler von Pakete hatten so auch den Anreiz nicht zu viel in ein Paket zu packen. Jedes Paket (oder auch Modul) soll nur genau
eine Funktion übernehmen (z.B. das Anzeigen von Bildergallerien). Wird ein Paket zu gross, sollte es möglichst in Module unterteilt werden.

### Das Dateichaos und Module Bundler ###

Grundsätzlich schön und gut, einige der beschriebenen Probleme wurden damit gelöst.

Dennoch müssen nun viele Files einzeln geladen werden und "verstopfen" den HTML Code. Ausserdem: Es gibt immer noch
Pakete mit sehr grossem Funktionsumfang. Was ist aber, wenn ich von einem solchen Paket nur ein oder zwei Module benötige?

Hier kommt ein Module Builder wie Webpack zum Einsatz. Webpack analysiert den Javascript Code und stellt aus dem eigenen Code
und allen installierten Paketen ein einziges Javascript File zur Verfügung, welches allen Code enthält den man benötigt.

## Webpack ##

Im Rahmen unseres Unterrichts werden wir Webpack nur sehr oberflächlich verwenden. Um aber eine ungefähre Idee der Verwendung
zu bekommen, arbeiten Sie Sich bitte durch [dieses Webpack Tutorial](https://webpack.js.org/guides/getting-started/) (nur die erste Seite)

## Weitere Funktionen ##

Webpack kann weitaus mehr als nur Javascript bündeln. Diese Punkte sprengen den Rahmen dieses Unterrichts, aber es ist dennoch
Interessant wenn man sie mal gehört hat:

- Bilder automatisch optimieren
- Auto-Reload: Der Browser wird bei Änderungen automatisch neu geladen (Dev-Server)
- SCSS/SASS/Stylus/LESS kompilieren
- Typescript kompilieren
- TreeShaking: Automatisch ungebrauchte CSS Regeln entfernen
- Und noch viel mehr