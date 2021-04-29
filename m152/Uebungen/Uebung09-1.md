# Übung 9.1 #

## Schriftarten ##

### Schriften im Web ###

Die CSS Definition `font-family: "Times New Roman", Times, serif;` ist bekannt. Doch woher kommen diese Schriften?
Schlussendlich könnte man auch folgendes Angeben: `font-family: ABCD, EFG, XYZ;`.

Die Schriftarten welche man als `font-family` angibt müssen auf dem lokalen Computer installiert sein.
Viele Firmen haben jedoch eine eigene Schriftart. Wenn diese im Web verwendet werden wollen, müssen sie
dem Client in einem passenden Format zur Verfügung gestellt werden.

### Schriftformate im Web ###

Folgende Dateiformate sind (oder waren) im Web gebräuchlich:

|Format|Bezeichnung|
|---|---|
| TrueType Fonts (.ttf) | Relativ altes Dateiformat, von Microsoft und Apple verwendet |
| OpenType Fonts (.otf) | Format für variable Schriftarten, &trade;Microsoft |
| Web Open Font Format (.woff/.woff2) | Format welches explizit für das Web entwickelt wurde. Es verwendet dieselbe Technologie wie TTF/OTF, ist aber komprimiert |

#### Variable Schriftarten ####

Eine "aufwändig" gestaltete Schrift im Browser darzustellen ist gar keine so leichte Aufgabe.

Im Druckbereich sind die DPI (Dots per Inch) fix definiert. Im Web kann nicht gesagt werden, wie gross die Schrift
beim Client dargestellt wird (Handydisplays mit höheren DPIs, Zoomfunktion). So müssen z.B. häufig wenn die Schrift fett
dargestellt wird Details weggelassen werden.

Bei herkömmlichen TTF Fonts wurde deshalb eine separate Schriftart pro Schriftdicke (`font-weight`) erstellt.
OTF Schriftarten sind variabel, das heisst eine "Schriftart" (= ein File) reicht für verschiedene Schriftdicken.

Unterdessen unterstützen auch TTF Fonts variable Schriften.

## Schriftarten finden ##

Schriftarten werden unter anderem auch bezahlt für einen einzigen Kunden hergestellt. Diese dürfen, verständlicherweise,
nicht von anderen Firmen oder für private Projekte verwendet werden. Will man eine Schriftart einbinden muss man auch die Lizenz
dafür besitzen (wie bei einem Bild).

Ein guter Ort um lizenzfreie Schriftarten zu finden ist [Google Fonts](https://fonts.google.com/).

## Schriftarten einbinden ##

Schriftarten können im CSS wie folgt eingebaut werden:

```css
@font-face {
  font-family: Schriftname;
  src: url(/path/to/font.ttf);
}
```

Diese Schriftart (namens `Schriftname`) kann nun als `font-family` eingebunden werden:

```css
font-family: "Schriftname", "Times New Roman", Times, serif;
```

> Wichtig ist immer noch alternative, allgemein verfügbare Schriftarten anzugeben. Die Alternativ-Fonts sollten möglichst
> imselben Stil wie die eigene sein. So sieht die Website auch einigermassen gut aus, wenn der Browser das Font-File nicht
> laden kann oder nicht "versteht".

Ist die Schrift nicht variabel, muss zudem noch für jede gewünschte Grösse ein eigenes Font-File verlinkt werden:

```css
@font-face {
  font-family: Schriftname;
  src: url(/path/to/font-bold.ttf);
  font-weight: bold;
}
```

Dieses File wird immer dann verwendet, wenn der Browser die Schrift `Schriftname` fett darstellen soll.
Ist es nicht vorhanden, versucht er die normale Schrift fett zu zeichnen, was nicht immer die gewünschten Ergebnisse hat.

## Aufgabe ##

Suchen Sie Sich auf Google Fonts eine passende Schriftart und binden Sie diese ein. Verwenden Sie dafür die Übung mit dem
Team-Block.