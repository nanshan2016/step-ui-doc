### 

#### 安装使用

在项目中安装 step-ui 组件库

```
  npm install step-ui --save
```

在入口文件main.js 中安装使用,选择需要的组件进行全局注册

```
 import {
    SpBreadcrumb,
    SpBreadcrumbGroup,
    SpButton,
    SpCascader
 }

 Vue.use(SpBreadcrumb);
 Vue.use(SpBreadcrumbGroup);
 Vue.use(SpButton);
 Vue.use(SpCascader);
 ...
```

为保证组件能够正常显示及使用，请在全局添加如下css

```
button,div,form,img,input,label,li,ol,p,select,span,textarea,ul{box-sizing:border-box;margin:0;padding:0}
body,button,img,input,optgroup,option,select,textarea{font:14px/1 "Helvetica Neue",Helvetica,Arial,"PingFang SC","Hiragino Sans GB","Heiti SC","Microsoft YaHei","WenQuanYi Micro Hei",sans-serif;outline:0;border:0}
textarea{resize:none;overflow:auto}ol,ul{list-style:none}
.icon-mask{width:12px;height:12px;position:relative;top:2px}
```



