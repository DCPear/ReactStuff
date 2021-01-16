### Creating a react project from scratch. 2021

Without the help of Create React App or other boilerplate generators. This is a good experience for React developers to go through, at least once, since it gives a lot of insight into what goes on behind the scenes in a React app. And these are things that most developers don't ever think about.

```
We need:

index.html.
This is what will be sent to the client and what React will render our app into.

support for ES6,
Since obviously, we'd rather write our code using modern JavaScript syntax

Webpack.
This will take care of:

the actual building our app
allow us to use things like CSS modules to style our app
serve our app during development
root component.
This is the base of our component tree. You can think of it as the container that holds the rest of our application components.
```

#### Create a simple React App

```
1. Create a folder - “any-name”
Create and set up root directory that will hold our React project.
```

```
2. Inside that directory run - npm init -y
Initialise the project and create package.json file.
```

```
3. Inside that directory run - git init
Initialise as new git repo
```

```
4. Create two directories inside the root directory
$mkdir public - This will hold all the publicly accessible resources for our app just like in a regular static website.
$mkdir src - This will hold our actual react code.
```

```
5. Create an index.html inside folder /public
When someone send a request for your website, this is what gets sent.
$ cd public/
$ cat>index.html
```

```
6. Write index.html
Very basic html

DOCTYPE tag at the top and then the html tags.

<head>

<tittle> tag - what gets displayed at the top of the tab

<body> tag - define a div here that is very important. It needs to have the ID root. And this is the div that React will eventually render our app into.

<noscript> tag - just in case the user has JavaScript disabled in their browser

<script> tag to load our react code

Note: bundle.js does not exist yet.
```

```
7. npm install –save-dev @babel/core @babel/cli @babel/preset-env @babel/preset-react
Install babel and configure

create .babelrc file in root of the directory
        This file will tell the Babel transpiler what presets and plugins to use to transpile our code.
        Define a JSON object.

{

    "presets": ["@babel/preset-env", "@babel/preset-react"]

}
 Babel/preset-env -> handles the transformation of ES6 into common JS, @babel/preset-react-> deals with JSX.

We will be writing our code using ES6 syntax and JSX (React’s Special HTML-like syntax for defining page layouts)

Babel will use both of these presets to transform our code into something a browser can run, although just as a side note, most modern browsers now support ES6 syntax so this isn't as necessary as it once was.
```

```
8.Create App component src/App.js and src/App.css
```

```
9. Create src/index.js
Index.js code has the code that inserts our react app into our index.html page.

i.e code that will actually render our app component that we just created into the index.html page.
```

```
10. npm Install react react-dom
install react and react-dom, the 2 packages we are using in the components.
```

```
11. npm install –save-dev webpack webpack-cli webpack-dev-server style-loader babel-loader

Install and Configure Webpack
create webpack.config.js
note: Since web pack will be the thing that's actually transpiling our code from ES6 to common JS, the webpack code itself is usually written in common JS.
```

```
12. Define a npm scipts for webpack in package.json
"scripts": {
    "start": "webpack serve",
    "build": "webpack",
    "test": "echo \"Error: no test specified\" && exit 1"
  },
```

```
 13. All set. Now we can run "npm start"
 open localhost:8080 in browser

 Note: for app to be opened on a specific post other than defaul port 8080, change webpack config as follows
 devServer: {
        contentBase: path.join(__dirname, 'public/'),
        port: 3000,
        hotOnly: true,
        open:true
    },
```

```
14. Test framework -  Setup and use Jest and Enzyme to test
Both Jest and Enzyme are specifically designed to test React applications, Jest can be used with any other Javascript app but Enzyme only works with React.

Jest
npm install --save-dev jest babel-jest
add acript "test": "jest" to package.json

add to package.json
 "jest":{
    "moduleNameMapper":{
         "\\.(css|less|sass|scss)$": "<rootDir>/__mocks__/styleMock.js",
         "\\.(gif|ttf|eot|svg)$": "<rootDir>/__mocks__/fileMock.js"
    }
}
and add mock files themselves. refer to jest docmentation https://jestjs.io/docs/en/webpack#handling-static-assets

 * Jest is a JavaScript unit testing framework, used by Facebook to test services and React applications.
 * Jest acts as a test runner, assertion library, and mocking library.
 * Jest also provides Snapshot testing, the ability to create a rendered ‘snapshot’ of a component and compare it to a previously saved ‘snapshot’.

 Code Coverage reports
   * add a script to package.json ->to run npm run coverage
       "coverage":"npm run test -- --coverage",
----------|---------|----------|---------|---------|-------------------
File      | % Stmts | % Branch | % Funcs | % Lines | Uncovered Line #s
----------|---------|----------|---------|---------|-------------------
All files |     100 |      100 |     100 |     100 |
 App.js   |     100 |      100 |     100 |     100 |
----------|---------|----------|---------|---------|-------------------
Test Suites: 1 passed, 1 total
Tests:       2 passed, 2 total
Snapshots:   1 passed, 1 total

------------------
 Enzyme
 npm install --save-dev enzyme enzyme-to-json
 npm install --save-dev @wojtekmaj/enzyme-adapter-react-17
  * Enzyme is a JavaScript Testing utility for React that makes it easier to assert, manipulate, and traverse your React Components’ output.
  Enzyme, created by Airbnb, adds some great additional utility methods for rendering a component (or multiple components), finding elements, and interacting with elements.
```

```
15. Linting with ESLint - npm install --save-dev eslint(locally)
$./node_modules/.bin/eslint --init

answers for .eslintrc.json

* How would you like to use ESLint? .To check syntax, find problems, and enforce code style
* What type of modules does your project use? JavaScript modules (import/export)
* Which framework does your project use? React
 Does your project use TypeScript? » No
* Where does your code run? browser, node
* How would you like to define a style for your project? ...  guide
*  Which style guide do you want to follow? Airbnb: https://github.com/airbnb/javascript

configure rules in .eslintrc.json
add .eslintignore
add script eslint to package.json

fixing Eslint errors
control dot on Windows to show the recommendations
```
```
16. Testing and Debugging
   * Add React Developer Tools from Chrome web store -> Add to Chrome
   (adds Components and Profiler in Dev tools)
```
```
16. proptypes vs flow???
Type checking with flow??? or 
Static type checkers like Flow and TypeScript identify certain types of problems before you even run your code. They can also improve developer workflow by adding features like auto-completion. For this reason, we recommend using Flow or TypeScript instead of PropTypes for larger code bases.
```
