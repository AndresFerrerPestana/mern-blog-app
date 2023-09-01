# MERN BLOG APP

## Install the project

- create a folder mern-react-blog

- Navigate to `mern-react-blog` folder and run this commands:

```js
npm create vite@latest frontend-blog -- --template react
```

```powershell
cd frontend-blog
```

```cd frontend-blog
npm install
```

```cd frontend-blog
code .
```

```js
npm run dev
```

## Tailwind css installation

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

Open index.css file and remove everything, then past the source code:

```js
@tailwind base;
@tailwind components;
@tailwind utilities;
```

Open `App.jsx` and remove all the imports

```html
<div className="w-screen h-screen bg-red-300"></div>
```

## Create project structure

Inside the src folder create this folders:

- components folder in the src foder
- assets in the source folder
- hooks folder in the src folder
- store folder to use redux
- services folder for organizing api routes
- constants folder, for all of all constant variables
- utils folder, for usefull repetitive functions
- pages folder
