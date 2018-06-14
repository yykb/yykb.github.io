---
title: nrm 使用简介
date: 2018-06-14 22:04:19
tags: npm nrm
---

>[nrm](https://github.com/Pana/nrm) 是npm的镜像源管理工具,他可以帮助你快速的切换不同的npm源。并且，切换以后可以继续使用npm命令操作。

## 安装

```bash
    $ npm install -g nrm
```

<!-- more -->

## 使用

#### 1. 查看源列表
    ```bash

        $ nrm ls

        * npm ---- https://registry.npmjs.org/
        cnpm --- http://r.cnpmjs.org/
        taobao - https://registry.npm.taobao.org/
        nj ----- https://registry.nodejitsu.com/
        rednpm - http://registry.mirror.cqupt.edu.cn/
        npmMirror  https://skimdb.npmjs.com/registry/
        edunpm - http://registry.enpmjs.org/

    ```
    星号表示目前正在使用的npm源。

####  2. 测试源速度
    ```bash

        //测试所有源的速度
        $ nrm test

        * npm ---- 1032ms
        cnpm --- 220ms
        taobao - 278ms
        nj ----- Fetch Error
        rednpm - Fetch Error
        npmMirror  2672ms
        edunpm - Fetch Error

        //测试某一个源的速度
        $ nrm test taobao

        * taobao - 232ms

    ```

####  3. 选择使用源
    ```bash

        //切换为cnpm源
        $ nrm use cnpm  

        Registry has been set to: http://r.cnpmjs.org/

        //切换后的源列表
        $ nrm ls

        npm ---- https://registry.npmjs.org/
        * cnpm --- http://r.cnpmjs.org/
        taobao - https://registry.npm.taobao.org/
        nj ----- https://registry.nodejitsu.com/
        rednpm - http://registry.mirror.cqupt.edu.cn/
        npmMirror  https://skimdb.npmjs.com/registry/
        edunpm - http://registry.enpmjs.org/

    ```


至此，最基础的操作已经完成。此外，nrm还可以添加、删除源，具体操作，请参照 [nrm开源项目]((https://github.com/Pana/nrm)) 文档。