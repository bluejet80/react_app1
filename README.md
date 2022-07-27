# React App

This is the react app I will be making

the course is located here
[react course](https://www.youtube.com/watch?v=LMagNcngvcU)

this is the git hub repo
[Github repo](https://github.com/adrianhajdin/project_modern_ui_ux_gpt3)

## Parts of the Video

### The file Structure

This is the first thing that is different and should be noted is how this guy
sets up his file structure

## Progress

I stopped at 49:19. We are just ready to style the button.

## How to setup react

Once you have created a folder and move into that folder then just run the following command:

        npx create-react-app ./

This will setup a barbones react app in your directory.

Start VS Code and then the first thing to do is just completely delete the /src folder so that we can begin fresh with
only the things that we need for our app.

The first file to create is **index.js**.

Inside this file we will type:

        import React from 'react';
        import ReactDOM from 'react-dom';

        import App from './App';

        ReactDOM.render(<App />, document.getElementById('root'));

Now we will create the file which will contain our app **App.js**

Then inside that file we can type **rafce**

This will create a **react functional component** if you have the ES7 React Snippits Extension installed for VS Code

Now inside the file should be this:

        import React from 'react'

        const App = () => {
            return (
                <div>

                </div>
            )
        }

        export default App

For this course the only other thing left to do is install the dependencies that it will require.

This application only requires one dependecy and that is **react-icons**

So you wil install it by typing:

        npm install react-icons

Now to start our application we just type:

        npm start

This will start the development server on local host port **3000**

## Setting up basic file and folder structure

```
├── package.json
├── package-lock.json
├── public
│   ├── favicon.ico
│   ├── index.html
│   ├── logo192.png
│   ├── logo512.png
│   ├── manifest.json
│   └── robots.txt
├── react.md
├── README.md
└── src
    ├── App.css
    ├── App.js
    ├── components
    │   ├── action
    │   │   ├── action.css
    │   │   └── Action.jsx
    │   ├── article
    │   │   ├── article.css
    │   │   └── Article.jsx
    │   ├── brand
    │   │   ├── brand.css
    │   │   └── Brand.jsx
    │   ├── feature
    │   │   ├── feature.css
    │   │   └── Feature.jsx
    │   ├── index.js
    │   └── navbar
    │       ├── navbar.css
    │       └── Navbar.jsx
    ├── containers
    │   ├── blog
    │   │   ├── blog.css
    │   │   └── Blog.jsx
    │   ├── features
    │   │   ├── features.css
    │   │   └── Features.jsx
    │   ├── footer
    │   │   ├── footer.css
    │   │   └── Footer.jsx
    │   ├── header
    │   │   ├── header.css
    │   │   └── Header.jsx
    │   ├── index.js
    │   ├── possibility
    │   │   ├── possibility.css
    │   │   └── Possibility.jsx
    │   └── whatGPT3
    │       ├── whatGPT3.css
    │       └── WhatGPT3.jsx
    ├── index.css
    └── index.js
```

Inside the src folder we can see that all of our files are divided between two folders. The **components** folder and the **containers** folder.

The **component** folder will hold more simple componenets, and the **containers** folder will hold more complex componenets. Those created from multiple other components.

### Export Components from a single file

Instead of having to import each component in our App.js file. There is a way for us to import all the files with just a single file. We do this by creating an **index.js** file inside each the **components** folder and the **containers** folder.

Then within these files we will import all the components and then in our **App.js** file we will only have to import these files. And we do this by putting this code inside our **index.js** files. For our file inside the **components** folder, it will look like this:

        export { default as Article } from "./article/Article.jsx";
        export { default as Brand } from "./brand/Brand.jsx";
        export { default as Action } from "./action/Action.jsx";
        export { default as Feature } from "./feature/Feature.jsx";
        export { default as Navbar } from "./navbar/Navbar.jsx";

And the **index.js** file inside the **containers** folder will look like this:

        export { default as Blog } from "./blog/Blog";
        export { default as Features } from "./features/Features";
        export { default as Footer } from "./footer/Footer";
        export { default as Header } from "./header/Header";
        export { default as Possibility } from "./possibility/Possibility";
        export { default as WhatGPT3 } from "./whatGPT3/WhatGPT3";

Now within our **App.js** file we will just need to add this code:

        import {
            Footer,
            Blog,
            Possibility,
            Features,
            WhatGPT3,
            Header,
        } from "./containers";

        import { Action, Brand, Navbar } from "./components";

With this setup it allow us to keep our code organized and readable.

Now within our App.js file we can create each component. Here is what the file should look like at this point:

        import React from "react";

        import {
        Footer,
        Blog,
        Possibility,
        Features,
        WhatGPT3,
        Header,
        } from "./containers";

        import { Action, Brand, Navbar } from "./components";

        import "./App.css";

        const App = () => {
        return (
            <div className="App">
            <div className="gradient__bg">
                <Navbar />
                <Header />
            </div>
            <Brand />
            <WhatGPT3 />
            <Features />
            <Possibility />
            <Action />
            <Blog />
            <Footer />
            </div>
        );
        };

        export default App;

### Next thing is to setup the main styles for the app.

The app will have a set of main styles and then ach component will have styles specific to that component.

An example of a general inital style setup might look like this:

        * {
        box-sizing: border-box;
        padding: 0;
        margin: 0;
        scroll-behavior: smooth;
        }

#### Setting up style variables

If we setup a file called **index.css**, we can create a root selector and then define our variables inside it like this:

        @import url("https://fonts.googleapis.com/css2?family=Manrope:wght@200;300;400;500;600;700;800&display=swap");

        :root {
        --font-family: "Manrope", sans-serif;

        --gradient-text: linear-gradient(89.97deg, #ae67fa 1.84%, #f49867 102.67%);
        --gradient-bar: linear-gradient(103.22deg, #ae67fa -13.86%, #f49867 99.55%);

        --color-bg: #040c18;
        --color-footer: #031b34;
        --color-blog: #042c54;
        --color-text: #81afdd;
        --color-subtext: #ff8a71;
        }

Then in our css we can just call the vaiables like this:

        body {
            background: var(--color-bg)
        }

This is very nice. Then if we want to change the syles, we can change them in one place and the change will be reflected everywhere we use that variable.

#### Creating a gradient

To create a gradient in the background you can use a wonderful online tool called **Angry Tools Online Gradient Generator**.

The link to this is here [Gradient Generator](https://angrytools.com/gradient/)

#### Creating Animations

There is also an online tool for generating css animations in your app.

The link to this is here [CSS Animations](https://animista.net)

After the code is generated you will need to copy both the class and the keyframes and paste them into your css file.

#### Media Queries

Set margins and paddings to display differently on different devices.

Here is an example of a media query for mobile devices:

        @media screen and (max-width: 550px) {
        .section__padding {
            padding: 4rem 2rem;
        }

        .section__margin {
            margin: 4rem 2rem;
        }
        }

## Begin Building the App

Most of the assets for this app are provided by a website called **figma.com**.

The link to that website is here [Figma](https://figma.com)

The actual design is right here [Design Layout](https://www.figma.com/file/lz9lLpFHMxHm2odnwM3R0z/gpt3?node-id=0%3A1)

While in the App.js file in VS Code you can use the **Ctrl-Click** to quickly open any one of the Components.

### Navbar

The first component we will create is the Navbar Component.

All the class names that we create follow a certain specification called **BEM** which stands for **Block Element Modifier**.

more information on this can be found here [BEM by Example](https://sparkbox.com/foundry/bem_by_example)
