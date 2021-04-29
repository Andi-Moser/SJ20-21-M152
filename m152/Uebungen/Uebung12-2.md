# Übung 12.2 #

## SVG Grafiken ##

SVG Grafiken haben den grossen Vorteil, da sie aus Vektoren bestehen. Dadurch sind sie nicht nur skalierbar,
sondern lassen sich auch direkt per "Code" erstellen.

Schauen Sie Sich folgendes Beispiel an:

```html
<svg width="100" height="100">
  <circle cx="50" cy="50" r="40" stroke="green" stroke-width="4" fill="yellow" />
</svg>
```
Sie können dieses Beispiel [hier](https://www.w3schools.com/graphics/tryit.asp?filename=trysvg_myfirst) im Browser ansehen.

Durch die Angabe von `<svg width="100" height="100">` wird quasi eine 100x100 Pixel grosse "Zeichenfläche" geschaffen.
Auf dieser Fläche lassen sich mit den SVG Tags diverse Elemente einfügen.

Lesen Sie Sich jetzt kurz in die Dokumentation der verschiedenen Elemente von [w3schools](https://www.w3schools.com/graphics/svg_rect.asp)
ein.

### Skalierbarkeit ###

Wenn Sie bei obenstehendem SVG die `width` und `height` Parameter verändern, werden Sie sehen, dass die Grafik darin
sich **nicht** skaliert.

Damit sich ein SVG korrekt skaliert, muss das `viewbox` Atrribut angegeben werden:

```html
<svg width="10" height="10" viewbox="0 0 100 100">
   <circle cx="50" cy="50" r="40" stroke="green" stroke-width="4" fill="yellow" />
</svg> 
```

Mit dem `viewbox` Attribut kann man quasi eine "virtuelle Zeichenfläche" erstellen. In obigen Beispiel ist diese 100x100 Pixel
gross, aber sie könnte auch andere Formate annehmen:

`viewbox="0 0 50 250` (50x250 Pixel)

Auf dieser "virtuellen Zeichenflächen" können Sie nun die SVG Elemente platzieren - und sie werden korrekt skaliert.

### Auftrag ###

Erstellen Sie ein cooles Logo per SVG. Spielen Sie mit den Elementen um ein Logo zu erstellen. Haben Sie keine Ideen für
ein Logo versuchen Sie ein bekanntes Logo nachzuahmen.

Laden Sie das HTML File mit dem Logo in 3 verschiedenen Grössen (skalieren) auf Ihr Git Repository als Abgabe hoch.