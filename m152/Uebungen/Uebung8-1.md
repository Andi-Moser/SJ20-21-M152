# Übung 8.1 #

## Komponenten ##

Bisher haben wir all unseren Code in einem File `App.vue` untergebracht.
Bei kleineren Applikationen stellt dies kein grösseres Problem dar, aber ab einem gewissen Punkt wird
der Code zu unübersichtlich.

Vue basiert daher auf Komponenten. Jede Komponente ist ein eigener Baustein einer Applikation welcher
unabhängig von den anderen lebt und funktioniert. Somit kann die Logik in kleinere Elemente aufgeteilt
werden und Komponenten können an unterschiedlichen Orten wiederverwendet werden.

Jedes `.vue` File ist eine eigene Komponente. Auch die Datei `App.vue` ist nichts anders als eine Komponente,
sie stellt einfach den zentralen Einstiegspunkt in die Applikation dar.

Eine Komponente definiert sich durch folgende Elemente:

- Template, Script und Style Angaben
- Eigenes `data` Object
- `props` - Properties welche beim Einbinden der Komponente gesetzt werden können
- `events` - Damit Komponenten informationen an ihre Parent-Komponente senden können, werden Events verwendet

## Aufbau einer Komponente ##

Wie gesagt ist eine Komponente ein eigenes `.vue` File.

Eine Beispielkomponente für eine ToDo Applikation würde z.B. so aussehen:

```vue
<template>
  <div>
    <ul>
      <li v-for="todo in todos">{{ todo }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'ToDos',
  props: {
    todos: Array
  },
  data: function() {
    return {}
  },
  methods: {

  },
  computed: {

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
```

Diese Komponente würde man dann in der `App.vue` wie folgt einbauen:

```vue
<template>
    <div class="main">
        <h1>{{ itemCount }} Einträge</h1>

        <ToDos :todos="tasks" />

        <input type="text" placeholder="Neues Item hinzufügen" v-model="newItem" />
        <input type="submit" value="Hinzufügen" @click="addItem(newItem)" />
    </div>
</template>

<script>
    import ToDos from './components/ToDos'

    export default {
        components: {ToDos},
        data: function() {
            return {
                tasks: [
                    "Einkaufen",
                    "Rasen mähen",
                    "Katze füttern"
                ],
                newItem: 'Neues Element'
            }
        },
        methods: {
            addItem: function(item) {
                this.tasks.push(item);
                this.newItem = '';
            }
        },
        computed: {
            itemCount: function() {
                return this.tasks.length;
            }
        }
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

Wichtig sind hierbei folgende Punkte:

- Die Komponente muss mit `import ToDos from './components/ToDos'` geladen werden
- Man muss die Komponente noch registrieren: `components: {ToDos},`
- Die Tasks welche an die Komponente übergeben werden müssen mit `:todos='tasks'` angegeben werden

> Würde nur `todos='tasks'` angegeben, würde der String `tasks` übergeben werden. Mit dem `:` sagen wir Vue,
> dass es sich beim Ausdruck um eine dynamische Variable handelt und nicht um einen fixen Wert.

## Aufteilung in Komponenten ##

> Wir verwenden für diese Übung eine angepasste Version der Übung 7.3. Sie finden diese im Ordner "/Unterlagen/Uebung8-1" in diesem git Repository.

Wir möchten die Komponente nun wie folgt aufteilen:

- `App.vue` - Hauptkomponente, stellt die Daten bereit
- `Subject.vue` - Komponente welche ein Fach darstellt 
- `Summary.vue` - Komponente welche die Zusammenfassung am Schluss darstellt

Versuchen Sie nun die Vorlage so umzubauen dass diese drei Komponenten verwendet werden.

### Bonusaufgabe ###

Die Funktion `getAverage` wird bei mehreren Komponenten eingesetzt und kommt daher doppelt vor.

Versuchen Sie diese Funktion in ein eigenes File auszulagern und an den nötigen Stellen zu importieren.