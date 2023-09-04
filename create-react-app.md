---
marp: true
theme: gaia
_class: lead
paginate: true
backgroundColor: #fff
backgroundImage: url('https://marp.app/assets/hero-background.svg')
---

![bg left:40% 80%](../../Customization/iths-logo.png)

# Create React App

Jens Palmqvist

---

# Vad är Create React App?

- För att starta ett nytt Reactprojekt använder vi *Create React App*
- Innehåller en massa trevliga saker vi vill ha:
  - Babel för transpilering
  - Utvecklingsmiljö med Hot reload
  - Script för att skapa produktionsfiler

---

# Komma igång

- För att skapa ett nytt projekt (med namnet *my-app*):

```sh
npx create-react-app my-app
```

- Gå sedan in i projektmappen

```sh
cd my-app
```
---

# Kommandon

```sh
npm start # Startar utvecklingsmiljön

npm run build # Skapar produktionsfiler i mappen dist

npm test # Kör eventuella tester

npm run eject # Skapar en lokal kopia av alla byggscript - rekommenderas ej!
```

---

# Mappstruktur

- public (statiska filer)
  - index.html (filen som skickas till webbläsaren)
  - bilder, favicon osv.
- src (här ligger koden)
  - index.jsx
    - Kör igång appen och renderar i root-elementet i index.html
  - App.jsx
    - Appens root-komponent

---

# Vi lägger in lite kod

- Vi tar bort exempelkoden i App.jsx
- Lägger istället in några av våra komponenter vi gjort tidigare

---

# Övning - kom igång med Create React App (CRA)

- Skapa din egen React-app med CRA
- Skapa en katalog som heter src/components
- Skapa en fil för komponenterna *OrderConfirmation*, *OrderConfirmationText* och *Title* som du skapade tidigare i en html-fil
- Kopiera in komponentkoden och exportera som default

---

# Övning, forts.

- Skriv om komponenten i App.jsx till en arrow-funktion som returnerar en React Fragment <></>
- Lägg in ett h1-element där det står Mina komponenter i
- Under H1:an länka in dina komponenter från *components*-mappen med dess taggar (glöm inte att importera från deras respektive filer)
- Här kan du sedan länka in komponenter som du bygger i senare övningar
- Kör **npm start** för att testa

---