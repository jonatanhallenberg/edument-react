---
marp: true
theme: gaia
_class: lead
paginate: true
backgroundColor: #fff
backgroundImage: url('https://marp.app/assets/hero-background.svg')
---

# Enhetstesta komponenter

Jens Palmqvist

---

# Ramverk för enhetstestning

- Det finns flera ramverk för enhetstestning av React-komponenter
- Vi kommer testa React Testing Library

---

# Kom igång

- Installera React Testing Library i din befintliga React-app

```sh
npm install --save-dev @testing-library/react
```

- För att köra tester:

```sh
npm test
```

---

# Ett första test

- Skapa en ny fil i mappen `src` som heter `App.test.js`
- Skriv följande kod i filen:

```js
import { render, screen } from "@testing-library/react";
import App from "./App";

test("renders learn react link", () => {
  render(<App />);
  const linkElement = screen.getByText(/learn react/i);
  expect(linkElement).toBeInTheDocument();
});
```

---

# Snapshot-testning

- Snapshot-testning är ett sätt att testa att en komponent renderas på ett visst sätt
- Om komponenten ändras på ett sätt som inte är avsett kommer testet att misslyckas

---

# Snapshot, exempel:

```js
import React from "react";
import renderer from "react-test-renderer";
import App from "./App";

test("renders correctly", () => {
  const tree = renderer.create(<App />).toJSON();
  expect(tree).toMatchSnapshot();
});
```

---

# Övning

- Skapa en komponent som visar upp en text
- Skapa ett snapshot-test för komponenten
- Ändra komponenten så att testet misslyckas
- Uppdatera snapshotet
