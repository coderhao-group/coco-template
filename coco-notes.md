npm WARN deprecated core-js@3.9.0: core-js@<3.23.3 is no longer maintained and not recommended for usage due to the number of issues. Because of the V8 engine whims, feature detection in old core-js versions could cause a slowdown up to 100x even if nothing is polyfilled. Some versions have web compatibility issues. Please, upgrade your dependencies to the actual version of core-js.
npm ERR! code E502
npm ERR! 502 Bad Gateway - GET http://npmreg.qa.91jkys.com/axios/-/axios-0.21.1.tgz



coco-component.vue?7b09:136 
        
       Uncaught DOMException: Failed to set the 'domain' property on 'Document': 'coco-h5.cn' is not a suffix of 'localhost'.


改host之后 
127.0.0.1 aaa.coco-h5.cn

梯子要关掉全局代理才能访问

模板项目：aaa.coco-h5.cn:8081 
接口报错
http://qa.api.com/api/api/1.0.0/getCampaignInfo
因为走了预览的接口，改成下方的mock接口：
http://aaa.coco-h5.cn:8081/?isEdit=true


aaa.coco-h5.cn:8080/#/edit?id=1&pageld=426608548



pageConfig:  {
  config: {
    templateId: 1,
    templateGit: 'coderhao-group/coco-template',
    templateName: 'coco-template',
    projectName: '活动777',
    gitName: 'qwer',
    templateVersion: '0.2.7'
  },
  userSelectComponents: [],
  components: []
}
coderhao-group/coco-template

创建页面时必须关掉代理，结果才能响应成功，创建的仓库里才有代码(貌似也不是必须关闭。。。。)

pageConfig:  {
  config: {
    templateId: 1,
    templateGit: 'coderhao-group/coco-template',
    templateName: 'coco-template',
    projectName: '活动888',
    gitName: 'qqqq',
    templateVersion: '0.2.7'
  },
  userSelectComponents: [],
  components: []
}
coderhao-group/coco-template
Connection to ssh.github.com port 443 [tcp/https] succeeded!
To github.com:coderhao-group/qqqq.git
 * [new branch]      master -> gh-pages

点击Pages，等待5分钟
自动生成下方的网页
https://coderhao-group.github.io/qqqq/
报跨域
 Uncaught DOMException: Failed to set the 'domain' property on 'Document': 'huodong.goodcoder.tech' is not a suffix of 'coderhao-group.github.io'.

https://coderhao-group.github.io/wwww/
 Uncaught DOMException: Failed to set the 'domain' property on 'Document': 'huodong.goodcoder.tech' is not a suffix of 'coderhao-group.github.io'.

## 1 前言：可视化搭建诞生背景

已学完学习时长：4分26秒

## 2 架构设计



![img](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/91f2299b194644758271222cb32cf9f2~tplv-k3u1fbpfcp-zoom-in-crop-mark:3024:0:0:0.awebp)

## 3 前置基础知识准备

### 组件库

基于上面的前端框架选项，我们采用的是 vue3 所以组件库我们可以采用市面上比较流行的且支持 vue3 的框架，综合比较下来，我们可以选择的有 [Element plus](https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2Felement-plus%2Felement-plus) 和 [antdv 2x](https://link.juejin.cn/?target=https%3A%2F%2F2x.antdv.com%2Fdocs%2Fvue%2Fintroduce-cn%2F) 但是综合比较下来 antdv 2x 的生态和组件的丰富度以及使用度上面都优于 element-plus。所以我们也是计划采用 antdv 来作为我们的主要组件库。后面说到设计 `动态表单` 的时候也离不开组件库，`antdv` 对 JSX 的支持也是非常友好。

### egg

要做编辑、发布、数据存贮工作，当然离不开服务端。这里我们可以选择前端较为熟悉的 `nodejs` 作为我们的服务端语言。我们可以配合着 `nodejs` 再选择一个适合的框架来提高我们的开发效率。为什么是[egg](https://link.juejin.cn/?target=https%3A%2F%2Feggjs.org%2Fzh-cn%2F)?

nodejs 框架业界也比较多，比如 express、koa、nest、fastify、egg、Sails.... 考虑到应用本身，需要有在追求规范和共建的同时，还需要考虑如何平衡不同团队之间的差异，求同存异这样一套企业级架构，支持渐进式可扩展的开发方式。

> Sails 是和 Egg 一样奉行『约定优于配置』的框架，扩展性也非常好。但是相比 Egg，Sails 支持 Blueprint REST API、WaterLine 这样可扩展的 ORM、前端集成、WebSocket 等，但这些功能都是由 Sails 提供的。而 Egg 不直接提供功能，只是集成各种功能插件，比如实现 egg-blueprint，egg-waterline 等这样的插件，再使用 sails-egg 框架整合这些插件就可以替代 Sails 了

Express 是 Node.js 社区广泛使用的框架，简单且扩展性强，非常适合做个人项目。但框架本身缺少约定，标准的 MVC 模型会有各种千奇百怪的写法。Egg 按照约定进行开发，奉行『约定优于配置』，团队协作成本低。 基于以上和社区的评价，选择 egg 作为我们的后端框架，egg 本身也是支持插件化的开发，对于渐进式开发非常友好，这本身也是我们所需要的，H5可视化搭建本身也是一个需要渐进式迭代的过程。



## 4 模板设计

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/01fe9550fd894356a8060461b065af89~tplv-k3u1fbpfcp-zoom-in-crop-mark:3024:0:0:0.awebp)

## 5 模板通信设计

### 有哪些组件

告诉编辑器我们的模板有哪些组件，需要解决的第一个问题是有哪些组件？按照我们之前的约定，所有的组件我们都写到了 `components` 目录下。那么无非是读取 `components` 目录中的组件信息，进行展示即可。在前端获取目录的组织结构，我们可以利用 `webpack` 提供的 `require.context` 的功能，比如（后面再介绍一下其他的实现方式）：

```js
function getComponent() {
  const componentConfig = [];
  const requireConfig = require.context(
    './components',
    // 是否查询其子目录
    true,
    /package.json$/
  );
  requireConfig.keys().forEach(fileName => {
    const config = requireConfig(fileName);
    componentConfig.push(config);
  });

  return componentConfig;
}
```

这里需要注意的是，我们的组件下都有一个 `package.json` 文件，来描述该组件信息，所以我们只需要根据 `package.json` 的信息就能感知到组件的信息。

### 组件的基础信息

到这里我们已经得到了当前模板有多少个组件。接下来我们就需要对组件的基础信息进行设计，目前可以把我们的基础信息全部放到当前组件目录的 `package.json` 文件中，这样可以方便我们再写组件时，快速完善组件信息。拿 banner 组件举例，按照 `组件名`、`组件描述`、`组件缩略图`、`schema` 的方式设计以下数据结构：

```json
{
  "name": "coco-banner",
  "description": "banner 组件",
  "snapshot": "https://cdn.img/banner.png",
  "schema": {
    "type": "object",
    "properties": {
      "src": {
        "title": "图片地址",
        "type": "string",
        "format": "image"
      },
      "link": {
        "title": "跳转链接",
        "type": "string",
        "format": "url"
      }
    },
    "required": [
      "src"
    ]
  }
}
```

再结合之前的获取组件信息的代码，我们执行后，对编辑器展示出的模板所有组件信息，就可以用以下数据结构来表达：

```json
[
  {
    description: "banner 组件",
    name: "coco-banner",
    schema: {...},
    snapshot: "https://cdn.img/banner.png",
  },
  {
    description: "form 组件",
    name: "coco-form",
    schema: {...},
    snapshot: "https://cdn.img/form.png",
  }
]
```

### TODO告知

```js
export function postMsgToParent (message) {
  window.parent.postMessage(
    message,
    '*'
  );
}

// 通知父容器
postMsgToParent({
  type: 'returnConfig',
  data: {
    components: this.componentConfig, // 当前模板信息
    // ...
  }
});
```



## 6 模板动态化交互

已学完学习时长：10分35秒

Vue JSX

```Vue
<template>
  <div id="slider-view" class="slider-view" v-if="loaded">
    <!-- 编辑容器 -->
    <div
      :data-layout="component.props && component.props._layout"
      :id="`coco-render-id-_component_${index}`"
      :key="index"
      v-for="(component, index) in components"
    >
      <div
        :is="component.name"
        :key="component + index"
        :obj="component.props || {}"
        :config="component.config"
        @onRemoteComponentLoad="remoteComponentLoad"
      />
    </div>
  </div>
</template>
```



## 7 稳定性-模板更新策略

已学完学习时长：3分33秒

## 8 全局组件设计

已学完学习时长：17分50秒

## 9 全局组件注册

已学完学习时长：9分1秒

## 10 稳定性-组件更新策略

已学完学习时长：7分15秒

## 11 设计实现 CLI 为开发助力

已学完学习时长：29分36秒

## 12 可视化编辑区实现

已学完学习时长：29分56秒

## 13 可视化编辑区mock&预览

已学完学习时长：6分12秒

## 14 vue3 Form render 实现

已学完学习时长：25分

## 15 Server 端编译实现åå

已学完学习时长：8分34秒