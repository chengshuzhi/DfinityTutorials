# 安装React框架

如果你不了解React框架，可以在[React网站](https://reactjs.org/)进行探索。

安装React模块步骤如下：

1. 运行下面的命令安装React模块

   ```text
   npm install --save react react-dom
   ```

2. 运行下面的命令安装Typescript加载器

   ```text
   npm install --save typescript ts-loader
   ```

3. 运行以下命令安装所需的样式加载器：

   ```text
   npm install --save style-loader css-loader
   ```

   如果 npm install 命令报告漏洞，您可能还需要运行 npm audit fix 命令尝试修复报告的漏洞，然后再继续。

   |  | 另一个安装模块的方法是，你可以编辑package.json文件来添加模块 |
   | :--- | :--- |


   ```text
   {
     "name": "contacts_assets",
     "version": "0.1.0",
     "description": "",
     "keywords": [],
     "scripts": {
       "build": "webpack"
     },
     "devDependencies": {
       "@dfinity/agent": "0.7.1",
       "assert": "2.0.0",
       "buffer": "6.0.3",
       "events": "3.3.0",
       "html-webpack-plugin": "5.3.1",
       "process": "0.11.10",
       "stream-browserify": "3.0.0",
       "terser-webpack-plugin": "5.1.1",
       "util": "0.12.3",
       "webpack": "5.24.4",
       "webpack-cli": "4.5.0"
     },
     "dependencies": {
       "css-loader": "^5.2.1",
       "react": "^17.0.2",
       "react-dom": "^17.0.2",
       "style-loader": "^2.0.0",
       "ts-loader": "^8.1.0",
       "typescript": "^4.2.4"
     }
   }
   ```

