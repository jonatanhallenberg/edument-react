---
marp: true
theme: gaia
_class: lead
paginate: true
backgroundColor: #fff
backgroundImage: url('https://marp.app/assets/hero-background.svg')
---

# Hooks + hämta och visa data

Jens Palmqvist

---

# Hooks i React

- Hooks är funktioner man kan använda för utökad funktionalitet i React
- Exempel på några hooks:
  - useState
  - useEffect
  - useMemo
  - useContext

---

# Hämta och visa data

- Vi kommer nu titta närmare på _useState_ och _useEffect_ som vi behöver för att kunna hämta och visa data.
- För att hämta data använder vi funktionen _fetch_ som finns inbyggd i webbläsaren

```jsx
const response = await fetch("https://www.api.com/data");
const data = await response.json();
console.log(data);
```

---

# useState

- När vi väl har hämtat datan vill vi visa den i vår komponent
- Med hjälp av _useState_ kan vi skapa en variabel som vi kan använda för att visa datan

```jsx
const [count, setCount] = useState(0);
```

- **count** är variabeln som vi kan använda för att visa datan
- **setCount** är funktionen vi använder för att uppdatera datan
- **0** är värdet som count får från början

---

# useEffect

- Kod i en komponent körs varje gång komponenten renderas vilket sker när vi uppdaterar statet
- För att förhindra en oändlig loop av api-anrop måste vi lägga fetch-koden i useEffect

```jsx
useEffect(() => {
  const fetchData = async () => {
    const response = await fetch("https://www.api.com/data");
    const data = await response.json();
    setCount(data.count);
  };
  fetchData();
}, []);
```

---

# useEffect - Dependency array

```jsx
useEffect(() => {
  //kod som körs när komponenten renderas
, []);
```

- useEffect tar emot en funktion med kod
- Den har även en _dependency array_ som tar emot variabler
- Koden i funktionen körs varje gång en variabel i _dependency array_ uppdateras
- Om arrayen är tom körs koden endast när komponenten renderas första gången

---

# Komplett exempel ladda och visa data

```jsx
import React, { useState, useEffect } from "react";

const App = () => {
  const [data, setData] = useState(0);

  useEffect(() => {
    const fetchData = async () => {
      const response = await fetch("https://www.api.com/data");
      const data = await response.json();
      setData(data);
    };
    fetchData();
  }, []);

  return (
    <div>
      <p>{data}</p>
    </div>
  );
};
```

---

# Övning: Kattfakta

- Genom att anropa 'https://catfact.ninja/fact' får vi tillbaka en slumpmässig kattfakta i json-format
- Skriv en react-komponent som hämtar en kattfakta och visar den på sidan

**Tänk på att:** beroende på om api:et svarar med ett object {} eller en array [] så måste du hantera datan olika i din komponent

```jsx
const [data, setData] = useState({});
```

```jsx
const [data, setData] = useState([]);
```

---

# Facit: Kattfakta

```jsx
import React, { useState, useEffect } from "react";

const App = () => {
  const [data, setData] = useState({});

  useEffect(() => {
    const fetchData = async () => {
      const response = await fetch("https://catfact.ninja/fact");
      const data = await response.json();
      setData(data);
    };
    fetchData();
  }, []);

  return (
    <div>
      <p>{data.fact || ""}</p>
    </div>
  );
};
```
