# Übung 2.2 #

> Wie immer, erstellen Sie zuerst einen eigenen Ordner für diese Übung.

## Aufgabe 1 ##

Studieren Sie folgendes HTML File:

```html
<html>
<body>
    
    <p class="myClass" id="myId">Ich bin ein normales p Tag mit einer ID und Klasse</p>
    <p>Ich bin ein normales p Tag</p>
    <p class="myClass">Ich bin ein normales p Tag mit einer Klasse</p>
    
    <style type="text/css">
        p {
            color: red;
        }
    
        .myClass {
            color: green;
        }
    
        #myId {
            color: blue;
        }
    </style>
</body>
</html>
```

Überlegen Sie, ohne den Code aufzurufen, welche Farbe welches Element nun hat und besprechen
Sie dies mit Ihrem Sitznachbarn.

## Aufgabe 2 ##

Verwenden Sie für diese Aufgabe folgendes HTML File:

```html
<html>
    <body>
    
    <button id="continue">Fortfahren</button>
    <button id="back">Zurück</button>
    <button id="abort">Abbrechen</button>
    <button id="restart">Neu Starten</button>
    
    <style type="text/css">
        #continue {
            background-color: green;
        }
    
        #back {
            background-color: orange;
        }
    
        #abort {
            background-color: red;
        }
    
        #restart {
            background-color: blue;
        }
    </style>
</body>
</html>
```

Sie haben nun vom Kunden den Auftrag erhalten, das Interface so zu gestalten dass Buttons
welche nicht zur Verfügung stehen einen grauen Hintergrund haben.

Der Entwickler welcher für das Backend zuständig ist, sagt Ihnen, er kann bei den inaktiven
Buttons eine Klasse `inactive` (`class='inactive'`) hinzufügen.

Versuchen Sie nun diese `inactive` Klasse dem Neu-Starten Button hinzuzufügen und ihm eine
graue Hintergrundfarbe zu geben.

Klappt dies? Wenn nein, wieso nicht? Überlegen Sie Sich wieso, wir besprechen die Lösung
der Aufgabe im Plenum.