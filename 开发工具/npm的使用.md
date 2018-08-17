### npm的使用

## npm
- node package manager
- 管理项目的依赖包
- 可以用来下载我们需要使用的东西
- 安装后可以通过`npm -v` 查看版本

### npm 使用
- 1.初始化操作
    + `npm init` 会生成一个package.json文件
- 2.下载所需要的包
    + `npm install jquery`  下载jquery
    + 会去 registry.npmjs.org 这个地址下载jquery
    + 会生成一个node_modules目录，下载的内容就放在这个目录

- 3.下载包时，可以加上 `--save` 参数
    + `npm install jquery --save`, 下载之后会在package.json中添加
    当前下载的包的版本信息。
