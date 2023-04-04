# usage
- `npx babel src/ --out-dir dist/`: dry run with no transformations
  - `--plugins=@babel/plugin-transform-arrow-functions`: applies a specific code transformation
  - `--presets=@babel-preset-env`: determined set of plugins

# packages
- all separate npm packages
  - scope: `@babel`
- `@babel/core`: core functionality, not used directly
  - options are set by other tools
- `@babel/cli`: commandline tool (see: usage)

## plugins
- `@babel/plugin-transform-arrow-functions`: transforms arrow to regular functions

## presets
- `@babel-preset-env`: all ES2015+ to ES5 transformations

# configuration
- *babel.confing.json* in project root
- example:
```json
{
  "presets": [
    [
      "@babel/preset-env",
      {
        "targets": {
          "edge": "17",
          "firefox": "60",
          "chrome": "67",
          "safari": "11.1"
        }
      }
    ]
  ]
}
```
