# mvp-webpack
Minimum viable product to start Webpack
```
mkdir my-project
cd my-project
npm init -y
```
Install babel
```
npm install --save-dev babel-core
npm install --save-dev babel-preset-env
npm install --save-dev babel-preset-react
```

Create file `.gitignore` and add `node_modules` in first license
Create file `.babelrc` and add options

```
{
  "presets": ["env", "react"]
}
```

Configure Webpack
```
npm install --save-dev webpack babel-loader
```

Create webpack config `webpack.config.js`
with options
```
const path = require('path');

module.exports = {
    context: path.join(__dirname, 'src'),
    entry: {
        app: './main.js'
    },
    output: {
        path: path.join(__dirname, 'dist'),
        filename: 'bundle.js'
    },
    module: {
        rules: [
            {
                test: /\.js$/,
                exclude: /node_modules/,
                use: [
                    'babel-loader',
                ]
            }
        ]
    },
    resolve: {
        modules: [
            path.join(__dirname, 'node_modules')
        ]
    }
};
```

Create folder `src` and file `main.js`
And put into es6 example
```
const getDate = () => `Today ${new Date()}`;
document.getElementById('root').innerHTML = getDate();
```

Create folder `dist` and file `index.html`
with first html. For example
```
<html>
<head>
  <title>MVP Webpack</title>
</head>
<body>
  <h1>Hello World!</h1>
  <div id="root"></div>
  <script src="bundle.js" ></script>
</body>
</html>
```
Add into packege.json in script section `"compile": "webpack"`
Run `npm run compile`
And open index.html
 
