# Übung 17.2 #

## Konva ##

Beim direkten Arbeiten mit dem `<canvas>` Element merkt man schnell, dass die simple Javascript API dafür etwas
umständlich ist.

Aus diesem Grund gibt es mehrere Frameworks welche einem die mühsame Arbeit des "Verschieben" des Stiftes abnehmen,
eine davon ist [Konva](https://konvajs.org/docs/overview.html).

Lesen Sie die oben verlinkte Einführungsseite durch und spielen Sie mit den verschiedenen Möglichkeiten Elemente
zu zeichnen.

Sie können folgendes HTML Grundgerüst verwenden:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Canvas tutorial</title>
    <script type="text/javascript">
        function draw () {
            // first we need to create a stage
            var stage = new Konva.Stage({
                container: 'viewport',   // id of container <div>
                width: 500,
                height: 500
            });

            // then create layer
            var layer = new Konva.Layer();

            // create our shape
            var circle = new Konva.Circle({
                x: stage.width() / 2,
                y: stage.height() / 2,
                radius: 70,
                fill: 'red',
                stroke: 'black',
                strokeWidth: 4
            });

            // add the shape to the layer
            layer.add(circle);

            // add the layer to the stage
            stage.add(layer);

            // draw the image
            layer.draw();
        }
    </script>

</head>
<body onload="draw();">
<div id="viewport"></div>
</body>
<script src="https://unpkg.com/konva@8/konva.min.js"></script>

</html>
```

> Hinweis: Normalerweise würden wir die Javascript Datei per NPM installieren und das eigens geschriebene Javascript auslagern.
> Für kleinere Übungen reicht es jedoch vollkommen aus, wenn das JS direkt in der HTML Datei eingebettet ist.

## Aufgabe ##

Versuchen Sie nun den Smiley von der letzten Übung selbstständig mit Konva nachzubauen.

Profis können einbauen dass wenn man dem Smiley in ein Auge klickt dieser unglücklich wird.