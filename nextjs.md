---
marp: true
theme: gaia
_class: lead
paginate: true
backgroundColor: #fff
backgroundImage: url('https://marp.app/assets/hero-background.svg')
---

# Next.js

Jens Palmqvist

---

# Vad är Next.js

- Next.js är ett ramverk för React
- Med next kan vi enkelt få upp grunden för ett React-projekt
- Hemsidor och webbapplikationer

---

# Komma igång

- För att skapa ett nytt projekt (med namnet _my-app_):

```sh
npx create-next-app my-app
```

- Gå sedan in i projektmappen

```sh
cd my-app
```

- Starta utvecklingsmiljön

```sh
npm run dev
```

---

# Kommandon

```sh
npm run dev # Startar utvecklingsmiljön

npm run build # Skapar produktionsfiler i mappen dist

npm run start # Startar produktionsmiljön

npm run test # Kör eventuella tester
```

---

# Mappstruktur

- pages (komponenter som används för att skapa sidor)
  - index.js (startsidan)
  - \_app.js (huvudkomponenten för hela applikationen)
  - \_document.js (huvudkomponenten för hela HTML-dokumentet)
- public (statiska filer)
  - bilder, favicon osv.
- styles (globala stilmallar)
  - global.css
- components (återanvändbara komponenter)
  - Header.js
  - Footer.js

---

# Routing i Next

- Next har inbyggd routing
- Varje fil i pages-mappen blir en sida
- Om vi skapar en fil som heter _about.js_ i pages-mappen kommer den att vara tillgänglig på adressen _/about_
- Om vi skapar en fil som heter _about/index.js_ i pages-mappen kommer den att vara tillgänglig på adressen _/about_

---

# Dynamisk routing

- Om vi vill skapa en dynamisk sida kan vi skapa en fil som heter _\[id\].js_ i pages-mappen
- För att hämta id:t i komponenten använder vi **useRouter**

```js
import { useRouter } from "next/router";
const Post = () => {
  const router = useRouter();
  const { id } = router.query;

  return <p>Post: {id}</p>;
};

export default Post;
```

---

# Övning - kom igång med Next.js

- Skapa ett nytt Next.js-projekt
- Skapa en sida som heter _about_
- Starta appen och navigera till sidan i webbläsaren

---

# Övning, dynamisk id

- Denna övning är lite svårare
- Skapa en dynamisk sida som heter _posts_ och som tar emot ett id som parameter -> visa upp id:t på sidan
- Du ska nu kunna navigera till http://localhost:3000/posts/1 och http://localhost:3000/posts/2 och se olika id:n på sidorna
