---
marp: true
theme: gaia
_class: lead
paginate: true
backgroundColor: #fff
backgroundImage: url('https://marp.app/assets/hero-background.svg')
---

# CSS i React

Jens Palmqvist

---

# Intro

- Det finns olika sätt att använda sig av CSS i React
- Vi ska gå igenom:
  - Global CSS
  - Inline Styling
  - CSS modules
  - Styled Components

---

# Global CSS

- Precis som att länka in en CSS fil i en HTML-sida
- En CSS-class som finns här kan användas var som helst på sidan

```tsx
import "./App.css";
```

---

# Scoped styling

- I React vill man undvika global styling
- Istället ska varje komponent ha sin egen lokala CSS som är oberoende av andra komponenters CSS
- Detta kallas **scoped styling** och kan åstadkommas på flera sätt

---

# Inline Styling

- Style attributet används och sätts till ett javascript-objekt
- Objektet har attribut som motsvarar CSS-attribut
- Attributen måste skrivas i camelCase så t.ex. background-color blir backgroundColor
- Attributvärdena måste oftast skrivas som strängar

---

# Inline styling - exempel

```tsx
const ButtonStyle = {
  backgroundColor: "#333333",
  borderRadius: "3px",
  padding: "5px 10px",
  color: "white",
};
```

```html
<button style="{ButtonStyle}">En stylad knapp!</button>
```

---

# Övning - Inline Styling

- Skapa en React-komponent som är en textruta (input) med följande styling:

```css
input {
  font-size: 18px;
  line-height: 20px;
  border: 1px solid gray;
  border-radius: 3px;
}
```

---

# CSS Modules

- CSS Modules är ett annat sätt att ha _scoped styling_
- En fil för CSS-moduler har filändelsen _.module.css_
- I den filen skriver man helt vanliga CSS-klasser
- Genom att importera filen i komponenten får man tillgång till CSS-klasserna och kan applicera på olika element via className

---

# CSS Modules - exempel

```css
/*button.module.css*/
.button {
  background-color: #333333;
  border-radius: 3px;
  padding: 5px 10px;
  color: white;
}
```

```tsx
import styles from "./button.module.css";
const ButtonCSSModule = () => (
  <button className={styles.button} type="button">
    Klicka här
  </button>
);
export default ButtonCSSModule;
```

---

# Övning - CSS Modules

- Skapa en React-komponent som är en textruta (input) med följande styling:

```css
input {
  font-size: 18px;
  line-height: 20px;
  border: 1px solid gray;
  border-radius: 3px;
}
```

---

# Styled components

- Styled components är ett mycket populärt npm-paket för att hantera CSS i React
- Det utgår ifrån CSS-in-JS som är en styling-teknik flera fördelar, bland annat:
  - Komponenttänk
  - JavaScript-logik
  - Helt isolerad CSS (påverkar bara den egna komponenten)

https://en.wikipedia.org/wiki/CSS-in-JS

---

# Hur funkar styled components?

- För att skapa en styled components kombinerar man ihop ett html-element och en sträng med CSS
- Strängen är en template string vilket innebär att man kan lägga in JS-kod i strängen

_En röd knapp:_

```tsx
const MyStyledButton = button.styled`
    background-color: red;
`;
```

---

# Installera Styled Components

- Innan vi använder Styled components måste vi installera npm-paketet:

```sh
npm install styled-components
npm install --save-dev @types/styled-components
```

- Och importera i komponenten:

```ts
import styled from "styled-components";
```

---

# VSCode syntax highlightning

- Plugin som heter _vscode-styled-components_
- Highlightar CSS-koden i strängen

---

# Styled components - exempel

```tsx
import styled from "styled-components";

const StyledButton = styled.button`
  background-color: #333333;
  border-radius: 3px;
  padding: 5px 10px;
  color: white;
`;

const ButtonStyledComponents = () => (
  <StyledButton type="button">Klicka här</StyledButton>
);

export default ButtonStyledComponents;
```

---

# Övning - Styled components

- Skapa en React-komponent som är en textruta (input) med följande styling:

```css
input {
  font-size: 18px;
  line-height: 20px;
  border: 1px solid gray;
  border-radius: 3px;
}
```

---

# Styled components - med props

- Man kan skicka med props till en styled component och variera css-koden beroende på vad som står i proppens värde:

```tsx
const StyledButton = styled.button`
  background-color: ${(props) => props.color};
  border-radius: 3px;
  padding: 5px 10px;
  color: white;
`;
```

```tsx
<StyledButton type="button" color="red">
  Klicka här!
</StyledButton>
```

---

# Övning - Styled Components m. props

- Skapa en textbox-komponent som tar emot en prop som heter isValid
- Om isValid=true ska bakgrundsfärger vara vit
- Om isValid=false ska bakgrundsfärgen vara ljusröd

```tsx
//Exempel på implementation
<Textbox isValid={false} />
```

---

# Styled components - Child-selektor

- För att kunna använda childselektorer använder man & när man refererar till det egna elementet

```tsx
// Alla ul som ligger i listan MyStyledList får röd textfärg
const MyStyledList = styled.ul`
  & > li {
    color: red;
  }
`;
```

---

# Styled components - Pseudoklasser

- & används också för att kunna applicera pseudoklasser till det egna elementet

```tsx
const MyStyledButton = styled.button`
  &:hover {
    background-color: red;
  }
`;
```
