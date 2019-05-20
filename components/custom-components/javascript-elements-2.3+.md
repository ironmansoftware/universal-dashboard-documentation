# JavaScript Elements \(2.3+\)

With Universal Dashboard 2.3 and later you can now define JavaScript elements without having to use `New-UDElement`. You can define your own objects and cmdlets without writing any C\# code. 

Universal Dashboard uses several web development technologies that may be helpful when developing your own JavaScript-based elements.

* Webpack
* Babel
* React
* NPM

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

Next, we are including a `UniversalDashboard` external. This variable is available to all custom components and defines functions for calling back to the server.

Finally, we use the provide plugin for React. This ensures that you do not include all over React with each of your components as UD will provide this dependency. 

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
    plugins: [
      new webpack.ProvidePlugin({
        React: "React", react: "React", "window.react": "React", "window.React": "React"
    }),
    ]
  };
}
```

The actual implementation of our React component is very minimal. It imports the `react-sparklines` components and passes props to them. We need to ensure that when this JavaScript file is loaded by UniversalDashboard, the component is registered. 

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

UniversalDashboard.register("sparklines", UDSparklines);
```

You will need to package your JavaScript before including it with your module. You can do this by running the npm build command. From the same directory where your package.json is. 

```text
npm run build
```

Finally, we can write the PowerShell script to create these components. The first step is to register the JavaScript with Universal Dashboard. This will return an ID that you need to include with your components. This ensures the JavaScript is loaded when you use a component. JavaScript is only loaded when the component is used. It won't be loaded more than once.

Now you can create a function that users will call. The function should return a hashtable. Make sure to set `isPlugin` to `$true` and `assetId` to the value you received when registering your script. 

{% code-tabs %}
{% code-tabs-item title="sparklines.psm1" %}
```text

$JsFiles = Get-ChildItem "$PSScriptRoot\*.bundle.js"
$SparklinesFile = $JsFiles | Where-Object { $_.FullName.Contains("sparklines")}
$AssetId = [UniversalDashboard.Services.AssetService]::Instance.RegisterScript($SparklinesFile.FullName)

function New-UDSparkline {
    param(
        [Parameter()]
        $Data,
        [Parameter()]
        $Color,
        [Parameter()]
        $Margin = 5
    )

    @{
         isPlugin = $true
         assetId = $AssetId 
         data = $Data 
         color = $Color
         margin = $Margin
    }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Distribution

At a minimum you will need to include the bundled JavaScript file and PSM1 file in a module. Users can then load this module into UD for use. 

