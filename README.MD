# [webpack4](https://v4.webpack.docschina.org/)

## [安装](https://v4.webpack.docschina.org/guides/installation/)

+ 初始化项目

```bash
npm init -y
```

+ 本地安装4版本

```bash
npm install --save-dev webpack@4.0.0
```

+ 4.0版本还需安装脚手架

```bash
npm install --save-dev webpack-cli@3.3.12
```

## [配置文件](https://v4.webpack.docschina.org/guides/getting-started/#%E4%BD%BF%E7%94%A8%E4%B8%80%E4%B8%AA%E9%85%8D%E7%BD%AE%E6%96%87%E4%BB%B6)

1. 在项目根目录创建**webpack.config.js**打包配置文件,单入口打包如:

```js
const path = require('path');

module.exports = {
    //打包入口
  entry: {
      main:'./src/index.js'
  },
  output: {
      //打包出口
    filename: 'main.js',
    path: path.resolve(__dirname, 'dist')
  }
};
```

2. 执行打包命令

```bash
npm webpack --config webpack.config.js
```
3. 创建快捷指令

在*package.json*文件中增加scripts选项配置中增加"build": "webpack"

```diff
 "scripts": {
      "test": "echo \"Error: no test specified\" && exit 1",
+     "build": "webpack"
    },
```

之后执行**npm run build**即可实现打包命令

## 模块

1. 导入[cssloader](https://v4.webpack.docschina.org/guides/asset-management/#%E5%8A%A0%E8%BD%BD-css)

```bash
npm install --save-dev style-loader@0.23.1 css-loader@2.1.1
```

2. 配置loader

​		在打包配置文件**webpack.config.js**增加module属性

```diff
 const path = require('path');

  module.exports = {
    entry: './src/index.js',
    output: {
      filename: 'bundle.js',
      path: path.resolve(__dirname, 'dist')
    },
+   module: {
+     rules: [
+       {
+         test: /\.css$/,
+         use: [
+           'style-loader',
+           'css-loader'
+         ]
+       }
+     ]
+   }
  };
```



## [插件](https://v4.webpack.docschina.org/plugins/)

+ [自动生成HTML](https://v4.webpack.docschina.org/plugins/html-webpack-plugin/)

