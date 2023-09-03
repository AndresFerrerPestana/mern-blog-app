# MERN BLOG APP

## How to install the project

### MERN stack Blog app using Tailwind CSS - 2 - setup project

- create a folder `mern-react-blog`
- Navigate to `mern-react-blog` folder and run this commands:

```powershell
npm create vite@latest frontend-blog -- --template react
```

Navigate to the `frontend-blog` folder

```powershell
cd frontend-blog
```

Inside the `frontend-blog` folder run this command, to install node packages:

```powershell
cd frontend-blog
npm install
```

```powershell
cd frontend-blog
code .
```

```powershell
npm run dev
```

## Cleanup structure folder and files

- Remove all the code in `App.css` and `index.css`
- Remove `reportWebVitals` file and all imports
- Remove `logo.svg` and all imports

## Tailwind css installation

In the next steps, please refer to `tailwindcss` page documentation

- https://tailwindcss.com/docs/installation

Install tailwindcss via npm, and create your `tailwind.config.js` file

```powershell
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```

Open `tailwind.config.js` and past this lines of code:

```js
/** @type {import('tailwindcss').Config} */
export default {
  content: ['./index.html', './src/**/*.{js,ts,jsx,tsx}'],
  theme: {
    extend: {},
  },
  plugins: [],
};
```

Open `index.css` file and remove everything, then past the source code:

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

Open `App.jsx` and remove all the imports. Remove the code in there between the `div` and past this code:

```html
<div
  className="w-screen h-screen bg-orange-200 background-color: rgb(226 232 240"
>
  <h2 className="text-red-500 text-5xl">Hello world</h2>
</div>
```

> Note: in order for this changes take effect, you must restart the server

## Create project structure

Inside the `src` folder create this folders:

- `components` folder, for all your components
- `assets` folder, for all fonts and images
- `hooks` folder, for your custom hooks
- `store` folder, in order to use with redux, inside the context api, for managing global state
- `services` folder, for organizing api routes
- `constants` folder, for all your constants variables
- `utils` folder, for usefull repetitive functions
- `pages` folder, for all your pages

At the end, it must be something like this:

```code
.
├── ./node_modules
├── ./public
└── ./src/
    ├── ./src/assets
    ├── ./src/components/
    │   ├── ./src/components/Footer.jsx
    │   ├── ./src/components/Header.jsx
    │   └── ./src/components/MainLayout.jsx
    ├── ./src/constants
    ├── ./src/hooks
    ├── ./src/pages
    ├── ./src/services
    ├── ./src/store
    └── ./src/utils
```

### MERN stack Blog app using Tailwind CSS - 3 - Creating Header

Inside the `pages` folder create a `HomePage.jsx` file

```js
import React from 'react';

const HomePage = () => {
  return <div>Home Page</div>;
};

export default HomePage;
```

Inside the `components` folder create a `Header.jsx` and a `Footer.jsx` file:

> Simply type **rfce** or **rafce** into your editor and VSCode will auto-magically create the relevant component structure for you. It formats your code and highlights the component name, initial text entry, and export statements so that you can easily rename it to whatever you'd like.

```js
import React from 'react';

const Header = () => {
  return <div>Header</div>;
};

export default Header;
```

```js
import React from 'react';

const Footer = () => {
  return <div>Footer</div>;
};

export default Footer;
```

Inside the `components` folder, create a `MainLayout.jsx` file, because the _header_ and the _footer_ are repectitive components in too many pages

```js
import React from 'react';

const MainLayout = () => {
  return <div>Main Layout Page</div>;
};

export default MainLayout;
```

Import `Header.jsx` and `Footer.jsx` into `MainLayout.jsx`

```js
import React from 'react';
import Header from './Header';
import Footer from './Footer';

const MainLayout = ({ children }) => {
  return (
    <div>
      <Header />
      {children}
      <Footer />
    </div>
  );
};

export default MainLayout;
```

> The `{ props. children }` property **allows you to create a generic template component that can be modified by the parent when it is invoked**. This means that a parent component can pass whatever is needed in the child component, even generated layout features that can then be rendered by the child.

Import `MainLayout.jsx` into `HomePage.jsx`

```js
import React from 'react';
import MainLayout from '../components/MainLayout';

const HomePage = () => {
  return (
    <div>
      <MainLayout></MainLayout>
    </div>
  );
};

export default HomePage;
```

At this moment it is not necessary to import anything between the `<MainLayout></MainLayout>` tags. For other parts we will import the `Hero.jsx` or `Article.jsx` component in the featured parts

### Creating the Header

The Header have two sections. The logo part and the navigation part

For managing images paths, I create constants.

Inside `constants` folder create an `images.jsx` file and paste this code:

```js
import Logo from '../assets/Logo.svg';

const images = {
  Logo,
};

export default images;
```

Inside `constants` folder create another file and name it `index.jsx` file and paste this code:

```js
export { default as images } from './images';
```

### Implement the `1st header` part // the `logo` part

Open the `Header.jsx` file and import the logo image

```js
import React from 'react';
import { images } from '../constants/index.jsx';

const Header = () => {
  return (
    <section>
      <header>
        <div>
          <img src={images.Logo} alt="logo image" />
        </div>
      </header>
    </section>
  );
};

export default Header;
```

You need to import the `Home.jsx` page in the `App.jsx` file, and now you can see the **logo section** with the `logo.svj`

```js
import HomePage from './pages/HomePage';

function App() {
  return (
    <div>
      <HomePage />
    </div>
  );
}

export default App;
```

### Implement the `2nd section` part // the `navigation` part

```js
import React from 'react';
import { images } from '../constants/index.jsx';

const Header = () => {
  return (
    <section>
      <header className="container mx-auto px-5 flex justify-between py-4 items-center">
        <div>
          <img src={images.Logo} alt="logo image" />
        </div>
        <div className="flex gap-x-9 items-center">
          <ul className="flex gap-x-5 font-semibold">
            <li className=" relative group">
              <a href="/" className="px-4 py-2">
                Home
              </a>
              <span className="text-blue-500 absolute transition-all duration-500 font-bold right-0 top-0  group-hover:right-[90%] opacity-0 group-hover:opacity-100">
                /
              </span>
            </li>
            <li>
              <a href="/articles">Articles</a>
            </li>
            <li>
              <a href="/pages">Pages</a>
            </li>
            <li>
              <a href="/pricing">Pricing</a>
            </li>
            <li>
              <a href="/faq">Faq</a>
            </li>
          </ul>
          <button className="border-2 border-blue-500 px-6 py-2 rounded-full text-blue-500 font-semibold hover:bg-blue-500 hover:text-white transition-all duration-300">
            Sign in
          </button>
        </div>
      </header>
    </section>
  );
};

export default Header;
```

In the `Header.jsx` create two components to iterate the `Navigation` links

```js
const NavItemsInfo = [
  { name: 'Home' },
  { name: 'Articles' },
  { name: 'Pages' },
  { name: 'Faq' },
];

const NavItem = ({ name }) => {
  return (
    <li className=" relative group">
      <a href="/" className="px-4 py-2">
        {name}
      </a>
      <span className="text-blue-500 absolute transition-all duration-500 font-bold right-0 top-0  group-hover:right-[90%] opacity-0 group-hover:opacity-100">
        /
      </span>
    </li>
  );
};
```

The final code in the `Header.jsx` will look like this:

```js
import React from 'react';
import { images } from '../constants/index.jsx';

const NavItemsInfo = [
  { name: 'Home' },
  { name: 'Articles' },
  { name: 'Pages' },
  { name: 'Faq' },
];

const NavItem = ({ name }) => {
  return (
    <li className=" relative group">
      <a href="/" className="px-4 py-2">
        {name}
      </a>
      <span className="text-blue-500 absolute transition-all duration-500 font-bold right-0 top-0  group-hover:right-[90%] opacity-0 group-hover:opacity-100">
        /
      </span>
    </li>
  );
};

const Header = () => {
  return (
    <section>
      <header className="container mx-auto px-5 flex justify-between py-4 items-center">
        <div>
          <img src={images.Logo} alt="logo image" />
        </div>
        <div className="flex gap-x-9 items-center">
          <ul className="flex gap-x-2 font-semibold">
            {NavItemsInfo.map((item) => {
              const { name } = item;
              return <NavItem key={name} name={name} />;
            })}
          </ul>
          <button className="border-2 border-blue-500 px-6 py-2 rounded-full text-blue-500 font-semibold hover:bg-blue-500 hover:text-white transition-all duration-300">
            Sign in
          </button>
        </div>
      </header>
    </section>
  );
};

export default Header;
```

### MERN stack Blog app using Tailwind CSS - 4 - Responsive Header

Open `tailwind.config.js` file and modify

```js
/** @type {import('tailwindcss').Config} */
export default {
  content: ['./index.html', './src/**/*.{js,ts,jsx,tsx}'],
  theme: {
    extend: {
      colors: {
        primary: '#1565D8',
        dark: {
          hard: '#0D2436',
          soft: '#183B56',
        },
      },
      fontFamily: {
        opensans: [],
        roboto: [],
      },
    },
  },
  plugins: [],
};
```

Download `Roboto` and `Open Sans` fonts from google fonts

https://fonts.google.com/

Open `App.css` and past the code below

```css
@import url('https://fonts.googleapis.com/css2?family=Open+Sans:ital,wght@0,300;0,400;0,500;0,600;0,700;0,800;1,300;1,400;1,500;1,600;1,700;1,800&family=Roboto:ital,wght@0,100;0,300;0,400;0,500;0,700;0,900;1,100;1,300;1,400;1,700;1,900&display=swap');
```

Open `tailwind.config.js` file again and add fonts array for global styles

```js
/** @type {import('tailwindcss').Config} */
export default {
  content: ['./index.html', './src/**/*.{js,ts,jsx,tsx}'],
  theme: {
    extend: {
      colors: {
        primary: '#1565D8',
        dark: {
          hard: '#0D2436',
          soft: '#183B56',
        },
      },
      fontFamily: {
        opensans: ['Open Sans', 'sans-serif'],
        roboto: ['Roboto', 'sans-serif'],
      },
    },
  },
  plugins: [],
};
```

Open `App.jsx` and modify the file so that the project use the general font `font-opensans`

```js
import './App.css';

function App() {
  return (
    <div className="App font-opensans">
      <HomePage />
    </div>
  );
}

export default App;
```

Modify the `header` so that can be responsive

```js
import React, { useState } from 'react';
import { images } from '../constants/index.jsx';
import { AiOutlineMenu, AiOutlineClose } from 'react-icons/ai';
import { MdOutlineKeyboardArrowDown } from 'react-icons/md';

const NavItemsInfo = [
  { name: 'Home', type: 'link' },
  { name: 'Articles', type: 'link' },
  { name: 'Pages', type: 'dropdown', items: ['About us', 'Contact us'] },
  { name: 'Pricing', type: 'link' },
  { name: 'Faq', type: 'link' },
];

const NavItem = ({ item }) => {
  const { type, name } = item;
  return (
    <li className="relative group">
      {type === 'link' ? (
        <>
          <a href="/" className="px-4 py-2">
            {name}
          </a>
          <span className="text-blue-500 absolute transition-all duration-500 font-bold right-0 top-0  group-hover:right-[90%] opacity-0 group-hover:opacity-100">
            /
          </span>
        </>
      ) : (
        <>
          <a href="/" className="px-4 py-2 flex gap-x-1 items-center">
            <span>{name}</span>
            <MdOutlineKeyboardArrowDown />
          </a>
          <div className="hidden transition-all duration-500 pt-4 absolute bottom-0 right-0 transform translate-y-full group-hover:block w-max">
            <ul className="flex flex-col shadow-lg rounded-lg overflow-hidden">
              {item.items.map((page) => {
                return (
                  <a
                    href="/"
                    className="hover:bg-dark-hard hover:text-white px-4 py-2 text-white lg:text-dark-soft"
                  >
                    {page}
                  </a>
                );
              })}
            </ul>
          </div>
        </>
      )}
    </li>
  );
};

const Header = () => {
  const [navIsVisible, setNavIsVisible] = useState(false);

  const navigationVisibleHandler = () => {
    setNavIsVisible((curState) => {
      return !curState;
    });
  };

  return (
    <section>
      <header className="container mx-auto px-5 flex justify-between py-4 items-center">
        <div>
          <img className="w-16" src={images.Logo} alt="logo image" />
        </div>
        <div className="lg:hidden z-50">
          {navIsVisible ? (
            <AiOutlineClose
              className="w-6 h-6"
              onClick={navigationVisibleHandler}
            />
          ) : (
            <AiOutlineMenu
              className="w-6 h-6"
              onClick={navigationVisibleHandler}
            />
          )}
        </div>
        <div
          className={`${
            navIsVisible ? 'right-0' : '-right-full'
          } transition-all duration-300 mt-[56px] lg:mt-0 bg-dark-hard lg:bg-transparent z-[49] flex flex-col w-full lg:w-auto justify-center lg:justify-end lg:flex-row fixed top-0 bottom-0  lg:static gap-x-9 items-center`}
        >
          <ul className="text-white items-center gap-y-5 lg:text-dark-soft flex flex-col lg:flex-row gap-x-2 font-semibold">
            {NavItemsInfo.map((item) => {
              const { name } = item;
              return <NavItem key={name} item={item} />;
            })}
          </ul>
          <button className="mt-5 lg:mt-0 border-2 border-blue-500 px-6 py-2 rounded-full text-blue-500 font-semibold hover:bg-blue-500 hover:text-white transition-all duration-300">
            Sign in
          </button>
        </div>
      </header>
    </section>
  );
};

export default Header;
```

### MERN stack Blog app using Tailwind CSS - 5 - Hero Section

# SPECIAL FEATURES USED in This Document

- https://tree.nathanfriend.io/

  An online tree-like utility for generating ASCII folder structure diagrams. Written in TypeScript and React.

# VISUAL STUDIO PLUGGINS

- install Tailwind CSS IntelliSense - https://marketplace.visualstudio.com/items?itemName=bradlc.vscode-tailwindcss

- Tailwind CSS IntelliSense - https://marketplace.visualstudio.com/items?itemName=bradlc.vscode-tailwindcss
