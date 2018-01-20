一安装和命令行
1.新建一个文件夹
mkdir webpack-test
2.进入目录中
cd webpack-test
3. npm初始化
npm init
得到package.json
4.安装webpack
npm install webpack --save-dev
5.ls
node_modules 和 package.json
6.新建一个hello.js文件 和一个 world.js
在hello.js里面引入require('./world.js');

7.打包
webpack hello.js hello.bundel.js
8.新建一个style.css文件
在hello.js里面引入require('./style.css');
报错：You may need an appropriate loader to handle this file type.k
原因：webpack本身不支持css需要依赖loader,而且必须同时依赖css-loader和style-loa
der
安装：npm install css-loader style-loader --save-dev
css-loader:打包变成css类型文件，style-loader创建一个style标签插入到head里面

require('style-loader!css-loader!./style.css');

引入每一个css没必要都添加style-loader!css-loader!
可以在命令行里面绑定输入即可
webpack hello.js hello.bundle.js --module-bind 'css=style-loader!css-loader'


修改文件后，自动打包但是得手动刷新页面的参数--watch
webpack hello.js hello.bundle.js --module-bind 'css=style-loader!css-loader' --watch

可以让你看到打包过程的--progress
webpack hello.js hello.bundle.js --module-bind 'css=style-loader!css-loader' --progress

查看打包的模块参数：--display-modules
webpack hello.js hello.bundle.js --module-bind 'css=style-loader!css-loader'  --display-modules

打包模块的原因参数：--display-reasons
webpack hello.js hello.bundle.js --module-bind 'css=style-loader!css-loader'  --display-reasons

9.如果出现vim编辑器，用wq关闭


10.新建一个index.html

二建立项目的 webpack 配置文件