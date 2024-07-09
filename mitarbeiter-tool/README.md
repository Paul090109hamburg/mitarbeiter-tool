# mitarbeiter-tool

Wir benutzen im Projekt HTML, CSS, JavaScript (auch JS genannt) und TypeScript. Außerdem das Framework Vue.js. 

Als erstes brauchtst du NodeJS. Hier der Link zum Download [https://nodejs.org](https://nodejs.org). NodeJS ist die Programmiersprache JavaScript wenn sie außerhalb vom Web-Browser verwendet wird.  

Um den Code zu bearbeiten, brauchst du einen Editor. Du kannst kostenlos Visual Studio Code von Mircosoft verwenden. Hier der Link zum download: [https://code.visualstudio.com/](https://code.visualstudio.com/)

Um das Projekt zu starten, öffne das Terminal ("Eingabeaufforderung") und gehen in deinen Projektordner. Das kannst Du mit dem Befehl `cd ordnername` bzw. `cd ..` machen.

Im Projektodner musst du als erstes deine Projektabhängigkeiten installieren. Tippe dazu `npm i` ein. Das kann kurz dauern.

Tippe dann `npm run dev`. Nach kurzer Zeit bekommst du eine URL angezeigt. Meist das Word "localhost" und eine Zahl wie z.B. `localhost:3000`. Kopiere diese URL in den Webbrowser und du siehst deine Seite. 






## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).

## Type Support for `.vue` Imports in TS

TypeScript cannot handle type information for `.vue` imports by default, so we replace the `tsc` CLI with `vue-tsc` for type checking. In editors, we need [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) to make the TypeScript language service aware of `.vue` types.

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Type-Check, Compile and Minify for Production

```sh
npm run build
```
