# Übung 2.3 #

> Wie immer, erstellen Sie zuerst einen eigenen Ordner für diese Übung.

## Spezifität ##

Die Spezifität eines CSS Selektors wird wie folgt berechnet:

| Spezifität | Selektor |
| --- | --- |
| 1000 | Inline-Styles (`style='color: red'`) |
| 100 | IDs |
| 10 | Klassen, Pseudo-Klassen, Attribute |
| 1 | Elementnamen |

## Aufgabe ##

Bauen Sie nun die Seite mit den 4 Buttons nach. Sie haben von Ihrem Auftraggeber hierzu
folgende Informationen erhalten:

- Fortfahren soll grün sein
- Zurück soll orange sein
- Abbrechen ist **immer** rot
- Neu Starten soll blau sein
- Inaktive Buttons sollen grau sein
- Gefährliche Buttons sollen orange sein
- Alle Elemente können aktiv oder inaktiv sein
    - Technisch gesehen erhalten diese Buttons eine Klasse inaktiv
    - Der Abbrechen Button soll weiterhin rot bleiben, auch wenn er inaktiv ist
- Alle Elemente können gefählrich oder ungefährlich sein
    - Ebenfalls mit einer Klasse, `dangerous`
- Buttons können auch ausgeblendet werden. Hierfür wird eine Klasse `hide` hinzugefügt
- Buttons über welchen der Mauszeiger befindet (`hover` Status) sollen einen roten Rand haben

Folgendes Stylesheet ist Teil des Designs und **muss** verwendet werden:

```css
button {
    display: block;
    visibility: visible;
    border-radius: 4px;
    margin-bottom: 10px;
    padding: 2px 10px;
}
```