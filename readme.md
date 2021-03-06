# OTC

> a new project which used React Native to create App

## 常用命令

具体请查看 package.json 文件

``` bash
# install dependencies
npm install

# start app for ios or andriod
npm run ios/ad

# release android
npm run release-android 

# bundle android
npm run bundle-android 

# build android
npm run build-android

```

## 项目说明

### 关于组件的数据源格式校验

```
  项目初期并不会通过propType 校验prop。
  这边打个备注
```

### 关于数据缓存

```
  目前并没有引入完善的数据缓存机制，过早地优化和设计反而不好，一切以需求为导向
```

### 组件设计原则

```
  note: 组件尽量保证数据的来源可查，减少组件自身的状态，用functional component 或者 PureComponent 组件设计完成尽量把注释写详细
  eg:
    /**
      * 交易列表组件
      * @param {String} market 交易市场 
      * @param {String} newPrice 最新价 
      * @param {String} highPrice 最高价 
      * @param {String} lowPrice 最低价 
      * @param {String} tradeNum 交易量 
      * @return {React Component}
      */
  并不强制要求注释，但求写的能让人一眼看明白（意思就是写注释）
```

### git规范 (写在这里也只是尽量规范项目)
- 好的git分支模型是什么样子的？ 👇点击下面查看
  [a-successful-git-branching-model](http://nvie.com/posts/a-successful-git-branching-model/) 
  ```json
    懒的人大概看下这里：
      主要分成两个分支
      - master 反应生产环境的状态
      - develop 反应最新开发环境的状态
      - staging 发布分支

      在这个基础上有以下几种类型的分支
      - release-* 即将发布的分支，一般都是从功能分支提交到develop，再合并到 release-* 分支。发布前尽量少做修改
      - hotfix-* 作为一个模块的修补分支，命名以模块名作为后缀
      - feat-* 作为一个新模块分支，命名以模块名作为后缀
      ...
      合并 release-* 分支后请打上tag
      $ git checkout master
      切换到分支'master' 
      $ git merge --no-ff release-* (一般为版本号)
      由递归合并。
      （更改摘要）
      $ git tag -a * (一般为版本号)
  ```
- git 提交注释规范
  ```json
    build: 影响构建系统或外部依赖关系的更改（示例范围：gulp，webpack，npm）
    ci: 更改配置文件和脚本（示例范围：Travis，Circle，BrowserStack，SauceLabs
    docs: 仅文档更改
    feat: 一个新功能
    fix: 修复错误
    perf: 改进性能的代码更改
    refactor: 代码更改，既不修复错误也不添加功能
    style: 不影响代码含义的变化（空白，格式化，缺少分号等）
    test: 添加缺失测试或更正现有测试
  ```

### 发布前注意事项

* 合并当前分支到`develop`分支 并在`develop`测试通过，合并到`release-*`分支
* 发布前修改xxx`待补充`中的配置，用于显示当前发布内容
* ...

## 技术栈相关文档推荐

核心技术栈(包括但不限于以下)：
- [react-navigation](https://github.com/react-community/react-navigation) 使用react-navigation 替代官方路由
- [mobx-react](https://github.com/mobxjs/mobx-react) mobx for react
- [mobx](https://github.com/mobxjs/mobx) 中小型项目使用mobx替代redux 提升性能
- [react-native-looped-carousel](https://github.com/appintheair/react-native-looped-carousel) 轮播组件
- [react-native](https://github.com/facebook/react-native) 基于react的移动端开发框架
- [react-native-parallax-scroll-view](https://github.com/jaysoo/react-native-parallax-scroll-view)
- [crypto-js](https://github.com/brix/crypto-js) 加密库
- [moment](https://github.com/moment/moment) 时间格式化库
- [react-redux](https://github.com/reactjs/react-redux) react-redux封装
- [redux](https://github.com/reactjs/redux) 状态管理
- [redux-actions](https://github.com/reduxactions/redux-actions) flux规范的redux action
- ...

## 迭代说明

1.0.4 / 2017-11-07 (添加redux相关依赖)
===================

* 添加redux相关依赖，集成react navigation 解决路由跳转scene无法触发unmount，清除定时器

1.0.3 / 2017-11-01 (请求)
===================

* 配置允许http请求
* 引入pod第三方管理
* 配置一些常用的运行命令
* 交易列模块的完成

1.0.2 / 2017-07-19 (整体页面)
===================

* 添加资产，个人信息，交易记录，提取分工，登录，注册页面 `over`
* 完成个人中心ui `over`
* 整合api接口 `over`
* 完成交易块组件 `over`

1.0.1 / 2017-07-18 (小功能修改)
===================

* 添加交易块组件 `wait`
* 添加search组件 `wait`
* 添加搜索区块高度页面 `over`

1.0.0 / 2017-07-16 (项目初始化)
===================

* 初始化项目 `over`
* 项目整体路由设计 `over`
* mobx设计 `wait`
* 封装轮播组件 `over`


### 说明

目前就一个人在写，不想切分支，So, 我就一直用master咯...