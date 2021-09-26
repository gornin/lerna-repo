# lerna

## 以此执行以下命令

1. `npm install --global lerna`
2. `lerna init --independent`

3. `cd packages && mkdir fruit && cd fruit && touch index.js && npm init`

4. `cd ..`

5. `mkdir apple && cd apple && touch index.js && npm init`

6. 添加公共依赖

   `lerna add lodash`

7. 抽离公共模块

   `lerna bootstrap --hoist`

8. 添加单独依赖

   `lerna add jquery --scope=fruit`

   `lerna add zepto --scope=apple`

9. 添加 packages 里其他模块作为自己的依赖

   `lerna add fruit --scope=apple`

10. 更新公共依赖

    `npm install --save-dev lerna-update-wizard`

    `./node_modules/.bin/lernaupdate`

11. 全 package 发布

    `lerna publish`
