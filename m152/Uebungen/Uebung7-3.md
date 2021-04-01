# Übung 7.3 #

## Komplexere Applikationen ##

Ein zentrales Element in Vue sind die Daten (`data`). Diese können zwar sehr simpel sein,
werden in grossen Applikationen aber schnell sehr komplex. Meisten werden diese Daten auch nicht
statisch hinterlegt, sondern werden von einer API abgefragt.

Erstellen Sie eine Applikation welche folgende Liste von Fächern und Noten als Daten gespeichert hat und
dazu folgende Ausgabe macht:

- Alle Fächer mit allen Noten
- Pro Fach: Durchschnitt (gerundet auf 0.5)
- Durchschnitt über alle Fächer
- Mangelpunkte (Noten < 4) über alle Fächer

```javascript
[
    {
        name: "Mathematik",
        grades: [5,4.7,3.5,4.1] 
    },
    {
        name: "Geschichte",
        grades: [5.5,4.9,5.75] 
    },
    {
        name: "Physik",
        grades: [2,2.7,4.3] 
    },
    {
        name: "Deutsch",
        grades: [4.25,4.1,3.5] 
    },
]
```

## Bonusaufgabe ##

Fügen Sie ein Eingabefeld und Butotn ein, welche einem Fach eine neue Note hinzufügen.