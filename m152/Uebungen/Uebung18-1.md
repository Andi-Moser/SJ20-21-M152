# Übung 18.1 #

## Vier gewinnt ##

Untenstehend finden Sie einen vorbereiteten Start-Code für ein Vier gewinnt Spiel.

Dieser Code erzeugt folgende Ausgabe (Koordinaten werden nicht angezeigt):

![Übung 18.1](https://github.com/Andi-Moser/SJ20-21-M152/raw/master/m152/Uebungen/img/Uebung18-1.png)

### Aufbau ###

Das Spiel speichert seine Daten in zwei Arrays, `board` und `circles`.

Im `board` wird lediglich der Spieler als Integer (1/2) abgelegt. `circles` enthält die Referenzen zu
den Konva Shapes um diese entsprechend einzufärben.

## Aufgabe ##

Studieren Sie den Code und vervollständigen Sie die markierten Todo's

> Diese sind als Kommentar mit `// TODO: ` markiert.

Am Schluss sollte das Spiel funktionieren.

## Code ##

```html
<!DOCTYPE html>
<html>
<head>
    <title>Canvas tutorial</title>
    <script type="text/javascript">
        function initGame () {
            var width = 7;
            var height = 6;
            var board = [];
            var circles = [];
            var circleSize = 60;
            var currentPlayer = 1;

            for (var i=0; i<width; i++) {
                board[i] = [];
                circles[i] = [];
                for (var j = 0; j < height; j++) {
                    board[i][j] = 0;
                    circles[i][j] = 0;
                }
            }

            // first we need to create a stage
            var stage = new Konva.Stage({
                container: 'viewport',   // id of container <div>
                width: width * circleSize,
                height: (height + 1) * circleSize
            });

            // then create layer
            var layer = new Konva.Layer();

            function makeCircles() {
                for (var x=0; x<width; x++) {
                    for (var y = 0; y < height; y++) {
                        var circle = new Konva.Circle({
                            x: (x * circleSize) + circleSize / 2,
                            y: stage.height() - ((y * circleSize) + circleSize / 2) - 1,
                            radius: (circleSize / 2) - 2, // 2px smaller for the border
                            stroke: 'black',
                            strokeWidth: 1
                        });

                        circle.setAttr('cx', x);
                        circle.setAttr('cy', y);

                        circles[x][y] = circle;

                        layer.add(circles[x][y]);

                    }
                }
            }

            function makeArrows() {
                for (var i=0; i<width; i++) {
                    var arrow = new Konva.Rect({
                        x: (i * circleSize) + (circleSize / 4),
                        y: (circleSize - 20) / 2,
                        width: (circleSize / 2),
                        height: (circleSize / 2),
                        fill: 'green'
                    })

                    arrow.setAttr('cx', i);

                    arrow.on('click', function() {
                        console.log('click on row', this.getAttr('cx'));

                        // TODO: set the appropriate value of the 'board' array to the current player

                        // TODO: check if the current player has won the game

                        currentPlayer = currentPlayer === 1 ? 2 : 1;
                        fillCircles();
                    })

                    layer.add(arrow);
                }
            }

            function fillCircles() {
                for (var x=0; x<width; x++) {
                    for (var y = 0; y < height; y++) {
                        // TODO: Paint circles according to the player who "owns" them.
                    }
                }
            }

            makeCircles();
            makeArrows();

            // add the layer to the stage
            stage.add(layer);

            // draw the image
            layer.draw();

            function areFourConnected(player){
                // horizontalCheck
                for (var j = 0; j<height-3 ; j++ ){
                    for (var i = 0; i<width; i++){
                        if (board[i][j] === player && board[i][j+1] === player && board[i][j+2] === player && board[i][j+3] === player){
                            return true;
                        }
                    }
                }
                // verticalCheck
                for (var i = 0; i<width-3 ; i++ ){
                    for (var j = 0; j<height; j++){
                        if (board[i][j] === player && board[i+1][j] === player && board[i+2][j] === player && board[i+3][j] === player){
                            return true;
                        }
                    }
                }
                // ascendingDiagonalCheck
                for (var i=3; i<width; i++){
                    for (var j=0; j<height-3; j++){
                        if (board[i][j] === player && board[i-1][j+1] === player && board[i-2][j+2] === player && board[i-3][j+3] === player)
                            return true;
                    }
                }
                // descendingDiagonalCheck
                for (var i=3; i<width; i++){
                    for (var j=3; j<height; j++){
                        if (board[i][j] === player && board[i-1][j-1] === player && board[i-2][j-2] === player && board[i-3][j-3] === player)
                            return true;
                    }
                }
                return false;
            }
        }
    </script>

</head>
<body onload="initGame();">
<div id="viewport"></div>
</body>
<script src="https://unpkg.com/konva@8/konva.min.js"></script>

</html>
```