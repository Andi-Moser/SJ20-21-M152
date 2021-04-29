# Übung 7.1 #

## VueJS ##

### Neues Projekt erstellen ###

In dieser Übung erstellen Sie ein VueJS Grundgerüst.

1. Als Erstes muss das `vue-cli` Tool installiert werden. Dieses hilft bei der Erstellung von weiteren Vue Projekten.

    Installieren Sie `vue-cli` mit folgendem Befehl:
    
    ```shell script
    npm install -g @vue/cli
    ```
   
1. Nun können Sie das erste Projekt erstellen:

    ```shell script
    vue create demo-vue
    ```
   
1. Im Installationsassistenten wählen Sie folgende Optionen:

    - Manually select features
    - Aktivieren Sie folgende Checkboxen: (wählen Sie nur diese Checkboxen aus!)
        - Choose Vue Version
        - Router
        - Vuex
        - CSS Pre-processors
    - Wählen Sie die Version 3.x (Preview)
    - Bestätigen Sie die nächste Frage nach dem History Mode
    - Wählen Sie einen CSS Pre-processor aus (Empfehlung: dart-sass)
    - Wählen Sie aus dass die Konfigurationen in dedicated config files gespeichert werden soll
    - Die Konfiguration können Sie als Template speichern, wenn Sie möchten.
    
1. Wechseln Sie in das erstellte Verzeichnis (`cd demo-vue`) und starten Sie den Development Server (`npm run serve`)

1. Öffnen Sie die angezeigte URL in einem Browser (`http://localhost:8080/`)

1. Wenn die 'Welcome to Your Vue.js App' Seite angezeigt wird, ist alles richtig installiert.

> Diese Übung erfordert keine Abgabe. Erstellen Sie das Grundgerüst für die weiteren Übungen jeweils nach diesem Schema
> (Sie können auch bestehende Übungsordner kopieren).