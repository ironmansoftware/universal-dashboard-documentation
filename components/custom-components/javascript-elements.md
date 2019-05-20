# JavaScript Elements \(pre 2.3\)

New-UDElement can also define JavaScript-based components. These components should define a React component that is capable of loading into a React single page application.

Universal Dashboard uses several web development technologies that may be helpful when developing your own JavaScript-based elements.

* Webpack
* Babel
* React
* NPM

For this example, we will be using the [UDSparklines](https://github.com/ironmansoftware/ud-sparklines) project.

To get started, you will need to define a NPM package.json file. This final defines the package's dependencies and any tooling that is required to bundle the package into a final JS file. UDSparklines uses react-sparklines.

The `build` and `dev` tasks define how the JS file is compiled. In this case, we are using webpack.

```text
{
  "name": "ud-sparklines",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "build": "webpack -p --env production",
    "dev": "webpack -p --env development"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
      "react":"16.2.0",
      "react-sparklines":"1.7.0"
  },
  "devDependencies": {
    "babel-core": "^6.26.0",
    "babel-loader": "^7.1.2",
    "babel-preset-es2015": "^6.24.1",
    "babel-preset-react": "^6.24.1",
    "uglifyjs-webpack-plugin": "0.4.6",
    "webpack": "^3.6.0"
  }
}
```

To define how webpack packages the JS file, we need to use a webpack.config.js. This file defines all the settings for webpack. This is a very minimal file and you can expand it will all kinds of plugins and configuration options.

The `filename` option defines the output value of webpack. The `entry` option defines the input file. In this case, we are using Babel JSX to define our React component. You can also define React components with Typescript and JavaScript.

Finally, we are including a `UniversalDashboard` external. This variable is available to all custom components and defines functions for calling back to the server.

```text
var webpack = require('webpack');
var path = require('path');

var BUILD_DIR = path.resolve(__dirname, 'public');
var SRC_DIR = path.resolve(__dirname);
var APP_DIR = path.resolve(__dirname, 'src/app');

module.exports = (env) => {
  const isDev = env == 'development' || env == 'isolated';

  return {
    entry: [__dirname + '/index.jsx'],
    output: {
      library: "UDSparklines",
      libraryTarget: "var",
      path: BUILD_DIR,
      filename: isDev ? 'sparklines.bundle.js' : 'sparklines.[hash].bundle.js',
      //sourceMapFilename: 'bundle.map',
      publicPath: "/"
    },
    module : {
      loaders : [
        { test: /\.(js|jsx)$/, exclude: [/node_modules/, /public/], loader: 'babel-loader'}
      ]
    },
    externals: {
      UniversalDashboard: 'UniversalDashboard'
    },
    resolve: {
      extensions: ['.json', '.js', '.jsx']
    },
    plugins: []
  };
}
```

The actual implementation of our React component is very minimal. It imports the `react-sparklines` components and passes props to them. These props are provided via PowerShell and the `New-UDElement` cmdlet.

```text
import React from 'react';
import { Sparklines, SparklinesBars } from 'react-sparklines';

export default class UDSparklines extends React.Component {
    render() {
      return (
        <Sparklines data={this.props.data} limit={10} margin={this.props.margin}>
            <SparklinesBars color={this.props.color} />
        </Sparklines>
      );
    }
}
```

Finally, the `New-UDElement` cmdlet is used to bring it all together. It defines the JavaScript file to import. The `ModuleName` parameter should be a globally unique name for the component. The hashtable defined by `Properties` will be passed to the JavaScript component via `this.props`.

```text
function New-UDSparkline {
    param(
        [Parameter()]
        $Data,
        [Parameter()]
        $Color,
        [Parameter()]
        $Margin = 5
    )

    New-UDElement -JavaScriptPath $JsFile -ModuleName "UDSparklines" -Properties @{
        data = $Data
        color = $Color
        margin = $Margin
    }
}
```

The full source code for this example is on [GitHub](https://github.com/ironmansoftware/ud-sparklines).

