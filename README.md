This repo is a collection of simple demos of Webpack.

These demos are purposely written in a simple and clear style.

You will find webpack@2x and webpack@1x, so don't use webpack globally:
```bash
$ npm i -g webpack@1.x webpack-dev-server@1.x
```

```javascript
{// 必要时请手动 npm install --save | uninstall --save 进行版本切换：
    "dependencies": {
      "webpack": "^1.13.3", // 1.14.0
      "webpack-dev-server": "^1.16.2"
    },
    "dependencies": {
      "webpack": "^2.3.3",
      "webpack-dev-server": "^2.4.2" // webpack-dev-server@2.4.2 requires a peer of webpack@^2.2.0
    }
}
```

## How to use

clone the repo and install the dependencies.
```bash
$ cd webpack-demos
$ npm install
```

文件夹命名：包含 webpack.config.js 配置文件 + index.js + index.html + app.css
- demo01，默认为 webpack@2.x
- demo01-1x， 注明`1x`的表示 webpack@1.x webpack-dev-server@1.x

```javascript
// package.json
{
    "scripts": {
        "build": "webpack --config ./demo02/webpack.config.js"
    }
}
```

```javascript
// webpack.config.js
module.exports = {
  entry: './demo02/main.js',
  output: {
    filename: './demo02/bundle.js'
  }
};
```

#### webpack
- webpack 指定特定的 webpack.config.js

```bash
cd /Users/galaxyw/Documents/web/demo/demo-webpack/loaders/extract
webpack --config webpack.config.js
```

- 设置`process.env.NODE_ENV`

```javascript
// package.json
{
  // ...
  "scripts": {
    "dev": "webpack-dev-server --devtool eval --progress --colors",
    "deploy": "NODE_ENV=production webpack -p"
    // NODE_ENV=production webpack --progress --colors
    // NODE_ENV=production webpack --config ./webpack.config.js
  },
  // ...
}
```

#### webpack-dev-server
实际上是一个小型Express服务器，它是用webpack-dev-middleware来处理webpack编译后的输出

```javascript
// webpack-dev-server@2.4.2 requires a peer of webpack@^2.2.0
// @^1.16.2 ，但是可以兼容 webpack-dev-server@2.4.2 的。
```

```
--config
    webpack-dev-server 指定特定的配置文件
--hort | --port
    # 访问方式，默认为localhost:8080,可通过 --hort --port 配置
    webpack-dev-server --inline --host localhost --port 9093 --config webpack.config.js
    http://localhost:8080/index-dev.html
--hot
    使用webpack-dev-server的自动刷新功能时，浏览器会整页刷新。
    热替换的区别就在于，当前端代码变动时，无需刷新整个页面，只把变化的部分替换掉。
    热更新
    webpack-dev-server --inline --hot --config ./webpack.config.js
```

#### loaders
- extract

#### plugins
- ExtractTextPlugin

## Index

1. [Entry file - 入口](#demo01-entry-file-source)
1. [Tree-shaking - 消除无用的代码（dead code）](#demo02-tree-shaking)

1. [Multiple entry files - 多入口](#demo02-multiple-entry-files-source)
1. [Babel-loader - 转换器](#demo03-babel-loader-source)
1. [CSS-loader](#demo04-css-loader-source)
1. [Image loader](#demo05-image-loader-source)
1. [CSS Module - css转换器，查询参数?module 的应用](#demo06-css-module-source)
1. [UglifyJs Plugin - 插件(压缩)](#demo07-uglifyjs-plugin-source)
1. [HTML Webpack Plugin and Open Browser Webpack Plugin - 插件(html处理、打开浏览器)](#demo08-html-webpack-plugin-and-open-browser-webpack-plugin-source)
1. [Environment flags - 开发\发布环境标识](#demo09-environment-flags-source)
1. [Code splitting - 代码分割](#demo10-code-splitting-source)
1. [Code splitting with bundle-loader](#demo11-code-splitting-with-bundle-loader-source)
1. [Common chunk - 通用块](#demo12-common-chunk-source)
1. [Vendor chunk - 第三方依赖块](#demo13-vendor-chunk-source)
1. [Exposing Global Variables - 导出全局变量](#demo14-exposing-global-variables-source)
1. [Hot Module Replacement - 模块热替换](#demo15-hot-module-replacement-source)
1. [React router - React路由器](#demo16-react-router-source)

## Demo01: Entry file ([source](https://github.com/ruanyf/webpack-demos/tree/master/demo01))

## Demo02: Tree shaking ([source](https://github.com/ruanyf/webpack-demos/tree/master/demo02))

***

## Useful links

- [Webpack docs](http://webpack.github.io/docs/)
- [webpack-howto](https://github.com/petehunt/webpack-howto), by Pete Hunt
- [Diving into Webpack](https://web-design-weekly.com/2014/09/24/diving-webpack/), by Web Design Weekly
- [Webpack and React is awesome](http://www.christianalfoni.com/articles/2014_12_13_Webpack-and-react-is-awesome), by Christian Alfoni
- [Browserify vs Webpack](https://medium.com/@housecor/browserify-vs-webpack-b3d7ca08a0a9), by Cory House
- [React Webpack cookbook](https://christianalfoni.github.io/react-webpack-cookbook/index.html), by Christian Alfoni

## License

MIT
