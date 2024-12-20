# Discord-website-bot
Dieser Bot erlaubt die Synchronisation zwischen der Webseite von ifheroes.de und unserem Discord-Server

## Was kann dieser Bot?

> 1. Der Bot läuft mit Slash Commands, die nur von Leuten mit einer bestimmten Rolle ausgeführt werden können.
> 2. Beim Ausführen werden Titel, Text und Bild abgefragt und in eine JSON Datei geschrieben. Darauf wird ein Embed mit den angegeben Daten in den Channel gesendet, in dem man den Command ausgeführt hat. Weiteres: siehe Unten.

### Setup

> 1. Erstellung einer MongoDB Datenbank mit dem Namen `ifheroes`.
> 2. Die Datei `config.json.pub` muss in `config.json` umbenannt und ausgefüllt werden. Die Datei befindet sich in `src/data`. Die `ticket-setup.json` muss noch nicht bearbeitet werden, diese ist für die Zukunft gedacht.
> 3. Installation der node modules via `npm install`.
> 4. "Veröffentlichung der Commands":
>> 4.1 Dieser Schritt ist nötig, da es sich hierbei um Slash Commands handelt, die zuerst registriert und an den Server gebunden werden müssen.
>> 
>> 4.2 Möglich mit `npm run deploy` oder `node src/deploy-commands.js`.

> 5. Starten des Bots
>> 5.1 Gestartet wird der Bot entweder mit `node .`, `node src/index.js`, `npm start` oder `npm run start`.
>> 
>> 5.2 Sofern auf Linux, kann die `start.sh` Datei im Stammverzeichnis genutzt werden, welche den Bot in Dauerschleife laufen lässt. Sofern möglich, empfiehlt es sich hierfür screen zu nutzen. Beispiel: `screen -d -m -S discord-web-bot bash start.sh`

#### JSON-Informationen

Jede JSON-Datei existiert nur einmal, es kann keinen Dateinamen zwei mal geben, denn:
Der Dateiname besteht aus `Jahr-Monat-Tag_Stunde-Minute-Sekunde.json` (`YYYY-MM-DD_HH-mm-ss`), Bsp. `2024-12-16_17-27-12.json` (16.12.2024, 17:27:12 Uhr).

## Informationen zur Verwendung mit Docker

1. Zunächst muss das Repo von github heruntergeladen werden

2. Im gleichen file die dem Dockerfile muss nun die config.json abgelegt werden.
    
3. Aktuell muss noch ein Image erstellt werden mit dem Befehl:
````
docker build --pull --rm -f "Dockerfile" -t infinityheroesbot:latest "."
````
4. Nun kann das image mit ausgeführt werden mit
````
docker run -d -p 8080:8080 infinityheroesbot:latest 
````
