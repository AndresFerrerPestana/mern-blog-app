# MERN BLOG APP

## How to install the project

- create a folder `mern-react-blog`
- Navigate to `mern-react-blog` folder and run this commands:

```js
npm create vite@latest frontend-blog -- --template react
```

Navigate to the `frontend-blog` folder

```powershell
cd frontend-blog
```

Inside the `frontend-blog` folder run this command, to install node packages:

```cd frontend-blog
npm install
```

```cd frontend-blog
code .
```

```js
npm run dev
```

## Cleanup structure folder and files

- Remove all the code in `App.css` and `index.css`
- Remove `reportWebVitals` file and all imports
- Remove `logo.svg` and all imports

## Tailwind css installation

In the next steps, please refer to `tailwindccs` page documentation

- https://tailwindcss.com/docs/installation

Install tailwindcss via npm, and create your `tailwind.config.js` file.

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

```js
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

- `components` folder
- `assets` folder for all fonts and images
- `hooks` folder for your custom hooks
- `store` folder in order to use with redux, inside the context api, for managing global state
- `services` folder for organizing api routes
- `constants` folder, for all your constants variables
- `utils` folder, for usefull repetitive functions
- `pages` folder, for all your pages

```json
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

## MERN stack Blog app using Tailwind CSS - 2 - setup project

https://www.youtube.com/watch?v=_vKFcLxuwoQ
3:51

- setup a HomePage.jsx

Note:

- install Tailwind CSS IntelliSense - https://marketplace.visualstudio.com/items?itemName=bradlc.vscode-tailwindcss

- Tailwind CSS IntelliSense - https://marketplace.visualstudio.com/items?itemName=bradlc.vscode-tailwindcss

# SPECIAL FEATURES USED in This Document

- https://tree.nathanfriend.io/

  An online tree-like utility for generating ASCII folder structure diagrams. Written in TypeScript and React.
