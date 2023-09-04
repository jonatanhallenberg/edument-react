---
marp: true
theme: gaia
_class: lead
paginate: true
backgroundColor: #fff
backgroundImage: url('https://marp.app/assets/hero-background.svg')
---

![bg left:40% 80%](../../Customization/iths-logo.png)

# React Router

Jonatan Hallenberg

---

## Intro

- Med React bygger vi en Single Page Application
- Det innebär att HTML-sidan inte laddas om varje gång vi byter adress i webbläsaren
- Istället används JavaScript och React för att rendera nytt innehåll när vi går till en ny webbadress (URL)
- För att fånga upp när vi byter URL och visa upp nytt innehåll använder vi *React Router*

---

## Installera React Router

```tsx
npm install react-router-dom
```

---

## BrowserRouter i index.js

```diff
import App from './App';
+import { BrowserRouter } from "react-router-dom";

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <React.StrictMode>
+   <BrowserRouter>
      <App />
+    </BrowserRouter>
  </React.StrictMode>
);
```

---

## Skapa en Home-komponent

```jsx
//Home.jsx

const Home = () => (
    <>
        <h2>Home</h2>
        <p>Välkommen till vår sida!</p>
    </>
)
export default Home;
```

---

## Skapa en About-komponent

```jsx
//About.jsx

const About = () => (
    <>
        <h2>Om oss</h2>
        <p>Vi är ett härligt gäng :)</p>
    </>
)
export default About;
```

---

# Lägga in router i App.js

```jsx
import { Routes, Route, NavLink } from "react-router-dom";
import Home from './Home';
import About from './About';

const App = () => (
  <div>
    <h1>Min sida med routes</h1>
    <Routes>
      <Route path="/" element={<Home />} />
      <Route path="about" element={<About />} />
    </Routes>
  </div>
)

export default App;

```

---

# Testa

- Gå in på http://localhost:3000/
- Gå in på http://localhost:3000/about

---

# Länka mellan sidor

- Vi använder <NavLink> istället för vanlig ```<a/>``` när vi länkar mellan olika sidor

```diff
//Home.jsx
+import { NavLink } from 'react-router-dom';

const Home = () => (
    <>
        <h2>Home</h2>
        <p>Välkommen till vår sida!</p>
+        <NavLink to="/about">Om oss</Link>
    </>
)
export default Home;
```

---

## Flytta meny

- Flytta länkarna så att de ligger direkt i App.js - det blir som en meny för sidan:

```diff
import { Routes, Route, NavLink } from "react-router-dom";
import Home from './Home';
import About from './About';

const App = () => (
  <div>
    <h1>Min sida med routes</h1>
+    <h2>Meny</h2>
+    <ul>
+       <li><NavLink to="/">Hem</NavLink>
+       <li><NavLink to="/about">Om oss</NavLink> 
+    </ul>
    <Routes>
      <Route path="/" element={<Home />} />
      <Route path="about" element={<About />} />
    </Routes>
  </div>
)

export default App;

```

---

## Markera länk för den sida man är på

- Ofta vill man på något sätt markera länken för den sida man är på
- Vi skapar en App.module.css och skapar två klasser, en för länken på den sida man är på och en för de sidor man inte är på:

```css
/* App.module.css */
.activeLink {
    color: red;
    font-weight: bold;
    text-decoration: underline;
}

.inactiveLink {
    color: blue;
    text-decoration: none;
}
```

---

## Länka in CSS och välja rätt klass

- Nu länkar vi in css-filen i App.js och väljer rätt klass beroende på om vi är på länkens sida eller inte:

```js
//App.js

import styles from './App.module.css';

...

<NavLink to="/" className={({isActive}) => isActive ? styles.activeLink : styles.inactiveLink}>Hem</NavLink>

...

<NavLink to="/about" className={({isActive}) => isActive ? styles.activeLink : styles.inactiveLink}>Om oss</NavLink>

```

---

## Hämta parametrar från url

- Vi kan använda parametrar i en url
- Lägg till en route som hämtar olika katter

```js

<Route path="cat/:catName" element={<Cats />} />

```

--- 

## Hämta parameter i komponent

- Vi skapar komponenten <Cats />
- Parametern från url:en (:catName) hämtar vi med hjälp av hooken useParams


```js
import { useParams } from 'react-router';
const Cats = () => {
    const { catName } = useParams();
    return <p>En katt som heter <b>{catName}</b></p>
}
export default Cats;
```

---

## Länkar till olika katter i menyn

- Lägg till länkar till olika katter i App.js:

```jsx
<li>
    <NavLink to="/cat/Bosse" className={({isActive}) => isActive ? styles.activeLink : styles.inactiveLink}>Bosse</NavLink>
</li>
<li>
    <NavLink to="/cat/Misse" className={({isActive}) => isActive ? styles.activeLink : styles.inactiveLink}>Misse</NavLink>
</li>
<li>
    <NavLink to="/cat/Eva" className={({isActive}) => isActive ? styles.activeLink : styles.inactiveLink}>Eva</NavLink>
</li>
<li>
    <NavLink to="/cat/Hasse" className={({isActive}) => isActive ? styles.activeLink : styles.inactiveLink}>Hasse</NavLink>
</li>
```