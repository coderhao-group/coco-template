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

创建页面时必须关掉代理，结果才能响应成功，创建的仓库里才有代码

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