---
title: 前端国际化框架 -- i8next
date: 2018-07-30 22:51:43
tags: JavaScript i18n
---

> 最近项目要求增加对多语言的支持，在几经比对之后，选择了 i18next 作为前端国际化框架，他有如下有点：
>
> 1. 不仅支持jQuery，还支持其他 如：react vue 等多种主流框架/库。
> 2. 支持多种形式的文本替换，可以尽量减少对页面架构的调整。
> 3. 更新时间较新，并且有文档可以查询。

 [i18next](https://github.com/i18next/i18next)  是一个运行在浏览器或其它JavaScript环境下的国际化框架，并且有数量众多的插件，下面只在项目中用到的做一些简单的介绍。具体内容请查阅文档：https://www.i18next.com/overview/introduction

<!-- more -->

#### 1. 初始化

在引入 i18next.js 和 jquery-i18next.js 之后，需要首先执行初始化操作：

```javascript
 i18next.init(options, callback) 
```

根据官方文档可以带参数跟回调初始化，或者只带回调

```javascript
i18next.init({
  fallbackLng: 'en',
  ns: ['file1', 'file2'],
  defaultNS: 'file1',
  debug: true
}, (err, t) => {
  if (err) return console.log('something went wrong loading', err);
  t('key'); // -> same as i18next.t
});

// with only callback
i18next.init((err, t) => {
  if (err) return console.log('something went wrong loading', err);
  t('key'); // -> same as i18next.t
});
```

可以设置的参数包括：

```javascript
i18next.init({
    lng: 'zh-CN', //当前使用语言
    fallbackLng: ['zh-CN'], //设置语言不存在时的回退语言，默认为：'dev'
    preload: ['zh-CN','en'], //预加载的语言，默认为：false
    whitelist: ['zh-CN','en'], //只允许加载的语言，默认为：false
    ns: ['cashier'], //命名空间，默认为：'translation'
    defaultNS: 'cashier', //默认命名空间，默认为：'translation'
    debug: true, //调试开关，默认为：false
    resources: { // 语言资源
        'zh-CN':{
            cashier: {
              common: {
                confirm: "确定",
                cancel: "取消"
              }
            }
        },
        en:{
            cashier: {
              common: {
                confirm: "confirm",
                cancel: "cancel"
              }
            }
        }
  	},
  }, function(err, t) {
    jqueryI18next.init(i18next, $); //jQuery-i18next 初始化，一般不需要特殊设置
    $('body').localize(); //执行翻译操作
  });
```

一般来说我们更倾向于吧语言资源文件放到外部文件更方便管理，i18next也有这方面的考虑，需要首先引入 i18nextXHRBackend.js ，在初始化时需要加上 .use(window.i18nextXHRBackend)，如下：

```javascript
i18next.use(window.i18nextXHRBackend).init({
    // 其他参数
    backend: { //与 resources 二选一，如果同时存在则执行 resources 中的内容
      loadPath: '/lang/{{lng}}/{{ns}}.json',
    },
  }, function(err, t) {});

});
```

网上所说的 resGetPath 参数这种方法在新版本中已经废弃了（大概1.8以后吧），新版本只能通过这种方式，语言文件格式为 .json，而且应该不是只能用固定的两种模式，上面双括号中的 lng 与 ns 是自己参数中设置的 lng 与 ns，应该可以放置在路径的任何地方。

#### 2. 在页面中的使用

在需要翻译的节点使用 data-i18n 属性即可，其中 i18n 可以在 jQuery-i18next 初始化时自行设置为其它文字，具体[参阅文档](https://github.com/i18next/jquery-i18next#initialize-the-plugin)

```html
<div>
    <button data-i18n="common.confirm"></button>
    <button data-i18n="common.concel"></button>
</div>
```

效果：

此外还可以追加文本，设置属性等

```html
<div>
    <button data-i18n="[title]common.confirm">确认按钮</button>
    <button data-i18n="[prepend]common.concel"></button>
    <button data-i18n="[append]common.concel"></button>
</div>
```



