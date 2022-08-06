---
layout: post
title:  "Create your first component in ReactJS"
author: kean
categories: [ ReactJS, create, component ]
image: assets/images/reactjs-banner.png
---
I will help you to create your first component with this guide. This guide also assume you were familiar with Typescript.

1. We have a new basic reactjs project with following folder structure.
```
 .
├── public 
│   ├── index.html
│   └── manifest.json
├── src 
│   ├── index.js
│   ├── index.css
│   ├── App.tsx
│   ├── App.test.tsx
│   └── App.css
├── package.json 
├── tsconfig.json
└── README.md
```

2. Create a new folder which name `components` under `src`. This folder will contain all your components.
```
 .
├── public/
│   ├── index.html
│   └── manifest.json
├── src/
│   ├── components/
│   ├── index.js
│   ├── index.css
│   ├── App.tsx
│   ├── App.test.tsx
│   └── App.css
├── package.json 
├── tsconfig.json
└── README.md
```

3. Create a new `HelloWorld.tsx` file in `components` folder.
```
 .
├── public/
│   ├── index.html
│   └── manifest.json
├── src/
│   ├── components/
│       └── HelloWorld.tsx
│   ├── index.js
│   ├── index.css
│   ├── App.tsx
│   ├── App.test.tsx
│   └── App.css
├── package.json 
├── tsconfig.json
└── README.md
```

4. We declare a new HelloWorld component in `HelloWorld.tsx` as following.
```js
function HelloWorld() {
  return (
    &lt;h2&gt;Hello World!&lt;/h2&gt;
  );
}

export default HelloWorld;
```

5. Update your `App.tsx` file.
```js
import HelloWorld from './components/HelloWorld';

function App() {
  return (
    <HelloWorld></HelloWorld>
  );
}

export default App;
```

6. Note: your custom component name should use uppercase to distinguish from native HTML tag.