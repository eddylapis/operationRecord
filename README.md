## 利用现代浏览器的强大功能还原操作并储存 V1.0.0

![示例图片](./Kapture 2019-01-25 at 15.14.45.gif)

## ✨ 特性

- 录制并回放任意 web 界面中的用户操作 前端封装+后端。
- 开箱即用。
- 支持跨域。

## 🖥 支持环境

- `Linux`,`MacOS`,`Windows`。
- 现代浏览器和 IE11及以上。
- [Electron](http://electron.atom.io/)

## 💽 后端架构

1. 基于[NodeJS](https://nodejs.org)
2. 数据库使用[MySQL](https://www.mysql.com/)
3. 服务框架使用[express4](http://www.expressjs.com.cn/)

## 💻 前端架构

1. 录制基于[rrweb](https://github.com/rrweb-io/rrweb)
2. `http`请求默认依赖[axios](https://www.kancloud.cn/yunye/axios/234845)可配置为[jQuery](http://jquery.com/)以及任何与`jQuery`结构相同的库
3. 回放页面前端框架使用[VUE](https://cn.vuejs.org/)
4. `UI`框架使用[Element](http://element-cn.eleme.io/#/zh-CN)
5. 回放基于[rrewb-player](https://github.com/rrweb-io/rrweb-player)

## 📦 安装

1. 安装[MySQL](https://www.mysql.com/)并配置`./server/mysql.config`里的端口号及用户密码

2. 安装[NodeJS](https://nodejs.org/)

3. 进入项目目录

4. 安装依赖

   ```shell
   npm i #国内使用cnpm
   ```

5. 启动项目

   ```shell
   node server
   ```

   

## operationRecord.js参数

```javascript
const record=new Record({
    url: '/operationRecord/add',//后台服务器url，如未修改服务器文件，应为：服务端ip+/operationRecord/add
    name: '不知名的测试人员',//提交人，会显示在统计页面。默认：unknow
    projectName: 'test',//需要连接的表名
    ajaxFn:$,//ajax 提交函数，默认依赖axios，如果项目中使用的是jquery直接写$,可以使用人和和jquery结构一致的ajax库
    msg:'你这东西有bug啊',//提交bug信息，最多255
    isReport:'1',//是否认为上报，1：是，0：否。默认：0
    interval:'2000',//提交间隔，默认10秒，单位ms
    success: function (res) {
        console.log(`成功的回调${res}`);
    },
    error: function (err) {
        console.log(`失败的回调${err}`);
    }
});
//方法
record.destroy(); //销毁
console.log(record) //查看属性
```



## 🔨 示例

```html
<!DOCTYPE html>
<html lang="en">

    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <meta http-equiv="X-UA-Compatible" content="ie=edge">
        <title>test</title>
    </head>

    <body>
        <h1>test</h1>
        <input type="text">
        <button>测试</button>
        <button>回放</button>
        <script src="./js/axios.min.js"></script>
        <script src="./js/operationRecord.js"></script>
        <script>
            let a = new Record({
                url: 'ip地址+/operationRecord/add',
                name: 'liu',
                projectName: 'testProject',
                msg:'测试信息',
                interval:20000,
                success: function (res) {
                    console.log(res);
                }
            });
        </script>
    </body>

</html>
```

打开`http://localhost:9527/`查看结果

## 📖 目录结构

```
├── .git								
├── .gitignore
├── README.md
├── datas								// 录制数据储存目录
├── node_modules
├── package.json
├── public								// 静态文件目录
├── ├── .DS_Store
├── ├── css								// css文件
├── ├── ├── element.min.css
├── ├── ├── fonts						// 字体文件
├── ├── ├── ├── element-icons.ttf
├── ├── ├── ├── element-icons.woff
├── ├── ├── player.min.css
├── ├── ├── reset.min.css
├── ├── ├── style.css					// 自定义样式
├── ├── index.html
├── ├── js								// js文件
├── ├── ├── axios.min.js
├── ├── ├── element.min.js
├── ├── ├── operationRecord.js
├── ├── ├── player.min.js
├── ├── ├── replay.js
├── ├── ├── vue.js
├── ├── replayer.html
├── readme.js
├── server								// 服务器文件
├── ├── local-zh.config					// 表名中英文对应
├── ├── mysql.config					// mysql配置文件
├── ├── mysql.js						// mysql操作
├── server.js							// server
```

## 🤝 参与共建 [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)

[提交pr](https://github.com/asdjgfr/operationRecord/pulls)

[提交issue](https://github.com/asdjgfr/operationRecord/issues)





