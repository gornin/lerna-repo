# lerna 多包管理工具

## 简介

Lerna 是一个包管理工具
中文网站：<https://lernajs.bootcss.com/>

### 两种工作模式

- Fixed/Locked mode
  自动更新改动包的版本号

- Independent mode
  `lerna init --independent`
  每次 publish 都要手动指定是补丁、次要更新、主要更改等

## 使用

### 全局安装 lerna

```bash
npm install lerna -g
lerna -v
```

### 初始化项目仓库 lerna-repo

```bash
$ mkdir lerna-repo && cd lerna-repo #或 cd $_
# 运行初始化命令
$ lerna init # 默认固定模式
```

### 目录结构

- lerna.json
  lerna 的配置文件，packages 目录下所有的文件夹都是可以发版的 npm 包

### 生成一个 npm 包

`lerna create <包名> [目录]`

```bash
cd packages && mkdir plugins

# 手动创建plugins目录后执行
lerna create aaa packages/plugins
lerna create bbb packages/plugins

# 默认放在packages目录
lerna create outDir
```

### 为包添加依赖

`lerna add <package>[@version] [--scope=特定的某个包] [--dev] [--exact]`
功能类似于 `npm install 包名`

- `scope` 指定为某个包添加依赖，如果没有 `scope` 选项，就会为 `packages` 下所有的包添加这个依赖；
- `dev` 选项代表依赖添加进 `devDependencies` 中。

```bash
lerna add lodash --scope=outDir --dev
```

### 查看整个工程目录下有哪些包

`lerna list [-l]`

### 安装依赖

为每个包安装依赖
`lerna bootstrap [--scope=特定的某个包]` 功能和 `npm install` 差不多，
如果不加 scope，lerna 会把工程下的所有包的依赖都安装好！

```bash
lerna bootstrap --scope=outDir
```

### 删除依赖

```bash
lerna clean
```

### 导入外部包

`lerna import 外部包的位置 --dest=工程下的位置`

```bash
#导入到packages/plugins目录下
lerna import ../a --dest=packages/plugins
```

### 运行包的 script 命令

`lerna run 命令 [--scope=特定的某个包]`
如果没有 scope 选项，lerna 会运行每个包的 script 命令

```bash
lerna run dev --scope=outDir
```

### 发版

`lerna publish`

### 列出更新的包

`lerna changed`

### 运行任意命令

`lerna exec -- <command> [...args]`
