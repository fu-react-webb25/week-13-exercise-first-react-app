# Vecka 13: My First React App

I den här övningen är tanken att du skall få en steg-för-steg-guide i hur du går till väga för att skapa upp ditt första React-projekt, samt använda några av de mest grundläggande teknikerna och tankesätten.

Tills detta sitter i autopiloten kan du använda vissa av stegen i denna övning som en lathund när du skapar nya React-appar under kommande veckor.

---

## Steg 1: Installera Node.js

För att kunna skapa React-appar behöver vi först installera **Node.js**. Node innehåller även **npm (Node Package Manager)** som vi använder för att installera paket och utvecklingsverktyg.

Ladda ner Node här:

https://nodejs.org

Klicka på **Download Node.js (LTS)**.  
LTS står för *Long Term Support* och är den stabila version som rekommenderas för utveckling.

När installationsfilen laddats ner öppnar du den och klickar dig igenom installationen utan att ändra några inställningar.

När installationen är klar kan du kontrollera att allt fungerar genom att öppna en terminal och köra:

```
node -v
```

Du bör nu se ett versionsnummer.

---

## Steg 2: Kontrollera npm

När Node installeras följer **npm** automatiskt med.

Kontrollera att npm fungerar genom att köra:

```
npm -v
```

Du bör få upp ett versionsnummer.

Om du inte får upp något versionsnummer kan något ha gått fel och du kan behöva installera Node igen.

---

## Steg 3: Skapa din React-app

Nu är det dags att skapa ditt första React-projekt.

Öppna en terminal i den mapp på din dator där du vill skapa ditt projekt.

Kör kommandot:

```
npm create vite@latest
```

Du kommer nu få svara på några frågor.

Exempel:

```
OK to proceed? (y): y
Project name: my-first-react-app
Select a framework: React
Select a variant: JavaScript
Install with npm and start now: Yes
```

Detta kommer omedelbart starta upp din utvecklingsserver, men först vill du göra lite andra saker. Stäng därför din utvecklingsserver genom att trycka ```Ctrl + c``` i terminalen.

När projektet skapats kör du följande kommandon i terminalen:

```
cd my-first-react-app
npm install
code .
npm run dev
```

`npm run dev` startar din utvecklingsserver.

När servern startar visas en adress i terminalen, oftast:

```
http://localhost:5173
```

Öppna adressen i din webbläsare.

Från och med nu använder vi **Vites utvecklingsserver** istället för **Go Live** i VS Code eftersom den inte fungerar för React-applikationer.

---

## Steg 4: Rensa din React-app

När man startar nya projekt är det bra att ta bort kod man inte kommer använda.

Gör följande:

1. Ta bort alla filer i mappen **public**
2. Ta bort alla filer i **assets**
3. Ta bort filen **App.css**
4. Töm filen **index.css**
5. Ta bort all kod i **App.jsx**

Ersätt innehållet i `App.jsx` med följande kod:

```jsx
function App() {

  return (
    <div className="app">Hello React</div>
  )
}

export default App;
```

Spara filen och kontrollera att texten visas i webbläsaren.

Om du ser texten fungerar din React-app. Testa att byta text, spara och se om ändringen visas.

---

## Steg 5: Skapa din första komponent

1. Skapa nu en ny mapp i src som heter `components`.
2. Skapa sedan filen `FavoriteList.jsx` i `components-mappen`.
3. Klistra in följande kod i filen:

```
function FavoriteList() {

  return (
    <div>
      <h2>Min favoritlista</h2>
      <ul></ul>
    </div>
  )
}

export default FavoriteList;
```

3. Importera din nya komponent längst upp i `App.jsx`:

```
import FavoriteList from './components/FavoriteList'
```

4. Rendera komponenten:

```
function App() {

  return (
    <div className="app">
      <FavoriteList />
    </div>
  )
}

export default App;
```

5. Kontrollera i webbläsaren att komponenten visas.

---

## Steg 6: Listor i React

1. Lägg till följande kod i FavoriteList:

```
const favorites = ['fotboll', 'tv-spel', 'golf', 'film', 'mat']
```

2. Rendera ut varje favorit i listan med .map():

```
<ul>
  {favorites.map((fav, index) => (
    <li key={index}>{fav}</li>
  ))}
</ul>
```

3. Kontrollera att listan visas i webbläsaren.

React kräver att varje element i en lista har en key.
Den hjälper React att förstå vilka element som förändras när sidan uppdateras.

---

## Steg 7: Conditional Rendering

1. Ersätt din tidigare array med:

```
const favs = [
  { name: 'fotboll', isCool: false },
  { name: 'tv-spel', isCool: true },
  { name: 'golf', isCool: true },
  { name: 'film', isCool: false },
  { name: 'mat', isCool: true }
];
```

2. Rendera nu listan igen:

```
<ul>
  {favs.map((fav, index) => (
    <li key={index}>
      Det är {fav.isCool ? '' : 'inte'} coolt med {fav.name}
    </li>
  ))}
</ul>
```

Här använder vi en ternary operator.

Syntaxen ser ut så här:

```
villkor ? omSant : omFalskt
```

Det fungerar ungefär som en kortare version av en if-else-sats.

---

## Steg 8: Props

Nu ska vi förbättra strukturen i vår kod.

Istället för att skapa varje <li> direkt i FavoriteList, ska vi skapa en ny komponent.

1. Skapa filen `FavoriteItem.jsx`

2. Skapa komponenten:

```
function FavoriteItem({ fav }) {

  return (
    <li>
      Det är {fav.isCool ? '' : 'inte'} coolt med {fav.name}
    </li>
  )
}

export default FavoriteItem;
```

3. Importera din nya komponent längst upp i `FavoriteList.jsx`

```
import FavoriteItem from './FavoriteItem'
```

4. Rendera den så här:

```
<ul>
  {favs.map((fav, index) => (
    <FavoriteItem key={index} fav={fav} />
  ))}
</ul>
```

Nu skickar vi data från en komponent till en annan med hjälp av props.

Detta är ett av de allra viktigaste koncepten i React.

## Klart!

Du har nu lärt dig att:
* skapa en React-app
* arbeta med komponenter
* använda JSX
* rendera listor
* använda conditional rendering
* skicka data mellan komponenter med props

Dessa koncept är grunden i nästan alla React-applikationer.
