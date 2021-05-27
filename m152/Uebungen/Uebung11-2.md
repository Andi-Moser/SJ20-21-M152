# Übung 11.2 #

## Javascript und Video ##

Das HTML `video` Tag kennen Sie wahrscheinlich bereits. Dieses bietet eine Möglichkeit Videos einzubinden
und stellt uns einige Controls (Play, Stop, Lautstärke) zur Verfügung um dieses zu steuern.

Wir möchten nun jedoch einen eigenen Videoplayer auf Basis des `video` Tags erstellen. Unser Player soll mit
eigens erstellten HTML Elementen (Buttons, Dropdowns, Links) das Video Tag kontrollieren.

## Ressourcen ##

- [Video Tag](https://www.w3schools.com/tags/tag_video.asp)
- [Javascript Properties/Methoden/Events](https://www.w3schools.com/tags/ref_av_dom.asp)
- [Demo Video](https://github.com/Andi-Moser/SJ20-21-M152/raw/master/m152/Uebungen/Unterlagen/Video.mp4)

## Anforderungen ##

- Einbinden eines Videos mit dem `video` Tag
- Erstellen von folgenden Steuerelementen:
    - Play/Pause Button (soll sich dem Status anpassen)
    - Lautstärke höher/leiser
    - Wiedergabegeschwindigkeit (von 0.5x - 2x)
    - Video wiederholen (`loop` Property, Checkbox oder anderer Toggle)
    
### Bonusaufgabe ###

Auch wenn wir beim `video` Tag die Controls ausblenden hat der Benutzer dennoch Möglichkeiten das Video zu steuern -
z.B. über eine Play/Pause Taste auf der Tastatur oder ein Lautstärkeregler.

Reagieren Sie per Javascript nun wenn dies geschieht (Sprich: Eventhandling) und passen Sie das Interface entsprechend an.