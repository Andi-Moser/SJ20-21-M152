# Übung 7.2 #


## Erste Applikation ##

Der Einstiegspunkt der Vue Applikation ist die Datei `/src/App.vue`. Dies ist die Start-Komponente welche als erstes angezeigt wird.

### Komponenten ###

Eine Vue Applikation ist in mehrere Komponenten unterteilt. Eine Komponente enthält jeweils folgende drei Parts:

- Template: Das HTML Template welches im Browser gerendert wird
- Script: Der Javascript Code zur Komponente
- Style: Die CSS Angaben für diese Komponente

Kopieren Sie als Erstes diesen Code in die Datei `/src/App.vue`:

```vue
<template>
    <div class="main">
        <h1>Hello World</h1>

        <ul class="todos">
            <li>Einkaufen</li>
            <li>Rasen mähen</li>
            <li>Katze füttern</li>
        </ul>

        <input type="text" placeholder="Neues Item hinzufügen"/>
        <input type="submit" value="Hinzufügen"/>
    </div>
</template>

<script>
    export default {
        
    }
</script>

<style lang="scss">
    .main {
        max-width: 500px;
        margin: 0 auto;
        background-color: #eee;
        padding: 20px;

        h1 {
            text-align: center;
        }
    }
</style>
```

> Hinweis: Sie müssen den Browser nach den Änderungen nicht neu laden - Der Webpack Dev Server übernimmt dies für Sie!

### Script ###

Der `<script>` Teil jeder Vue Komponente ist beinahe das Wichtigste - dort ist alle Logik untergebracht. 
Wir möchten nun die Logik (neues ToDo hinzufügen) und die Daten (Einträge der Liste) in den Script Part übernehmen.

Fügen Sie dort nun diesen Code ein:

```javascript
export default {
    data: function() {
        return {
            tasks: [
                "Einkaufen",
                "Rasen mähen",
                "Katze füttern"
            ]
        }
    },
    methods: {
        addItem: function(item) {
            this.tasks.push(item);
        }
    }
}
```

Das Script exportiert ein JS-Objekt, in unserem Falle mit zwei Properties:

- `data`: Dies ist eine Funktion welche wiederrum alle Daten welche der View (dem Template Part) zur Verfügung stehen.
- `methods`: Hier lassen sich Methoden definieren, welche wir für diese Komponente zur Verfügung stellen möchten.
    - In diesem Fall haben wir eine Methode definiert, welche der Task-Liste ein weiteres Item hinzufügt.

### Template ###

Nun möchten wir diese Daten und die eine Methode nutzen um effektiv die "Magie" von Vue zu sehen.

Ersetzen Sie also den Template Part durch folgenden Code:

```html
<div class="main">
    <h1>Hello World</h1>

    <ul class="todos">
        <li v-for="item in tasks">{{ item }}</li>
    </ul>

    <input type="text" placeholder="Neues Item hinzufügen" v-model="newItem" />
    <input type="submit" value="Hinzufügen" v-on:click="addItem(newItem)" />
</div>
```

Wie Sie sehen haben wir hier das HTML mit Vue Spezifischen Elementen erweitert:

- `v-for="item in tasks"`: Dieses Attribut erzeugt eine for-Schlaufe und gibt das HTML Element entsprechend aus
- `{{ item }}`: Dieser Platzhalter wird verwendet um Inhalte dynamisch ins HTML zu rendern
    - Achtung: Die `{{ }}` Schreibweise darf nie innerhalb eines Tags (Attribut) vorkommen!
- `v-model="newItem"`: Felder welche vom Benutzer bearbeitet werden können mit einem `v-model` versehen werden. Der Inhalt der Felder wird durch Vue automatisch immer synchron gehalten.
- `v-on:click="addItem(newItem)"`: Hier wird ein Event Handler für den Click Event erstellt. Darin wird die (im Script definierte) Methode `addItem` aufgerufen.

### Computed ###

Ein wichtiges Merkmal von Vue ist die sog. Reaktivität (reactivity).

Anstelle dass zu Beginn der Applikation gewisse Werte fix berechnet werden (z.B. die Anzahl der ToDos),
wird definiert wie die Anzahl ToDos berechnet wird. Vue übernimmt dann das automatische Aktualisieren dieses Wertes.

Sie können es sich in etwa wie im Excel vorstellen. Wenn in einer Zelle eine Formel eingegeben wird, stellt Excel sicher, dass
diese immer aktuell ist.

Solche "Formeln" heissen bei Vue `computed-properties`. Fügen Sie folgenden Code im Script Part analog zu `data` und `methods` ein:

```javascript
computed: {
    itemCount: function() {
        return this.tasks.length;
    }
}
```

Geben Sie nun im Template an passender Stelle die Anzahl Tasks mit `{{ itemCount }}` aus!