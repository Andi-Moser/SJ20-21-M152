# Übung 16.1 #

## Canvas ##

Das `<canvas>` Element ist eines der flexibelsten Elemente in HTML.

Auf einem `<canvas>` Element lassen sich beliebige Formen und Text frei darstellen und bewegen. Es ist sozusagen
das äquivalent zu Windows Paint oder anderen Zeichnungsprogrammen.

### Canvas vs SVG ###

Auch SVG Dateien lassen sich bekanntlich direkt im Browser durch Javascript erstellen, wieso verwendet man dann
keine SVG Dateien?

Der grosse Unterschied liegt in der internen Verarbeitung: Das Canvas Element wird intern von der Grafikkarte
gezeichnet (oder zumindest von ihr beschleunigt). Dies ermöglicht es sogar gute und performante 3D Szenen auf
einem Canvas darzustellen. (So wurde die ganze Quake 3D Enginge bereits in [Javascript nachgebaut](http://www.quakejs.com/))

## Grundprinzipien ##

Das folgende HTML File zeigt den Grundaufbau und wie auf einem Canvas Element gezeichnet werden kann:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Canvas tutorial</title>
    <script type="text/javascript">
        function draw () {
            var canvas = document.getElementById('tutorial');
            if (canvas.getContext) {
                var ctx = canvas.getContext('2d');
                
                ctx.fillStyle = 'rgb(200, 0, 0)';
                ctx.fillRect(10, 10, 50, 50);

                ctx.fillStyle = 'rgba(0, 0, 200, 0.5)';
                ctx.fillRect(30, 30, 50, 50);
            }
        }
    </script>
    <style type="text/css">
        canvas {
            border: 1px solid black;
        }
    </style>
</head>
<body onload="draw();">
<canvas id="tutorial" width="500" height="500"></canvas>
</body>
</html>
```

Komplexere Formen können mit folgenden Methoden gezeichnet werden:

```javascript
function draw() {
  var canvas = document.getElementById('canvas');
  if (canvas.getContext) {
     var ctx = canvas.getContext('2d');

     ctx.beginPath();
     ctx.arc(75, 75, 50, 0, Math.PI * 2, true); // Outer circle
     ctx.moveTo(110, 75);
     ctx.arc(75, 75, 35, 0, Math.PI, false);    // Mund
     ctx.moveTo(65, 65);
     ctx.arc(60, 65, 5, 0, Math.PI * 2, true);  // Linkes Auge
     ctx.moveTo(95, 65);
     ctx.arc(90, 65, 5, 0, Math.PI * 2, true);  // Rechtes Auge
     ctx.stroke();
  }
}
```

Kopieren Sie dieses Beispiel in eine HTML Datei und studieren Sie diese.

Wie Sie sehen, ist es wirklich fast wie ein Zeichnungsprogramm. Der Programmierer steuert einen virtuellen
Stift welcher sich auf dem Canvas bewegt und gibt diesem Anweisungen wann er was zeichnen soll.

### Aufgabe ###

Versuchen Sie nun dieses Beispiel so umzubauen, dass der Smiley nicht lächelt sondern unglücklich ist.

> Hinweis: Versuchen Sie als erstes bei der Funktion `ctx.arc` welche den Mund zeichnet den letzten Parameter auf `true` zu setzen.