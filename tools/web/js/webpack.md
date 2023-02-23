- static javascript bundler
    1. combines modules
    2. creates bundles
    3. bundles are static assets for the webapp
- usage: `npx webpack`
- configured in: *webpack.config.js*
```
module.exports = {
  <config>
};
```
- **entry** point:
    - start for internal dependency graph
    - which other modules are needed to run the entry point
    - default: *src/index.js*
    - config: `entry: './path/to/my/entry/file.js',`
- **output**:
    - where shall the bundles be created
    - default: `./dist/main.js`
    - important: `publicPath: '',` sets where to search assets relative to HTML page (here: same directory)
    - config:
```
output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'my-first-webpack.bundle.js',
  },
```

- `path()` is from: `const path = require('path');` node module
- **loaders**
    - initial support: .js, .json
    - 2 properties: `test`, `use`
    - `test`: which files to load
    - `use`: which module should transform the file
    - multiple loaders possible, order in `use` config matters
    - config:
```
module: {
    rules: [{ test: /\.txt$/, use: 'raw-loader' }],
  },
```
- **plugins**
    - used for other tasks than what loaders do
    - config:
```
const HtmlWebpackPlugin = require('html-webpack-plugin');
const webpack = require('webpack'); //to access built-in plugins

...

    plugins: [new HtmlWebpackPlugin({ template: './src/index.html' })],
```
- **mode**
    - enable built in optimizations
    - config: `mode: 'production'|'development',`
