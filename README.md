# reapop-theme-bootstrap

[![npm version](https://img.shields.io/npm/v/reapop-theme-bootstrap.svg?style=flat-square)](https://www.npmjs.com/package/reapop-theme-bootstrap) [![npm dependencies](https://img.shields.io/david/LouisBarranqueiro/reapop-theme-bootstrap.svg?style=flat-square)](https://www.npmjs.com/package/reapop-theme-bootstrap) [![npm download/month](https://img.shields.io/npm/dm/reapop-theme-bootstrap.svg?style=flat-square)](https://www.npmjs.com/package/reapop-theme-bootstrap) [![gitter chat](https://img.shields.io/gitter/room/LouisBarranqueiro/reapop-theme-bootstrap.svg?style=flat-square)](https://gitter.im/LouisBarranqueiro/reapop-theme-bootstrap)

Bootstrap theme for [Reapop](https://github.com/LouisBarranqueiro/reapop)

## Compatibility

Tested and works with **Reapop v0.6.0** in :

![Supported browsers](https://reapop-theme-wybo.s3.eu-central-1.amazonaws.com/supported-browsers.jpg)

## Installation

```
npm install reapop-theme-bootstrap --save
```

## Integration

### Update webpack config

You have to define some loaders to handle files of theme. If it's not already the case, you need to install :

 - **style-loader** with `npm install style-loader --save-dev`
 - **css-loader** with `npm install css-loader --save-dev`
 - **sass-loader** with `npm install sass-loader --save-dev`
 - **url-loader** with `npm install url-loader --save-dev`
 - **file-loader** with `npm install file-loader --save-dev`

Look at this example, you can use it in for your project. Check out configuration of [Reapop Demo](https://github.com/LouisBarranqueiro/reapop) to see a complete example.

``` js
// CSS loader with some configuration
// read https://github.com/webpack/css-loader to understand each query parameters
var CSSLoader = [
  'css?sourceMap&-minimize',
  'modules',
  'importLoaders=1',
  'localIdentName=[name]__[local]__[hash:base64:5]'
].join('&');

module.exports = {
  module: {
    loaders: [{
      test: /\.scss$/,
      loaders: ['style', CSSLoader, 'sass']
    }, {
      test: /\.woff(2)?(\?v=[0-9]\.[0-9]\.[0-9])?$/,
      loader: "url-loader?limit=10000&minetype=application/font-woff"
    }, {
      test: /\.(ttf|eot|svg)(\?v=[0-9]\.[0-9]\.[0-9])?$/,
      loader: "file-loader"
    }]
  }
};
```

### Install Font Awesome and Bootstrap

This theme doesn't include bootstrap and Font Awesome to let you install them the way you want:

#### With Webpack

1. Install Bootstrap with `npm install bootstrap --save`
2. Install Font Awesome with `npm install font-awesome --save`

and import them in your app. Example :

```
import '!style-loader!css-loader!bootstrap/dist/css/bootstrap.min.css';
import '!style-loader!css-loader!font-awesome/css/font-awesome.min.css';
```

#### With BootstrapCDN

Add these lines in `<head>` of your main `index.html` file :
``` html
<link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css" rel="stylesheet">
<link href="https://maxcdn.bootstrapcdn.com/font-awesome/4.6.3/css/font-awesome.min.css" rel="stylesheet">
```

### Set the theme

``` js
import React, {Component} from 'react';
import NotificationsSystem from 'reapop';
// 1. import Bootstrap and Font Awesome
import '!style-loader!css-loader!bootstrap/dist/css/bootstrap.min.css';
import '!style-loader!css-loader!font-awesome/css/font-awesome.min.css';
// 2. import reapop theme
import theme from 'reapop-theme-bootstrap';

class ATopLevelComponent extends Component {
  render() {
   // 3. set `theme` prop
    return (
      <div>
        <NotificationsSystem theme={theme}/>
      </div>
    );
  }
}
```

### Customize the theme

Follow this guide : [Reapop - Customize or create a theme](https://github.com/LouisBarranqueiro/reapop/blob/master/docs/api.md#customize-or-create-a-theme)

## License

Reapop-theme-bootstrap is under [MIT License](https://github.com/LouisBarranqueiro/reapop-theme-bootstrap/blob/master/LICENSE)
