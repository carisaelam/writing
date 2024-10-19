# Webpack Cheat Sheet

Create package.json
`npm init -y`

Install dependencies
`npm install --save-dev webpack webpack-cli`
`npm install --save-dev html-webpack-plugin`
`npm install --save-dev style-loader css-loader`
`npm install --save-dev html-loader`
`npm install --save-dev webpack-dev-server`

create `src` directory for files to live in
create `src/template.html`
create `src/styles.css`
`import './styles.css'` in index.js

create `webpack.config.js` file

```Javascript
// webpack.config.js
const path = require("path");
const HtmlWebpackPlugin = require("html-webpack-plugin");

module.exports = {
  mode: "development",
  entry: "./src/index.js",
  output: {
    filename: "main.js",
    path: path.resolve(__dirname, "dist"),
    clean: true,
  },
  devtool: "eval-source-map",
  devServer: {
    watchFiles: ["./src/template.html"],
  },
  plugins: [
    new HtmlWebpackPlugin({
      template: "./src/template.html",
    }),
  ],
  module: {
    rules: [
      {
        test: /\.css$/i,
        use: ["style-loader", "css-loader"],
      },
      {
        test: /\.html$/i,
        loader: "html-loader",
      },
      {
        test: /\.(png|svg|jpg|jpeg|gif)$/i,
        type: "asset/resource",
      },
    ],
  },
};

```

`package.json` scripts:

```JSON

"scripts": {
    "build": "webpack",
    "dev": "webpack serve",
    "deploy": "git subtree push --prefix dist origin gh-pages"


```

## Deployment to GitHub Pages

1. Create new branch `gh-pages`
2. Add and commit all changes
3. `git checkout gh-pages && git merge main --no-edit`
4. `npm run build`
5. `git add dist -f && git commit -m "Deployment commit"`
6. `npm run deploy`
7. `git checkout main`


