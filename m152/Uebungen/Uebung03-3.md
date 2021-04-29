# Übung 3.3 #

## Transformations / Transitions ##

### Transition ###

Transitions sind dazu da, den Übergang zwischen zwei Stati (z.B. Hintergrundfarbe) anzupassen.

Bei einer Transition muss immer angegeben werden auf welches Property sie sich bezieht:

`transition: background-color 2s;`

Wird dem Element nun eine andere Hintergrundfarbe gegeben, wird diese über 2 Sekunden langsam geändert.

> Meistens wird dies beim Hover Status (`:hover`) geändert.

[Mehr zu Transitions hier](https://www.w3schools.com/cssref/css3_pr_transition.asp)

### Transformation ###

Eine Transformation verändert die Box welche ein Element belegt.

[Mehr zu Transformations hier](https://www.w3schools.com/cssref/css3_pr_transform.asp)

## Aufgabe ##

Wir erweitern wieder die Personenblöcke aus der Übung 3.1. Ihr Chef möchte gerne einen Effekt wenn ein Benutzer
über eine Person hovert:

- Die Box sollte leicht grösser werden
- Der Button sollte sich in ein dunkleres Grün verfärben

> Hinweis: In SCSS können Sie Regeln für den Hover Status mit `&:hover {}` hinzufügen:
> 
> ```scss
> .person {
>    &:hover {
> 
>    }
> }
> ```